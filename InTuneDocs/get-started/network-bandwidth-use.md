---
title: Uso della larghezza di banda di rete in Intune | Documentazione Microsoft
description: utilizzo della larghezza di banda di rete in intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0f5972171349325eeb750e552481cbcf903fdf95
ms.openlocfilehash: 9f1cd7ea3e92ac2e3a1b828e8185961060a7c619


---

# <a name="intune-network-bandwidth-use"></a>Uso della larghezza di banda di rete di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Queste indicazioni sono rivolte agli amministratori di sistema responsabili della gestione dei dispositivi nell'organizzazione. Per informazioni sull'uso di Intune nel dispositivo mobile, vedere le [domande frequenti su Portale aziendale di Intune](https://docs.microsoft.com/intune/enduser/company-portal-frequently-asked-questions).

Prima di configurare Microsoft Intune leggere questo argomento e gli altri requisiti indicati in [Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)

Usare le informazioni nelle sezioni seguenti per pianificare il traffico di rete per i client Microsoft Intune.

## <a name="average-network-traffic"></a>Traffico di rete medio
In questa tabella sono elencate le dimensioni approssimative e la frequenza di contenuto comune che viaggia attraverso la rete per ogni client.

> [!NOTE]
> Per assicurarsi che i computer e i dispositivi mobili ricevano gli aggiornamenti e i contenuti necessari dal servizio Intune, è necessario che siano connessi periodicamente a Internet. Il tempo necessario per ricevere gli aggiornamenti o i contenuti può variare ma, come indicazione generale, è opportuno lasciarli connessi a Internet senza interruzioni per almeno un'ora al giorno.

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
Per ridurre la duplicazione di scaricamenti e diminuire l'uso di larghezza di banda di rete da parte di client che richiedono contenuto da Internet, è possibile usare un server proxy in grado di memorizzare contenuto nella cache.

Un server proxy di memorizzazione nella cache riceve richieste di contenuto dai computer client sulla rete, recupera quel contenuto da Internet e poi memorizza nella cache sia le risposte HTTP che i download binari. Il server usa le informazioni memorizzate nella cache per rispondere a richieste successive dai computer client di Intune.

Di seguito vengono riportate alcune impostazioni tipiche da usare per un server proxy che memorizza contenuti nella cache per i client di Intune.

|Impostazioni|Impostazione consigliata|Dettagli|
|-----------|---------------------|-----------|
|Dimensione della cache|da 5 a 30 GB|Il valore varia in base al numero di computer client della rete e alle configurazioni usate. Per evitare che i file vengano eliminati troppo presto, regolare le dimensioni della cache per l'ambiente.|
|Dimensione del file nella singola cache|950 MB|L'impostazione potrebbe non essere disponibile in tutti i server proxy per la memorizzazione nella cache.|
|Tipi di oggetto da memorizzare nella cache|HTTP<br /><br />HTTPS<br /><br />BITS|I pacchetti Intune sono file CAB recuperati tramite download del Servizio trasferimento intelligente in Background (BITS) su HTTP.|
Per informazioni sull'utilizzo di un server proxy per memorizzare contenuto nella cache, vedere la documentazione per la soluzione server proxy in uso.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Usare Servizio trasferimento intelligente in background sui computer
Intune supporta l'uso di Servizio trasferimento intelligente in background (BITS) in un computer Windows per diminuire l'uso di larghezza di banda di rete durante le ore configurate. È possibile configurare i criteri per BITS nella pagina **Larghezza di banda di rete** del criterio Agente di Intune.

Per altre informazioni su BITS e sui computer Windows, vedere [Servizio trasferimento intelligente in background](http://technet.microsoft.com/library/bb968799.aspx) nella libreria TechNet.

### <a name="use-branchcache-on-computers"></a>Usare BranchCache sui computer
I client di Intune possono usare BranchCache per ridurre il traffico WAN. I seguenti sistemi operativi supportati come client supportano anche BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Per usarlo nel computer client, BranchCache deve essere abilitato e configurato per la **modalità cache distribuita**.

Per impostazione predefinita, BranchCache e la modalità Cache distribuita vengono abilitati in un computer quando viene installato il client di Intune. Tuttavia, se è presente un Criterio di gruppo che disattiva BranchCache, Intune non sostituisce quel criterio e l'opzione BranchCache resterà disabilitata nel computer.

Se si usa BranchCache, è necessario comunicarlo agli altri amministratori nell'organizzazione che gestiscono i Criteri di gruppo e i criteri firewall di Intune per assicurarsi che non distribuiscano criteri che disabilitano BranchCache o le eccezioni Firewall. Per altre informazioni su BranchCache, vedere [Panoramica di BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Requisiti per le comunicazioni di rete

È necessario abilitare le comunicazioni di rete tra i dispositivi gestiti e usati per gestire la sottoscrizione di Intune e i siti Web richiesti per i servizi basati su cloud.

Intune non usa alcuna infrastruttura locale (come server che eseguono il software Intune), ma esistono delle opzioni per usare l'infrastruttura locale, tra cui gli strumenti di sincronizzazione di Exchange e Active Directory.

Per gestire i computer protetti da firewall e server proxy, è necessario configurare i firewall e i server proxy per consentire le comunicazioni per Intune.

### <a name="requirements-for-proxy-servers"></a>Requisiti per i server proxy
Per gestire i computer protetti da un server proxy, occorre ricordare quanto segue:

-   Il server proxy deve supportare sia **HTTP** che **HTTPS** perché i client di Intune usano entrambi i protocolli
-   Intune supporta i server proxy non autenticati

È possibile modificare le impostazioni del server proxy per i singoli computer client o usare le impostazioni di Criteri di gruppo per modificare le impostazioni di tutti i computer client protetti da uno specifico server proxy.

### <a name="requirements-for-firewalls-ports-and-domains"></a>Requisiti per firewall, porte e domini
I dispositivi gestiti richiedono configurazioni che consentono a **Tutti gli utenti** di accedere ai servizi tramite i firewall.

Nella tabella seguente sono elencati i domini e i servizi a cui accede il client di Intune.

|**Dominio**|**Porte**|**Indirizzo IP**|
|------|----|---|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>p.manage.microsoft.com<br>r.manage.microsoft.com|80 e 443|134.170.168.254<br>134.170.51.126
|m.manage.microsoft.com|80 e 443| 13.91.59.243<br>40.68.30.140
|portal.manage.microsoft.com|80 e 443|40.121.50.69<br>52.169.30.159
|account.manage.microsoft.com|80 e 443|157.56.13.59
|fef.msua01.manage.microsoft.com|80 e 443|138.91.243.97
|fef.msua02.manage.microsoft.com|80 e 443|23.96.112.46
|fef.msua04.manage.microsoft.com|80 e 443|23.96.112.28
|fef.msua05.manage.microsoft.com|80 e 443|138.91.244.151
|fef.msub01.manage.microsoft.com|80 e 443|137.135.128.214
|fef.msub02.manage.microsoft.com|80 e 443|137.135.130.29
|fef.msub03.manage.microsoft.com|80 e 443|23.97.165.17
|fef.msub05.manage.microsoft.com|80 e 443|23.97.166.52
|fef.msuc01.manage.microsoft.com|80 e 443|207.46.225.1
|fef.msuc02.manage.microsoft.com|80 e 443|23.98.66.118
|fef.msuc03.manage.microsoft.com|80 e 443|23.101.0.100
|fef.msuc05.manage.microsoft.com|80 e 443|207.46.154.33
|fef.msua06.manage.microsoft.com|80 e 443|104.42.188.1
|fei.msua01.manage.microsoft.com|80 e 443|138.91.240.131
|fei.msua02.manage.microsoft.com|80 e 443|23.96.112.143
|fei.msua04.manage.microsoft.com|80 e 443|23.96.112.147
|fei.msua05.manage.microsoft.com|80 e 443|138.91.240.163
|fei.msub01.manage.microsoft.com|80 e 443|137.135.130.85
|fei.msub02.manage.microsoft.com|80 e 443|137.135.132.149
|fei.msub03.manage.microsoft.com|80 e 443|23.97.160.232
|fei.msub05.manage.microsoft.com|80 e 443|23.97.162.250
|fei.msuc01.manage.microsoft.com|80 e 443|207.46.224.73
|fei.msuc02.manage.microsoft.com|80 e 443|23.98.66.194
|fei.msuc03.manage.microsoft.com|80 e 443|23.101.2.105
|fei.msuc05.manage.microsoft.com|80 e 443|207.46.147.126
|fei.msua06.manage.microsoft.com|80 e 443|138.91.149.190
|m.fei.msua01.manage.microsoft.com|80 e 443|138.91.240.131
|m.fei.msua02.manage.microsoft.com|80 e 443|23.96.112.143
|m.fei.msua04.manage.microsoft.com|80 e 443|23.96.112.147
|m.fei.msua05.manage.microsoft.com|80 e 443|138.91.240.163
|m.fei.msub01.manage.microsoft.com|80 e 443|137.135.130.85
|m.fei.msub02.manage.microsoft.com|80 e 443|137.135.132.149
|m.fei.msub03.manage.microsoft.com|80 e 443|23.97.160.232
|m.fei.msub05.manage.microsoft.com|80 e 443|23.97.162.250
|m.fei.msuc01.manage.microsoft.com|80 e 443|207.46.224.73
|m.fei.msuc02.manage.microsoft.com|80 e 443|23.98.66.194
|m.fei.msuc03.manage.microsoft.com|80 e 443|23.101.2.105
|m.fei.msuc05.manage.microsoft.com|80 e 443|207.46.147.126
|m.fei.msua06.manage.microsoft.com|80 e 443|138.91.149.190
|m.msua01.manage.microsoft.com|80 e 443|157.55.50.182
|m.msua02.manage.microsoft.com|80 e 443|134.170.49.121
|m.msua04.manage.microsoft.com|80 e 443|134.170.49.126
|m.msua05.manage.microsoft.com|80 e 443|157.55.240.190
|m.msua06.manage.microsoft.com|80 e 443|134.170.49.114
|m.msub01.manage.microsoft.com|80 e 443|94.245.121.50
|m.msub02.manage.microsoft.com|80 e 443|94.245.121.58
|m.msub03.manage.microsoft.com|80 e 443|94.245.121.56
|m.msub05.manage.microsoft.com|80 e 443|157.56.113.123
|m.msuc01.manage.microsoft.com|80 e 443|104.44.84.187
|m.msuc02.manage.microsoft.com|80 e 443|104.44.84.188
|m.msuc03.manage.microsoft.com|80 e 443|104.44.84.189
|m.msuc05.manage.microsoft.com|80 e 443|111.221.76.60
|msua01.manage.microsoft.com|80 e 443|157.55.50.182
|msua02.manage.microsoft.com|80 e 443|134.170.49.121
|msua04.manage.microsoft.com|80 e 443|134.170.49.126
|msua05.manage.microsoft.com|80 e 443|157.55.240.190
|msub01.manage.microsoft.com|80 e 443|94.245.121.50
|msub02.manage.microsoft.com|80 e 443|94.245.121.58
|msub03.manage.microsoft.com|80 e 443|94.245.121.56
|msub05.manage.microsoft.com|80 e 443|157.56.113.123
|msuc01.manage.microsoft.com|80 e 443|104.44.84.187
|msuc02.manage.microsoft.com|80 e 443|104.44.84.188
|msuc03.manage.microsoft.com|80 e 443|104.44.84.189
|msuc05.manage.microsoft.com|80 e 443|111.221.76.60
|msua06.manage.microsoft.com|80 e 443|134.170.49.114
|ncufun.account.manage.microsoft.com|80 e 443|157.55.252.224
|neufun.account.manage.microsoft.com|80 e 443|65.52.229.134
|portal.fei.msua01.manage.microsoft.com|80 e 443|138.91.240.131
|portal.fei.msua02.manage.microsoft.com|80 e 443|23.96.112.143
|portal.fei.msua04.manage.microsoft.com|80 e 443|23.96.112.147
|portal.fei.msua05.manage.microsoft.com|80 e 443|138.91.240.163
|portal.fei.msub01.manage.microsoft.com|80 e 443|137.135.130.85
|portal.fei.msub02.manage.microsoft.com|80 e 443|137.135.132.149
|portal.fei.msub03.manage.microsoft.com|80 e 443|23.97.160.232
|portal.fei.msub05.manage.microsoft.com|80 e 443|23.97.162.250
|portal.fei.msuc01.manage.microsoft.com|80 e 443|207.46.224.73
|portal.fei.msuc02.manage.microsoft.com|80 e 443|23.98.66.194
|portal.fei.msuc03.manage.microsoft.com|80 e 443|23.101.2.105
|portal.fei.msuc05.manage.microsoft.com|80 e 443|207.46.147.126
|portal.fei.msua06.manage.microsoft.com|80 e 443|138.91.149.190
|portal.msua01.manage.microsoft.com|80 e 443|157.55.50.182
|portal.msua02.manage.microsoft.com|80 e 443|134.170.49.121
|portal.msua04.manage.microsoft.com|80 e 443|134.170.49.126
|portal.msua05.manage.microsoft.com|80 e 443|157.55.240.190
|portal.msub01.manage.microsoft.com|80 e 443|94.245.121.50
|portal.msub02.manage.microsoft.com|80 e 443|94.245.121.58
|portal.msub03.manage.microsoft.com|80 e 443|94.245.121.56
|portal.msub05.manage.microsoft.com|80 e 443|157.56.113.123
|portal.msuc01.manage.microsoft.com|80 e 443|104.44.84.187
|portal.msuc02.manage.microsoft.com|80 e 443|104.44.84.188
|portal.msuc03.manage.microsoft.com|80 e 443|104.44.84.189
|portal.msuc05.manage.microsoft.com|80 e 443|111.221.76.60
|portal.msua06.manage.microsoft.com|80 e 443|134.170.49.114
|ssu2.manage.microsoft.com|80 e 443|157.55.99.181
|status.manage.microsoft.com|80 e 443|157.55.99.170
|swda01.manage.microsoft.com<br>swda02.manage.microsoft.com<br>swdb01.manage.microsoft.com<br>swdb02.manage.microsoft.com<br>swdc01.manage.microsoft.com<br>swdc02.manage.microsoft.com|80 e 443|93.184.215.200
|*.microsoftonline-p.com|80 e 443||
|has.spserv.microsoft.com<br>Obbligatorio per il servizio di attestazione dell'integrità del dispositivo|443||
|*.microsoftonline-p.net|80 e 443||
|*.portal.office.com|80 e 443||
|*.spynet2.microsoft.com|443||
|c.microsoft.com|80 e 443||
|c1.microsoft.com|80 e 443||
|blob.core.windows.net|80 e 443||
|ajax.aspnetcdn.com|80 e 443||
|*.googleapis.com<br>Questo dominio è richiesto per il supporto di JQuery quando si usa il sito Web del portale aziendale.|80 e 443||
|wustat.microsoft.com|80 e 443||
|Servizi Microsoft Update|\*.update.microsoft.com<br>download.microsoft.com<br>update.microsoft.com<br>\*.download.windowsupdate.com<br>download.windowsupdate.com<br>\*.windowsupdate.com<br>windowsupdate.microsoft.com<br>ntservicepack.microsoft.com|80 e 443|
|Richieste di ricerca DNS|manage.microsoft.com.nsatc.net|80|
|Comunicazioni del dispositivo Samsung KNOX Standard attraverso il firewall|Per consentire ai dispositivi Samsung KNOX Standard di contattare i server KNOX Standard attraverso il firewall, seguire le istruzioni nelle domande frequenti relative a Samsung KNOX Standard.||
|Comunicazione con accesso condizionale|443|204.79.197.200|
|Documentazione, Guida e assistenza:</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||

>[!div class="step-by-step"]

>[&larr; **Prerequisiti**](what-to-know-before-you-start-microsoft-intune.md)     [**Sottoscrizione** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)  



<!--HONumber=Feb17_HO2-->


