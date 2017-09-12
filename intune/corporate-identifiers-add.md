---
title: Aggiungere identificatori aziendali a Intune
titlesuffix: Azure portal
description: Informazioni su come aggiungere gli identificatori aziendali (metodo di registrazione, numeri IMEI e numeri di serie) a Microsoft Intune. "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 85303c503e068ec23c8321b9359760775bbdb6f8
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="identify-devices-as-corporate-owned"></a>Identificare i dispositivi di proprietà dell'azienda

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'amministratore di Intune può identificare un dispositivo come di proprietà aziendale in diversi modi. Intune può raccogliere informazioni aggiuntive dai dispositivi di proprietà aziendale. È anche possibile configurare restrizioni per i dispositivi, in modo da impedire la registrazione da parte di dispositivi non appartenenti all'azienda.

Un dispositivo viene identificato come di proprietà aziendale se una delle condizioni seguenti risulta vera:

- Registrazione con un account di [manager di registrazione dispositivi](device-enrollment-manager-enroll.md) (tutte le piattaforme)
- Registrazione con Apple [Device Enrollment Program](device-enrollment-program-enroll-ios.md), [Apple School Manager](apple-school-manager-set-up-ios.md) o [Apple Configurator](apple-configurator-enroll-ios.md) (solo iOS)
- [Identificazione come di proprietà aziendale prima della registrazione](#identify-corporate-owned-devices-with-imei-or-serial-number) tramite numeri IMEI (International Mobile Equipment Identifier) nel caso di tutte le piattaforme con numeri IMEI oppure tramite i numeri di serie nel caso di iOS e Android
- Registrazione in Azure Active Directory o Enterprise Mobility + Security come dispositivo Windows 10 Enterprise (solo Windows 10)
- Identificazione come [dispositivo di proprietà aziendale](#change-device-ownership) nell'elenco delle proprietà del dispositivo

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identificare i dispositivi di proprietà aziendale con numero IMEI o numero di serie

Un amministratore di Intune può creare e importare un file con valori delimitati da virgole (con estensione csv) che elenca i numeri IMEI o i numeri di serie. Intune usa questi identificatori per specificare la proprietà aziendale del dispositivo durante la registrazione del dispositivo. È possibile dichiarare i numeri IMEI per tutte le piattaforme supportate. È possibile dichiarare solo il numero di serie per i dispositivi iOS e Android. Per ogni numero IMEI o numero di serie, nell'elenco possono essere specificati dettagli per scopi amministrativi.

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

### <a name="add-a-csv-list-of-corporate-identifiers"></a>Aggiungere un elenco di identificatori aziendali con estensione csv

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** e quindi fare clic su **Aggiungi**.

 ![Screenshot dell'area di lavoro Identificatori dei dispositivi aziendali con il pulsante Aggiungi evidenziato.](./media/add-corp-id.png)

2. Nel pannello **Aggiungi identificatori** specificare il tipo di identificatore, **IMEI** o **Numero di serie**. È possibile specificare se i numeri importati in precedenza debbano **Sovrascrivere i dettagli per gli identificatori esistenti**.

3. Fare clic sull'icona della cartella e specificare il percorso dell'elenco da importare. Passare al file con estensione csv e selezionare **Aggiungi**. È possibile fare clic su **Aggiorna** per visualizzare i nuovi identificatori di dispositivo.

I dispositivi importati non sono necessariamente registrati. I dispositivi possono avere lo stato **Registrato** o **Non contattato**. **Non contattato** significa che il dispositivo non ha mai eseguito la connessione al servizio Intune.

### <a name="delete-corporate-identifiers"></a>Eliminare gli identificatori aziendali

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali**.
2. Selezionare gli identificatori dei dispositivi da eliminare e quindi scegliere **Elimina**.
3. Confermare l'eliminazione.

L'eliminazione di un identificatore aziendale per un dispositivo registrato non comporta la modifica della proprietà del dispositivo. Per modificare la proprietà di un dispositivo, passare a **Dispositivi** > **Tutti i dispositivi**, selezionare il dispositivo, scegliere **Proprietà** e quindi modificare la **Proprietà del dispositivo**.

### <a name="imei-specifications"></a>Specifiche IMEI
Per specifiche dettagliate sui codici IMEI, vedere [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Modificare la proprietà del dispositivo

Le proprietà dei dispositivi mostrano la **Proprietà** per ogni record di dispositivo in Intune. L'amministratore può specificare i dispositivi come **Personale** o **Aziendale**.

**Per modificare la proprietà del dispositivo:**
1. In Intune nel portale di Azure passare a **Dispositivi** > **Tutti i dispositivi** e quindi scegliere il dispositivo.
3. Scegliere **Proprietà**.
4. Specificare la **Proprietà del dispositivo** come **Personale** o **Aziendale**.

  ![Screenshot delle proprietà del dispositivo che mostra le opzioni Categoria del dispositivo e Proprietà del dispositivo.](./media/device-properties.png)
