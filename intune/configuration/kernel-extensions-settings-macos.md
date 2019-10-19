---
title: impostazioni dell'estensione del kernel macOS in Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Aggiungere, configurare o creare impostazioni nei dispositivi macOS per usare le estensioni del kernel. Inoltre, consentire agli utenti di eseguire l'override delle estensioni approvate, consentire tutte le estensioni da un identificatore del team o consentire estensioni o app specifiche in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8632f5b8df0f483de3bb4d06a6823639ba52c604
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506705"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>impostazioni del dispositivo macOS per configurare e usare le estensioni del kernel in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo elenca e descrive le diverse impostazioni di estensione del kernel che è possibile controllare nei dispositivi macOS. Come parte della soluzione di gestione dei dispositivi mobili (MDM), usare queste impostazioni per aggiungere e gestire le estensioni del kernel nei dispositivi.

Per altre informazioni sulle estensioni del kernel in Intune ed eventuali prerequisiti, vedere Aggiungere le [estensioni del kernel MacOS](../kernel-extensions-overview-macos.md).

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo in Intune e quindi assegnate o distribuite ai dispositivi macOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione delle estensioni del kernel del dispositivo](../kernel-extensions-overview-macos.md).

> [!NOTE]
> Queste impostazioni si applicano a diversi tipi di registrazione. Per ulteriori informazioni sui diversi tipi di registrazione, vedere la pagina relativa alla [registrazione MacOS](../macos-enroll.md).

## <a name="kernel-extensions"></a>Estensioni del kernel

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>Le impostazioni si applicano a: approvazione utente, registrazione automatica del dispositivo

- **Consenti sostituzioni utente**: **Consenti** consente agli utenti di approvare le estensioni kernel non incluse nel profilo di configurazione. **Non configurato** (impostazione predefinita) impedisce agli utenti di consentire le estensioni non incluse nel profilo di configurazione. Ciò significa che sono consentite solo le estensioni incluse nel profilo di configurazione.

  Per ulteriori informazioni su questa funzionalità, vedere [caricamento dell'estensione del kernel approvato dall'utente](https://developer.apple.com/library/archive/technotes/tn2459/_index.html) (apre il sito Web di Apple).

- **Identificatori del team consentiti**: usare questa impostazione per consentire uno o molti ID team. Tutte le estensioni del kernel firmate con gli ID del team immessi sono consentite e attendibili. In altre parole, usare questa opzione per consentire tutte le estensioni del kernel nello stesso ID team, che può essere uno sviluppatore o un partner specifico.

  **Aggiungere** un identificatore del team di estensioni kernel valide e firmate che si vuole caricare. È possibile aggiungere più identificatori del team. L'identificatore del team deve essere alfanumerico (lettere e numeri) e contenere 10 caratteri. Immettere ad esempio `ABCDE12345`.

  Una volta aggiunto, l'identificatore del team può anche essere eliminato.

  [Individuare l'ID del team](https://help.apple.com/developer-account/#/dev55c3c710c) (aprire il sito Web di Apple) con ulteriori informazioni.

- **Estensioni del kernel consentite**: usare questa impostazione per consentire estensioni kernel specifiche. Solo le estensioni del kernel immesse sono consentite o attendibili. 

  **Aggiungere** l'identificatore del bundle e l'identificatore del team di un'estensione del kernel che si vuole caricare. Per le estensioni del kernel legacy senza segno, usare un identificatore del team vuoto. È possibile aggiungere più estensioni del kernel. L'identificatore del team deve essere alfanumerico (lettere e numeri) e contenere 10 caratteri. Ad esempio, immettere `com.contoso.appname.macos` per **Bundle ID**e `ABCDE12345` per **identificatore del team**.

  > [!TIP]
  > Per ottenere l'ID bundle di un'estensione del kernel (kext) in un dispositivo macOS, è possibile:
  >
  > 1. Nel terminale eseguire `kextstat | grep -v com.apple` e annotare l'output. Installare il software o il kext desiderato. Eseguire di nuovo `kextstat | grep -v com.apple` e cercare le modifiche.
  >
  >    Nel terminale `kextstat` elenca tutte le estensioni del kernel nel sistema operativo. 
  >
  > 2. Sul dispositivo aprire il file dell'elenco delle proprietà delle informazioni (info. plist) per un kext. Viene visualizzato l'ID bundle. Ogni kext dispone di un file INFO. plist archiviato all'interno di. 

> [!NOTE]
> Non è necessario aggiungere gli identificatori del team e le estensioni del kernel. È possibile configurare uno o l'altro.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](../device-profile-monitor.md).
