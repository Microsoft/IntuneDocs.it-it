---
title: Gestione del servizio DEP di Apple per i dispositivi iOS
description: Per gestire i dispositivi Apple, distribuire un profilo di registrazione che registri i dispositivi iOS acquistati tramite Device Enrollment Program (DEP) in modalità wireless.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 03/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 383309944bd185ea2abc79b3bcc3488ad3377b50
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-corporate-owned-device-enrollment-program-ios-devices"></a>Registrare i dispositivi IOS di proprietà dell'azienda usando il programma di registrazione dispositivi (DEP)

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune può distribuire un profilo di registrazione che registra in modalità wireless i dispositivi iOS acquistati tramite il programma di registrazione dispositivi (DEP). Il pacchetto di registrazione può includere opzioni di Assistente configurazione per il dispositivo.

>[!NOTE]
>La registrazione DEP non può essere usata con il metodo del [manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).
>Se gli utenti registrano i dispositivi iOS (ad esempio tramite l'app Portale aziendale) e i numeri di serie di tali dispositivi vengono poi importati con corrispondente assegnazione di un profilo DEP, la registrazione del dispositivo in Intune verrà annullata.
> Il programma di registrazione dei dispositivi non è attualmente supportato dai dispositivi macOS.

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-dep-management"></a>Prerequisiti per la registrazione di dispositivi iOS tramite la gestione del servizio DEP di Apple

- [Installare un certificato APN](set-up-ios-and-mac-management-with-microsoft-intune.md)

- L'organizzazione deve aderire al servizio DEP di Apple e ottenere i dispositivi tramite il programma. I dettagli del processo sono disponibili all'indirizzo: [https://deploy.apple.com](https://deploy.apple.com). I vantaggi del programma includono la configurazione dei dispositivi senza intervento dell'utente e senza dover connettere ogni dispositivo a un computer tramite un cavo USB.

- Per registrare i dispositivi iOS di proprietà dell'azienda con DEP, è necessario un token DEP di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi di proprietà dell'azienda che partecipano al programma DEP. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

## <a name="steps-to-enroll-ios-devices-by-using-apple-dep-management"></a>Passaggi per la registrazione di dispositivi iOS tramite la gestione del servizio DEP di Apple

La procedura seguente descrive come registrare i dispositivi iOS al primo utilizzo usando la gestione del servizio DEP di Apple. Poiché i dispositivi vengono aggiunti e rimossi dall'organizzazione, è probabile che alcuni passaggi, ad esempio l'aggiunta o la rimozione dei numeri di serie, vengano ripetuti, come descritto di seguito.

### <a name="get-an-encryption-key"></a>Ottenere una chiave di crittografia

1. Come utente amministratore, aprire la [console di amministrazione di Microsoft Intune](https://manage.microsoft.com), andare a **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **iOS** &gt; **Programma di registrazione dispositivi** e scegliere **Scarica chiave di crittografia**.

2. Salvare il file della chiave di crittografia (con estensione pem) localmente. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.

![Aggiornare un token del programma di registrazione dispositivi](../media/dev-sa-ios-dep.png)

### <a name="get-a-device-enrollment-program-token"></a>Ottenere un token del programma di registrazione dispositivi

1. Aprire il [portale di Apple Device Enrollment Program](https://deploy.apple.com) (https://deploy.apple.com)) e accedere con l'ID Apple aziendale. Lo stesso ID Apple dovrà essere usato in futuro per rinnovare il token DEP.

2. Nel portale del programma di registrazione dispositivi passare a **Programma di registrazione dei dispositivi** &gt; **Gestisci server** e quindi scegliere **Aggiungi server MDM**.

3. Immettere il **nome del server MDM** e scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.

4. Si apre la finestra di dialogo **Aggiungi &lt;NomeServer&gt;**. Fare clic su **Scegli file** per caricare il file PEM e scegliere **Avanti**.

5. La finestra di dialogo **Aggiungi &lt;Nome Server&gt;** include un collegamento al **Token del server**. Scaricare il file token del server (con estensione p7m) nel computer e fare clic su **Fine**.

   Questo file del certificato (.p7m) viene usato per stabilire una relazione di trust tra i server di Intune e del programma di registrazione dispositivi di Apple.

### <a name="add-the-dep-token-to-intune"></a>Aggiungere il token DEP a Intune

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) passare a **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **iOS** &gt; **Programma di registrazione dispositivi**.

2. Scegliere **Carica token DEP**. **Individuare** il file del certificato (con estensione p7m), immettere l'**ID Apple** e scegliere **Carica**.

### <a name="add-the-corporate-device-enrollment-policy"></a>Aggiungere il criterio Registrazione di dispositivi aziendali

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) passare a **Criteri** &gt; **Registrazione di dispositivi aziendali** e scegliere **Aggiungi**.

2. Specificare le informazioni **generali** includendo **Nome** e **Descrizione** e indicare se i dispositivi assegnati al profilo hanno affinità utente o appartengono a un gruppo:

   - **Richiedi affinità utente**: il dispositivo deve essere associato a un utente durante la configurazione iniziale per poter accedere ai dati aziendali e alla posta elettronica con il nome utente. **Affinità utente** deve essere configurata per i dispositivi gestiti tramite DEP che appartengono a utenti che devono usare il portale aziendale, ad esempio per installare app. L'autenticazione a più fattori non funziona durante la registrazione nei dispositivi DEP con affinità utente. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto in questi dispositivi. Per i nuovi utenti a cui è richiesto di modificare la password al primo accesso non è possibile richiedere la password durante la registrazione nei dispositivi DEP. Agli utenti con password scadute, inoltre, non verrà richiesto di reimpostare la password durante la registrazione DEP e devono reimpostarla da un dispositivo diverso.

     >[!NOTE]
     >DEP con affinità utente richiede un [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) per essere abilitato a richiedere token utente. [Altre informazioni su WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

   - **Nessuna affinità utente**: il dispositivo non è associato a un utente. Usare questa associazione per dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.

   È anche possibile **assegnare dispositivi ai gruppi seguenti**. Fare clic su **Seleziona** per scegliere un gruppo.

   > [!Important]
   > Le assegnazioni dei gruppi vengono trasferite da Intune ad Azure Active Directory. Dopo che l'account Intune ha ricevuto l'aggiornamento, l'opzione **Assegna dispositivi ai gruppi seguenti** non è più visibile. [Altre informazioni](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments).

3. Abilitare **Configura le impostazioni del programma di registrazione dispositivi per questo criterio** per supportare il programma di registrazione dei dispositivi.

      ![Riquadro di Assistente configurazione](../media/pol-sa-corp-enroll.png)

   Per i dispositivi gestiti da DEP sono disponibili le seguenti impostazioni:

   - **Reparto**: viene visualizzata quando gli utenti toccano **Informazioni configurazione** durante l'attivazione.
   - **Numero di telefono per supporto tecnico**: viene visualizzata quando l'utente fa clic sul pulsante **Richiesta di assistenza** durante l'attivazione.
   - **Modalità di preparazione**: viene impostata durante l'attivazione e non può essere modificata senza ripristinare le impostazioni predefinite del dispositivo:
       - **Supervisione non eseguita**: capacità di gestione limitate.
       - **Supervisione eseguita**: attiva altre opzioni di gestione e disattiva il blocco attivazione per impostazione predefinita.
   - **Bloccare il profilo di registrazione nel dispositivo**: viene configurata durante l'attivazione e può essere modificata solo ripristinando le impostazioni predefinite.
       - **Disattiva**: consente la rimozione del profilo di gestione dal menu **Impostazioni**.
       - **Abilita**: richiede **Modalità di preparazione** = **Supervisione eseguita**. Disattiva l'opzione del menu delle impostazioni di iOS per la rimozione del profilo di gestione
   - **Opzioni dell'assistente di configurazione**: queste impostazioni facoltative possono essere configurate in un secondo momento nel menu **Impostazioni** di iOS.
     - **Passcode**: consente di richiedere un passcode durante l'attivazione. Richiedere sempre un passcode, a meno che il dispositivo non sia protetto o l'accesso al dispositivo non venga controllato in un altro modo, ad esempio con la modalità tutto schermo, che limita l'uso del dispositivo a una sola app
       - **Servizi di posizione**: se l'opzione è abilitata, Assistente configurazione richiede il servizio al momento dell'attivazione.
       - **Ripristina**: se l'opzione è abilitata, Assistente configurazione richiede il backup in iCloud durante l'attivazione.
       - **ID Apple**: se l'opzione è abilitata, iOS richiede agli utenti un ID Apple quando Intune prova a installare un'applicazione senza ID. È necessario un ID Apple per il download delle app da iOS App Store, incluse le app installate da Intune.
       - **Terms and Conditions** (Termini e condizioni): se l'opzione è abilitata, Assistente configurazione richiede di accettare i termini e condizioni Apple durante l'attivazione.
       - **ID tocco**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
       - **Apple Pay**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
       - **Zoom**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
       - **Siri**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
       - **Invia i dati di diagnostica ad Apple**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
   - **Abilita la gestione di Apple Configurator**: se impostata su **Non consentire**, evita la sincronizzazione di file con iTunes o la gestione tramite Apple Configurator. È consigliabile scegliere **Non consentire**, esportare altre configurazioni da Apple Configurator e distribuire come profilo di configurazione iOS personalizzato con Intune invece di usare questa impostazione per consentire la distribuzione manuale con o senza un certificato.
      - **Non consentire**: impedisce al dispositivo di comunicare tramite USB (disattiva l'associazione).
      - **Consenti**: consente al dispositivo di comunicare tramite una connessione USB a qualsiasi PC o Mac.
      - **Richiedi certificato**: consente l'associazione a un Mac con un certificato importato nel profilo di registrazione.

### <a name="assign-the-profile-to-devices"></a>Assegnare il profilo ai dispositivi

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) passare a **Criteri** &gt; **Registrazione di dispositivi aziendali** e quindi scegliere **Assegna**.

2. Scegliere i dispositivi a cui si vuole assegnare il profilo creato. È possibile scegliere **Tutti i dispositivi** o selezionare dispositivi specifici e quindi selezionare **Aggiungi**.

> [!Important]
> Poiché Intune consente attualmente di definire un profilo di registrazione dei dispositivi "predefinito", i nuovi numeri di serie vengono assegnati automaticamente al profilo predefinito quando si esegue la sincronizzazione dei nuovi numeri di serie con il servizio DEP di Apple. In futuro, quando verrà eseguita la migrazione del tenant nel nuovo portale di Azure, non sarà più possibile impostare un profilo predefinito e assegnare automaticamente i numeri di serie al profilo. Sarà necessario assegnare manualmente i numeri di serie a un profilo specifico. [Altre informazioni](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios)

### <a name="assign-dep-devices-for-management"></a>Assegnare dispositivi DEP per la gestione

1. Aprire il [portale di Apple Device Enrollment Program](https://deploy.apple.com) (https://deploy.apple.com)) e accedere con l'ID Apple aziendale.

2. Passare a **Programma di distribuzione** &gt; **Programma di registrazione dispositivi** &gt; **Gestione dei dispositivi**.

3. Specificare come **scegliere i dispositivi**, fornire le informazioni sul dispositivo e specificare i dettagli in base al **Numero di serie**del dispositivo, al **Numero dell'ordine**o **caricando un file CSV**.

4. Scegliere **Assegna al server**, selezionare il &lt;nome del server&gt; specificato per Microsoft Intune e fare clic su **OK**.

### <a name="synchronize-dep-managed-devices"></a>Sincronizzare i dispositivi gestiti da DEP

Questo passaggio consente di sincronizzare i dispositivi con il servizio DEP di Apple e di visualizzare i dispositivi nella console di Intune.

1. Come utente amministratore, aprire la [console di amministrazione di Microsoft Intune](https://manage.microsoft.com), passare ad **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **iOS** &gt; **Programma di registrazione dispositivi** e scegliere **Sincronizza**. Viene inviata una richiesta di sincronizzazione ad Apple.

2. Per visualizzare i dispositivi gestiti da DEP dopo la sincronizzazione, nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) passare a **Gruppi** &gt; **Tutti i dispositivi** &gt; **Dispositivi aziendali preregistrati** &gt; **Per numero di serie iOS**. Nell'area di lavoro **Per numero di serie iOS**, lo **Stato** per i dispositivi gestiti rimane "Non contattato" finché il dispositivo non viene acceso e non viene eseguito l'Assistente configurazione per la registrazione del dispositivo.

   Per soddisfare i requisiti Apple per volumi di traffico DEP accettabili, Intune impone le seguenti limitazioni:

   - Una sincronizzazione DEP completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna tutti i numeri di serie che Apple ha assegnato a Intune, anche se sono già stati sincronizzati in precedenza. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.

   - Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 10 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.

### <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

Ora è possibile distribuire i dispositivi di proprietà dell'azienda agli utenti. Quando un dispositivo iOS viene attivato, viene registrato per la gestione con Intune. Il limite per i dispositivi utente è valido per i dispositivi gestiti da DEP.

>[!NOTE]
>Se un utente tenta di registrare un dispositivo DEP ma ha superato il limite dei dispositivi, la registrazione non riuscirà senza alcun avviso all'utente.

## <a name="changes-to-intune-group-assignments"></a>Modifiche alle assegnazioni di gruppo di Intune

A partire dal mese di aprile 2017 la gestione dei gruppi di dispositivi passerà ad Azure Active Directory. Dopo la transizione a gruppi di Azure Active Directory, l'assegnazione dei gruppi non sarà più inclusa nelle opzioni del profilo di registrazione aziendale. Poiché questa modifica verrà implementata nel corso di diversi mesi, potrebbe non essere visibile immediatamente. Dopo il passaggio al nuovo portale, è possibile definire le assegnazioni di gruppi di dispositivi dinamici in base ai nomi dei profili di registrazione aziendali.

Durante la migrazione, per ogni gruppo di dispositivi Intune preassegnato da un profilo Registrazione di dispositivi aziendali, in Azure AD verrà creato un corrispondente gruppo di dispositivi dinamico basato sul nome del profilo Registrazione di dispositivi aziendali. I nuovi nomi di profilo presentano il formato *ProfiloRegistrazione:&lt;nome del profilo associato&gt;*. Questo processo assicura che i dispositivi già assegnati a un gruppo di dispositivi verranno registrati automaticamente nel gruppo con le app e i criteri distribuiti.

Questa creazione automatica di gruppi viene eseguita una sola volta, durante la migrazione dei gruppi. Dopo la migrazione, gli amministratori di Intune devono creare i gruppi mediante il portale di Azure. Per informazioni dettagliate sull'effetto di questa funzionalità sulla registrazione dei dispositivi iOS di proprietà dell'azienda, vedere [Changes to Automatic Grouping for Corporate Pre-enrolled iOS Devices](https://blogs.technet.microsoft.com/intunesupport/2017/04/19/changes-to-automatic-grouping-for-corporate-pre-enrolled-ios-devices/) (Modifiche al raggruppamento automatico per i dispositivi iOS aziendali preregistrati).

Vedere anche [Altre informazioni sui gruppi di Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).

### <a name="see-also"></a>Vedere anche
[Prerequisiti per la registrazione dei dispositivi](prerequisites-for-enrollment.md)
