---
title: Impostazioni della modalità tutto schermo per Windows Holographic for Business in Microsoft Intune - Azure | Microsoft Docs
description: Configurare i dispositivi Windows Holographic for Business per l'esecuzione di una o più app in modalità tutto schermo, personalizzare il menu Start, aggiungere app, visualizzare la barra della applicazioni e configurare un Web browser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aef2db158e0572c1eec056a1d6e33b4b97aea77a
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047029"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Impostazioni dei dispositivi Windows Holographic for Business per l'esecuzione come dispositivo in modalità tutto schermo in Intune

È possibile configurare i dispositivi Windows Holographic for Business per l'esecuzione di una o più app in modalità tutto schermo. Alcune funzionalità non sono supportate in Windows Holographic for Business.

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi Windows Holographic for Business. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per configurare i dispositivi Windows Holographic for Business da eseguire in modalità tutto schermo.

Come amministratore di Intune, è possibile creare e assegnare queste impostazioni ai dispositivi.

Per altre informazioni sulla funzionalità Modalità tutto schermo di Windows in Intune, vedere [Configurare le impostazioni a tutto schermo](kiosk-settings.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare il profilo](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>App singola per chioschi multimediali a schermo intero

Quando si sceglie la modalità App singola per chiosco multimediale a schermo intero, immettere le impostazioni seguenti:

- **Tipo di accesso utente**: selezionare **Account utente locale** per immettere l'account utente locale (per il dispositivo) oppure un account Microsoft associato all'app in modalità tutto schermo. I tipi di account utente con **accesso automatico** non sono supportati in Windows Holographic for Business.

- **Tipo di applicazione**: selezionare **App Store**.

- **App da eseguire in modalità tutto schermo**: scegliere **Aggiungi un'app dello Store** e selezionare un'app nell'elenco.

    Se l'elenco non include app, aggiungerne qualcuna seguendo la procedura in [App client](apps-add.md).

    Selezionare **OK** per salvare le modifiche.

## <a name="multi-app-kiosks"></a>Più app in modalità tutto schermo

Le app in questa modalità sono disponibili nel menu Start. Sono le uniche app che l'utente può aprire. Quando si sceglie la modalità tutto schermo per più app, immettere le impostazioni seguenti:

- **Specifica Windows 10 come destinazione nei dispositivi in modalità S**: scegliere **No**. La modalità S non è supportata in Windows Holographic for Business.

- **Tipo di accesso utente**: aggiungere uno o più account utente autorizzati a usare le app aggiunte. Le opzioni disponibili sono: 

  - **Accesso automatico**: opzione non supportata in Windows Holographic for Business.
  - **Account utente locale**: scegliere **Aggiungi** per aggiungere l'account utente locale (per il dispositivo). L'account specificato viene usato per accedere al chiosco multimediale.
  - **Utente o gruppo di Azure AD (Windows 10, versione 1803+)** : richiede le credenziali utente per accedere al dispositivo. Selezionare **Aggiungi** per scegliere utenti o gruppi di Azure AD nell'elenco. È possibile selezionare più utenti e gruppi. Scegliere **OK** per salvare le modifiche.
  - **Visitatore di HoloLens**: l'account del visitatore è un account Guest che non richiede credenziali utente o autenticazione, come descritto in [Concetti della modalità PC condiviso](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Applicazioni**: aggiungere le app da eseguire nel dispositivo in modalità tutto schermo. Ricordarsi che è possibile aggiungere più app.

  - **Aggiungi l'app dello Store**: selezionare un'app esistente aggiunta tramite [App client](apps-add.md). Se l'elenco non include alcuna app, è possibile ottenerle e [aggiungerle a Intune](store-apps-windows.md).
  - **Aggiungi app di Win32**: opzione non supportata in Windows Holographic for Business.
  - **Aggiungi in base all'ID modello utente applicazione**: usare questa opzione per aggiungere app predefinite di Windows. Immettere le proprietà seguenti: 

    - **Nome applicazione**: obbligatorio. Immettere un nome per l'applicazione.
    - **ID modello utente applicazione (AUMID)** : obbligatorio. Immettere l'ID modello utente applicazione (AUMID) dell'app Windows. Per ottenere questo ID, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata) per ottenere l'ID.
    - **Dimensioni del riquadro**: obbligatorio. Scegliere Piccolo, Medio o Grande per le dimensioni del riquadro.

- **Impostazioni del browser in modalità tutto schermo**: opzione non supportata in Windows Holographic for Business.

- **Usa un layout Start alternativo**: scegliere **Sì** per immettere un file XML che descrive come le app vengono visualizzate nel menu Start, incluso il relativo ordine. Usare questa opzione se è necessaria una maggiore personalizzazione nel menu Start. [Personalizzare ed esportare il layout della schermata Start](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) offre alcune indicazioni e include un file XML specifico per i dispositivi Windows Holographic for Business.

- **Barra delle applicazioni di Windows**: opzione non supportata in Windows Holographic for Business.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili in modalità tutto schermo per dispositivi [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) e [Windows 10 e versioni successive](kiosk-settings-windows.md).
