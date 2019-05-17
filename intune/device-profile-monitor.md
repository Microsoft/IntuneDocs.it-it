---
title: Visualizzare profili di dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare e gestire i dettagli dei profili di configurazione dei dispositivi in Microsoft Intune, visualizzare un grafico del numero di dispositivi assegnati a un profilo e visualizzare i dispositivi con profili assegnati o distribuiti. È anche possibile risolvere i problemi di profili con impostazioni che causano conflitto.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 786cd6e7d0acaeb6e78035d8ec580c30d29d09e7
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57391717"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Monitorare i profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune include alcune funzionalità nel portale di Azure, che consentono di monitorare e gestire i profili di configurazione dei dispositivi. È ad esempio possibile controllare lo stato di un profilo, visualizzare i dispositivi assegnati e aggiornare le proprietà di un profilo.

## <a name="view-existing-profiles"></a>Visualizzare i profili esistenti

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Profili**.

Tutti i profili esistenti sono elencati, includono dettagli come, ad esempio, la piattaforma e nell'elenco viene indicato se il profilo è assegnato a tutti i dispositivi.

## <a name="view-details-on-a-profile"></a>Visualizzare i dettagli su un profilo

Dopo avere creato il profilo del dispositivo, Intune fornisce i grafici. Questi grafici visualizzano lo stato di un profilo, ad esempio che è correttamente assegnato ai dispositivi oppure se il profilo mostra un conflitto.

1. Selezionare un profilo esistente. Selezionare, ad esempio, un profilo macOS.
2. Selezionare la scheda **Panoramica**.

    Il grafico in alto illustra il numero di dispositivi assegnati al profilo del dispositivo specifico. Se ad esempio il profilo di configurazione si applica ai dispositivi macOS, il grafico elencherà il conteggio dei dispositivi macOS.

    Visualizza anche il numero di dispositivi per le altre piattaforme a cui è assegnato lo stesso profilo di dispositivo. Visualizza, ad esempio, il conteggio dei dispositivi non macOS.

    ![Visualizzare il numero di dispositivi assegnati al profilo di dispositivo](./media/device-configuration-profile-graphical-chart.png)

    Il grafico in basso illustra il numero di utenti assegnati al profilo del dispositivo specifico. Se ad esempio il profilo di configurazione si applica agli utenti macOS, il grafico elencherà il conteggio degli utenti macOS.

3. Selezionare il cerchio nel grafico in alto. Si apre **Stato del dispositivo**.

    Sono elencati i dispositivi assegnati al profilo ed è indicato se il profilo è stato distribuito correttamente. Si noti anche che sono elencati solo i dispositivi con la piattaforma specifica (ad esempio, macOS).

    Chiudere i dettagli sullo **Stato del dispositivo**.

4. Selezionare il cerchio nel grafico in basso. Si apre la finestra **Stato dell'utente**. 

    Sono elencati gli utenti assegnati al profilo ed è indicato se il profilo è stato distribuito correttamente. Si noti anche che sono elencati solo gli utenti con la piattaforma specifica (ad esempio, macOS).

    Chiudere i dettagli sullo **Stato del dispositivo**.

5. Selezionare un profilo specifico nell'elenco **Profili**. È anche possibile modificare le proprietà esistenti:
  - **Proprietà**: modificare il nome o aggiornare le impostazioni esistenti.
  - **Assegnazioni**: includere o escludere i dispositivi a cui applicare i criteri. Scegliere **Gruppi selezionati** per scegliere gruppi specifici.
  - **Stato dispositivo**: Sono elencati i dispositivi assegnati al profilo ed è indicato se il profilo è stato distribuito correttamente. È possibile selezionare un dispositivo specifico per ottenere altri dettagli, incluse le app installate.
  - **Stato dell'utente**: elenca i nomi degli utenti con dispositivi interessati da questo profilo e indica se il profilo è stato distribuito correttamente. È possibile selezionare un utente specifico per ottenere altri dettagli.
  - **Stato per singola impostazione**: filtra l'output visualizzando le singole impostazioni nel profilo e indica se l'impostazione è stata applicata correttamente.

## <a name="view-conflicts"></a>Visualizzare i conflitti

In **Dispositivi** > **Tutti i dispositivi** è possibile visualizzare tutte le impostazioni che causano il conflitto. Quando si verifica un conflitto, vengono visualizzati anche tutti i profili di configurazione che contengono questa impostazione. Gli amministratori possono usare questa funzionalità per agevolare la risoluzione dei problemi e la correzione di eventuali discrepanze con i profili.

1. In Intune selezionare **Dispositivi** > **Tutti i dispositivi** > selezionare un dispositivo esistente nell'elenco. L'utente finale può ottenere il nome del dispositivo dall'app Portale aziendale.
2. Selezionare **Configurazione del dispositivo**. Vengono elencati tutti i criteri di configurazione che si applicano al dispositivo.
3. Selezionare il criterio. Vengono visualizzate tutte le impostazioni del criterio che si applicano al dispositivo. Se un dispositivo ha stato **Conflitto**, selezionare la riga. Nella nuova finestra vengono visualizzati tutti i profili e i nomi di profilo che includono l'impostazione che provoca il conflitto.

Ora che si conosce l'impostazione che causa il conflitto e i criteri che includono tale impostazione, dovrebbe essere più semplice risolvere il conflitto. 

## <a name="next-steps"></a>Passaggi successivi
[Assegnare profili utente e profili di dispositivo](device-profile-assign.md)  
[Problemi comuni e soluzioni per i profili di dispositivo](device-profile-troubleshoot.md)
