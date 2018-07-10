---
title: Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo?
description: Informazioni visibili e non visibili per il personale IT sul dispositivo gestito.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.openlocfilehash: ad949cc9d20e0e46ab986b4646059af733018255
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232807"
---
# <a name="what-information-can-my-company-see-when-i-enroll-my-device"></a>Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo?

L'azienda non può vedere le informazioni personali di un utente quando registra un dispositivo con Microsoft Intune. Quando si registra un dispositivo, si concede all'azienda l'autorizzazione per visualizzare determinati tipi di informazioni nel dispositivo, ad esempio il modello di dispositivo e il numero di serie. L'azienda usa queste informazioni per la protezione dei dati aziendali nel dispositivo.

**Informazioni che l'azienda non può mai visualizzare:**

- Cronologia delle chiamate e delle esplorazioni Web
- Posta elettronica e messaggi di testo
- Contatti
- Calendario
-   Password
- Immagini, incluse quelle nell'app Foto o nel rullino della fotocamera

**Informazioni che l'azienda può sempre visualizzare:**

- Modello del dispositivo, ad esempio Google Pixel
- Produttore, ad esempio Microsoft
- Sistema operativo, ad esempio iOS
- Nomi di app, ad esempio Microsoft Word
- Proprietario del dispositivo
- Nome dispositivo
- Numero di serie

**Informazioni che l'azienda potrebbe visualizzare:**

-  Numero di telefono: per i dispositivi di proprietà dell'**azienda** può essere visualizzato il numero di telefono completo. Per i dispositivi di proprietà **personale** sono visibili all'azienda solo le ultime quattro cifre del numero di telefono. Per visualizzare il **tipo di proprietà** di un singolo dispositivo, aprire la pagina **Dettagli dispositivo** del dispositivo.
-  Località: l'azienda non può mai visualizzare dove si trova il dispositivo, a meno che non si tratti di un dispositivo iOS supervisionato che è stato perso. [Come scoprirlo?](https://go.microsoft.com/fwlink/?linkid=853816)
- Inventario delle app: se l'azienda usa Mobile Threat Defense, può visualizzare dettagli aggiuntivi sulle app presenti nel dispositivo iOS. Altre informazioni su [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md).
- Informazioni di rete: alcune informazioni sulle connessioni di rete per dispositivi Android possono essere disponibili per il supporto tecnico dell'azienda. Se l'azienda esigesse, ad esempio, che i dispositivi rimangano all'interno di un determinato edificio, il dispositivo potrebbe identificare la rete a cui è connesso. 
