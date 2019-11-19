---
title: Impostazioni relative all'ottimizzazione recapito per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare l'uso dell'ottimizzazione recapito nei dispositivi Windows 10 gestiti con Intune. In Intune, creare un profilo di configurazione del dispositivo per installare gli aggiornamenti da Internet. Vedere anche come sostituire gli anelli di aggiornamento esistenti con un profilo di ottimizzazione recapito.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 908319c588fe2a1bf55a376d3f02a03db780a3ad
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755394"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Impostazioni di ottimizzazione recapito in Microsoft Intune

Con Intune, è possibile usare le impostazioni di ottimizzazione recapito per i dispositivi Windows 10 per ridurre il consumo di larghezza di banda quando tali dispositivi scaricano aggiornamenti e applicazioni. L'ottimizzazione recapito viene impostata come parte dei profili di configurazione dei dispositivi.  

Questo articolo descrive come configurare le impostazioni di ottimizzazione recapito come parte di un profilo di configurazione del dispositivo. Dopo aver creato un profilo, lo si assegna o distribuisce ai dispositivi Windows 10. 

Per un elenco delle impostazioni di ottimizzazione recapito supportate da Intune, vedere [Impostazioni di ottimizzazione recapito per Intune](../delivery-optimization-settings.md).  

Per informazioni sull'ottimizzazione recapito in Windows 10, vedere [Ottimizzazione recapito per gli aggiornamenti](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) nella documentazione di Windows.  

> [!NOTE]
> Le impostazioni **Aggiornamenti software - Anelli di aggiornamento di Windows 10** vengono sostituite dalle impostazioni di **Ottimizzazione recapito**. È possibile modificare gli anelli di aggiornamento esistenti in modo da usare le impostazioni di **Ottimizzazione recapito**. [Passare anelli di aggiornamento esistenti all'ottimizzazione recapito](#move-existing-update-rings-to-delivery-optimization) (in questo articolo)

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
    - **Tipo di profilo**: selezionare **Ottimizzazione recapito**.

4. Scegliere **Impostazioni** > **Configura** e definire come scaricare aggiornamenti e app. Per informazioni sulle impostazioni disponibili, vedere [Impostazioni di ottimizzazione recapito per Intune](../delivery-optimization-settings.md).

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco. [Assegnare il profilo](device-profile-assign.md) e quindi [monitorarne lo stato](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Passare anelli di aggiornamento esistenti all'ottimizzazione recapito

Le impostazioni di **Ottimizzazione recapito** sostituiscono **Aggiornamenti software - Anelli di aggiornamento di Windows 10**. Gli anelli di aggiornamento esistenti possono essere facilmente modificati per usare le impostazioni di **Ottimizzazione recapito**. Per mantenere le stesse impostazioni quando si crea un profilo di ottimizzazione recapito, usare la stessa impostazione per *Modalità di download con ottimizzazione recapito* e quindi configurare le stesse impostazioni già in uso. È tuttavia possibile scegliere di riconfigurare le impostazioni di ottimizzazione recapito per sfruttare la gamma completa di impostazioni aggiuntive che il profilo di ottimizzazione recapito può gestire.

1. Creare un profilo di configurazione di ottimizzazione recapito:

    1. Nell'interfaccia di amministrazione di Microsoft Endpoint Manager selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
    2. Immettere le proprietà seguenti:

        - **Nome**: immettere un nome descrittivo per il nuovo profilo.
        - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
        - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
        - **Tipo di profilo**: selezionare **Ottimizzazione recapito**.
        - **Impostazioni**: Per **Modalità di download con ottimizzazione recapito**, scegliere la stessa modalità usata dall'anello di aggiornamento software esistente, a meno che non si voglia cambiare le impostazioni applicate ai dispositivi. Le opzioni disponibili sono:
            - **Non configurato**
            - **Solo HTTP, senza peering**
            - **HTTP misto con peering nella stessa NAT**
            - **HTTP misto con peering in un gruppo privato**
            - **HTTP misto con peering Internet**
            - **Modalità di download semplice senza peering**
            - **Modalità Bypass**
    3. Configurare eventuali impostazioni aggiuntive da gestire.

2. Assegnare questo nuovo profilo agli stessi dispositivi e utenti dell'anello di aggiornamento software esistente. La procedura è descritta in [Assegnare un profilo di dispositivo](device-profile-assign.md).

3. Annullare la configurazione dell'anello di aggiornamento software esistente:
    1. Nell'interfaccia di amministrazione di Microsoft Endpoint Manager passare ad **Aggiornamenti software** > Anelli di aggiornamento di Windows 10.
    2. Selezionare l'anello di aggiornamento nell'elenco.
    3. Nelle impostazioni specificare **Non configurata** per **Modalità di download con ottimizzazione recapito**.
    4. **OK** > **Salva** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).  
Visualizzare le [impostazioni di ottimizzazione recapito](../delivery-optimization-settings.md) per Intune.
