---
title: Impostazioni relative all'ottimizzazione recapito per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare l'uso dell'ottimizzazione recapito nei dispositivi Windows 10 gestiti con Intune. In Intune, creare un profilo di configurazione del dispositivo per installare gli aggiornamenti da Internet. Vedere anche come sostituire gli anelli di aggiornamento esistenti con un profilo di ottimizzazione recapito.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124810"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Impostazioni di ottimizzazione recapito in Microsoft Intune

Con Intune, usare le impostazioni di Ottimizzazione recapito per i dispositivi Windows 10 per ridurre il consumo di larghezza di banda quando tali dispositivi scaricano aggiornamenti e applicazioni. Configurare Ottimizzazione recapito come parte dei profili di configurazione dei dispositivi.  

Questo articolo descrive come configurare le impostazioni di ottimizzazione recapito come parte di un profilo di configurazione del dispositivo. Dopo aver creato un profilo, lo si assegna o distribuisce ai dispositivi Windows 10. 

Per visualizzare un elenco delle impostazioni di Ottimizzazione recapito supportate da Intune, vedere [Impostazioni di Ottimizzazione recapito per Intune](../delivery-optimization-settings.md).  

Per informazioni sull'ottimizzazione recapito in Windows 10, vedere [Ottimizzazione recapito per gli aggiornamenti](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) nella documentazione di Windows.  

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
    - **Tipo di profilo**: selezionare **Ottimizzazione recapito**.

4. Scegliere **Impostazioni** > **Configura** e definire come scaricare aggiornamenti e app. Per informazioni sulle impostazioni disponibili, vedere [Impostazioni di ottimizzazione recapito per Intune](../delivery-optimization-settings.md).

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco. [Assegnare il profilo](device-profile-assign.md) e quindi [monitorarne lo stato](device-profile-monitor.md).

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>Rimuovere Ottimizzazione recapito dagli anelli di aggiornamento di Windows 10

Ottimizzazione recapito è una funzionalità precedentemente configurata come parte degli anelli di aggiornamento software. A partire da febbraio 2019, le impostazioni di Ottimizzazione recapito sono configurate come parte di un profilo di configurazione del dispositivo di Ottimizzazione del recapito, che include impostazioni aggiuntive con effetti più ampi del recapito degli aggiornamenti software ai dispositivi. Se non è già stato fatto, rimuovere l'impostazione di Ottimizzazione recapito dagli anelli di aggiornamento impostandola su *Non configurato* e quindi usare un profilo di Ottimizzazione recapito per gestire la gamma più ampia di opzioni disponibili.

1. Creare un profilo di configurazione del dispositivo di Ottimizzazione recapito:

    1. Nell'interfaccia di amministrazione di Microsoft Endpoint Manager selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
    2. Immettere le proprietà seguenti:

        - **Nome**: immettere un nome descrittivo per il nuovo profilo.
        - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
        - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
        - **Tipo di profilo**: selezionare **Ottimizzazione recapito**.
        - **Settings** (Impostazioni): Per **Modalità di download con ottimizzazione recapito**, scegliere la stessa modalità usata dall'anello di aggiornamento software esistente, a meno che non si voglia cambiare le impostazioni applicate ai dispositivi. Le opzioni disponibili sono:
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
