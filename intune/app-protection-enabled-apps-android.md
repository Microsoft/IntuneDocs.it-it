---
title: App Android con criteri di protezione delle app
titleSuffix: Intune on Azure
description: "Questo argomento descrive cosa accade quando un'app Android è gestita in base ai criteri di protezione delle app.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6d48725852e26b9e4b9c66a3d614bfc1c95dc58f
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2017
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Aspettative dalla gestione dell'app per Android con criteri di protezione delle app 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo argomento descrive l'esperienza utente relativa alle app con criteri di protezione. I criteri di protezione delle app vengono applicati solo quando le app sono usate nel contesto di lavoro, ad esempio nei casi di accesso alle app con l'account aziendale o di accesso ai file archiviati nel percorso OneDrive aziendale.
##  <a name="accessing-apps"></a>Accesso alle app

L'app Portale aziendale è necessaria per tutte le app associate a criteri di protezione delle app in dispositivi Android.

Per i dispositivi non registrati in Intune è necessario installare l'app Portale aziendale nel dispositivo. Tuttavia, l'utente non deve avviare l'app Portale aziendale o accedervi per poter usare le app gestite tramite criteri di protezione delle app.
L'app Portale aziendale è una modalità con cui Intune condivide i dati in una posizione sicura. Questo quindi è un requisito anche se il dispositivo non è registrato in Intune.


##  <a name="using-apps-with-multi-identity-support"></a>Uso di app con supporto di più identità

I criteri di protezione delle app vengono applicati solo al contesto di lavoro quando si usa l'app. Il comportamento delle diverse app quindi può essere diverso a seconda del contesto, di lavoro o personale.

Per le app che supportano più identità, Intune applica i criteri di protezione delle app solo quando l'utente finale usa l'app nel contesto di lavoro.  Ad esempio, l'utente finale riceverà la richiesta di inserimento del PIN al momento di accedere ai dati di lavoro.  Per l'**app Outlook**, all'utente finale viene richiesto il PIN all'avvio dell'app. Per l'**app OneDrive** ciò si verifica quando l'utente finale digita l'account aziendale.  Per Microsoft **Word**, **PowerPoint* ed **Excel**, ciò si verifica quando l'utente finale accede ai documenti archiviati nel percorso aziendale di OneDrive for Business.
##  <a name="managing-user-accounts-on-the-device"></a>Gestione degli account utente nel dispositivo

Intune supporta solo la distribuzione di criteri di protezione delle app a un unico account utente per dispositivo.

* A seconda dell'applicazione che si usa, è possibile scegliere di bloccare o meno il secondo utente del dispositivo. In ogni caso, sarà tuttavia interessato dai criteri di protezione delle app solo il primo utente che ottiene i criteri.

  * **Microsoft Word**, **Excel** e **PowerPoint** non bloccano un secondo account utente. Questo account utente non sarà tuttavia interessato dai criteri di protezione delle app.

  * Per le app **OneDrive e Outlook**, è possibile usare un solo account aziendale.  L'aggiunta di più account aziendali è bloccata in queste app.  È tuttavia possibile rimuovere un utente e aggiungere un altro utente sul dispositivo.


* Se prima della distribuzione dei criteri di protezione delle app, un dispositivo ha più di un account utente, il primo account che riceve la distribuzione dei criteri di protezione delle app sarà gestito dai criteri di protezione delle app di Intune.


Per capire meglio come vengono gestiti gli account utente multipli, leggere lo scenario di esempio riportato sotto.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri di protezione delle app. L'**Azienda X** distribuisce i criteri di protezione delle app **prima dell'****Azienda Y**. L'account associato all'**Azienda X** otterrà i criteri di protezione delle app, a differenza dell'account associato all'Azienda Y. Se si vuole che l'account utente associato all'Azienda Y sia gestito con i criteri di protezione delle app, è necessario rimuovere l'utente associato all'Azienda X.
### <a name="adding-a-second-account"></a>Aggiunta di un secondo account
####  <a name="android"></a>Android
Se si usa un dispositivo Android, potrebbe essere visualizzato un messaggio di blocco con le istruzioni necessarie per rimuovere l'account esistente e aggiungerne uno nuovo.  Per rimuovere l'account esistente, passare a **Impostazioni &gt; Generali &gt; Applicazioni &gt;Portale aziendale e selezionare "Cancella dati"**.

![Schermata del messaggio di errore con le istruzioni per rimuovere l'account](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>Visualizzazione di file multimediali con l'app Azure Information Protection (nota in precedenza come app di condivisione Rights Management)
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
## <a name="next-steps"></a>Passaggi successivi
[Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Vedere anche
[Creare e distribuire i criteri di protezione delle app con Microsoft Intune](app-protection-policies.md)
