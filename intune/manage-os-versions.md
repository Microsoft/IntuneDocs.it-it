---
title: Gestire le versioni del sistema operativo con Microsoft Intune | Microsoft Intune
description: Informazioni su come gestire le versioni del sistema operativo su piattaforme con Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.openlocfilehash: 27a581a72c20c940a04a791ef9e63a2dc8bf5b24
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816991"
---
# <a name="manage-operating-system-versions-with-intune"></a>Gestire le versioni del sistema operativo con Intune
Sulle piattaforme moderne di dispositivi mobili e desktop, i principali aggiornamenti, le patch e le nuove versioni vengono rilasciati con una certa rapidità. In Windows è possibile controllare la gestione completa degli aggiornamenti e delle patch, mentre altre piattaforme quali iOS e Android richiedono la partecipazione degli utenti finali al processo.  Le funzionalità di Microsoft Intune consentono di strutturare la gestione delle versioni del sistema operativo in piattaforme diverse.

Intune consente di gestire questi scenari comuni: 
- determinare quali sono le versioni del sistema operativo nei dispositivi degli utenti finali
- controllare l'accesso ai dati aziendali nei dispositivi durante il rilascio di una nuova versione del sistema operativo
- invitare/richiedere agli utenti finali di eseguire l'aggiornamento all'ultima versione del sistema operativo approvata dall'organizzazione
- gestire un'implementazione a livello di organizzazione di una nuova versione del sistema operativo
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Controllo della versione del sistema operativo usando le restrizioni di registrazione della gestione di dispositivi mobili (MDM) di Intune
Le restrizioni di registrazione MDM di Intune lasciano definire i requisiti del dispositivo client prima di consentire la registrazione del dispositivo. L'obiettivo è quello di far sì che gli utenti finali registrino solo dispositivi conformi per accedere alle risorse aziendali. I requisiti del dispositivo includono sia la versione minima sia la versione massima consentita del sistema operativo per le piattaforme supportate.
 
![Pannello delle restrizioni di configurazione della piattaforma](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>In pratica
Le organizzazioni usano le restrizioni sul tipo di dispositivo per controllare l'accesso alle risorse aziendali usando le impostazioni seguenti: 
1. Usare la versione minima del sistema operativo per mantenere gli utenti finali nelle piattaforme correnti e supportate dall'organizzazione. 
2. Lasciare la versione massima del sistema operativo non specificata (nessun limite) oppure impostare l'ultima versione convalidata dall'organizzazione per lasciare un determinato periodo di tempo per effettuare test interni relativi alle nuove versioni del sistema operativo.

Per informazioni dettagliate, vedere [Impostare le restrizioni sul tipo di dispositivi](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions).
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>Report della versione del sistema operativo e conformità ai criteri di conformità del dispositivo MDM di Intune
I criteri di conformità MDM di Intune offrono gli strumenti seguenti: 
- specificare le regole di conformità
- visualizzare lo stato di conformità tramite report
- agire sulla mancata conformità tramite quarantena dei dispositivi e accesso condizionale

Analogamente alle restrizioni di registrazione, i criteri di conformità del dispositivo includono sia la versione minima sia quella massima del sistema operativo. I criteri comprendono anche una cronologia di conformità per offrire agli utenti un periodo di tolleranza per ottenere tale conformità. I criteri di conformità dei dispositivi mantengono i dispositivi registrati dell'utente finale conformi ai criteri dell'organizzazione.

![Conformità del dispositivo - azioni per i dispositivi non conformi](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>In pratica
Le organizzazioni usano i criteri di conformità del dispositivo per gli stessi scenari come restrizioni di registrazione. Questi criteri mantengono gli utenti nella versione del sistema operativo corrente e convalidata dall'azienda. Quando i dispositivi degli utenti finali risultano non conformi, l'accesso alle risorse dell'organizzazione può essere bloccato tramite l'accesso condizionale fino a quando gli utenti finali non rientreranno nell'intervallo del sistema operativo supportato per l'organizzazione. Gli utenti finali non conformi ricevono una notifica e i passaggi per ripristinare l'accesso.   

Per informazioni dettagliate, vedere [Get started with device compliance](https://docs.microsoft.com/intune/device-compliance-get-started) (Introduzione alla conformità dei dispositivi).
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Controlli della versione del sistema operativo tramite i criteri di protezione app di Intune    
I criteri di protezione delle app di Intune e le impostazioni di accesso della gestione di applicazioni mobili (MAM) consentono di specificare la versione minima del sistema operativo a livello dell'app. Consente di informare e invitare gli utenti ad aggiornare il sistema operativo a una versione minima specificata.
 
Sono disponibili due opzioni diverse: 
- **Avviso**: consiglia all'utente finale di effettuare l'aggiornamento quando si apre un'applicazione con criteri di protezione o impostazioni di accesso della gestione di applicazioni mobili su un dispositivo con una versione del sistema operativo precedente alla versione specificata. Accesso alle app e ai dati aziendali consentito.
  ![Immagine della finestra di dialogo Avviso sull'aggiornamento di Android](./media/os-version-update-warning.png) 

- **Blocco**: informa l'utente finale che è necessario effettuare l'aggiornamento quando si apre un'app con criteri di protezione o impostazioni di accesso della gestione di applicazioni mobili su un dispositivo con una versione del sistema operativo precedente alla versione specificata. Accesso alle app e ai dati aziendali non consentito.
  ![Immagine della finestra di dialogo L'accesso all'app è bloccato](./media/os-version-access-blocked.png)

### <a name="in-practice"></a>In pratica
Le organizzazioni usano le impostazioni dei criteri di protezione delle app quando le app vengono aperte come mezzo per informare gli utenti finali circa la necessità di mantenere aggiornate le proprie app. Una configurazione di esempio si ha quando gli utenti ricevono l'avviso sulla versione attuale meno uno e sono bloccati sulla versione attuale meno due.
 
Per informazioni dettagliate, vedere [Come creare e assegnare criteri di protezione delle app](https://docs.microsoft.com/intune/app-protection-policies).

## <a name="managing-a-new-operating-system-version-rollout"></a>Gestione di una nuova implementazione di versione del sistema operativo
È possibile usare le funzionalità di Intune descritte in questo articolo per far passare l'organizzazione a una nuova versione del sistema operativo nella sequenza temporale definita. I seguenti passaggi sono un modello di distribuzione di esempio per spostare gli utenti dalla versione 1 del sistema operativo alla versione 2 del sistema operativo in sette giorni.
- **Passaggio 1**: Usare le restrizioni di registrazione per richiedere la versione 2 del sistema operativo come versione minima per registrare il dispositivo. Ciò garantisce che i nuovi dispositivi degli utenti finali siano compatibili in fase di registrazione.
- **Passaggio 2a**: Usare i criteri di protezione delle app di Intune per avvisare gli utenti quando l'app viene aperta o se è necessaria la versione 2 del sistema operativo.
- **Passaggio 2b**. Usare criteri di conformità dei dispositivi per richiedere la versione 2 del sistema operativo come versione minima per la conformità del dispositivo. Usare **Azioni** in caso di mancata conformità per consentire un periodo di tolleranza di sette giorni e inviare agli utenti finali una notifica di posta elettronica con i requisiti e la sequenza temporale.
  -  Questi criteri informano gli utenti finali che i dispositivi esistenti devono essere aggiornati tramite posta elettronica, il portale aziendale di Intune e quando l'applicazione viene aperta per le app abilitate con un criterio di protezione delle app.
  - È possibile eseguire un report di conformità per identificare gli utenti non conformi. 
- **Passaggio 3a**: Usare i criteri di protezione delle app di Intune per bloccare gli utenti quando un'applicazione viene aperta se il dispositivo non esegue la versione 2 del sistema operativo.
- **Passaggio 3b**: Usare criteri di conformità dei dispositivi per richiedere la versione 2 del sistema operativo come versione minima per la conformità del dispositivo.
  - Questi criteri richiedono l'aggiornamento dei dispositivi per continuare ad accedere ai dati aziendali. I servizi protetti vengono bloccati quando vengono usati con accesso condizionale per i dispositivi. Le app abilitate con un criterio di protezione delle app vengono bloccate quando aperte o quando accedono ai dati aziendali.

## <a name="next-steps"></a>Passaggi successivi
Usare le risorse seguenti per gestire le versioni del sistema operativo all'interno dell'organizzazione: 

- [Impostare le restrizioni sul tipo di dispositivi](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [Get started with device compliance](https://docs.microsoft.com/intune/device-compliance-get-started) (Introduzione alla conformità dei dispositivi)
- [Come creare e assegnare criteri di protezione delle app](https://docs.microsoft.com/intune/app-protection-policies) (How to create and assign app protection policies)
