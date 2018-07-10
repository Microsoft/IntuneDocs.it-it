---
title: Impostare l'autorità di gestione dei dispositivi mobili
titlesuffix: Microsoft Intune
description: Impostare l'autorità di gestione dei dispositivi mobili in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4c1902e319a862c9ffcda5068753f917bf8f4c3f
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232919"
---
# <a name="set-the-mobile-device-management-authority"></a>Impostare l'autorità di gestione dei dispositivi mobili

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'amministratore IT deve impostare un'autorità MDM prima che gli utenti possano registrare i dispositivi per la gestione.

Le configurazioni possibili sono:

- **Intune autonomo**: gestione solo cloud, che viene configurata tramite il portale di Azure. Include il set completo di funzionalità offerte da Intune. [Impostare l'autorità MDM nella console di Intune](#set-mdm-authority-to-intune).

- **Intune ibrido**: integrazione della soluzione cloud di Intune con System Center Configuration Manager. Intune viene configurato tramite la console di Configuration Manager. [Impostare l'autorità MDM in Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestione dei dispositivi mobili per Office 365**: integrazione di Office 365 con la soluzione cloud di Intune. Intune viene configurato dall'interfaccia di amministrazione di Office 365. Include un sottoinsieme delle funzionalità disponibili con Intune autonomo. Impostare l'autorità MDM nell'interfaccia di amministrazione di Office 365.

> [!IMPORTANT]
> In Configuration Manager versione 1610 o successiva e Microsoft Intune versione 1705 è possibile modificare l'autorità MDM senza dover contattare il supporto Microsoft e senza che sia necessario annullare la registrazione dei dispositivi gestiti esistenti e quindi eseguirla di nuovo. Per informazioni dettagliate, vedere [Cosa fare se si sceglie l'impostazione dell'autorità MDM sbagliata](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Impostare l'autorità MDM su Intune

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Selezionare l'intestazione arancione per aprire l’impostazione **Autorità di gestione dei dispositivi mobili**.
4. In **Autorità di gestione dei dispositivi mobili** scegliere una delle opzioni seguenti per l'autorità MDM:
   - **Autorità MDM Intune**
   - **Autorità MDM Configuration Manager**
   - **Nessuno**

   ![Immagine della schermata di impostazione dell’autorità di gestione dei dispositivi mobili di Intune](media/set-mdm-auth.png)

   Un messaggio indica che l'autorità MDM è stata impostata su Intune.

### <a name="workflow-of-intune-administration-ui"></a>Flusso di lavoro dell'interfaccia utente di amministrazione di Intune
Quando è abilitata la gestione dei dispositivi Android o Apple, Intune invia informazioni sul dispositivo e l'utente da integrare con i servizi di terze parti per la gestione dei rispettivi dispositivi.

Gli scenari con il consenso alla condivisione dei dati vengono inclusi se:
- Si abilita Android for Work.
- Si abilitano e caricano i certificati per le notifiche push MDM Apple.
- Si abilita uno dei servizi Apple, ad esempio Device Enrollment Program, School Manager o Volume Purchasing Program.

In ogni caso, il consenso è strettamente correlato all'esecuzione di un servizio di gestione dei dispositivi mobili, ad esempio per confermare che un amministratore IT ha autorizzato la registrazione di dispositivi Google o Apple. La documentazione da consultare per sapere quali informazioni vengono condivise quando vengono pubblicati i nuovi flussi di lavoro è disponibile nelle posizioni seguenti:
- [Dati inviati da Intune a Google](https://aka.ms/Data-intune-sends-to-google)
- [Dati inviati da Intune ad Apple](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>Considerazioni principali
Dopo il passaggio alla nuova autorità MDM, è probabile che vi sia un tempo di transizione (fino a otto ore) prima dell'archiviazione del dispositivo e della sua sincronizzazione con il servizio. È necessario configurare le impostazioni nella nuova autorità MDM (ibrida) per garantire che i dispositivi registrati continuino a essere gestiti e protetti dopo la modifica. 
- Dopo la modifica, i dispositivi devono connettersi al servizio, in modo che le impostazioni della nuova autorità MDM (Intune autonomo) sostituiscano le impostazioni esistenti nel dispositivo.
- Dopo aver cambiato l'autorità MDM, alcune impostazioni di base (ad esempio i profili) dell'autorità MDM precedente (Intune autonomo) rimarranno nel dispositivo per un massimo di sette giorni o fino a quando il dispositivo stesso non si connetterà al servizio per la prima volta. È consigliabile configurare le app e le impostazioni (criteri, profili, app e così via) nella nuova autorità MDM (ibrida) appena possibile e distribuire le impostazioni ai gruppi di utenti con utenti che hanno già dispositivi registrati. Non appena un dispositivo si connette al servizio dopo che l'autorità MDM è stata cambiata, riceve le nuove impostazioni dall'autorità MDM impedendo che vi siano vuoti nella gestione e protezione.
- Quando in Intune e in Configuration Manager sono presenti le stesse categorie di dispositivi, dopo il passaggio alla nuova autorità MDM le assegnazioni di categorie relative ai dispositivi non vengono applicate. Per continuare a usare tali categorie, è necessario aggiungere manualmente i dispositivi sottoposti a migrazione alle raccolte appropriate dopo che l'autorità MDM è cambiata e dopo che i dispositivi sono stati visualizzati nella console di Configuration Manager.
- Per i dispositivi senza utenti associati (generalmente con il Device Enrollment Program per dispositivi iOS o scenari di registrazione in massa) non viene eseguita la migrazione alla nuova autorità MDM. Per tali dispositivi è necessario chiamare il supporto tecnico per chiedere assistenza nel passaggio alla nuova autorità MDM.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>Preparare il passaggio all'autorità MDM in Configuration Manager

Esaminare le informazioni seguenti per preparare il passaggio alla nuova autorità MDM:
- Perché sia disponibile l'opzione per cambiare l'autorità MDM è necessario disporre di Configuration Manager 1610 o versioni successive.
- Prima che un dispositivo si connetta al servizio dopo il passaggio alla nuova autorità MDM possono trascorrere fino a otto ore.
- Creare una raccolta di utenti di Configuration Manager con tutti gli utenti attualmente gestiti da Intune autonomo. Questa raccolta verrà usata al momento della configurazione della sottoscrizione a Intune nella console di Configuration Manager. Questo contribuisce ad assicurare che l'utente e i suoi dispositivi abbiano una licenza di Configuration Manager e siano gestiti nell'ambiente ibrido dopo il passaggio alla nuova autorità MDM.
- Assicurarsi che anche l'utente amministratore IT si trovi in questa raccolta di utenti.  
- Prima della modifica, l'autorità MDM sarà indicata come **Impostata su Microsoft Intune** (autonomo) nella console di amministrazione di Intune.
- Prima della modifica dell'autorità MDM, per essa nella console di amministrazione di Microsoft Intune deve comparire **Impostata su Microsoft Intune** (tenant autonomo).
    > [!NOTE]    
    > Se l'autorità MDM visualizza **Managed by Intune and Office 365** (Gestito da Intune e Office 365) e si cambia l'autorità MDM in **Configuration Manager** (ibrida), i dispositivi MDM gestiti da Office 365 non vengono più gestiti. Si consiglia di assegnare agli utenti licenze di Intune o Enterprise Mobility Suite prima di cambiare l'autorità MDM.   

- Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) rimuovere il ruolo Manager di registrazione dispositivi. Per altre informazioni, vedere [Eliminare un manager di registrazione dispositivi da Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune).
- Disattivare tutti i mapping di gruppi di dispositivi configurati. Per altre informazioni, vedere [Categorize devices with device group mapping in Microsoft Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune) (Classificare i dispositivi con mapping di gruppi di dispositivi in Microsoft Intune).
- Durante il cambiamento nell'autorità MDM non vi sarà alcun impatto visibile sugli utenti finali. Tuttavia è consigliabile comunicare questa modifica agli utenti per assicurarsi che i loro dispositivi siano accesi e si connettono con il servizio subito dopo la modifica. Ciò garantisce che, appena possibile, verrà connesso e registrato al servizio il numero massimo di dispositivi tramite la nuova autorità.
- Se si usa Intune autonomo per gestire i dispositivi iOS prima di cambiare l'autorità MDM, è necessario assicurarsi che lo stesso certificato del servizio Apple Push Notification (APN) utilizzato in precedenza in Intune sia rinnovato e utilizzato per configurare nuovamente il tenant Configuration Manager (ibrido).    

    > [!IMPORTANT]  
    > Se si usa un altro certificato APN per il sistema ibrido, viene annullata la registrazione di TUTTI i dispositivi iOS registrati in precedenza ed è necessario ripetere la procedura di registrazione. Prima di cambiare l'autorità MDM, assicurarsi di sapere esattamente quale certificato APN è stato usato per gestire i dispositivi iOS in Intune. Individuare lo stesso certificato elencato nel portale Apple Push Certificates (https://identity.apple.com)) e assicurarsi che l'utente il cui ID Apple è stato usato per creare il certificato APN originale sia identificato e disponibile per rinnovare gli stessi certificati APN come parte del passaggio alla nuova autorità MDM.

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Cambiare l'autorità MDM in Configuration Manager

1. Nella console di Configuration Manager passare ad **Amministrazione** &gt; **Panoramica** &gt; **Servizi cloud** &gt; **Sottoscrizione a Microsoft Intune** e scegliere di aggiungere una sottoscrizione a Intune.
2. Accedere al tenant di Intune usato al momento della configurazione originaria dell'autorità MDM in Intune e fare clic su **Avanti**.
3. Selezionare **Cambia l'autorità MDM in Configuration Manager** e fare clic su **Avanti**.
4. Selezionare la raccolta di utenti contenente tutti gli utenti che continueranno a essere gestiti dalla nuova autorità MDM ibrida.
5. Fare clic su **Avanti** e completare la procedura guidata. L'autorità MDM ora è cambiata in **Configuration Manager**.
6. Eseguire l'accesso alla [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) usando lo stesso tenant di Intune e verificare che l'autorità MDM ora corrisponda a **Imposta su Configuration Manager**.
7. Dopo aver modificato l'autorità MDM impostandola su Configuration Manager, è possibile configurare la [registrazione iOS](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/enroll-hybrid-ios-mac) e la [registrazione Android](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/enroll-hybrid-android).
8. Nella console di Configuration manager configurare e distribuire le nuove impostazioni e app dalla nuova autorità MDM (ibrido).

Alla successiva connessione al servizio, i dispositivi saranno sincronizzati e riceveranno le nuove impostazioni dalla nuova autorità MDM.

## <a name="change-mdm-authority-to-office-365"></a>Cambiare l'autorità MDM in Office 365

Per attivare la gestione dei dispositivi mobili di Office 365 nel servizio Intune Service esistente, passare a [https://protection.office.com](https://protection.office.com), scegliere **Prevenzione della perdita di dati** > **Criteri di sicurezza dei dispositivi** > **Visualizza l'elenco dei dispositivi gestiti** > **Inizia**.

Per altre informazioni, vedere [Configurare Gestione di dispositivi mobili in Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Se si vuole che gli utenti finali siano gestiti solo con Office 365 MDM, rimuovere qualsiasi licenza di Intune e/o EMS assegnata dopo l'attivazione di Office 365 MDM.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Pulizia dei dispositivi mobili dopo la scadenza del certificato MDM

Il certificato MDM viene rinnovato automaticamente quando i dispositivi mobili comunicano con il servizio Intune. In caso di cancellazione dei dispositivi mobili o se questi non riescono a comunicare con il servizio Intune per un determinato periodo di tempo, il certificato MDM non verrà rinnovato. Il dispositivo viene rimosso dal portale di Azure 180 giorni dopo la scadenza del certificato MDM.

## <a name="remove-mdm-authority"></a>Rimuovere l'autorità MDM

Non è possibile reimpostare l'autorità MDM su Sconosciuto. L'autorità MDM è usata dai server Microsoft per determinare il portale di registrazione dei dispositivi a cui fare riferimento (Configuration Manager, Intune di Azure, Office 365 MDM).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>Conseguenze della modifica dell'autorità MDM

- Quando il servizio Intune rileva che l'autorità MDM di un tenant è cambiata, invia un messaggio di notifica a tutti i dispositivi registrati perché eseguano l'archiviazione e la sincronizzazione con il servizio (al di fuori delle normali archiviazioni pianificate). Di conseguenza, dopo la modifica dell'autorità MDM per il tenant da Intune autonomo a ibrida, tutti i dispositivi accesi e online si connetteranno al servizio e riceveranno la nuova autorità MDM. Da quel momento saranno gestiti in modo ibrido. La gestione e la protezione di questi dispositivi non viene mai interrotta.
- Anche se i dispositivi sono accesi e online durante (o immediatamente dopo) la modifica nell'autorità MDM, ci sarà un ritardo massimo di otto ore (a seconda del momento della successiva archiviazione periodica pianificata) prima che i dispositivi siano registrati per il servizio con la nuova autorità MDM.    

  > [!IMPORTANT]    
  > Tra il momento in cui si cambia l'autorità MDM e quello in cui viene caricato il certificato rinnovato del servizio APN per la nuova autorità, le nuove registrazioni e le nuove archiviazioni di dispositivi iOS hanno esito negativo. Pertanto è importante analizzare e caricare il certificato APN per la nuova autorità al più presto dopo la modifica nell'autorità MDM.

- Gli utenti possono passare rapidamente alla nuova autorità MDM avviando manualmente un'archiviazione dal dispositivo al servizio. Gli utenti possono farlo facilmente usando l'app del portale aziendale e avviando un controllo di conformità del dispositivo.
- Per verificare che tutto funzioni correttamente dopo che i dispositivi sono stati archiviati e sincronizzati con il servizio dopo la modifica dell'autorità MDM, cercare i dispositivi nella console di amministrazione di Configuration Manager. I dispositivi precedentemente gestiti da Intune vengono ora visualizzati come dispositivi gestiti nella console di Configuration Manager.    
- Quando un dispositivo è offline durante la modifica nell'autorità MDM e quando il dispositivo viene archiviato nel servizio si ha una situazione intermedia. Per garantire la protezione e il funzionamento del dispositivo durante questo periodo, i profili riportati di seguito rimarranno nel dispositivo per un massimo di sette giorni o fino a quando il dispositivo non si connetterà alla nuova autorità MDM e non riceverà le nuove impostazioni, che sovrascriveranno quelle esistenti.
    - Profilo di posta elettronica
    - Profilo VPN
    - Profilo certificato
    - Profilo Wi-Fi
    - Profili di configurazione
- Dopo il passaggio alla nuova autorità MDM, i dati di conformità nella console di amministrazione di Microsoft Intune possono richiedere fino a una settimana per un reporting preciso. Tuttavia, gli stati di conformità in Azure Active Directory e nel dispositivo sono accurati. Il dispositivo, quindi, è comunque protetto.
- Verificare che le nuove impostazioni che devono sovrascrivere quelle esistenti abbiano lo stesso nome delle precedenti per garantire che le impostazioni precedenti vengano sovrascritte. In caso contrario, i dispositivi potrebbero finire con criteri e profili ridondanti.    

  > [!TIP]    
  > Come procedura consigliata è necessario creare tutte le impostazioni di gestione e le configurazioni, nonché le distribuzioni, subito dopo aver completato la modifica dell'autorità MDM. Questo contribuisce a garantire la protezione e la gestione attiva dei dispositivi durante il periodo intermedio.

-  Dopo aver modificato l'autorità MDM, eseguire la procedura seguente per verificare che i nuovi dispositivi siano registrati correttamente con la nuova autorità:   
    - Registrare un nuovo dispositivo
    - Verificare che il dispositivo appena registrato sia presente nella console di Configuration Manager.
    - Eseguire un'azione, ad esempio il blocco remoto, dalla console di amministrazione al dispositivo. Se l'azione ha esito positivo, il dispositivo è gestito dalla nuova autorità MDM.
- Nel caso di problemi con dispositivi specifici, è possibile annullare e ripetere la registrazione dei dispositivi in modo che siano connessi alla nuova autorità e gestiti il più rapidamente possibile.

## <a name="next-steps"></a>Passaggi successivi

Con il set di autorità MDM, è possibile iniziare la [registrazione dei dispositivi](device-enrollment.md).