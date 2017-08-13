---
title: App iOS con criteri di protezione delle app
description: "Questo argomento descrive cosa accade quando l'app iOS è gestita in base ai criteri di protezione delle app."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9e1b11f9bf644b2e92dad0d0281bf11febae622b
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

 Questo argomento descrive l'esperienza utente nell'uso di app a cui sono applicati i criteri di protezione delle app. I criteri di protezione delle app vengono applicati solo alle app usate in un contesto aziendale, ad esempio quando l'utente accede alle app con un account aziendale o accede ai file archiviati in una posizione di OneDrive for Business.

##  <a name="access-apps"></a>Accedere alle app

Se il dispositivo **non è registrato in Intune**, all'utente verrà chiesto di riavviare l'app la prima volta che la usa. Il riavvio è necessario per consentire l'applicazione dei criteri di protezione all'app.

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

Per i dispositivi **registrati per la gestione in Intune**, l'utente riceve un messaggio in cui viene segnalato che l'app è gestita.

##  <a name="use-apps-with-multi-identity-support"></a>Usare app con supporto di più identità

Le app che supportano identità multiple consentono di usare account differenti, aziendale e personale, per accedere alle stesse app, mentre i criteri di protezione delle app vengono applicati solo quando le app vengono usate nel contesto aziendale.  

Ad esempio, l'utente riceve la richiesta di inserimento del PIN al momento di accedere ai dati di lavoro. Per l'**app Outlook**, all'utente viene richiesto un PIN all'avvio dell'app. Per l'**app OneDrive**, all'utente viene richiesto un PIN all'inserimento dell'account aziendale.  Per **Microsoft Word**, **PowerPoint** ed **Excel**, all'utente viene richiesto un PIN quando accede ai documenti archiviati nel percorso OneDrive for Business dell'azienda.

- Altre informazioni sulle app che supportano la [protezione delle app e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

I criteri di protezione delle app si applicano solo in un contesto aziendale. Di conseguenza, l'app potrebbe comportarsi in modo diverso a seconda che il contesto sia aziendale o personale.

##  <a name="manage-user-accounts-on-the-device"></a>Gestire gli account utente nel dispositivo

Intune supporta la distribuzione dei criteri di protezione delle app a un solo account utente per dispositivo.

* A seconda dell'applicazione che si usa, è possibile scegliere di bloccare il secondo utente del dispositivo. In ogni caso, sarà tuttavia interessato dai criteri di protezione delle app solo il primo utente che ottiene i criteri.
  * **Microsoft Word**, **Excel** e **PowerPoint** non bloccano un secondo account utente. Questo account utente non sarà tuttavia interessato dai criteri di protezione delle app.  

  * Per le app **OneDrive** e **Outlook**, è possibile usare un solo account aziendale. Non è possibile aggiungere più account aziendali per queste app. È tuttavia possibile rimuovere un utente e aggiungere un altro utente sul dispositivo.

* Se prima della distribuzione dei criteri di protezione delle app un dispositivo ha più account utente, il primo account che riceve la distribuzione sarà gestito in base ai criteri di protezione delle app di Intune.


Per capire meglio come vengono gestiti gli account utente multipli, leggere lo scenario di esempio seguente.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri di protezione delle app. L'**Azienda X** distribuisce i criteri di protezione delle app **prima dell'****Azienda Y**. L'account associato all'**Azienda X** ottiene i criteri di protezione delle app, a differenza dell'account associato all'Azienda Y. Se si vuole che l'account utente associato all'Azienda Y sia gestito in base ai criteri di protezione delle app, è necessario rimuovere l'account utente associato all'Azienda X.

### <a name="add-a-second-account"></a>Aggiungere un secondo account

Se si usa un dispositivo iOS, quando si prova ad aggiungere un secondo account aziendale in tale dispositivo potrebbe essere visualizzato un messaggio di blocco. Verranno visualizzati gli account e sarà quindi possibile scegliere l'account da rimuovere.

## <a name="next-steps"></a>Passaggi successivi
[Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](end-user-mam-apps-android.md)
