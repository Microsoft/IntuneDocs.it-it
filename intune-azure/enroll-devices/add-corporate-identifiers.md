---
title: Aggiungere identificatori IMEI in Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come aggiungere gli identificatori aziendali (numeri IMEI) a Microsoft Intune. '
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: e0a853c34c6d38e8fae6f4712ba6c2b767e5d0ba
ms.lasthandoff: 03/22/2017

---

# <a name="add-corporate-identifiers"></a>Aggiungere identificatori aziendali

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Come amministratore IT è possibile creare e importare un file con valori delimitati da virgole (con estensione csv) che elenca i codici IMEI (International Mobile Equipment Identity) per identificare i dispositivi di proprietà dell'azienda. Per ogni codice IMEI, nell'elenco possono essere specificati dettagli per scopi amministrativi.

## <a name="create-a-csv-file"></a>Creare un file con estensione csv
Per creare l'elenco, generare un elenco di valori a due colonne, delimitato da virgole (file con estensione CSV) senza intestazione. Aggiungere l'identificatore IMEI nella colonna a sinistra e i dettagli nella colonna destra. Il testo dei dettagli può avere una lunghezza massima di 128 caratteri. Il limite corrente per ogni file con estensione csv è di 500 righe.

**Caricando un file con estensione csv contenente i numeri di serie**: creare un elenco delimitato da virgole (con estensione csv) composto da due colonne senza intestazione e limitato a 5.000 dispositivi o a 5 MB per ogni file con estensione csv.

|||
|-|-|
|&lt;IMEI n. 1&gt;|&lt;Dettagli sul dispositivo 1&gt;|
|&lt;IMEI n. 2&gt;|&lt;Dettagli sul dispositivo 2&gt;|

    This .csv file when viewed in a text editor appears as:

    ```
    01 234567 890123,device details
    02 234567 890123,device details
    ```

**Per aggiungere un elenco di identificatori aziendali con estensione CSV**

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Identificatori dei dispositivi aziendali**.

3. Se si sta importando un file con nuovi dettagli che sovrascriveranno quelli esistenti, selezionare **Sovrascrivere i dettagli per gli identificatori esistenti.** per sostituire i dettagli esistenti con i nuovi.

4. Passare al file CSV dei valori IMEI e selezionare **Aggiungi**.

> [!IMPORTANT]
> Alcuni dispositivi Android hanno più numeri IMEI. Intune archivia un numero IMEI per ogni dispositivo. Se si importa un numero IMEI che non corrisponde al numero IMEI specificato in Intune, il dispositivo verrà classificato come dispositivo personale anziché come dispositivo aziendale. Se si importano più numeri IMEI per un dispositivo, sarà visualizzato lo stato di registrazione **Sconosciuto** per i numeri non archiviati.

Una volta importati, questi dispositivi possono essere registrati o meno e possono avere lo stato **Registrato** o **Non contattato**. **Non contattato** significa che il dispositivo non ha mai eseguito la connessione al servizio Intune.

## <a name="delete-a-csv-list"></a>Eliminare un elenco con estensione csv

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Identificatori dei dispositivi aziendali**.

3. Scegliere **Elimina**.

Per specifiche dettagliate sui codici IMEI, vedere [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

