---
title: Introduzione a Intune
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ef58e46118a0a44609abba5de4986b5a1526a151
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2017
---
# <a name="what-is-microsoft-intune"></a>Informazioni su Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Microsoft Intune nel portale di Azure](./media/generic-intune-azure.png)

Microsoft Intune è uno dei servizi più nuovi di Azure. Offre strumenti per la gestione dei dispositivi mobili aziendali, dei PC e delle app [aggiornati regolarmente](whats-new.md). Oltre alla console moderna di Azure, Intune consente anche di usare la console classica. La console classica è la prima versione di Intune da dove è ancora possibile [gestire i PC Windows con il software client di Intune](/intune-classic/deploy-use/pc-management-comparison.md). Il portale classico, compilato in Silverlight, viene usato per un numero limitato di attività. Tutto il resto, inclusa la gestione dei dispositivi mobili e delle app, viene eseguito nel portale di Azure. La Guida introduttiva illustra le attività di base da eseguire per poter usare correttamente Intune nel portale di Azure.

![Pannello della guida e del supporto tecnico, disponibile nella parte inferiore dell'elenco delle azioni nella barra laterale sinistra di Intune.](./media/intune-azure-help-support-closeup.png)

## <a name="what-does-intune-in-the-azure-portal-provide"></a>Vantaggi di Intune nel portale di Azure

Intune nel portale di Azure offre i seguenti vantaggi:

* Una console integrata per tutti i [componenti di Enterprise Mobility + Security (EMS)](https://docs.microsoft.com/enterprise-mobility-security)
* Una console HTML creata su standard Web che supporta i [Web browser moderni](supported-devices-browsers.md)
* [Gruppi di Azure Active Directory](groups-get-started.md) per offrire compatibilità a tutte le applicazioni Azure
* Automazione tramite l'[API Microsoft Graph](intune-graph-apis.md)

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, è necessario avere un account amministratore e un tenant per Intune attivato. È possibile iscriversi [qui](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) per tali account. I sottoscrittori correnti possono anche completare queste attività nel tenant live. Assicurarsi di usare solo dispositivi di test.

Per poter completare tutte le attività della guida, è anche necessario essere amministratore globale dell'organizzazione.
