---
title: Aggiungere identificatori IMEI in Intune
titleSuffix: Intune on Azure
description: Informazioni su come aggiungere gli identificatori aziendali (numeri IMEI) a Microsoft Intune. "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b38bf2da70537d07a050fa21be9a2a3062ca84b
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="add-corporate-identifiers"></a>Aggiungere identificatori aziendali

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Come amministratore di Intune, è possibile creare e importare un file con valori delimitati da virgole (con estensione csv) che elenca i numeri IMEI (International Mobile Equipment Identity) o i numeri di serie. Intune usa questi identificatori per specificare la proprietà aziendale del dispositivo. È possibile dichiarare i numeri IMEI per tutte le piattaforme supportate. È possibile dichiarare solo il numero di serie per i dispositivi iOS e Android. Per ogni numero IMEI o numero di serie, nell'elenco possono essere specificati dettagli per scopi amministrativi.

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

[Informazioni su come trovare il numero di serie di un dispositivo Apple](https://support.apple.com/HT204308).<br>
[Informazioni su come trovare il numero di serie di un dispositivo Android](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers"></a>Aggiungere identificatori aziendali
Per creare l'elenco, generare un elenco di valori a due colonne, delimitato da virgole (file con estensione CSV) senza intestazione. Aggiungere i numeri IMEI o i n numeri di serie nella colonna sinistra e i dettagli nella colonna destra. È possibile importare un solo tipo di ID, numero IMEI o numero di serie in un singolo file con estensione csv. I dettagli sono limitati a 128 caratteri e sono destinati esclusivamente a un uso amministrativo. Non sono visualizzati nel dispositivo. Il limite corrente per ogni file con estensione csv è di 500 righe.

**Caricando un file con estensione csv contenente i numeri di serie**: creare un elenco delimitato da virgole (con estensione csv) composto da due colonne senza intestazione e limitato a 5.000 dispositivi o a 5 MB per ogni file con estensione csv.

|||
|-|-|
|&lt;ID 1&gt;|&lt;Dettagli sul dispositivo 1&gt;|
|&lt;ID 2&gt;|&lt;Dettagli sul dispositivo 2&gt;|

Il file con estensione CSV quando viene visualizzato in un editor di testo viene visualizzato come:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Alcuni dispositivi Android hanno più numeri IMEI. Intune legge solo un numero IMEI per ogni dispositivo registrato. Se si importa un numero IMEI che non corrisponde al numero IMEI specificato in Intune, il dispositivo viene classificato come dispositivo personale anziché come dispositivo di proprietà dell'azienda. Se si importano più numeri IMEI per un dispositivo, viene visualizzato lo stato di registrazione **Sconosciuto** per i numeri non archiviati.<br>
>Si noti anche che non è garantito che i numeri di serie Android siano univoci o attuali. Contattare il fornitore del dispositivo per determinare se il numero di serie è un ID dispositivo affidabile.
>I numeri di serie specificati dal dispositivo in Intune potrebbero non corrispondere all'ID visualizzato nei menu Impostazioni o Info di Android nel dispositivo. Verificare il tipo di numero di serie specificato dal produttore del dispositivo.


**Per aggiungere un elenco di identificatori aziendali con estensione CSV**

1. Nel portale di Intune scegliere **Registrazione del dispositivo** > **Restrizioni registrazione**, scegliere **Identificatori dei dispositivi aziendali** e quindi fare clic su **Aggiungi**.

 ![Screenshot dell'area di lavoro Identificatori dei dispositivi aziendali con il pulsante Aggiungi evidenziato.](./media/add-corp-id.png)

2. Nel pannello **Aggiungi identificatori** specificare il tipo di identificatore, **IMEI** o **Numero di serie**. È possibile specificare se i numeri importati in precedenza debbano **Sovrascrivere i dettagli per gli identificatori esistenti**.

3. Fare clic sull'icona della cartella e specificare il percorso dell'elenco da importare. Passare al file con estensione csv e selezionare **Aggiungi**. È possibile fare clic su **Aggiorna** per visualizzare i nuovi identificatori di dispositivo.

I dispositivi importati non sono necessariamente registrati. I dispositivi possono avere lo stato **Registrato** o **Non contattato**. **Non contattato** significa che il dispositivo non ha mai eseguito la connessione al servizio Intune.

## <a name="delete-corporate-identifiers"></a>Eliminare gli identificatori aziendali

1. Nel portale di Intune scegliere **Registrazione del dispositivo** > **Restrizioni registrazione**, scegliere **Identificatori dei dispositivi aziendali** e quindi **Elimina**.

3. Nel pannello **Delete Identifiers** (Elimina identificatori) individuare il file con estensione csv degli identificatori dei dispositivi da eliminare e fare clic su **Elimina**.

## <a name="imei-specifications"></a>Specifiche IMEI
Per specifiche dettagliate sui codici IMEI, vedere [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).
