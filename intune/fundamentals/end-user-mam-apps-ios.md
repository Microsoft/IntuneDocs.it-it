---
title: App iOS con criteri di protezione delle app
description: Questo argomento descrive cosa accade quando l'app iOS è gestita in base ai criteri di protezione delle app.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606622"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app

I criteri di protezione delle app di Intune si applicano alle app usate per il lavoro o l'istruzione. Ciò significa che quando i dipendenti e gli studenti usano le proprie app in un contesto personale, potrebbero non riscontrare alcuna differenza nell'esperienza. Nel contesto aziendale o dell'istituto di istruzione, tuttavia, potrebbero ricevere richieste per prendere decisioni relative agli account, aggiornarne le impostazioni o contattare l'utente per assistenza. Usare questo articolo per apprendere gli aspetti dell'esperienza degli utenti quando provano ad accedere e usare le app protette da Intune.  

## <a name="access-apps"></a>Accedere alle app

Se il dispositivo **non è registrato in Intune**, all'utente verrà chiesto di riavviare l'app la prima volta che la usa. Per consentire l'applicazione dei criteri di protezione all'app è necessario il riavvio.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Per i dispositivi **registrati per la gestione in Intune**, l'utente riceve un messaggio in cui viene segnalato che l'app è gestita.

## <a name="use-apps-with-multi-identity-support"></a>Usare app con supporto di più identità

Le app che supportano più identità consentono di usare account personali e di lavoro diversi per l'accesso alle stesse app. I criteri di protezione delle app, ad esempio l'immissione di un PIN del dispositivo, vengono attivati quando gli utenti accedono a queste app in un contesto aziendale o di istruzione.   

Gli utenti potrebbero vedere la richiesta di PIN in modo diverso nelle diverse app, a seconda della configurazione dei criteri.  Ad esempio, è possibile configurare i criteri in modo che:       
* Microsoft Outlook richieda un PIN all'avvio dell'app. 
* OneDrive richieda un PIN quando l'utente accede al proprio account aziendale.  
* Microsoft Word, PowerPoint ed Excel richiedano all'utente un PIN quando accede ai documenti archiviati nel percorso OneDrive for Business dell'azienda.  

- Altre informazioni sulle app che supportano la [protezione delle app e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.  

## <a name="manage-user-accounts-on-the-device"></a>Gestire gli account utente nel dispositivo  

I criteri di protezione delle app di Intune limitano gli utenti a un solo account aziendale o dell'istituto di istruzione gestito per app. I criteri di protezione delle app non limitano il numero di account non gestiti che un utente può aggiungere.   

- Se un utente prova ad aggiungere un secondo account gestito, gli viene chiesto di selezionare quale account gestito usare. Se l'utente aggiunge il secondo account, il primo account verrà rimosso.
- Se si aggiungono criteri di protezione a un altro account utente, viene richiesto all'utente di selezionare l'account gestito da usare. L'altro account viene rimosso. 

Alcuni utenti non dispongono dell'opzione per alternare o selezionare account gestiti. L'opzione non è disponibile nei dispositivi che sono:
* Gestiti da Intune  
* Gestiti da soluzioni di gestione della mobilità aziendale di terze parti e configurati con l'impostazione IntuneMAMUPN 

Lo scenario di esempio seguente illustra come vengono gestiti gli account utente multipli.  

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri di protezione delle app. L'**Azienda X** distribuisce i criteri di protezione delle app **prima**  dell'**Azienda Y**. L'account associato all'**Azienda X** ottiene per primo i criteri di protezione dell'app. Se si vuole che l'account utente associato all'Azienda Y venga gestito dai criteri di protezione delle app, è necessario rimuovere l'account utente associato all'Azienda X e aggiungere l'account utente associato all'Azienda Y.  

## <a name="next-steps"></a>Passaggi successivi

[Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](end-user-mam-apps-android.md)
