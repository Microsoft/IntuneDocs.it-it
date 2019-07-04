---
title: Determinare scopi, obiettivi e sfide per la distribuzione
titleSuffix: Microsoft Intune
description: Questo articolo consente di determinare gli scopi, gli obiettivi e le sfide per la distribuzione di un'implementazione di Microsoft Intune in configurazione solo cloud.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b29e59924ec4bf08336cbd1ea9aa588fd8612233
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044426"
---
# <a name="determine-deployment-goals-objectives-and-challenges"></a>Determinare scopi, obiettivi e sfide per la distribuzione

Per un piano di distribuzione efficace è innanzitutto necessario identificare gli scopi e gli obiettivi dell'organizzazione, insieme alle potenziali sfide da affrontare. Esaminiamo ognuna di queste aree più in dettaglio.

## <a name="deployment-goals"></a>Scopi della distribuzione

Gli scopi della distribuzione sono i traguardi a lungo termine che si intende raggiungere con l'implementazione di Intune nell'organizzazione. Di seguito sono riportati alcuni esempi di tali scopi, con la relativa descrizione e informazioni sul valore aziendale.

-   **Assicurare l'integrazione con Office 365 e supportare l'uso delle app di Office Mobile**

    -   **Descrizione:** fornire una stretta integrazione con Office 365 e l'uso di app di Office per dispositivi mobili con protezione delle app.

    -   **Valore per l'azienda:** esperienza utente sicura e migliorata che permette agli utenti di usare app con cui hanno già familiarità e che preferiscono.

-   **Abilitare l'accesso ai servizi aziendali interni nei dispositivi mobili**

    -   **Descrizione:** permettere ai dipendenti di essere produttivi ovunque si trovino e con il dispositivo più appropriato per ognuno. Questo progetto deve puntare ad abilitare la produttività da dispositivi mobili e l'accesso ai dati aziendali in modo sicuro.

    -   **Valore per l'azienda:** la capacità di permettere ai dipendenti di essere agili e di lavorare ovunque si trovino aumenta la competitività dell'azienda e offre un ambiente di lavoro più gratificante.

-   **Garantire la protezione dei dati nei dispositivi mobili**

    -   **Descrizione:** quando si archiviano dati in un dispositivo mobile, è essenziale proteggerli per evitare che vadano persi o vengano condivisi in modo intenzionale o accidentale.

    -   **Valore per l'azienda:** la protezione dei dati è fondamentale per garantire che l'organizzazione resti competitiva e che i clienti e i rispettivi dati vengano gestiti nel modo più appropriato.

-   **Ridurre i costi**

    -   **Descrizione:** quando possibile, il progetto riduce i costi operativi e di distribuzione.

    -    **Valore per l'azienda:** l'uso efficiente delle risorse permette all'azienda di investire in altre aree, essere più competitiva e offrire un servizio migliore ai clienti.

## <a name="deployment-objectives"></a>Obiettivi della distribuzione

Gli obiettivi della distribuzione sono le azioni che l'organizzazione può intraprendere per raggiungere gli scopi della distribuzione di Intune. Di seguito sono riportati alcuni esempi di obiettivi della distribuzione, con informazioni su come conseguire ciascun obiettivo.

-   **Ridurre il numero delle soluzioni di gestione dei dispositivi**

    -   **Implementazione:** consolidamento in un'unica soluzione di gestione di dispositivi mobili: Microsoft Intune per la protezione dei dati aziendali di app e dispositivi.

-   **Fornire un accesso sicuro a Exchange e SharePoint Online**

    -   **Implementazione:** applicare l'accesso condizionale per Exchange e SharePoint Online.

-   **Impedire che i dati aziendali vengano archiviati o inoltrati a servizi non aziendali sui dispositivi mobili**

    -   **Implementazione:** applicare criteri di protezione delle app di Intune per le app di Microsoft Office e line-of-business.

-   **Fornire funzionalità per la cancellazione dei dati aziendali dal dispositivo**

    -   **Implementazione:** registrare dispositivi in Intune. Questo offre la possibilità di eseguire una cancellazione remota dei dati e delle risorse aziendali, quando appropriato.

## <a name="deployment-challenges"></a>Sfide della distribuzione

Le sfide della distribuzione sono i problemi più importanti per un'organizzazione, che possono avere un impatto negativo sulla distribuzione. Può trattarsi di problemi che si sono verificati durante progetti precedenti e che si desidera evitare oppure di nuovi problemi correlati alla distribuzione corrente. Di seguito sono riportati alcuni esempi di sfide per la distribuzione di Intune, insieme alle potenziali strategie di riduzione del rischio.

-   La preparazione per il supporto e l'esperienza utente finale non sono incluse nell'ambito del progetto iniziale. Questo comporta un'adozione limitata da parte degli utenti finali e problemi per l'organizzazione di supporto.

    -   **Prevenzione:** integrare la formazione per il supporto. Convalidare l'esperienza dell'utente finale con metriche di successo nel piano di distribuzione.

-   La mancanza di metriche di successo e obiettivi chiaramente definiti comporta risultati indeterminati. Può inoltre portare l'organizzazione a intervenire in modo reattivo quando si verificano problemi.

    -   **Prevenzione:** definire obiettivi e metriche di successo nelle fasi iniziali della definizione dell'ambito del progetto e usare questi punti dati per approfondire le altre fasi dell'implementazione. Assicurarsi che gli obiettivi siano specifici, misurabili, realizzabili, realistici e tempestivi. Pianificare la verifica degli obiettivi in ogni fase e garantire che il progetto di implementazione sia conforme.

-   Si trascura di creare, convalidare e condividere sistematicamente una proposta di valore ben definita adatta alle esigenze dell'organizzazione. Questo spesso comporta un'adozione limitata e una mancanza del ritorno sugli investimenti (ROI).

    -   **Prevenzione:** prima di passare all'implementazione del progetto, assicurarsi di aver chiaramente definito gli scopi e gli obiettivi. Includere questi scopi e obiettivi in tutte le attività di formazione e sensibilizzazione per garantire agli utenti un'adeguata comprensione del motivo per cui l'organizzazione ha adottato Intune.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere identificato gli scopi, gli obiettivi e le potenziali sfide della distribuzione, è possibile passare alla sezione successiva: [Identificare gli scenari per i casi d'uso](planning-guide-scenarios.md).
