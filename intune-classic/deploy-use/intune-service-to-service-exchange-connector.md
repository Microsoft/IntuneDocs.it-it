---
title: Exchange Connector per Exchange Online | Documentazione Microsoft
description: Connettere Intune al servizio di Office 365 Exchange per supportare la gestione di dispositivi mobili (MDM) di Exchange ActiveSync.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4b73767f585cfa6283c7fb0601e7061efe42c606
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="configure-the-intune-service-to-service-connector-for-exchange-online"></a>Configurare Intune Service to Service Connector per Exchange Online

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare queste informazioni per connettere Microsoft Intune ed Exchange Online oppure il nuovo servizio Exchange Online dedicato. Per determinare se la configurazione dell'ambiente Exchange Online dedicato è la versione **nuova** o **legacy**, contattare l'account manager. Intune supporta solo una connessione con Exchange Connector di qualsiasi tipo per ogni sottoscrizione.

## <a name="service-to-service-connector-requirements"></a>Requisiti per Service to Service Connector
**Service to Service Connector** supporta solo Exchange Online o l'ambiente Exchange Online dedicato e non presenta requisiti per l'infrastruttura locale.

|Requisito|Altre informazioni|
|---------------|--------------------|
|Exchange Online configurato e in esecuzione|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Autorità di gestione dei dispositivi mobili| [Impostare l'autorità di gestione dei dispositivi mobili su Microsoft Intune](prerequisites-for-enrollment.md#step-2-set-mdm-authority)|
|Versione di Microsoft Exchange|Exchange Online o il nuovo servizio Exchange Online dedicato|
|Sincronizzazione di Active Directory|Prima di poter usare Intune Connector è necessario [configurare la sincronizzazione di Active Directory](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3), in modo che gli utenti e i gruppi di sicurezza locali siano sincronizzati con l'istanza di Azure Active Directory.|

### <a name="exchange-cmdlet-requirements"></a>Requisiti dei cmdlet di Exchange

È anche necessario creare un account utente di Exchange Online, che viene usato da Intune Exchange Connector. L'account deve avere autorizzazioni per l'uso della console di amministrazione di Intune e per l'esecuzione dei seguenti cmdlet Exchange di Windows PowerShell obbligatori:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Configurare Service to Service Connector

1. Aprire la [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) con un account utente provvisto di diritti di amministratore di Exchange e autorizzazioni per i cmdlet [elencati in precedenza](#exchange-cmdlet-requirements). Microsoft Intune usa l'indirizzo di posta elettronica dell'utente attualmente connesso per configurare la connessione.

2.  Nel riquadro dei collegamenti alle aree di lavoro scegliere **AMMINISTRAZIONE**>**Gestione dei dispositivi mobili** > **Microsoft Exchange** > **Configura connessione Exchange**.
![Configurare la pagina Service to Service Connector](../media/intunesa5cservicetoserviceconnector.png)

3.  Nella pagina **Configura connessione Exchange** scegliere **Configura Service to Service Connector**.


Service to Service Connector viene configurato automaticamente e sincronizzato con Exchange Online o con il nuovo ambiente Exchange Online dedicato.

## <a name="validate-your-exchange-connection"></a>Convalidare la connessione a Exchange

Dopo aver configurato correttamente Exchange Connector, accedere alla [console di amministrazione di Microsoft Intune](https://manage.microsoft.com). Scegliere **Amministrazione**> **Gestione dei dispositivi mobili** > **Microsoft Exchange**. Verificare che i dettagli specificati appaiano in **Informazioni sulla connessione Exchange**.

È inoltre possibile verificare la data e ora dell'ultimo tentativo di sincronizzazione riuscito.

