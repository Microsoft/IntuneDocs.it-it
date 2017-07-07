---
title: Come funziona un ciclo di migrazione a Intune tipico
description: "Lo scopo di questo articolo è spiegare come funziona un ciclo di migrazione a Intune e sono disponibili esempi delle modalità di gestione dei cicli di migrazione per i clienti."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 70aa7155e050450a2d786a1f16e42ce2a3c77f9e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="typical-migration-cycle"></a>Ciclo di migrazione tipico

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

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


## <a name="post-migration"></a>Post-migrazione

È necessario ritirare il precedente provider MDM e annullare la sottoscrizione al servizio dopo aver completato la migrazione a Intune. Sarà anche necessario rimuovere eventuali requisiti di infrastruttura non necessari seguendo le istruzioni del provider MDM.
