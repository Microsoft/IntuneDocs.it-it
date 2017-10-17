---
title: Gestione dei dispositivi con Exchange ActiveSync
description: Gestire i dispositivi mobili con la gestione di Exchange ActiveSync (EAS) usando Exchange Connector
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 02d6220a4c780eafb7afb01208e18e7df7684b68
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="exchange-activesync-mobile-device-management-with-microsoft-intune"></a>Gestione dei dispositivi mobili con Exchange ActiveSync e Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per la gestione diretta dei dispositivi mobili con Microsoft Intune, i dispositivi devono essere [registrati in Intune](prerequisites-for-enrollment.md). In alternativa, gli amministratori possono abilitare una soluzione di gestione più limitata che usa la gestione di Exchange ActiveSync (EAS) con Exchange Connector. È possibile gestire i dispositivi con server Exchange locali o con Exchange Online usando Office 365. Per ogni sottoscrizione Intune supporta una sola connessione con Exchange Connector di qualsiasi tipo.

## <a name="exchange-access-rules-for-mobile-devices"></a>Regole di accesso a Exchange per dispositivi mobili ##

Exchange richiede un set di regole che definisce ciò che accade quando i dispositivi mobili tentano di connettersi a EAS. Queste regole vengono gestite nella console di amministrazione di Intune.

[Regole di accesso a Exchange per dispositivi mobili](exchange-access-rules-for-mobile-devices.md)

## <a name="install-the-exchange-connector"></a>Installare Exchange Connector
Exchange Connector consente di gestire la distribuzione di Exchange nella console di Intune. Prima è necessario installare e configurare il connettore tra Intune ed Exchange appropriato. Scegliere l'opzione appropriata a seconda che il server Exchange sia locale o ospitato come servizio nel cloud:

-   [Configurare Intune per Exchange Online o i nuovi ambienti Exchange Online dedicati](intune-service-to-service-exchange-connector.md)
-   [Installare Intune Connector per i server Exchange locali e gli ambienti legacy Exchange Online dedicati](intune-on-premises-exchange-connector.md)


## <a name="apply-policy-for-exchange-managed-mobile-devices"></a>Applicare i criteri per i dispositivi mobili gestiti da Exchange
La console di Intune può essere usata per gestire [le impostazioni dei criteri EAS](exchange-activesync-policy-settings-in-microsoft-intune.md) e [limitare l'accesso alle risorse aziendali](restrict-access-to-email-and-o365-services-with-microsoft-intune.md). Per l'elenco delle impostazioni di criteri e delle funzionalità di Exchange ActiveSync supportate da dispositivi mobili specifici, vedere [Exchange ActiveSync Client Comparison Table](http://go.microsoft.com/fwlink/?LinkId=247270) (Tabella di confronto dei client di Exchange ActiveSync).

> [!NOTE]
> Dopo aver connesso Intune a un ambiente Microsoft Exchange, i criteri EAS per tutti gli utenti gestiti mediante Intune verranno reimpostati ai criteri predefiniti correnti nel server Microsoft Exchange, salvo se in Intune sono definiti criteri più specifici.

## <a name="wipe-company-data-from-mobile-devices"></a>Cancellare i dati aziendali dai dispositivi mobili
Infine è possibile [cancellare i dati aziendali da dispositivi mobili gestiti da EAS](wipe-for-exchange-managed-mobile-devices.md) quando i dispositivi non sono più in uso o in caso di smarrimento o furto.
