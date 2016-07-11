---
title: Implementazione dei criteri | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 390d5adf-86d2-4e23-ba93-1e61e6b1028b
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d82d0ae4820d2e2141848235b8741abccaec3bc6
ms.openlocfilehash: 8935fbc42d7b406a5bcdbfc4353209b4447ae413


---

# Implementazione dei criteri
Questo argomento fornisce consigli specifici per un'implementazione graduale dei criteri in Microsoft Intune. Questo approccio si applica ai primi criteri applicati in una nuova distribuzione di Intune o ai criteri aggiunti a una distribuzione esistente.

Per informazioni generali sulle fasi di implementazione, vedere [Fasi dell'implementazione di Microsoft Intune](rollout-phases-for-microsoft-intune-deployment.md).

### Fasi dell'implementazione dei criteri
Le fasi dell'implementazione dei criteri sono:

-   Definizione dell'ambito

-   Modello di verifica

-   Distribuzione pilota

-   Implementazione nell'organizzazione

-   Operazioni e manutenzione

## Definizione dell'ambito
Definire l'ambito della distribuzione di criteri di Intune:

-   Per una nuova implementazione, è necessario definire tutti i comportamenti desiderati del dispositivo e i requisiti di sicurezza da creare con il set di criteri.

-   Decidere su quali utenti e dispositivi influiranno i criteri.

-   Progettare gruppi di utenti e dispositivi per consentire di applicare i nuovi criteri in modo appropriato.

-   Determinare se sono presenti limitazioni o requisiti associati a ogni sistema operativo che influiranno sulle intenzioni dei criteri.

-   Prendere in considerazione le specifiche di progettazione dei criteri, ad esempio il tipo e il modello di criteri da usare.

-   Indipendentemente dal fatto che si stia definendo il primo set di criteri o si stiano aggiungendo nuovi criteri a un set esistente, tenere in considerazione le modalità di interazione dei vari criteri e l'eventuale comportamento del dispositivo. È possibile rilevare eventuali problemi di interazioni e conflitti tra i criteri durante la fase pilota, tuttavia il rilevamento dei conflitti tra criteri nella fase iniziale della pianificazione semplificherà l'esecuzione della fase pilota.

## Modello di verifica
Nella fase del modello di verifica è possibile testare la distribuzione dei criteri in un ambiente di laboratorio su dispositivi e utenti configurati esclusivamente a scopo di test.

-   È importante che il personale del supporto tecnico partecipi a questa fase per individuare eventuali problemi che possono verificarsi durante la distribuzione pilota e di produzione. Per informazioni relative alla risoluzione dei problemi, vedere [Risolvere i problemi relativi ai criteri in Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune).

-   A questo punto del processo è necessario sviluppare piani di comunicazione per gli utenti pilota e di produzione. Il piano deve includere almeno i comportamenti del dispositivo che verranno modificati e il momento in cui avverrà la modifica, lo scopo aziendale della modifica e che cosa fare se il personale IT o gli utenti incontrano problemi, fornendo sia informazioni di supporto autonomo sia indicazioni per contattare il supporto tecnico.

## Fase pilota
Durante la fase pilota i criteri verranno distribuiti a un piccolo gruppo di utenti e dispositivi di test. È necessario prendere in considerazione alcuni aspetti specifici per eseguire la fase pilota dei criteri in Intune:

-   Il gruppo di test deve essere rappresentativo del gruppo a cui i criteri verranno applicati per l'implementazione di produzione.

-   Informare il personale del supporto tecnico in merito alle modifiche apportate ai criteri e verificare che sia in grado di fornire assistenza agli utenti nel gruppo di test.

-   Attivare il piano di comunicazione pilota con gli utenti.

-   La fase pilota può essere eseguita inizialmente in modalità isolata, in cui il dispositivo non è soggetto ad altri criteri che possono causare un comportamento imprevisto e con conflitti.

-   Il test finale deve considerare i nuovi criteri e tutti i criteri esistenti che verranno applicati allo stesso dispositivo.

## Implementazione nell'organizzazione

-   In base ai risultati della fase pilota, regolare i criteri pianificati per risolvere i conflitti tra criteri e casi di comportamento inaspettato.

-   Notificare il personale del supporto tecnico della pianificazione dell'implementazione nell'organizzazione. Realizzare le misure necessarie per rispondere alle richieste di assistenza e regolare l'implementazione in base alle esigenze.

-   Prepararsi a risolvere eventuali problemi correlati ai criteri.

-   Attivare il piano di comunicazione con gli utenti in fase di produzione.

-   Applicare i criteri in modo incrementale ad altri gruppi, monitorando lo stato dei criteri per i dispositivi interessati e rilevando le richieste di assistenza che possono essere correlate ai nuovi criteri.

## Operazioni e manutenzione
**Operazioni:** monitorare la console di Intune per eventuali avvisi e problemi correlati a utenti o dispositivi e verificare che i criteri siano conformi alla progettazione.

**Supporto tecnico:** assicurarsi che il supporto tecnico sia a conoscenza di eventuali modifiche ai criteri che influiranno sull'esperienza utente, in quanto potrebbero generare richieste di supporto.


### Vedere anche
[Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili con Microsoft Intune](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Risolvere i problemi relativi ai criteri in Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)



<!--HONumber=Jun16_HO4-->


