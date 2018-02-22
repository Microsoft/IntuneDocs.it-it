---
title: Introduzione a Intune nel portale di Azure
titlesuffix: Azure portal
description: Nozioni di base su Intune nel portale di Azure e informazioni su come questo strumento aiuta nella gestione dei dispositivi."
keywords: 
author: arob98
ms.author: angrobe
nmanager: dougeby
ms.date: 02/14/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: 6e2528c243938e81a6f730a950ee3949ca44047c
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Introduzione a Microsoft Intune nel portale di Azure


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Analogamente ad altri servizi di Azure, Microsoft Intune è disponibile nel portale di Azure. Selezionando **Intune** nel portale di Azure, è possibile gestire i dispositivi mobili, i PC e le app dell'organizzazione.

>[!NOTE] 
> Se è stata usata una versione precedente di Microsoft Intune, le informazioni seguenti possono rivelarsi utili:
    * [Dove si trovano le funzionalità di Intune in Azure?](ui-changes.md) è un riferimento che descrive i flussi di lavoro specifici e le interfacce utente modificati con lo spostamento in Azure.
    * [Gruppi di Intune classici nel portale di Azure](groups-get-started.md) descrive le implicazioni dello spostamento nei gruppi di sicurezza di Azure Active Directory per la gestione dei gruppi.

Tra gli elementi in evidenza dell'esperienza di Microsoft Intune nel portale di Azure sono inclusi i seguenti:

- Una console integrata per tutti i componenti Enterprise Mobility + Security (EMS)
- Una console basata su HTML compilata su standard Web
- Supporto dell'API Graph di Microsoft per automatizzare molte azioni
- Gruppi di Azure Active Directory (AD) per garantire compatibilità su tutte le applicazioni Azure
- Supporto per i browser Web più recenti

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

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune nel portale di Azure

Il [portale di Azure](https://portal.azure.com) è l'area in cui è disponibile il servizio Microsoft Intune. Azure include diversi servizi, molti dei quali possono non essere usati regolarmente. Per una guida rapida per personalizzare l'esperienza del portale, vedere [Guida introduttiva a Intune nel portale di Azure](get-started-azure.md).

## <a name="the-microsoft-intune-documentation"></a>Documentazione di Microsoft Intune

Questo argomento, nonché l'intero set della documentazione di Microsoft Intune, viene aggiornato continuamente. Per eventuali suggerimenti, inviare feedback tramite i commenti dell'argomento. Saremmo lieti di ricevere la tua opinione.

La documentazione riflette il layout di Microsoft Intune nel portale di Azure (mostrato di seguito) per semplificare il reperimento delle informazioni necessarie.

![Carichi di lavoro del portale di Azure](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>Guida alla documentazione

Usare la tabella seguente per trovare e comprendere rapidamente le aree principali di Microsoft Intune.

| Sezione                                                      | Descrizione                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Introduzione e operazioni preliminari](introduction-intune.md)       | Nozioni fondamentali su Intune, tra cui:<br /> - Soluzioni comuni<br /> - Funzionamento di Microsoft Intune<br /> - Gestione dei dispositivi in Intune<br /> - Gestione delle app in Intune<br /> - Gestione della mobilità aziendale con e senza registrazione dei dispositivi                                                         |
| [Pianificazione e progettazione](planning-guide.md)                         | Linee guida per semplificare la pianificazione e la progettazione dell'ambiente Microsoft Intune.                                                                                                                                                                                                             |
| [Registrazione dei dispositivi](device-enrollment.md)                    | Informazioni sul modo in cui Microsoft Intune semplifica la gestione dei dispositivi del personale tramite la registrazione dei dispositivi nel servizio. Esistono diversi metodi per registrare i dispositivi del personale.                                                                                                         |
| [Conformità dei dispositivi](device-compliance.md)                    | I criteri di Intune per la conformità dei dispositivi definiscono le regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme da Microsoft Intune. Ad esempio, la richiesta di una password per l'accesso del dispositivo, la crittografia dei dispositivi e la versione minima del sistema operativo sono tutti esempi di conformità. |
| [Configurazione dei dispositivi](device-profiles.md)                   | Informazioni su come configurare impostazioni e funzionalità in tutti i dispositivi gestiti usando Microsoft Intune tramite la creazione di profili dei dispositivi. Ad esempio, è possibile configurare funzionalità come le notifiche, la condivisione di dati, il supporto per l'e-mail, la connettività Wi-Fi, i certificati e la protezione degli endpoint.              |
| [Dispositivi](device-management.md)                              | Informazioni su come garantire che i dispositivi gestiti forniscano le risorse di cui gli utenti finali hanno bisogno per svolgere il proprio lavoro, proteggendo i dati aziendali dai rischi. È possibile gestire i dispositivi esaminando l'inventario dei dispositivi del personale ed eseguendo azioni sui dispositivi in remoto.                                                      |
| [App per dispositivi mobili](app-management.md)                             | Informazioni su come aggiungere, distribuire, monitorare, configurare e proteggere le app.                                                                                                                                                                                                                             |
| [Accesso condizionale](conditional-access.md)                  | Informazioni su come definire condizioni basate sul dispositivo e sull'app per controllare l'accesso ai dati aziendali.                                                                                                                                                                                                            |
| [Utenti](users-add.md)                                        | Informazioni su come aggiungere utenti delle app e dei dispositivi gestiti.                                                                                                                                                                                                                                           |
| [Gruppi](groups-get-started.md)                              | Informazioni su come creare e gestire gruppi con Intune. Tramite i gruppi è possibile assegnare rapidamente criteri di configurazione e protezione di dispositivi e app.                                                                                                                                             |
| [Ruoli di Intune](role-based-access-control.md)                 | Informazioni su come controllare chi può eseguire diverse azioni di Intune e come devono essere applicate tali azioni. È possibile usare i ruoli predefiniti che coprono alcuni scenari comuni in Intune oppure creare ruoli personalizzati.                                                                                 |
| [Aggiornamenti software](windows-update-for-business-configure.md) | Informazioni su come configurare gli aggiornamenti software per i dispositivi Windows 10.                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>Quali sono le novità?

Per informazioni sulle funzionalità più recenti di Microsoft Intune, vedere [Novità](whats-new.md).
