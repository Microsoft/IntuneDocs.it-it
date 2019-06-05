---
title: Creare profili di dispositivo iOS o macOS in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di dispositivo iOS o macOS e quindi configurare le impostazioni per AirPrint, layout della schermata iniziale, notifiche delle app, dispositivi condivisi, Single Sign-On e filtro del contenuto Web in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a5c85c936e49c277b54b542f372f97b247d6a37
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373813"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Aggiungere impostazioni relative alle funzionalità dei dispositivi iOS e macOS in Intune

Intune include molte funzionalità e numerose impostazioni che consentono agli amministratori di controllare i dispositivi iOS e macOS. Gli amministratori sono ad esempio in grado di:

- Consentire agli utenti l'accesso alle stampanti AirPrint presenti nella rete
- Aggiungere alla schermata iniziale app e cartelle, nonché nuove pagine
- Scegliere se e come visualizzare le notifiche delle app
- Configurare la schermata di blocco in modo da visualizzare un messaggio o il tag asset, in particolare per i dispositivi condivisi
- Offrire agli utenti un'esperienza Single Sign-On sicura per la condivisione delle credenziali tra app diverse
- Filtrare i siti Web che usano un linguaggio non adatto ai minori e consentire o bloccare siti Web specifici

Queste funzionalità sono disponibili in Intune e possono essere configurate dall'amministratore. Intune usa "profili di configurazione" per creare e personalizzare queste impostazioni per le esigenze dell'organizzazione. Dopo aver aggiunto queste funzionalità in un profilo, è possibile eseguire il push o distribuire il profilo nei dispositivi iOS e macOS nell'organizzazione.

Questo articolo illustra come creare un profilo di configurazione del dispositivo. È anche possibile visualizzare tutte le impostazioni disponibili per i dispositivi [iOS](ios-device-features-settings.md) e [macOS](macos-device-features-settings.md).

## <a name="create-a-device-profile"></a>Creare un profilo del dispositivo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare la piattaforma in uso:
        - **iOS**
        - **macOS**
    - **Tipo di profilo**: selezionare **Funzionalità dei dispositivi**.
    - **Impostazioni**: immettere le impostazioni da configurare. Per un elenco di tutte le impostazioni e delle operazioni corrispondenti, vedere:

        - [iOS](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. Al termine, selezionare **OK** e quindi scegliere **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco. Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo averlo creato, il profilo è pronto per l'assegnazione. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Visualizzare tutte le impostazioni delle funzionalità per i dispositivi [iOS](ios-device-features-settings.md) e [macOS](macos-device-features-settings.md).
