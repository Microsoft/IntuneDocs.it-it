---
title: Impostazioni di Windows Update per le aziende per Microsoft Intune - Azure | Microsoft Docs
description: Impostazioni di Windows Update per le aziende per dispositivi Windows 10 che possono essere distribuiti tramite Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e44f9d0848d449ef9131c76784ca8c7244b7c223
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550100"
---
# <a name="windows-update-settings-for-intune"></a>Impostazioni di aggiornamento di Windows per Intune  

Visualizzare le impostazioni di aggiornamento di Windows 10 che è possibile [configurare e gestire](windows-update-for-business-configure.md) con Microsoft Intune.  

Quando si configurano le impostazioni per gli anelli di aggiornamento di Windows 10 in Intune, si stanno configurando le impostazioni di aggiornamento di Windows. Se un'impostazione di aggiornamento di Windows presenta una dipendenza dalla versione di Windows 10, tale dipendenza viene indicata nei dettagli delle impostazioni.  

## <a name="update-settings"></a>Impostazioni di aggiornamento  

Le impostazioni di aggiornamento specificano quali bit un dispositivo scaricherà e quando. Per altre informazioni sul comportamento di ogni impostazione, vedere la documentazione di riferimento di Windows.  

- **Canale di manutenzione**  
  **Impostazione predefinita**: Canale semestrale  
  Windows Update CSP: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

  Impostare il canale (ramo) da cui il dispositivo riceverà gli aggiornamenti di Windows. I vari canali possono applicare periodi di differimento diversi prima di inviare gli aggiornamenti.  

  Il *canale semestrale* offre ad esempio un differimento di sei mesi. Se si usa questo canale senza aggiungere differimenti da questa serie di impostazioni, il dispositivo installerà l'aggiornamento sei mesi dopo il suo rilascio.  

  Canali di aggiornamento supportati:  

  - Canale semestrale  
  - Canale semestrale (mirato)  
  - Windows Insider - Veloce  
  - Windows Insider - Lenta  
  - Versione di Windows Insider  

  Se si seleziona un canale di Insider, Intune configura automaticamente l'impostazione di aggiornamento di Windows [Update/ManagePreviewBuildss](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) affinché la build di Insider funzioni.  


  > [!IMPORTANT]  
  > A partire da Windows versione 1903, l'uso del *Canale semestrale (mirato)* (SAC-T) è ritirato. In seguito a questa modifica, il canale SAC-T si unisce al *canale semestrale*. Per altre informazioni su questa modifica e sulle conseguenze in Windows Update per le aziende, vedere il post di blog di Windows IT Pro [Windows Update for Business and the retirement of SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523) (Windows Update per le aziende e il ritiro di SAC-T).  
 
- **Aggiornamenti ai prodotti Microsoft**  
  **Impostazione predefinita**: Consenti  
  Windows Update CSP: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **Consenti** : selezionare *Consenti* per analizzare gli aggiornamenti dell'app da Microsoft Update.  
  - **Blocca**-Seleziona blocco per impedire l'analisi degli aggiornamenti dell'app.  

- **Driver di Windows**  
  **Impostazione predefinita**: Consenti  
  Windows Update CSP: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **Consenti** -selezionare *Consenti* Includi driver Windows Update durante gli aggiornamenti.  
  - **Blocca**-Seleziona blocco per evitare l'analisi dei driver.  

- **Periodo di differimento dell'aggiornamento qualitativo (giorni)**  
  **Impostazione predefinita**: 0  
  Windows Update CSP: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  Specificare un numero di giorni compreso tra 0 e 30 di cui vengono posticipati gli aggiornamenti qualitativi. Questo periodo si aggiunge agli altri periodi di differimento previsti dal canale di manutenzione selezionato. Il periodo di differimento inizia nel momento in cui il dispositivo riceve il criterio.  

  Gli aggiornamenti qualitativi includono in genere correzioni e miglioramenti alle funzionalità di Windows esistenti.  

- **Periodo di differimento dell'aggiornamento delle funzionalità (giorni)**  
  **Impostazione predefinita**: 0  
  Windows Update CSP: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  Specificare il numero di giorni di cui vengono posticipati gli aggiornamenti delle funzionalità. Questo periodo si aggiunge agli altri periodi di differimento previsti dal canale di manutenzione selezionato. Il periodo di differimento inizia nel momento in cui il dispositivo riceve il criterio.  

  Periodo di differimento supportato:  

  - *Windows versione 1709 e successive* : da 0 a 365 giorni  
  - *Windows versione 1703*: da 0 a 180 giorni  

  Gli aggiornamenti delle funzionalità includono in genere nuove funzionalità per Windows.  

- **Impostare il periodo di disinstallazione degli aggiornamenti delle funzionalità (2-60 giorni)**  
  **Impostazione predefinita**: 10  
  Windows Update CSP: [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  Configurare un periodo dopo il quale non è possibile disinstallare gli aggiornamenti delle funzionalità.  

  Trascorso questo periodo, i bit di aggiornamento precedenti vengono rimossi dal dispositivo. Non è quindi più possibile eseguire la disinstallazione e passare alla versione di aggiornamento precedente.  

  Si consideri ad esempio un anello di aggiornamento che ha un periodo di disinstallazione degli aggiornamenti delle funzionalità di 20 giorni. Dopo 25 giorni si decide di eseguire il rollback dell'aggiornamento delle funzionalità più recente e di usare l'opzione di disinstallazione.  I dispositivi che hanno installato l'aggiornamento delle funzionalità oltre 20 giorni prima non possono disinstallare l'aggiornamento perché sono stati rimossi i bit necessari come parte della manutenzione. I dispositivi che invece hanno installato l'aggiornamento delle funzionalità non oltre 19 giorni prima possono disinstallare l'aggiornamento, verificando di aver ricevuto il comando di disinstallazione prima di aver superato il periodo di disinstallazione di 20 giorni.  

## <a name="user-experience-settings"></a>Impostazioni dell'esperienza utente  

Le impostazioni dell'esperienza utente specificano l'esperienza dell'utente finale relativamente al riavvio dei dispositivi e ai promemoria. Per altre informazioni sul comportamento di ogni impostazione, vedere la documentazione CSP (Configuration Service Provider) di Windows Update.  

- **Comportamento di aggiornamento automatico**  
  **Impostazione predefinita**: Installa automaticamente durante la manutenzione  
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  Scegliere la modalità di installazione degli aggiornamenti automatici e se necessario quando riavviare il dispositivo.  

  Opzioni supportate:  

  - **Notifica download**: invia una notifica all'utente prima di scaricare l'aggiornamento. Gli utenti scelgono di scaricare e installare gli aggiornamenti.  

  - **Installa automaticamente durante la manutenzione**: aggiorna automaticamente il download ed esegue l'installazione durante la Manutenzione automatica quando il dispositivo non è in uso oppure è alimentato a batteria. Quando il riavvio è obbligatorio, viene richiesto il riavvio per sette giorni, dopo di ché il riavvio viene forzato.  

    Questa opzione consente di riavviare un dispositivo automaticamente dopo l'installazione dell'aggiornamento. Usare le impostazioni **Orario di attività** per definire un periodo durante il quale i riavvii automatici sono bloccati:  

    - **Inizio dell'orario di attività**: consente di specificare un'ora di inizio per impedire i riavvi conseguenti all'installazione degli aggiornamenti.  
      **Impostazione predefinita**: ore 8  
      Windows Update CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Fine dell'orario di attività**: consente di specificare un'ora di fine per impedire i riavvi conseguenti all'installazione degli aggiornamenti.  
      **Impostazione predefinita**: ore 17  
      Windows Update CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Installa e riavvia automaticamente durante la manutenzione**: aggiorna automaticamente il download ed esegue l'installazione durante la Manutenzione automatica quando il dispositivo non è in uso oppure è alimentato a batteria. Quando il riavvio è obbligatorio, il dispositivo viene riavviato in un momento in cui non è in uso. È l'impostazione predefinita per i dispositivi non gestiti.  

    Questa opzione consente di riavviare un dispositivo automaticamente dopo l'installazione dell'aggiornamento. L'uso delle impostazioni **Orario di attività** non è descritto nelle impostazioni di Windows Update. Questi impostazioni vengono comunque usate da Intune per definire un periodo durante il quale i riavvii automatici sono bloccati:  

    - **Inizio dell'orario di attività**: consente di specificare un'ora di inizio per impedire i riavvi conseguenti all'installazione degli aggiornamenti.  
      **Impostazione predefinita**: ore 8  
      Windows Update CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Fine dell'orario di attività**: consente di specificare un'ora di fine per impedire i riavvi conseguenti all'installazione degli aggiornamenti.  
      **Impostazione predefinita**: ore 17  
      Windows Update CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Installa e riavvia automaticamente all'ora pianificata**: consente di specificare un giorno e un'ora per l'installazione. Se non vengono specificati, l'installazione viene eseguita ogni giorno alle 15:00 e dopo un conto alla rovescia di 15 minuti, il dispositivo viene riavviato. Gli utenti che hanno eseguito l'accesso possono ritardare il conto alla rovescia e riavviare.   
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    Questa opzione supporta impostazioni aggiuntive.  

    - **Frequenza del comportamento automatico**: usare questa impostazione per pianificare il momento in cui vengono installati gli aggiornamenti, inclusi settimana, data e ora.  
      **Impostazione predefinita**: Ogni settimana

    - **Giorno pianificato per l'installazione**: specificare il giorno della settimana in cui si vogliono installare gli aggiornamenti.  
      **Impostazione predefinita**: Qualsiasi giorno  

    - **Orario pianificato per l'installazione**: specificare l'ora del giorno in cui si vogliono installare gli aggiornamenti.  
      **Impostazione predefinita**: ore 3  

  - **Installa e riavvia automaticamente senza il controllo dell'utente finale**: aggiorna automaticamente il download ed esegue l'installazione durante la Manutenzione automatica quando il dispositivo non è in uso oppure è alimentato a batteria. Quando il riavvio è obbligatorio, il dispositivo viene riavviato in un momento in cui non è in uso. Questa opzione imposta il riquadro di controllo degli utenti finali in sola lettura.  

  - **Ripristina predefinito**: ripristina le impostazioni di aggiornamento automatico originali nei computer Windows 10 che hanno eseguito l'Aggiornamento di Windows 10 (ottobre 2018) o versioni successive.  


- **Verifiche al riavvio**  
  **Impostazione predefinita**: Consenti  
  Windows Update CSP: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  Per ignorare queste verifiche quando si riavvia un dispositivo, selezionare **Ignora**. 
  
  I risultati di questa impostazione sono diversi a seconda della versione dei dispositivi di Windows:  
 
  - *Windows versione 1703 e precedenti*: quando si riavvia un dispositivo, vengono eseguite alcune verifiche, ad esempio la ricerca di utenti attivi, i livelli di batteria, eventuali giochi in esecuzione e altro ancora.  
  
  - *Windows versione 1709 e successive*: durante gli orari di attività, per gli aggiornamenti non vengono eseguiti processi quali analisi, download, installazione e riavvio. Al termine degli orari di attività, i processi di aggiornamento vengono eseguiti, possono riattivare il dispositivo da sospensione, analisi, download e installazione e riavviano il dispositivo dopo aver controllato la batteria e l'alimentazione. 

- **Impedisci all'utente di sospendere gli aggiornamenti Windows**  
  **Impostazione predefinita**: Consenti  
  Windows Update CSP: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **Consenti** : consente agli utenti del dispositivo di sospendere l'installazione di un aggiornamento.  
  - **Blocca** : impedisce agli utenti del dispositivo di sospendere l'installazione di un aggiornamento.  

- **Impedisci all'utente di cercare aggiornamenti Windows**  
  **Impostazione predefinita**: Consenti  
  Windows Update CSP: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **Consenti** : consente agli utenti del dispositivo di usare Windows Update Scan per trovare e scaricare gli aggiornamenti e installare le funzionalità.
  - **Blocca** : impedisce agli utenti del dispositivo di accedere al Windows Update analisi, scaricare gli aggiornamenti e installare le funzionalità.  

- **Richiedi l'approvazione dell'utente per il riavvio in orario non lavorativo**  
  **Impostazione predefinita**: Non configurato  
  Windows Update CSP: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **Non configurato**  
  - **Obbligatorio**: per richiedere l'approvazione dell'utente per riavviare un dispositivo in orario non lavorativo.  
   
- **Avvisa l'utente prima del riavvio automatico obbligatorio con un promemoria ignorabile (ore)**  
  **Impostazione predefinita**: 4  
  Windows Update CSP: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  Specificare quanto tempo prima di un riavvio automatico l'utente di un dispositivo deve visualizzare una notifica ignorabile sul riavvio. I valori supportati espressi in ora sono **2**, **4**, **8**, **12** o **24**.  
  
  Quando si cancella il valore predefinito, questa impostazione *non*viene configurata.  

- **Avvisa l'utente prima del riavvio automatico obbligatorio con un promemoria permanente (minuti)**  
  **Impostazione predefinita**: 15  
  Windows Update CSP: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  Specificare quanto tempo prima di un riavvio automatico l'utente di un dispositivo deve visualizzare un avviso non ignorabile sul riavvio. I valori supportati espressi in minuti sono **15**, **30** o **60**.  

  Quando si cancella il valore predefinito, questa impostazione *non*viene configurata.  

- **Modifica il livello di aggiornamento della notifica**  
  **Impostazione predefinita**: Usa le notifiche predefinite di Windows Update  
  Windows Update CSP: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  Specificare il livello di notifiche di Windows Update per gli utenti. Questa impostazione non controlla come e quando gli aggiornamenti vengono scaricati e installati.  

  Opzioni supportate:
  - **Non configurato**
  - **Usa le notifiche predefinite di Windows Update**
  - **Disattiva tutte le notifiche, esclusi gli avvisi di riavvio**
  - **Disattiva tutte le notifiche, inclusi gli avvisi di riavvio**  

- **Consenti all'utente di riavviare (riavvio in caso di occupato)**  
  **Impostazione predefinita**: Non configurato  
  > [!IMPORTANT]  
  > Non è più consigliabile usare le impostazioni di *riavvio* . Usare invece le nuove impostazioni di *scadenza* che sostituiscono le impostazioni di *riavvio* . Intune determinerà [il supporto *per le* impostazioni di riavvio](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) in un aggiornamento futuro.

  Il riavvio attivato è supportato per Windows 10 versione 1803 e versioni successive. 

  > [!NOTE]  
  > Windows 10 versione 1809 introduce impostazioni aggiuntive di riavvio in caso di occupato che consentono di applicare impostazioni distinte agli aggiornamenti delle funzionalità e agli aggiornamenti qualitativi. Le impostazioni gestite da Intune non vengono tuttavia applicate separatamente ai vari tipi di aggiornamento. Al contrario, Intune applica gli stessi valori sia agli aggiornamenti delle funzionalità sia agli aggiornamenti qualitativi.  
  
  - **Non configurato**  
  - **Obbligatorio**: impostare su *Obbligatorio* per consentire l'uso delle opzioni di riavvio in caso di occupato per gli aggiornamento di Windows 10. Queste opzioni coinvolgono l'utente di un dispositivo nella gestione del riavvio di un dispositivo dopo l'installazione di un aggiornamento che richiede un riavvio.  

  Per altre informazioni su questa opzione, vedere [Riavvio in caso di occupato](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart) nella documentazione di Windows 10 per la distribuzione degli aggiornamenti.  

  Le impostazioni seguenti consentono di specificare quando si verificano le azioni di riavvio in caso di occupato.  

  - **Esegui la transizione degli utenti al riavvio in caso di occupato dopo un riavvio automatico (giorni)**  
    **Impostazione predefinita**: non configurata Windows Update CSP: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
    
    Specificare un valore compreso tra **2** e **30** giorni per indicare dopo quanto tempo dall'installazione dell'aggiornamento il dispositivo attiva il comportamento di riavvio in caso di occupato. Trascorso il numero di giorni configurato, gli utenti riceveranno una richiesta di riavvio del dispositivo.  

  - **Posponi il promemoria per il riavvio in caso di occupato (giorni)**  
    **Impostazione predefinita**: Non configurato    
    Windows Update CSP: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
    
    Specificare un valore compreso tra **1** e **3** per il periodo di tempo durante il quale una richiesta di riavvio può essere posticipata.  Trascorso questo periodo, viene nuovamente richiesto il riavvio. L'utente può continuare a posporre il promemoria fino alla scadenza dell'installazione.  

  - **Imposta la scadenza per i riavvii in sospeso (giorni)**  
    **Impostazione predefinita**: Non configurato  
    Windows Update CSP: [Update/EngagedRestartDeadline](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  
    Specificare un valore compreso tra **2** e **30** come numero massimo di giorni di attesa dall'inizio del comportamento di riavvio in caso di occupato, prima che il dispositivo imponga un riavvio obbligatorio. Per questo riavvio verrà richiesto agli utenti di salvare il lavoro.

- **Usa impostazioni scadenza**  
  **Impostazione predefinita**: Non configurato  
  > [!IMPORTANT]  
  > A partire dall'aggiornamento di agosto per Intune, è consigliabile usare le seguenti impostazioni di scadenza che sostituiscono le impostazioni di riavvio. Intune determinerà [il supporto *per le* impostazioni di riavvio](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) in un futuro aggiornamento a Intune.  

  Consente all'utente di usare le impostazioni di scadenza.  

  - **Non configurato**
  - **Consentito**

  Quando è impostato su *Consenti*, è possibile configurare le impostazioni seguenti per le scadenze:

  - **Scadenza per gli aggiornamenti delle funzionalità**  
    **Impostazione predefinita**: 7  
    Windows Update CSP: [Update/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    Specifica il numero di giorni per cui un utente ha prima che gli aggiornamenti delle funzionalità vengano installati automaticamente nei dispositivi (2-30).

  - **Scadenza per gli aggiornamenti qualitativi**  
    **Impostazione predefinita**: 7  
    Windows Update CSP: [Update/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    Specifica il numero di giorni per cui un utente ha prima che gli aggiornamenti qualitativi siano installati automaticamente nei propri dispositivi (2-30).

  - **Periodo di tolleranza**  
    **Impostazione predefinita**: 2 Windows Update CSP: [Update/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    Specifica un numero minimo di giorni dopo la scadenza finché i riavvii non vengono eseguiti automaticamente (0-7).

  - **Riavvio automatico prima della scadenza**  
    **Impostazione predefinita**: Sì Windows Update CSP: [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    Specifica se il dispositivo deve essere riavviato automaticamente prima della scadenza.
    - **Sì**
    - **No**




### <a name="delivery-optimization-download-mode"></a>Modalità di download con ottimizzazione recapito  

L’ottimizzazione del recapito non viene più configurata nell’ambito di un anello di aggiornamento di Windows 10 durante l’esecuzione della funzionalità Aggiornamenti software. L’ottimizzazione del recapito ora viene impostata tramite la configurazione del dispositivo. Tuttavia, le configurazioni precedenti rimangono disponibili nella console. È possibile rimuovere le configurazioni precedenti impostandole su *Non configurato*. Non è tuttavia possibile modificarle in altro modo. 

Per evitare conflitti tra criteri nuovi e precedenti, vedere [Passare dagli anelli di aggiornamento esistenti a ottimizzazione recapito](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) e quindi spostare le impostazioni in un profilo di ottimizzazione recapito.
