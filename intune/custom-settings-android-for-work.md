---
title: Aggiungere impostazioni personalizzate ai dispositivi Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo personalizzato per i dispositivi aziendali Android in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 73075ed06e98ca987e87a7cfda70c546127bf881
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179593"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Usare le impostazioni personalizzate per i dispositivi Android Enterprise in Microsoft Intune

Con Microsoft Intune è possibile aggiungere o creare impostazioni personalizzate per i dispositivi Android Enterprise usando un "profilo personalizzato". I profili personalizzati sono una funzionalità di Intune. Sono progettati per aggiungere impostazioni dei dispositivi e funzionalità non incluse in Intune.

I profili personalizzati Android Enterprise usano impostazioni Open Mobile Alliance Uniform Resource Identifier (OMA-URI) per controllare le funzionalità nei dispositivi Android Enterprise. Queste impostazioni vengono in genere usate dai produttori di dispositivi mobili per controllare le funzionalità.

Intune supporta un numero limitato di profili personalizzati Android.

Questo articolo descrive come creare un profilo personalizzato per i dispositivi Android Enterprise. L'articolo offre anche un esempio di profilo personalizzato che blocca l'operazione di copia e incolla.

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il profilo, ad esempio `android enterprise custom profile`
    - **Descrizione**: immettere una descrizione per il profilo
    - **Piattaforma**: scegliere **Android Enterprise**
    - **Tipo di profilo**: scegliere **Personalizzato**

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome univoco per l'impostazione OMA-URI in modo da poterla individuare facilmente.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altri dettagli importanti.
    - **OMA-URI**: immettere l'OMA-URI da usare come impostazione.
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

In questo esempio viene creato un profilo personalizzato che limita le operazioni di copia e incolla tra app aziendali e personali nei dispositivi Android Enterprise.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il profilo, ad esempio `android ent block copy paste custom profile`.
    - **Descrizione:** immettere una descrizione per il profilo.
    - **Piattaforma**: scegliere **Android Enterprise**.
    - **Tipo di profilo**: scegliere **Personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome come `Block copy and paste`.
    - **Descrizione**: immettere una descrizione come `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: immettere `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Tipo di dati**: scegliere **Booleano** in modo che il valore per l'OMA-URI sia **True** o **False**.
    - **Valore**: scegliere **True**.

5. Dopo aver immesso le impostazioni, l'ambiente avrà un aspetto simile all'immagine seguente:

    ![Bloccare copia e incolla per il profilo di lavoro Android.](./media/custom-policy-afw-copy-paste.png)

Quando si assegna il profilo ai dispositivi Android Enterprise gestiti, le operazioni di copia e incolla verranno bloccate tra le app incluse nei profili aziendali e personali.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. È ora necessario [assegnare il profilo](device-profile-assign.md).

Vedere come [creare il profilo nei dispositivi Android](custom-settings-android.md).