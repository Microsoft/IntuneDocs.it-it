---
title: Visualizzare profili di dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare e gestire i dettagli dei profili di configurazione dei dispositivi in Microsoft Intune e visualizzare un grafico del numero di dispositivi assegnati a un profilo e i dispositivi con profili assegnati o distribuiti.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1c2eb08db58940ed575b3dea011395edd6711fc
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2018
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Monitorare i profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune include alcune funzionalità nel portale di Azure, che consentono di monitorare e gestire i profili di configurazione dei dispositivi. È ad esempio possibile controllare lo stato di un profilo, visualizzare i dispositivi assegnati e aggiornare le proprietà di un profilo.

## <a name="view-existing-profiles"></a>Visualizzare i profili esistenti

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Profili**.

Tutti i profili esistenti sono elencati e includono dettagli indicanti, ad esempio, la piattaforma e se il profilo è assegnato a tutti i dispositivi.

## <a name="view-details-on-a-profile"></a>Visualizzare i dettagli su un profilo

Dopo avere creato il profilo del dispositivo, Intune fornisce i grafici. Questi grafici visualizzano lo stato di un profilo, ad esempio che è correttamente assegnato ai dispositivi oppure se il profilo mostra un conflitto.

1. Selezionare un profilo esistente. Selezionare, ad esempio, un profilo macOS.
2. Selezionare la scheda **Panoramica**.

    Il grafico mostra il numero di dispositivi assegnati al profilo del dispositivo specifico. Se ad esempio il profilo di configurazione si applica ai dispositivi macOS, il grafico elencherà il conteggio dei dispositivi macOS.

    Visualizza anche il numero di dispositivi per le altre piattaforme a cui è assegnato lo stesso profilo di dispositivo. Visualizza, ad esempio, il conteggio dei dispositivi non macOS.

    ![Visualizzare il numero di dispositivi assegnati al profilo di dispositivo](./media/device-configuration-profile-graphical-chart.png)

3. Selezionare il cerchio nel grafico. Si apre **Stato del dispositivo**.

    Sono elencati i dispositivi assegnati al profilo ed è indicato se il profilo è stato distribuito correttamente. Si noti anche che sono elencati solo i dispositivi con la piattaforma specifica (ad esempio, macOS).

    Chiudere i dettagli sullo stato del dispositivo.

4. Nelle proprietà del profilo (**Profiles** > selezionare un profilo specifico) è anche possibile modificare le proprietà esistenti:
  - **Proprietà**: modificare il nome o aggiornare le impostazioni esistenti.
  - **Assegnazioni**: includere o escludere i dispositivi a cui applicare i criteri. Scegliere **Gruppi selezionati** per scegliere gruppi specifici.
  - **Stato del dispositivo**: sono elencati i dispositivi assegnati al profilo ed è indicato se il profilo è stato distribuito correttamente. È possibile selezionare un dispositivo specifico per ottenere altri dettagli, incluse le app installate.
  - **Stato dell'utente**: elenca i nomi degli utenti con i dispositivi interessati da questo profilo e indica se il profilo è stato distribuito correttamente. È possibile selezionare un utente specifico per ottenere altri dettagli.
  - **Stato per singola impostazione**: filtra l'output visualizzando le singole impostazioni nel profilo e indica se l'impostazione è stata applicata correttamente.

## <a name="next-steps"></a>Passaggi successivi
[Assegnare profili utente e profili di dispositivo](device-profile-assign.md)  
[Problemi comuni e soluzioni per i profili di dispositivo](device-profile-troubleshoot.md)