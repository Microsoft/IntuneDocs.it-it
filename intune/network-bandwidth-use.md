---
title: Requisiti e dettagli della larghezza di banda di rete per Microsoft Intune
titlesuffix: 
description: Requisiti di configurazione e dettagli della larghezza di banda di rete per Intune.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b21c4421914294e84bae637e489065c5e4410839
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Requisiti di configurazione di rete di Intune e larghezza di banda

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Queste linee guida consentono agli amministratori di Intune di conoscere i requisiti di rete per il servizio Intune. È possibile usare queste informazioni per comprendere i requisiti di larghezza di banda e le impostazioni di porta e indirizzo IP necessarie per le impostazioni proxy.

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
|Aggiornamenti software|Varia<br /><br />Le dimensioni dipendono dagli aggiornamenti distribuiti.|**Ogni mese**<br /><br />In genere, gli aggiornamenti software vengono rilasciati il secondo martedì di ogni mese.<br /><br />Un computer appena registrato o distribuito potrebbe usare più larghezza di banda di rete durante il download della serie completa di aggiornamenti rilasciati in precedenza.|
|Service Pack|Varia<br /><br />Le dimensioni variano per ogni Service Pack distribuito.|**Varia**<br /><br />Dipende da quando si distribuiscono i Service Pack.|
|Distribuzione del software|Varia<br /><br />Le dimensioni dipendono dal software distribuito.|**Varia**<br /><br />Dipende da quando si distribuisce il software.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>Come ridurre l'uso della larghezza di banda di rete
È possibile usare uno dei metodi seguenti per ridurre l'uso della larghezza di banda di rete per i client di Intune.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Usare un server proxy per memorizzare nella cache le richieste di contenuti
È possibile usare un server proxy che memorizza i contenuti nella cache per ridurre i download duplicati e l'utilizzo della larghezza di banda di rete per i contenuti scaricati da Internet.

Un server proxy di memorizzazione nella cache che riceve le richieste di contenuto dai client può recuperare il contenuto e memorizzare nella cache le risposte Web e i download. Il server usa i dati memorizzati nella cache per rispondere alle richieste successive provenienti dai client.

Di seguito vengono riportate alcune impostazioni tipiche da usare per un server proxy che memorizza contenuti nella cache per i client di Intune.

|Impostazione|Impostazione consigliata|Dettagli|
|-----------|---------------------|-----------|
|Dimensione della cache|da 5 a 30 GB|Il valore varia in base al numero di computer client della rete e alle configurazioni usate. Per evitare che i file vengano eliminati troppo presto, regolare le dimensioni della cache per l'ambiente.|
|Dimensione del file nella singola cache|950 MB|L'impostazione potrebbe non essere disponibile in tutti i server proxy per la memorizzazione nella cache.|
|Tipi di oggetto da memorizzare nella cache|HTTP<br /><br />HTTPS<br /><br />BITS|I pacchetti Intune sono file CAB recuperati tramite download del Servizio trasferimento intelligente in Background (BITS) su HTTP.|
Per informazioni sull'utilizzo di un server proxy per memorizzare contenuto nella cache, vedere la documentazione per la soluzione server proxy in uso.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Usare Servizio trasferimento intelligente in background sui computer
Intune supporta l'uso di Servizio trasferimento intelligente in background (BITS) in un computer Windows per diminuire l'uso di larghezza di banda di rete durante le ore configurate. È possibile configurare i criteri per BITS nella pagina **Larghezza di banda di rete** del criterio Agente di Intune.

Per altre informazioni su BITS e sui computer Windows, vedere [Servizio trasferimento intelligente in background](http://technet.microsoft.com/library/bb968799.aspx) nella libreria TechNet.

### <a name="use-branchcache-on-computers"></a>Usare BranchCache sui computer
I client di Intune possono usare BranchCache per ridurre il traffico WAN. I sistemi operativi seguenti supportano BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Per usarlo nel computer client, BranchCache deve essere abilitato e configurato per la **modalità cache distribuita**.

Per impostazione predefinita, BranchCache e la modalità cache distribuita vengono abilitati nei computer quando viene installato il client di Intune. Tuttavia, se i criteri di gruppo hanno disabilitato BranchCache, Intune non ignora i criteri e BranchCache rimane disabilitato.

Se si usa BranchCache, collaborare con gli altri amministratori dell'organizzazione per la gestione dei criteri di gruppo e dei criteri firewall di Intune. Assicurarsi che non distribuiscano criteri che disabilitano BranchCache o le eccezioni del firewall. Per altre informazioni su BranchCache, vedere [Panoramica di BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Requisiti per le comunicazioni di rete

Abilitare le comunicazioni di rete tra i dispositivi gestiti e i siti Web richiesti per i servizi basati su cloud.

Intune non usa alcuna infrastruttura locale (come server che eseguono il software Intune), ma esistono delle opzioni per usare l'infrastruttura locale, tra cui gli strumenti di sincronizzazione di Exchange e Active Directory.

Per gestire i computer protetti da firewall e i server proxy, è necessario abilitare le comunicazioni per Intune.

-   Il server proxy deve supportare sia **HTTP (80)** che **HTTPS (443)** perché i client di Intune usano entrambi i protocolli
-   Intune richiede l'accesso del server proxy non autenticato a manage.microsoft.com per alcune operazioni, ad esempio il download di software e aggiornamenti

È possibile modificare le impostazioni del server proxy per i singoli computer client o usare le impostazioni di Criteri di gruppo per modificare le impostazioni di tutti i computer client protetti da uno specifico server proxy.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

I dispositivi gestiti richiedono configurazioni che consentono a **Tutti gli utenti** di accedere ai servizi tramite i firewall.

Nelle tabelle seguenti sono elencati i servizi e le porte a cui accede il client di Intune:

|**Domini**|**Indirizzo IP**|
|---------------------|-----------|
|login.microsoftonline.com | Altre informazioni sono disponibili in [URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|23.97.165.17|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|

### <a name="apple-device-network-information"></a>Informazioni di rete dei dispositivi Apple
| Hostname  | URL (indirizzo IP/subnet) | Protocollo | Porta | Dispositivo |
| --- | --- | --- | --- | --- |
|  Console di amministrazione  | gateway.push.apple.com (17.0.0.0/8) | TCP | 2195 | Apple iOS e macOS |
| Console di amministrazione  | feedback.push.apple.com(17.0.0.0/8) | TCP | 2196 | Apple iOS e macOS |
| Console di amministrazione  | Apple iTunesitunes.apple.com, \*.mzstatic.com, \*.phobos.apple.com, \*.phobos.apple.com.edgesuite.net | HTTP | 80 | Apple iOS e macOS  |
| Server PI  | gateway.push.apple.com(17.0.0.0/8) feedback.push.apple.com(17.0.0.0/8) | TCP | 2195, 2196 | Per messaggi cloud di Apple iOS e macOS. |
| Servizi per dispositivi  | gateway.push.apple.com | TCP | 2195 | Apple  |
| Servizi per dispositivi  | feedback.push.apple.com | TCP | 2196 | Apple  |
| Servizi per dispositivi  | Apple iTunesitunes.apple.com \*.mzstatic.com\*.phobos.apple.com \*.phobos.apple.com.edgesuite.net | HTTP | 80 | Apple  |
| Dispositivi (Internet/Wi-Fi) | #-courier.push.apple.com(17.0.0.0/8) | TCP | 5223 e 443 | Solo Apple. &#39;#&#39; è un numero casuale compreso tra 0 e 200. |
| Dispositivi (Internet/Wi-Fi) | phobos.apple.comocsp.apple.comax.itunes.apple.com | HTTP/HTTPS | 80 o 443 | Solo Apple |
