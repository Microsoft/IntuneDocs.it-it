---
title: Modello di dati del data warehouse | Microsoft Docs
description: Il data warehouse di Intune esegue il campionamento giornaliero dei dati per fornire una visualizzazione cronologia dell'ambiente per dispositivi mobili in continua evoluzione.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f52531f854c57551613b1e94f0cfd0925c6d3d12
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="data-warehouse-data-model"></a>Modello di dati del data warehouse

Il data warehouse di Intune esegue il campionamento giornaliero dei dati per fornire una visualizzazione cronologica dell'ambiente dei dispositivi mobili, in continua evoluzione. La visualizzazione è costituita da elementi correlati nel tempo.

## <a name="things-entity-sets"></a>Elementi: set di entità

Il warehouse espone i dati nelle aree generali seguenti:

  -  App abilitate per la protezione dati e utilizzo
  -  Dispositivi registrati, proprietà e inventario
  -  Inventario app e software
  -  Configurazione del dispositivo e criteri di conformità

Queste aree contengono le entità (o elementi) significative per l'ambiente Intune. Informazioni dettagliate sui set di entità sono disponibili negli argomenti seguenti:

  -  [Applicazione](reports-ref-application.md)
  -  [Data](reports-ref-date.md)
  -  [Dispositivi](reports-ref-devices.md)
  -  [Intune Management Extension](reports-ref-intunemanagementextension.md) (Estensione di gestione di Intune)
  -  [Criteri](reports-ref-policy.md)
  -  [Gestione delle app mobili (MAM)](reports-ref-mobile-app-management.md)
  -  [User](reports-ref-user.md)
  -  [Current User](reports-ref-current-user.md)
  -  [Associazioni utente-dispositivo](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>Relazione: modello di schema a stella

Il warehouse organizza le entità in relazioni significative per il tipo di domande che si vogliono chiedere. È possibile, ad esempio, verificare il numero di installazioni di un'applicazione Android sviluppata internamente. La struttura del data warehouse consente di ottenere informazioni nell'ambiente per dispositivi mobili. A loro volta, gli strumenti di analisi come Microsoft Power BI possono usare il modello di dati del data warehouse per creare visualizzazioni e dashboard dinamici.

Le entità e le relazioni usano un modello di schema a stella, che correla i fatti sulla dimensione del tempo. Un *fatto* nel contesto del modello è una misura quantitativa quale il numero di dispositivi, il numero di app o la data/ora di registrazione. Nelle tabelle dei fatti viene archiviata una grande quantità di dati. Le tabelle possono quindi acquisire dimensioni molto grandi e, per questo motivo, le informazioni vengono mantenute al loro interno per 30 giorni. Una *dimensione* fornisce il contesto dei fatti. Se il fatto indica cosa è accaduto, le dimensioni indicano a chi è accaduto. Le tabelle delle dimensioni, come la tabella **User**, sono di dimensioni inferiori e possono quindi mantenere i dati per periodi più lunghi rispetto alle tabelle dei fatti. 

Un modello di schema a stella è ottimizzato per l'analisi di dati e la flessibilità per poter creare i report necessari a comprendere l'ambiente per dispositivi mobili in continua evoluzione.

## <a name="time-daily-snapshots"></a>Tempo: snapshot giornalieri

Il warehouse si trova a valle rispetto ai dati di Intune. Intune crea uno snapshot giornaliero a mezzanotte UTC e lo archivia nel warehouse. La durata degli snapshot acquisiti varia in base alla tabella dei fatti in uso. Alcune tabelle li mantengono per sette giorni, altre per 30 giorni e altre per periodi ancora più lunghi.

## <a name="next-steps"></a>Passaggi successivi

 - Per altre informazioni su come il data warehouse controlla la durata di un utente in Intune, vedere [Rappresentazione della durata degli utenti nel data warehouse di Intune](reports-ref-user-timeline.md).
 - Per altre informazioni sull'uso dei data warehouse, vedere [Create First Data WareHouse](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse) (Creare il primo warehouse).
 - Per altre informazioni sull'uso di Power BI e di un data warehouse, vedere [Create a new Power BI report by importing a dataset](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/) (Creare un nuovo report di Power BI importando un set di dati). 
