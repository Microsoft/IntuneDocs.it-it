---
title: Impostazioni di Windows Update per le aziende per Microsoft Intune - Azure | Microsoft Docs
description: Impostazioni di Windows Update per le aziende per dispositivi Windows 10 che possono essere distribuiti tramite Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98c3425c58b6039c8a1c3b5750f9473c74a78634
ms.sourcegitcommit: 93de3423d2d8f0019e676a63784edeb3daf47cb7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/16/2019
ms.locfileid: "56325470"
---
# <a name="windows-update-settings-for-intune"></a>Impostazioni di aggiornamento di Windows per Intune  

Visualizzare le impostazioni di aggiornamento di Windows 10 che è possibile [configurare e gestire](windows-update-for-business-configure.md) con Microsoft Intune.  

Quando si configurano le impostazioni per gli anelli di aggiornamento di Windows 10 in Intune, si stanno configurando le impostazioni di aggiornamento di Windows.  Quando un'impostazione di aggiornamento di Windows presenta una dipendenza dalla versione di Windows 10, tale dipendenza viene indicata nei dettagli delle impostazioni.  

## <a name="update-settings"></a>Impostazioni di aggiornamento  

Le impostazioni di aggiornamento specificano quali bit un dispositivo scaricherà e quando. Vedere la documentazione di riferimento di Windows per altre informazioni sul comportamento di ogni impostazione.  

### <a name="servicing-channel"></a>Canale di manutenzione  

- **Impostazione predefinita**: Canale semestrale (mirato)  
- **Documentazione di riferimento di Windows**: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
Impostare il canale (ramo) da cui il dispositivo riceverà gli aggiornamenti di Windows. I vari canali possono applicare periodi di differimento diversi prima di inviare gli aggiornamenti.  

Il *canale semestrale* offre ad esempio un differimento di sei mesi. Ciò significa che se si usa questo canale senza aggiungere differimenti da questa serie di impostazioni, il dispositivo installerà l'aggiornamento sei mesi dopo il suo rilascio.  

Canali di aggiornamento supportati:  

- Canale semestrale  
- Canale semestrale (mirato)  
- Windows Insider - Veloce  
- Windows Insider - Lenta  
- Versione di Windows Insider  

Se si seleziona un canale di Insider, Intune configura automaticamente l'impostazione di aggiornamento di Windows [Update/ManagePreviewBuildss](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) affinché la build di Insider funzioni.  


> [!IMPORTANT]  
> A partire da Windows versione 1903, l'uso del *Canale semestrale (mirato)* (SAC-T) è ritirato. In seguito a questa modifica, il canale SAC-T si unisce al *canale semestrale*. Per altre informazioni su questa modifica e sulle conseguenze in Windows Update per le aziende, vedere il post di blog di Windows IT Pro [Windows Update for Business and the retirement of SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523) (Windows Update per le aziende e il ritiro di SAC-T).
 


### <a name="microsoft-product-updates"></a>Aggiornamenti di prodotti Microsoft  

- **Impostazione predefinita**:  Consenti
- **Documentazione di riferimento di Windows**: [Update/AllowMUUpdateService](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Scegliere *Consenti* per cercare gli aggiornamenti di app in Microsoft Update.    

### <a name="windows-drivers"></a>Driver di Windows  

- **Impostazione predefinita**:  Consenti
- **Documentazione di riferimento di Windows**: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Scegliere *Consenti* per includere i driver di Windows Update durante gli aggiornamenti

### <a name="quality-update-deferral-period-days"></a>Periodo di differimento dell'aggiornamento qualitativo (giorni)  

- **Impostazione predefinita**: 0  
- **Documentazione di riferimento di Windows**: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Specificare un numero di giorni compreso tra 0 e 30 di cui vengono posticipati gli aggiornamenti qualitativi. Questo periodo si aggiunge agli altri periodi di differimento previsti dal canale di manutenzione selezionato. Il periodo di differimento inizia nel momento in cui il dispositivo riceve il criterio.  

Gli aggiornamenti qualitativi includono in genere correzioni e miglioramenti alle funzionalità di Windows esistenti.  

### <a name="feature-update-deferral-period-days"></a>Periodo di differimento dell'aggiornamento delle funzionalità (giorni)  

- **Impostazione predefinita**: 0  
- **Documentazione di riferimento di Windows**: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Specificare il numero di giorni di cui vengono posticipati gli aggiornamenti delle funzionalità. Questo periodo si aggiunge agli altri periodi di differimento previsti dal canale di manutenzione selezionato. Il periodo di differimento inizia nel momento in cui il dispositivo riceve il criterio.  
Periodo di differimento supportato:  

- *Windows 1709 o versioni successive*: da 0 a 365 giorni  
- *Windows versione 1703*:  da 0 a 180 giorni  

Gli aggiornamenti delle funzionalità includono in genere nuove funzionalità per Windows.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Impostare il periodo di disinstallazione degli aggiornamenti delle funzionalità (2-60 giorni)  

- **Impostazione predefinita**: 10  
- **Documentazione di riferimento di Windows**:  [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Configurare un periodo dopo il quale non è possibile disinstallare gli aggiornamenti delle funzionalità.  

Trascorso questo periodo, i bit di aggiornamento precedenti vengono rimossi dal dispositivo. Non è quindi più possibile eseguire la disinstallazione e passare alla versione di aggiornamento precedente.  

Si consideri ad esempio un anello di aggiornamento che ha un periodo di disinstallazione degli aggiornamenti delle funzionalità di 20 giorni. Dopo 25 giorni si decide di eseguire il rollback dell'aggiornamento delle funzionalità più recente e di usare l'opzione di disinstallazione.  I dispositivi che hanno installato l'aggiornamento delle funzionalità oltre 20 giorni prima non possono disinstallare l'aggiornamento perché sono stati rimossi i bit necessari come parte della manutenzione. I dispositivi che invece hanno installato l'aggiornamento delle funzionalità non oltre 19 giorni prima possono disinstallare l'aggiornamento, verificando di aver ricevuto il comando di disinstallazione prima di aver superato il periodo di disinstallazione di 20 giorni.  


## <a name="user-experience-settings"></a>Impostazioni dell'esperienza utente  

Le impostazioni dell'esperienza utente specificano l'esperienza dell'utente finale relativamente al riavvio dei dispositivi e ai promemoria. Vedere la documentazione di riferimento di Windows per altre informazioni sul comportamento di ogni impostazione.  

### <a name="automatic-update-behavior"></a>Comportamento di aggiornamento automatico  

- **Impostazione predefinita**: installa e riavvia automaticamente all'ora pianificata  
- **Documentazione di riferimento di Windows**: [Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Scegliere la modalità di installazione degli aggiornamenti automatici e se necessario quando riavviare il dispositivo.  

Vedere la documentazione di riferimento di Windows per informazioni dettagliate sulle opzioni supportate seguenti:  

- **Notifica download**: invia una notifica all'utente prima di scaricare l'aggiornamento. Gli utenti scelgono di scaricare e installare gli aggiornamenti.  

- **Installa automaticamente durante la manutenzione**: aggiorna automaticamente il download ed esegue l'installazione durante la Manutenzione automatica quando il dispositivo non è in uso oppure è alimentato a batteria. Quando il riavvio è obbligatorio, viene richiesto il riavvio per sette giorni, dopo di ché il riavvio viene forzato.  

  Questa opzione consente di riavviare un dispositivo automaticamente dopo l'installazione dell'aggiornamento. Usare le impostazioni **Orario di attività** per definire un periodo durante il quale i riavvii automatici sono bloccati:  

  - **Inizio dell'orario di attività**: consente di specificare un'ora di inizio per impedire i riavvi conseguenti all'installazione degli aggiornamenti.  
    **Documentazione di riferimento di Windows**:  [Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Impostazione predefinita**: 8:00  
  
  - **Fine dell'orario di attività**: consente di specificare un'ora di fine per impedire i riavvi conseguenti all'installazione degli aggiornamenti.  
    **Documentazione di riferimento di Windows**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Impostazione predefinita**: 17:00  

- **Installa e riavvia automaticamente durante la manutenzione**: aggiorna automaticamente il download ed esegue l'installazione durante la Manutenzione automatica quando il dispositivo non è in uso oppure è alimentato a batteria. Quando il riavvio è obbligatorio, il dispositivo viene riavviato in un momento in cui non è in uso. È l'impostazione predefinita per i dispositivi non gestiti.  

  Questa opzione consente di riavviare un dispositivo automaticamente dopo l'installazione dell'aggiornamento. L'uso delle impostazioni **Orario di attività** non è descritto nelle impostazioni di Windows Update. Questi impostazioni sono comunque usate da Intune per definire un periodo durante il quale i riavvii automatici sono bloccati:  

  - **Inizio dell'orario di attività**: consente di specificare un'ora di inizio per impedire i riavvi conseguenti all'installazione degli aggiornamenti.  
    **Documentazione di riferimento di Windows**:  [Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Impostazione predefinita**: 8:00  

  - **Fine dell'orario di attività**: consente di specificare un'ora di fine per impedire i riavvi conseguenti all'installazione degli aggiornamenti.  
    **Documentazione di riferimento di Windows**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Impostazione predefinita**: 17:00  

- **Installa e riavvia automaticamente all'ora pianificata**: consente di specificare un giorno e un'ora per l'installazione. Se non vengono specificati, l'installazione viene eseguita ogni giorno alle 15:00 e dopo un conto alla rovescia di 15 minuti, il dispositivo viene riavviato. Gli utenti che hanno eseguito l'accesso possono ritardare il conto alla rovescia e riavviare.  
  
  Questa opzione supporta impostazioni aggiuntive.  
  **Documentazione di riferimento di Windows**:  [Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Frequenza del comportamento automatico**: Usare questa impostazione per pianificare il momento in cui vengono installati gli aggiornamenti, inclusi settimana, data e ora.  
    **Impostazione predefinita**: Ogni settimana

  - **Giorno pianificato per l'installazione**:  consente di specificare il giorno della settimana in cui si vogliono installare gli aggiornamenti.  
    **Impostazione predefinita**: Qualsiasi giorno  

  - **Orario pianificato per l'installazione**:  consente di specificare l'ora del giorno in cui si vogliono installare gli aggiornamenti.  
    **Impostazione predefinita**: 15:00  

- **Installa e riavvia automaticamente senza il controllo dell'utente finale**: aggiorna automaticamente il download ed esegue l'installazione durante la Manutenzione automatica quando il dispositivo non è in uso oppure è alimentato a batteria. Quando il riavvio è obbligatorio, il dispositivo viene riavviato in un momento in cui non è in uso. Questa opzione imposta il riquadro di controllo degli utenti finali in sola lettura.  

- **Ripristina predefinito**: ripristina le impostazioni di aggiornamento automatico originali nei computer Windows 10 che hanno eseguito l'Aggiornamento di Windows 10 (ottobre 2018) o versioni successive.  


### <a name="restart-checks"></a>Verifiche al riavvio  

- **Impostazione predefinita**: Consenti  
- **Documentazione di riferimento di Windows**: [Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

I risultati di questa impostazione sono diversi a seconda della versione dei dispositivi di Windows:  

- Windows versione 1703 e versioni precedenti: Quando si riavvia un dispositivo, vengono eseguite alcune verifiche, ad esempio la ricerca di utenti attivi, i livelli di batteria, eventuali giochi in esecuzione e altro ancora. Per ignorare queste verifiche quando si riavvia un dispositivo, selezionare **Ignora**.  
- A partire da Windows versione 1709: Durante gli orari di attività, i processi seguenti non vengono eseguiti in caso di aggiornamento: analisi, download, installazione e riavvio. Al termine degli orari di attività, i processi di aggiornamento vengono eseguiti, possono riattivare il dispositivo da sospensione, analisi, download e installazione e riavviano il dispositivo dopo aver controllato la batteria e l'alimentazione. Per altre informazioni, vedere [Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>Impedisci all'utente di sospendere gli aggiornamenti Windows  

- **Impostazione predefinita**: Consenti  
- **Documentazione di riferimento di Windows**: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Consente o impedisce a un utente del dispositivo di sospendere l'installazione di un aggiornamento.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>Richiedi l'approvazione dell'utente per il riavvio in orario non lavorativo  

- **Impostazione predefinita**: Non configurata  
- **Documentazione di riferimento di Windows**: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
Selezionare *Obbligatoria* per richiedere l'approvazione dell'utente per riavviare un dispositivo in orario non lavorativo.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>Avvisa l'utente prima del riavvio automatico obbligatorio con un promemoria ignorabile (ore)  

- **Impostazione predefinita**: *Non è configurabile per impostazione predefinita. Non vengono inviati promemoria agli utenti*.  
- **Documentazione di riferimento di Windows**: [Update/ScheduleRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Specificare quanto tempo prima di un riavvio automatico l'utente di un dispositivo deve visualizzare una notifica ignorabile sul riavvio. I valori supportati espressi in ora sono **2**, **4**, **8**, **12** o **24**.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>Avvisa l'utente prima del riavvio automatico obbligatorio con un promemoria permanente (minuti)  

- **Impostazione predefinita**: *Non è configurabile per impostazione predefinita. Non vengono inviati promemoria agli utenti*.  
- **Documentazione di riferimento di Windows**: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Specificare quanto tempo prima di un riavvio automatico l'utente di un dispositivo deve visualizzare un avviso non ignorabile sul riavvio. I valori supportati espressi in minuti sono **15**, **30** o **60**.  
 
### <a name="allow-user-to-restart-engaged-restart"></a>Consenti all'utente di riavviare (riavvio in caso di occupato)  

- **Impostazione predefinita**: Non configurata  
- **Documentazione di riferimento di Windows**: *Non applicabile*  
- **Versione di Windows**: supporto per Windows 10 versione 1803 e versioni successive  

  > [!NOTE]  
  > Windows 10 versione 1809 introduce impostazioni aggiuntive di riavvio in caso di occupato che consentono di applicare impostazioni distinte agli aggiornamenti delle funzionalità e agli aggiornamenti qualitativi. Le impostazioni gestite da Intune non vengono tuttavia applicate separatamente ai vari tipi di aggiornamento. Al contrario, Intune applica gli stessi valori sia agli aggiornamenti delle funzionalità sia agli aggiornamenti qualitativi.  

Se si imposta **Obbligatoria**, si abilita l'uso delle opzioni di riavvio in caso di occupato per gli aggiornamento di Windows 10. Queste opzioni coinvolgono l'utente di un dispositivo nella gestione del riavvio di un dispositivo dopo l'installazione di un aggiornamento che richiede un riavvio.  

Per altre informazioni su questa opzione, vedere [Riavvio in caso di occupato](https://docs.microsoft.com/en-us/windows/deployment/update/waas-restart#engaged-restart) nella documentazione di Windows 10 per la distribuzione degli aggiornamenti.  

Le impostazioni seguenti consentono di specificare quando si verificano le azioni di riavvio in caso di occupato.  

- **Esegui la transizione degli utenti al riavvio in caso di occupato dopo un riavvio automatico (giorni)**  
  - **Impostazione predefinita**:  Per impostazione predefinita, questa impostazione non è configurata, ma supporta un valore compreso tra **2** e **30**.  
  - **Documentazione di riferimento di Windows**: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Specifica dopo quanto tempo dall'installazione dell'aggiornamento il dispositivo attiva il comportamento di riavvio in caso di occupato. Trascorso il numero di giorni configurato, gli utenti riceveranno una richiesta di riavvio del dispositivo.  

- **Posponi il promemoria per il riavvio in caso di occupato (giorni)**  
  - **Impostazione predefinita**:  Per impostazione predefinita, questa impostazione non è configurata, ma supporta un valore compreso tra **1** e **3**.  
  - **Documentazione di riferimento di Windows**: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Specifica per quanto tempo è possibile posporre il riavvio.  Trascorso questo periodo, viene nuovamente richiesto il riavvio. L'utente può continuare a posporre il promemoria fino alla scadenza dell'installazione.  

- **Imposta la scadenza per i riavvii in sospeso (giorni)**  
  - **Impostazione predefinita**:  Per impostazione predefinita, questa impostazione non è configurata, ma supporta un valore compreso tra **2** e **30**.  
  - **Documentazione di riferimento di Windows**: [Update/EngagedRestartDeadline](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Specifica un numero massimo di giorni di attesa dall'inizio del comportamento di riavvio in caso di occupato, prima che il dispositivo imponga un riavvio obbligatorio. Agli utenti sarà richiesto il riavvio del dispositivo per salvare il lavoro.

### <a name="delivery-optimization-download-mode"></a>Modalità di download con ottimizzazione recapito  

- **Impostazione predefinita**:  Non applicabile
- **Documentazione di riferimento di Windows**: *Non applicabile*

L’ottimizzazione del recapito non viene più configurata nell’ambito di un anello di aggiornamento di Windows 10 durante l’esecuzione della funzionalità Aggiornamenti software. L’ottimizzazione del recapito ora viene impostata tramite la configurazione del dispositivo. Tuttavia, le configurazioni precedenti rimangono disponibili nella console. È possibile rimuovere le configurazioni precedenti impostandole su *Non configurato*. Non è tuttavia possibile modificarle in altro modo. 

Per evitare conflitti tra criteri nuovi e precedenti, vedere [Passare dagli anelli di aggiornamento esistenti a ottimizzazione recapito](https://docs.microsoft.com/en-us/intune/delivery-optimization-windows#move-from-existing-update-rings-to-delivery-optimization) e quindi spostare le impostazioni in un profilo di ottimizzazione recapito.


