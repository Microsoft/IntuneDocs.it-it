---
title: Exchange Connector per Exchange Online | Microsoft Intune
description: Connettere Intune al servizio di Office 365 Exchange per supportare la gestione di dispositivi mobili (MDM) di Exchange ActiveSync.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: de3296e81c88b3ac04e3ba3f3d3ca222a59df7bd
ms.openlocfilehash: 1aabf820170483eacc83bec5e2b275e84dc07ffd


---

# Configurare Intune Service to Service Connector per Exchange Online

Usare queste informazioni per connettere Microsoft Intune ed Exchange Online oppure il nuovo servizio Exchange Online dedicato. Per determinare se la configurazione dell'ambiente Exchange Online dedicato è **nuova** o **legacy**, contattare l'account manager. Intune supporta solo una connessione con Exchange Connector di qualsiasi tipo per ogni sottoscrizione.

## Requisiti per Service to Service Connector
**Service to Service Connector** supporta solo Exchange Online o il nuovo ambiente Exchange Online dedicato e non presenta requisiti per l'infrastruttura locale.

|Requisito|Altre informazioni|
|---------------|--------------------|
|Exchange Online configurato e in esecuzione|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Autorità di gestione dei dispositivi mobili| [Impostare l'autorità di gestione dei dispositivi mobili su Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Versione di Microsoft Exchange|Exchange Online o il nuovo servizio Exchange Online dedicato|
|Configurare la sincronizzazione di Active Directory|Prima di poter usare Intune Connector è necessario [configurare la sincronizzazione di Active Directory](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3), in modo che gli utenti e i gruppi di sicurezza locali siano sincronizzati con l'istanza di Azure Active Directory.|

### Requisiti dei cmdlet di Exchange

È anche necessario creare un account utente di Exchange Online, che viene usato da Intune Exchange Connector. L'account deve avere autorizzazioni per l'uso della console di amministrazione di Intune e per l'esecuzione dei cmdlet Exchange di Windows PowerShell obbligatori elencati di seguito.

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## Configurare Service to Service Connector

1. Aprire la [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) con un account utente con diritti di amministratore di Exchange e autorizzazioni per i cmdlet [sopra elencati](#exchange-cmdlet-requirements). Microsoft Intune usa l'indirizzo di posta elettronica dell'utente attualmente connesso per configurare la connessione.

2.  Nel riquadro dei collegamenti alle aree di lavoro scegliere **AMMINISTRAZIONE**, quindi scegliere **Gestione dei dispositivi mobili** > **Microsoft Exchange** > **Configura connessione Exchange**.
![Configurare la pagina Service to Service Connector](../media/intunesa5cservicetoserviceconnector.png)

3.  Nella pagina **Configura connessione Exchange** scegliere **Configura Service to Service Connector**.


Service to Service Connector viene configurato e sincronizzato automaticamente con Exchange Online o il nuovo ambiente Exchange Online dedicato.

## Convalidare la connessione a Exchange

Dopo aver configurato Exchange Connector, nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) scegliere **Amministrazione** e passare a **Gestione dei dispositivi mobili** > **Microsoft Exchange** e verificare che i dettagli specificati siano visualizzati in **Informazioni sulla connessione Exchange**.

È inoltre possibile verificare la data e ora dell'ultimo tentativo di sincronizzazione riuscito.



<!--HONumber=Jul16_HO5-->


