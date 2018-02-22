---
title: App Android con criteri di protezione delle app
description: "Questo argomento descrive cosa accade quando l'app è gestita in base ai criteri di protezione delle app."
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 738f747c06f8ad7e6deb90908c2b4b653bad63e3
ms.sourcegitcommit: 6d69403266dbcb31c879432719798935c94917fa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Aspettative dalla gestione dell'app per Android con criteri di protezione delle app

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Questo articolo descrive l'esperienza utente per le app con criteri di protezione delle app. I criteri di protezione delle app vengono applicati solo alle app usate in un contesto aziendale, ad esempio quando l'utente accede alle app con un account aziendale o accede a file archiviati in un percorso di OneDrive for Business.

##  <a name="access-apps"></a>Accedere alle app

L'app Portale aziendale è necessaria per tutte le app associate a criteri di protezione delle app in dispositivi Android.

Per i dispositivi non registrati in Intune è necessario installare l'app Portale aziendale nel dispositivo. Tuttavia, l'utente non deve avviare l'app Portale aziendale o accedervi prima di poter usare app gestite tramite criteri di protezione delle app.

L'app Portale aziendale è una modalità con cui Intune condivide i dati in una posizione sicura. Di conseguenza, l'app Portale aziendale è necessaria per tutte le app associate a criteri di protezione delle app, anche se il dispositivo non è registrato in Intune.


##  <a name="use-apps-with-multi-identity-support"></a>Usare app con supporto di più identità

I criteri di protezione delle app si applicano solo in un contesto aziendale. Di conseguenza, l'app potrebbe comportarsi in modo diverso a seconda che il contesto sia aziendale o personale.

Ad esempio, l'utente riceve la richiesta di inserimento del PIN al momento di accedere ai dati di lavoro. Per l'**app Outlook**, all'utente viene richiesto un PIN all'avvio dell'app. Per l'**app OneDrive**, all'utente viene richiesto il PIN all'inserimento dell'account aziendale. Per **Microsoft Word**, **PowerPoint** ed **Excel**, all'utente viene richiesto il PIN quando accede ai documenti archiviati nel percorso OneDrive for Business dell'azienda.

##  <a name="manage-user-accounts-on-the-device"></a>Gestire gli account utente nel dispositivo

Le applicazioni con identità multiple permettono agli utenti di aggiungere più account.  L'APP Intune supporta un solo account gestito.  L'APP Intune non limita il numero di account non gestiti.

Quando in un'applicazione è presente un account gestito:
*   Se un utente prova ad aggiungere un secondo account gestito, gli viene chiesto di selezionare quale account gestito usare.  L'altro account viene rimosso.
*   Se l'amministratore IT aggiunge criteri a un secondo account esistente, all'utente viene chiesto di selezionare quale account gestito usare.  L'altro account viene rimosso.

Per capire meglio come vengono gestiti gli account utente multipli, leggere lo scenario di esempio seguente.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri di protezione delle app. L'**Azienda X** distribuisce i criteri di protezione delle app **prima dell'****Azienda Y**. L'account associato all'**Azienda X** ottiene i criteri di protezione delle app, a differenza dell'account associato all'Azienda Y. Se si vuole che l'account utente associato all'Azienda Y venga gestito dai criteri di protezione delle app, è necessario rimuovere l'account utente associato all'Azienda X e aggiungere l'account associato all'Azienda Y.
### <a name="add-a-second-account"></a>Aggiungere un secondo account
####  <a name="android"></a>Android
Se si usa un dispositivo Android, potrebbe essere visualizzato un messaggio di blocco con le istruzioni necessarie per rimuovere l'account esistente e aggiungerne uno nuovo.  Per rimuovere l'account esistente, passare a **Impostazioni &gt; Generali &gt; Applicazioni &gt;Portale aziendale** e selezionare **Cancella dati**.

![Schermata del messaggio di errore con le istruzioni per rimuovere l'account](./media/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>Visualizzare file multimediali con l'app Azure Information Protection
Per visualizzare file AV, PDF e di immagine in dispositivi Android, usare l'[app Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (nota in precedenza come app di condivisione file Rights Management).

Scaricare questa app da Google Play Store.  

Sono supportati i tipi di file seguenti:

* **Audio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (enhanced AAC+), AAC ELD (enhanced low delay AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Video:** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Immagine:** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg
* **Documenti:** PDF, PPDF


|**pfile**|**text**|
|----|----|
|Il formato pfile è un formato "wrapper" generico per i file protetti che incapsula il contenuto crittografato e le licenze Azure Information Protection e può essere usato per proteggere qualsiasi tipo di file.|I file di testo, ad esempio i file XML, CSV e così via, possono essere aperti nell'app anche se sono protetti. Tipi di file: txt, ptxt, csv, pcsv, log, plog, xml, pxml.|

## <a name="next-steps"></a>Passaggi successivi
[Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](end-user-mam-apps-ios.md)
