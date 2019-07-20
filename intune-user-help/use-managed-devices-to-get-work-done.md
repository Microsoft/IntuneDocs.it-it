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
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883862"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Registrare il dispositivo per l'accesso alle risorse aziendali o dell'Istituto di istruzione
Per registrare il dispositivo e ottenere l'accesso alla posta elettronica e alle app, è necessario installare l'app Portale aziendale Intune o Microsoft Intune. Quando si esegue la registrazione, al dispositivo vengono applicati i criteri di gestione di base configurati dall'organizzazione, ad esempio password, PIN e crittografia. Quando le impostazioni del dispositivo soddisfano tutti i requisiti dell'organizzazione, è possibile accedere in modo sicuro alle informazioni di lavoro praticamente ovunque.  

Le app Portale aziendale e Microsoft Intune consentono di proteggere il dispositivo registrato assicurando che le impostazioni del dispositivo corrispondano ai criteri dell'organizzazione. 

L'app Portale aziendale, inoltre:  
* Mantiene separate le informazioni personali e di lavoro.  
* Semplifica la ricerca e l'installazione di applicazioni aziendali e dell'Istituto di istruzione pertinenti.   

## <a name="get-the-apps"></a>Ottenere le app
Per ottenere l'app Portale aziendale:

- Installare l'app Portale aziendale dall'App Store specifica della piattaforma. In alcuni casi, l'organizzazione installerà l'app Portale aziendale.  
- Passare al [sito web portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per accedere all'app da un browser.  

Se è necessario usare l'app Microsoft Intune, l'organizzazione verrà installata per l'utente.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>Quali sono le informazioni visibili per l'azienda quando si effettua la registrazione?
Dopo che il dispositivo è stato registrato, le persone del supporto tecnico dell'organizzazione possono visualizzare solo le informazioni rilevanti per il lavoro. Non possono vedere le informazioni personali. Se si sta registrando un dispositivo personale per l'uso al lavoro, è necessario [conoscere esattamente cosa può e non è](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)possibile visualizzare.  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Qual è la differenza tra app e sito Web?
L'app Portale aziendale è disponibile per i dispositivi Windows 10, iOS, macOS e Android. Si integra perfettamente con la piattaforma corrispondente del dispositivo. La versione nel sito Web è accessibile da qualsiasi dispositivo e offre la stessa esperienza universale indipendentemente dal dispositivo in uso. 

L'app Microsoft Intune è destinata ai dispositivi Android di proprietà dell'azienda.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Quali tipi di dispositivi è possibile registrare con Portale aziendale?
- Dispositivi Apple con iOS (ad esempio iPhone e iPad) e macOS (ad esempio MacBook e iMac)
- Dispositivi Android
- Dispositivi Windows
  - Windows 10 Mobile
  - Windows 10 Desktop
  - Windows Phone 8.1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Quali tipi di dispositivi è possibile registrare con l'app Microsoft Intune?  
È possibile registrare i dispositivi Android di proprietà dell'azienda che l'organizzazione ha configurato per l'uso con l'app. L'app supporta Android 6,0 e versioni successive. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>È possibile rimuovere un computer o un dispositivo dal Portale aziendale?
È possibile rimuovere o reimpostare un computer o un dispositivo dal Portale aziendale. Esiste una differenza tra **rimuovere** e **reimpostare**.

Quando si rimuove un computer o un dispositivo dal portale aziendale, si annulla la registrazione del dispositivo in Intune. Dopo l'annullamento della registrazione non è più possibile accedere al Portale aziendale con tale dispositivo e alcuni dati aziendali all'interno di quest'ultimo potrebbero essere rimossi. Per informazioni su come rimuovere il dispositivo dalla Portale aziendale, vedere i collegamenti seguenti:  

- [Annullamento della registrazione del dispositivo Android](unenroll-your-device-from-intune-android.md)
- [Annullamento della registrazione del dispositivo iOS](unenroll-your-device-from-intune-ios.md)
- [Annullamento della registrazione del dispositivo macOS](unenroll-your-device-from-intune-macos.md)
- [Annullamento della registrazione del dispositivo Windows](unenroll-your-device-from-intune-windows.md)

Quando si reimposta un computer o un dispositivo, il Portale aziendale tenta di reimpostare le impostazioni predefinite del computer o del dispositivo stesso. La reimpostazione del dispositivo rimuove tutti i dati personali e aziendali dal dispositivo. Se si smarrisce il dispositivo, è possibile reimpostarlo anche in remoto dal sito Web del portale aziendale.  

Per informazioni su come reimpostare il dispositivo, vedere [reimpostare il dispositivo dal sito web portale aziendale](reset-erase-your-device-cpwebsite.md).  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>È possibile rimuovere un computer o un dispositivo dall'app Microsoft Intune?
No, non è possibile rimuovere un dispositivo di proprietà dell'azienda dall'app Microsoft Intune.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>Cosa accade se il dispositivo non è visibile nell'app Portale aziendale o Microsoft Intune?
Per essere visibile, un dispositivo deve essere in primo luogo aggiunto al Portale aziendale. Accedere al Portale aziendale consigliato dall'amministratore e seguire la procedura per il dispositivo in uso. Inoltre, non saranno più visualizzati i dispositivi di proprietà e gestiti dall'azienda.

Se si usa l'app Microsoft Intune, verrà visualizzato solo il dispositivo attualmente in uso. Altri dispositivi registrati non saranno visibili all'utente nell'app.  

## <a name="where-else-can-i-go-for-help"></a>Dove è possibile trovare altre informazioni?  
Per risolvere problemi comuni e domande, vedere questi documenti specifici della piattaforma:  

- [Risolvere problemi comuni con il dispositivo Android](check-compliance-on-your-device-android.md)  
- [Risolvere problemi comuni con il dispositivo iOS](troubleshoot-your-device-ios.md)
- [Risolvere problemi comuni con il dispositivo macOS](troubleshoot-your-device-macos.md)
- [Risolvere problemi comuni con il dispositivo Windows](troubleshoot-your-device-windows.md)

È anche possibile contattare il personale di supporto. L'app Portale aziendale e Microsoft Intune offre le pagine di guida e supporto che elencano le informazioni di contatto e i modi per segnalare un problema. Le informazioni di contatto sono disponibili anche nel [sito web portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980)dell'organizzazione.  

## <a name="next-steps"></a>Passaggi successivi  

Ottenere la guida che inizia con la registrazione, che è specifica della piattaforma del dispositivo:  

- [Uso del dispositivo Android](using-your-android-device-with-intune.md)
- [Uso del dispositivo iOS](using-your-ios-device-with-intune.md)
- [Uso del dispositivo macOS](using-your-macos-device-with-intune.md)
- [Uso del dispositivo Windows](using-your-windows-device-with-intune.md)
- [Uso del sito Web del portale aziendale](using-the-intune-company-portal-website.md)


