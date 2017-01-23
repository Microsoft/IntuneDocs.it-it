---
title: App Android con criteri MAM | Documentazione Microsoft
description: "Questo argomento descrive cosa accade quando l&quot;app è gestita dai criteri di gestione delle app mobili."
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: aeacfddb3ed42938dd9443e2734222c977436430


---

# <a name="what-to-expect-when-your-android-app-is-managed-by-mam-policies"></a>Aspettative dalla gestione dell'app per Android con criteri MAM

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento descrive l'esperienza dell'utente finale con le app con criteri di gestione delle app mobili (MAM). I criteri di gestione delle app mobili (MAM, Mobile Application Management) vengono applicati solo quando le app vengono usate in un contesto di lavoro, ad esempio quando l'utente accede alle app con un account aziendale o accede ai file archiviati in un percorso OneDrive aziendale.
##  <a name="access-apps"></a>Accedere alle app

L'app Portale aziendale è necessaria per tutte le app associate a criteri MAM in dispositivi Android.

Per i dispositivi non registrati in Intune è necessario installare l'app Portale aziendale nel dispositivo. Tuttavia, l'utente non deve avviare l'app Portale aziendale o accedervi per poter usare le app gestite con i criteri MAM.

L'app Portale aziendale è una modalità con cui Intune condivide i dati in una posizione sicura. Quindi, l'app Portale aziendale è necessaria per tutte le app associate a criteri MAM, anche se il dispositivo non è registrato in Intune.


##  <a name="use-apps-with-multi-identity-support"></a>Usare app con supporto di più identità

I criteri MAM si applicano solo in un contesto aziendale. Di conseguenza, l'app potrebbe comportarsi in modo diverso a seconda che il contesto sia aziendale o personale.

Ad esempio, l'utente riceve la richiesta di inserimento del PIN al momento di accedere ai dati di lavoro. Per l'**app Outlook**, all'utente viene richiesto un PIN all'avvio dell'app. Per l'**app OneDrive**, all'utente viene richiesto il PIN all'inserimento dell'account aziendale. Per **Microsoft Word**, **PowerPoint** ed **Excel**, all'utente viene richiesto il PIN quando accede ai documenti archiviati nel percorso OneDrive for Business dell'azienda.

##  <a name="manage-user-accounts-on-the-device"></a>Gestire gli account utente nel dispositivo

Intune supporta la distribuzione di criteri MAM solo a un unico account utente per dispositivo.

* A seconda dell'applicazione che si usa, è possibile scegliere di bloccare il secondo utente del dispositivo. In ogni caso, sarà tuttavia interessato dai criteri MAM solo il primo utente che ottiene i criteri.

  * **Microsoft Word**, **Excel** e **PowerPoint** non bloccano un secondo account utente. Questo account utente non sarà tuttavia interessato dai criteri MAM.

  * Per le app **OneDrive** e **Outlook**, è possibile usare un solo account aziendale.  Non è possibile aggiungere più account aziendali per queste app.  È tuttavia possibile rimuovere un utente e aggiungere un altro utente sul dispositivo.


* Se prima della distribuzione dei criteri MAM, un dispositivo ha più di un account utente, il primo account che riceve la distribuzione dei criteri MAM sarà gestito dai criteri MAM di Intune.


Per capire meglio come vengono gestiti gli account utente multipli, leggere lo scenario di esempio seguente.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri MAM. L'**Azienda X** distribuisce i criteri MAM **prima dell'****Azienda Y**. L'account associato all'**Azienda X** ottiene i criteri MAM, a differenza dell'account associato all'Azienda Y. Se si vuole che l'account utente associato all'Azienda Y sia gestito con i criteri MAM, è necessario rimuovere l'utente associato all'Azienda X.
### <a name="add-a-second-account"></a>Aggiungere un secondo account
####  <a name="android"></a>Android
Se si usa un dispositivo Android, potrebbe essere visualizzato un messaggio di blocco con le istruzioni necessarie per rimuovere l'account esistente e aggiungerne uno nuovo.  Per rimuovere l'account esistente, passare a **Impostazioni &gt; Generali &gt; Applicazioni &gt;Portale aziendale** e selezionare **Cancella dati**.

![Schermata del messaggio di errore con le istruzioni per rimuovere l'account](../media/AppManagement/Android_SwitchUser.png)

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
[Aspettative dalla gestione dell'app per iOS con criteri MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### <a name="see-also"></a>Vedere anche
[Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


