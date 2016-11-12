---
title: App iOS con criteri MAM | Microsoft Intune
description: "Questo argomento descrive cosa accade quando l&quot;app iOS è gestita da criteri di gestione delle app mobili."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 3f9d9c7cafcdac0db21e5ba35f713fe630c65b99


---

# Aspettative dalla gestione dell'app per iOS con criteri MAM
 Questo argomento descrive l'esperienza dell'utente finale con le app con criteri MAM. I criteri di gestione delle applicazioni mobili (MAM, Mobile Application Management) vengono applicati solo quando le app vengono usate nel contesto di lavoro, ad esempio nei casi di accesso alle app con l'account aziendale o di accesso ai file archiviati nel percorso OneDrive aziendale.
##  Accesso alle app

Se il dispositivo **non è registrato in Intune**, all'utente finale verrà chiesto di riavviare l'app la prima volta che la usa.  Il riavvio è necessario per consentire l'applicazione dei criteri MAM all'app. Lo screenshot seguente illustra questo aspetto tramite l'app Skype:


![screenshot di un dispositivo iOS con la richiesta del PIN](../media/appmanagement/iOS_AppPINPrompt.png)

Per i dispositivi **registrati per la gestione in Intune**, l'utente finale riceverà il messaggio che l'app è ora gestita dalla società:

![schermata del dispositivo iOS con il messaggio relativo alla gestione da parte della società e la richiesta del PIN](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  Uso di app con supporto di più identità

I criteri MAM vengono applicati al contesto di lavoro solo quando si usa l'app. Il comportamento delle diverse app quindi può essere diverso a seconda del contesto, di lavoro o personale.  

Per le app che supportano più identità, Intune applica i criteri MAM solo quando l'utente finale usa l'app nel contesto di lavoro.  Ad esempio, l'utente finale riceverà la richiesta di inserimento del PIN al momento di accedere ai dati di lavoro.  Per l'**app Outlook**, all'utente finale viene richiesto il PIN all'avvio dell'app. Per l'**app OneDrive** ciò si verifica quando l'utente finale digita l'account aziendale.  Per Microsoft **Word**, **PowerPoint* ed **Excel**, ciò si verifica quando l'utente finale accede ai documenti archiviati nel percorso OneDrive for Business.
##  Gestione degli account utente nel dispositivo

Intune supporta solo la distribuzione di criteri MAM a un unico account utente per dispositivo.

* A seconda dell'applicazione che si usa, è possibile scegliere di bloccare o meno il secondo utente del dispositivo. In ogni caso, sarà tuttavia interessato dai criteri MAM solo il primo utente che ottiene i criteri.
  * **Microsoft Word**, **Excel** e **PowerPoint** non bloccano un secondo account utente. Questo account utente non sarà tuttavia interessato dai criteri MAM.  

  * Per le app **OneDrive e Outlook**, è possibile usare un solo account aziendale.  L'aggiunta di più account aziendali è bloccata in queste app.  È tuttavia possibile rimuovere un utente e aggiungere un altro utente sul dispositivo.

* Se prima della distribuzione dei criteri MAM, un dispositivo ha più di un account utente, il primo account che riceve la distribuzione dei criteri MAM sarà gestito dai criteri MAM di Intune.


Per capire meglio come vengono gestiti gli account utente multipli, leggere lo scenario di esempio riportato sotto.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri MAM. L'**Azienda X** distribuisce i criteri MAM **prima dell'****Azienda Y**. L'account associato all'**Azienda X** otterrà i criteri MAM, a differenza dell'account associato all'Azienda Y. Se si vuole che l'account utente associato all'Azienda Y sia gestito con i criteri MAM, è necessario rimuovere l'utente associato all'Azienda X.
### Aggiunta di un secondo account

Se si usa un dispositivo iOS, quando si prova ad aggiungere un secondo account aziendale nello stesso dispositivo potrebbe essere visualizzato un messaggio di blocco.  Verranno visualizzati gli account e sarà possibile scegliere l'account da rimuovere.

![Schermata della finestra di dialogo con il messaggio di blocco e le opzioni Sì e No](../media/AppManagement/iOS_SwitchUser.PNG)
## Passaggi successivi
[Aspettative dalla gestione dell'app per Android con criteri MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### Vedere anche
[Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


