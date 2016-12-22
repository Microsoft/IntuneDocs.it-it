---
title: Prerequisiti per i criteri MAM| Microsoft Intune
description: "Questo argomento descrive i prerequisiti e la modalità di configurazione degli utenti per creare i criteri di gestione di app mobili."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: ac820146d81fb121a60f7029f6a52a0056d6ab0a


---

# <a name="get-ready-to-configure-mobile-app-management-policies-on-the-azure-portal"></a>Preparazione alla configurazione dei criteri di gestione di app per dispositivi mobili nel Portale di Azure
Questo argomento descrive i prerequisiti e i passaggi da completare **prima** di poter creare criteri MAM (Mobile App Management, Gestione delle app mobili) nel portale di Azure.

Per capire come i criteri MAM in Intune possono proteggere i dati aziendali, vedere [Proteggere app e dati usando i criteri di gestione delle app mobili](protect-apps-and-data-with-microsoft-intune.md).

## <a name="what-is-the-azure-portal"></a>Introduzione al portale di Azure

Il portale di Azure è la nuova console di amministrazione per la creazione dei criteri MAM. Supporta gli scenari MAM seguenti:
- Dispositivi registrati in Intune
- Dispositivi gestiti da un'altra soluzione di Gestione dei dispositivi mobili (MDM)
- Dispositivi non gestiti da alcuna soluzione MDM (BYOD)

Attualmente, la **console di amministrazione di Intune** e il **portale di Azure** consentono di configurare criteri MAM.  Considerare quanto segue:

* I criteri creati nel **portale di Azure** sono supportati per **tutti gli scenari MAM** elencati in precedenza. La **console di amministrazione di Intune** supporta solo la creazione di criteri per **i dispositivi registrati e gestiti da Intune**.

* Potrebbe non essere possibile visualizzare tutte le impostazioni dei criteri MAM nella console di amministrazione di Intune perché le **nuove impostazioni** possono essere aggiunti solo nel **portale di Azure**.

* Se si creano criteri MAM nella console di amministrazione di Intune e nel portale di Azure, i criteri **del portale vengono applicati alle app e distribuiti agli utenti**.
    * I criteri MAM creati nella console di amministrazione di Intune non possono essere importati nel portale di Azure.  Tali criteri devono essere ricreati nel portale di Azure.


* Altre **funzionalità di gestione di app**, ad esempio la distribuzione di app e di criteri di configurazione delle app, sono attualmente disponibili solo nella **console di amministrazione di Intune**.


Se non si ha familiarità con l'uso del portale di Azure, leggere [Portale di Azure per i criteri MAM di Microsoft Intune](azure-portal-for-microsoft-intune-mam-policies.md) per una breve panoramica sull'uso del portale di Azure.

Per istruzioni su come creare un criterio MAM usando la console di amministrazione di Intune, vedere [Configurare e distribuire criteri di gestione delle applicazioni mobili nella console di Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).


##  <a name="supported-platforms"></a>Piattaforme supportate
- iOS 8.1 o versioni successive
- Android 4 o versioni successive

>[!NOTE]
>I dispositivi Windows non supportano i criteri di gestione delle applicazioni per dispositivi mobili. Tuttavia, quando si registrano i dispositivi di Windows 10 con Intune, è possibile usare Windows Information Protection, che offre funzionalità simili. Per altre informazioni, vedere [Proteggere i dati aziendali con Windows Information Protection (WIP)](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

##  <a name="supported-apps"></a>App supportate
* **App Microsoft:** queste app includono Intune App SDK e non richiedono alcuna elaborazione aggiuntiva per l'applicazione dei criteri MAM.
Per visualizzare l'elenco completo delle app Microsoft supportate, passare alla [raccolta di applicazioni mobili di Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) nella pagina dei partner di app di Microsoft Intune. Fare clic su un'app per visualizzare le piattaforme e gli scenari supportati e per verificare se l'app supporta più identità.

* **App line-of-business create internamente:** è necessario preparare queste app per includere Intune App SDK prima di applicare i criteri MAM.

  * Per i dispositivi gestiti da Intune, vedere [Decide how to prepare apps for MAM (Decidere come preparare le app per MAM)](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

  * Per i dispositivi non gestiti, ad esempio i dispositivi personali dei dipendenti, o per i dispositivi gestiti da un'altra soluzione di gestione dei dispositivi mobili, vedere [Proteggere app e dati line-of-business su dispositivi non registrati in Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

## <a name="prerequisites"></a>Prerequisiti

-   **Sottoscrizione di Microsoft Intune**. Gli utenti devono avere le licenze di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per ottenere app con criteri MAM.
Si dispone già di una sottoscrizione di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] se si usa [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per gestire i dispositivi. Si dispone di una sottoscrizione di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] anche nel caso in cui sia stata acquistata una licenza di Enterprise Mobility Suite (EMS). Se si sta provando [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per testare le funzionalità MAM, è possibile ottenere un account di valutazione nella [pagina di Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/).

    Per verificare se si ha già una sottoscrizione di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], accedere alla pagina **Fatturazione** nel portale di Office.  Se si ha una sottoscrizione, [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] dovrebbe essere visualizzata come **Attivo** nella sezione delle sottoscrizioni.

-   Avere un **abbonamento a Office 365**, necessario per le operazioni seguenti:

  - Applicare criteri MAM alle app con supporto per più identità.

  - Creare account aziendali di SharePoint Online ed Exchange Online. Exchange locale e SharePoint locale non sono supportati.

-   **Configurazione di Skype for Business Online per l'autenticazione moderna**. Per altre informazioni, vedere [Enable modern authentication (Abilitare l'autenticazione moderna)](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) per creare utenti. Azure AD esegue l'autenticazione quando gli utenti aprono l'app e immettono le credenziali di lavoro.

    > [!NOTE]
    > I gruppi di utenti devono essere impostati in Azure AD. I gruppi utenti di Intune non possono essere usati per distribuire criteri MAM nel portale di Azure.

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>Creare utenti e assegnare le licenze di Microsoft Intune

1.  Accedere al [portale di Office](http://portal.office.com) con le credenziali di amministratore.

2.  Aggiungere utenti come descritto nella sezione **Passaggi per completare una valutazione di 30 giorni di Intune** della [Guida alla valutazione di Intune](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) e quindi assegnare le licenze Intune. Per consentire a un utente di accedere al portale di Office, al portale di Azure AD e al portale di Azure, assegnare all'utente il ruolo **Amministratore globale**.

5.  I criteri MAM vengono distribuiti ai gruppi di utenti in Azure Active Directory. Per creare gruppi di utenti per i criteri MAM, vedere la sezione **Creare un gruppo di utenti** di [Creare gruppi per organizzare utenti e dispositivi della sottoscrizione di valutazione](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3).

### <a name="assign-roles-to-non-global-admin-users"></a>Assegnare ruoli agli utenti amministratori non globali

Gli amministratori globali hanno accesso al [portale di Azure](https://portal.azure.com).  Se si vuole che gli utenti amministratori non globali possano configurare i criteri ed eseguire altre attività di gestione di app mobili, è possibile assegnare a tali utenti il ruolo di collaboratore. Per istruzioni dettagliate, vedere [Usare le assegnazioni di ruolo per gestire l'accesso alle risorse della sottoscrizione di Azure](https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-configure/).



La tabella seguente elenca i ruoli e le autorizzazioni che possono essere assegnati agli utenti amministratori.



|||
|--|----|
|**Ruolo**|**Autorizzazioni**|
|Amministratore globale (portale di Office 365)|Accesso al portale di Office 365 e al portale di Azure AD.<br /><br />Accesso al portale di Azure (può eseguire attività di gestione sia dei ruoli che delle app mobili).|
|Proprietario (portale di Azure)|Accesso al portale di Azure (può eseguire attività di gestione sia dei ruoli che delle app mobili).|
|Collaboratore (portale di Azure)|Accesso al portale di Azure (può eseguire solo le attività di gestione di app mobili).|




## <a name="next-steps"></a>Passaggi successivi
[Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


