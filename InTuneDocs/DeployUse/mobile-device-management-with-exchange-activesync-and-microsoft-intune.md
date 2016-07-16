---
title: Gestione dei dispositivi mobili con Exchange ActiveSync e Microsoft Intune | Microsoft Intune
description: 
keywords: 
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: d24395786daa7aec103ec754895868a75983e099


---

# Gestione dei dispositivi mobili con Exchange ActiveSync e Microsoft Intune
Per la gestione diretta dei dispositivi mobili con Microsoft Intune, gli utenti devono registrare i dispositivi in Intune. Per i dispositivi mobili che gli utenti non hanno registrato, è possibile abilitare la gestione Exchange ActiveSync (EAS) usando Exchange Connector. È possibile gestire i dispositivi con server Exchange locali o con Exchange ospitato nel cloud in Microsoft Office 365.

## Regole di accesso a Exchange per dispositivi mobili ##

Exchange richiede un set di regole che definisce ciò che accade quando i dispositivi mobili tentano di connettersi a EAS. Queste regole vengono gestite nella console di amministrazione di Intune.

[Regole di accesso a Exchange per dispositivi mobili](exchange-access-rules-for-mobile-devices.md)

## Installare Exchange Connector
Exchange Connector consente di gestire la distribuzione di Exchange nella console di Intune. Prima è necessario installare e configurare il connettore tra Intune ed Exchange appropriato. Scegliere l'opzione appropriata a seconda che il server Exchange sia locale o ospitato come servizio nel cloud:

-   [Installare il connettore Intune per Exchange locale](intune-on-premises-exchange-connector.md)
-   [Configurare il connettore Intune Service to Service per Exchange ospitato](intune-service-to-service-exchange-connector.md)

## Applicare i criteri per i dispositivi mobili gestiti da Exchange
Le impostazioni dei criteri possono essere applicate con la console di Intune. Per informazioni, vedere [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). Per l'elenco delle impostazioni di criteri e delle funzionalità di Exchange ActiveSync supportate da dispositivi mobili specifici, vedere [Exchange ActiveSync Client Comparison Table (Tabella di confronto dei client di Exchange ActiveSync)](http://go.microsoft.com/fwlink/?LinkId=247270).

> [!NOTE]
> Dopo aver connesso Intune a un ambiente Microsoft Exchange, i criteri EAS per tutti gli utenti gestiti mediante Intune verranno reimpostati ai criteri predefiniti correnti nel server Microsoft Exchange, salvo se in Intune sono definiti criteri più specifici.

## Cancellare i dati aziendali dai dispositivi mobili
Infine è possibile [cancellare i dati aziendali da dispositivi mobili gestiti da EAS](wipe-for-exchange-managed-mobile-devices.md) quando i dispositivi non sono più in uso o in caso di smarrimento o furto.



<!--HONumber=Jun16_HO4-->


