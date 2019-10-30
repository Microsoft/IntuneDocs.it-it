---
title: Aggiungere identificatori aziendali a Intune
titleSuffix: ''
description: Informazioni su come aggiungere gli identificatori aziendali (metodo di registrazione, numeri IMEI e numeri di serie) a Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3d98a0e3c5bd2a5c11c9aa72d791306dfbe6578
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503308"
---
# <a name="identify-devices-as-corporate-owned"></a>Identificare i dispositivi di proprietà dell'azienda

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'amministratore di Intune può identificare i dispositivi di proprietà dell'azienda per perfezionare la gestione e l'identificazione. Con Intune è possibile eseguire attività di gestione aggiuntive e raccogliere altre informazioni, ad esempio il numero di telefono completo e un inventario delle app dai dispositivi di proprietà dell'azienda. È anche possibile configurare restrizioni per impedire la registrazione da parte di dispositivi che non sono di proprietà dell'azienda.

Al momento della registrazione, Intune assegna automaticamente lo stato di proprietà dell'azienda ai dispositivi caratterizzati da:

- Registrazione con un account di [manager di registrazione dispositivi](device-enrollment-manager-enroll.md) (tutte le piattaforme)
- Registrazione con Apple [Device Enrollment Program](device-enrollment-program-enroll-ios.md), [Apple School Manager](apple-school-manager-set-up-ios.md) o [Apple Configurator](apple-configurator-enroll-ios.md) (solo iOS)
- [Identificazione come di proprietà aziendale prima della registrazione](#identify-corporate-owned-devices-with-imei-or-serial-number) tramite numeri IMEI (International Mobile Equipment Identifier) nel caso di tutte le piattaforme con numeri IMEI oppure tramite i numeri di serie nel caso di iOS e Android
- Associazione ad Azure Active Directory con credenziali aziendali o dell'istituto di istruzione. [I dispositivi registrati in Azure Active Directory ](https://docs.microsoft.com/azure/active-directory/devices/overview) verranno contrassegnati come personali.
- Impostazione come proprietà aziendale [nell'elenco delle proprietà del dispositivo](#change-device-ownership)

Dopo la registrazione, è possibile [modificare l'impostazione della proprietà](#change-device-ownership) tra **Personale** e **Aziendale**.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identificare i dispositivi di proprietà aziendale con numero IMEI o numero di serie

Un amministratore di Intune può creare e importare un file con valori delimitati da virgole (con estensione csv) che elenca i numeri IMEI o i numeri di serie a 14 cifre. Intune usa questi identificatori per specificare la proprietà aziendale del dispositivo durante la registrazione del dispositivo. Per ogni numero IMEI o numero di serie, nell'elenco possono essere specificati dettagli per scopi amministrativi.

Questa funzionalità è supportata nelle piattaforme seguenti:

| Piattaforma | Numeri IMEI | Numeri di serie |
|---|---|---|
| Windows | Supportato (Windows Phone) | Non supportato |
| iOS/macOS | Non supportato | Supportato |
| Android OS v10 gestito con gestione dispositivi | Non supportato | Non supportato |
| Altri dispositivi Android | Non supportato | Supportato |

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Informazioni su come trovare il numero di serie di un dispositivo Apple](https://support.apple.com/HT204308).<br>
[Informazioni su come trovare il numero di serie di un dispositivo Android](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Aggiungere identificatori aziendali usando un file con estensione csv
Per creare l'elenco, generare un elenco di valori a due colonne, delimitato da virgole (file con estensione CSV) senza intestazione. Aggiungere i numeri IMEI o i numeri di serie a 14 cifre nella colonna sinistra e i dettagli nella colonna destra. È possibile importare un solo tipo di ID, numero IMEI o numero di serie in un singolo file con estensione csv. I dettagli sono limitati a 128 caratteri e sono destinati esclusivamente a un uso amministrativo. Non sono visualizzati nel dispositivo. Il limite corrente per ogni file CSV è di 5.000 righe.

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
> Alcuni dispositivi Android e iOS hanno più numeri IMEI. Intune legge solo un numero IMEI per ogni dispositivo registrato. Se si importa un numero IMEI che non corrisponde al numero IMEI specificato in Intune, il dispositivo viene classificato come dispositivo personale anziché come dispositivo di proprietà dell'azienda. Se si importano più numeri IMEI per un dispositivo, viene visualizzato lo stato di registrazione **Sconosciuto** per i numeri non archiviati.<br>
>Notare anche quanto segue: I numeri di serie sono il formato di identificazione consigliato per i dispositivi iOS.
>non è garantito che i numeri di serie Android siano univoci o attuali. Contattare il fornitore del dispositivo per determinare se il numero di serie è un ID dispositivo affidabile.
>I numeri di serie specificati dal dispositivo in Intune potrebbero non corrispondere all'ID visualizzato nei menu Impostazioni o Info di Android nel dispositivo. Verificare il tipo di numero di serie specificato dal produttore del dispositivo.
>Il tentativo di caricare un file con numeri di serie contenenti punti (.) causerà l'esito negativo del caricamento. I numeri di serie con punti non sono supportati.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Caricare un elenco di identificatori aziendali con estensione csv

1. Accedere ad [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), scegliere **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** > **Aggiungi** > **Carica il file CSV**.

   ![Area di lavoro Identificatori dei dispositivi aziendali con il pulsante Aggiungi evidenziato](./media/corporate-identifiers-add/add-corp-id.png)

2. Nel pannello **Aggiungi identificatori** specificare il tipo di identificatore: **IMEI** o **Di serie**.

3. Fare clic sull'icona della cartella e specificare il percorso dell'elenco da importare. Passare al file con estensione csv e scegliere **Aggiungi**. 

4. Se il file con estensione csv contiene identificatori aziendali già presenti in Intune, ma con dettagli diversi, viene visualizzata la finestra popup **Verifica gli identificatori duplicati**. Selezionare gli identificatori che si vuole sovrascrivere in Intune e scegliere **Ok** per aggiungerli. Per ogni identificatore viene confrontato solo il primo duplicato.

## <a name="manually-enter-corporate-identifiers"></a>Immettere manualmente gli identificatori aziendali

1. Accedere ad [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), scegliere **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** > **Aggiungi** > **Immetti manualmente**.

2. Nel pannello **Aggiungi identificatori** specificare il tipo di identificatore: **IMEI** o **Di serie**.

3. Immettere **Identificatore** e **Dettagli** per ogni identificatore da aggiungere. Al termine dell'inserimento degli identificatori, scegliere **Aggiungi**.

5. Se sono stati immessi identificatori aziendali già presenti in Intune, ma con dettagli diversi, viene visualizzata la finestra popup **Verifica gli identificatori duplicati**. Selezionare gli identificatori che si vuole sovrascrivere in Intune e scegliere **Ok** per aggiungerli. Per ogni identificatore viene confrontato solo il primo duplicato.

È possibile fare clic su **Aggiorna** per visualizzare i nuovi identificatori di dispositivo.

I dispositivi importati non sono necessariamente registrati. I dispositivi possono avere lo stato **Registrato** o **Non contattato**. **Non contattato** significa che il dispositivo non ha mai eseguito la connessione al servizio Intune.

## <a name="delete-corporate-identifiers"></a>Eliminare gli identificatori aziendali

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), scegliere **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali**.
2. Selezionare gli identificatori dei dispositivi da eliminare e quindi scegliere **Elimina**.
3. Confermare l'eliminazione.

L'eliminazione di un identificatore aziendale per un dispositivo registrato non comporta la modifica della proprietà del dispositivo. Per modificare la proprietà di un dispositivo, passare a **Dispositivi**, selezionare il dispositivo, scegliere **Proprietà** e quindi modificare **Proprietà del dispositivo**.

## <a name="imei-specifications"></a>Specifiche IMEI
Per specifiche dettagliate sui codici IMEI, vedere [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Modificare la proprietà del dispositivo

Le proprietà dei dispositivi mostrano la **Proprietà** per ogni record di dispositivo in Intune. L'amministratore può specificare i dispositivi come **Personale** o **Aziendale**. Quando il tipo di proprietà di un dispositivo viene modificato da personale a aziendale, Intune elimina tutte le informazioni sulle app raccolte in precedenza dal dispositivo entro 7 giorni. Se applicabile, Intune eliminerà anche il numero di telefono in archivio. 

**Per modificare la proprietà del dispositivo:**
1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), passare a **Dispositivi** e scegliere il dispositivo.
2. Scegliere **Proprietà**.
3. Specificare la **Proprietà del dispositivo** come **Personale** o **Aziendale**.

   ![Proprietà del dispositivo che mostrano le opzioni Categoria del dispositivo e Proprietà del dispositivo](./media/corporate-identifiers-add/device-properties.png)
