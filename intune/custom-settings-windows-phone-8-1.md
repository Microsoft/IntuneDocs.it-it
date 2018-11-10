---
title: Aggiungere impostazioni personalizzate ai dispositivi Windows Phone 8.1 in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Aggiungere o creare un profilo personalizzato per usare le impostazioni OMA-URI per i dispositivi che eseguono Windows Phone 8.1 in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f2202d7abf80c6a78fd365a4629e970bc9ec36ce
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983092"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Usare le impostazioni personalizzate per i dispositivi Windows Phone 8.1 in Intune

Con Microsoft Intune è possibile aggiungere o creare impostazioni personalizzate per i dispositivi Windows Phone 8.1 usando i "profili personalizzati". I profili personalizzati sono una funzionalità di Intune. Sono progettati per aggiungere impostazioni dei dispositivi e funzionalità non incluse in Intune.

I profili personalizzati Windows Phone 8.1 usano impostazioni Open Mobile Alliance Uniform Resource Identifier (OMA-URI) per configurare funzionalità diverse. Tali impostazioni vengono in genere usate dai produttori di dispositivi mobili per controllare le funzionalità del dispositivo.

Questo articolo descrive come creare un profilo personalizzato per i dispositivi Windows Phone 8.1. 

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il profilo, ad esempio `windows phone custom profile`.
    - **Descrizione:** immettere una descrizione per il profilo.
    - **Piattaforma**: scegliere **Windows Phone 8.1**.
    - **Tipo di profilo**: scegliere **Personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome univoco per l'impostazione OMA-URI per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuare il profilo.
    - **OMA-URI (maiuscole/minuscole)**: immettere il valore OMA-URI che si vuole usare come impostazione.
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

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. È ora necessario [assegnare il profilo](device-profile-assign.md).

Vedere come creare un profilo personalizzato nei [dispositivi Windows 10](custom-settings-windows-10.md).