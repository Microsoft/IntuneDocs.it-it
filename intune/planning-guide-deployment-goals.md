---
title: Determinare scopi, obiettivi e sfide per la distribuzione
description: Questo articolo consente di determinare gli scopi, gli obiettivi e le sfide per la distribuzione di un'implementazione di Microsoft Intune in configurazione solo cloud.
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fe680fcb617c29678f193aac2d74c12398a2a7f8
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="determine-deployment-goals-objectives-and-challenges"></a>Determinare scopi, obiettivi e sfide per la distribuzione

Per un piano di distribuzione efficace è innanzitutto necessario identificare gli scopi e gli obiettivi dell'organizzazione, insieme alle potenziali sfide da affrontare. Esaminiamo ognuna di queste aree più in dettaglio.

## <a name="deployment-goals"></a>Scopi della distribuzione

Gli scopi della distribuzione sono i traguardi a lungo termine che si intende raggiungere con l'implementazione di Intune nell'organizzazione. Di seguito sono riportati alcuni esempi di tali scopi, con la relativa descrizione e informazioni sul valore aziendale.

-   **Assicurare l'integrazione con Office 365 e supportare l'uso delle app di Office Mobile**

    -   **Descrizione:** fornire una stretta integrazione con Office 365 e l'uso delle app di Office Mobile con la protezione delle app.

    -   **Valore aziendale:** esperienza utente sicura e migliorata, consentendo agli utenti di usare le app che già conoscono.

-   **Abilitare l'accesso ai servizi aziendali interni nei dispositivi mobili**

    -   **Descrizione:** consentire ai dipendenti di essere produttivi ovunque si trovino e con qualsiasi dispositivo. Questo progetto deve puntare ad abilitare la produttività da dispositivi mobili e l'accesso ai dati aziendali in modo sicuro.

    -   **Valore aziendale:** consentire ai dipendenti di essere agili e di lavorare ovunque si trovino aumenta la competitività dell'azienda e fornisce un ambiente di lavoro più gratificante.

-   **Garantire la protezione dei dati nei dispositivi mobili**

    -   **Descrizione:** quando si archiviano dati in un dispositivo mobile, è essenziale proteggere le informazioni per evitare che vadano perse o che vengano condivise in modo intenzionale o accidentale.

    -   **Valore aziendale:** la protezione dei dati è fondamentale per garantire che l'organizzazione rimanga competitiva e che i clienti e i relativi dati vengano gestiti nel modo più appropriato.

-   **Ridurre i costi**

    -   **Descrizione:** quando possibile, il progetto mira a ridurre i costi di distribuzione e operativi.

    -    **Valore aziendale:** l'uso efficiente delle risorse consente all'azienda di investire in altre aree, competere in modo più efficace e offrire un servizio migliore ai clienti.

## <a name="deployment-objectives"></a>Obiettivi della distribuzione

Gli obiettivi della distribuzione sono le azioni che l'organizzazione può intraprendere per raggiungere gli scopi della distribuzione di Intune. Di seguito sono riportati alcuni esempi di obiettivi della distribuzione, con informazioni su come conseguire ciascun obiettivo.

-   **Ridurre il numero delle soluzioni di gestione dei dispositivi**

    -   **Implementazione:** eseguire il consolidamento su una singola soluzione di gestione dei dispositivi mobili, Microsoft Intune per la protezione dei dati aziendali di app e dispositivi.

-   **Fornire un accesso sicuro a Exchange e SharePoint Online**

    -   **Implementazione:** applicare l'accesso condizionale per Exchange e SharePoint Online.

-   **Impedire che i dati aziendali vengano archiviati o inoltrati a servizi non aziendali sui dispositivi mobili**

    -   **Implementazione:** applicare i criteri di protezione delle app di Intune per le app Microsoft Office e line-of-business.

-   **Fornire funzionalità per la cancellazione dei dati aziendali dal dispositivo**

    -   **Implementazione:** registrare i dispositivi in Intune. Questo offre la possibilità di eseguire una cancellazione remota dei dati e delle risorse aziendali, quando appropriato.

## <a name="deployment-challenges"></a>Sfide della distribuzione

Le sfide della distribuzione sono i problemi più importanti per un'organizzazione, che possono avere un impatto negativo sulla distribuzione. Può trattarsi di problemi che si sono verificati durante progetti precedenti e che si desidera evitare oppure di nuovi problemi correlati alla distribuzione corrente. Di seguito sono riportati alcuni esempi di sfide per la distribuzione di Intune, insieme alle potenziali strategie di riduzione del rischio.

-   La preparazione per il supporto e l'esperienza utente finale non sono incluse nell'ambito del progetto iniziale. Questo comporta un'adozione limitata da parte degli utenti finali e problemi per l'organizzazione di supporto.

    -   **Strategia di riduzione del rischio:** incorporare la formazione per il supporto. Convalidare l'esperienza dell'utente finale con metriche di successo nel piano di distribuzione.

-   La mancanza di metriche di successo e obiettivi chiaramente definiti comporta risultati indeterminati. Può inoltre portare l'organizzazione a intervenire in modo reattivo quando si verificano problemi.

    -   **Strategia di riduzione del rischio:** definire obiettivi e metriche di successo nelle fasi iniziali di definizione dell'ambito e usare questi dati per approfondire le altre fasi dell'implementazione. Assicurarsi che gli obiettivi siano specifici, misurabili, realizzabili, realistici e tempestivi. Pianificare la verifica degli obiettivi in ogni fase e garantire che il progetto di implementazione sia conforme.

-   Si trascura di creare, convalidare e condividere sistematicamente una proposta di valore ben definita adatta alle esigenze dell'organizzazione. Questo spesso comporta un'adozione limitata e una mancanza del ritorno sugli investimenti (ROI).

    -   **Strategia di riduzione del rischio:** prima di passare all'implementazione del progetto, assicurarsi di aver chiaramente definito gli scopi e gli obiettivi. Includere questi scopi e obiettivi in tutte le attività di formazione e sensibilizzazione per garantire agli utenti un'adeguata comprensione del motivo per cui l'organizzazione ha adottato Intune.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere identificato gli scopi, gli obiettivi e le potenziali sfide della distribuzione, possiamo passare alla sezione successiva: [Identificare gli scenari per i casi d'uso](planning-guide-scenarios.md).
