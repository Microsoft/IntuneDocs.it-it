---
title: Limitare le funzionalità dei i dispositivi tramite i criteri in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere un profilo del dispositivo per limitare le funzionalità dei dispositivi Android, macOS, iOS, iPadOS, Windows Phone e Windows 10 in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c86252030a4baf957077cd889386bb8016554f1
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206568"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune



Intune include criteri di limitazioni dei dispositivi che consentono agli amministratori di controllare i dispositivi Android, iOS, macOS e Windows. Queste limitazioni consentono di controllare una vasta gamma di impostazioni e funzionalità per proteggere le risorse dell'organizzazione. Gli amministratori sono ad esempio in grado di:

- Consentire o bloccare l'uso della fotocamera del dispositivo
- Controllare l'accesso a Google Play, App Store, visualizzazione di documenti e giochi
- Bloccare app predefinite o creare un elenco di app consentite o non consentite
- Consentire o impedire il backup di file nel cloud e negli account di archiviazione
- Impostare una lunghezza minima per le password e bloccare le password semplici

Queste funzionalità sono disponibili in Intune e possono essere configurate dall'amministratore. Intune usa "profili di configurazione" per creare e personalizzare queste impostazioni per le esigenze dell'organizzazione. Dopo aver aggiunto queste funzionalità a un profilo, è possibile eseguire il push del profilo o distribuirlo nei dispositivi dell'organizzazione.

Questo articolo illustra come creare un profilo di limitazioni del dispositivo. È anche possibile visualizzare tutte le impostazioni disponibili per le varie piattaforme.

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di criterio valido è **iOS: Blocca fotocamera nei dispositivi**.
    - **Descrizione**: immettere una descrizione del criterio. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:  

        - **Android**
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 e versioni successive**
        - **Windows 10 e versioni successive**

    - **Tipo di profilo**: Selezionare **Limitazioni del dispositivo**.

        Per creare un profilo di restrizione per dispositivi Windows 10 Team come Surface Hub, scegliere **Limitazioni del dispositivo (Windows 10 Team)** .

4. Le impostazioni configurabili variano in base alla piattaforma scelta. Scegliere la piattaforma per le impostazioni dettagliate:

    - [Impostazioni Android](../device-restrictions-android.md)
    - [Impostazioni Android Enterprise](../device-restrictions-android-for-work.md)
    - [Impostazioni di iOS/iPadOS](device-restrictions-ios.md)
    - [Impostazioni macOS](device-restrictions-macos.md)
    - [Impostazioni Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Impostazioni Windows 10](device-restrictions-windows-10.md)
    - [Impostazioni Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Impostazioni di Windows Holographic for Business](device-restrictions-windows-holographic.md)

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Dopo averlo creato, il profilo è pronto per l'assegnazione. [Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](../device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
