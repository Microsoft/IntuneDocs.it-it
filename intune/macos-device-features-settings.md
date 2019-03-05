---
title: Impostazioni delle funzionalità dei dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare tutte le impostazioni per configurare i dispositivi macOS per AirPrint in Microsoft Intune. Vedere anche i passaggi per ottenere l'indirizzo IP, il percorso e le impostazioni della porta di un server AirPrint in rete. Usare queste impostazioni in un profilo di configurazione del dispositivo per configurare i dispositivi macOS per l'uso dei server AirPrint nella rete.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0707226412d314ac1d44ba339b4c9151b394919
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233900"
---
# <a name="macos-device-feature-settings-in-intune"></a>Impostazioni relative alle funzionalità dei dispositivi macOS in Intune

Intune include alcune impostazioni predefinite per consentire agli utenti macOS di stampare su stampanti AirPrint in rete. L'articolo elenca queste impostazioni e descrive la funzione di ogni impostazione. Vengono inoltre elencati i passaggi per ottenere l'indirizzo IP, il percorso e la porta delle stampanti AirPrint tramite l'app Terminale (emulatore).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione dei dispositivi macOS](device-features-configure.md).

## <a name="airprint-settings"></a>Impostazioni AirPrint

1. In **Impostazioni** selezionare **AirPrint**. Immettere le proprietà seguenti del server AirPrint:

    - **Indirizzo IP**: immettere l'indirizzo IPv4 o IPv6 della stampante. Se si usano i nomi host per identificare le stampanti, è possibile ottenere l'indirizzo IP effettuando il ping della stampante nell'app Terminale. Per informazioni più dettagliate, vedere [Ottenere l'indirizzo IP e il percorso](#get-the-ip-address-and-path) (in questo articolo).
    - **Percorso**: immettere il percorso della stampante. il percorso è in genere `ipp/print` per le stampanti di rete. Per informazioni più dettagliate, vedere [Ottenere l'indirizzo IP e il percorso](#get-the-ip-address-and-path) (in questo articolo).
    - **Porta**: immettere la porta di ascolto della destinazione AirPrint. Se si omette questa proprietà, AirPrint usa la porta predefinita. Disponibile in iOS 11.0 e versioni successive.
    - **TLS**: scegliere **Abilita** per proteggere le connessioni AirPrint con Transport Layer Security (TLS). Disponibile in iOS 11.0 e versioni successive.

2. Selezionare **Aggiungi**. Il server AirPrint viene aggiunto all'elenco. È possibile aggiungere più server AirPrint.

    È anche possibile **importare** un file delimitato da virgole (CSV) che include un elenco delle stampanti AirPrint. Dopo aver aggiunto le stampanti AirPrint in Intune, è anche possibile **esportare** questo elenco.

3. Al termine, selezionare **OK** per salvare l'elenco.

## <a name="get-the-ip-address-and-path"></a>Ottenere l'indirizzo IP e il percorso

Per aggiungere i server AirPrinter, sono necessari l'indirizzo IP della stampante, il percorso della risorsa e la porta. La procedura seguente mostra come ottenere queste informazioni.

1. In un dispositivo Mac connesso alla stessa rete locale (subnet) delle stampanti AirPrint aprire **Terminale** (da **/Applicazioni/Utilità**).
2. Nell'app Terminale digitare `ippfind` e premere INVIO.

    Prendere nota delle informazioni della stampante. Ad esempio, potrebbe restituire un valore simile a `ipp://myprinter.local.:631/ipp/port1`. La prima parte è il nome della stampante. L'ultima parte (`ipp/port1`) è il percorso della risorsa.

3. Nel Terminale digitare `ping myprinter.local` e premere INVIO.

   Prendere nota dell'indirizzo IP. Ad esempio, potrebbe restituire un valore simile a `PING myprinter.local (10.50.25.21)`.

4. Usare i valori del percorso della risorsa e dell'indirizzo IP. In questo esempio l'indirizzo IP è `10.50.25.21` e il percorso della risorsa è `/ipp/port1`.

## <a name="next-steps"></a>Passaggi successivi

- Visualizzare tutte le impostazioni per i dispositivi [iOS](ios-device-features-settings.md).
- Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).
