---
title: Uso della larghezza di banda di rete in Intune | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: e104dc52a8a9bdda4b2edb2939d8c7c36e8ecc12


---

# Uso della larghezza di banda di rete di Intune

Prima di configurare [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] leggere questo argomento e gli altri requisiti elencati in [Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).

Usare le informazioni nelle sezioni riportate di seguito per pianificare il traffico di rete per i client [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)].

## Traffico di rete medio
Nella tabella seguente sono elencate le dimensioni approssimative e la frequenza di contenuto comune che viaggia attraverso la rete per ogni client.

> [!NOTE]
> Per assicurarsi che i computer e i dispositivi mobili ricevano gli aggiornamenti e i contenuti necessari dal servizio [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], è necessario che siano connessi periodicamente a Internet. Il tempo necessario per ricevere gli aggiornamenti o i contenuti può variare ma, come indicazione generale, è opportuno lasciarli connessi a Internet senza interruzioni per almeno un'ora al giorno.

|Tipo di contenuto|Dimensione approssimativa|Frequenza e dettagli|
|----------------|--------------------|-------------------------|
|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Installazione client<br /><br />**I seguenti requisiti vanno aggiunti all'installazione del client [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]**|125 MB|**Una volta**<br /><br />Le dimensioni del download del client variano a seconda del sistema operativo del computer client.|
|Pacchetto di registrazione client|15 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Agente Endpoint Protection|65 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Agente Operations Manager|11 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Agente criteri|3 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Assistenza remota tramite l'agente Microsoft Easy Assist|6 MB|**Una volta**<br /><br />Ulteriori download sono possibili quando sono disponibili aggiornamenti per questo tipo di contenuto.|
|Operazioni quotidiane di client|6 MB|**Ogni giorno**<br /><br />Il client [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] comunica regolarmente con il servizio [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per verificare la disponibilità di aggiornamenti e criteri nonché per segnalare lo stato del client al servizio.|
|Aggiornamenti delle definizioni malware di Endpoint Protection|Varia<br /><br />In genere, da 40 KB a 2 MB|**Ogni giorno**<br /><br />Fino a tre volte al giorno.|
|Aggiornamento del motore Endpoint Protection|5 MB|**Ogni mese**|
|Aggiornamenti software|Varia<br /><br />Le dimensioni dipendono dagli aggiornamenti distribuiti.|**Ogni mese**<br /><br />In genere, gli aggiornamenti software vengono rilasciati il secondo martedì di ogni mese.<br /><br />Un computer appena registrato o distribuito potrebbe usare più larghezza di banda di rete durante il download della serie completa di aggiornamenti rilasciati in precedenza.|
|Service Pack|Varia<br /><br />Le dimensioni variano per ogni Service Pack distribuito.|**Varia**<br /><br />Dipende da quando si distribuiscono i Service Pack.|
|Distribuzione del software|Varia<br /><br />Le dimensioni dipendono dal software distribuito.|**Varia**<br /><br />Dipende da quando si distribuisce il software.|

## Come ridurre l'uso della larghezza di banda di rete
È possibile usare uno dei seguenti metodi per ridurre l'uso di larghezza di banda di rete per i client [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

### Usare un server proxy per memorizzare nella cache le richieste di contenuti
Per ridurre la duplicazione di scaricamenti e diminuire l'uso di larghezza di banda di rete da parte di client che richiedono contenuto da Internet, è possibile usare un server proxy in grado di memorizzare contenuto nella cache.

Un server proxy di memorizzazione nella cache riceve richieste di contenuto dai computer client sulla rete, recupera quel contenuto da Internet e poi memorizza nella cache sia le risposte HTTP che i download binari. Il server usa le informazioni memorizzate nella cache per rispondere a richieste successive dai computer client [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Di seguito vengono riportate alcune impostazioni tipiche da usare per un server proxy che memorizza contenuti nella cache per i client [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

|Impostazioni|Impostazione consigliata|Dettagli|
|-----------|---------------------|-----------|
|Dimensione della cache|da 5 a 30 GB|Il valore varia in base al numero di computer client della rete e alle configurazioni usate. Per evitare che i file vengano eliminati troppo presto, regolare le dimensioni della cache per l'ambiente.|
|Dimensione del file nella singola cache|950 MB|L'impostazione potrebbe non essere disponibile in tutti i server proxy per la memorizzazione nella cache.|
|Tipi di oggetto da memorizzare nella cache|HTTP<br /><br />HTTPS<br /><br />BITS|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] sono file CAB recuperati tramite download del Servizio trasferimento intelligente in Background (BITS) su HTTP.|
Per informazioni sull'utilizzo di un server proxy per memorizzare contenuto nella cache, vedere la documentazione per la soluzione server proxy in uso.

### Usare Servizio trasferimento intelligente in background sui computer
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] supporta l'utilizzo di Servizio trasferimento intelligente in background (BITS) in un computer Windows per diminuire l'uso di larghezza di banda di rete durante le ore configurate. È possibile configurare i criteri per BITS nella pagina **Larghezza di banda di rete** del criterio Agente di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Per altre informazioni su BITS e sui computer Windows, vedere [Servizio trasferimento intelligente in background](http://technet.microsoft.com/library/bb968799.aspx) nella libreria TechNet.

### Usare BranchCache sui computer
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] possono usare BranchCache per ridurre il traffico WAN. I seguenti sistemi operativi supportati come client supportano anche BranchCache:

-   [!INCLUDE[nextref_client_7](../includes/nextref_client_7_md.md)]

-   [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]

-   [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]

Per usarlo nel computer client, BranchCache deve essere abilitato e configurato per la **modalità cache distribuita**.

Per impostazione predefinita, BranchCache e la modalità Cache distribuita sono abilitate nel computer quando viene installato il client di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Tuttavia, se è presente un Criterio di gruppo che disattiva BranchCache, [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] non sostituisce quel criterio e l'opzione BranchCache resterà disabilitata nel computer.

Se si usa BranchCache, è necessario comunicarlo agli altri amministratori nell'organizzazione che gestiscono i Criteri di gruppo e i criteri firewall di [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] per assicurarsi che non distribuiscano criteri che disabilitano BranchCache o le eccezioni Firewall. Per altre informazioni su BranchCache, vedere [Panoramica di BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

### Vedere anche
[Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=Jun16_HO4-->


