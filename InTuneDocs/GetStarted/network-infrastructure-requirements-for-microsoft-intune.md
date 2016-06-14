---
# required metadata

title: Requisiti dell'infrastruttura di rete | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 074de65b-84a5-4a01-a824-18ffd838eab0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Requisiti dell'infrastruttura di rete per Microsoft Intune
Prima di configurare Microsoft Intune leggere questo argomento e gli altri requisiti indicati in [Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)

Questo argomento descrive i requisiti che consentono all'infrastruttura di rete di passare le comunicazioni tra i dispositivi gestiti e usati per gestire la sottoscrizione a Intune e i siti Web su Internet usati dal servizio basato sul cloud.

Non è richiesto l'utilizzo di un'infrastruttura locale (come ad esempio un server in cui si deve installare il software), tuttavia esistono delle opzioni per usare l'infrastruttura locale, tra cui gli strumenti di sincronizzazione Exchange e Active Directory.

Per gestire i computer protetti da firewall e server proxy, è necessario configurare i firewall e i server proxy per consentire le comunicazioni per Intune.

## Requisiti per firewall, porte e domini
I dispositivi gestiti richiedono configurazioni che consentono a **Tutti gli utenti** di accedere a vari servizi tramite i firewall.

Nella tabella seguente sono elencati i domini e i servizi a cui accede il client di Intune.


|**Dominio**|**Porte**|**Indirizzo IP**|
|------|----|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>m.manage.microsoft.com<br>p.manage.microsoft.com<br>portal.manage.microsoft.com<br>r.manage.microsoft.com|80 e 443|134.170.168.254<br>134.170.51.126
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
|Comunicazione del dispositivo Samsung KNOX attraverso il firewall|Per consentire ai dispositivi Samsung KNOX di contattare i server KNOX attraverso il firewall, seguire le istruzioni in Domande frequenti su Samsung KNOX.||
|Documentazione, Guida e assistenza:</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||



## Requisiti per i server proxy
Per gestire i computer protetti da un server proxy, occorre ricordare quanto segue:

-   Il server proxy deve supportare sia **HTTP** che **HTTPS** perché i client di Intune usano entrambi i protocolli.

-   Intune supporta i server proxy non autenticati.

È possibile modificare le impostazioni del server proxy per i singoli computer client o usare le impostazioni di Criteri di gruppo per modificare le impostazioni di tutti i computer client protetti da uno specifico server proxy.

È anche possibile usare un server proxy che memorizza il contenuto nella cache per [ridurre la larghezza di banda di rete](network-bandwidth-use.md) usata dai client di Intune.


### Vedere anche
[Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO2-->


