---
title: Impostazioni relative alle restrizioni dei dispositivi di Intune per Windows Holographic for Business
titlesuffix: Azure portal
description: "Informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità nei dispositivi Windows Holographic for Business\"."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/19/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 300ddb15f2d7b8f2fc6ab4a0e9e32852e0604e0a
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="windows-holographic-for-business-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Windows Holographic for Business in Microsoft Intune

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

-   **App Store**: consente o blocca l'uso dell'App Store nei dispositivi.
-   **Aggiorna automaticamente le app dallo Store**: consente l'aggiornamento automatico delle app installate da Microsoft Store.
-   **Installazione di app attendibile**: consente il trasferimento locale delle app con certificato attendibile.
-   **Sblocco dallo sviluppatore**: consente la modifica delle impostazioni da parte degli sviluppatori Windows, ad esempio consentire all'utente finale di modificare le app trasferite localmente.

## <a name="edge-browser"></a>Browser Edge

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