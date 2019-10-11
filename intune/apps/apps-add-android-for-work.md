---
title: Assegnare app Google Play gestite a dispositivi Android Enterprise
titleSuffix: Microsoft Intune
description: Informazioni su come sincronizzare e assegnare app ai dispositivi Android Enterprise dalla versione gestita di Google Play Store.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbcc777cc6d8b803c502d847114ef7cff04ceb26
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725335"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Aggiungere app Google Play gestite a dispositivi Android Enterprise con Intune

Google Play gestito è lo store di app aziendali di Google e l'unica origine di applicazioni per Android Enterprise. È possibile usare Intune per orchestrare la distribuzione di app tramite Google Play gestito per qualsiasi scenario Android Enterprise (incluso il profilo di lavoro e le registrazioni dedicate e completamente gestite). Il modo in cui si aggiungono le app Google Play gestite a Intune differisce dalla modalità con cui vengono aggiunte le app Android per i dispositivi non Android Enterprise. Le app dello Store, le app line-of-business (LOB) e le app Web sono approvate o aggiunte a Google Play gestito e quindi sincronizzate in Intune in modo che vengano visualizzate nell'elenco App client. Dopo l'aggiunta all'elenco App client, è possibile gestire l'assegnazione di tutte le app Google Play gestite allo stesso modo dell'assegnazione delle altre app.

Per facilitare la configurazione e l'uso delle funzionalità di gestione di Android Enterprise, dopo la connessione del tenant di Intune a Google Play gestito, Intune aggiunge automaticamente quattro app Android Enterprise correlate comuni alla console di amministrazione di Intune. Le quattro app sono le seguenti:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Usata per gli scenari di Android Enterprise completamente gestiti. Questa app viene installata automaticamente nei dispositivi completamente gestiti durante il processo di registrazione del dispositivo.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - Consente di accedere agli account se si usa la verifica a due fattori. Questa app viene installata automaticamente nei dispositivi completamente gestiti durante il processo di registrazione del dispositivo.
- **[Portale aziendale di Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Usare per gli scenari con criteri di protezione app e profili di lavoro di Android Enterprise.
- **[Schermata iniziale gestita](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** - Usata per gli scenari di più app dedicate in modalità tutto schermo Android Enterprise. Gli amministratori IT devono creare un'assegnazione per installare questa app in dispositivi dedicati che verranno usati in scenari di più app in modalità tutto schermo.

>[!NOTE]
>Quando un utente finale registra il dispositivo Android Enterprise completamente gestito, l'app Portale aziendale Intune viene installata automaticamente e l'icona dell'applicazione può essere visibile all'utente finale. Se l'utente finale tenta di avviare l'app Portale aziendale Intune, l'utente finale verrà reindirizzato all'app Microsoft Intune e l'icona dell'app Portale aziendale verrà successivamente nascosta.

## <a name="before-you-start"></a>Prima di iniziare
- Assicurarsi di aver connesso il tenant di Intune a Google Play gestito.  Per altre informazioni, vedere [Connettere l'account di Intune all'account di Google Play gestito](../enrollment/connect-intune-android-enterprise.md).
- Se si prevede di registrare dispositivi con profilo di lavoro, assicurarsi di avere configurato l'uso di Intune con i profili di lavoro Android nel carico di lavoro **Registrazione del dispositivo** del portale di Azure. Per altre informazioni, vedere [Registrare i dispositivi Android](../enrollment/android-work-profile-enroll.md).

>[!NOTE]
>Quando si lavora con Microsoft Intune, è consigliabile usare il browser Microsoft Edge o Google Chrome.

## <a name="managed-google-play-app-types"></a>Tipi di app Google Play gestite
Con Google Play gestito sono disponibili tre tipi di app:

* **App di Google Play Store gestite** - App pubbliche disponibili a livello generale in Play Store. Per gestire queste app in Intune, è possibile cercare le app da gestire, approvarle e quindi sincronizzarle in Intune.
* **App privata Google Play gestita** - Si tratta di app line-of-business pubblicate in Google Play gestito da amministratori di Intune.  Queste app sono private e sono disponibili solo per il tenant di Intune. Questo è il modo in cui le app line-of-business vengono gestite e distribuite con Google Play gestito e Android Enterprise.
* **Collegamento Web a Google Play gestito** - collegamenti Web con icone definite dall'amministratore IT che possono essere distribuiti nei dispositivi Android Enterprise. I collegamenti vengono visualizzati nei dispositivi nell'elenco delle app del dispositivo come le normali app.

## <a name="managed-google-play-store-apps"></a>App Google Play Store gestite
È possibile esplorare e approvare le app Google Play Store gestite con Intune in due modi:

1. Direttamente nella console di Intune: esplorare e approvare le app dello Store in una vista ospitata in Intune. La vista viene aperta direttamente nella console di Intune e non richiede una nuova autenticazione con un account diverso.
1. Nella console di Google Play gestito: è possibile aprire direttamente la console di Google Play gestito e approvare le app nella console. Per altre informazioni, vedere [Sincronizzare un'app della versione gestita di Google Play con Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).  Questa operazione un accesso separato con l'account usato per connettere il tenant di Intune a Google Play gestito.


### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>Aggiungere un'app Google Play Store gestita direttamente nella console di Intune

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client** > **App**.
5. Nel riquadro **App** selezionare **Aggiungi**.
6. Nella casella a discesa **Tipo di App** selezionare **Google Play gestito**.
7. Selezionare **Google Play gestito - Apri** per aprire il catalogo di Google Play gestito.
7. Selezionare **Search Play Store** (Cerca in Play Store) nel catalogo di Google Play.
8. Usare la casella di ricerca per cercare le app da gestire.
9. Fare clic su **Approva** per approvare l'app in Google Play gestito e fare clic su **Approva** per accettare le autorizzazioni dell'app.
10. Selezionare **Keep approved when app requests new permissions** (Mantieni approvazione quando l'app richiede nuove autorizzazioni) nella finestra Impostazioni di approvazione e quindi fare clic su **Salva**. Se non si sceglie questa opzione e lo sviluppatore dell'app pubblica un aggiornamento, è necessario approvare manualmente eventuali nuove autorizzazioni. Ciò causerà l'arresto delle installazioni e degli aggiornamenti dell'app finché le autorizzazioni non vengono approvate. Per questo motivo, è consigliabile selezionare l'opzione per l'approvazione automatica delle nuove autorizzazioni. 
11. Fare clic su **OK** per includere le app approvate.
12. Fare clic su **Sincronizza** nel riquadro **Aggiungi app** per eseguire la sincronizzazione con il servizio Google Play gestito.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>Aggiungere un'app Google Play Store gestita nella console di Google Play gestito (alternativa)
Se si vuole sincronizzare un'app di Google Play gestita con Intune anziché aggiungerla direttamente con Intune, seguire questa procedura.

> [!IMPORTANT]
> Le informazioni seguenti forniscono un metodo alternativo all'aggiunta di un'app di Google Play gestita con Intune, come descritto in precedenza.

1. Passare alla [versione gestita di Google Play Store](https://play.google.com/work). Accedere con lo stesso account usato per configurare la connessione tra Intune e Android Enterprise.
2. Cercare nello store l'app che si vuole assegnare usando Intune e selezionarla.
3. Nella pagina in cui è visualizzata l'app selezionare **Approva**.  
    Nell'esempio seguente è stata scelta l'app Microsoft Excel.

    ![Pulsante di approvazione nella versione gestita di Google Play Store](./media/apps-add-android-for-work/approve.png)

   Viene visualizzata una finestra per l'app in cui viene richiesto di concedere le autorizzazioni che consentono all'app di eseguire diverse operazioni.

4. Selezionare **Approva** per accettare le autorizzazioni per l'app e continuare.

    ![Pulsante Approva per le autorizzazioni per l'app](./media/apps-add-android-for-work/approve-app-permissions.png)

5. Selezionare un'opzione per gestire le nuove richieste di autorizzazioni per l'app e quindi selezionare **Salva**.

    ![Opzioni per gestire le nuove richieste di autorizzazioni per l'app](./media/apps-add-android-for-work/approve-app-settings.png)

    L'app viene approvata e visualizzata nella console di amministrazione IT. È quindi possibile [sincronizzare l'app con profilo di lavoro Android con Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).

## <a name="managed-google-play-private-lob-apps"></a>App line-of-business private di Google Play gestito

Le app line-of-business possono essere aggiunte a Google Play gestito in due modi:

1. Direttamente nella console di Intune: in questo modo è possibile aggiungere le app line-of-business inviando solo l'APK dell'app e un titolo direttamente in Intune. Questo metodo non richiede un account per sviluppatore Google e non richiede il pagamento della tariffa per la registrazione in Google come sviluppatore.  Questo metodo è più semplice e ha un numero significativamente ridotto di passaggi e rende disponibili le app line-of-business per la gestione in soli dieci minuti.
1. In Google Play Developer Console: se si dispone di un account per sviluppatore Google o si vuole configurare funzionalità di distribuzione avanzate disponibili solo in Google Play Developer Console (ad esempio l'aggiunta di ulteriori screenshot delle app), è possibile usare [Google Play Developer Console](https://play.google.com/apps/publish). 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Pubblicazione di app line-of-business private di Google Play gestito direttamente nella console di Intune

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client** > **App**.
5. Nel riquadro **App** selezionare **Aggiungi**.
6. Nella casella a discesa **Tipo di App** selezionare **Google Play gestito**.
7. Selezionare **Google Play gestito - Apri** per aprire il catalogo di Google Play gestito.
7. Selezionare **Private Apps** (App private) nel catalogo di Google Play.
7. Fare clic sul pulsante **"+"** per aggiungere una nuova app
8. Inviare un titolo e un pacchetto APK per l'app
9. Fare clic su **Crea**
9. Chiudere il riquadro di Google Play gestito dopo aver aggiunto le app desiderate
12. Fare clic su **Sincronizza** nel riquadro **Aggiungi app** per eseguire la sincronizzazione con il servizio Google Play gestito. Si noti che le app private potrebbero richiedere alcuni minuti per essere sincronizzate. Se non viene visualizzata la prima volta che si esegue una sincronizzazione, attendere qualche minuto e avviare una nuova sincronizzazione.

Per altre informazioni sulle app private di Google Play gestito, incluse le domande frequenti, vedere l'articolo del supporto tecnico di Google: https://support.google.com/googleplay/work/answer/9146439

>[!NOTE]
>Le app private aggiunte usando questo metodo non possono mai essere rese pubbliche. Usare questa opzione di pubblicazione solo se si è certi che questa app sarà sempre privata per l'organizzazione.
  

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Pubblicazione di app line-of-business private di Google Play gestito con Google Developer Console

1. Accedere a [Google Play Developer Console](https://play.google.com/apps/publish) con lo stesso account usato per configurare la connessione tra Intune e Android Enterprise.  
    Se si accede per la prima volta, è necessario registrarsi e pagare una quota per diventare membro del programma per gli sviluppatori Google.
2. Nella console selezionare **Add new application** (Aggiungi nuova applicazione).
3. Caricare e specificare informazioni sull'app allo stesso modo in cui si pubblicano le altre app in Google Play. È tuttavia necessario selezionare **Only make this application available to my organization (<*organization name*>)** (Rendi disponibile l'app soltanto per la mia organizzazione).

    ![Rendere disponibile l'app soltanto per la propria organizzazione](./media/apps-add-android-for-work/restrict.png)

    Questa operazione rende disponibile l'app soltanto per la propria organizzazione. Non sarà disponibile nel Google Play Store pubblico.

    Per altre informazioni sul caricamento e sulla pubblicazione di app Android, vedere la [Guida di Play Console di Google](https://support.google.com/googleplay/android-developer/answer/113469).
4. Dopo avere pubblicato l'app, accedere alla [versione gestita di Google Play Store](https://play.google.com/work) con lo stesso account usato per configurare la connessione tra Intune e Android Enterprise.
5. Nel nodo **App** dello store verificare che l'app pubblicata sia visualizzata.  
    L'app viene approvata automaticamente per essere sincronizzata con Intune.

## <a name="managed-google-play-web-links"></a>Collegamenti Web di Google Play gestito

I collegamenti Web di Google Play gestito possono essere installati e gestiti in modo analogo alle altre app Android. Dopo essere stati installati in un dispositivo, vengono visualizzati nell'elenco di app dell'utente insieme alle altre app installate. Toccare il collegamento per avviarlo nel browser del dispositivo.

I collegamenti Web vengono aperti con Microsoft Edge o qualsiasi altra app browser selezionata per la distribuzione. Assicurarsi di distribuire almeno un'app browser nei dispositivi affinché i collegamenti Web possano essere aperti correttamente. Tuttavia, tutte le opzioni di **visualizzazione** disponibili per i collegamenti Web (schermo intero, autonomo e interfaccia utente minima) funzioneranno solo con il browser Chrome. 

> [!IMPORTANT]
> Al momento della pubblicazione di questo documento, esiste un bug noto di Google che impedisce l'apertura dei collegamenti Web nei dispositivi con browser diversi da Chrome. Google si è impegnato a correggere questo bug.  Questa comunicazione verrà rimossa quando Microsoft avrà la conferma che Google ha pubblicato la correzione.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client** > **App**.
5. Nel riquadro **App** selezionare **Aggiungi**.
6. Nella casella a discesa **Tipo di App** selezionare **Google Play gestito**.
7. Selezionare **Google Play gestito - Apri** per aprire il catalogo di Google Play gestito.
7. Selezionare **Web apps** (App Web) nel catalogo di Google Play.
7. Fare clic sul pulsante **"+"** per aggiungere una nuova app
7. Immettere le informazioni richieste, quindi fare clic su **Create** (Crea).
7. Chiudere il riquadro di Google Play gestito dopo aver aggiunto le app desiderate
12. Fare clic su **Sincronizza** nel riquadro **Aggiungi app** per eseguire la sincronizzazione con il servizio Google Play gestito. Si noti che le app private potrebbero richiedere alcuni minuti per essere sincronizzate. Se non viene visualizzata la prima volta che si esegue una sincronizzazione, attendere qualche minuto e avviare una nuova sincronizzazione.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Sincronizzare un'app della versione gestita di Google Play con Intune

Se è stata approvata un'app dallo Store e l'app non è ancora visualizzata nel carico di lavoro **App client**, forzare una sincronizzazione immediata come descritto di seguito:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro del carico di lavoro **App client** in **Installazione** selezionare **Google Play gestito**.
5. Nel riquadro **Google Play gestito** scegliere **Aggiorna**.  
    La pagina aggiorna l'ora e lo stato dell'ultima sincronizzazione.
6. Nel riquadro del carico di lavoro **App client** selezionare **App**.  
    L'app della versione gestita di Google Play, appena resa disponibile, viene visualizzata.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Assegnazione di un'app Google Play gestita a dispositivi con profilo di lavoro Android Enterprise

Quando l'app viene visualizzata nel nodo **Licenze dell'app** del riquadro del carico di lavoro **App client**, è possibile [assegnarla come qualsiasi altra app](/intune-azure/manage-apps/deploy-apps) assegnando l'app ai gruppi di utenti.

Dopo essere stata assegnata, l'app viene installata o resa disponibile per l'installazione nei dispositivi degli utenti selezionati come destinazione. All'utente del dispositivo non viene chiesto di approvare l'installazione. Per altre informazioni sui dispositivi con profilo di lavoro Android Enterprise, vedere [Configurare la registrazione di dispositivi con profilo di lavoro Android Enterprise](../enrollment/android-work-profile-enroll.md). 

> [!NOTE] 
> Solo le app che sono state assegnate vengono visualizzate in Google Play Store gestito per gli utenti finali. Per questa ragione, si tratta di un passaggio chiave che l'amministratore deve eseguire quando configura le app con Google Play gestito.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Assegnazione di un'app Google Play gestita a dispositivi Android Enterprise completamente gestiti

I [dispositivi Android Enterprise completamente gestiti](../enrollment/android-fully-managed-enroll.md) sono dispositivi di proprietà aziendale associati a un utente singolo e usati esclusivamente per lavoro e non per uso personale. Gli utenti di dispositivi completamente gestiti possono ottenere le app aziendali disponibili dall'app Google Play gestita sul dispositivo.

Per impostazione predefinita, un dispositivo Android Enterprise completamente gestito non consentirà ai dipendenti di installare le app che non sono approvate dall'organizzazione. Inoltre, i dipendenti non saranno in grado di rimuovere le app installate in base ai criteri. Per offrire agli utenti un accesso completo a Google Play Store per installare le app anziché un accesso limitato alle app approvate in Google Play Store gestito, è possibile impostare **Consenti l'accesso a tutte le app in Google Play Store** su **Consenti**. Con questa impostazione, l'utente può accedere a tutte le app in Google Play Store usando il proprio account aziendale, ma gli acquisti possono essere limitati. È possibile rimuovere la restrizione relativa agli acquisti consentendo agli utenti di aggiungere nuovi account al dispositivo. Questa operazione consentirà agli utenti finali di acquistare app da Google Play Store usando account personali nonché di effettuare acquisti in-app. Per altre informazioni, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md). 

> [!NOTE]
> L'app Microsoft Intune e l'app Microsoft Authenticator verranno installate come app richieste su tutti i dispositivi completamente gestiti durante l'onboarding. L'installazione automatica di queste app offre il supporto dell'accesso condizionale e consente agli utenti dell'app Microsoft Intune di visualizzare e risolvere i problemi di conformità. 

## <a name="manage-android-enterprise-app-permissions"></a>Gestire le autorizzazioni per le app Android Enterprise
Android Enterprise richiede l'approvazione delle app nella console Web della versione gestita di Google Play prima di sincronizzarle con Intune e assegnarle agli utenti. Poiché Android Enterprise consente di eseguire automaticamente il push delle app ai dispositivi degli utenti, è necessario accettare le autorizzazioni dell'app per conto di tutti gli utenti. Gli utenti non vedono le autorizzazioni durante l'installazione delle app. È quindi importante comprendere le autorizzazioni.

Quando lo sviluppatore di un'app aggiorna le autorizzazioni con una nuova versione dell'app, queste non vengono automaticamente accettate, anche se le autorizzazioni precedenti erano state approvate. I dispositivi che eseguono la versione precedente dell'app possono comunque usarla. Tuttavia, l'app non viene aggiornata fino a quando non vengono approvate le nuove autorizzazioni. I dispositivi in cui non è installata l'app non la installano fino a quando non vengono approvate le nuove autorizzazioni dell'app. 

### <a name="update-app-permissions"></a>Aggiornare le autorizzazioni di app

Visitare periodicamente la console di Google Play gestita per verificare se sono disponibili nuove autorizzazioni. È possibile configurare Google Play per l'invio di un messaggio di posta elettronica quando sono necessarie nuove autorizzazioni per un'app approvata. Se si assegna un'app e si nota che non è installata nei dispositivi, verificare la disponibilità di nuove autorizzazioni seguendo questa procedura:

1. Andare a [Google Play](https://play.google.com/work).
2. Accedere con l'account Google usato per pubblicare e approvare le app.
3. Selezionare la scheda **Aggiornamenti** e verificare se sono necessari aggiornamenti per le app.  
    Le app elencate richiedono nuove autorizzazioni e non vengono assegnate finché non vengono applicate.

In alternativa, è possibile configurare Google Play per approvare di nuovo automaticamente le autorizzazioni delle app per ogni app.

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Segnalazione app Google Play gestite per dispositivi del profilo di lavoro Android Enterprise

Per le app Google Play gestite distribuite nei dispositivi del profilo di lavoro Android Enterprise, è possibile visualizzare il numero di versione specifico dell'app installata in un dispositivo. Questo vale solo per le app richieste. 


## <a name="delete-managed-google-play-apps"></a>Eliminare le app di Google Play gestite
Se necessario, è possibile eliminare da Microsoft Intune le app di Google Play gestite. Per eliminare un'app di Google Play gestita, aprire Microsoft Intune nel portale di Azure e selezionare **App client** > **App**. Nell'elenco di app selezionare i puntini di sospensione (...) a destra dell'app di Google Play gestita e quindi selezionare **Elimina** nell'elenco visualizzato. Quando si elimina un'app di Google Play gestita dall'elenco di app, l'app risulta automaticamente non approvata.

## <a name="android-enterprise-system-apps"></a>App di sistema Android Enterprise

È possibile abilitare un'app di sistema Android Enterprise per [dispositivi completamente gestiti](../enrollment/android-kiosk-enroll.md) o [dispositivi dedicati Android Enterprise](../enrollment/android-fully-managed-enroll.md). Per altre informazioni sull'aggiunta di un'app di sistema Android Enterprise, vedere [Aggiungere app di sistema Android Enterprise a Microsoft Intune](apps-ae-system.md).

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md)
