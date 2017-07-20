---
title: Introduzione a Intune nel portale di Azure
titleSuffix: Intune on Azure
description: Nozioni di base su Intune nel portale di Azure e informazioni su come questo strumento aiuta nella gestione dei dispositivi."
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 06/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae42ab64945982fedc2d6858e2f3eca8fbed334c
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2017
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Introduzione a Microsoft Intune nel portale di Azure


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune ora è disponibile nel portale di Azure e ciò significa che i flussi di lavoro e le funzionalità conosciute dall'utente sono cambiati.
Il nuovo design offre funzionalità nuove e aggiornate nel portale di Azure, in cui è possibile gestire dispositivi mobili, PC e app dell'organizzazione.

> [!IMPORTANT]
> **Non è ancora possibile visualizzare il nuovo portale?**<br>
> È in corso la migrazione dei tenant esistenti alla nuova esperienza. Prima di eseguire la migrazione del tenant, viene visualizzata una notifica nel Centro messaggi di Office.
>
> Gli account di Intune creati prima di gennaio 2017 richiedono un'unica migrazione prima che i flussi di lavoro Registrazione Apple siano disponibili in Azure. La pianificazione per la migrazione non è ancora stata annunciata. Se l'account esistente non può accedere al portale di Azure, è consigliabile creare un account di prova.
>
> Rivedere l'elenco dei blocchi potenziali https://blogs.technet.microsoft.com/intunesupport/2017/05/17/intune-migration-blockers-for-grouping-targeting/


È possibile trovare informazioni sul nuovo portale in questa raccolta, che viene continuamente aggiornata. Per eventuali suggerimenti, inviare feedback tramite i commenti dell'argomento. Saremmo lieti di ricevere la tua opinione.

Le caratteristiche della nuova esperienza includono:

- Una console integrata per tutti i componenti Enterprise Mobility + Security (EMS)
- Una console basata su HTML compilata su standard Web
- Supporto dell'API Graph di Microsoft per automatizzare molte azioni
- Gruppi di Azure Active Directory (AD) per garantire compatibilità su tutte le applicazioni Azure
- Supporto per i browser Web più recenti

Per la documentazione relativa alla console di Intune classica, vedere la [libreria della documentazione di Intune](https://docs.microsoft.com/intune-classic/).

## <a name="before-you-start"></a>Prima di iniziare

Per usare Intune nel portale di Azure, è necessario disporre di un account amministrazione e Intune e di un account tenant. Se non di dispone di un account, [iscriversi per crearne uno](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

## <a name="supported-web-browsers-for-the-azure-portal"></a>Web browser supportati per il portale di Azure

Il portale di Azure può essere eseguito sui più moderni PC, Mac e tablet. I telefoni cellulari non sono supportati.
Attualmente sono supportati i browser seguenti:

- Microsoft Edge (versione più recente)
- Microsoft Internet Explorer 11
- Safari (versione più recente, solo Mac)
- Chrome (versione più recente)
- Firefox (versione più recente)

Per informazioni aggiornate sui browser supportati, vedere il [portale di Azure](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices).

## <a name="whats-in-this-library"></a>Contenuto della libreria

La documentazione riflette il layout del portale di Intune per rendere più semplice trovare le informazioni necessarie.

![Carichi di lavoro del portale di Azure](./media/azure-portal-workloads.png)

### <a name="introduction-and-get-started"></a>Introduzione e operazioni preliminari
Questa sezione contiene [informazioni introduttive](introduction-intune.md) per l'uso di Intune.
### <a name="plan-and-design"></a>Pianificare e progettare
Informazioni utili per [pianificare e progettare](/intune-classic/plan-design/introduction) l'ambiente di Intune.
### <a name="device-enrollment"></a>Registrazione del dispositivo
[Come impostare la gestione dei dispositivi da Intune](device-enrollment.md).
### <a name="device-compliance"></a>Conformità del dispositivo
[Definire un livello di conformità per i dispositivi e segnalare i dispositivi non conformi](device-compliance.md).
### <a name="device-configuration"></a>Configurazione del dispositivo
[Informazioni sui profili per la configurazione di impostazioni e funzionalità nei dispositivi gestiti](device-profiles.md).
### <a name="devices"></a>Dispositivi
[Conoscere i dispositivi gestiti con l'inventario e i report](device-management.md).
### <a name="mobile-apps"></a>App per dispositivi mobili
[Come pubblicare, gestire, configurare e proteggere le app](app-management.md).
### <a name="conditional-access"></a>Accesso condizionale
[Limitare l'accesso ai servizi Exchange in base alle condizioni specificate](conditional-access.md).
### <a name="on-premises-access"></a>Accesso in locale
[Configurare l'accesso a Exchange ActiveSync ed Exchange locale](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Users
[Informazioni sugli utenti dei dispositivi gestiti e su come ordinare le risorse in gruppi](users-add.md).
### <a name="groups"></a>Gruppi
[Informazioni su come usare i gruppi di Azure Active Directory con Intune](groups-get-started.md)
### <a name="intune-roles"></a>Ruoli di Intune
[Definire gli utenti che possono eseguire determinate azioni di Intune e gli utenti ai quali si applicano tali azioni](role-based-access-control.md). È possibile usare i ruoli predefiniti che coprono alcuni scenari comuni in Intune oppure creare ruoli personalizzati.
### <a name="software-updates"></a>Aggiornamenti software
[Informazioni su come configurare gli aggiornamenti software per i dispositivi Windows 10](windows-update-for-business-configure.md).



## <a name="whats-new"></a>Quali sono le novità?

[Novità di Intune](whats-new.md).
