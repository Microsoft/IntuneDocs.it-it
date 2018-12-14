---
title: Impostazioni relative all'ottimizzazione recapito per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare la modalità di recapito degli aggiornamenti software ai dispositivi tramite i servizi cloud di ottimizzazione recapito disponibili per i dispositivi con Windows 10 e versioni successive. In Intune, creare un profilo di configurazione del dispositivo per installare gli aggiornamenti da Internet. Vedere anche come sostituire gli anelli di aggiornamento esistenti con un profilo di ottimizzazione recapito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36cfb5ac05b2d69b5c7349f4ebc6054848a08fc8
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52730402"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Impostazioni di ottimizzazione recapito per Windows 10 (e versioni successive) in Microsoft Intune

Questo articolo elenca e descrive tutte le impostazioni di ottimizzazione recapito che è possibile configurare per i dispositivi Windows 10. Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo e quindi assegnate o distribuite ai dispositivi con Microsoft Intune.

## <a name="settings"></a>Impostazioni

**Modalità di download con ottimizzazione recapito**: scegliere la modalità di recapito degli aggiornamenti ai dispositivi. Le opzioni disponibili sono:

- **Non configurata**: gli utenti finali aggiornano i propri dispositivi usando il metodo prescelto, che può essere usare **Windows Update** o le impostazioni di **Ottimizzazione recapito** disponibili con il sistema operativo.
- **Solo HTTP, senza peering**: ottenere gli aggiornamenti solo da Internet. Non è consentito ottenere aggiornamenti da altri computer nella rete (operazione nota come peering o peer-to-peer).
- **HTTP misto con peering nella stessa NAT/HTTP misto con peering in un gruppo privato**: ottenere gli aggiornamenti da Internet e da altri computer nella rete. Il peering si verifica per i dispositivi nello stesso sito di Active Directory (se presente) o nello stesso dominio. Quando questa opzione è selezionata, il peering attraversa gli indirizzi IP di NAT (Network Address Translation).
- **HTTP misto con peering Internet**: ottenere gli aggiornamenti da Internet e da altri computer nella rete.
- **Modalità di download semplice senza peering**: ottenere gli aggiornamenti da Internet, direttamente dal proprietario dell'aggiornamento, ad esempio Microsoft. Non vengono contattati i servizi cloud di ottimizzazione recapito.
- **Modalità Bypass**: usare BITS (Background Intelligent Transfer Service) per ottenere gli aggiornamenti. Non usare ottimizzazione recapito.

## <a name="move-from-existing-update-rings-to-delivery-optimization"></a>Passare dagli anelli di aggiornamento esistenti a ottimizzazione recapito

Le impostazioni **Aggiornamenti software - Anelli di aggiornamento di Windows 10** vengono sostituite dalle impostazioni di **Ottimizzazione recapito**. Gli anelli di aggiornamento esistenti possono essere facilmente modificati per usare le impostazioni di **Ottimizzazione recapito**. Unità di tempo:

1. Creare un profilo di configurazione di ottimizzazione recapito:

    1. In Intune selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
    2. Immettere un **Nome** e una **Descrizione** per il profilo.
    3. Per **Piattaforma** scegliere **Windows 10 e versioni successive**. Per **Tipo di profilo** scegliere **Ottimizzazione recapito**.
    4. Selezionare **Impostazioni**. Per **Modalità di download con ottimizzazione recapito**, scegliere la stessa modalità usata dall'anello di aggiornamento software esistente. Le opzioni disponibili sono:
        - **Non configurato**
        - **Solo HTTP, senza peering**
        - **HTTP misto con peering nella stessa NAT/HTTP misto con peering in un gruppo privato**
        - **HTTP misto con peering Internet**
        - **Modalità di download semplice senza peering**
        - **Modalità Bypass**

2. Assegnare questo nuovo profilo agli stessi dispositivi e utenti dell'anello di aggiornamento software esistente. La procedura è descritta in [Assegnare un profilo di dispositivo](device-profile-assign.md).

3. Annullare la configurazione dell'anello di aggiornamento software esistente:
    1. In Intune, passare ad **Aggiornamenti software** > Anelli di aggiornamento di Windows 10.
    2. Selezionare l'anello di aggiornamento nell'elenco.
    3. Nelle impostazioni, specificare **Non configurata** per **Modalità di download con ottimizzazione recapito**.
    4. **OK** > **Salva** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).