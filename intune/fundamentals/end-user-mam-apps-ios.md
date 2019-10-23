---
title: App iOS con criteri di protezione delle app
description: Questo argomento descrive cosa accade quando l'app iOS è gestita in base ai criteri di protezione delle app.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 807b33867d827415165eb65d81b91683830735f5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502863"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

 Questo argomento descrive l'esperienza utente nell'uso di app a cui sono applicati i criteri di protezione delle app. I criteri di protezione delle app vengono applicati solo alle app usate in un contesto aziendale, ad esempio quando l'utente accede alle app con un account aziendale o accede ai file archiviati in una posizione di OneDrive for Business.

## <a name="access-apps"></a>Accedere alle app

Se il dispositivo **non è registrato in Intune**, all'utente verrà chiesto di riavviare l'app la prima volta che la usa. Il riavvio è necessario per consentire l'applicazione dei criteri di protezione all'app.

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Per i dispositivi **registrati per la gestione in Intune**, l'utente riceve un messaggio in cui viene segnalato che l'app è gestita.

## <a name="use-apps-with-multi-identity-support"></a>Usare app con supporto di più identità

Le app che supportano identità multiple consentono di usare account differenti, aziendale e personale, per accedere alle stesse app, mentre i criteri di protezione delle app vengono applicati solo quando le app vengono usate nel contesto aziendale.  

Ad esempio, l'utente riceve la richiesta di inserimento del PIN al momento di accedere ai dati di lavoro. Per l'**app Outlook**, all'utente viene richiesto un PIN all'avvio dell'app. Per l'**app OneDrive**, all'utente viene richiesto un PIN all'inserimento dell'account aziendale.  Per **Microsoft Word**, **PowerPoint** ed **Excel**, all'utente viene richiesto un PIN quando accede ai documenti archiviati nel percorso OneDrive for Business dell'azienda.

- Altre informazioni sulle app che supportano la [protezione delle app e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

I criteri di protezione delle app si applicano solo in un contesto aziendale. Di conseguenza, l'app potrebbe comportarsi in modo diverso a seconda che il contesto sia aziendale o personale.

## <a name="manage-user-accounts-on-the-device"></a>Gestire gli account utente nel dispositivo

Le applicazioni con identità multiple permettono agli utenti di aggiungere più account.  L'APP Intune supporta un solo account gestito.  L'APP Intune non limita il numero di account non gestiti.

Quando in un'applicazione è presente un account gestito:
* Se un utente prova ad aggiungere un secondo account gestito, gli viene chiesto di selezionare quale account gestito usare.  L'altro account viene rimosso.
* Se l'amministratore IT aggiunge criteri a un secondo account esistente, all'utente viene chiesto di selezionare quale account gestito usare.  L'altro account viene rimosso.

Per capire meglio come vengono gestiti gli account utente multipli, leggere lo scenario di esempio seguente.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri di protezione delle app. L'**Azienda X** distribuisce i criteri di protezione delle app **prima dell'** **Azienda Y**. L'account associato all'**Azienda X** ottiene per primo i criteri di protezione dell'app. Se si vuole che l'account utente associato all'Azienda Y venga gestito dai criteri di protezione delle app, è necessario rimuovere l'account utente associato all'Azienda X e aggiungere l'account utente associato all'Azienda Y.

### <a name="add-a-second-account"></a>Aggiungere un secondo account

Se si usa un dispositivo iOS, quando si prova ad aggiungere un secondo account aziendale in tale dispositivo potrebbe essere visualizzato un messaggio di blocco. Verranno visualizzati gli account e sarà quindi possibile scegliere l'account da rimuovere.

## <a name="next-steps"></a>Passaggi successivi
[Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](end-user-mam-apps-android.md)
