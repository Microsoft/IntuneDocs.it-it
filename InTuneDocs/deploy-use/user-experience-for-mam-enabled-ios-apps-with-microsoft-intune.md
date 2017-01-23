---
title: App iOS con criteri MAM | Documentazione Microsoft
description: "Questo argomento descrive cosa accade quando l&quot;app iOS è gestita da criteri di gestione delle app mobili."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b068da7685792757825a4bc0d555e28ee0168cb1
ms.openlocfilehash: f5a26d3d5ed060571892d91637dc12cae08f1a69


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-mam-policies"></a>Aspettative dalla gestione dell'app per iOS con criteri MAM

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

 Questo argomento descrive l'esperienza dell'utente finale con le app con criteri di gestione delle app mobili (MAM). I criteri di gestione delle app mobili (MAM, Mobile Application Management) vengono applicati solo quando le app vengono usate nel contesto di lavoro, ad esempio quando l'utente accede alle app con un account aziendale o accede ai file archiviati in un percorso OneDrive aziendale.

##  <a name="access-apps"></a>Accedere alle app

Se il dispositivo **non è registrato in Intune**, all'utente verrà chiesto di riavviare l'app la prima volta che la usa.  Il riavvio è necessario per consentire l'applicazione dei criteri MAM all'app. 

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

Per i dispositivi **registrati per la gestione in Intune**, l'utente riceve il messaggio che l'app è ora gestita dalla società:

![Schermata del dispositivo iOS con il messaggio relativo alla gestione dell'app da parte della società e la richiesta del PIN](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  <a name="use-apps-with-multi-identity-support"></a>Usare app con supporto di più identità

I criteri MAM si applicano solo in un contesto aziendale. Di conseguenza, l'app potrebbe comportarsi in modo diverso a seconda che il contesto sia aziendale o personale.

 Ad esempio, l'utente riceve la richiesta di inserimento del PIN al momento di accedere ai dati di lavoro. Per l'**app Outlook**, all'utente viene richiesto un PIN all'avvio dell'app. Per l'**app OneDrive**, all'utente viene richiesto un PIN all'inserimento dell'account aziendale.  Per **Microsoft Word**, **PowerPoint** ed **Excel**, all'utente viene richiesto un PIN quando accede ai documenti archiviati nel percorso OneDrive for Business dell'azienda.

##  <a name="manage-user-accounts-on-the-device"></a>Gestire gli account utente nel dispositivo

Intune supporta la distribuzione di criteri MAM solo a un unico account utente per dispositivo.

* A seconda dell'applicazione che si usa, è possibile scegliere di bloccare il secondo utente del dispositivo. In ogni caso, sarà tuttavia interessato dai criteri MAM solo il primo utente che ottiene i criteri.
  * **Microsoft Word**, **Excel** e **PowerPoint** non bloccano un secondo account utente. Questo account utente non sarà tuttavia interessato dai criteri MAM.  

  * Per le app **OneDrive** e **Outlook**, è possibile usare un solo account aziendale. Non è possibile aggiungere più account aziendali per queste app. È tuttavia possibile rimuovere un utente e aggiungere un altro utente sul dispositivo.

* Se prima della distribuzione dei criteri MAM, un dispositivo ha più di un account utente, il primo account che riceve la distribuzione dei criteri MAM sarà gestito dai criteri MAM di Intune.


Per capire meglio come vengono gestiti gli account utente multipli, leggere lo scenario di esempio seguente.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri MAM. L'**Azienda X** distribuisce i criteri MAM **prima dell'****Azienda Y**. L'account associato all'**Azienda X** ottiene i criteri MAM, a differenza dell'account associato all'Azienda Y. Se si vuole che l'account utente associato all'Azienda Y sia gestito con i criteri MAM, è necessario rimuovere l'utente associato all'Azienda X.

### <a name="add-a-second-account"></a>Aggiungere un secondo account

Se si usa un dispositivo iOS, quando si prova ad aggiungere un secondo account aziendale in tale dispositivo potrebbe essere visualizzato un messaggio di blocco. Verranno visualizzati gli account e sarà quindi possibile scegliere l'account da rimuovere.

![Schermata della finestra di dialogo con il messaggio di blocco e le opzioni Sì e No](../media/AppManagement/iOS_SwitchUser.PNG)
## <a name="next-steps"></a>Passaggi successivi
[Aspettative dalla gestione dell'app per Android con criteri MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>Vedere anche
[Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


