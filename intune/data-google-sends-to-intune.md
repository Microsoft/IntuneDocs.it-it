---
title: Dati inviati da Google a Intune
titleSuffix: Microsoft Intune
description: Elenco di dati inviati da Google a Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 368205b63fcd360adf66f964c6cae087f6da3dfc
ms.sourcegitcommit: 2162ed46d939b4a9b85fa4e7e9943f2fb5948f1e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
ms.locfileid: "31617603"
---
# <a name="data-google-sends-to-intune"></a>Dati inviati da Google a Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando la gestione dei dispositivi aziendali Android è abilitata in un dispositivo, Microsoft Intune stabilisce una connessione con Google e le informazioni sull'utente e il dispositivo vengono condivise tra Intune e Google. Per consentire a Microsoft Intune di stabilire una connessione è necessario creare un account di Google.

Nella tabella seguente sono elencati i dati che Google invia a Intune quando la gestione dei dispositivi è abilitata in un dispositivo:


| Dati inviati da Google a Intune | Dettagli | Utilizzato per | Esempio |
|:---:|:---:|:---:|:---:|
| Dati aziendali | Identificatori aziendali del cliente in Google. | Collegare le informazioni del cliente tra Intune e Google. | Esempio di **enterpriseId**: LC04eik8a6.<br>**Nome**. Nome dell'amministratore immesso durante la configurazione di Android Enterprise. Esempio: Joe Smith.<br>**Posta elettronica amministratore**. YourAdmin@gmail.com usato durante la configurazione di Android Enterprise. |
| Dati delle applicazioni | Dati per le applicazioni gestite di Play Store. | Destinare l'applicazione a utenti o dispositivi come disponibile o obbligatoria. | Esempio di **nome applicazione**: Contoso Warehouse Inventory Application.<br>Esempio di **identificatore univoco per rappresentare l'applicazione**: app:com.Contoso.Warehouse.InventoryTracking |
| Account di servizio | Account del servizio Google interno univoco da usare con le chiamate di clienti specifici. | Usato per effettuare chiamate a Google per conto dei clienti (per visualizzare app, dispositivi e altro ancora) | Esempio di **nome**: InternalAccount@InternalService.com.<br>Esempio di **chiavi**: ServiceAccountPassword |


Per interrompere l'uso della gestione dispositivi aziendali Android con Microsoft Intune ed eliminare i dati è necessario disabilitare la gestione dispositivi aziendali Android di Microsoft Intune ed eliminare l'account Google. Per informazioni sulla gestione account, vedere l'account Google.


