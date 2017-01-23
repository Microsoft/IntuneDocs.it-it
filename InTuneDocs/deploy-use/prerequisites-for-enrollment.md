---
title: Prerequisiti per la registrazione dei dispositivi mobili | Documentazione Microsoft
description: Configurare i prerequisiti per la gestione di dispositivi mobili (MDM) e prepararsi alla registrazione di diversi sistemi operativi.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 2b7fe00a2f3b289958aa77df5eaffd35de7c8c97


---

# <a name="prerequisites-for-mobile-device-management-in-intune"></a>Prerequisiti per la gestione dei dispositivi mobili in Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

È possibile consentire ai dipendenti di registrare i propri dispositivi mobili con Intune mediante la procedura seguente. Questi stessi passaggi sono necessari per gestire i dispositivi di proprietà dell'azienda.

|Passaggi|Dettagli|  
|-----------|-------------|  
|**Passaggio 1:** [Abilitare le connessioni](#step-1-enable-connections)|Assicurarsi che il nome di dominio personalizzato sia configurato e che la comunicazione di rete sia predisposta|  
|**Passaggio 2:** [Impostare l'autorità MDM](#step-2-set-mdm-authority)|L'autorità di gestione dei dispositivi mobili definisce il servizio assegnato ai dispositivi|
|**Passaggio 3:** [Creare i gruppi](#step-3-create-groups)|Configurare le impostazioni utente per l'app del portale aziendale|  
|**Passaggio 4:** [Configurare il portale aziendale](#step-4-configure-company-portal)|Configurare le impostazioni utente per l'app del portale aziendale|  
|**Passaggio 5:** [Assegnare le licenze utente](#step-5-assign-user-licenses)|Assegnare le licenze Intune agli utenti in modo che possano registrare i dispositivi|
|**Passaggio 6:** [Abilitare la registrazione](#step-6-enable-enrollment)|Abilitare le impostazioni specifiche della piattaforma per la gestione di Windows e iOS. Per i dispositivi Android non è necessaria alcuna configurazione aggiuntiva.|
|**Passaggio 7:** [Fasi successive](#step-7-next-steps)|Abilitare le impostazioni specifiche della piattaforma per la gestione di Windows e iOS. Per i dispositivi Android non è necessaria alcuna configurazione aggiuntiva.|

Si sta cercando Intune con Configuration Manager?
> [!div class="button"]
[Visualizzare i documenti SCCM >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## <a name="step-1-enable-connections"></a>Passaggio 1: Abilitare le connessioni

Prima di abilitare la registrazione dei dispositivi mobili, assicurarsi di aver eseguito le operazioni seguenti:
- [Esaminare le porte e gli URL di rete richiesti](../get-started/network-infrastructure-requirements-for-microsoft-intune.md)
- [Aggiungere e verificare il nome di dominio](../get-started/domain-names-for-microsoft-intune.md)

## <a name="step-2-set-mdm-authority"></a>Passaggio 2: Impostare l'autorità MDM
Questa autorità definisce il servizio di gestione autorizzato a gestire un set di dispositivi. L'autorità di gestione di dispositivi mobili (MDM) prevede due opzioni: l'uso di Intune da solo e l'uso di Configuration Manager con Intune. Se Configuration Manager è impostato come autorità di gestione, non è possibile usare altri servizi per la gestione dei dispositivi mobili.

>[!IMPORTANT]
> Valutare attentamente se gestire i dispositivi mobili usando solo Intune (servizio online) o System Center Configuration Manager con Intune (soluzione software locale in combinazione con il servizio online). Dopo l'impostazione, l'autorità di gestione dei dispositivi mobili non può essere modificata.



1.  Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dispositivi mobili**.

2.  Nell'elenco **Attività** fare clic su **Imposta autorità di gestione dei dispositivi mobili**. Verrà visualizzata la finestra di dialogo **Imposta autorità MDM** .

    ![Finestra di dialogo Imposta autorità MDM](../media/intune-mdm-authority.png)

3.  Intune richiede di confermare che si vuole usare Intune come autorità di gestione dei dispositivi mobili. Selezionare la casella di controllo e quindi scegliere **Sì** per usare Microsoft Intune per la gestione dei dispositivi mobili.

## <a name="step-3-create-groups"></a>Passaggio 3: Creare i gruppi

È possibile creare gruppi di utenti e dispositivi per semplificare la gestione e migliorare l'assegnazione di applicazioni distribuite, criteri e risorse aziendali. [Informazioni su come creare i gruppi](use-groups-to-manage-users-and-devices-with-microsoft-intune.md#create-groups).

## <a name="step-4-configure-company-portal"></a>Passaggio 4: Configurare il portale aziendale

Il Portale aziendale di Intune è il punto in cui gli utenti possono accedere ai dati aziendali ed eseguire attività comuni quali la registrazione dei dispositivi, l'installazione di app e la ricerca delle informazioni di assistenza del reparto IT.

> [!TIP]
> Quando si personalizza il portale aziendale, le configurazioni vengono applicate sia al sito Web che alle app Portale aziendale.

La personalizzazione del Portale aziendale consente di offrire agli utenti finali un'esperienza familiare e utile. A tale scopo, accedere alla [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) come amministratore tenant o del servizio, scegliere **Amministrazione** &gt; **Portale aziendale** e configurare le impostazioni del Portale aziendale.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### <a name="company-contact-information-and-privacy-statement"></a>Informazioni di contatto e informativa sulla privacy della società

Il nome dell'azienda viene visualizzato come titolo del portale aziendale. I dettagli e le informazioni di contatto vengono visualizzati agli utenti nella schermata Contatta l'IT del portale aziendale. L'informativa sulla privacy viene visualizzata quando un utente fa clic sul relativo collegamento.

|Nome campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |Nome società|40|È il nome che verrà visualizzato come titolo del portale aziendale. **Nota**: solo caratteri alfanumerici. Questo campo non supporta i caratteri speciali.|
    |Nome contatto del reparto IT|40|Questo nome viene visualizzato nella pagina **Contatta l'IT**.|
    |Numero di telefono del reparto IT|20|Questo numero di contatto viene visualizzato nella pagina **Contatta l'IT**.|
    |Indirizzo di posta elettronica del reparto IT|40|Questo indirizzo di contatto viene visualizzato nella pagina **Contatta l'IT**. È necessario immettere un indirizzo di posta elettronica valido nel formato **alias@domainname.com**.|
    |Informazioni aggiuntive|120|Queste informazioni vengono visualizzate nella pagina **Contatta l'IT**.|
    |URL dell'informativa sulla privacy dell'azienda|79|È possibile indicare l'informativa sulla privacy della propria azienda che verrà visualizzata quando gli utenti fanno clic sui collegamenti relativi alla privacy dal portale aziendale. Immettere un URL valido nel formato https://www.contoso.com.|

### <a name="support-contacts"></a>Contatti del supporto tecnico
Il sito di assistenza viene visualizzato agli utenti nel portale aziendale in modo da consentire l'accesso all'assistenza online.

|Nome del campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |URL sito Web del supporto tecnico|150|Se si dispone di un sito Web di supporto che si desidera venga usato dagli utenti, è necessario specificare qui l'URL. Il formato dell'URL deve essere https://www.contoso.com. Se non si specifica un URL, non verrà visualizzato alcun valore nella pagina **Contatta l'IT** del portale aziendale.|
    |Nome sito Web|40|Questo è il nome descrittivo visualizzato per l'URL del sito Web del supporto tecnico. Se si specifica solo un URL del sito Web e nessun nome descrittivo, nella pagina **Contatta l'IT** del portale aziendale verrà visualizzato **Vai al sito Web IT**.|


### <a name="company-branding-customization"></a>Personalizzazione del branding aziendale

È possibile personalizzare il Portale aziendale con il logo aziendale, il nome della società, un colore del tema e uno sfondo.

|Nome campo|Altre informazioni|
    |----------|----------------|
    |Colore del tema|Selezionare un colore del tema da applicare al portale aziendale.|
    |Includere il logo aziendale|Quando si attiva questa opzione, è possibile caricare il logo aziendale da visualizzare nel portale aziendale. È possibile caricare due loghi: uno che verrà visualizzato quando lo sfondo del portale è bianco e uno che verrà visualizzato quando lo sfondo del portale aziendale usa il colore del tema selezionato. Ogni logo deve essere un file con estensione jpg o png, avere una risoluzione massima di 400x100 pixel e una dimensione massima di 750 KB.|
    |Scegliere uno sfondo per l'app portale aziendale|Questa impostazione influisce solo sullo sfondo dell'app portale aziendale.|


Dopo aver salvato le modifiche, è possibile usare i collegamenti riportati in fondo alla pagina **Portale aziendale** della console di amministrazione per visualizzare il sito Web del Portale aziendale. Questi collegamenti non possono essere modificati. Quando un utente esegue l'accesso, questi collegamenti visualizzano le sottoscrizioni nel portale aziendale.

## <a name="step-5-assign-user-licenses"></a>Passaggio 5: Assegnare le licenze utente

Usare il **portale di gestione di Office 365** per aggiungere manualmente gli utenti basati su cloud e assegnare licenze sia ad account utente basati su cloud sia ad account sincronizzati da Active Directory locale a Azure Active Directory (Azure AD). È possibile [sincronizzare gli utenti locali con Azure AD](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md#how-to-sync-on-premises-users-with-azure-ad).

1.  Accedere al [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) usando le credenziali di amministratore tenant.

2.  Selezionare l'account utente a cui si vuole assegnare una licenza utente di Intune e quindi selezionare la casella di controllo **Microsoft Intune** nelle proprietà dell'account utente.

3.  L'account utente verrà ora aggiunto al gruppo di utenti di Microsoft Intune, che concede le autorizzazioni per usare il servizio e registrare i dispositivi per la gestione.

### <a name="to-synchronize-on-premises-users-with-azure-ad"></a>Per sincronizzare gli utenti locali con Azure AD

1. [Aggiungere il suffisso UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) per il dominio personalizzato in Active Directory locale.
2. Impostare il nuovo suffisso UPN per gli utenti locali da importare.
3. Eseguire la [sincronizzazione di Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) per integrare gli utenti locali con Azure AD.
4. Dopo la sincronizzazione delle informazioni degli account utente è possibile assegnare licenze di Microsoft Intune usando il [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx).

## <a name="step-6-enable-enrollment"></a>Passaggio 6: Abilitare la registrazione
Dopo aver configurato l'autorità MDM, è necessario impostare la gestione dei dispositivi per i sistemi operativi che l'organizzazione vuole supportare. I passaggi necessari per configurare la gestione dei dispositivi variano a seconda del sistema operativo. Ad esempio, per il sistema operativo Android non è necessario eseguire alcuna operazione nella console di amministrazione di Intune. Windows e iOS invece richiedono una relazione di trust tra i dispositivi e Intune per consentire la gestione.

Configurare la gestione per le piattaforme seguenti:
- [iOS e Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Android](set-up-android-management-with-microsoft-intune.md)
- [Android for Work](set-up-android-for-work.md)
- [PC e portatili Windows](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows 10 Mobile e Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

È anche possibile abilitare la [registrazione di dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md).

## <a name="step-7-next-steps"></a>Passaggio 7: Fasi successive

Ora che la registrazione è abilitata, è necessario configurare la gestione in base alle esigenze dell'azienda. L'elenco seguente include alcune delle opzioni disponibili per la gestione:

- [Distribuire criteri per gestire impostazioni e funzionalità nei dispositivi](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
- [Abilitare l'accesso alle risorse aziendali come posta elettronica, Wi-Fi e VPN](enable-access-to-company-resources-with-microsoft-intune.md)
- [Aggiungere app](add-apps.md) e [distribuire app](deploy-apps.md) nei dispositivi gestiti
- [Creare criteri di conformità dei dispositivi](introduction-to-device-compliance-policies-in-microsoft-intune.md) e [limitare l'accesso in base alla conformità](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


