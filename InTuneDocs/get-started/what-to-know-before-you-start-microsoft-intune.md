---
title: Dispositivi supportati in Microsoft Intune | Documentazione Microsoft
description: Questo articolo elenca le piattaforme di dispositivi e i browser supportati per la gestione dei dispositivi in Intune.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 0fa045d31125ba0d67f19bb46aa2728ae9bbcc93
ms.lasthandoff: 04/14/2017


---

# <a name="supported-devices-and-browsers"></a>Dispositivi e browser supportati

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo articolo è rivolto agli amministratori di sistema responsabili della gestione dei dispositivi nell'organizzazione. Per informazioni sull'installazione di Intune sul telefono, vedere [Uso di dispositivi gestiti per lo svolgimento del lavoro](https://docs.microsoft.com/intune/enduser/company-portal-frequently-asked-questions).

Prima di iniziare la configurazione di Microsoft Intune, esaminare i requisiti seguenti:

- [Dispositivi e computer supportati](#intune-supported-devices)
- [Elenco di Web browser supportati che usano Intune](#intune-supported-web-browsers)

È anche consigliabile acquisire familiarità con l'[utilizzo della larghezza di banda di rete in Intune](network-bandwidth-use.md).

## <a name="intune-supported-devices"></a>Dispositivi supportati da Intune

È possibile gestire i dispositivi seguenti con Gestione dei dispositivi mobili di Intune:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Intune non può essere usato per gestire sistemi operativi Windows Server.

La gestione dei dispositivi Intune offre le [funzionalità descritte di seguito](mobile-device-management-capabilities-in-microsoft-intune.md).

### <a name="windows-pc-software-client"></a>Client software PC Windows

Un [client software Intune](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune) può essere distribuito e installato nei PC di Windows come metodo alternativo di registrazione. È possibile usare il client software di Intune per gestire PC con Windows 7 e versioni successive, ad eccezione dell'edizione Windows 10 Home. La gestione dei PC con il software client offre [queste funzionalità](windows-pc-management-capabilities-in-microsoft-intune.md).

### <a name="exchange-activesync-management"></a>Gestione di Exchange ActiveSync

È possibile gestire [dispositivi Exchange ActiveSync](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) dalla console di Intune. Questa opzione fornisce un set limitato di funzionalità di gestione rispetto agli altri metodi. Per un elenco dei dispositivi supportati vedere [Funzionalità del servizio incorporato Gestione di dispositivi mobili in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0).

## <a name="intune-supported-web-browsers"></a>Web browser supportati da Intune

Per le svariate attività amministrative è necessario usare uno dei siti Web di amministrazione seguenti.

- [Portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Console di amministrazione di Microsoft Intune](https://admin.manage.microsoft.com/)

|Funzionalità di Intune |Browser supportati|
|---------|---------|
|**Console di amministrazione di Intune**     |  Internet Explorer 10 o versione successiva<br /><br />Google Chrome (versioni precedenti alla versione 42)<br /><br />Mozilla Firefox con Silverlight abilitato<br />**Nota:** Mozilla rimuoverà il supporto per Silverlight a partire da marzo 2017. [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=836872). |
|**Portale di amministrazione di Office 365**     |Tutti i browser, inclusi i browser per dispositivi mobili e i browser gestiti  |
|**Sito Web del portale aziendale**     |**Nei dispositivi mobili:** usare il Web browser predefinito per ogni piattaforma supportata   <br /><br />**Nei PC Windows:** Internet Explorer 10 o versione successiva oppure Microsoft Edge<br /><br />**In Mac OS X 10.9 o versioni successive:** Apple Safari    |

> [!Note]
> Microsoft Edge e i browser per dispositivi mobili non sono supportati per la console di amministrazione perché non supportano [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx). La console di Intune entro un certo periodo lascerà l'esperienza Silverlight. Infine, tutte le funzionalità di gestione delle applicazioni e dei dispositivi mobili di Intune saranno [disponibili nel nuovo portale di Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).


Solo gli utenti con autorizzazioni di amministratore del servizio o di amministratore tenant con il ruolo Amministratore globale possono accedere al portale. Per accedere alla console di amministrazione, è necessario che l'account abbia una licenza per l'uso di Intune e lo stato di accesso **Consentito**.

>[!div class="step-by-step"]

>[**Funzionalità di rete** &rarr;](network-bandwidth-use.md)  

