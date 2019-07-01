---
title: Crea profilo di dispositivo kernel le estensioni di macOS con Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Aggiungere o creare profili di dispositivo macOS e quindi configurare le estensioni del kernel per consentire l'override dell'utente, aggiungere l'identificatore di team e un identificatore di bundle e il team in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403906"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Aggiungere le estensioni di kernel macOS in Intune

Nei dispositivi macOS, è possibile aggiungere funzionalità a livello di kernel. Queste funzionalità di accedere alle parti del sistema operativo che non possono accedere a programmi regolari. L'organizzazione può avere specifiche esigenze o requisiti che non sono disponibili in un'app, una funzionalità del dispositivo e così via. 

Per aggiungere le estensioni di kernel che sono sempre consentite il caricamento dei dispositivi, aggiungere "estensioni kernel" (KEXT) in Microsoft Intune e quindi distribuire queste estensioni per i dispositivi.

Ad esempio, si dispone di un programma antivirus che esegue l'analisi del dispositivo per il contenuto dannoso. È possibile aggiungere questa estensione kernel del programma antivirus come un'estensione del kernel consentito in Intune. Quindi, "assegnare" l'estensione per i dispositivi macOS.

Con questa funzionalità, gli amministratori possono consentire agli utenti di eseguire l'override delle estensioni di kernel, aggiungere gli identificatori di team e aggiungere le estensioni specifiche del kernel in Intune.

Questa funzionalità si applica a:

- macOS 10.13.2 e versioni successive

Per usare questa funzionalità, i dispositivi devono essere:

- Registrati in Intune con Apple Device Enrollment Program (DEP). [Registrare automaticamente i dispositivi macOS](device-enrollment-program-enroll-macos.md) contiene ulteriori informazioni.

  OPPURE

- Registrati in Intune con la "registrazione approvato dall'utente" (termine di Apple). [Preparare le modifiche alle estensioni del kernel in macOS High Sierra](https://support.apple.com/en-us/HT208019) (apre i siti web di Apple) contiene altre informazioni.

Intune usa "profili di configurazione" per creare e personalizzare queste impostazioni per le esigenze dell'organizzazione. Dopo aver aggiunto queste funzionalità in un profilo, è possibile eseguire il push del profilo o distribuirlo nei dispositivi macOS nell'organizzazione.

Questo articolo illustra come creare un profilo di configurazione dispositivo con le estensioni del kernel in Intune.

> [!TIP]
> Per altre informazioni sulle estensioni del kernel, vedere [panoramica delle estensioni di kernel](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (apre i siti web di Apple).

## <a name="what-you-need-to-know"></a>Informazioni importanti

- È possibile aggiungere le estensioni del kernel legacy non firmato.
- Assicurarsi di immettere l'identificatore di team corretto e ID dell'estensione per il kernel del bundle. Intune non convalida i valori che immessi. Se si immettono informazioni errate, l'estensione non funzionerà sul dispositivo.

> [!NOTE]
> Apple ha rilasciato informazioni relative alla firma e notarization per tutto il software. In macOS 10.14.5 e kernel più recente, le estensioni distribuite tramite Intune non sono necessario soddisfare criteri notarization di Apple.
>
> Per informazioni su questo criterio notarization e tutti gli aggiornamenti o modifiche, vedere le risorse seguenti:
>
>  - [L'app prima della distribuzione notarizing](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (si apre sito web il) 
>  - [Preparare le modifiche alle estensioni del kernel in macOS High Sierra](https://support.apple.com/en-us/HT208019) (si apre sito web il)

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Descrizione:** immettere una descrizione per il profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **macOS**
    - **Tipo di profilo**: selezionare **estensioni**.
    - **Impostazioni**: immettere le impostazioni da configurare. Per un elenco di tutte le impostazioni e delle operazioni corrispondenti, vedere:

        - [macOS](kernel-extensions-settings-macos.md)

4. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco. Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo averlo creato, il profilo è pronto per l'assegnazione. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
