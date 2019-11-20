---
title: Impostazioni per dispositivi Windows Holographic for Business - Microsoft Intune - Azure | Microsoft Docs
description: Conoscere e configurare impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune per Windows Holographic for Business, tra cui annullamento della registrazione, georilevazione, password, installazione di app dall'App Store, cookie e popup in Microsoft Edge, Microsoft Defender, ricerca, cloud e archiviazione, connettività Bluetooth, orario di sistema e dati di utilizzo in Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1f90a5a13859ff19765e22444a84b9c11405af73
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059496"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Impostazioni dei dispositivi Windows Holographic for Business per consentire o limitare l'uso delle funzionalità tramite Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi Windows Holographic for Business, come Microsoft HoloLens. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per abilitare o disabilitare funzionalità, controllare le impostazioni di sicurezza e altro ancora.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Generale

- **Annullamento manuale della registrazione**: consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.
- **Cortana**: abilita o disabilita l'assistente vocale Cortana.
- **Georilevazione**: specifica se il dispositivo può usare le informazioni dei servizi di posizione.

## <a name="password"></a>Password

- **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
- **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività**: specifica che l'utente deve inserire una password per sbloccare il dispositivo.

## <a name="app-store"></a>App Store

- **Aggiorna automaticamente le app dallo Store**: consente l'aggiornamento automatico delle app installate da Microsoft Store.
- **Installazione di app attendibile**: consente il trasferimento locale delle app con certificato attendibile.
- **Sblocco dallo sviluppatore**: consente all'utente finale di modificare le impostazioni per gli sviluppatori Windows, ad esempio consentire il trasferimento locale delle app.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

- **Cookie**: consente al browser di salvare i cookie di Internet nel dispositivo.
- **Pop-up**: blocca le finestre popup del browser (si applica solo a Windows 10 Desktop).
- **Suggerimenti per la ricerca**: consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca.
- **Strumento per la gestione delle password**: abilita o disabilita la funzionalità di gestione password di Microsoft Edge.
- **Invia intestazioni DNT (Do Not Track)** : configura il browser Microsoft Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti.

## <a name="microsoft-defender-smart-screen"></a>Smart Screen di Microsoft Defender

- **SmartScreen per Microsoft Edge**: abilita SmartScreen di Microsoft Edge per l'accesso a siti e download di file.

## <a name="search"></a>Cerca

- **Cerca la posizione**: specifica se la ricerca può usare le informazioni sulla posizione. Informazioni su

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione

- **Account Microsoft**: consente all'utente di associare un account Microsoft al dispositivo.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività

- **Bluetooth**: controlla se l'utente può abilitare e configurare Bluetooth nel dispositivo.
- **Individuabilità di Bluetooth**: consente l'individuazione del dispositivo da altri dispositivi con la funzione Bluetooth attivata.
- **Annunci con Bluetooth**: consente al dispositivo di ricevere annunci tramite Bluetooth.

## <a name="control-panel-and-settings"></a>Pannello di controllo e impostazioni

- **Modifica dell'ora di sistema**: impedisce all'utente finale di modificare la data e l'ora del dispositivo.

## <a name="kiosk---obsolete"></a>Modalità tutto schermo - Obsoleta

Queste impostazioni sono di sola lettura e non possono essere modificate. Per configurare la modalità tutto schermo, vedere [Impostazioni della modalità tutto schermo](kiosk-settings-holographic.md).

In genere un'app specifica viene eseguita in un dispositivo in modalità tutto schermo. Agli utenti viene impedito l'accesso a qualsiasi funzionalità o funzione del dispositivo all'esterno dell'app in modalità tutto schermo.

- **Modalità tutto schermo**: identifica il tipo di modalità tutto schermo supportata dal criterio. Le opzioni includono:

  - **Non configurata** (impostazione predefinita): il criterio non abilita la modalità tutto schermo. 
  - **App singola per chiosco multimediale**: il profilo abilita il dispositivo perché esegua solo un'app. Quando l'utente accede, viene avviata un'app specifica. Questa modalità impedisce anche all'utente di aprire nuove app o modificare l'app in esecuzione.
  - **Più app in modalità tutto schermo**: il profilo abilita il dispositivo perché esegua più app. Solo le app aggiunte sono disponibili all'utente. Il vantaggio di avere più app in modalità tutto schermo, o un dispositivo predefinito per uno scopo, consiste nel garantire un'esperienza semplice, consentendo di accedere solo alle app necessarie e rimuovendo dalla visualizzazione le app non necessarie. 
  
    Quando si aggiungono app per un'esperienza costituita da più app in modalità a tutto schermo, si aggiunge anche un file di layout per il menu di avvio. Il [file di layout del menu di avvio](/hololens/hololens-kiosk#start-layout-file-for-mdm-intune-and-others) include codice XML di esempio che è possibile usare in Intune. 

### <a name="single-app-kiosks"></a>App singole per chioschi multimediali

Immettere le impostazioni seguenti:

- **Account utente**: immettere l'account utente locale (per il dispositivo) o l'account di accesso di Azure AD associato all'app in modalità tutto schermo. Per gli account aggiunti ai domini di Azure AD, immettere l'account nel formato `domain\username@tenant.org`. 

    Per i chioschi multimediali in ambienti pubblici con accesso automatico abilitato, è necessario usare un tipo di utente con privilegi minimi, ad esempio l'account utente standard locale. Per configurare un account Azure Active Directory (AD) per la modalità tutto schermo, usare il formato `AzureAD\user@contoso.com`.

- **ID modello utente applicazione (AUMID, Application User Model ID) dell'app**: immettere l'ID modello utente applicazione dell'app in modalità tutto schermo. Per altre informazioni, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata).

## <a name="reporting-and-telemetry"></a>Creazione di report e telemetria

- **Condividi i dati di utilizzo**: selezionare il livello di invio dei dati diagnostici.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
