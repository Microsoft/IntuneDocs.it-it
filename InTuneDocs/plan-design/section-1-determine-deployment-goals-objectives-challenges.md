---
title: Determinare scopi, obiettivi e sfide per la distribuzione di Intune | Documentazione Microsoft
description: Questo articolo consente di determinare gli scopi, gli obiettivi e le sfide per la distribuzione di un&quot;implementazione di Microsoft Intune in configurazione solo cloud.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: 2e46c5612c120a24d3f8fe32decd3eb7a0d4e709


---

# <a name="determine-intune-deployment-goals-objectives-and-challenges"></a>Determinare scopi, obiettivi e sfide per la distribuzione di Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Per un piano di distribuzione efficace è innanzitutto necessario identificare gli scopi e gli obiettivi dell'organizzazione, insieme alle potenziali sfide da affrontare. Ogni organizzazione è diversa dalle altre, quindi avrà specifici scopi, obiettivi e sfide per la distribuzione con caratteristiche uniche. Esaminiamo ognuna di queste aree più in dettaglio.

## <a name="deployment-goals"></a>Scopi della distribuzione

Gli scopi della distribuzione sono i traguardi a lungo termine che si intende raggiungere con l'implementazione di Microsoft Intune in un'organizzazione. Di seguito sono riportati alcuni esempi di scopi per la distribuzione di Intune in un'organizzazione, con la relativa descrizione e informazioni sul valore aziendale.

-   **Assicurare l'integrazione con Office 365 e supportare l'uso delle app di Office Mobile**

    -   **Descrizione:** fornire una stretta integrazione con Office 365 e l'uso delle applicazioni di Office Mobile con la protezione dell'applicazione.

    -   **Valore aziendale:** esperienza utente sicura e migliorata, consentendo agli utenti di usare le app che già conoscono.

-   **Abilitare l'accesso ai servizi aziendali interni nei dispositivi mobili**

    -   **Descrizione:** consentire ai dipendenti di essere produttivi ovunque si trovino e con qualsiasi dispositivo è un aspetto di importanza strategica per l'organizzazione. Questo progetto deve puntare ad abilitare la produttività da dispositivi mobili e l'accesso ai dati aziendali in modo sicuro.

    -   **Valore aziendale:** consentire ai dipendenti di essere agili e di lavorare ovunque si trovino aumenta la competitività dell'azienda e fornisce un ambiente di lavoro più gratificante.

-   **Garantire la protezione dei dati nei dispositivi mobili**

    -   **Descrizione:** quando si archiviano dati in un dispositivo mobile, è essenziale proteggere le informazioni per evitare che vadano perse o che vengano condivise in modo intenzionale o accidentale.

    -   **Valore aziendale:** la protezione dei dati è fondamentale per garantire che l'organizzazione rimanga competitiva e che i clienti e i relativi dati vengano gestiti nel modo più appropriato.

-   **Ridurre i costi**

    -   **Descrizione:** quando possibile, il progetto mira a ridurre i costi di distribuzione e operativi.

    -    **Valore aziendale:** l'uso efficiente delle risorse consente all'azienda di investire in altre aree, competere in modo più efficace e offrire un servizio migliore ai clienti.

## <a name="deployment-objectives"></a>Obiettivi della distribuzione

Gli obiettivi della distribuzione sono le azioni che un'organizzazione può intraprendere per raggiungere gli scopi della distribuzione di Microsoft Intune. Di seguito sono riportati alcuni esempi di obiettivi della distribuzione di un'organizzazione, con informazioni su come conseguire ciascun obiettivo.

-   **Ridurre il numero delle soluzioni di gestione dei dispositivi**
<br>
    -   **Esecuzione:** eseguire il consolidamento su una singola soluzione di gestione dei dispositivi mobili, Microsoft Intune per la protezione dei dati aziendali di app e dispositivi.
<br></br>
-   **Fornire un accesso sicuro a Exchange e SharePoint Online**
<br>
    -   **Esecuzione:** implementare l'accesso condizionale di Microsoft Intune per Exchange e SharePoint Online.
<br></br>
-   **Impedire che i dati aziendali vengano archiviati o inoltrati a servizi non aziendali sui dispositivi mobili**
<br>
    -   **Esecuzione:** implementare i criteri di protezione delle app di Microsoft Intune per le app Microsoft Office e line-of-business.
<br></br>
-   **Fornire funzionalità per la cancellazione dei dati aziendali dal dispositivo**
<br>
    -   **Esecuzione:** registrare e gestire i dispositivi con Microsoft Intune, che offre la possibilità di eseguire una cancellazione remota dei dati e delle risorse aziendali, quando necessario.

## <a name="deployment-challenges"></a>Sfide della distribuzione

Le sfide della distribuzione sono i problemi più importanti per un'organizzazione, che possono avere un impatto negativo sulla distribuzione. Potrebbe trattarsi di problemi che si sono verificati durante progetti precedenti e che si desidera evitare oppure di nuovi problemi correlati alla distribuzione corrente. Di seguito sono riportati alcuni esempi di sfide per la distribuzione di Microsoft Intune in un'organizzazione, insieme alle potenziali strategie di riduzione del rischio.

-   La preparazione per il supporto e l'esperienza utente finale non sono incluse nell'ambito del progetto iniziale.  Questo ostacola l'adozione da parte degli utenti finali e rappresenta un problema per il supporto della soluzione.
<br>
    -   **Strategia di riduzione del rischio:** incorporare la formazione per il supporto e la convalida dell'utente esperienza finale con metriche di successo nel piano di distribuzione.
<br></br>
-   Mancanza di metriche di successo e obiettivi chiaramente definiti con conseguenti risultati negativi e capacità di reazione solo di fronte ai problemi.
<br>
    -   **Strategia di riduzione del rischio:** definire obiettivi e metriche di successo nelle fasi iniziali di definizione dell'ambito e usare questi dati per approfondire le altre fasi dell'implementazione. Assicurarsi che gli obiettivi siano specifici, misurabili, realizzabili, realistici e tempestivi, pianificare la verifica degli obiettivi in ogni fase e garantire che il progetto di implementazione sia conforme.
<br></br>
-   Trascurare di creare, convalidare e condividere sistematicamente una proposta di valore ben definita adatta alle esigenze dell'organizzazione causa spesso un'adozione limitata e mancanza del ritorno sugli investimenti (ROI).
<br>
    -   **Strategia di riduzione del rischio:** prima di passare all'implementazione del progetto, assicurarsi di aver chiaramente definito gli scopi e gli obiettivi. Includere questi scopi e obiettivi in tutte le attività di formazione e sensibilizzazione per garantire agli utenti un'adeguata comprensione del motivo per cui l'organizzazione ha adottato Intune.

## <a name="next-section"></a>Sezione successiva

Dopo avere identificato gli scopi, gli obiettivi e le potenziali sfide della distribuzione, possiamo passare alla sezione successiva: [Identificare gli scenari per i casi d'uso](section-2-identify-use-case-scenarios.md).



<!--HONumber=Dec16_HO5-->


