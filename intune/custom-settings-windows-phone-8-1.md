---
title: Aggiungere impostazioni personalizzate ai dispositivi Windows Phone 8.1 in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Aggiungere o creare un profilo personalizzato per usare le impostazioni OMA-URI per i dispositivi che eseguono Windows Phone 8.1 in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 97d656db3e828ef3377b927395a283fe995bb8a4
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389288"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Usare le impostazioni personalizzate per i dispositivi Windows Phone 8.1 in Intune

Con Microsoft Intune è possibile aggiungere o creare impostazioni personalizzate per i dispositivi Windows Phone 8.1 usando i "profili personalizzati". I profili personalizzati sono una funzionalità di Intune. Sono progettati per aggiungere impostazioni dei dispositivi e funzionalità non incluse in Intune.

I profili personalizzati Windows Phone 8.1 usano impostazioni Open Mobile Alliance Uniform Resource Identifier (OMA-URI) per configurare funzionalità diverse. Tali impostazioni vengono in genere usate dai produttori di dispositivi mobili per controllare le funzionalità del dispositivo. [Documentazione relativa al protocollo Windows Phone 8.1 MDM](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) sono elencate le impostazioni.

Questo articolo descrive come creare un profilo personalizzato per i dispositivi Windows Phone 8.1. 

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il profilo, ad esempio `windows phone custom profile`.
    - **Descrizione:** immettere una descrizione per il profilo.
    - **Piattaforma**: scegliere **Windows Phone 8.1**.
    - **Tipo di profilo**: scegliere **Personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome univoco per l'impostazione OMA-URI per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuare il profilo.
    - **OMA-URI (maiuscole/minuscole)** : immettere il valore OMA-URI che si vuole usare come impostazione.
    - **Tipo di dati**: immettere il tipo di dati da usare per l'impostazione OMA-URI. Le opzioni disponibili sono:

        - Stringa
        - Stringa (file XML)
        - Data e ora
        - Integer
        - A virgola mobile
        - Boolean
        - Base64 (file)

    - **Valore**: immettere il valore dati da associare all'impostazione OMA-URI immessa. Il valore varia a seconda del tipo di dati selezionato. Ad esempio, se si sceglie **Data e ora**, selezionare il valore dalla selezione data.

    Dopo aver aggiunto alcune impostazioni, è possibile selezionare **Esporta**. **Esporta** crea un elenco di tutti i valori aggiunti in un file con valori delimitati da virgole (file con estensione csv).

5. Selezionare **OK** per salvare le modifiche. Continuare ad aggiungere altre impostazioni in base alle esigenze.
6. Al termine, scegliere **OK** > **Crea** per creare il profilo di Intune. Il profilo viene visualizzato nell'elenco **Configurazione del dispositivo - Profili**.

## <a name="example"></a>Esempio

Nell'esempio seguente, i dispositivi Windows 8.1 phone sono stati impediti la modifica di reti cellulari durante i viaggi di fuori dell'area di copertura del vettore.

- **Nome**: Consenti rete dati in Roaming
- **Descrizione**: consente o impedisce il roaming dei dati del cellulare
- **URI OMA** (maiuscole / minuscole): ./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **Tipo di dati:** Integer
- **Valore**: 0

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. È ora necessario [assegnare il profilo](device-profile-assign.md).

Vedere come creare un profilo personalizzato nei [dispositivi Windows 10](custom-settings-windows-10.md).
