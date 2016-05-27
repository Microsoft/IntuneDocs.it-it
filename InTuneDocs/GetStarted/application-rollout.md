---
# required metadata

title: Implementazione di applicazioni | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0fc32ed3-bcf4-472a-80e7-eb20986f78fa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Implementazione di applicazioni
Questo argomento contiene consigli specifici per un'implementazione graduale delle app in Microsoft Intune. Per informazioni generali sulle fasi di implementazione, vedere [Rollout phases for Microsoft Intune deployment](rollout-phases-for-microsoft-intune-deployment.md) (Fasi di implementazione per la distribuzione di Microsoft Intune)..

### Fasi dell'implementazione di app
Le fasi dell'implementazione di app sono le seguenti:

-   Ambito del progetto

-   Modello di verifica

-   Distribuzione pilota

-   Implementazione nell'organizzazione

-   Operazioni e manutenzione

## Ambito del progetto
Considerare quanto segue:

-   L'attività utente che deve essere abilitata dall'app.

-   L'idoneità dell'app per gli utenti e i dispositivi (tutti i sistemi operativi che verranno probabilmente usati).

-   Verificare che il programma di installazione scelto per l'app sia supportato dalla distribuzione di app di Intune, come descritto in  [Aggiungere app con Microsoft Intune](/intune/deploy-use/add-apps).

-   Assicurarsi che siano installati i prerequisiti di distribuzione dell'applicazione. <!---, as described in [Plan for app deployment in Microsoft Intune](plan-for-app-deployment-in-microsoft-intune.md--->).

-   Controllare che il tipo di app sia supportato da Intune.

-   Verificare che vi sia sufficiente spazio di archiviazione nel cloud per il caricamento dell'applicazione. L'articolo [Aggiungere app con Microsoft Intune](/intune/deploy-use/add-apps) riporta le istruzioni per l'acquisto di spazio di archiviazione aggiuntivo..

## Modello di verifica
Nella fase del modello di verifica è possibile testare la distribuzione dell'app in un ambiente di laboratorio su dispositivi e utenti configurati esclusivamente a scopo di test.

-   È importante che il personale del supporto tecnico partecipi a questa fase per individuare eventuali problemi che possono verificarsi durante la distribuzione pilota e di produzione. Per informazioni relative alla risoluzione dei problemi, vedere l'articolo [Troubleshoot app deployment problems in Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune) (Risoluzione dei problemi di distribuzione delle app in Microsoft Intune)..

-   A questo punto del processo è necessario sviluppare piani di comunicazione per gli utenti pilota e di produzione. Il piano deve includere almeno quale app verrà distribuita, come e quando gli utenti la riceveranno, lo scopo aziendale della distribuzione e che cosa in caso di problemi, fornendo sia informazioni di supporto autonomo sia indicazioni per contattare il supporto tecnico.

## Distribuzione pilota
Durante la fase pilota l'app verrà distribuita a un piccolo gruppo di utenti e dispositivi di test. Considerare quanto segue:

-   Assicurarsi che il gruppo di test sia rappresentativo degli utenti e dei dispositivi che useranno l'applicazione dopo l'implementazione della produzione.

-   Informare il personale del supporto tecnico in merito alla distribuzione dell'app e verificare che sia in grado di fornire assistenza agli utenti nel gruppo di test.

-   Scegliere utenti di prova che usino l'app nel modo tipico e che riferiscano in modo affidabile i problemi agli amministratori del progetto pilota.

-   Attivare il piano di comunicazione pilota con gli utenti.

## Implementazione nell'organizzazione

-   Usare i risultati del progetto pilota per mettere a punto l'implementazione nell'organizzazione.

-   Avvisare il personale del supporto tecnico della pianificazione dell'implementazione dell'app. Realizzare le misure necessarie per rispondere alle richieste di assistenza e regolare l'implementazione in base alle esigenze.

-   Prepararsi a risolvere eventuali problemi correlati alla distribuzione.

-   Attivare il piano di comunicazione con gli utenti in fase di produzione.

-   Adottare un approccio graduale per la distribuzione dell'app, aggiungendo gruppi poco alla volta per assicurarsi che la distribuzione avvenga senza problemi.

## Operazioni e manutenzione
**Operazioni:** monitorare la console di Intune per eventuali avvisi e problemi correlati a utenti o dispositivi e per verificare che la distribuzione delle applicazioni sia conforme al progetto.

**Help desk:** assicurarsi che l'help desk sia a conoscenza di eventuali variazioni della disponibilità dell'app che possono generare richieste di assistenza.

### Vedere anche
[Distribuire le app](/intune/deploy-use/deploy-apps)

[Risorse che consentono di risolvere i problemi di distribuzione dell'app in Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)


<!--HONumber=May16_HO1-->


