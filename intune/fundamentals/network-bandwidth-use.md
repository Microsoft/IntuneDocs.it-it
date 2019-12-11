---
title: Requisiti e dettagli della larghezza di banda di rete per Microsoft Intune
titleSuffix: ''
description: Requisiti di configurazione e dettagli della larghezza di banda di rete per Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0507d607bfac6c084f1ce0b1f59d7474810ec8b7
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73415105"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Requisiti di configurazione di rete di Intune e larghezza di banda

È possibile usare queste informazioni per capire quali sono i requisiti di larghezza di banda per le distribuzioni di Intune.

## <a name="average-network-traffic"></a>Traffico di rete medio

In questa tabella sono elencate le dimensioni approssimative e la frequenza di contenuto comune che viaggia attraverso la rete per ogni client.

> [!NOTE]
> Per garantire che i dispositivi ricevano gli aggiornamenti e i contenuti da Intune è necessario che vengano regolarmente connessi a Internet. Il tempo necessario per ricevere gli aggiornamenti o i contenuti può variare ma è opportuno lasciarli connessi a Internet senza interruzioni per almeno un'ora al giorno.

|Tipo di contenuto|Dimensione approssimativa|Frequenza e dettagli|
|----------------|--------------------|-------------------------|
|Installazione del client di Intune<br /><br />**I requisiti seguenti vanno aggiunti all'installazione del client di Intune**|125 MB|**Una volta**<br /><br />Le dimensioni del download del client variano a seconda del sistema operativo del computer client.|
|Pacchetto di registrazione client|15 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Agente Endpoint Protection|65 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Agente Operations Manager|11 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Agente criteri|3 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Assistenza remota tramite l'agente Microsoft Easy Assist|6 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Operazioni quotidiane di client|6 MB|**Ogni giorno**<br /><br />Il client di Intune comunica regolarmente con il servizio Intune per verificare la disponibilità di aggiornamenti e criteri nonché per segnalare lo stato del client al servizio.|
|Aggiornamenti delle definizioni malware di Endpoint Protection|Varia<br /><br />In genere, da 40 KB a 2 MB|**Ogni giorno**<br /><br />Fino a tre volte al giorno.|
|Aggiornamento del motore Endpoint Protection|5 MB|**Ogni mese**|
|Aggiornamenti software|Varia<br /><br />Le dimensioni dipendono dagli aggiornamenti distribuiti.|**Monthly** (Mensile)<br /><br />In genere, gli aggiornamenti software vengono rilasciati il secondo martedì di ogni mese.<br /><br />Un computer appena registrato o distribuito potrebbe usare più larghezza di banda di rete durante il download della serie completa di aggiornamenti rilasciati in precedenza.|
|Service Pack|Varia<br /><br />Le dimensioni variano per ogni Service Pack distribuito.|**Varia**<br /><br />Dipende da quando si distribuiscono i Service Pack.|
|Distribuzione del software|Varia<br /><br />Le dimensioni dipendono dal software distribuito.|**Varia**<br /><br />Dipende da quando si distribuisce il software.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>Come ridurre l'uso della larghezza di banda di rete

È possibile usare uno dei metodi seguenti per ridurre l'uso della larghezza di banda di rete per i client di Intune.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Usare un server proxy per memorizzare nella cache le richieste di contenuti

È possibile usare un server proxy che memorizza i contenuti nella cache per ridurre i download duplicati e l'utilizzo della larghezza di banda di rete per i contenuti scaricati da Internet.

Un server proxy di memorizzazione nella cache che riceve le richieste di contenuto dai client può recuperare il contenuto e memorizzare nella cache le risposte Web e i download. Il server usa i dati memorizzati nella cache per rispondere alle richieste successive provenienti dai client.

Di seguito vengono riportate alcune impostazioni tipiche da usare per un server proxy che memorizza contenuti nella cache per i client di Intune.


|          Impostazione           |           Impostazione consigliata           |                                                                                                  Dettagli                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Dimensione della cache         |             da 5 a 30 GB             | Il valore varia in base al numero di computer client della rete e alle configurazioni usate. Per evitare che i file vengano eliminati troppo presto, regolare le dimensioni della cache per l'ambiente. |
| Dimensione del file nella singola cache |                950 MB                 |                                                                     L'impostazione potrebbe non essere disponibile in tutti i server proxy per la memorizzazione nella cache.                                                                     |
|   Tipi di oggetto da memorizzare nella cache    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               I pacchetti Intune sono file CAB recuperati tramite download del Servizio trasferimento intelligente in Background (BITS) su HTTP.                                               |
> [!NOTE]
> Se si usa un server proxy per memorizzare nella cache le richieste di contenuti, la comunicazione viene crittografata solo tra il client e il proxy e dal proxy a Intune. La connessione dal client a Intune non viene crittografata end-to-end.

Per informazioni sull'utilizzo di un server proxy per memorizzare contenuto nella cache, vedere la documentazione per la soluzione server proxy in uso.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>Usare Servizio trasferimento intelligente in background (BITS) nei computer

Durante gli orari configurati è possibile usare BITS in un computer Windows per ridurre la larghezza di banda della rete. È possibile configurare i criteri BITS nella pagina **Larghezza di banda di rete** del criterio Agente di Intune.

> [!NOTE]
> Per la gestione di dispositivi mobili in Windows, solo l'interfaccia di gestione del sistema operativo per il tipo di app MobileMSI usa BITS per il download. AppX e MsiX usano il proprio stack di download non BITS e le app Win32 tramite l'agente di Intune usano Ottimizzazione recapito invece di BITS.

Per altre informazioni su BITS e sui computer Windows, vedere [Servizio trasferimento intelligente in background](https://technet.microsoft.com/library/bb968799.aspx) nella libreria TechNet.

### <a name="delivery-optimization"></a>Ottimizzazione recapito

Ottimizzazione recapito consente di usare Intune per ridurre il consumo di larghezza di banda quando i dispositivi Windows 10 scaricano aggiornamenti e applicazioni. Usando una cache distribuita con organizzazione automatica, è possibile estrarre i download dai server tradizionali e da origini alternative, ad esempio i peer di rete.

Per visualizzare l'elenco completo delle versioni di Windows 10 e dei tipi di contenuto supportati da Ottimizzazione recapito, vedere [l'articolo sugli aggiornamenti di Ottimizzazione recapito per Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements).

[Ottimizzazione recapito può essere impostata](../configuration/delivery-optimization-settings.md) come parte dei profili di configurazione dei dispositivi.

### <a name="use-branchcache-on-computers"></a>Usare BranchCache sui computer

I client di Intune possono usare BranchCache per ridurre il traffico WAN. I sistemi operativi seguenti supportano BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Per usarlo nel computer client, BranchCache deve essere abilitato e configurato per la **modalità cache distribuita**.

Quando il client di Intune è installato nei computer, BranchCache e la modalità cache distribuita sono abilitati per impostazione predefinita. Tuttavia, se i criteri di gruppo hanno disabilitato BranchCache, Intune non esegue l'override dei criteri e BranchCache rimane disabilitato.

Se si usa BranchCache, collaborare con gli altri amministratori dell'organizzazione per la gestione dei criteri di gruppo e dei criteri firewall di Intune. Assicurarsi che non distribuiscano criteri che disabilitano BranchCache o le eccezioni del firewall. Per altre informazioni su BranchCache, vedere [Panoramica di BranchCache](https://technet.microsoft.com/library/hh831696.aspx).

> [!NOTE]
> È possibile usare Microsoft Intune per gestire i PC Windows [come dispositivi mobili con la soluzione di gestione dei dispositivi mobili (MDM)](../enrollment/windows-enroll.md) o come computer con il software client di Intune. Si consiglia ai clienti di [usare la soluzione di gestione MDM](../enrollment/windows-enroll.md) laddove possibile. Con questo tipo di gestione BranchCache non è supportato. Per altre informazioni, vedere [Confrontare la gestione dei PC Windows come computer o come dispositivi mobili](../pc-management-comparison.md).


## <a name="next-steps"></a>Passaggi successivi

[Esaminare gli endpoint per Intune](../intune-endpoints.md)

