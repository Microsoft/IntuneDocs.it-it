---
title: "Novità | Documentazione Microsoft"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2fdf4086ccf4b4f256596b7d0f7192b70a4efd2a
ms.openlocfilehash: a2f3eab11f208c0260dc4dbc245801416dc36633


---
# <a name="whats-new-in-microsoft-intune---january-2017"></a>Novità di Microsoft Intune - Gennaio 2017
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

> [!Note]
> Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

<!--### Actions for non-compliance <!--730266
_Actions for non-compliance_ is a new feature of compliance policies that lets you take action on devices that are out of compliance. You can specify single or multiple actions and specify the time period at which those actions must occur. For example, you can notify users of non-compliant devices immediately after the devices become non-compliant through email, or you can block non-compliant devices from accessing corporate resources after a 3-day grace period via Conditional Access.-->

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Report nella console per MAM senza registrazione <!--677961-->
Sono stati aggiunti nuovi report relativi alla protezione delle app, sia per i dispositivi registrati che per quelli non registrati. Per altre informazioni in merito, vedere [Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

<!--### Conditional access for MAM with SharePoint Online <!--679339
You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint Online.  You can get started using Intune mobile app management in the Azure portal. Look for the __Conditional Access__ section in the __Settings__ blade which will include the option for SharePoint Online. This feature will ship separately from the rest of the service release. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Supporto per Android 7.1.1 <!--694397-->
Intune ora supporta completamente Android 7.1.1 e la relativa gestione.

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Risolvere il problema nel caso in cui i dispositivi iOS non sono attivi o la console di amministrazione non è in grado di comunicare con i dispositivi

Quando i dispositivi degli utenti perdono la connessione con Intune è possibile indicare nuovi passaggi per la risoluzione dei problemi per ripristinare l'accesso alle risorse aziendali. Vedere [I dispositivi sono inattivi o la console di amministrazione non è in grado di comunicare con i dispositivi](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="notices"></a>Notifiche

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>La gestione dei dispositivi desktop Windows avviene per impostazione predefinita tramite le impostazioni di Windows <!--663050-->
Il comportamento predefinito per la registrazione dei computer desktop di Windows 10 sta cambiando. Per le nuove registrazioni verrà usato il flusso di registrazione dell'agente MDM tipico anziché tramite l'agente per PC.

Il sito Web del portale aziendale fornirà agli utenti di desktop Windows 10 istruzioni per la registrazione, che consentono di eseguire in modo guidato il processo di aggiunta di computer desktop Windows 10 come dispositivi mobili. Ciò non influirà su PC già registrati e l'organizzazione può comunque decidere di gestire i desktop Windows 10 con l'agente per PC, [se preferibile](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

<!--### Company Portal for iOS links open inside the app <!--665954
Links inside of the Company Portal app for iOS, including those to documentation and apps, will open directly in the Company Portal app using an in-app view of Safari. This update will ship separately from the service update in January.-->

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Miglioramento del supporto della gestione delle app per dispositivi mobili per la cancellazione selettiva <!--581242-->
Gli utenti finali riceveranno ulteriori indicazioni su come riottenere l'accesso ai dati aziendali o dell'istituto di istruzione se i dati vengono rimossi automaticamente a causa del criterio "Intervallo offline (giorni) prima della cancellazione dei dati dell'app".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nuova documentazione per i criteri di protezione delle app <!--583398-->
È stata aggiornata la documentazione per gli amministratori e gli sviluppatori di app che vogliono abilitare i criteri di protezione delle app (noti come criteri MAM) nelle loro app iOS e Android usando lo strumento di wrapping delle app di Intune o Intune App SDK.

Sono stati aggiornati gli articoli seguenti:

* [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Preparare le app per iOS per la gestione delle app mobili con lo strumento di wrapping delle app di Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Introduzione a Microsoft Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Manuale dello sviluppatore di Intune App SDK per iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Gli articoli seguenti sono stati aggiunti alla raccolta della documentazione:

* [Plug-in Cordova per Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Componente Xamarin per Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

<!--### Progress bar when launching the Company Portal on iOS <!--665978
The Company Portal for iOS is introducing a progress bar on the launch screen to provide the user with information about the loading processes that occur. There will be a phased rollout of the progress bar to replace the spinner. This means that some of your users will see the new progress bar while others will continue to see the spinner.-->

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novità dell'anteprima pubblica dell'esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

Per qualsiasi domanda in merito alla tempistica per la migrazione del tenant, contattare il team Microsoft responsabile della migrazione all'indirizzo [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

Le novità dell'anteprima di Intune in Azure sono descritte [qui](https://docs.microsoft.com/intune-azure/introduction/whats-new).

### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novità dell'anteprima di Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Archivio delle novità](whats-new-archive.md)



<!--HONumber=Jan17_HO2-->


