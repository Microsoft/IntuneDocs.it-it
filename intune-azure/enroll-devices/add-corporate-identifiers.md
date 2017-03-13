---
title: Aggiungere identificatori IMEI in Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come aggiungere gli identificatori aziendali (numeri IMEI) a Microsoft Intune. '
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 0d7c8eedbdad917a43d43d2e79ead5663e8e2871
ms.lasthandoff: 02/18/2017

---

# <a name="add-corporate-identifiers"></a>Aggiungere identificatori aziendali

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

È possibile creare un elenco di numeri IMEI(International Mobile Equipment Identity) per identificare i dispositivi aziendali. Questi dispositivi possono essere registrati o meno e presentano lo stato "Registrato" o "Non contattato". "Non contattato" significa che il dispositivo non effettua mai la connessione al servizio Intune.

Per creare l'elenco, generare un elenco di valori a due colonne, delimitato da virgole (file con estensione CSV) senza intestazione. Aggiungere l'identificatore IMEI nella colonna a sinistra e i dettagli nella colonna destra. Il limite massimo corrente per l'elenco è di 500 righe.

In un editor di testo, l'elenco CSV è simile al seguente:

01 234567 890123,dettagli del dispositivo</br>
02 234567 890123,dettagli del dispositivo

**Per aggiungere un elenco di identificatori aziendali con estensione CSV**

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Identificatori dei dispositivi aziendali**.

3. Se si sta importando un file con nuovi dettagli che sovrascriveranno quelli esistenti, selezionare **Sovrascrivere i dettagli per gli identificatori esistenti.** per sostituire i dettagli esistenti con i nuovi.

4. Passare al file CSV dei valori IMEI e selezionare **Aggiungi**.

**Per eliminare un elenco di identificatori aziendali con estensione CSV**

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Identificatori dei dispositivi aziendali**.

3. Scegliere **Elimina**.

