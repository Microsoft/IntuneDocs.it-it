---
title: Usare dispositivi gestiti per lo svolgimento del lavoro | Microsoft Docs
description: Informazioni su cosa significa registrare un dispositivo nel sistema di gestione con Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c0d3484311d044842daf6718b306d45fc93edf2
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545936"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Registrazione dispositivo per l'accesso all'azienda o dell'istituto di istruzione delle risorse
Per registrare il dispositivo e ottenere l'accesso alla posta elettronica e le app, è necessario installare l'app portale aziendale di Intune o app di Microsoft Intune. Quando si registra, i criteri di gestione di base che l'organizzazione ha configurato, ad esempio password, PIN e la crittografia, vengono applicati al dispositivo. Dopo che le impostazioni del dispositivo che soddisfi tutti i requisiti dell'organizzazione, è possibile accedere in modo sicuro le informazioni di lavoro praticamente ovunque ti trovi.  

L'App portale aziendale e Microsoft Intune Proteggi dispositivo registrato, garantendo che le impostazioni del dispositivo corrispondano i criteri dell'organizzazione. 

L'app Portale aziendale, inoltre:  
* Mantiene le informazioni personali e di lavoro separati.  
* Rende facile trovare e installare rilevanti App aziendali e dell'istituto di istruzione.   

## <a name="get-the-apps"></a>Ottenere le app
Per ottenere l'app Portale aziendale:

- Installare l'app portale aziendale dall'archivio di app specifici della piattaforma. In alcuni casi, l'organizzazione verrà installata l'app portale aziendale per l'utente.  
- Andare alla [sito Web portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per accedere all'app da un browser.  

Se ti viene richiesto di usare l'app di Microsoft Intune, l'organizzazione verrà installato automaticamente.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>Quali sono le informazioni visibili per l'azienda quando si effettua la registrazione?
Dopo aver registrato il dispositivo, addetti al supporto tecnico dell'organizzazione possono visualizzare solo le informazioni relative al lavoro. Non possono vedere le informazioni personali. Se si vuole registrare un dispositivo personale per usarlo al lavoro, [informazioni su esattamente cosa può e non possono essere visualizzati](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Qual è la differenza tra app e sito Web?
L'app portale aziendale è disponibile per dispositivi Android, iOS, macOS e Windows 10. Si integra perfettamente con rispettiva piattaforma del dispositivo. La versione nel sito Web è accessibile da qualsiasi dispositivo e offre la stessa esperienza universale indipendentemente dal dispositivo in uso. 

L'app di Microsoft Intune è per i dispositivi Android aziendali.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Che tipo di dispositivi possono essere registrati con il portale aziendale?
- Dispositivi Apple con iOS (ad esempio iPhone e iPad) e macOS (ad esempio MacBook e iMac)
- Dispositivi Android
- Dispositivi Windows
    - Windows 10 Mobile
    - Windows 10 Desktop
    - Windows Phone 8.1
    - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Che tipo di dispositivi possono essere registrati con l'app di Microsoft Intune?  
È possibile registrare dispositivi Android aziendali impostati dall'organizzazione da usare con l'app. L'app supporta Android 6.0 e versioni successive. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>È possibile rimuovere un computer o un dispositivo dal Portale aziendale?
È possibile rimuovere o reimpostare un computer o un dispositivo dal Portale aziendale. Esiste una differenza tra **rimuovere** e **reimpostare**.

Quando si rimuove un computer o un dispositivo dal portale aziendale, si annulla la registrazione del dispositivo in Intune. Dopo l'annullamento della registrazione non è più possibile accedere al Portale aziendale con tale dispositivo e alcuni dati aziendali all'interno di quest'ultimo potrebbero essere rimossi. Per informazioni su come rimuovere il dispositivo dal portale aziendale, vedere i collegamenti seguenti:  

- [Annullamento della registrazione del dispositivo Android](unenroll-your-device-from-intune-android.md)
- [Annullamento della registrazione del dispositivo iOS](unenroll-your-device-from-intune-ios.md)
- [Annullamento della registrazione del dispositivo macOS](unenroll-your-device-from-intune-macos.md)
- [Annullamento della registrazione del dispositivo Windows](unenroll-your-device-from-intune-windows.md)

Quando si reimposta un computer o un dispositivo, il Portale aziendale tenta di reimpostare le impostazioni predefinite del computer o del dispositivo stesso. La reimpostazione del dispositivo rimuove tutti i dati personali e aziendali dal dispositivo. Se si smarrisce il dispositivo, è possibile reimpostarlo anche in remoto dal sito Web del portale aziendale.  

Per informazioni su come reimpostare il dispositivo, vedere [Reimposta il dispositivo dal sito Web del portale aziendale](reset-erase-your-device-cpwebsite.md).  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>È possibile rimuovere un computer o dispositivo dall'app Microsoft Intune?
No, non è possibile rimuovere un dispositivo aziendale dall'app Microsoft Intune.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>Cosa accade se non è visibile il dispositivo nell'app portale aziendale o Microsoft Intune
Per essere visibile, un dispositivo deve essere in primo luogo aggiunto al Portale aziendale. Accedere al Portale aziendale consigliato dall'amministratore e seguire la procedura per il dispositivo in uso. Inoltre, non saranno più visualizzati i dispositivi di proprietà e gestiti dall'azienda.

Se si usa l'app di Microsoft Intune, verrà visualizzato solo il dispositivo che attualmente in uso. Altri dispositivi registrati non saranno visibili all'utente nell'app.  

## <a name="where-else-can-i-go-for-help"></a>Dove è possibile trovare altre informazioni?  
Per risolvere i problemi e domande comuni, vedere questi documenti specifici della piattaforma:  

- [Risolvere problemi comuni con il dispositivo Android](check-compliance-on-your-device-android.md)  
- [Risolvere problemi comuni con il dispositivo iOS](troubleshoot-your-device-ios.md)
- [Risolvere problemi comuni con il dispositivo macOS](troubleshoot-your-device-macos.md)
- [Risolvere problemi comuni con il dispositivo Windows](troubleshoot-your-device-windows.md)

È possibile anche contattare il supporto tecnico. L'App portale aziendale e Microsoft Intune app offrono assistenza e supportano le pagine che elenca le informazioni di contatto e sui modi per segnalare un problema. Informazioni di contatto sono inoltre disponibili sul nome organizzazione [sito Web portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="next-steps"></a>Passaggi successivi  

L'assistenza per iniziare a con la registrazione, che è specifica della piattaforma del dispositivo:  

- [Uso del dispositivo Android](using-your-android-device-with-intune.md)
- [Uso del dispositivo iOS](using-your-ios-device-with-intune.md)
- [Uso del dispositivo macOS](using-your-macos-device-with-intune.md)
- [Uso del dispositivo Windows](using-your-windows-device-with-intune.md)
- [Uso del sito Web del portale aziendale](using-the-intune-company-portal-website.md)


