---
title: Modello di verifica | Microsoft Intune
description: Suggerimenti per la fase del modello di verifica di una distribuzione di Intune.
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f3c97380-23ca-40da-acbc-78108507cad7
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c1e215320168c659d5f838355f6350111d6979b0
ms.openlocfilehash: 57f6d51a3f1e05a7edd260b0923d099510114a9f


---

# Modello di verifica (PoC)
Nella fase del modello di verifica è necessario definire se la distribuzione è in grado di soddisfare i requisiti aziendali. Questa fase prevede una topologia semplice progettata per convalidare specifici scenari tecnici.  La distribuzione deve essere eseguita in un ambiente di test e non deve coinvolgere gli utenti dell'ambiente di produzione.

## Perché questa fase è importante?
Un modello di verifica è importante per comprendere la fattibilità della distribuzione prima del passaggio agli utenti della fase pilota. Deve essere considerata un esperimento su scala ridotta da cui si apprenderà il funzionamento di Microsoft Intune nell'ambiente in uso. Deve inoltre consentire di convalidare scenari specifici prima di investire nelle risorse necessarie per una fase pilota. Gli aspetti appresi nel modello di verifica devono influenzare la progettazione della fase pilota e di produzione.
Per individuare l'ambito e definire la fase del modello di verifica, è consigliabile consultare le domande preliminari.

## Domande preliminari
Discutere queste domande con il team di progetto per individuare i dettagli del progetto, scoprire i potenziali rischi e definire le attività da eseguire.

-   Quali sono gli scenari principali che Intune deve affrontare per soddisfare le esigenze di gestione dei dispositivi dell'organizzazione?

-   Quali sono le funzionalità da analizzare e convalidare?

-   Quali risorse sono necessarie nell'ambiente di test per completare la convalida di questi scenari?

## Obiettivi specifici
Questa sezione offre indicazioni sulle attività specifiche da eseguire in questa fase dell'implementazione.

### Pianificazione
È necessario conoscere gli scenari da convalidare e le operazioni fondamentali da eseguire per il completamento della convalida, prima di distribuire l'infrastruttura del modello di verifica.

### Supporto tecnico
Il personale del supporto tecnico non necessita di preparazione per questa fase del progetto in quanto non saranno coinvolti utenti o dispositivi di produzione. Tuttavia, questa fase rappresenta un'opportunità per il supporto tecnico per ottenere informazioni sulla distribuzione e sul funzionamento di Intune.

### Sensibilizzazione
Il team tecnico e i responsabili della sponsorizzazione devono avere visibilità dello stato di avanzamento dello scenario di test. Il team di progettazione deve essere a conoscenza degli aspetti da integrare nella progettazione.

### Formazione
Gli amministratori che gestiranno utenti, dispositivi, criteri e applicazioni devono usare il modello di verifica come un'opportunità per ottenere informazioni sulle funzionalità e sulla console di Intune.

### Operazioni
Durante il modello di verifica non è necessario svolgere particolari operazioni. Possono, tuttavia, presentarsi scenari specifici da comprendere o convalidare nel modello di verifica.

## Elenco di controllo delle attività iniziali
Ecco un elenco dei passaggi per iniziare a realizzare la fase del **modello di verifica**.

-   Definire i criteri di successo del modello di verifica. Questi devono basarsi sulla convalida dei requisiti aziendali e tecnici.

-   Identificare le risorse necessarie per la convalida degli scenari di test.

-   Identificare gli ambienti di test appropriati che imitino l'ambiente di produzione, ad esempio, il numero necessario di dispositivi con i diversi sistemi operativi.

## Problemi comuni
Ecco alcuni problemi che si possono verificare durante la fase del **modello di verifica**.

-   **Problema:** ottenere le risorse tecniche e umane per convalidare scenari simili a quello di produzione.

    **Soluzione:** definire chiaramente che gli aspetti appresi nell'ambiente del modello di verifica saranno utili nella progettazione tecnica e miglioreranno la qualità delle fasi successive. La mancanza di risorse per il modello di verifica richiederà che questi aspetti vengano appresi dopo il completamento della progettazione tecnica, con conseguente necessità di riprogettare alcuni elementi.

-   **Problema:** definire gli scenari di test necessari nell'ambiente di produzione.

    **Soluzione:** collaborare con i team responsabili della sponsorizzazione, della rete e degli utenti per comprendere i requisiti di una soluzione di gestione client.

### Passaggi successivi
[Fase pilota](pilot.md)



<!--HONumber=Jul16_HO3-->


