---
title: Come funziona un ciclo di migrazione a Intune tipico
titleSuffix: Microsoft Intune
description: Questo articolo spiega come funziona un ciclo di migrazione a Microsoft Intune e offre esempi di come gestire i cicli di migrazione.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30e104d82580a5a0b6b01edb0eaade0673b33d83
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2019
ms.locfileid: "67548393"
---
# <a name="typical-migration-cycle"></a>Ciclo di migrazione tipico

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

Vedere [come Adatum Corporation ha gestito il processo di migrazione da un provider MDM di terze parti a Intune](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0).

## <a name="monitoring-migration"></a>Monitoraggio della migrazione

Intune offre vari strumenti per il monitoraggio della migrazione:

* Visualizzazioni dei gruppi di utenti di Intune

* Set di report predefiniti

* Avvisi nella console

Tenere traccia del numero di utenti con dispositivi registrati dopo ogni fase per poter:

- Valutare l'efficacia del piano di comunicazione.

- Stimare l'impatto dell'applicazione dell'accesso condizionale.


## <a name="post-migration"></a>Post-migrazione

Ritirare il precedente provider MDM e annullare la sottoscrizione al servizio dopo aver completato la migrazione a Intune. Rimuovere anche eventuali requisiti di infrastruttura non necessari seguendo le istruzioni del provider MDM.
