---
title: Impostazioni del profilo personalizzato di Intune per i profili di lavoro Android
titlesuffix: Microsoft Intune
description: Informazioni su come creare impostazioni di profilo personalizzato di Microsoft Intune per dispositivi del profilo di lavoro Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109c50acf194598017aa507a0979ad3b9298de9e
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905292"
---
# <a name="create-intune-custom-profile-settings-for-android-work-profile-devices"></a>Creare impostazioni del profilo personalizzato di Intune per i dispositivi del profilo di lavoro Android

Usare i criteri di configurazione personalizzati del profilo di lavoro Android in Intune per assegnare le impostazioni URI OMA che possono essere usate per controllare le funzionalità nei dispositivi del profilo di lavoro Android. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di assegnare le impostazioni Android non configurabili con i criteri di Intune. Intune supporta attualmente un numero limitato di criteri personalizzati Android. Vedere gli esempi in questo articolo per scoprire quali criteri è possibile configurare.

## <a name="create-a-custom-profile"></a>Creare un profilo personalizzato

1. Per iniziare, usare le istruzioni illustrate in [Come configurare le impostazioni dispositivo personalizzate](custom-settings-configure.md). Per **Piattaforma** scegliere **Android Enterprise** e per **Tipo di profilo** scegliere **Personalizzato**.
2. Nel pannello **Impostazioni URI OMA personalizzate** scegliere **Aggiungi** per aggiungere una nuova impostazione.
3. Nel pannello **Aggiungi riga** configurare quanto segue:
    - **Nome**: immettere un nome univoco per le impostazioni personalizzate del profilo di lavoro Android per poterle identificare nel portale di Azure.
    - **Descrizione**: immettere una descrizione di carattere generale sui criteri personalizzati Android e altre informazioni rilevanti per consentirne l'individuazione.
    - **URI OMA**: immettere l'URI OMA per cui si vuole specificare un'impostazione.
    - **Tipo di dati**: selezionare il tipo di dati in cui verrà specificata questa impostazione URI OMA. Scegliere tra **Stringa**, **Stringa (file XML)**, **Data e ora**, **Integer**, **Virgola mobile**, **Booleano** o **Base64 (file)**.
    - **Valore**: specificare il valore da associare all'impostazione URI OMA specificata in precedenza. Il metodo usato per specificare questo valore varia in base al tipo di dati selezionato. Ad esempio, se si sceglie **Data e ora**, è necessario scegliere il valore da un selezione data.
4. Al termine, scegliere OK per ritornare a **Impostazioni URI OMA personalizzate** e quindi aggiungere altre impostazioni o scegliere **Crea** per creare il profilo personalizzato.


## <a name="example"></a>Esempio

In questo esempio verrà creato un profilo personalizzato che può essere usato per determinare se le azioni di copia e incolla tra app aziendali e personali sono consentite nei dispositivi del profilo di lavoro Android.

1. Usare la procedura di questo articolo per creare un profilo personalizzato per i dispositivi del profilo di lavoro Android con i valori seguenti:
    - **Nome**: immettere "Blocca copia e incolla" o testo di propria scelta.
    - **Descrizione**: immettere "Blocca copia e incolla tra app aziendali e personali" o testo di propria scelta.
    - **URI OMA**: immettere **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**.
    - **Tipo di dati**: selezionare **Booleano** per indicare che il valore per questo URI OMA è **True** o **False**.
    - **Valore**: Selezionare **True**.
2. Le impostazioni dovrebbero essere simili a quelle dell'immagine seguente.
![Bloccare copia e incolla per il profilo di lavoro Android.](./media/custom-policy-afw-copy-paste.png)
3. A questo punto, quando si assegna questo profilo personalizzato ai dispositivi del profilo di lavoro Android, le azioni di copia e incolla verranno bloccate tra app incluse in profili aziendali e personali.