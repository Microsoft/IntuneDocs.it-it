---
title: Impostazioni relative alle restrizioni dei dispositivi per macOS
titlesuffix: Azure portal
description: "Informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità del dispositivo in dispositivi macOS.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/31/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a88cf11209726a622863339c3a6c117f7b83be1e
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi macOS in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare queste impostazioni per gestire i dispositivi macOS in un profilo di restrizione del dispositivo.

## <a name="password"></a>Password
-   **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
    -   **Tipo di password richiesto** - Specifica se la password utilizzata può essere solo numerica o se deve essere di tipo alfanumerico, ovvero contenere lettere e numeri. Questa impostazione è supportata solo su Mac OS X 10.10.3 e versioni successive.
    -   **Numero di caratteri non alfanumerici nella password** - Specifica il numero di caratteri complessi che è necessario includere nella password (da **0** a **4**).<br>Un carattere complesso è un simbolo, ad esempio "**?**".
    -   **Lunghezza minima password** - Immettere la lunghezza minima della password che l'utente deve configurare, da **4** a **16** caratteri.
    -   **Password semplici** - Consente l'uso di password semplici come **0000** o **1234**.
    -   **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password** - Specifica quanto tempo il computer deve rimanere inattivo prima che sia necessario inserire la password per sbloccarlo.
    -   **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il periodo di tempo per cui il computer deve rimanere inattivo prima che lo schermo venga bloccato.
    -   **Scadenza password (giorni)** - Specifica quanti giorni devono trascorrere prima che l'utente sia obbligato a cambiare la password, da **1** a **255** giorni.
    -   **Impedisci riutilizzo delle password precedenti** - Specifica il numero di password utilizzate in precedenza che non possono essere riutilizzate, da **1** a **24**.

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

- Un elenco **App non consentite** - Elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire. Agli utenti non viene impedito di installare un'app non consentita, ma se lo fanno si riceverà una segnalazione.
- Un elenco **App approvate** - Elenca le app che gli utenti sono autorizzati a installare. Gli utenti non devono installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite. Agli utenti non viene impedito di installare un'app non inclusa nell'elenco delle app approvate, ma se lo fanno si riceverà una segnalazione.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'ID pacchetto dell'app (ad esempio *com.apple.calculator*).

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Domini di posta elettronica non contrassegnati

Nel campo **URL del dominio di posta elettronica** aggiungere uno o più URL all'elenco. Quando gli utenti finali ricevono un messaggio di posta elettronica da un dominio diverso da quello configurato, il messaggio di posta elettronica viene contrassegnato come non attendibile nell'app di posta in iOS.

