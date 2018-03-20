---
title: Exchange senza gestione dei dispositivi
titleSuffix: Microsoft Intune
description: Usare Microsoft Intune per concedere ai dipendenti l'accesso alla posta elettronica Office 365 Exchange Online senza configurare un sistema di gestione dei dispositivi.
keywords: Accesso alla posta elettronica di Office 365 Exchange
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 10/31/2017
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88a0d3b9-2622-403b-8374-1396afd8066e
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e677a8418aba9aca4db753695444140ea9f6f941
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="protect-office-365-exchange-online-without-requiring-device-management"></a>Proteggere Office 365 Exchange Online senza richiedere la gestione dei dispositivi

Se si vuole, è possibile concedere ai dipendenti l'accesso alla posta elettronica aziendale senza dover configurare un sistema di gestione dei dispositivi. È possibile concedere l'accesso a Office 365 Exchange Online tramite Intune. Per completare la procedura necessaria, confermare di avere licenze per Microsoft 365 o Azure Active Directory (Premium) e Intune. I dipendenti devono avere un [dispositivo iOS o Android supportato](supported-devices-browsers.md). 

Se si decide di configurare un sistema di gestione dei dispositivi, è possibile farlo. Questo tipo di protezione delle app è indipendente dalla gestione dei dispositivi. 

## <a name="action-plan"></a>Piano di azione

1. [Ottenere informazioni sull'accesso condizionale](conditional-access.md). 
2. [Ottenere informazioni sull'accesso condizionale basato su app](app-based-conditional-access-intune.md).
3. [Configurare criteri di accesso condizionale basato su app per Exchange Online](app-based-conditional-access-intune-create.md).
4. [Bloccare le app che non possono essere gestite](app-modern-authentication-block.md), in particolare le app che non usano Azure Active Directory Authentication Library (ADAL).
5. (Facoltativo) [Configurare criteri di accesso condizionale basato su app per SharePoint Online](app-based-conditional-access-intune-create.md). Questi criteri impediscono l'accesso ai dati aziendali da app che non possono essere gestite e protette. I criteri limitano anche l'accesso tramite SharePoint Mobile. 

## <a name="what-to-tell-employees-and-students"></a>Informazioni da comunicare a dipendenti e studenti

* È necessario richiedere ai dipendenti e agli studenti di scaricare e installare Microsoft Outlook o Microsoft SharePoint per iOS dall'App Store di Apple o per Android da Google Play Store. 
* Se si impedisce l'accesso alle app che non usano l'autenticazione moderna, è necessario segnalare tale limitazione a dipendenti e studenti. 

## <a name="next-steps"></a>Passaggi successivi

È stato usato l'accesso condizionale per incrementare la sicurezza dei dati aziendali. Come parte delle procedure successive, è possibile ottenere informazioni su altre strategie per incrementare la protezione dei dati aziendali, ad esempio: 

* Configurazione dell'[accesso condizionale basato sulla conformità dei dispositivi, sul rischio dei dispositivi, sulla posizione e sugli attributi utente in Active Directory e Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).  
* Configurazione dei criteri di protezione delle app per semplificare la protezione dei dati aziendali da perdite di dati intenzionali o accidentali. 
* Sfruttamento delle funzionalità di Azure Information Protection per proteggere i dati aziendali all'esterno della rete aziendale. 

Se si vuole ottenere assistenza per l'abilitazione di questi scenari o di altri scenari per EMS oppure Office 365 e sono disponibili almeno 150 licenze per Microsoft 365, Enterprise Mobility + Security o Azure Active Directory Premium, usare i propri [vantaggi FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 