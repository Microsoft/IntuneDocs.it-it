---
title: Modello di dati del data warehouse | Microsoft Docs
description: Il data warehouse di Intune esegue il campionamento giornaliero dei dati per fornire una visualizzazione cronologia dell'ambiente per dispositivi mobili in continua evoluzione.
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f720d5f9dbf91d7f098a640d640f8f35136da4fc
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2017
---
# <a name="data-warehouse-data-model"></a>Modello di dati del data warehouse

Il data warehouse di Intune esegue il campionamento giornaliero dei dati per fornire una visualizzazione cronologia dell'ambiente per dispositivi mobili in continua evoluzione.

I dati estratti dal tenant vengono aggiunti a un data warehouse. Il warehouse è un set di entità e relazioni che sono significative per il tipo di domande che si vogliono chiedere. Ad esempio, è possibile esaminare il numero di installazioni di un'applicazione Android sviluppata internamente per ogni giorno dell'ultima settimana per valutare se è presente una tendenza crescente di installazioni. La struttura del data warehouse consente di ottenere informazioni nell'ambiente per dispositivi mobili. A loro volta, gli strumenti di analisi come Microsoft Power BI possono usare il modello di dati del data warehouse per creare visualizzazioni e dashboard dinamici.

La struttura del data warehouse di Intune usa un modello di schema a stella. Lo schema a stella organizza i fatti sulla dimensione del tempo. Un *fatto* nel contesto del modello è una misura quantitativa quale il numero di dispositivi, il numero di app o la data/ora di registrazione. Una *dimensione* nel contesto del modello è un set di categorie con le rispettive relazioni gerarchiche. Ad esempio, i giorni sono raggruppati in mesi e i mesi sono raggruppati in anni. Un modello di schema a stella è ottimizzato per l'analisi di dati e la flessibilità per poter creare i report necessari a comprendere l'ambiente per dispositivi mobili in continua evoluzione.

Il warehouse espone i dati nelle seguenti categorie generali:
  -  App abilitate per la protezione dati e utilizzo
  -  Dispositivi registrati, proprietà e inventario
  -  Inventario app e software
  -  Configurazione del dispositivo e criteri di conformità

**Set di entità del modello di dati**

I set di entità sono raccolte di entità denominate nel modello di dati. Questi set contengono le entità che definiscono i dati raccolti nel modello. Ogni set di entità fornisce un punto di accesso nel modello di dati Data warehouse. Sono disponibili informazioni dettagliate sulle seguenti categorie di entità:

  -  [Applicazione](reports-ref-application.md)
  -  [Data](reports-ref-date.md)
  -  [Dispositivi](reports-ref-devices.md)
  -  [Intune Management Extension](reports-ref-intunemanagementextension.md) (Estensione di gestione di Intune)
  -  [Criteri](reports-ref-policy.md)
  -  [Gestione delle app mobili (MAM)](reports-ref-mobile-app-management.md)
  -  [Utente](reports-ref-user.md)
  -  [Associazioni utente-dispositivo](reports-ref-user-device.md)