---
title: Aggiungere identificatori IMEI in Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come aggiungere gli identificatori aziendali (numeri IMEI) a Microsoft Intune. '
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: d8cb15d1b8c1c100f15084e43d2c3c4633fd64b5
ms.openlocfilehash: f12d538b1f4cd327b893d234f2b558185cdd9d85
ms.lasthandoff: 03/09/2017

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

> [!IMPORTANT]
> Alcuni dispositivi Android hanno più numeri IMEI. Intune archivia un numero IMEI per ogni dispositivo. Se si importa un numero IMEI che non corrisponde al numero IMEI specificato in Intune, il dispositivo verrà classificato come dispositivo personale anziché come dispositivo aziendale. Se si importano più numeri IMEI per un dispositivo, sarà visualizzato lo stato di registrazione **Sconosciuto** per i numeri non archiviati.

**Per eliminare un elenco di identificatori aziendali con estensione CSV**

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Identificatori dei dispositivi aziendali**.

3. Scegliere **Elimina**.

