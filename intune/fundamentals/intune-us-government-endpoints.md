---
title: Endpoint di rete per le distribuzioni US Government - Microsoft Intune
titleSuffix: ''
description: Esaminare gli endpoint US Government per Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d876c0268f38a09ea3729a7e19ee00b321ae897a
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000398"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Endpoint US Government per Microsoft Intune

Questa pagina elenca gli endpoint US Government necessari per le impostazioni proxy nelle distribuzioni di Intune.

Per gestire i dispositivi protetti da firewall e i server proxy, è necessario abilitare le comunicazioni per Intune.

- Il server proxy deve supportare sia **HTTP (80)** che **HTTPS (443)** perché i client di Intune usano entrambi i protocolli
- Per alcune attività, ad esempio il download di aggiornamenti software, Intune richiede l'accesso del server proxy non autenticato a manage.microsoft.com

È possibile modificare le impostazioni del server proxy nei singoli computer client. È anche possibile usare le impostazioni di Criteri di gruppo per modificare le impostazioni di tutti i computer client protetti da un server proxy specificato.

I dispositivi gestiti richiedono configurazioni che consentono a **Tutti gli utenti** di accedere ai servizi tramite i firewall.

Nelle tabelle seguenti sono elencati i servizi e le porte a cui accede il client di Intune:

|**Endpoint**|**Indirizzo IP**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Endpoint designati per i clienti delle distribuzioni US Government:
- Portale di Azure: https:\//portal.azure.us/ 
- Office 365: https:\//portal.office365.us/ 
- Portale aziendale di Intune: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Endpoint dei servizi partner da cui dipende Intune:
- Servizio AAD Sync: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Servizio token di sicurezza Evo: https:\//login.microsoftonline.us
- Proxy di directory: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https:\//directory.microsoftazure.us and https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Servizi notifica push Windows
Nei dispositivi gestiti da Intune che vengono gestiti tramite Gestione dispositivi mobili (MDM), le azioni dei dispositivi e altre attività immediate richiedono l'uso dei servizi notifica push Windows (WNS). Per altre informazioni, vedere [Configurazioni del proxy e del firewall aziendale per supportare il traffico WNS](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## <a name="apple-device-network-information"></a>Informazioni di rete dei dispositivi Apple

|**Uso**|**Nome host (indirizzo IP/subnet)**|**Protocollo**|**Porta**|
|------------|-----------|------------|-----------|
|Recupero e visualizzazione di contenuto dai server Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|Comunicazioni con i server APNS|#-courier.push.apple.com<br>'#' è un numero casuale compreso tra 0 e 50.|TCP|5223 e 443|
|Varie funzionalità tra cui l'acceso a Internet, iTunes Store, App Store macOS, iCloud, messaggistica e così via.|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 o 443|

Per altre informazioni, vedere:

- [Porte TCP e UDP usate dai prodotti software Apple](https://support.apple.com/HT202944)
- [Informazioni sui processi in background e le connessioni host ai server macOS, iOS e iTunes](https://support.apple.com/HT201999)
- [Se i tuoi client macOS e iOS non ricevono le notifiche push di Apple](https://support.apple.com/HT203609)

## <a name="next-steps"></a>Passaggi successivi
[Endpoint di rete per Microsoft Intune](intune-endpoints.md)

[Registrazione automatica di Windows 10 e registrazione dei dispositivi](../enrollment/windows-enroll.md#registration-and-enrollment-cnames)