---
title: Impostare VPN per app in Microsoft Intune su dispositivi iOS
titleSuffix: Intune on Azure
description: Specificare quali app gestite possono usare la VPN nei dispositivi iOS gestiti da Intune.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/5/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f7e53f9a440d945d834c17b9db85ed5f6e42229
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="set-up-per-app-vpn-in-microsoft-intune-for-ios-devices"></a>Impostare VPN per app in Microsoft Intune su dispositivi iOS

È possibile specificare quali app gestite possono usare la rete privata virtuale (VPN) nei dispositivi iOS gestiti da Intune. Quando si specifica una VPN per app in Intune, l'utente finale si connette automaticamente tramite la VPN durante l'accesso ai documenti aziendali.

## <a name="prerequisites-for-the-per-app-vpn"></a>Prerequisiti per VPN per app

Per dimostrare la propria identità, il server VPN presenta il certificato che deve essere accettato senza prompt da parte del dispositivo. Per garantire l'approvazione automatica del certificato, è possibile creare un profilo certificato attendibile con un certificato radice del server VPN emesso dalla CA. 

Esportare il certificato e aggiungere la CA.

1. Aprire la console di amministrazione nel server VPN.
2. Verificare che il server VPN utilizzi l'autenticazione basata sui certificati. 
3. Esportare il file relativo al certificato radice attendibile. Si tratta di un file CER da aggiungere durante la creazione di un profilo di un certificato attendibile.
4. Aggiungere il nome della CA che ha emesso il certificato di autenticazione per il server VPN.
    Se l'autorità di certificazione presentata dal dispositivo corrisponde a una CA presente nell'elenco di CA attendibili del server VPN, allora il server VPN autentica il dispositivo.

## <a name="create-a--group-for-your-vpn-users"></a>Creare un gruppo per gli utenti VPN

Creare o scegliere un gruppo esistente in Azure Active Directory (Azure AD) per includere i membri che hanno accesso a VPN per app.

1. Aprire il portale di Azure. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
2. Scegliere **Gruppi** e fare clic su **Nuovo gruppo**.
3. Immettere il **Nome** del gruppo. 
4. Specifica la **Descrizione** del gruppo. 
5. Selezionare **Assegnato** per **Tipo di appartenenza**.
6. Selezionare **No** per**Enable Office features** (Abilitare le funzionalità di Office).
7. Cercare gli utenti VPN per nome o indirizzo di posta nel pannello **Membri**.
8. Selezionare ogni utente e fare clic su **Seleziona**.
9. Fare clic su **Crea**

## <a name="create-a-trusted-certificate-profile"></a>Creare un profilo certificato attendibile

Importare il certificato di radice del server VPN rilasciato dalla CA in un profilo creato in Intune. Il profilo certificato attendibile indica al dispositivo iOS di considerare attendibile automaticamente la CA che il server VPN presenta.

1. Aprire il portale di Azure. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
2. Scegliere **Configurazione del dispositivo** e poi fare clic su **Profili**.
3. Fare clic su **+ Crea profilo**. In **Crea profilo**:
    1. Immettere il **Nome**.
    2. Immettere la **Descrizione**.
    3. Selezionare **iOS** per **Piattaforma**.
    4. Selezionare **Certificato attendibile** per il **Tipo profilo**.
4. Fare clic sull'icona della cartella e individuare il certificato VPN (file CER) esportato dalla console di amministrazione di VPN. Scegliere OK
5. Scegliere **Crea**.

    ![Creare un profilo certificato attendibile](media\vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-certificate-profile"></a>Creare un profilo certificato SCEP

Il profilo del certificato radice attendibile consente a iOS di considerare automaticamente attendibile il Server VPN. Il certificato SCEP specifica le credenziali dal client VPN iOS al server VPN. Il certificato permette l'autenticazione del dispositivo iOS senza che l'utente debba inserire nome utente e password. 

1. Aprire il portale di Azure. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**. 
2. Scegliere **Configurazione del dispositivo** e poi fare clic su **Profili**.
3. Fare clic su **+ Crea profilo**. In **Crea profilo**:
    1. Immettere il **Nome**.
    2. Immettere la **Descrizione**.
    3. Selezionare **iOS** per **Piattaforma**.
    4. Selezionare **Certificato SCEP** per il **Tipo profilo**.
4. Selezionare **Anni** e tipo `2` per **periodo di validità del certificato**.
5. Selezionare **Nome comune** per **formato nome soggetto**.
6. Selezionare **UPN** per **Nome alternativo soggetto**.
7. Selezionare **Firma digitale** e **Crittografia chiave** per **Utilizzo chiave**.
8. Selezionare **2048** per **Dimensioni chiave (bit)**.
9. Selezionare un certificato radice e un certificato SCEP. Fare clic su **OK**.
10. Immettere `Client Authentication` in **nome** per **Utilizzo chiave avanzato**.
11. Immettere `1.3.6.1.5.5.7.3.2` in **Identificatore dell'oggetto**.
12. Fare clic su **Aggiungi**.
13. Immettere l'***URL del Server*** e fare clic su **Aggiungi**.
14. Fare clic su **OK**.
15. Scegliere **Crea**.

    ![Creare un profilo certificato SCEP](media\vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Creare un Profilo VPN per app

Il profilo VPN contiene il certificato SCEP con le credenziali del client, le informazioni di connessione per la connessione VPN e il flag Per VPN APP per abilitare la funzionalità di VPN Per App per l'utilizzo da parte dell'applicazione iOS.

1. Aprire il portale di Azure. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
2. Scegliere **Configurazione del dispositivo** e poi fare clic su **Profili**.
3. Fare clic su **+ Crea profilo**. In **Crea profilo**:
    1. Immettere il **Nome**.
    2. Immettere la **Descrizione**.
    3. Selezionare **iOS** per **Piattaforma**.
    4. Selezionare **VPN** per il **Tipo profilo**.
4. Selezionare **VPN di base**. In **VPN di base**:
    1. Immettere il **Nome connessione**.
    2. Immettere **Indirizzo IP o FQDN**.
    3. Selezionare **Certificati** per il **Metodo di autenticazione**.
    4. Selezionare il certificato SCEP in **Certificato di autenticazione** e fare clic su **OK**.
    5. Selezionare la rete VPN per **Tipo di connessione**.
    6. Se necessario, configurare gli attributi per la VPN.
    7. Selezionare **Disable Split** (Disabilita Split) tunneling.
5. Click **VPN automatica**. In **VPN automatica**:
    1. Selezionare **VPN Per App** per il **Tipo di VPN automatica**.
    2. Digitare l'URL per la VPN e fare clic su **Aggiungi**.
    3. Fare clic su **OK**.
6. Fare clic su **OK**.
7. Scegliere **Crea**.

    ![Creare un Profilo VPN per app](media\vpn-per-app-create-vpn-profile.png)


## <a name="associate-an-app-with-the-vpn-profile"></a>Associare un'applicazione con il profilo VPN

Dopo aver aggiunto il profilo VPN, associare l'app e il gruppo di Azure AD per il profilo.

1. Aprire il portale di Azure. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
2. Scegliere **App per dispositivi mobili**.
3. Fare clic su **Applicazioni**.
4. Selezionare l'app dall'elenco delle app.
5. Fare clic **Assegnazioni.**
6. Fare clic su **Seleziona gruppi**, selezionare il gruppo definito in precedenza. Fare clic su **Seleziona**.
7. Nel pannello **Assegnazioni** selezionare **Required** (Obbligatorio) in **Tipo**.
8. Selezionare la definizione VPN per le reti **VPN**.
 
    > [!NOTE]  
    > In alcuni casi la definizione VPN può richiedere alcuni minuti per recuperare il valore. Attendere 3-5 minuti prima di fare clic su **Salva**.

9. Fare clic su **Save**.

    ![Associare un'applicazione alla VPN](media\vpn-per-app-app-to-vpn.png)

## <a name="verify-the-connection-on-the-ios-device"></a>Verificare la connessione al dispositivo iOS

Con la VPN per app configurata e associata all'app, verificare da un dispositivo che la connessione funzioni.

### <a name="before-you-attempt-to-connect"></a>Prima di provare a connettersi

 - Verificare che sia in esecuzione iOS 7 o una versione successiva.
 - Verificare di implementare *tutti* i criteri citati allo stesso gruppo di utenti. In caso contrario l'esperienza di VPN per app sarà sicuramente interrotta.  
 - Verificare che sia installata l'app VPN di terze parti supportata. Sono supportate le seguenti VPN:
    - Pulse Secure
    - Checkpoint
    - F5
    - SonicWall

### <a name="connect-using-the-per-app-vpn"></a>Connessione mediante VPN per app

Verificare l'esperienza completamente automatica effettuando la connessione senza dover selezionare la VPN o digitare le credenziali. Con l'esperienza completamente automatica:

 - il dispositivo non richiede di considerare attendibile il server VPN. Vale a dire, verrà visualizzata la finestra di dialogo **Dynamic Trust** (Trust dinamico).
 - non è necessario digitare le credenziali.
 - la connessione alla VPN sarà attiva dopo aver fatto clic sul pulsante Connetti.

Verificare la connessione dei dispositivi iOS.

1. Toccare l'app VPN.
2. Toccare **Connetti**.  
La VPN si connette senza prompt aggiuntivi.

<!-- ## Troubleshooting the Per-App VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Passaggi successivi

- Per le impostazioni iOS, vedere [VPN settings for iOS devices in Microsoft Intune](vpn-settings-ios.md) (Impostazioni VPN per dispositivi iOS in Microsoft Intune).
-  Per altre informazioni sulle impostazioni VPN e Intune, vedere [Come configurare le impostazioni VPN in Microsoft Intune](vpn-settings-configure.md).