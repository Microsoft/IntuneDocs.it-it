---
title: Impostazioni di aggiornamento e modalità S di Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni e delle loro funzioni durante l'aggiornamento di un'edizione di Windows 10 in un dispositivo oppure abilitare la modalità S in un dispositivo tramite un profilo di configurazione del dispositivo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c34f683bfd16362dfb9af9a69c6f7d9b04860c7
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042189"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Impostazioni dei dispositivi Windows 10 e versioni successive per l'aggiornamento dell'edizione o per l'abilitazione della modalità S in Intune

Microsoft Intune include diverse impostazioni utili per la gestione e la protezione dei dispositivi. Questo articolo elenca e descrive le impostazioni per l'aggiornamento dell'edizione o per l'abilitazione della modalità S nei dispositivi Windows 10. Queste impostazioni vengono create in un profilo di configurazione dell'aggiornamento in Intune di cui viene eseguito il push o la distribuzione nei dispositivi.

Nell'ambito della soluzione di gestione di dispositivi mobili (MDM, Mobile Device Management) in uso, usare queste impostazioni per controllare le opzioni relative all'edizione e alla modalità S per i dispositivi Windows 10.

Per altre informazioni su questa funzionalità, vedere [Aggiornare le edizioni di Windows 10 o abilitare la modalità S](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare il profilo](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Aggiornamento dell'edizione

- **Edizione a cui eseguire l'aggiornamento**: selezionare l'edizione Windows 10 a cui si esegue l'aggiornamento. I dispositivi a cui è destinato questo criterio vengono aggiornati all'edizione che scelta.
- **Codice Product Key**: immettere il codice product key ricevuto da Microsoft. Dopo aver creato il criterio con il codice Product Key, la chiave non può essere aggiornata e viene nascosta per motivi di sicurezza. Per modificare il codice Product Key, immettere nuovamente l'intero codice.
- **File di licenza**: per l'edizione **Windows 10 Holographic for Business** o **Windows 10 Mobile**, scegliere **Sfoglia** per selezionare il file di licenza ricevuto da Microsoft. Il file di licenza include le informazioni di licenza delle edizioni a cui si stanno aggiornando i dispositivi.

## <a name="mode-switch"></a>Cambio di modalità

- **Nessuna configurazione**: un dispositivo in modalità S resta in modalità S. Un utente finale può disattivare la modalità S sul dispositivo.
- **Mantieni in modalità S**: impedisce all'utente finale di poter disattivare la modalità S sul dispositivo.
- **Switch** (Cambia): disattiva la modalità S sul dispositivo.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma potrebbe non essere ancora operativo. Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili di aggiornamento dell'edizione per dispositivi [Windows Holographic for Business](holographic-upgrade.md).
