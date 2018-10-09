---
title: Intune Exchange Connector per Exchange Online
titleSuffix: ''
description: Connettere Intune al servizio di Office 365 Exchange per supportare la gestione di dispositivi mobili (MDM) di Exchange ActiveSync.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6be3694a18cd0df09b52b535a0fcd2050bf7a98
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231245"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Configurare il connettore del servizio Exchange per Intune ed Exchange Online

Questo articolo illustra come connettere il servizio Microsoft Intune a Exchange Online oppure al nuovo servizio Exchange Online dedicato. Per determinare se la configurazione dell'ambiente Exchange Online dedicato è la versione **nuova** o **legacy**, contattare l'account manager.

## <a name="service-to-service-connector-requirements"></a>Requisiti per Service to Service Connector
**Service to Service Connector** supporta solo Exchange Online o l'ambiente Exchange Online dedicato e non presenta requisiti per un'infrastruttura locale.


|              Requisito               |                                                                                                            Altre informazioni                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange Online configurato e in esecuzione |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   Autorità di gestione dei dispositivi mobili   |                                                       [Impostare l'autorità di gestione dei dispositivi mobili su Microsoft Intune](mdm-authority-set.md)                                                       |
|       Versione di Microsoft Exchange       |                                                                                      Exchange Online o il nuovo servizio Exchange Online dedicato                                                                                      |
|    Sincronizzazione di Active Directory    | Prima di poter usare Intune Connector è necessario [configurare la sincronizzazione di Active Directory](/intune/users-add), in modo che gli utenti e i gruppi di sicurezza locali siano sincronizzati con l'istanza di Azure Active Directory. |

### <a name="exchange-cmdlet-requirements"></a>Requisiti dei cmdlet di Exchange

È anche necessario creare un account utente di Exchange Online, che viene usato dal connettore del servizio Intune Exchange. L'account deve avere le autorizzazioni per eseguire i cmdlet Exchange di Windows PowerShell richiesti elencati di seguito.

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Configurare Service to Service Connector

1. Accedere al [portale di Azure](http://portal.azure.com) con un account utente provvisto di diritti di amministratore di Exchange, autorizzazioni per i cmdlet [elencati in precedenza](#exchange-cmdlet-requirements), una licenza di Intune valida e un ruolo Amministratore globale. Microsoft Intune usa l'indirizzo di posta elettronica dell'utente attualmente connesso per configurare la connessione.

2. Scegliere **Tutti i servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune** per aprire il dashboard di Microsoft Intune. Scegliere **Accesso condizionale** e quindi in **Installazione** scegliere **Connettore del servizio Exchange**.

4.  Nella pagina **Accesso condizionale - Connettore del servizio Exchange** scegliere **Configura Service to Service Connector**. 
   
     ![Immagine che mostra la selezione del collegamento Configura Service to Service Connector](media/exchange_service_connector.png)

Service to Service Connector viene configurato automaticamente e sincronizzato con Exchange Online o con il nuovo ambiente Exchange Online dedicato.

## <a name="validate-your-exchange-connection"></a>Convalidare la connessione a Exchange

Dopo avere correttamente configurato il connettore da servizio a servizio per Exchange, convalidare le informazioni del server di Exchange Connector nella pagina **Accesso condizionale - Connettore del servizio Exchange**.

È anche possibile verificare lo **stato della connessione** e la data e ora dell'ultimo tentativo di sincronizzazione riuscito.

## <a name="next-steps"></a>Passaggi successivi
[Monitorare l'accesso condizionale per Exchange in Microsoft Intune](conditional-access-exchange-monitor.md)