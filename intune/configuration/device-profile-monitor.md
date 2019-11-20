---
title: Visualizzare profili di dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare e gestire i dettagli dei profili di configurazione dei dispositivi in Microsoft Intune, visualizzare un grafico del numero di dispositivi assegnati a un profilo e visualizzare i dispositivi con profili assegnati o distribuiti. È anche possibile risolvere i problemi di profili con impostazioni che causano conflitto.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85ba34cfec8ebe78d2574034967bd7ed76f3304e
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059555"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Monitorare i profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune include alcune funzionalità che consentono di monitorare e gestire i profili di configurazione dei dispositivi. È ad esempio possibile controllare lo stato di un profilo, visualizzare i dispositivi assegnati e aggiornare le proprietà di un profilo.

## <a name="view-existing-profiles"></a>Visualizzare i profili esistenti

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione**.

Tutti i profili esistenti sono elencati, includono dettagli come, ad esempio, la piattaforma e nell'elenco viene indicato se il profilo è assegnato a tutti i dispositivi.

## <a name="view-details-on-a-profile"></a>Visualizzare i dettagli su un profilo

Dopo avere creato il profilo del dispositivo, Intune fornisce i grafici. Questi grafici visualizzano lo stato di un profilo, ad esempio che è correttamente assegnato ai dispositivi oppure se il profilo mostra un conflitto.

1. Selezionare un profilo esistente. Selezionare, ad esempio, un profilo macOS.
2. Selezionare la scheda **Panoramica**.

    Il grafico in alto illustra il numero di dispositivi assegnati al profilo del dispositivo. Se ad esempio il profilo di configurazione si applica ai dispositivi macOS, il grafico elencherà il conteggio dei dispositivi macOS.

    Visualizza anche il numero di dispositivi per le altre piattaforme a cui è assegnato lo stesso profilo di dispositivo. Visualizza, ad esempio, il conteggio dei dispositivi non macOS.

    ![Visualizzare il numero di dispositivi assegnati al profilo di dispositivo](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    Il grafico in basso illustra il numero di utenti assegnati al profilo del dispositivo. Se ad esempio il profilo di configurazione si applica agli utenti macOS, il grafico elencherà il conteggio degli utenti macOS.

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

In **Dispositivi** > **Tutti i dispositivi** è possibile visualizzare tutte le impostazioni che causano il conflitto. In presenza di un conflitto, vengono visualizzati anche tutti i profili di configurazione che contengono questa impostazione. Gli amministratori possono usare questa funzionalità per agevolare la risoluzione dei problemi e la correzione di eventuali discrepanze con i profili.

1. In Intune selezionare **Dispositivi** > **Tutti i dispositivi** > selezionare un dispositivo esistente nell'elenco. L'utente finale può ottenere il nome del dispositivo dall'app Portale aziendale.
2. Selezionare **Configurazione del dispositivo**. Vengono elencati tutti i criteri di configurazione che si applicano al dispositivo.
3. Selezionare il criterio. Vengono visualizzate tutte le impostazioni del criterio che si applicano al dispositivo. Se un dispositivo ha stato **Conflitto**, selezionare la riga. Nella nuova finestra vengono visualizzati tutti i profili e i nomi di profilo che includono l'impostazione che provoca il conflitto.

Ora che si conosce l'impostazione che causa il conflitto e i criteri che includono tale impostazione, dovrebbe essere più semplice risolvere il conflitto. 

## <a name="device-firmware-configuration-interface-profile-reporting"></a>Informazioni di report per il profilo dell'interfaccia di configurazione del firmware del dispositivo (DFCI)

> [!WARNING]
> Le funzionalità di monitoraggio dei profili DFCI sono in corso di creazione. Anche se DFCI è disponibile in anteprima pubblica, i dati di monitoraggio potrebbero risultare mancanti o incompleti.

Per i profili DFCI vengono prodotte informazioni di report in base alle singole impostazioni, analogamente ad altri profili di configurazione dei dispositivi. A seconda del supporto del produttore dell'interfaccia DFCI, alcune impostazioni potrebbero non essere applicabili.

Con le impostazioni del profilo DFCI, è possibile che vengano visualizzati gli stati seguenti:

- **Conforme**: questo stato indica quando un valore di impostazione nel profilo corrisponde all'impostazione nel dispositivo. Questo stato può verificarsi negli scenari seguenti:

  - Il profilo DFCI ha completato la configurazione dell'impostazione nel profilo.
  - Il dispositivo non ha la funzionalità hardware controllata dall'impostazione e l'impostazione del profilo è **Disabilitato**.
  - UEFI non consente a DFCI di disabilitare la funzionalità e l'impostazione del profilo è **Abilitato**.
  - Il dispositivo non dispone dell'hardware per disabilitare la funzionalità e l'impostazione del profilo è **Abilitato**.

- **Non applicabile**: questo stato indica quando un valore di impostazione nel profilo è **Abilitato** e l'impostazione corrispondente nel dispositivo non viene trovata. Questo stato può verificarsi se l'hardware del dispositivo non ha la funzionalità.

- **Non conforme**: questo stato indica quando un valore di impostazione nel profilo non corrisponde all'impostazione nel dispositivo. Questo stato può verificarsi negli scenari seguenti:

  - UEFI non consente a DFCI di disabilitare un'impostazione e l'impostazione del profilo è **Disabilitato**.
  - Il dispositivo non dispone dell'hardware per disabilitare la funzionalità e l'impostazione del profilo è **Disabilitato**.
  - Il dispositivo non ha la versione più recente del firmware DFCI.
  - L'interfaccia DFCI è stata disabilitata prima di essere registrata in Intune usando un controllo per il "rifiuto esplicito" locale nel menu UEFI.
  - Il dispositivo è stato registrato in Intune al di fuori della registrazione di Autopilot.
  - Il dispositivo non è stato registrato in Autopilot da un partner Microsoft CSP o è stato registrato direttamente dall'OEM.

## <a name="next-steps"></a>Passaggi successivi

[Domande, problemi e soluzioni comuni per i profili dei dispositivi](device-profile-troubleshoot.md)  
[Risolvere problemi relativi a criteri e profili in Intune](troubleshoot-policies-in-microsoft-intune.md)
