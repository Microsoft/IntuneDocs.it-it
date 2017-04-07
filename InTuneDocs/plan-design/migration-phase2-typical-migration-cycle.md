---
title: Come funziona un ciclo di migrazione a Intune tipico | Microsoft Docs
description: "Lo scopo di questo articolo è spiegare come funziona un ciclo di migrazione a Intune e sono disponibili esempi delle modalità di gestione dei cicli di migrazione per i clienti."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: aa8fb215772b6e8d3a913d929c030d68e363970b
ms.lasthandoff: 03/27/2017


---

# <a name="phase-2-typical-migration-cycle"></a>Fase 2: Ciclo di migrazione tipico

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Per le organizzazioni, è pratica comune iniziare la migrazione a Intune con una piccola distribuzione pilota che coinvolge un sottoinsieme di utenti del reparto IT. L'organizzazione potrebbe anche avere l'esigenza di discutere di fattori quali la predisposizione del gruppo al cambiamento, il numero di utenti, la complessità, i requisiti, la posizione e i rischi aziendali per valutare e decidere la tempistica per la migrazione.

Ecco un esempio della possibile pianificazione dei gruppi di destinazione:

  | **Gruppi di destinazione della migrazione** | **Periodo di tempo 1** | **Periodo di tempo 2** | **Periodo di tempo 3** | **Periodo di tempo 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| Progetto pilota limitato org IT (50 utenti) | Annunciare il piano | Istruzioni per la registrazione | Definire la scadenza | Applicare l'accesso condizionale |  |                                                        
| Progetto pilota esteso org IT (200 utenti) |  | Annunciare il piano | Istruzioni per la registrazione | Definire la scadenza | Applicare l'accesso condizionale | 
| Fase di migrazione 1 - Utenti esperti (2000) |  |  | Annunciare il piano | Istruzioni per la registrazione | Definire la scadenza | 
| Fase di migrazione 2 - Stati Uniti Orientali |  |  |  | Annunciare il piano | Istruzioni per la registrazione | 
| Tutte le aree |  |  |  |  | Annunciare il piano | 

## <a name="customer-migration-case-study"></a>Case study di migrazione di un cliente

### <a name="adatum-corporation"></a>Adatum Corporation

- Vedere [come Adatum Corporation ha gestito il processo di migrazione da un provider MDM di terze parti a Intune](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0).

## <a name="monitoring-migration"></a>Monitoraggio della migrazione

Microsoft Intune offre vari strumenti per il monitoraggio della migrazione:

1.  Visualizzazioni dei gruppi di utenti di Intune

2.  Report predefiniti e

3.  Avvisi nella console.

È necessario verificare il numero di utenti con dispositivi registrati dopo ogni fase in modo da potere:

-   Valutare l'efficacia del piano di comunicazione.

-   Stimare l'impatto dell'applicazione dell'accesso condizionale.

Informazioni su [come monitorare una migrazione a Intune](https://docs.microsoft.com/intune/deploy-use/understand-microsoft-intune-operations-by-using-reports).

## <a name="post-migration"></a>Post-migrazione

È necessario ritirare il precedente provider MDM e/o annullare la sottoscrizione al servizio dopo aver completato la migrazione a Intune. Sarà anche necessario rimuovere eventuali requisiti di infrastruttura non necessari seguendo le istruzioni del provider MDM.

