---
title: Impostazioni dei dispositivi condivisi Windows Holographic Business - Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere e usare dispositivi Windows Holographic for Business condivisi o usati da più utenti in Microsoft Intune. Visualizzare un elenco delle impostazioni di Gestione account e delle loro funzioni nei dispositivi, inclusi i dispositivi Microsoft HoloLens.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 428025e5e56450fd859f6bf2c9a990cbdca4f263
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835113"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Impostazioni di Windows Holographic for Business per gestire i dispositivi condivisi con Intune

I dispositivi Windows Holographic for Business, ad esempio Microsoft HoloLens, possono essere usati da più utenti. I dispositivi con più utenti, detti dispositivi condivisi, fanno parte di soluzioni di gestione di dispositivi mobili (MDM, Mobile Device Management).

Con Microsoft Intune gli utenti possono accedere a tali dispositivi condivisi con un account Guest. Quando usano il dispositivo, possono accedere solo alle funzionalità loro consentite.

Questo articolo elenca e descrive le impostazioni usate in un profilo di configurazione di dispositivi Windows Holographic for Business e versioni successive. Quando il profilo viene creato in Intune, l'amministratore lo distribuisce o lo assegna ai gruppi di dispositivi nell'organizzazione. Il profilo può anche essere assegnato a un gruppo di dispositivi contenente tipi di dispositivo e versioni del sistema operativo diversi.

Per altre informazioni su questa funzionalità in Intune, vedere [Controllare l'accesso, gli account e le funzionalità di risparmio energia nei PC condivisi o nei dispositivi con più utenti](shared-user-device-settings.md). Per altre informazioni sul provider di servizi di configurazione di Windows, vedere [AccountManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp) (Provider di servizi di configurazione AccountManagement).

## <a name="before-your-begin"></a>Prima di iniziare

[Creare il profilo](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Impostazioni dei dispositivi multiutente condivisi

> [!NOTE]
> I dispositivi che eseguono Windows Holographic for Business, tra cui i dispositivi Microsoft HoloLens, supportano solo le impostazioni **Gestione account**. Se si configura una delle altre impostazioni visualizzate in Intune, inclusa l'impostazione **Modalità Computer condiviso**, tale configurazione non influirà su questi dispositivi.

- **Gestione account**: impostare su **Abilita** per eliminare automaticamente gli account locali creati dagli utenti Guest e gli account in AD e in Azure AD. Quando un utente si disconnette dal dispositivo o quando viene eseguita la manutenzione del sistema, questi account vengono eliminati. Quando l'opzione è abilitata, impostare anche:
  - **Eliminazione account**: scegliere quando eliminare gli account: **In corrispondenza della soglia di spazio di archiviazione**, **In corrispondenza della soglia di spazio di archiviazione e della soglia di inattività** o **Immediatamente dopo la disconnessione**. Specificare anche:
    - **Soglia di inizio dell'eliminazione (%)**: immettere una percentuale (0-100) di spazio su disco. Quando lo spazio totale di archiviazione o su disco scende sotto il valore specificato, vengono eliminati gli account memorizzati nella cache. Gli account vengono eliminati in modo continuo per recuperare spazio su disco. Gli account inattivi da più tempo vengono eliminati per primi.
    - **Soglia di interruzione dell'eliminazione (%)**: immettere una percentuale (0-100) di spazio su disco. Quando lo spazio totale di archiviazione o su disco corrisponde al valore specificato, l'eliminazione viene interrotta.

  Impostare su **Disabilita** per mantenere gli account locali, AD e Azure AD creati dagli utenti guest.

  > [!NOTE]
  > I dispositivi Microsoft HoloLens supportano solo le impostazioni **Gestione account**.

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
- Vedere le impostazioni per [Windows 10 e versioni successive](shared-user-device-settings-windows.md).
