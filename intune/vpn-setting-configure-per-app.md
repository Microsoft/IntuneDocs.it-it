---
title: Configurare una VPN per app per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Vedere i prerequisiti, creare un gruppo per gli utenti della rete privata virtuale (VPN), aggiungere un profilo certificato SCEP, configurare un profilo VPN per app e assegnare alcune app al profilo VPN in Microsoft Intune in dispositivi iOS. Elenca anche i passaggi per verificare la connessione VPN nel dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7609b3a190cacc7b722f408133f6c5f10d96771
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233135"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>Configurare una rete privata virtuale (VPN) per app per dispositivi iOS in Intune

In Microsoft Intune è possibile creare e usare VPN assegnate a un'app. Questa funzionalità è denominata "VPN per app". È necessario scegliere le app gestite che possono usare la VPN nei dispositivi gestiti da Intune. Quando si usa una VPN per app, gli utenti finali si connettono automaticamente tramite VPN per accedere alle risorse aziendali, ad esempio ai documenti.

Questa funzionalità si applica a:

- iOS 9 e versioni successive

Controllare la documentazione del provider della VPN per verificare se la VPN supporta la VPN per app.

Questo articolo illustra come creare un profilo VPN per app e assegnarlo alle app. Seguire questa procedura per creare una semplice esperienza VPN per app per gli utenti finali. Nella maggior parte delle VPN che supportano la VPN per app, l'utente apre un'app e automaticamente si connette alla VPN.

Alcune connessioni VPN prevedono l'autenticazione tramite nome utente e password per la VPN per app. Gli utenti dovranno quindi immettere un nome utente e una password per connettersi alla VPN.

## <a name="per-app-vpn-with-zscaler"></a>VPN per app con Zscaler

Zscaler Private Access (ZPA) si integra con Azure Active Directory (Azure AD) per l'autenticazione. Quando si usa ZPA, non sono necessari né il profilo del [certificato attendibile](#create-a-trusted-certificate-profile) né il profilo del [certificato SCEP o PKCS](#create-a-scep-or-pkcs-certificate-profile) (descritti in questo articolo). Se è stato configurato un profilo VPN per app per Zscaler, l'apertura di una delle app associate non determina la connessione automatica a ZPA. L'utente deve invece accedere prima all'app di Zscaler. L'accesso remoto sarà limitato alle app associate.

## <a name="prerequisites-for-per-app-vpn"></a>Prerequisiti per VPN per app

> [!IMPORTANT]
> Può succedere che il vendor VPN abbia altri requisiti per VPN per app, ad esempio hardware o licenze particolari. Controllare la relativa documentazione e soddisfare tali prerequisiti prima di configurare VPN per app in Intune.

Per dimostrare la propria identità, il server VPN presenta il certificato che deve essere accettato senza prompt da parte del dispositivo. Per confermare l'approvazione automatica del certificato, creare un profilo del certificato attendibile che contiene un certificato radice del server VPN emesso dall'Autorità di certificazione (CA). 

#### <a name="export-the-certificate-and-add-the-ca"></a>Esportare il certificato e aggiungere la CA

1. Nel server VPN aprire la console di amministrazione.
2. Confermare che il server VPN usi l'autenticazione basata sui certificati. 
3. Esportare il file relativo al certificato radice attendibile. Si tratta di un file CER da aggiungere durante la creazione di un profilo di un certificato attendibile.
4. Aggiungere il nome della CA che ha emesso il certificato di autenticazione per il server VPN.

    Se l'autorità di certificazione presentata dal dispositivo corrisponde a una CA presente nell'elenco di CA attendibili del server VPN, allora il server VPN autenticherà il dispositivo.

## <a name="create-a-group-for-your-vpn-users"></a>Creare un gruppo per gli utenti VPN

Creare o scegliere un gruppo esistente in Azure Active Directory (Azure AD) per gli utenti o i dispositivi che usano la VPN per app. Per creare un nuovo gruppo, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](groups-add.md).

## <a name="create-a-trusted-certificate-profile"></a>Creare un profilo certificato attendibile

Importare il certificato di radice del server VPN rilasciato dalla CA in un profilo creato in Intune. Il profilo certificato attendibile indica al dispositivo iOS di considerare attendibile automaticamente la CA che il server VPN presenta.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:
    - **Nome**
    - **Descrizione**
    - **Piattaforma**: selezionare **iOS**.
    - **Tipo di profilo**: selezionare **Certificato attendibile**.
4. Selezionare l'icona della cartella e individuare il certificato VPN (file con estensione cer) esportato dalla console di amministrazione della VPN. 
5. Selezionare **OK** > **Crea**.

    ![Creare un profilo del certificato attendibile per dispositivi iOS in Microsoft Intune](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>Creare un profilo del certificato SCEP o PKCS

Il profilo del certificato radice trusted consente al dispositivo di considerare automaticamente attendibile il server VPN. Il certificato SCEP o PKCS specifica le credenziali dal client VPN iOS al server VPN. Il certificato consente l'autenticazione automatica del dispositivo senza che sia necessario immettere un nome utente o una password. 

Per configurare e assegnare il certificato di autenticazione client, vedere uno degli articoli seguenti:

- [Configurare e gestire i certificati SCEP con Intune](certificates-scep-configure.md)
- [Configurare e gestire i certificati PKCS con Intune](certficates-pfx-configure.md)

Verificare che il certificato sia configurato per l'autenticazione client. È possibile impostare questa opzione direttamente nei profili del certificato SCEP (elenco **Utilizzo chiavi avanzato** > **Autenticazione client**). Per PKCS, impostare l'autenticazione client nel modello di certificato nella CA.

![Creare un profilo del certificato SCEP in Microsoft Intune che include formato del nome soggetto, utilizzo chiavi, utilizzo chiavi avanzato e così via](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Creare un profilo VPN per app

Il profilo VPN contiene il certificato SCEP o PKCS con le credenziali del client, le informazioni di connessione alla VPN e il flag VPN per app per abilitare la funzionalità VPN per app utilizzabile dall'applicazione iOS.

1. In **Intune** selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**. 
2. Immettere le proprietà seguenti: 
    - **Nome**
    - **Descrizione**
    - **Piattaforma**: selezionare **iOS**.
    - **Tipo di profilo**: selezionare **VPN**.
3. In **Tipo di connessione** selezionare l'app client VPN.
4. Selezionare **VPN di base**. Nella pagina relativa alle [impostazioni VPN iOS](vpn-settings-ios.md) sono elencate e descritte tutte le impostazioni. Quando si usa una VPN per app, assicurarsi che le queste proprietà siano impostate come specificato di seguito: 
    
    - **Metodo di autenticazione**: selezionare **Certificati**. 
    - **Certificato di autenticazione**: selezionare un certificato SCEP o PKCS esistente > **OK**.      
    - **Split tunneling**: selezionare **Disabilita** affinché tutto il traffico usi il tunnel VNP quando la connessione VPN è attiva. 

      ![In un profilo VPN per app immettere una connessione, l'indirizzo IP o un FQDN, il metodo di autenticazione e lo split tunneling in Microsoft Intune](./media/vpn-per-app-create-vpn-profile.png)

    Per informazioni su altre impostazioni, vedere la pagina relativa alle [impostazioni VPN iOS](vpn-settings-ios.md).

5. Selezionare **VPN automatico** > **Tipo di VPN automatica** > **VPN per app**

    ![Impostare VPN automatico per VPN per app in dispositivi iOS in Intune](./media/vpn-per-app-automatic.png)

6. Selezionare **OK** > **OK** > **Crea**.

## <a name="associate-an-app-with-the-vpn-profile"></a>Associare un'applicazione con il profilo VPN

Dopo aver aggiunto il profilo VPN, associare l'app e il gruppo di Azure AD per il profilo.

1. In **Intune** selezionare **App client** > **App**.
2. Selezionare un'app dall'elenco > **Assegnazioni** > **Aggiungi gruppo**.
3. In **Tipo di assegnazione** selezionare **Obbligatorio** o **Available for enrolled devices** (Disponibile per i dispositivi registrati).
4. Selezionare **Gruppi inclusi** > **Selezionare i gruppi da includere** > selezionare il gruppo [creato](#create-a-group-for-your-vpn-users) (in questo articolo) > **Seleziona**.
5. In **VPN** selezionare il profilo VPN per app [creato](#create-a-per-app-vpn-profile) (in questo articolo).

    ![Assegnare un'app al profilo VPN per app in Microsoft Intune](./media/vpn-per-app-app-to-vpn.png)

6. Selezionare **OK** > **Salva**.

L'associazione tra un'app e un profilo viene rimossa durante la successiva archiviazione del dispositivo, quando si verificano tutte le condizioni seguenti:

- L'app è con finalità di installazione richiesta.
- Sia il profilo che l'app sono destinati allo stesso gruppo.
- È possibile rimuovere la configurazione VPN per app dall'assegnazione di app.

L'associazione tra un'app e un profilo rimane fino a quando l'utente non richiede una reinstallazione dal portale aziendale, quando si verificano tutte le condizioni seguenti:

- L'app è con finalità di installazione disponibile.
- Sia il profilo che l'app sono destinati allo stesso gruppo.
- L'utente finale ha richiesto l'installazione dell'app dal portale aziendale con la conseguente installazione dell'app e del profilo nel dispositivo.
- È possibile rimuovere o modificare la configurazione VPN per app dall'assegnazione di app.

## <a name="verify-the-connection-on-the-ios-device"></a>Verificare la connessione al dispositivo iOS

Con la VPN per app configurata e associata all'app, verificare da un dispositivo che la connessione funzioni.

### <a name="before-you-attempt-to-connect"></a>Prima di provare a connettersi

 - Verificare di implementare tutti i criteri specificati allo stesso gruppo di utenti. In caso contrario, l'esperienza VPN per app non funzionerà.
 - Se si usa l'app VPN Pulse Secure o un'app client VPN personalizzata, è possibile scegliere di usare il tunnelling di livello app o di livello pacchetto. Impostare il valore **ProviderType** su **app-proxy** per il tunneling di livello app e su **packet-tunnel** per il tunneling di livello pacchetto. Controllare la documentazione del provider della VPN per assicurarsi di usare il valore corretto.

### <a name="connect-using-the-per-app-vpn"></a>Connessione mediante VPN per app

Verificare l'esperienza completamente automatica effettuando la connessione senza dover selezionare la VPN o digitare le credenziali. Con l'esperienza completamente automatica:

 - Il dispositivo non richiede di considerare attendibile il server VPN. Non verrà quindi visualizzata la finestra di dialogo **Dynamic Trust** (Trust dinamico).
 - Non è necessario digitare le credenziali.
 - Il dispositivo dell'utente si connette alla VPN all'apertura di una delle app associate.

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Passaggi successivi

- Per le impostazioni iOS, vedere [VPN settings for iOS devices in Microsoft Intune](vpn-settings-ios.md) (Impostazioni VPN per dispositivi iOS in Microsoft Intune).
- Per altre informazioni sulle impostazioni VPN e Intune, vedere la pagina relativa alla [configurazione delle impostazioni VPN in Microsoft Intune](vpn-settings-configure.md).
