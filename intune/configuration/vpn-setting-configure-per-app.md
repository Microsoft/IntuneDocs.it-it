---
title: Configurare una VPN per app per dispositivi iOS/iPadOS in Microsoft Intune - Azure | Microsoft Docs
description: Vedere i prerequisiti, creare un gruppo per gli utenti della rete privata virtuale (VPN), aggiungere un profilo certificato SCEP, configurare un profilo VPN per app e assegnare alcune app al profilo VPN in Microsoft Intune in dispositivi iOS/iPadOS. Elenca anche i passaggi per verificare la connessione VPN nel dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd53172a1086f48dc1646e1b8a63de8bec37b934
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512603"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-iosipados-devices-in-intune"></a>Configurare una rete privata virtuale (VPN) per app per dispositivi iOS/iPadOS in Intune

In Microsoft Intune è possibile creare e usare VPN assegnate a un'app. Questa funzionalità è denominata "VPN per app". È necessario scegliere le app gestite che possono usare la VPN nei dispositivi gestiti da Intune. Quando si usa una VPN per app, gli utenti finali si connettono automaticamente tramite VPN per accedere alle risorse aziendali, ad esempio ai documenti.

Questa funzionalità si applica a:

- iOS 9 e versioni successive
- iPadOS 13.0 e versioni successive

Controllare la documentazione del provider della VPN per verificare se la VPN supporta la VPN per app.

Questo articolo illustra come creare un profilo VPN per app e assegnarlo alle app. Seguire questa procedura per creare una semplice esperienza VPN per app per gli utenti finali. Nella maggior parte delle VPN che supportano la VPN per app, l'utente apre un'app e automaticamente si connette alla VPN.

Alcune connessioni VPN prevedono l'autenticazione tramite nome utente e password per la VPN per app. Gli utenti dovranno quindi immettere un nome utente e una password per connettersi alla VPN.

> [!IMPORTANT]
> La VPN per app non è supportata per i profili VPN IKEv2 per iOS/iPadOS.

## <a name="per-app-vpn-with-zscaler"></a>VPN per app con Zscaler

Zscaler Private Access (ZPA) si integra con Azure Active Directory (Azure AD) per l'autenticazione. Quando si usa ZPA, non sono necessari né il profilo del [certificato attendibile](#create-a-trusted-certificate-profile) né il profilo del [certificato SCEP o PKCS](#create-a-scep-or-pkcs-certificate-profile) (descritti in questo articolo). Se è stato configurato un profilo VPN per app per Zscaler, l'apertura di una delle app associate non determina la connessione automatica a ZPA. L'utente deve invece accedere prima all'app di Zscaler. L'accesso remoto sarà limitato alle app associate.

## <a name="prerequisites-for-per-app-vpn"></a>Prerequisiti per VPN per app

> [!IMPORTANT]
> Può succedere che il vendor VPN abbia altri requisiti per VPN per app, ad esempio hardware o licenze particolari. Controllare la relativa documentazione e soddisfare tali prerequisiti prima di configurare VPN per app in Intune.

Per dimostrare la propria identità, il server VPN presenta il certificato che deve essere accettato senza prompt da parte del dispositivo. Per confermare l'approvazione automatica del certificato, creare un profilo del certificato attendibile che contiene un certificato radice del server VPN emesso dall'Autorità di certificazione (CA). 

### <a name="export-the-certificate-and-add-the-ca"></a>Esportare il certificato e aggiungere la CA

1. Nel server VPN aprire la console di amministrazione.
2. Confermare che il server VPN usi l'autenticazione basata sui certificati. 
3. Esportare il file relativo al certificato radice attendibile. Si tratta di un file CER da aggiungere durante la creazione di un profilo di un certificato attendibile.
4. Aggiungere il nome della CA che ha emesso il certificato di autenticazione per il server VPN.

    Se l'autorità di certificazione presentata dal dispositivo corrisponde a una CA presente nell'elenco di CA attendibili del server VPN, allora il server VPN autenticherà il dispositivo.

## <a name="create-a-group-for-your-vpn-users"></a>Creare un gruppo per gli utenti VPN

Creare o scegliere un gruppo esistente in Azure Active Directory (Azure AD) per gli utenti o i dispositivi che usano la VPN per app. Per creare un nuovo gruppo, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](../fundamentals/groups-add.md).

## <a name="create-a-trusted-certificate-profile"></a>Creare un profilo certificato attendibile

Importare il certificato di radice del server VPN rilasciato dalla CA in un profilo creato in Intune. Il profilo certificato attendibile indica al dispositivo iOS/iPadOS di considerare attendibile automaticamente la CA che il server VPN presenta.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:
    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di profilo valido è **Profilo VPN iOS/iPadOS con certificato attendibile per l'intera azienda**.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: Selezionare **iOS/iPadOS**.
    - **Tipo di profilo**: selezionare **Certificato attendibile**.
4. Selezionare l'icona della cartella e individuare il certificato VPN (file con estensione cer) esportato dalla console di amministrazione della VPN. 
5. Selezionare **OK** > **Crea**.

    ![Creare un profilo certificato attendibile per dispositivi iOS/iPadOS in Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>Creare un profilo del certificato SCEP o PKCS

Il profilo del certificato radice trusted consente al dispositivo di considerare automaticamente attendibile il server VPN. Il certificato SCEP o PKCS specifica le credenziali dal client VPN iOS/iPadOS al server VPN. Il certificato consente l'autenticazione automatica del dispositivo senza che sia necessario immettere un nome utente o una password. 

Per configurare e assegnare il certificato di autenticazione client, vedere uno degli articoli seguenti:

- [Configurare l'infrastruttura per il supporto di SCEP con Intune](../protect/certificates-scep-configure.md)
- [Configurare e gestire i certificati PKCS con Intune](../protect/certficates-pfx-configure.md)

Verificare che il certificato sia configurato per l'autenticazione client. È possibile impostare questa opzione direttamente nei profili del certificato SCEP (elenco **Utilizzo chiavi avanzato** > **Autenticazione client**). Per PKCS, impostare l'autenticazione client nel modello di certificato nella CA.

![Creare un profilo del certificato SCEP in Microsoft Intune che include formato del nome soggetto, utilizzo chiavi, utilizzo chiavi avanzato e così via](./media/vpn-setting-configure-per-app/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Creare un profilo VPN per app

Il profilo VPN contiene il certificato SCEP o PKCS con le credenziali del client, le informazioni di connessione alla VPN e il flag VPN per app per abilitare la funzionalità VPN per app utilizzabile dall'applicazione iOS/iPadOS.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
2. Immettere le proprietà seguenti:
    - **Nome**: Immettere un nome descrittivo per il profilo personalizzato. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di profilo valido è **Profilo VPN iOS/iPadOS per app per l'intera azienda**.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: Selezionare **iOS/iPadOS**.
    - **Tipo di profilo**: selezionare **VPN**.
3. In **Tipo di connessione** selezionare l'app client VPN.
4. Selezionare **VPN di base**. Nella pagina relativa alle [impostazioni VPN iOS/iPadOS](vpn-settings-ios.md) sono elencate e descritte tutte le impostazioni. Quando si usa una VPN per app, assicurarsi che le queste proprietà siano impostate come specificato di seguito:

    - **Metodo di autenticazione**: selezionare **Certificati**. 
    - **Certificato di autenticazione**: selezionare un certificato SCEP o PKCS esistente > **OK**.
    - **Split tunneling**: selezionare **Disabilita** affinché tutto il traffico usi il tunnel VNP quando la connessione VPN è attiva. 

      ![In un profilo VPN per app immettere una connessione, l'indirizzo IP o un FQDN, il metodo di autenticazione e lo split tunneling in Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-vpn-profile.png)

    Per informazioni su altre impostazioni, vedere la pagina relativa alle [impostazioni VPN iOS/iPadOS](vpn-settings-ios.md).

5. Selezionare **VPN automatico** > **Tipo di VPN automatica** > **VPN per app**

    ![In Intune impostare VPN automatico su VPN per app nei dispositivi iOS/iPadOS](./media/vpn-setting-configure-per-app/vpn-per-app-automatic.png)

6. Selezionare **OK** > **OK** > **Crea**.

## <a name="associate-an-app-with-the-vpn-profile"></a>Associare un'applicazione con il profilo VPN

Dopo aver aggiunto il profilo VPN, associare l'app e il gruppo di Azure AD per il profilo.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **App** > **Tutte le app**.
2. Selezionare un'app dall'elenco > **Assegnazioni** > **Aggiungi gruppo**.
3. In **Tipo di assegnazione** selezionare **Obbligatorio** o **Available for enrolled devices** (Disponibile per i dispositivi registrati).
4. Selezionare **Gruppi inclusi** > **Selezionare i gruppi da includere** > selezionare il gruppo [creato](#create-a-group-for-your-vpn-users) (in questo articolo) > **Seleziona**.
5. In **VPN** selezionare il profilo VPN per app [creato](#create-a-per-app-vpn-profile) (in questo articolo).

    ![Assegnare un'app al profilo VPN per app in Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-app-to-vpn.png)

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

## <a name="verify-the-connection-on-the-iosipados-device"></a>Verificare la connessione al dispositivo iOS/iPadOS

Con la VPN per app configurata e associata all'app, verificare da un dispositivo che la connessione funzioni.

### <a name="before-you-attempt-to-connect"></a>Prima di provare a connettersi

- Verificare di implementare tutti i criteri specificati allo stesso gruppo di utenti. In caso contrario, l'esperienza VPN per app non funzionerà.
- Se si usa l'app VPN Pulse Secure o un'app client VPN personalizzata, è possibile scegliere di usare il tunnelling di livello app o di livello pacchetto. Impostare il valore **ProviderType** su **app-proxy** per il tunneling di livello app e su **packet-tunnel** per il tunneling di livello pacchetto. Controllare la documentazione del provider della VPN per assicurarsi di usare il valore corretto.

### <a name="connect-using-the-per-app-vpn"></a>Connessione mediante VPN per app

Verificare l'esperienza completamente automatica effettuando la connessione senza dover selezionare la VPN o digitare le credenziali. Con l'esperienza completamente automatica:

- Il dispositivo non richiede di considerare attendibile il server VPN. Non verrà quindi visualizzata la finestra di dialogo **Dynamic Trust** (Trust dinamico).
- Non è necessario digitare le credenziali.
- Il dispositivo dell'utente si connette alla VPN all'apertura di una delle app associate.

## <a name="next-steps"></a>Passaggi successivi

- Per esaminare le impostazioni per iOS/iPadOS, vedere [Impostazioni VPN per dispositivi iOS/iPadOS in Microsoft Intune](vpn-settings-ios.md).
- Per altre informazioni sulle impostazioni VPN e Intune, vedere la pagina relativa alla [configurazione delle impostazioni VPN in Microsoft Intune](vpn-settings-configure.md).
