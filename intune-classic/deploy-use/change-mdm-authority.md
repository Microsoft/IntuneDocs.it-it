---
title: "Cambiare l'autorità MDM in Configuration Manager (MDM ibrida)"
description: "Informazioni su come modificare l'autorità MDM da Intune autonoma a Configuration Manager (MDM ibrida)"
keywords: 
author: dougeby
manager: angrobe
ms.date: 05/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f1b4bce3-7932-4a0d-aa92-6dacc7060f42
ms.reviewer: 
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 816aa3effc8be66844000394f27eacc4215c1bc2
ms.sourcegitcommit: 94177ee8bc9f2fe448738773757e40d799f71c18
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
---
# <a name="change-the-mdm-authority"></a>Cambiare l'autorità MDM
A partire dalla versione 1610 di Configuration Manager, è possibile cambiare l'autorità MDM senza contattare il supporto tecnico Microsoft e senza dover annullare e ripetere la registrazione dei dispositivi gestiti esistenti. Questo argomento illustra la procedura da seguire per cambiare un tenant di Microsoft Intune esistente configurato da Intune e con l'autorità MDM impostata su **Microsoft Intune** (autonomo) a **Configuration Manager** (MDM ibrida) senza dover annullare e ripetere la registrazione dei dispositivi gestiti esistenti.

> [!Note]    
> Se si vuole cambiare un tenant di Microsoft Intune esistente configurato dalla console di Configuration Manager (ibrida) e con l'autorità MDM impostata su **Configuration Manager** (ibrida) a **Microsoft Intune** autonomo, vedere [Cambiare l'autorità MDM da Configuration Manager (MDM ibrida) a Intune autonomo](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority). 


### <a name="key-considerations"></a>Considerazioni principali
Dopo il passaggio alla nuova autorità MDM, è probabile che vi sia un tempo di transizione (fino a otto ore) prima dell'archiviazione del dispositivo e della sua sincronizzazione con il servizio. Sarà necessario configurare le impostazioni nella nuova autorità MDM (ibrido) per garantire che i dispositivi registrati continueranno a essere gestiti e protetti dopo la modifica. . Tieni presente quanto segue:
- I dispositivi devono connettersi con il servizio dopo la modifica, in modo che le impostazioni dalla nuova autorità MDM (Intune autonomo) sostituiscano le impostazioni esistenti nel dispositivo.
- Dopo aver cambiato l'autorità MDM, alcune delle impostazioni di base (ad esempio i profili) dall'autorità MDM precedente (Intune autonomo) rimarranno sul dispositivo fino a 7 giorni o fino a quando il dispositivo si connetterà al servizio per la prima volta. Si consiglia di configurare le app e le impostazioni (criteri, profili, app e così via) nella nuova autorità MDM (ibrido) appena possibile e distribuire le impostazioni ai gruppi di utenti contenenti gli utenti che hanno dispositivi registrati esistenti. Non appena un dispositivo si connette al servizio dopo che l'autorità MDM è stata cambiata, riceve le nuove impostazioni dall'autorità MDM impedendo che vi siano vuoti nella gestione e protezione.
- Per i dispositivi senza utenti associati (generalmente con il Device Enrollment Program per dispositivi iOS o scenari di registrazione in massa) non viene eseguita la migrazione alla nuova autorità MDM. Per tali dispositivi è necessario chiamare il supporto tecnico per chiedere assistenza nel passaggio alla nuova autorità MDM.

### <a name="prepare-to-change-the-mdm-authority-to-configuration-manager-hybrid"></a>Preparare il passaggio all'autorità MDM in Configuration Manager (ibrido)
Esaminare le informazioni seguenti per preparare il passaggio alla nuova autorità MDM:
- Perché sia disponibile l'opzione per cambiare l'autorità MDM è necessario disporre di Configuration Manager 1610 o versioni successive.
- Prima che un dispositivo si connetta al servizio dopo il passaggio alla nuova autorità MDM possono trascorrere fino a otto ore.
- Creare una raccolta di utenti di Configuration Manager con tutti gli utenti attualmente gestiti da Intune autonomo, che verrà usata quando si configurerà la sottoscrizione a Intune nella console di Configuration Manager. Questo contribuirà ad assicurare che l'utente e i suoi dispositivi abbiano una licenza di Configuration Manager assegnata e siano gestiti nell'ambiente ibrido dopo il passaggio all'autorità MDM.
- Assicurarsi che anche l'utente amministratore IT si trovi in questa raccolta di utenti.  
- Prima della modifica, l'autorità MDM sarà indicata come **Impostata su Microsoft Intune** (autonomo) nella console di amministrazione di Intune.
- Prima della modifica dell'autorità MDM, per essa nella console di amministrazione di Microsoft Intune deve comparire **Impostata su Microsoft Intune** (tenant autonomo).
    > [!NOTE]    
    > Se per l'autorità MDM compare **Managed by Intune and Office 365** (Gestito da Intune e Office 365), i dispositivi MDM gestiti da Office 365 non saranno più gestiti quando si cambia l'autorità MDM in **Configuration Manager** (ibrido). Si consiglia di assegnare agli utenti licenze di Intune o Enterprise Mobility Suite prima di cambiare l'autorità MDM.   

- Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) rimuovere il ruolo Manager di registrazione dispositivi. Per altre informazioni, vedere [Eliminare un manager di registrazione dispositivi da Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune).
- Disattivare tutti i mapping di gruppi di dispositivi configurati. Per altre informazioni, vedere [Categorize devices with device group mapping in Microsoft Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune) (Classificare i dispositivi con mapping di gruppi di dispositivi in Microsoft Intune).
- Durante il cambiamento nell'autorità MDM non vi sarà alcun impatto visibile sugli utenti finali. Tuttavia è consigliabile comunicare questa modifica agli utenti per assicurarsi che i loro dispositivi siano accesi e si connettono con il servizio subito dopo la modifica. Ciò garantisce che, appena possibile, verrà connesso e registrato al servizio il numero massimo di dispositivi tramite la nuova autorità.
- Se si usa Intune autonomo per gestire i dispositivi iOS prima di cambiare l'autorità MDM, è necessario assicurarsi che lo stesso certificato del servizio Apple Push Notification (APN) utilizzato in precedenza in Intune sia rinnovato e utilizzato per configurare nuovamente il tenant Configuration Manager (ibrido).    

    > [!IMPORTANT]  
    > Se si usa un altro certificato APN per il sistema ibrido, viene annullata la registrazione di TUTTI i dispositivi iOS registrati in precedenza ed è necessario ripetere la procedura di registrazione. Prima di cambiare l'autorità MDM, assicurarsi di sapere esattamente quale certificato APN è stato usato per gestire i dispositivi iOS in Intune. Individuare lo stesso certificato elencato nel portale Apple Push Certificates (https://identity.apple.com) e assicurarsi che l'utente il cui ID Apple è stato usato per creare il certificato APN originale sia identificato e disponibile per rinnovare gli stessi certificati APN come parte del passaggio alla nuova autorità MDM.  

### <a name="change-the-mdm-authority-to-configuration-manager"></a>Cambiare l'autorità MDM in Configuration Manager
Il processo per cambiare l'autorità MDM in Configuration Manager (ibrido) include i passaggi generali seguenti:  
- Nella console di Configuration Manager aggiungere la sottoscrizione a Microsoft Intune.
- Configurare il certificato APN Apple usando lo stesso certificato APN che è stato rinnovato.
- Nella console di Configuration manager configurare e distribuire le nuove impostazioni e app dalla nuova autorità MDM (ibrido).
- Alla successiva connessione al servizio, i dispositivi saranno sincronizzati e riceveranno le nuove impostazioni dalla nuova autorità MDM.

#### <a name="to-change-the-mdm-authority-to-configuration-manager"></a>Per cambiare l'autorità MDM in Configuration Manager
1. Nella console di Configuration Manager passare ad **Amministrazione** &gt; **Panoramica** &gt; **Servizi cloud** &gt; **Sottoscrizione a Microsoft Intune** e scegliere di aggiungere una sottoscrizione a Intune.
2. Accedere al tenant di Intune utilizzato in origine quando è stata configurata l'autorità MDM in Intune e fare clic su **Avanti**.
3. Selezionare **Cambia l'autorità MDM in Configuration Manager** e fare clic su **Avanti**.
4. Selezionare la raccolta di utenti contenente tutti gli utenti che continueranno a essere gestiti dalla nuova autorità MDM ibrida.
5. Fare clic su **Avanti** e completare la procedura guidata. L'autorità MDM ora è cambiata in **Configuration Manager**.
6. Eseguire l'accesso alla [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) usando lo stesso tenant di Intune e verificare che l'autorità MDM sia ora **Impostata su Configuration Manager**.


### <a name="enable-ios-enrollment"></a>Abilita registrazione iOS
Quando si usano dispositivi iOS è necessario configurare il certificato APN in Configuration Manager.

#### <a name="to-enable-ios-enrollment-and-configure-the-apns-certificate"></a>Per abilitare la registrazione iOS e configurare il certificato APN

1. **Scaricare una richiesta di firma del certificato**

    1. Nella console di Configuration Manager passare ad **Amministrazione** &gt; **Servizi cloud** &gt; **Sottoscrizioni a Microsoft Intune** e selezionare **Crea richiesta certificato per servizio APN** per aprire la finestra di dialogo **Richiesta di firma del certificato per il servizio Apple Push Notification**.  
    2. **Andare** al percorso per salvare il nuovo file di richiesta di firma del certificato (csr). Salvare il file della richiesta di firma del certificato (estensione csr) in locale.  
    3. Fare clic su **Scarica**. Il nuovo file CSR di Microsoft Intune viene scaricato e salvato da Configuration Manager.   

    > [!IMPORTANT]
    > È necessario scaricare una nuova richiesta di firma del certificato. Non usare un file esistente o l'operazione avrà esito negativo.  

2.  Passare al [portale Apple Push Certificates](http://go.microsoft.com/fwlink/?LinkId=269844) ed eseguire l'accesso con lo **stesso** ID Apple usato in precedenza per creare e rinnovare il certificato APN impiegato in Intune autonomo.

    ![Pagina di accesso al portale Apple Push Certificates](../media/mdm-change-apns-portal.png)

3. Selezionare il certificato APN utilizzato in Intune autonomo e quindi fare clic su **Rinnova**.

    ![Finestra di dialogo Renew APNs (Rinnova servizio APN)](../media/mdm-change-renew-apns.png)

4. Selezionare il file della richiesta di firma del certificato APN (.csr) che è stato scaricato localmente e fare clic su **Carica**.

    ![Pagina di accesso al portale Apple Push Certificates](../media/mdm-change-renew-apns-upload.png)
 
5. Selezionare lo stesso servizio APN e fare clic su **Scarica**. Scaricare il certificato APN (con estensione pem) e salvare il file in locale.  

    ![Pagina di accesso al portale Apple Push Certificates](../media/mdm-change-renew-apns-download.png)

6. Caricare il certificato APN rinnovato nel tenant ibrido usando lo stesso ID Apple di prima.

    1.  Nella console di Configuration Manager passare ad **Amministrazione** &gt; **Servizi cloud** &gt; **Sottoscrizione a Microsoft Intune** e scegliere **Configura piattaforme** &gt; **iOS**.  
    2.  Nella finestra di dialogo **Proprietà della sottoscrizione a Microsoft Intune** selezionare la scheda **Certificato di servizio APN** e fare clic per selezionare la casella di controllo **Abilita registrazione iOS e MAC OS X (MDM)**.  
    3.  Fare clic su **Sfoglia**e andare al file (con estensione CER) del certificato per il servizio APN scaricato da Apple. Configuration Manager visualizza le informazioni sul certificato APNs. Fare clic su **OK** per salvare il certificato APN in Intune.  

        ![Pagina delle proprietà della sottoscrizione a Intune - iOS](../media/mdm-change-subscription-properties-ios.png)

### <a name="enable-android-enrollment"></a>Abilitare la registrazione di Android
1. Nella console di Configuration Manager passare ad **Amministrazione** &gt; **Servizi cloud** &gt; **Sottoscrizione a Microsoft Intune** e scegliere **Configura piattaforme** &gt; **Android**.  
2. Selezionare **Abilita registrazione di Android** e fare clic su **OK**.

### <a name="enable-windows-enrollment"></a>Abilitare la registrazione di Windows
1. Nella console di Configuration Manager passare ad **Amministrazione** &gt; **Servizi cloud** &gt; **Sottoscrizione a Microsoft Intune** e scegliere **Configura piattaforme** &gt; **Windows**.  
2. Selezionare **Abilita registrazione Windows** e fare clic su **OK**.

### <a name="enable-windows-phone-enrollment"></a>Abilitare la registrazione di Windows Phone
1. Nella console di Configuration Manager passare ad **Amministrazione** &gt; **Servizi cloud** &gt; **Sottoscrizione a Microsoft Intune** e scegliere **Configura piattaforme** &gt; **Windows Phone**.  
2. Selezionare la piattaforma da abilitare e fare clic su **OK**.


### <a name="next-steps"></a>Passaggi successivi
Una volta completata la modifica dell'autorità MDM, esaminare i passaggi seguenti:
- Quando il servizio Intune rileva che l'autorità MDM di un tenant è cambiata, invia un messaggio di notifica a tutti i dispositivi registrati per l'archiviazione e la sincronizzazione con il servizio (questo avviene al di fuori delle archiviazioni periodiche pianificate). Di conseguenza, dopo che l'autorità MDM per il tenant è stata modificata da Intune autonomo a ibrida, tutti i dispositivi accesi e in linea si connetteranno con il servizio, riceveranno la nuova autorità MDM e da quel momento saranno gestiti in modo ibrido. Non ci saranno interruzioni alla gestione e protezione di questi dispositivi.
- Anche se i dispositivi sono accesi e online durante (o immediatamente dopo) la modifica nell'autorità MDM, ci sarà un ritardo massimo di otto ore (a seconda del momento della successiva archiviazione periodica pianificata) prima che i dispositivi siano registrati con il servizio mediante la nuova autorità MDM.    

  > [!IMPORTANT]    
  > Tra il momento in cui si cambia l'autorità MDM e quello in cui viene caricato il certificato APN rinnovato per la nuova autorità, le nuove registrazioni e archiviazioni di dispositivi iOS avranno esito negativo. Pertanto è importante analizzare e caricare il certificato APN per la nuova autorità al più presto dopo la modifica nell'autorità MDM.

- Gli utenti possono passare rapidamente alla nuova autorità MDM avviando manualmente un'archiviazione dal dispositivo al servizio. Gli utenti possono farlo facilmente usando l'app del portale aziendale e avviando un controllo di conformità del dispositivo.
- Per verificare che tutto funzioni correttamente dopo che i dispositivi sono stati archiviati e sincronizzati con il servizio dopo la modifica dell'autorità MDM, cercare i dispositivi nella console di amministrazione di Configuration Manager. I dispositivi che sono stati precedentemente gestiti da Intune verranno ora visualizzati come dispositivi gestiti nella console di Configuration Manager.    
- Quando un dispositivo è offline durante la modifica nell'autorità MDM e quando il dispositivo viene archiviato nel servizio si ha una situazione intermedia. Per garantire che il dispositivo rimanga protetto e funzionale durante questo periodo, gli elementi seguenti rimarranno sul dispositivo fino a 7 giorni (o fino a quando il dispositivo si connetterà con la nuova autorità MDM e riceverà le nuove impostazioni che sovrascriveranno quelle esistenti):
    - Profilo di posta elettronica
    - Profilo VPN
    - Profilo certificato
    - Profilo Wi-Fi
    - Profili di configurazione
- Dopo il passaggio alla nuova autorità MDM, i dati di conformità nella console di amministrazione di Microsoft Intune possono richiedere fino a una settimana per un reporting preciso. Tuttavia, gli stati di conformità in Azure Active Directory e nel dispositivo saranno accurati e il dispositivo sarà comunque protetto.
- Verificare che le nuove impostazioni che devono sovrascrivere quelle esistenti abbiano lo stesso nome delle precedenti per garantire che le impostazioni precedenti vengano sovrascritte. In caso contrario, i dispositivi potrebbero finire con criteri e profili ridondanti.    

  > [!TIP]    
  > Come procedura consigliata è necessario creare tutte le impostazioni di gestione e le configurazioni, nonché le distribuzioni, subito dopo aver completato la modifica dell'autorità MDM. Questo contribuirà a garantire che i dispositivi siano protetti e attivamente gestiti durante il periodo intermedio.

-  Dopo aver modificato l'autorità MDM, eseguire la procedura seguente per verificare che i nuovi dispositivi siano registrati correttamente con la nuova autorità:   
    - Registrare un nuovo dispositivo
    - Verificare che il dispositivo appena registrato sia presente nella console di Configuration Manager.
    - Eseguire un'azione, ad esempio il blocco remoto, dalla console di amministrazione al dispositivo. Se l'azione ha esito positivo, il dispositivo è gestito dalla nuova autorità MDM.
- Nel caso di problemi con dispositivi specifici, è possibile annullare e ripetere la registrazione dei dispositivi in modo che siano connessi alla nuova autorità e gestiti il più rapidamente possibile.