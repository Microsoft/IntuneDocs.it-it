---
title: Dispositivi supportati in Microsoft Intune
description: Questo articolo elenca le piattaforme di dispositivi e i browser supportati per la gestione dei dispositivi in Intune.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: df9c4c0a0a23740bf9df4c13e34b8752838aa99a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="supported-devices-and-browsers"></a>Dispositivi e browser supportati

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Questo articolo è rivolto agli amministratori di sistema responsabili della gestione dei dispositivi nell'organizzazione. Per informazioni sull'installazione di Intune sul telefono, vedere [Uso di dispositivi gestiti per lo svolgimento del lavoro](/intune-user-help/company-portal-frequently-asked-questions).

Prima di iniziare la configurazione di Microsoft Intune, esaminare i requisiti seguenti:

- [Dispositivi e computer supportati](#intune-supported-devices)
- [Elenco di Web browser supportati che usano Intune](#intune-supported-web-browsers)

È anche consigliabile acquisire familiarità con l'[uso della larghezza di banda di rete in Intune](network-bandwidth-use.md) ([console classica](/intune-classic/get-started/network-bandwidth-use)).

## <a name="intune-supported-devices"></a>Dispositivi supportati da Intune

È possibile gestire i dispositivi seguenti con Gestione dei dispositivi mobili di Intune:

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

Intune non può essere usato per gestire sistemi operativi Windows Server.

### <a name="windows-pc-software-client"></a>Client software PC Windows

Un [client software Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) può essere distribuito e installato nei PC di Windows come metodo alternativo di registrazione. Questa funzionalità è disponibile solo nella console classica di Intune. È possibile usare il client software di Intune per gestire PC con Windows 7 e versioni successive, ad eccezione dell'edizione Windows 10 Home.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Web browser supportati da Intune

Per le svariate attività amministrative è necessario usare uno dei siti Web di amministrazione seguenti.

- [Portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Portale di Intune](https://portal.azure.com/)

Per questi portali sono supportati i browser seguenti:
- Microsoft Edge (versione più recente)
- Microsoft Internet Explorer 11
- Safari (versione più recente, solo Mac)
- Chrome (versione più recente)
- Firefox (versione più recente)

### <a name="intune-classic-portal"></a>Portale classico di Intune

Le funzionalità esclusivamente classiche di Intune, come il client software per PC di Intune e l'integrazione con i partner Mobile Threat Defense sono disponibili solo nel portale classico di Intune (https://manage.microsoft.com). Per la console classica di Intune è richiesto il supporto di un browser Silverlight.

La console classica di Intune è supportata dai browser Silverlight seguenti:
- Internet Explorer 10 o versione successiva
- Google Chrome (versioni precedenti alla versione 42)
- Mozilla Firefox con Silverlight abilitato [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> Microsoft Edge e i browser per dispositivi mobili non sono supportati per la console classica di Intune perché non supportano [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).


Solo gli utenti con autorizzazioni di amministratore del servizio o di amministratore tenant con il ruolo Amministratore globale possono accedere al portale. Per accedere alla console di amministrazione, è necessario che l'account abbia una licenza per l'uso di Intune e lo stato di accesso **Consentito**.
