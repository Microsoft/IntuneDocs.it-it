---
title: Restrizioni dei dispositivi per Windows Holographic for Business in Microsoft Intune - Azure | Microsoft Docs
description: Conoscere e configurare impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune per Windows Holographic for Business, tra cui annullamento della registrazione, georilevazione, password, installazione di app dall'App store, cookie e popup in Edge, Windows Defender, ricerca, cloud e archiviazione, connettività bluetooth, ora di sistema e dati di utilizzo in Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e8a1abb4229b3e6b4c91cfd49b4f66dbe739ea7d
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="device-restriction-settings-for-windows-holographic-for-business-in-intune"></a>Impostazioni relative alle restrizioni dei dispositivi per Windows Holographic for Business in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

## <a name="kiosk"></a>Modalità tutto schermo

In genere un'app specifica viene eseguita in un dispositivo in modalità tutto schermo. Agli utenti viene impedito l'accesso a qualsiasi funzionalità o funzione del dispositivo all'esterno dell'app in modalità tutto schermo.

- **Modalità tutto schermo**: identifica il tipo di modalità tutto schermo supportata dai criteri. Le opzioni includono:

  - **Non configurata** (impostazione predefinita): il criterio non abilita la modalità tutto schermo. 
  - **App singola per chiosco multimediale**: il profilo abilita il dispositivo perché esegua solo un'app. Quando l'utente accede, viene avviata un'app specifica. Questa modalità impedisce anche all'utente di aprire nuove app o modificare l'app in esecuzione.
  - **Più app in modalità tutto schermo**: il profilo abilita il dispositivo perché esegua più app. Solo le app aggiunte sono disponibili all'utente. Il vantaggio di avere più app in modalità tutto schermo, o un dispositivo predefinito per uno scopo, consiste nel garantire un'esperienza semplice, consentendo di accedere solo alle app necessarie e rimuovendo dalla visualizzazione le app non necessarie. 
  
    Quando si aggiungono app per un'esperienza costituita da più app in modalità a tutto schermo, si aggiunge anche un file di layout per il menu di avvio. Il [file di layout del menu di avvio](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune) include codice XML di esempio che è possibile usare in Intune. 

#### <a name="single-app-kiosks"></a>App singole per chioschi multimediali
Immettere le impostazioni seguenti:

- **Account utente**: immettere l'account utente locale (per il dispositivo) o l'account di accesso di Azure AD associato all'app in modalità tutto schermo. Per gli account aggiunti ai domini di Azure AD, immettere l'account nel formato `domain\username@tenant.org`. 

    Per i chioschi multimediali in ambienti pubblici con accesso automatico abilitato, è necessario usare un tipo di utente con privilegi minimi, ad esempio l'account utente standard locale. Per configurare un account Azure Active Directory (AD) per la modalità tutto schermo, usare il formato `AzureAD\user@contoso.com`.

- **ID modello utente applicazione (AUMID, Application User Model ID) dell'app**: immettere l'ID modello utente applicazione dell'app in modalità tutto schermo. Per altre informazioni, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata).

## <a name="reporting-and-telemetry"></a>Creazione di report e telemetria

- **Condividi i dati di utilizzo**: selezionare il livello di invio dei dati diagnostici.
