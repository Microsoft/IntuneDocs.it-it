---
title: Prerequisiti per la registrazione dei dispositivi mobili | Microsoft Intune
description: Configurare i prerequisiti per la gestione di dispositivi mobili (MDM) e prepararsi alla registrazione di diversi sistemi operativi.
keywords: 
author: NathBarn
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
ms.sourcegitcommit: 77c8df8f1886786a2e772429d93b034798b22a66
ms.openlocfilehash: 8c500a5bfd59f801d1177a681fa9d55d1aa1ee0e


---

# Prerequisiti per la gestione dei dispositivi mobili in Intune
È possibile consentire ai dipendenti di registrare i propri dispositivi mobili con Intune mediante la procedura seguente. Questi stessi passaggi sono necessari per gestire i dispositivi di proprietà dell'azienda.

|Passaggi|Dettagli|  
|-----------|-------------|  
|**Passaggio 1:** [dipendenze della registrazione del dispositivo](#step-1-device-enrollment-dependencies)|Assicurarsi che il nome di dominio personalizzato sia configurato e che la comunicazione di rete sia predisposta|  
|**Passaggio 2:** [impostare l'autorità di gestione del dispositivo](#step-2-set-mobile-device-management-authority)|L'autorità di gestione dei dispositivi mobili definisce il servizio assegnato ai dispositivi|
|**Passaggio 3:** [configurare il portale aziendale di Intune](#step-3-configure-the-intune-company-portal)|Configurare le impostazioni utente per l'app del portale aziendale|  
|**Passaggio 4:** [assegnare le licenze utente di Intune](#step-4-assign-intune-user-licenses)|Assegnare le licenze Intune agli utenti in modo che possano registrare i dispositivi|
|**Passaggio 5:** [impostare la gestione dei dispositivi](#step-5-set-up-device-management)|Abilitare le impostazioni specifiche della piattaforma per la gestione di Windows e iOS. Per i dispositivi Android non è necessaria alcuna configurazione aggiuntiva.|

Si sta cercando Intune con Configuration Manager?
> [!div class="button"]
[Visualizza i documenti SCCM >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## Passaggio 1: dipendenze della registrazione del dispositivo

Prima di abilitare la registrazione dei dispositivi mobili, assicurarsi di aver eseguito le operazioni seguenti:
- [Esaminare le porte e gli URL di rete richiesti](../get-started/network-infrastructure-requirements-for-microsoft-intune)
- [Aggiungere e verificare il nome di dominio](../get-started/domain-names-for-microsoft-intune)

## Passaggio 2: impostare l'autorità di gestione dei dispositivi mobili
Questa autorità definisce il servizio di gestione autorizzato a gestire un set di dispositivi. L'autorità di gestione di dispositivi mobili (MDM) prevede due opzioni: l'uso di Intune da solo e l'uso di Configuration Manager con Intune. Se Configuration Manager è impostato come autorità di gestione, non è possibile usare altri servizi per la gestione dei dispositivi mobili.

>[!IMPORTANT]
> Valutare attentamente se gestire i dispositivi mobili usando solo Intune (servizio online) o System Center Configuration Manager con Intune (soluzione software locale in combinazione con il servizio online). Dopo l'impostazione, l'autorità di gestione dei dispositivi mobili non può essere modificata.



1.  Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dispositivi mobili**.

2.  Nell'elenco **Attività** fare clic su **Imposta autorità di gestione dei dispositivi mobili**. Verrà visualizzata la finestra di dialogo **Imposta autorità MDM** .

    ![Finestra di dialogo Imposta autorità MDM](../media/intune-mdm-authority.png)

3.  Intune richiede di confermare che si vuole usare Intune come autorità di gestione dei dispositivi mobili. Selezionare la casella di controllo e quindi scegliere **Sì** per usare Microsoft Intune per la gestione dei dispositivi mobili.

## Passaggio 3: configurare il portale aziendale di Intune

Il Portale aziendale di Intune è il punto in cui gli utenti possono accedere ai dati aziendali ed eseguire attività comuni quali la registrazione dei dispositivi, l'installazione di app e la ricerca delle informazioni di assistenza del reparto IT.

> [!TIP]
> Quando si personalizza il portale aziendale, le configurazioni vengono applicate sia al sito Web che alle app Portale aziendale.

La personalizzazione del Portale aziendale consente di offrire agli utenti finali un'esperienza familiare e utile. A tale scopo, accedere alla [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) come amministratore tenant o del servizio, scegliere **Amministrazione** &gt; **Portale aziendale** e configurare le impostazioni del Portale aziendale.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### Informazioni di contatto e informativa sulla privacy della società

Il nome dell'azienda viene visualizzato come titolo del portale aziendale. I dettagli e le informazioni di contatto vengono visualizzati agli utenti nella schermata Contatta l'IT del portale aziendale. L'informativa sulla privacy viene visualizzata quando un utente fa clic sul relativo collegamento.

|Nome campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |Nome società|40|È il nome che verrà visualizzato come titolo del portale aziendale. **Nota**: solo caratteri alfanumerici. Questo campo non supporta i caratteri speciali.|
    |Nome contatto del reparto IT|40|Questo nome viene visualizzato nella pagina **Contatta l'IT**.|
    |Numero di telefono del reparto IT|20|Questo numero di contatto viene visualizzato nella pagina **Contatta l'IT**.|
    |Indirizzo di posta elettronica del reparto IT|40|Questo indirizzo di contatto viene visualizzato nella pagina **Contatta l'IT**. È necessario immettere un indirizzo di posta elettronica valido nel formato **alias@nomedominio.com**.|
    |Informazioni aggiuntive|120|Queste informazioni vengono visualizzate nella pagina **Contatta l'IT**.|
    |URL dell'informativa sulla privacy dell'azienda|79|È possibile indicare l'informativa sulla privacy della propria azienda che verrà visualizzata quando gli utenti fanno clic sui collegamenti relativi alla privacy dal portale aziendale. Immettere un URL valido nel formato https://www.contoso.com.|

### Contatti del supporto tecnico
Il sito di assistenza viene visualizzato agli utenti nel portale aziendale in modo da consentire l'accesso all'assistenza online.

|Nome del campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |URL sito Web del supporto tecnico|150|Se si dispone di un sito Web di supporto che si desidera venga usato dagli utenti, è necessario specificare qui l'URL. Il formato dell'URL deve essere https://www.contoso.com. Se non si specifica un URL, non verrà visualizzato alcun valore nella pagina **Contatta l'IT** del portale aziendale.|
    |Nome sito Web|40|Questo è il nome descrittivo visualizzato per l'URL del sito Web del supporto tecnico. Se si specifica solo un URL del sito Web e nessun nome descrittivo, nella pagina **Contatta l'IT** del portale aziendale verrà visualizzato **Vai al sito Web IT**.|


### Personalizzazione del branding aziendale

È possibile personalizzare il Portale aziendale con il logo aziendale, il nome della società, un colore del tema e uno sfondo.

|Nome campo|Altre informazioni|
    |----------|----------------|
    |Colore del tema|Selezionare un colore del tema da applicare al portale aziendale.|
    |Includere il logo aziendale|Quando si attiva questa opzione, è possibile caricare il logo aziendale da visualizzare nel portale aziendale. È possibile caricare due loghi: uno che verrà visualizzato quando lo sfondo del portale è bianco e uno che verrà visualizzato quando lo sfondo del portale aziendale usa il colore del tema selezionato. Ogni logo deve essere un file con estensione jpg o png, avere una risoluzione massima di 400x100 pixel e una dimensione massima di 750 KB.|
    |Scegliere uno sfondo per l'app portale aziendale|Questa impostazione influisce solo sullo sfondo dell'app portale aziendale.|


Dopo aver salvato le modifiche, è possibile usare i collegamenti riportati in fondo alla pagina **Portale aziendale** della console di amministrazione per visualizzare il sito Web del Portale aziendale. Questi collegamenti non possono essere modificati. Quando un utente esegue l'accesso, questi collegamenti visualizzano le sottoscrizioni nel portale aziendale.

## Passaggio 4: assegnare le licenze utente di Intune

Usare il **portale di gestione di Office 365** per aggiungere manualmente gli utenti basati su cloud e assegnare licenze sia ad account utente basati su cloud sia ad account sincronizzati da Active Directory locale a Azure Active Directory (Azure AD). È possibile [sincronizzare gli utenti locali con Azure AD](../get-started/domain-names-for-microsoft-intune#to-synchronize-on-premises-users-with-azure-ad.md).

1.  Accedere al [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) usando le credenziali di amministratore tenant.

2.  Selezionare l'account utente a cui si vuole assegnare una licenza utente di Intune e quindi selezionare la casella di controllo **Microsoft Intune** nelle proprietà dell'account utente.

3.  L'account utente verrà ora aggiunto al gruppo di utenti di Microsoft Intune, che concede le autorizzazioni per usare il servizio e registrare i dispositivi per la gestione.

### Per sincronizzare gli utenti locali con Azure AD

1. [Aggiungere il suffisso UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) per il dominio personalizzato in Active Directory locale.
2. Impostare il nuovo suffisso UPN per gli utenti locali da importare.
3. Eseguire la [sincronizzazione di Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) per integrare gli utenti locali con Azure AD.
4. Dopo la sincronizzazione delle informazioni degli account utente è possibile assegnare licenze di Microsoft Intune usando il [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx).

## Passaggio 5: impostare la gestione dei dispositivi
Dopo aver configurato l'autorità MDM, è necessario impostare la gestione dei dispositivi per i sistemi operativi che l'organizzazione vuole supportare. I passaggi necessari per configurare la gestione dei dispositivi variano a seconda del sistema operativo. Ad esempio, per il sistema operativo Android non è necessario eseguire alcuna operazione nella console di amministrazione di Intune. Windows e iOS invece richiedono una relazione di trust tra i dispositivi e Intune per consentire la gestione.

Configurare la gestione per le piattaforme seguenti:
- [Android](set-up-android-management-with-microsoft-intune.md)
- [iOS e Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [PC e portatili Windows](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows 10 Mobile e Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

È inoltre possibile:
 - Usare l'[account del manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) per registrare numerosi dispositivi.
 - [Specificare i dispositivi aziendali con i numeri IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) per registrare i dispositivi e i criteri di destinazione.



<!--HONumber=Oct16_HO2-->


