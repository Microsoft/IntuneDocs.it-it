---
# required metadata

title: Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili con Microsoft Intune
Questo argomento descrive i passaggi precedenti la creazione dei criteri di gestione delle app per dispositivi mobili (MAM) nel portale di Azure.

Il portale di Azure è la nuova console di amministrazione per la creazione di criteri MAM. È consigliabile usare questo portale per creare criteri MAM. Il portale di Azure supporta gli scenari MAM seguenti:
- Dispositivi registrati in Intune
- Dispositivi gestiti da una soluzione MDM di terze parti
- Dispositivi non gestiti da nessuna soluzione MDM (BYOD).

Se non si ha familiarità con l'uso del portale di Azure, leggere l'argomento [Azure portal for Microsoft Intune MAM policies (Portale di Azure per i criteri MAM di Microsoft Intune)](azure-portal-for-microsoft-intune-mam-policies.md) per una breve panoramica.

Se si usa la **console di amministrazione di Intune** per la gestione dei dispositivi, è possibile creare criteri MAM che supportano le app per i dispositivi registrati in Intune usando la **console di amministrazione di Intune**, ma è consigliabile usare il portale di Azure anche per i dispositivi registrati in Intune. Per istruzioni su come creare criteri MAM usando la console di amministrazione di Intune, fare clic [qui](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

>[!IMPORTANT]
> È possibile che nella console di amministrazione di Intune non vengano visualizzate tutte le impostazioni dei criteri MAM. Se si creano criteri MAM sia nella console di amministrazione di Intune che nel portale di Azure, i criteri di quest'ultimo vengono applicati alle app e distribuiti agli utenti.


##  Piattaforme supportate
- iOS 8.1 o versioni successive

- Android 4 o versioni successive

I dispositivi Windows non sono attualmente supportati.
##  App supportate
* **App Microsoft:** queste app includono Intune App SDK e non richiedono alcuna elaborazione aggiuntiva per l'applicazione dei criteri MAM.
Per visualizzare l'elenco completo delle app Microsoft supportate, passare alla [raccolta di applicazioni per dispositivi mobili di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) nella pagina dei partner di Microsoft Intune. Fare clic sull'app per visualizzare gli scenari e le piattaforme supportate e per verificare se l'app supporta identità multiple.
* **App line-of-business create internamente:** è necessario preparare l'app per includere Intune App SDK prima di applicare i criteri MAM.

  * Per i dispositivi gestiti da Intune, vedere [Decide how to prepare apps for MAM (Decidere come preparare le app per MAM)](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).
  * Per i dispositivi non gestiti, ad esempio i dispositivi personali dei dipendenti, o per i dispositivi gestiti da una soluzione di gestione dei dispositivi mobili di terze parti, vedere [Protect line of business apps and data on devices not enrolled in Intune (Proteggere le app line-of-business e i dati su dispositivi non registrati in Intune)](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

**Prima** di poter configurare i criteri MAM, è necessario:

-   Avere una **sottoscrizione a Microsoft Intune**.    Gli utenti finali devono avere le licenze di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per ottenere le app con i criteri MAM.

-   Avere una sottoscrizione **Office 365 (O365)**, necessaria per le operazioni seguenti:
  - Applicare i criteri MAM alle app con supporto di più identità.
  - Creare account aziendali di SharePoint Online ed Exchange Online. Exchange locale e SharePoint locale non sono supportati.
-    **Abilitare l'autenticazione moderna** per **Skype for Business Online**. Accedere a Microsoft Connect e riempire [questo modulo](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) per la registrazione al programma dell'autenticazione moderna.


- Usare **Azure Active Directory (Azure AD)** per creare utenti. Azure AD autentica l'utente quando l'utente finale avvia l'app e immette le credenziali aziendali.

    > [!NOTE] Se si stanno impostando utenti che usano la console di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], tenere presente che la configurazione dei criteri MAM in futuro verrà trasferita nel portale di Azure e che, per usare questo portale, è necessario impostare i gruppi di utenti di Azure AD tramite il portale di Office 365.


## Creare utenti e assegnare le licenze di Microsoft Intune

1. È necessario avere una sottoscrizione di Intune: si dispone già di una sottoscrizione di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] se si sta già usando [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per gestire i dispositivi.  La sottoscrizione di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] è già disponibile anche se è stata acquistata una licenza EMS. Se si sta provando [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per testare le funzionalità MAM, è possibile ottenere un account di valutazione [qui](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/).

    Per verificare se si ha già una sottoscrizione di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], accedere alla pagina Fatturazione nel portale di Office.  [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] dovrebbe essere visualizzato come **Attivo** nella sezione delle sottoscrizioni.

2.  Accedere al   [portale di Office](http://portal.office.com) con le credenziali di amministratore.

3.  Accedere alla pagina **Utenti attivi** per aggiungere utenti e assegnare licenze di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Pagina del portale di Office per aggiungere utenti](../media/AppManagement/OfficePortal_AddUsers.png)

4.  Per consentire a un utente di accedere al portale di Office, al portale di Azure AD e al portale di Azure, assegnare il **ruolo Amministratore globale** all'utente.

    ![Screenshot del portale di Office che illustra la pagina Utenti attivi ](../media/AppManagement/OfficePortal_AddRoletoUser.png)

5.  I criteri MAM vengono distribuiti ai gruppi di utenti in Azure Active Directory. Per creare i gruppi di utenti da usare per i criteri MAM, accedere alla pagina **Gruppi** nel **portale di Office** e fare clic sull'icona **+** per creare un nuovo gruppo di sicurezza.  Digitare un nome e una descrizione e fare clic su **Crea**. Quando viene creato il gruppo, è possibile aggiungere utenti al gruppo facendo clic su **Modifica appartenenza** nel gruppo di sicurezza appena creato. Il gruppo di sicurezza viene creato in Azure Active Directory.

    ![Screenshot della pagina che visualizza la selezione del ruolo dell'amministratore globale nella pagina di modifica dei ruoli utente](../media/AppManagement/OfficePortal_CreateGroups.png)

La tabella seguente elenca ruoli e autorizzazioni che possono essere assegnati agli utenti amministratori.

|||
|--|----|
|**Ruolo**|**Autorizzazioni**|
|Amministratore globale (portale di O365)|Accesso al portale di Office 365 e al portale di Azure AD<br /><br />Accesso al portale di Azure (può eseguire sia la gestione dei ruoli che le attività di gestione per le app per dispositivi mobili).|
|Ruolo di proprietario (portale di Azure)|Accesso al portale di Azure (può eseguire sia la gestione dei ruoli che le attività di gestione per le app per dispositivi mobili).|
|Ruolo di collaboratore (portale di Azure)|Accesso al portale di Azure (può eseguire solo le attività di gestione di app per dispositivi mobili).|

## Assegnare il ruolo di collaboratore a un utente

Gli **amministratori globali** hanno accesso al [portale di Azure](https://portal.azure.com).  Se si vuole che altri utenti amministratori siano in grado di configurare i criteri ed eseguire altre attività di gestione di app per dispositivi mobili, è possibile assegnare il **ruolo di collaboratore** all'utente, come descritto di seguito:


1.  Nel pannello **Impostazioni** fare clic su **Utenti** nella sezione **Gestione risorse**.

    ![Screenshot del pannello Utenti nel portale di Azure](../media/AppManagement/AzurePortal_MAM_AddUsers.png)

2.  Fare clic su **Aggiungi** per aprire il pannello **Aggiungi accesso** .

3.  Fare clic su **Selezionare un ruolo**, quindi sul **ruolo Collaboratore**.

    ![Screenshot del pannello Selezionare un ruolo nel portale di Azure](../media/AppManagement/AzurePortal_MAM_AddRole.png)

4.  Dopo aver selezionato il ruolo, fare clic su **Aggiungi utente**e cercare l'utente in base all'indirizzo di posta elettronica o al nome utente. Gli utenti visualizzati in questo elenco sono i primi 1000 utenti creati in precedenza in Azure AD tramite il portale di Office. Fare clic su **OK** sul pannello **Aggiungi accesso** per salvare e assegnare il ruolo all'utente.

    ![Screenshot del pannello Aggiungi utenti nel portale di Azure](../media/AppManagement/AzurePortal_MAM_AddusertoRole.png)

    > [!IMPORTANT] Se è stato selezionato un utente cui non è associata una licenza di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], tale utente non riuscirà ad accedere al portale.

## Passaggi successivi
[Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


