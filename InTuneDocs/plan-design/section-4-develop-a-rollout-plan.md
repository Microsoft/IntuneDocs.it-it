---
title: Determinare i gruppi di destinazione e gli intervalli di tempo per l&quot;implementazione di Intune | Documentazione Microsoft
description: Questo articolo aiuta a determinare i gruppi di destinazione e gli intervalli di tempo per un&quot;implementazione di Microsoft Intune in configurazione solo cloud.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: 36530602813467c184b4f262719a56cedbaa2ba9


---

# <a name="develop-an-intune-rollout-plan"></a>Elaborare un piano di implementazione di Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Questa sezione consente di determinare i gruppi di destinazione dell'organizzazione per l'implementazione di Intune, nonché l'intervallo di tempo di implementazione per ogni gruppo e gli approcci alla registrazione che verranno usati.

## <a name="determine-intune-rollout-targeted-groups-and-timeframes"></a>Determinare i gruppi di destinazione e gli intervalli di tempo per l'implementazione di Intune

È importante identificare innanzitutto i gruppi di destinazione per l'implementazione di Intune. I gruppi di destinazione sono stati illustrati in precedenza nella sezione Identificare gli scenari dei casi d'uso per Intune di questa guida.

In secondo luogo, è necessario determinare l'intervallo di tempo per cui ogni gruppo sarà interessato dall'implementazione di Intune. Questo in genere richiede una discussione all'interno del team di distribuzione di Intune e con i gruppi di destinazione, per determinare l'intervallo di tempo di implementazione più appropriato per ciascun gruppo.

Per determinare l'intervallo di tempo di implementazione, il team di distribuzione di Intune potrebbe ad esempio discutere di fattori quali l'interesse del gruppo per il cambiamento, il numero di utenti e dispositivi, i tipi di piattaforme per i dispositivi, i requisiti, la posizione geografica e i rischi aziendali.

Le organizzazioni generalmente scelgono di avviare l'implementazione di Intune con un progetto pilota, che coinvolge un piccolo gruppo di utenti del reparto IT. Il progetto pilota può quindi essere ampliato per includere un set più ampio di utenti IT e la partecipazione di altri gruppi dell'organizzazione. Dopo il successo del progetto pilota, le organizzazioni sono pronte per avviare una distribuzione completa in produzione, per il resto dei gruppi dell'organizzazione. Di seguito sono riportati alcuni esempi dei vari gruppi e delle fasi di implementazione:

-   **Progetto pilota:** la prima fase di implementazione deve coinvolgere utenti pilota. Gli utenti pilota devono comprendere di essere i primi utenti di una nuova soluzione ed essere disposti a fornire feedback per migliorare la configurazione, la documentazione e le notifiche, nonché agevolare tutti gli altri utenti nelle fasi di implementazione successive. Questi utenti non devono essere dirigenti o persone importanti.

-   **Reparti:** a ogni reparto può essere associata una fase di implementazione. In questo scenario, si effettuerà l'implementazione per un intero reparto alla volta. In questo tipo di implementazione, gli utenti di ogni fase in genere useranno i dispositivi mobili nello stesso modo e accederanno alle stesse applicazioni. Per gli utenti sono inoltre solitamente previsti gli stessi tipi di criteri.

-   **Area geografica:** questo tipo di distribuzione consiste nella distribuzione per tutti gli utenti in una specifica area geografica (un continente, un paese, una regione o un edificio della stessa società). Questo tipo di distribuzione graduale consente di concentrarsi sulla specifica posizione degli utenti. In questo modo, è possibile adottare un approccio basato su un [trattamento esclusivo](#user-assisted-enrollment), perché si riduce il numero di posizioni in cui eseguire la distribuzione di Intune contemporaneamente. Poiché è possibile che siano presenti diversi reparti o casi d'uso nella stessa posizione, può essere necessario distribuire diversi casi d'uso nello stesso momento.

-   **Piattaforma:** questo tipo di distribuzione consiste nella distribuzione di piattaforme simili nello stesso momento. Un esempio potrebbe essere: tutti i dispositivi iOS durante il primo mese, seguiti dai dispositivi Android e quindi dai dispositivi Windows. Questo tipo di distribuzione graduale consente di semplificare il supporto help desk, perché sarebbe sufficiente supportare un'unica piattaforma alla volta.

Di seguito è riportato un esempio di un piano di implementazione di Intune che include i gruppi di destinazione e le sequenze temporali:

| **Fase di implementazione** | **Luglio** | **Agosto** | **Settembre** | **Ottobre** |
|:---:|:---:|:---:|:---:|:---:|
| Progetto pilota limitato | IT (50 utenti) |  |  |  |                                                         
| Progetto pilota ampliato | IT (200 utenti), responsabili IT (10 utenti) |  |  |  |                                                         
| Fase 1 di implementazione in produzione |  | Vendite e marketing (2000 utenti) |  |  |
| Fase 2 di implementazione in produzione |  |  | Vendita al dettaglio (1000 utenti) |  |
| Fase 3 di implementazione in produzione |  |  |  | HR (50 utenti), finanza (40 utenti), dirigenti (30 utenti) |

## <a name="determine-the-intune-enrollment-approach"></a>Determinare l'approccio alla registrazione di Intune

Dopo avere determinato i gruppi di destinazione e gli intervalli di tempo per l'implementazione di Intune, il passaggio successivo consiste nello scegliere l'approccio alla registrazione di Intune più appropriato per ogni gruppo. Esistono diversi approcci alla registrazione che le organizzazioni possono adottare per l'implementazione di Intune. Alcuni approcci comuni alla registrazione includono la registrazione self-service, la registrazione assistita e gli eventi IT.

### <a name="user-self-service"></a>Registrazione self-service

Con questo approccio, l'utente è responsabile per la registrazione del proprio dispositivo, in genere seguendo le istruzioni di registrazione fornite dall'organizzazione IT. Questo approccio è quello usato più di frequente nelle organizzazioni ed è più scalabile rispetto alla registrazione assistita.

### <a name="user-assisted-enrollment"></a>Registrazione assistita

Questo approccio, che garantisce all'utente un trattamento esclusivo, prevede che un membro del team IT assista l'utente nel corso del processo di registrazione, di persona o tramite Skype. Questo approccio viene solitamente adottato per i dirigenti e altri gruppi che potrebbero richiedere particolare assistenza durante il processo di registrazione.

### <a name="it-tech-fair"></a>Evento IT

Un'altra opzione per la registrazione degli utenti in Intune l'organizzazione di un evento IT. Nel corso dell'evento, il gruppo IT può organizzare uno stand per fornire assistenza per la registrazione di Intune, dove gli utenti possono ricevere informazioni sulla registrazione di Intune, porre domande e ottenere assistenza per il processo di registrazione. Questa opzione può essere utile sia per il gruppo IT che per gli utenti, soprattutto durante le fasi iniziali dell'implementazione di Intune.

Di seguito è riportato un esempio di un piano di implementazione di Intune con i gruppi di destinazione, le sequenze temporali e gli approcci alla registrazione:

| **Fase di implementazione** | **Luglio** | **Agosto** | **Settembre** | **Ottobre** |
|:---:|:---:|:---:|:---:|:---:|
| Progetto pilota limitato |  |  |  |  |                                                         
| Self-service | IT |  |  |  |
| Progetto pilota ampliato |  |  |  |  |                                                         
| Self-service | IT |  |  |  |
| Trattamento esclusivo | Responsabili IT |  |  |  |
| Fase 1 di implementazione in produzione |  | Vendite, marketing |  |  |
| Self-service |  | Vendite e marketing |  |  |
| Fase 2 di implementazione in produzione |  |  | Vendita al dettaglio |  |
| Self-service |  |  |  |  |
| Fase 3 di implementazione in produzione |  |  | Vendita al dettaglio |  |
| Self-service |  |  |  | HR, finanza |
| Trattamento esclusivo |  |  |  | Dirigenti |

## <a name="next-section"></a>Sezione successiva

Nella sezione successiva vengono fornite indicazioni su [come elaborare un piano di comunicazione per l'implementazione di Intune](section-5-develop-a-rollout-communication-plan.md).



<!--HONumber=Dec16_HO5-->


