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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 25414cd42159d1c3e09b80d236ccb12f0df5662a
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017

---

# <a name="add-corporate-identifiers"></a>Aggiungere identificatori aziendali

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Come amministratore IT è possibile creare e importare un file con valori delimitati da virgole (con estensione csv) che elenca i codici IMEI (International Mobile Equipment Identity) per identificare i dispositivi di proprietà dell'azienda. Per ogni codice IMEI, nell'elenco possono essere specificati dettagli per scopi amministrativi.

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

## <a name="add-corporate-identifiers"></a>Aggiungere identificatori aziendali
Per creare l'elenco, generare un elenco di valori a due colonne, delimitato da virgole (file con estensione CSV) senza intestazione. Aggiungere l'identificatore IMEI nella colonna a sinistra e i dettagli nella colonna destra. I dettagli sono limitati a 128 caratteri e sono destinati esclusivamente a un uso amministrativo. Non sono visualizzati nel dispositivo. Il limite corrente per ogni file con estensione csv è di 500 righe.

**Caricando un file con estensione csv contenente i numeri di serie**: creare un elenco delimitato da virgole (con estensione csv) composto da due colonne senza intestazione e limitato a 5.000 dispositivi o a 5 MB per ogni file con estensione csv. 

|||
|-|-|
|&lt;IMEI n. 1&gt;|&lt;Dettagli sul dispositivo 1&gt;|
|&lt;IMEI n. 2&gt;|&lt;Dettagli sul dispositivo 2&gt;|

Il file con estensione CSV quando viene visualizzato in un editor di testo viene visualizzato come:

```
01234567890123,device details
02234567890123,device details
```


> [!IMPORTANT]
> Alcuni dispositivi Android hanno più numeri IMEI. Intune archivia un numero IMEI per ogni dispositivo. Se si importa un numero IMEI che non corrisponde al numero IMEI specificato in Intune, il dispositivo verrà classificato come dispositivo personale anziché come dispositivo aziendale. Se si importano più numeri IMEI per un dispositivo, sarà visualizzato lo stato di registrazione **Sconosciuto** per i numeri non archiviati.

**Per aggiungere un elenco di identificatori aziendali con estensione CSV**

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registrazione del dispositivo** > **Restrizioni registrazione**, scegliere **Identificatori dei dispositivi aziendali** e fare clic su **Aggiungi**.

3. Nel pannello **Aggiungi identificatori** specificare il tipo di identificatore, **IMEI**. È possibile specificare se i numeri importati in precedenza debbano **Sovrascrivere i dettagli per gli identificatori esistenti**.  

4. Fare clic sull'icona della cartella e specificare il percorso dell'elenco da importare. Passare al file CSV dei valori IMEI e selezionare **Aggiungi**.

Una volta importati, questi dispositivi possono essere registrati o meno e possono avere lo stato **Registrato** o **Non contattato**. **Non contattato** significa che il dispositivo non ha mai eseguito la connessione al servizio Intune.

## <a name="delete--corporate-identifiers"></a>Eliminare identificatori aziendali

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registrazione del dispositivo** > **Restrizioni registrazione**, scegliere **Identificatori dei dispositivi aziendali** e quindi **Elimina**.

3. Nel pannello **Delete Identifiers** (Elimina identificatori) individuare il file con estensione csv degli identificatori dei dispositivi da eliminare e fare clic su **Elimina**.

## <a name="imei-specifications"></a>Specifiche IMEI
Per specifiche dettagliate sui codici IMEI, vedere [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

