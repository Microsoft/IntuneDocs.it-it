---
title: Abilitare il connettore Mobile Threat Defense in Microsoft Intune
titleSuffix: ''
description: Abilitare il connettore tra il partner Mobile Threat Defense (MTD) e Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2937814ae5ceb6c7d8b3def4e954c8eec9337126
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180477"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Abilitare il connettore Mobile Threat Defense in Intune

> [!NOTE] 
> Questo argomento si applica a tutti i partner Mobile Threat Defense.

Durante l'installazione di Mobile Threat Defense (MTD), sono stati configurati criteri di classificazione delle minacce nella console del partner MTD e sono stati creati criteri di conformità del dispositivo in Intune. Se il connettore Intune nella console del partner MTD è già stato configurato, è possibile abilitare la connessione MTD in Intune.

## <a name="to-enable-the-mtd-connector"></a>Per abilitare il connettore MTD

1. Andare nel [portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune. Dopo aver completato l'accesso, viene visualizzato il **dashboard di Azure**.

2. Nel **dashboard di Azure** scegliere **Tutti i servizi** dal menu di sinistra e digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune**. Viene aperto il **dashboard di Intune**.

4. Nel **dashboard di Intune** scegliere **Conformità del dispositivo** e quindi **Mobile Threat Defense** nella sezione **Installazione**.

5. Nel riquadro **Mobile Threat Defense** scegliere **Aggiungi**.

6. Scegliere la soluzione MTD nell'elenco a discesa **Selezionare il connettore Mobile Threat Defense da configurare**.

    ![Configurazione di MTD nel portale di Intune di Azure](./media/enable-mtd-connector-1.png)

7. Abilitare le opzioni con interruttore di attivazione/disattivazione in base ai requisiti dell'organizzazione. Le opzioni di attivazione/disattivazione visibili variano a seconda del partner MTD.

## <a name="mtd-toggle-options"></a>Opzioni di attivazione/disattivazione di MTD

È possibile scegliere le opzioni di attivazione/disattivazione MTD da abilitare in base ai requisiti dell'organizzazione. Ecco ulteriori dettagli:

- **Connetti dispositivi Android 4.1+ a [nome partner MTD] for Work MTD**: quando si abilita questa opzione è possibile fare in modo che i dispositivi Android 4.1+ segnalino i rischi di sicurezza in Intune.
    - **Contrassegna come non conforme se non vengono ricevuti dati**: se Intune non riceve dati su un dispositivo in questa piattaforma da un partner MTD, il dispositivo viene considerato non conforme.
<br></br>
- **Connetti dispositivi iOS 8.0+ a [nome partner MTD] for Work MTD**: quando si abilita questa opzione è possibile fare in modo che i dispositivi iOS 8.0+ segnalino i rischi di sicurezza in Intune.
    - **Contrassegna come non conforme se non vengono ricevuti dati**: se Intune non riceve dati su un dispositivo in questa piattaforma da un partner MTD, il dispositivo viene considerato non conforme.
<br></br>
- **Abilita la sincronizzazione delle app per dispositivi iOS**: consente a questo partner di Mobile Threat Defense di richiedere metadati delle applicazioni iOS da Intune per l'uso per finalità di analisi delle minacce.

- **Blocca le versioni del sistema operativo non supportate**: bloccare un dispositivo che esegue un sistema operativo con un versione precedente a quella minima supportata.

- **Numero di giorni dopo i quali il partner risulta non reattivo**: numero di giorni di inattività prima che Intune consideri il partner non reattivo a causa della perdita della connessione. Intune ignora lo stato di conformità per i partner MTD non reattivi.

> [!IMPORTANT] 
> È necessario aggiungere e assegnare le app MTD prima di creare le regole di conformità del dispositivo e dei criteri di accesso condizionale. Ciò garantisce che l'app MTD sia pronta e disponibile in modo che gli utenti finali possano installarla prima di ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.

> [!TIP]
> Nel riquadro Mobile Threat Defence sono visualizzati lo **Stato connessione** e l'ora dell'**Ultima sincronizzazione** tra Intune e il partner MTD.
