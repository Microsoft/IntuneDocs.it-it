---
title: Impostazioni relative alle restrizioni dei dispositivi per macOS in Microsoft Intune
titlesuffix: ''
description: Informazioni sulle opzioni di Intune per il controllo delle impostazioni e delle funzionalità nei dispositivi che eseguono macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0a2a096bfb4b5fafd895425a775abc13afc643e2
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728537"
---
# <a name="microsoft-intune-macos-device-restriction-settings"></a>Impostazioni relative alle restrizioni dei dispositivi macOS in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni relative alle restrizioni dei dispositivi di Microsoft Intune configurabili per i dispositivi che eseguono macOS.

## <a name="password"></a>Password
- **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
  - **Tipo di password richiesto** - Specifica se la password utilizzata può essere solo numerica o se deve essere di tipo alfanumerico, ovvero contenere lettere e numeri. Questa impostazione è supportata solo su Mac OS X 10.10.3 e versioni successive.
  - **Numero di caratteri non alfanumerici nella password** - Specifica il numero di caratteri complessi che è necessario includere nella password (da **0** a **4**).<br>Un carattere complesso è un simbolo, ad esempio "**?**".
  - **Lunghezza minima password** - Immettere la lunghezza minima della password che l'utente deve configurare, da **4** a **16** caratteri.
  - **Password semplici** - Consente l'uso di password semplici come **0000** o **1234**.
  - **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password** - Specifica quanto tempo il computer deve rimanere inattivo prima che sia necessario inserire la password per sbloccarlo.
  - **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il periodo di tempo per cui il computer deve rimanere inattivo prima che lo schermo venga bloccato.
  - **Scadenza password (giorni)** - Specifica quanti giorni devono trascorrere prima che l'utente sia obbligato a cambiare la password, da **1** a **255** giorni.
  - **Impedisci riutilizzo delle password precedenti** - Specifica il numero di password utilizzate in precedenza che non possono essere riutilizzate, da **1** a **24**.

- **Blocca il riempimento automatico delle password**: scegliere **Blocca** per impedire l'uso della funzionalità di riempimento automatico delle password in macOS. La scelta di **Blocca** ha anche le conseguenze seguenti:

  - Agli utenti non viene richiesto di usare una password salvata in Safari o in qualsiasi app.
  - Le password complesse automatiche sono disabilitate e non vengono consigliate password complesse agli utenti.

  **Non configurata** consente queste funzionalità.

- **Blocca le richieste di prossimità password**: scegliere **Blocca** in modo che il dispositivo di un utente non richieda password dai dispositivi nelle vicinanze. **Non configurata** consente queste richieste di password.

- **Blocca la condivisione delle password**: **Blocca** impedisce la condivisione delle password tra i dispositivi tramite AirDrop. **Non configurata** consente di condividere le password.


## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

- Un elenco **App non consentite** - Elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire. Agli utenti non viene impedito di installare un'app non consentita, ma se lo fanno si riceverà una segnalazione.
- Un elenco **App approvate** - Elenca le app che gli utenti sono autorizzati a installare. Gli utenti non devono installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite. Agli utenti non viene impedito di installare un'app non inclusa nell'elenco delle app approvate, ma se lo fanno si riceverà una segnalazione.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'ID pacchetto dell'app (ad esempio *com.apple.calculator*).

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Domini di posta elettronica non contrassegnati

Nel campo **URL del dominio di posta elettronica** aggiungere uno o più URL all'elenco. Quando gli utenti ricevono un messaggio di posta elettronica da un dominio diverso da quello configurato, il messaggio di posta elettronica viene contrassegnato come non attendibile nell'app di posta in MacOS.

