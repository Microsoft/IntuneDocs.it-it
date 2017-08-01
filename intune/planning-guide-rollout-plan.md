---
title: Determinare i gruppi di destinazione e gli intervalli di tempo per l'implementazione
description: Questo articolo consente di decidere i gruppi di cui eseguire l'implementazione in Intune e gli intervalli di tempo per tali distribuzioni.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9dda530be47b5449a9c1ed610d8e409fd62148d7
ms.sourcegitcommit: ce363409d1206e4a3d669709863ccc9eb22b7d5f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2017
---
# <a name="develop-a-rollout-plan"></a>Elaborare un piano di implementazione

Il piano di implementazione identifica i gruppi dell'organizzazione di destinazione per l'implementazione di Intune, l'intervallo di tempo di implementazione per ciascun gruppo e gli approcci di registrazione da usare.

## <a name="targeted-groups-and-timeframes"></a>Gruppi di destinazione e intervalli di tempo

Innanzitutto, controllare i gruppi di destinazione per l'implementazione di Intune che sono stati identificati negli [scenari dei casi d'uso](planning-guide-scenarios.md).

In secondo luogo, determinare l'intervallo di tempo per ogni gruppo di destinazione. Questa attività in genere richiede una discussione all'interno del team di distribuzione di Intune e con i gruppi di destinazione, per determinare l'intervallo di tempo di implementazione più appropriato per ciascun gruppo. I punti da affrontare in una discussione di questo tipo includono:
* Disponibilità del gruppo al cambiamento
* Numero di utenti e dispositivi
* Tipi di piattaforme per i dispositivi
* Requisiti
* Posizione geografica
* Rischio aziendale

## <a name="rollout-phases"></a>Fasi di implementazione
Le organizzazioni generalmente scelgono di avviare l'implementazione di Intune con un progetto pilota, che coinvolge un piccolo gruppo di utenti del reparto IT. Il progetto pilota può essere ampliato per includere un set più ampio di utenti IT e può comprendere la partecipazione di altri gruppi dell'organizzazione.

### <a name="pilot"></a>Distribuzione pilota
La prima fase di implementazione deve coinvolgere utenti pilota. Gli utenti pilota devono essere consapevoli di essere i primi utenti di una nuova soluzione. Devono essere disposti a fornire feedback per migliorare la configurazione, la documentazione e le notifiche, nonché agevolare tutti gli altri utenti nelle fasi di implementazione successive. Questi utenti non devono essere dirigenti o persone importanti.

Il progetto pilota rappresenta una valida opportunità per testare le [problematiche](planning-guide-deployment-goals.md) e perfezionare i [requisiti](planning-guide-requirements.md) raccolti in precedenza.

Includere il piano di [comunicazione](planning-guide-communication-plan.md), il piano di [supporto](planning-guide-support-plan.md) e [i test e la convalida](planning-guide-test-validation.md), in modo da risolvere gli eventuali problemi mentre l'impatto per gli utenti è ancora ridotto.

### <a name="production-rollout"></a>Implementazione in produzione
Dopo il progetto pilota, si è pronti per avviare un'implementazione completa in produzione, per il resto dei gruppi dell'organizzazione. Alcuni esempi dei diversi gruppi e delle fasi di distribuzione sono:

-   **Reparti** <br/>A ogni reparto può essere associata una fase di implementazione. Si effettuerà l'implementazione per un intero reparto alla volta. In questo tipo di implementazione, gli utenti di ogni reparto tendono a usare i dispositivi mobili nello stesso modo e ad accedere alle stesse applicazioni. Per gli utenti sono solitamente previsti gli stessi tipi di criteri.

-   **Area geografica** <br/>Questo approccio prevede la distribuzione per tutti gli utenti in una specifica area geografica (un continente, un paese, una regione o un edificio della stessa società). Questo tipo di distribuzione graduale consente di concentrarsi sulla specifica posizione degli utenti. In questo modo, è possibile adottare un approccio basato su un [trattamento esclusivo](#user-assisted-enrollment), perché si riduce il numero di posizioni in cui eseguire la distribuzione di Intune contemporaneamente. Poiché è possibile che siano presenti diversi reparti o casi d'uso nella stessa posizione, può essere necessario distribuire diversi casi d'uso nello stesso momento.

-   **Piattaforma** <br/>Questo tipo di distribuzione consiste nella distribuzione di piattaforme simili nello stesso momento. Un esempio potrebbe essere: tutti i dispositivi iOS durante il primo mese, seguiti dai dispositivi Android e quindi dai dispositivi Windows. Questo tipo di distribuzione graduale consente di semplificare il supporto help desk, perché sarebbe sufficiente supportare un'unica piattaforma alla volta.

Di seguito è riportato un esempio di un piano di implementazione di Intune che include i gruppi di destinazione e le sequenze temporali:

| **Fase di implementazione** | **Luglio** | **Agosto** | **Settembre** | **Ottobre** |
|:---:|:---:|:---:|:---:|:---:|
| Progetto pilota limitato | IT (50 utenti) |  |  |  |                                                         
| Progetto pilota ampliato | IT (200 utenti), responsabili IT (10 utenti) |  |  |  |                                                         
| Fase 1 di implementazione in produzione |  | Vendite e marketing (2000 utenti) |  |  |
| Fase 2 di implementazione in produzione |  |  | Vendita al dettaglio (1000 utenti) |  |
| Fase 3 di implementazione in produzione |  |  |  | HR (50 utenti), finanza (40 utenti), dirigenti (30 utenti) |

È anche possibile [scaricare un modello della tabella precedente](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) per immettere le fasi di implementazione della propria organizzazione.
## <a name="match-rollout-groups-to-enrollment-approaches"></a>Associare i gruppi di distribuzione agli approcci di registrazione

Dopo avere determinato i gruppi di destinazione e gli intervalli di tempo per l'implementazione di Intune, il passaggio successivo consiste nello scegliere l'approccio alla registrazione di Intune più appropriato per ogni gruppo. È possibile usare diversi approcci di registrazione, tra cui:
* Registrazione self-service
* Registrazione assistita
* Evento IT

### <a name="user-self-service"></a>Registrazione self-service

In questo caso, l'utente è responsabile per la registrazione del proprio dispositivo, in genere seguendo le istruzioni di registrazione fornite dall'organizzazione IT. Questo approccio è quello usato più di frequente nelle organizzazioni ed è più scalabile rispetto alla registrazione assistita.

### <a name="user-assisted-enrollment"></a>Registrazione assistita

Questo approccio garantisce all'utente un trattamento esclusivo. Un membro del team IT assiste l'utente durante il processo di registrazione, di persona o tramite Skype. Questo approccio viene solitamente adottato per i dirigenti e altri gruppi che potrebbero richiedere particolare assistenza durante il processo di registrazione.

### <a name="it-tech-fair"></a>Evento IT

Un'altra opzione per la registrazione degli utenti in Intune è l'organizzazione di un evento IT. Nel corso dell'evento, il gruppo IT organizza uno stand per fornire assistenza per la registrazione di Intune, dove gli utenti possono ricevere informazioni sulla registrazione di Intune, porre domande e ottenere assistenza per il processo di registrazione. Questa opzione può essere utile sia per il gruppo IT che per gli utenti, soprattutto durante le fasi iniziali dell'implementazione di Intune.

Ecco un esempio aggiornato del piano di implementazione di Intune precedente che include gli approcci di registrazione:

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

## <a name="next-steps"></a>Passaggi successivi

Nella sezione successiva vengono fornite indicazioni su [come elaborare un piano di comunicazione per l'implementazione di Intune](planning-guide-communication-plan.md).
