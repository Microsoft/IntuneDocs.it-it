---
# required metadata

title: Prepararsi alla registrazione dei dispositivi | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Prepararsi alla registrazione dei dispositivi in Microsoft Intune
Per consentire ai dipendenti di registrare i dispositivi mobili, inclusi i dispositivi [Android](set-up-android-management-with-microsoft-intune.md), [iOS e Mac](set-up-ios-and-mac-management-with-microsoft-intune.md), [Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md) e i [PC Windows](set-up-windows-device-management-with-microsoft-intune.md), in Intune è necessario abilitare la registrazione dei dispositivi. Per consentire la registrazione è necessario impostare un'autorità di gestione dei dispositivi mobili, configurare il portale aziendale di Intune, assegnare le licenze e abilitare la registrazione per la piattaforma del dispositivo.

## <a name="BKMK_Set_MDM_Authority"></a>Impostare l'autorità di gestione dei dispositivi mobili
Questa autorità definisce il servizio di gestione con le autorizzazioni per la gestione di un set di dispositivi. L'autorità di gestione di dispositivi mobili (MDM) prevede due opzioni: l'uso di Intune da solo e l'uso di Configuration Manager con Intune. Se Configuration Manager è impostato come autorità di gestione, non è possibile usare altri servizi per la gestione dei dispositivi mobili.

>[!IMPORTANT]
> Valutare attentamente se gestire i dispositivi mobili usando solo Intune (servizio online) o System Center Configuration Manager con Intune (soluzione software locale in combinazione con un servizio online). Dopo l'impostazione, l'autorità di gestione del dispositivo mobile non può essere modificata.



1.  Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dispositivi mobili**.

2.  Nell'elenco **Attività** fare clic su **Imposta autorità di gestione dei dispositivi mobili**. Verrà visualizzata la finestra di dialogo **Imposta autorità MDM** .

    ![Finestra di dialogo Imposta autorità MDM](../media/intune-mdm-authority.png)

3.  Intune richiede di confermare che si vuole usare Intune come autorità di gestione dei dispositivi mobili. Selezionare la casella e quindi scegliere **Sì** per usare Microsoft Intune per la gestione dei dispositivi mobili.

## Configurare il Portale aziendale di Intune
La personalizzazione del portale aziendale consente di offrire agli utenti finali un'esperienza familiare e utile. A tale scopo, accedere alla [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) come amministratore tenant o del servizio, scegliere **Amministrazione** &gt; **Portale aziendale** e configurare le impostazioni del Portale aziendale.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_setup.png)

#### Informazioni di contatto e informativa sulla privacy della società
Il nome dell'azienda viene visualizzato come titolo del portale aziendale. I dettagli e le informazioni di contatto vengono visualizzati agli utenti nella schermata Contatta l'IT del portale aziendale. L'informativa sulla privacy viene visualizzata quando un utente fa clic sul relativo collegamento.

|Nome del campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |Nome società|40|È il nome che verrà visualizzato come titolo del portale aziendale.|
    |Nome contatto del reparto IT|40|Questo nome viene visualizzato nella pagina **Contatta l'IT**.|
    |Numero di telefono del reparto IT|20|Questo numero di contatto viene visualizzato nella pagina **Contatta l'IT**.|
    |Indirizzo di posta elettronica del reparto IT|40|Questo indirizzo di contatto viene visualizzato nella pagina **Contatta l'IT**. È necessario immettere un indirizzo di posta elettronica valido nel formato **alias@nomedominio.com**.|
    |Informazioni aggiuntive|120|Visualizzato nella pagina **Contatta l'IT**|
    |URL dell'informativa sulla privacy dell'azienda|79|È possibile indicare l'informativa sulla privacy della propria azienda che verrà visualizzata quando gli utenti fanno clic sui collegamenti relativi alla privacy dal portale aziendale. Immettere un URL valido nel formato https://www.contoso.com.|

#### Contatti del supporto tecnico
Il sito di assistenza viene visualizzato agli utenti nel portale aziendale in modo da consentire l'accesso all'assistenza online.

|Nome del campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |URL sito Web del supporto tecnico|150|Se si dispone di un sito Web di supporto che si desidera venga usato dagli utenti, è necessario specificare qui l'URL. Il formato dell'URL deve essere https://www.contoso.com. Se non si specifica un URL, non verrà visualizzato alcun valore nella pagina **Contatta l'IT** del portale aziendale.|
    |Nome sito Web|40|Questo è il nome descrittivo visualizzato per l'URL del sito Web del supporto tecnico. Se si specifica solo un URL del sito Web e nessun nome descrittivo, nella pagina **Contatta l'IT** del portale aziendale verrà visualizzato **Vai al sito Web IT**.|

## Personalizzazione del branding aziendale
È possibile personalizzare il portale aziendale con logo, nome dell'azienda, colore del tema e sfondo.

|Nome del campo|Altre informazioni|
    |----------|----------------|
    |Colore del tema|Selezionare un colore del tema da applicare al portale aziendale.|
    |Includere il logo aziendale|Quando si attiva questa opzione, è possibile caricare il logo aziendale da visualizzare nel portale aziendale. È possibile caricare due loghi: uno che verrà visualizzato quando lo sfondo del portale è bianco e uno che verrà visualizzato quando lo sfondo del portale aziendale usa il colore del tema selezionato. Ogni logo deve essere un file con estensione jpg o png, avere una risoluzione massima di 400 x 100 pixel e una dimensione massima di 750 KB.|
    |Scegliere uno sfondo per l'app Portale aziendale di [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]|Questa impostazione influisce sullo sfondo solo per l'app Portale aziendale di [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)].|


Una volta salvate le modifiche, è possibile usare i collegamenti riportati in fondo alla pagina **Portale aziendale** della console di amministrazione per visualizzare il sito Web del portale aziendale. Questi collegamenti non possono essere modificati. Quando un utente esegue l'accesso, questi collegamenti visualizzano le sottoscrizioni nel portale aziendale.



## Assegnare una licenza utente di Intune

Usare il **[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]** per aggiungere manualmente gli utenti basati su cloud e assegnare licenze ad account utente basati su cloud e account sincronizzati da Active Directory locale ad Azure AD.

1.  Accedere al [portale per gli account Intune](https://portal.office.com/Admin/Default.aspx) usando le credenziali di amministratore tenant.

2.  Selezionare l'account utente a cui si desidera assegnare la licenza e la licenza utente di Intune, quindi abilitare la casella di controllo **Microsoft Intune** nelle proprietà dell'account utente.

3.  L'account utente verrà ora aggiunto al gruppo di utenti di Microsoft Intune che concede le autorizzazioni per usare il servizio e registrare i dispositivi nella gestione.

## Impostare la gestione dei dispositivi
Dopo aver impostato l'autorità MDM, è necessario impostare la gestione dei dispositivi per i sistemi operativi che l'organizzazione vuole supportare. I passaggi necessari per configurare la gestione dei dispositivi variano a seconda del sistema operativo. Ad esempio, il sistema operativo Android non richiede di eseguire alcuna operazione nella console di amministrazione di Intune. Windows e iOS invece richiedono una relazione di trust tra i dispositivi e Intune per consentire la gestione.

> [!div class="op_single_selector"]
- [Configurare la gestione per Android con Microsoft Intune](set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Impostare la gestione di Windows Phone con Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md)
- [Configurare la gestione dei dispositivi Windows con Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md)

È inoltre possibile:
 - Usare [l'account manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) per registrare più dispositivi
 - [Specificare i dispositivi di proprietà dell'azienda con i numeri IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) per registrare i dispositivi e i criteri di destinazione


<!--HONumber=Jun16_HO1-->


