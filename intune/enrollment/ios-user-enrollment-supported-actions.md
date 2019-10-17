---
title: Azioni e opzioni di Intune supportate con la registrazione utente Apple
titleSuffix: Microsoft Intune
description: Informazioni sulle azioni e opzioni di Intune supportate con la registrazione utente Apple
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: acf1112f96b28b156b3c4857485de30d7ad553ef
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955249"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Azioni e opzioni di Intune supportate con la registrazione utente Apple

La registrazione utente supporta un subset di opzioni di gestione dei dispositivi. Se un profilo di configurazione preesistente viene applicato a un dispositivo di registrazione utente, solo le impostazioni supportate dalla registrazione utente verranno applicate al dispositivo.

## <a name="password-settings"></a>Impostazioni della password

Nei dispositivi di registrazione utente, se si configura qualsiasi impostazione della password, le impostazioni **Password semplici** vengono impostate automaticamente su **Blocca** e viene impostato un PIN a 6 cifre.

Si supponga ad esempio di configurare l'impostazione **Scadenza password** e di applicare questo criterio nei dispositivi registrati dall'utente. Nei dispositivi si verificherà quanto segue:
- L'impostazione **Scadenza password** viene ignorata.
- Le password semplici, ad esempio `1111` o `1234`, non sono consentite.
- Viene applicato un PIN di 6 cifre.

## <a name="administrator-remote-device-actions-and-options"></a>Azioni e opzioni dell'amministratore nei dispositivi remoti
Gli amministratori possono eseguire le azioni e le opzioni seguenti nei dispositivi di registrazione utente:
- Ritiro
- Eliminazione
- Blocco remoto
- Sincronizzazione

Tutte le altre azioni non sono supportate.

## <a name="end-user-actions"></a>Azioni dell'utente finale
Nei dispositivi di registrazione utente gli utenti finali possono eseguire le azioni seguenti nei propri dispositivi dall'applicazione Portale aziendale e dal sito Web:
- Ridenominazione. Questa azione si applica solo al nome visualizzato all'utente all'interno del portale aziendale. Il dispositivo non verrà rinominato al di fuori di questo contesto.
- Remove
- Blocco remoto
- Controllo dello stato

## <a name="other-supported-options"></a>Altre opzioni supportate

Le opzioni seguenti sono supportate in Intune per i dispositivi registrati con la registrazione utente Apple:
- VPN per singole app. Questo supporto esclude i domini Safari poiché la registrazione utente non supporta la configurazione delle impostazioni di Safari.
- Wi-Fi 
- Rimozione dell'app aziendale dopo l'annullamento della registrazione
- Distribuzione di app tramite Volume Purchasing Plan (VPP) con licenza utente
- Rilevamento jailbreak

Sono supportate le restrizioni seguenti:
- Visualizzazione dei documenti aziendali nelle app non gestite
- Visualizzazione di documenti non aziendali nelle app aziendali
- Consenti alle app gestite di leggere da contatti in account di contatti non gestiti
- Considera AirDrop come destinazione non gestita
- Richiedi il backup crittografato
- Sincronizzazione delle app gestite nel cloud
- Accesso al centro di controllo durante il blocco del dispositivo
- Accesso al centro notifiche durante il blocco del dispositivo
- Visualizzazione Oggi durante il blocco del dispositivo
- Blocca le registrazioni di screenshot e di schermate
- Blocca il backup di libri aziendali
- Blocca la sincronizzazione di metadati di libri aziendali
- Richiedi backup crittografato
- Rilevamento del polso per l'Apple Watch associato
- Blocca Siri
- Blocca Siri durante il blocco del dispositivo
- Avvisi in caso di illeciti di Safari
- Blocco dell'invio dei dati di diagnostica ad Apple


## <a name="options-not-supported"></a>Opzioni non supportate
Le opzioni seguenti non sono supportate nei dispositivi registrati con la registrazione utente. Se sono necessarie queste opzioni, vedere la registrazione dei dispositivi per i dispositivi personali o la registrazione automatica dei dispositivi per i dispositivi aziendali.
- Raccogliere l'inventario delle app per le app al di fuori del volume APFS gestito.
- Raccogliere l'inventario dei certificati e i profili di provisioning al di fuori del volume APFS gestito.
- Raccogliere UDID e altri identificatori di dispositivo permanenti.
- Sebbene la registrazione utente supporti un ID registrazione univoco per ogni dispositivo registrato, questo ID non viene mantenuto dopo l'annullamento della registrazione.
- Le funzionalità di Intune seguenti non sono supportate a causa di questa limitazione:
- Profili utente SCEP con formato del nome soggetto Numero di serie.
- VPN a livello di dispositivo.
- Distribuzione di app VPP con licenza dispositivo.
- Controllo MDM di applicazioni al di fuori del volume APFS gestito.
- I criteri di protezione delle applicazioni verranno comunque applicati a queste app. Tuttavia, non sarà possibile assumere la gestione o distribuire una versione gestita di queste app a meno che l'utente non le elimini dal dispositivo.
- Azioni, configurazioni, impostazioni e comandi che richiedono la supervisione. 

## <a name="next-steps"></a>Passaggi successivi

[Configurare la registrazione utente iOS e iPadOS](ios-user-enrollment.md)