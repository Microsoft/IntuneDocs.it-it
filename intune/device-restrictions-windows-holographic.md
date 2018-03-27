---
title: Impostazioni relative alle restrizioni dei dispositivi di Microsoft Intune per Windows Holographic for Business
titleSuffix: ''
description: Informazioni sulle opzioni di Intune per il controllo delle impostazioni e delle funzionalità nei dispositivi che eseguono Windows Holographic for Business.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 694b81434a95f48abc98f5012460523420df58cc
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="microsoft-intune-windows-holographic-for-business-device-restriction-settings"></a>Impostazioni relative alle restrizioni dei dispositivi per Windows Holographic for Business

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le impostazioni seguenti relative alle restrizioni dei dispositivi sono supportate nei dispositivi che eseguono Windows Holographic for Business, ad esempio Microsoft Hololens.

## <a name="general"></a>Generale

- **Annullamento manuale della registrazione** - Consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.
- **Cortana** - Abilita o disabilita l'assistente vocale Cortana.
- **Georilevazione** - Specifica se il dispositivo può usare le informazioni dei servizi di posizione.



## <a name="password"></a>Password
-   **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
    -   **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività**: specifica che l'utente deve inserire una password per sbloccare il dispositivo.



## <a name="app-store"></a>App Store

-   **Aggiorna automaticamente le app dallo Store**: consente l'aggiornamento automatico delle app installate da Microsoft Store.
-   **Installazione di app attendibile**: consente il trasferimento locale delle app con certificato attendibile.
-   **Sblocco dallo sviluppatore**: consente la modifica delle impostazioni da parte degli sviluppatori Windows, ad esempio consentire all'utente finale di modificare le app trasferite localmente.

## <a name="edge-browser"></a>Browser Microsoft Edge

-   **Browser Microsoft Edge**: consente l'uso del browser Web Microsoft Edge sul dispositivo.
-   **Cookie** - Consente al browser di salvare i cookie di Internet per il dispositivo.
-   **Pop-up**: blocca le finestra popup del browser (si applica solo a Windows 10 Desktop).
-   **Suggerimenti per la ricerca** - Consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca.
-   **Strumento per la gestione delle password** - Abilita o disabilita la funzione di gestione password di Microsoft Edge.
- **Invia intestazioni DNT (Do Not Track)** - Configura il browser Microsoft Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen per Microsoft Edge**: abilita SmartScreen di Edge per l'accesso al sito e i download di file.

## <a name="search"></a>Cerca
- **Cerca la posizione**: specifica se la ricerca può usare le informazioni sulla posizione. Informazioni su


## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione
-   **Account Microsoft** - Consente all'utente di associare un account Microsoft con il dispositivo.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività

-   **Bluetooth** - Controlla se l'utente può abilitare e configurare Bluetooth nel dispositivo.
-   **Individuabilità di Bluetooth** - Consente che il dispositivo sia scoperto da altri dispositivi con la funzione Bluetooth attivata.
-   **Annunci con Bluetooth** - Consente al dispositivo di ricevere annunci tramite Bluetooth.

## <a name="control-panel-and-settings"></a>Pannello di controllo e impostazioni

- **Modifica dell'ora di sistema**: impedisce all'utente finale di modificare la data e l'ora del dispositivo.

## <a name="reporting-and-telemetry"></a>Creazione di report e telemetria

- **Condividi i dati di utilizzo**: selezionare il livello di invio dei dati diagnostici.