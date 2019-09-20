---
title: Integrare Jamf Pro con Microsoft Intune per la conformità
titleSuffix: Microsoft Intune
description: Usare i criteri di conformità di Microsoft Intune con l'accesso condizionale di Azure Active Directory per proteggere i dispositivi gestiti tramite Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b439067d06cf49a4ff83288e109d1fccd3801106
ms.sourcegitcommit: 3db8af810b95c3a6ed3f8cc00f6ce79076ebb9db
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71012517"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrare Jamf Pro con Intune per la conformità

Si applica a: Intune nel portale di Azure

Le organizzazioni che usano [Jamf Pro](https://www.jamf.com) per gestire i computer Mac degli utenti finali possono adottare i criteri di conformità di Microsoft Intune e l'accesso condizionale di Azure Active Directory per garantire la conformità dei dispositivi presenti nell'organizzazione.

## <a name="prerequisites"></a>Prerequisiti

Per configurare l'accesso condizionale con Jamf Pro, è necessario quanto segue:

- Jamf Pro 10.1.0 o versione successiva
- [App Portale aziendale per macOS](https://aka.ms/macoscompanyportal)
- Dispositivi macOS con OS X 10.11 Yosemite o versioni successive

## <a name="connect-intune-to-jamf-pro"></a>Connettere Intune a Jamf Pro

Per connettere Intune a Jamf Pro:

1. Creare una nuova applicazione in Azure.
2. Abilitare Intune per l'integrazione con Jamf Pro.
3. Configurare l'accesso condizionale in Jamf Pro.

## <a name="create-an-application-in-azure-active-directory"></a>Creare un’applicazione in Azure Active Directory

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

6. Selezionare **Autorizzazioni API** in **Gestione**. Selezionare le autorizzazioni esistenti e quindi selezionare **Rimuovi l'autorizzazione** per eliminarle. È necessario rimuovere le autorizzazioni esistenti quando si aggiunge una nuova autorizzazione. L'applicazione funziona solo se è presente un'unica autorizzazione.  

7. Per assegnare una nuova autorizzazione, selezionare **Aggiungi un'autorizzazione**. Nella pagina **Richiedi le autorizzazioni dell'API** selezionare **Intune** e quindi selezionare **Autorizzazioni applicazione**. Selezionare solo la casella di controllo per **update_device_attributes**.  

   Selezionare **Aggiungi l'autorizzazione** per salvare questa configurazione.  

8. Nella pagina **Autorizzazioni API** selezionare **Concedi consenso amministratore per Microsoft**, quindi selezionare **Sì**.  

   Il processo di registrazione dell'app in Azure AD è stato completato.


    > [!NOTE]
    > Se il segreto client scade, è necessario crearne uno nuovo in Azure e quindi aggiornare i dati di accesso condizionale in Jamf Pro. Per evitare interruzioni del servizio, Azure consente di mantenere attivi sia il segreto precedente sia la nuova chiave.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Abilitare Intune per l'integrazione con Jamf Pro

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e passare a **Microsoft Intune** > **Conformità del dispositivo** > **Gestione dei dispositivi partner**.

2. Abilitare il connettore per la conformità per Jamf incollando l'ID dell'applicazione salvato durante la procedura precedente nel campo **Jamf Azure Active Directory App ID** (ID app di Azure Active Directory per Jamf).

3. Selezionare **Salva**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurare l'integrazione di Microsoft Intune in Jamf Pro

1. In Jamf Pro passare a **Gestione globale** > **Accesso condizionale**. Fare clic sul pulsante **Edit** (Modifica) nella scheda **macOS Intune Integration** (Integrazione con Intune per macOS).

2. Selezionare la casella di controllo **Enable Intune Integration for macOS** (Abilita integrazione con Intune per macOS).

3. Fornire le informazioni necessarie sul tenant di Azure, tra cui **Percorso**, **Nome di dominio**, **ID applicazione** e il valore del *segreto client* salvato quando è stata creata l'app in Azure AD.  

4. Selezionare **Salva**. Jamf Pro testerà le impostazioni e ne verificherà la correttezza.

## <a name="set-up-compliance-policies-and-register-devices"></a>Impostare i criteri di conformità e registrare i dispositivi

Dopo aver configurato l'integrazione tra Intune e Jamf, è necessario [applicare i criteri di conformità per i dispositivi gestiti da Jamf](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Disconnettere Jamf Pro e Intune 

Se non si usa più Jamf Pro per gestire i computer Mac nell'organizzazione e si vuole che gli utenti siano gestiti da Intune, è necessario rimuovere la connessione tra Jamf Pro e Intune. Rimuovere la connessione usando la console di Jamf Pro. 

1. In Jamf Pro passare a **Global Management** >  (Gestione globale) **Conditional Access** (Accesso condizionale). Nella scheda **macOS Intune Integration** (Integrazione con Intune per macOS) selezionare **Edit** (Modifica).
2. Deselezionare la casella di controllo **Enable Intune Integration for macOS** (Abilita integrazione con Intune per macOS).
3. Selezionare **Salva**. Jamf Pro invia la configurazione a Intune e l'integrazione verrà terminata.
4. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Passare a **Microsoft Intune** > **Conformità del dispositivo** > **Gestione dei dispositivi partner** per verificare che ora lo stato sia **Terminato**. 

   > [!NOTE]
   > I dispositivi Mac dell'organizzazione verranno rimossi alla data visualizzata nella console (3 mesi). 

## <a name="next-steps"></a>Passaggi successivi

- [Applicare criteri di conformità a dispositivi gestiti da Jamf](conditional-access-assign-jamf.md)
- [Dati inviati da Jamf a Intune](data-jamf-sends-to-intune.md)
