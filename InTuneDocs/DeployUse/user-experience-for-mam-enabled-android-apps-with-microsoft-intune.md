---
title: App Android con criteri MAM | Microsoft Intune
description: "Questo argomento descrive cosa accade quando l&quot;app è gestita dai criteri di gestione delle app mobili."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 546b909737b4ea34bd747880fe8ed2d366c6b18a


---

# Aspettative dalla gestione dell'app per Android con criteri MAM
Questo argomento descrive l'esperienza dell'utente finale con le app con criteri MAM. I criteri di gestione delle applicazioni mobili (MAM, Mobile Application Management) vengono applicati solo quando le app vengono usate nel contesto di lavoro, ad esempio nei casi di accesso alle app con l'account aziendale o di accesso ai file archiviati nel percorso OneDrive aziendale.
##  Accesso alle app

L'app Portale aziendale è necessaria per tutte le app associate a criteri MAM in dispositivi Android.

Per i dispositivi non registrati in Intune è necessario installare l'app Portale aziendale nel dispositivo. Tuttavia, l'utente non deve avviare l'app Portale aziendale o accedervi per poter usare le app gestite tramite criteri MAM.
L'app Portale aziendale è una modalità con cui Intune condivide i dati in una posizione sicura. Questo quindi è un requisito anche se il dispositivo non è registrato in Intune.


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
####  Android
Se si usa un dispositivo Android, potrebbe essere visualizzato un messaggio di blocco con le istruzioni necessarie per rimuovere l'account esistente e aggiungerne uno nuovo.  Per rimuovere l'account esistente, passare a **Impostazioni &gt; Generali &gt; Applicazioni &gt;Portale aziendale e selezionare "Cancella dati"**.

![Schermata del messaggio di errore con le istruzioni per rimuovere l'account](../media/AppManagement/Android_SwitchUser.png)

##  Visualizzazione di file multimediali con l'app Azure Information Protection (nota in precedenza come app di condivisione Rights Management)
Per visualizzare file AV, PDF e di immagine in dispositivi Android, usare l'[app Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Scaricare questa app da Google Play Store.  

Sono supportati i tipi di file seguenti:

* **Audio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (enhanced AAC+), AAC ELD (enhanced low delay AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE.
* **Video:** H.263, H.264 AVC, MPEG-4 SP, VP8.
* **Immagine:** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg.
* **Documenti:** PDF, PPDF

------------
|**pfile**|**text**|
|----|----|
|Il formato pfile è un formato "wrapper" generico per i file protetti che incapsula il contenuto crittografato e le licenze Azure Information Protection e può essere usato per proteggere qualsiasi tipo di file.|I file di testo, ad esempio i file XML, CSV e così via, possono essere aperti nell'app anche se sono protetti. Tipi di file: txt, ptxt, csv, pcsv, log, plog, xml, pxml.|
---------------
## Passaggi successivi
[Aspettative dalla gestione dell'app per iOS con criteri MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### Vedere anche
[Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


