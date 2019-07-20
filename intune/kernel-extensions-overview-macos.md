---
title: Creare un profilo di dispositivo delle estensioni kernel macOS con Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Aggiungere o creare un profilo di dispositivo macOS e quindi configurare le estensioni del kernel per consentire l'override degli utenti, aggiungere l'identificatore del team e un bundle e un identificatore del team in Microsoft Intune.
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
ms.openlocfilehash: eca4692189af9272d3d1fc427b4eba638d8b5b27
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882976"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Aggiungere le estensioni del kernel macOS in Intune

Nei dispositivi macOS è possibile aggiungere funzionalità a livello di kernel. Queste funzionalità accedono a parti del sistema operativo a cui i normali programmi non possono accedere. È possibile che l'organizzazione abbia esigenze o requisiti specifici che non sono disponibili in un'app, una funzionalità del dispositivo e così via. 

Per aggiungere estensioni del kernel a cui è sempre consentito il caricamento nei dispositivi, aggiungere "kernel Extensions" (KEXT) in Microsoft Intune e quindi distribuire tali estensioni nei dispositivi.

Si dispone, ad esempio, di un programma di analisi dei virus che analizza il dispositivo per ottenere contenuti dannosi. È possibile aggiungere l'estensione del kernel del programma Antivirus Scan come estensione del kernel consentita in Intune. Quindi, "assegnare" l'estensione ai dispositivi macOS.

Con questa funzionalità gli amministratori possono consentire agli utenti di eseguire l'override delle estensioni del kernel, aggiungere identificatori del team e aggiungere estensioni kernel specifiche in Intune.

Questa funzionalità si applica a:

- macOS 10.13.2 e versioni successive

Per usare questa funzionalità, i dispositivi devono essere:

- Registrato in Intune tramite la Device Enrollment Program di Apple (DEP). Per la [registrazione automatica dei dispositivi MacOS](device-enrollment-program-enroll-macos.md) sono presenti altre informazioni.

  OPPURE

- Registrato in Intune con "Iscrizione approvata dall'utente" (termine Apple). [Preparare le modifiche alle estensioni del kernel in MacOS High Sierra](https://support.apple.com/en-us/HT208019) (apre il sito Web di Apple) con ulteriori informazioni.

Intune usa "profili di configurazione" per creare e personalizzare queste impostazioni per le esigenze dell'organizzazione. Dopo aver aggiunto queste funzionalità in un profilo, è possibile eseguire il push del profilo o distribuirlo nei dispositivi macOS nell'organizzazione.

Questo articolo illustra come creare un profilo di configurazione del dispositivo usando le estensioni del kernel in Intune.

> [!TIP]
> Per altre informazioni sulle estensioni del kernel, vedere [Cenni preliminari sull'estensione kernel](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (aprire il sito Web di Apple).

## <a name="what-you-need-to-know"></a>Informazioni importanti

- È possibile aggiungere estensioni del kernel legacy senza segno.
- Assicurarsi di immettere l'identificatore del team e l'ID bundle corretti dell'estensione del kernel. Intune non convalida i valori immessi. Se si immettono informazioni errate, l'estensione non funzionerà nel dispositivo.

> [!NOTE]
> Apple ha rilasciato informazioni relative alla firma e all'autenticazione per tutti i software. In macOS 10.14.5 e versioni successive, le estensioni del kernel distribuite tramite Intune non devono soddisfare i criteri di autenticazione di Apple.
>
> Per informazioni sui criteri di autenticazione e sugli eventuali aggiornamenti o modifiche, vedere le risorse seguenti:
>
> - [Autenticazione dell'app prima della distribuzione](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (apre il sito Web di Apple) 
> - [Preparare le modifiche alle estensioni del kernel in MacOS High Sierra](https://support.apple.com/en-us/HT208019) (apre il sito Web di Apple)

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
