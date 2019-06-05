---
title: Impostazioni della modalità tutto schermo per dispositivi Windows e Holographic in Microsoft Intune - Azure | Microsoft Docs
description: Configurare i dispositivi Windows 10 e versioni successive e Windows Holographic for Business per l'esecuzione di una o più app in modalità tutto schermo, personalizzare il menu Start, aggiungere app, visualizzare la barra della applicazioni e configurare un Web browser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19641a36cf429773a8c0e06a90ee279d2baa06f7
ms.sourcegitcommit: 063177c6c365fef3642edd7c455790958469aad9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412247"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Impostazioni dei dispositivi Windows 10 e Windows Holographic for Business per l'esecuzione come dispositivo in modalità tutto schermo dedicato tramite Intune

Nei dispositivi Windows 10 usare Intune per eseguire i dispositivi come chiosco multimediale, talvolta noto anche come dispositivo dedicato. Un dispositivo nella modalità tutto schermo può eseguire un'app o molte app. È possibile visualizzare e personalizzare un menu Start, aggiungere app diverse, incluse app Win32, aggiungere una specifica home page per un Web browser e molto altro. 

Questa funzionalità si applica ai dispositivi che eseguono:

- Windows 10 e versioni successive
- Windows Holographic for Business

Intune supporta un profilo in modalità a tutto schermo per ogni dispositivo. Se servono più profili per la modalità tutto schermo in un singolo dispositivo, è possibile usare un [OMA-URI personalizzato](custom-settings-windows-10.md).

Intune usa "profili di configurazione" per creare e personalizzare queste impostazioni per le esigenze dell'organizzazione. Dopo aver aggiunto queste funzionalità in un profilo, eseguire il push o distribuire queste impostazioni ai gruppi nell'organizzazione.

Questo articolo illustra come creare un profilo di configurazione del dispositivo. Per un elenco di tutte le impostazioni e delle operazioni corrispondenti, vedere [Impostazioni della modalità tutto schermo per Windows 10](kiosk-settings-windows.md) e [Impostazioni della modalità tutto schermo per Windows Holographic for Business](kiosk-settings-holographic.md).

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:

   - **Nome**: immettere un nome descrittivo per il nuovo profilo.
   - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
   - **Piattaforma**: selezionare **Windows 10 e versioni successive**
   - **Tipo di profilo**: selezionare **Modalità tutto schermo**

4. In **Impostazioni** selezionare una **modalità tutto schermo**. La **modalità tutto schermo** identifica il tipo di modalità tutto schermo supportata dal criterio. Le opzioni includono:

    - **Non configurata** (impostazione predefinita): il criterio non abilita la modalità tutto schermo.
    - **App singola per chiosco multimediale a schermo intero**: il dispositivo viene eseguito con un singolo account utente e bloccato su una singola app dello Store. Pertanto, quando l'utente accede, viene avviata un'app specifica. Questa modalità impedisce anche all'utente di aprire nuove app o modificare l'app in esecuzione.
    - **App multiple per chiosco multimediale**: il dispositivo esegue più app dello Store, app Win32 o app predefinite di Windows tramite ID modello utente applicazione (AUMID). Solo le app aggiunte sono disponibili nel dispositivo.

        Il vantaggio di avere più app in modalità tutto schermo, o un dispositivo predefinito per uno scopo, consiste nel garantire un'esperienza semplice, consentendo di accedere solo alle app necessarie e rimuovendo dalla visualizzazione le app non necessarie.

    Per un elenco di tutte le impostazioni e delle operazioni corrispondenti, vedere:
      - [Impostazioni della modalità tutto schermo per Windows 10](kiosk-settings-windows.md)
      - [Impostazioni della modalità tutto schermo per Windows Holographic for Business](kiosk-settings-holographic.md)

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche. 

Il profilo verrà creato e visualizzato nell'elenco dei profili. È ora necessario [assegnare](device-profile-assign.md) il profilo.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È possibile creare profili in modalità tutto schermo per i dispositivi che eseguono le piattaforme seguenti:
- [Android](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 e versioni successive](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
