---
title: Exchange Connector per Exchange ospitato | Microsoft Intune
description: Connettere Intune al servizio di Office 365 Exchange per supportare la gestione di dispositivi mobili (MDM) di Exchange ActiveSync.
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1e0d05a4f229e2a8e72d1d60021b159f12dfa0d1
ms.openlocfilehash: 63697222f024169d9450b9f4fea8c666353e72cc


---

# Configurare Intune Service to Service Connector per Exchange Online

Usare queste informazioni per connettere Microsoft Intune e il servizio Exchange Online ospitato in Office 365.

## Requisiti per Service to Service Connector
**Service to Service Connector** supporta solo Exchange ospitato e non presenta requisiti per l'infrastruttura locale.

|Requisito|Altre informazioni|
|---------------|--------------------|
|Exchange ospitato configurato e in esecuzione|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Autorità di gestione dei dispositivi mobili| [Impostare l'autorità di gestione dei dispositivi mobili su Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Versione di Microsoft Exchange|È necessario avere una sottoscrizione a Office 365 con un tenant Exchange Server 2013 o successivo. Se il tenant è Exchange Server 2013 o successivo, il connettore supporta Exchange Server 2010 nello stesso ambiente.|
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


Service to Service Connector viene configurato e sincronizzato automaticamente con l'ambiente Exchange ospitato.

## Convalidare la connessione a Exchange

Dopo aver configurato Exchange Connector, nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) scegliere **Amministrazione** e passare a **Gestione dei dispositivi mobili** > **Microsoft Exchange** e verificare che i dettagli specificati siano visualizzati in **Informazioni sulla connessione Exchange**.

È inoltre possibile verificare la data e ora dell'ultimo tentativo di sincronizzazione riuscito.



<!--HONumber=Jul16_HO3-->


