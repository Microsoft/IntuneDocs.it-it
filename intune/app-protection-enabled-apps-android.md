---
title: App Android con criteri di protezione delle app
titlesuffix: Microsoft Intune
description: Informazioni su cosa aspettarsi da un'app Android con criteri di protezione.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16cef0b3e72c2e7815aada1c45c0e312b84931ab
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31833018"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Aspettative dalla gestione dell'app per Android con criteri di protezione delle app 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Informazioni su cosa aspettarsi da app Android con criteri di protezione delle app. I criteri di protezione delle app si applicano solo quando le app vengono usate in un contesto professionale, ad esempio quando si accede a un'app con un account aziendale o quando si accede a file archiviati nel percorso OneDrive dell'azienda.
##  <a name="accessing-apps"></a>Accesso alle app

L'app Portale aziendale è necessaria per tutte le app in dispositivi Android con criteri di protezione delle app.

Installare l'app Portale aziendale in tutti i dispositivi che non sono registrati in Intune. Agli utenti non viene richiesto di accedere all'app Portale aziendale per usare le app con criteri di protezione delle app.
L'app Portale aziendale consente di condividere i dati in una posizione sicura. È quindi un requisito anche per i dispositivi non registrati.


##  <a name="using-apps-with-multi-identity-support"></a>Uso di app con supporto di più identità

I criteri di protezione delle app hanno effetto solo quando un utente tenta di accedere a dati relativi al lavoro.  Se l'utente accede all'app per uso personale, i comportamenti possono essere diversi.

Alcune app supportano più identità. In questo caso, Intune applica i criteri di protezione delle app solo quando un utente accede ai dati di lavoro.  Un utente potrebbe, ad esempio, ricevere una richiesta di immissione di un PIN.  Nell'**app Outlook** il messaggio di richiesta viene visualizzato quando un utente avvia l'app. Nell'**app OneDrive** il messaggio di richiesta viene visualizzato quando un utente digita l'account aziendale.  In Microsoft **Word**, **PowerPoint** ed **Excel** il messaggio di richiesta viene visualizzato quando un utente accede a documenti di OneDrive aziendale.
##  <a name="managing-user-accounts-on-the-device"></a>Gestione degli account utente nel dispositivo

Intune supporta la distribuzione di criteri di protezione delle app a un unico account utente per dispositivo.

* A seconda dell'applicazione che si usa, è possibile scegliere di bloccare o meno il secondo utente del dispositivo. In ogni caso, sarà tuttavia interessato dai criteri di protezione delle app solo il primo utente che ottiene i criteri.

  * **Microsoft Word**, **Excel** e **PowerPoint** non bloccheranno l'accesso a un account utente aggiuntivo. L'account utente non sarà tuttavia interessato dai criteri di protezione delle app.

  * Per le app **OneDrive e Outlook**, è possibile usare un solo account aziendale.  L'aggiunta di più account aziendali è bloccata in queste app.  È comunque possibile rimuovere un utente da un dispositivo e quindi aggiungere un altro utente al dispositivo.


* In un dispositivo potrebbero essere presenti più account utente esistenti prima della distribuzione dei criteri di protezione delle app. In questo caso, il primo account al quale vengono distribuiti i criteri di protezione delle app è gestito dai criteri di protezione delle app di Intune.


Per informazioni su come Intune gestisce più account utente, vedere l'esempio seguente.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri di protezione delle app. L'**Azienda X** distribuisce i criteri di protezione delle app **prima dell'****Azienda Y**. L'account associato all'**Azienda X** otterrà i criteri di protezione delle app, a differenza dell'account associato all'Azienda Y. Per fare in modo che l'account utente associato all'Azienda Y sia gestito con i criteri di protezione delle app, l'utente A deve rimuovere l'account associato all'Azienda X.
### <a name="adding-a-second-account"></a>Aggiunta di un secondo account
####  <a name="android"></a>Android
Potrebbe essere richiesto di rimuovere l'account esistente e aggiungerne uno nuovo.  Per rimuovere l'account esistente, passare a **Impostazioni &gt; Generali &gt; Gestione applicazioni &gt;Portale aziendale. Selezionare quindi "Cancella dati".**

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

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>text</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pfile è un formato "wrapper" generico per i file protetti. Incapsula il contenuto crittografato e le licenze di Azure Information Protection. e può essere usato per proteggere qualsiasi tipo di file. | I file di testo, ad esempio i file XML, CSV e così via, possono essere aperti nell'app anche se sono protetti. Tipi di file: txt, ptxt, csv, pcsv, log, plog, xml, pxml. |

---------------
## <a name="next-steps"></a>Passaggi successivi
[Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Vedere anche
[Creare e distribuire i criteri di protezione delle app con Microsoft Intune](app-protection-policies.md)
