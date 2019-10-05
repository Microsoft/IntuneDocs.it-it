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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 490c939e79659baac655cfd7d3d3a2ee10d98382
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726050"
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