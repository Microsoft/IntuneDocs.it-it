---
title: Integrare Jamf Pro con Microsoft Intune per la conformità
titleSuffix: Microsoft Intune
description: Usare i criteri di conformità di Microsoft Intune con l'accesso condizionale di Azure Active Directory per favorire l'integrazione e la protezione dei dispositivi gestiti da Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dab1025e283ed1591c22b03ed4e3a61d40a20c3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515085"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrare Jamf Pro con Intune per la conformità

Quando l'organizzazione usa [Jamf Pro](https://www.jamf.com) per gestire i dispositivi macOS, è possibile adottare i criteri di conformità di Microsoft Intune e l'accesso condizionale di Azure Active Directory (Azure AD) per garantire la conformità dei dispositivi presenti nell'organizzazione prima che questi accedano alle risorse aziendali. Questo articolo consente di configurare l'integrazione di Jamf con Intune.

Quando Jamf Pro è integrato con Intune, è possibile sincronizzare i dati di inventario dei dispositivi macOS con Intune tramite Azure AD. Il motore di conformità di Intune analizza quindi i dati di inventario per generare un report. L'analisi di Intune viene combinata con informazioni sull'identità Azure AD dell'utente del dispositivo per configurare l'implementazione tramite l'accesso condizionale. I dispositivi conformi ai criteri di accesso condizionale possono ottenere l'accesso alle risorse aziendali protette.

Dopo aver configurato l'integrazione, si [configurano Jamf e Intune per applicare la conformità con l'accesso condizionale](conditional-access-assign-jamf.md) nei dispositivi gestiti da Jamf.

## <a name="prerequisites"></a>Prerequisiti

### <a name="products-and-services"></a>Prodotti e servizi

Per configurare l'accesso condizionale con Jamf Pro, è necessario quanto segue:

- Jamf Pro 10.1.0 o versione successiva
- [App Portale aziendale per macOS](https://aka.ms/macoscompanyportal)
- Dispositivi macOS con OS X 10.12 Yosemite o versioni successive

### <a name="network-ports"></a>Porte di rete

<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
Le seguenti porte devono essere accessibili per garantire l'integrazione corretta di Jamf e Intune:

- **Intune**: Porta 443
- **Apple**: Porte 2195, 2196 e 5223 (notifiche push a Intune)
- **Jamf**: Porte 80 e 5223

Per consentire il corretto funzionamento di APNS in rete, è necessario abilitare anche le connessioni in uscita a, e i reindirizzamenti da:

- Blocco Apple 17.0.0.0/8 sulle porte TCP 5223 e 443 da tutte le reti client.
- Porte 2195 e 2196 dai server Jamf Pro.  

Per altre informazioni su queste porte, vedere i seguenti articoli:

- [Requisiti di configurazione di rete di Intune e larghezza di banda](../fundamentals/network-bandwidth-use.md).
- [Network Ports Used by Jamf Pro](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) (Porte di rete usate da Jamf Pro) su jamf.com.
- [Porte TCP e UDP usate dai prodotti software Apple](https://support.apple.com/HT202944) su support.apple.com

## <a name="connect-intune-to-jamf-pro"></a>Connettere Intune a Jamf Pro

Per connettere Intune a Jamf Pro:

1. Creare una nuova applicazione in Azure.
2. Abilitare Intune per l'integrazione con Jamf Pro.
3. Configurare l'accesso condizionale in Jamf Pro.

### <a name="create-an-application-in-azure-active-directory"></a>Creare un’applicazione in Azure Active Directory

1. Nel [portale di Azure](https://portal.azure.com) passare ad **Azure Active Directory** > **Registrazioni app** e quindi selezionare **Nuova registrazione**.

2. Nella pagina **Registra un'applicazione** specificare i dettagli seguenti:

   - Nella sezione **Nome** immettere un nome significativo per l'applicazione, ad esempio **Accesso condizionale Jamf**.
   - Per la sezione **Tipi di account supportati** selezionare **Account in qualsiasi directory organizzativa**.
   - Per **URI di reindirizzamento** lasciare l'impostazione predefinita Web e quindi specificare l'URL dell'istanza Jamf Pro.

3. Selezionare **Registra** per creare l'applicazione e per aprire la pagina **Panoramica** per la nuova app.

4. Nella pagina **Panoramica** dell'app copiare il valore **ID client applicazione** e annotarlo per usarlo in seguito. Questo valore sarà necessario nelle procedure successive.

5. Selezionare **Certificates & secrets** (Certificati e segreti) in **Gestione**. Selezionare il pulsante **New client secret** (Nuovo segreto client). Immettere un valore in **Descrizione**, selezionare un'opzione per **Scadenza** e scegliere **Aggiungi**.

   > [!IMPORTANT]
   > Prima di uscire da questa pagina, copiare il valore del segreto client e annotarlo per usarlo in seguito. Questo valore sarà necessario nelle procedure successive. Questo valore non sarà più disponibile, senza ricreare la registrazione dell'app.

6. Selezionare **Autorizzazioni API** in **Gestione**. 

7. Nella pagina Autorizzazioni API rimuovere tutte le autorizzazioni da questa app selezionando l'icona **...** accanto a ogni autorizzazione esistente. Si noti che questa operazione è obbligatoria. L'integrazione avrà esito negativo se sono presenti autorizzazioni aggiuntive impreviste nella registrazione dell'app.

8. Successivamente, si aggiungeranno le autorizzazioni per aggiornare gli attributi del dispositivo. In alto a sinistra nella pagina **Autorizzazioni API** selezionare **Aggiungi un'autorizzazione** per aggiungere una nuova autorizzazione. 

9. Nella pagina **Richiedi le autorizzazioni dell'API** selezionare **Intune** e quindi selezionare **Autorizzazioni applicazione**. Selezionare solo la casella di controllo per **update_device_attributes** e salvare la nuova autorizzazione.

10. A questo punto, fornire il consenso amministratore per questa app selezionando **Fornisci il consenso amministratore per _\<tenant>_** in alto a sinistra nella pagina **Autorizzazioni API**. Potrebbe essere necessario autenticare nuovamente l'account nella nuova finestra e concedere all'applicazione l'accesso seguendo le istruzioni riportate.  

11. Aggiornare la pagina facendo clic sul pulsante **Aggiorna** nella parte superiore della pagina. Verificare che sia stato concesso il consenso dell'amministratore per l'autorizzazione **update_device_attributes**. 

12. Dopo la registrazione corretta dell'app, le autorizzazioni API devono contenere solo un'autorizzazione denominata **update_device_attributes** e devono essere visualizzate come segue:

   ![Autorizzazioni corrette](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   Il processo di registrazione dell'app in Azure AD è stato completato.

    > [!NOTE]
    > Se il segreto client scade, è necessario crearne uno nuovo in Azure e quindi aggiornare i dati di accesso condizionale in Jamf Pro. Per evitare interruzioni del servizio, Azure consente di mantenere attivi sia il segreto precedente sia la nuova chiave.

### <a name="enable-intune-to-integrate-with-jamf-pro"></a>Abilitare Intune per l'integrazione con Jamf Pro

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Gestione dei dispositivi partner**.

3. Abilitare il *connettore per la conformità per Jamf* incollando l'ID dell'applicazione salvato durante la procedura precedente nel campo **Specify the Azure Active Directory App ID for Jamf** (ID app di Azure Active Directory per Jamf).

4. Selezionare **Salva**.

### <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurare l'integrazione di Microsoft Intune in Jamf Pro

1. Attivare la connessione nella console di Jamf Pro:

   1. Aprire la console di Jamf Pro e passare a **Gestione globale** > **Accesso condizionale**. Fare clic sul pulsante **Edit** (Modifica) nella scheda **macOS Intune Integration** (Integrazione con Intune per macOS).
   2. Selezionare la casella di controllo **Enable Intune Integration for macOS** (Abilita integrazione con Intune per macOS).
   3. Fornire le informazioni necessarie sul tenant di Azure, tra cui **Percorso**, **Nome di dominio**, **ID applicazione** e il valore del *segreto client* salvato quando è stata creata l'app in Azure AD.
   4. Selezionare **Salva**. Jamf Pro testerà le impostazioni e ne verificherà la correttezza.

   Per completare la configurazione, tornare alla pagina **Gestione dei dispositivi partner** in Intune.

2. In Intune passare alla pagina **Gestione dei dispositivi partner**. In **impostazioni del connettore** configurare i gruppi per l'assegnazione:

   - Selezionare **Includi** e specificare i gruppi di utenti di destinazione per la registrazione di macOS con Jamf.
   - Usare **Escludi** per selezionare i gruppi di utenti che non verranno registrati con Jamf e registreranno i propri Mac direttamente con Intune.

   *Escludi* sostituisce *Includi*, quindi qualsiasi dispositivo presente in entrambi i gruppi viene escluso da Jamf e indirizzato alla registrazione con Intune.

   >[!NOTE]
   > Questo metodo di inclusione ed esclusione dei gruppi di utenti influisce sull'esperienza di registrazione dell'utente. Tutti gli utenti con un Mac già registrato in Jamf o Intune che in seguito vengono destinati alla registrazione con l'altra MDM devono annullare la registrazione del dispositivo e quindi ripeterla con la nuova MDM affinché la gestione del dispositivo funzioni correttamente.

3. Selezionare **Valuta** per determinare il numero di dispositivi che verranno registrati con Jamf, in base alle configurazioni del gruppo.

4. Selezionare **Salva** quando si è pronti ad applicare la configurazione.

5. Per continuare, sarà necessario usare [Jamf per distribuire il Portale aziendale per Mac](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) in modo che gli utenti possano registrare i propri dispositivi in Intune.

## <a name="set-up-compliance-policies-and-register-devices"></a>Impostare i criteri di conformità e registrare i dispositivi

Dopo aver configurato l'integrazione tra Intune e Jamf, è necessario [applicare i criteri di conformità per i dispositivi gestiti da Jamf](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Disconnettere Jamf Pro e Intune

Se non si usa più Jamf Pro per gestire i computer Mac nell'organizzazione e si vuole che gli utenti siano gestiti da Intune, è necessario rimuovere la connessione tra Jamf Pro e Intune. Rimuovere la connessione usando la console di Jamf Pro.

1. In Jamf Pro passare a **Global Management** >  (Gestione globale) **Conditional Access** (Accesso condizionale). Nella scheda **macOS Intune Integration** (Integrazione con Intune per macOS) selezionare **Edit** (Modifica).

2. Deselezionare la casella di controllo **Enable Intune Integration for macOS** (Abilita integrazione con Intune per macOS).

3. Selezionare **Salva**. Jamf Pro invia la configurazione a Intune e l'integrazione verrà terminata.

4. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Gestione dei dispositivi partner** per verificare che lo stato ora sia **Terminato**.

   > [!NOTE]
   > I dispositivi Mac dell'organizzazione verranno rimossi alla data visualizzata nella console (3 mesi).

## <a name="next-steps"></a>Passaggi successivi

- [Applicare criteri di conformità a dispositivi gestiti da Jamf](conditional-access-assign-jamf.md)
- [Dati inviati da Jamf a Intune](data-jamf-sends-to-intune.md)
