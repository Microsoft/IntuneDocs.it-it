---
title: Introduzione a Intune nel portale di anteprima di Azure
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: nozioni di base su Intune nel portale di anteprima di Azure e informazioni su come questo strumento aiuta nella gestione dei dispositivi.'
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 04/24/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 16d7ff50eb821e0927c3c6ea21f3cdb1257762a0
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---


# <a name="introduction-to-microsoft-intune-in-the-azure-portal-preview"></a>Introduzione a Microsoft Intune nel portale di anteprima di Azure


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Microsoft Intune sta migrando nel portale di Azure e ciò significa che i flussi di lavoro e le funzionalità conosciute dall'utente subiranno delle modifiche.
Il nuovo design offre un'anteprima delle funzionalità nuove e aggiornate nel portale di Azure, in cui è possibile gestire dispositivi mobili, PC e app dell'organizzazione.
Alla fine, tutte le funzionalità di Intune verranno migrate in Azure, ma è già possibile eseguire molte attività di Intune nel portale di Azure. Dal momento che questa nuova esperienza è disponibile in anteprima, alcune funzionalità potrebbero non essere ancora presenti nel portale. Per informazioni dettagliate, rivedere la sezione [Novità](#whats-new).

> [!IMPORTANT]
> **Non è ancora possibile visualizzare il nuovo portale?**<br>
> Abbiamo già iniziato a lanciare l'anteprima in alcuni tenant. I tenant esistenti verranno migrati alla nuova esperienza a partire dai primi periodi del 2017. L'utente riceverà una notifica nel centro messaggi di Office prima della migrazione del tenant.
>
> Gli account di Intune creati prima di gennaio 2017 richiederanno un'unica migrazione prima che i flussi di lavoro Registrazione Apple siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.


La documentazione sul nuovo prodotto sarà disponibile in questa libreria e verrà aggiornata continuamente durante l'anteprima. Se hai suggerimenti, inviaci un feedback tramite i commenti dell'argomento. Saremmo lieti di ricevere la tua opinione.

<!--- You can view the new Intune technical preview console in Azure at [portal.azure.com]. --->

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
Questa sezione contiene informazioni su [novità](whats-new.md), [problemi noti](known-issues.md), [come ottenere supporto](get-support.md) e come [iniziare a usare una versione di valutazione gratuita](free-trial-sign-up.md) di Intune.
### <a name="plan-and-design"></a>Pianificare e progettare
Informazioni utili per [pianificare e progettare](/intune-classic/plan-and-design/introduction) l'ambiente di Intune.
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
[Informazioni sugli utenti dei dispositivi gestiti e su come ordinare le risorse in gruppi](user-management.md).
### <a name="groups"></a>Gruppi
[Informazioni su come usare i gruppi di Azure Active Directory con Intune](groups-get-started.md)
### <a name="intune-roles"></a>Ruoli di Intune
[Definire gli utenti che possono eseguire determinate azioni di Intune e gli utenti ai quali si applicano tali azioni](role-based-access-control.md). È possibile usare i ruoli predefiniti che coprono alcuni scenari comuni in Intune oppure creare ruoli personalizzati.
### <a name="software-updates"></a>Aggiornamenti software
[Informazioni su come configurare gli aggiornamenti software per i dispositivi Windows 10](windows-update-for-business-configure.md).



## <a name="whats-new"></a>Quali sono le novità?

[Scopri le novità nella versione di anteprima](whats-new.md).
