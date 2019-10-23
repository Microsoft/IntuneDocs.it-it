---
title: Criteri di configurazione delle app per Microsoft Intune
titleSuffix: ''
description: Informazioni su come usare i criteri di configurazione delle app in un dispositivo iOS o Android in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 42d17c15a2a32f828c5715dfad51f34c5e531e76
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507559"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Criteri di configurazione delle app per Microsoft Intune

I criteri di configurazione delle app consentono di evitare i problemi di configurazione delle app, permettendo di assegnare le impostazioni di configurazione a criteri assegnati agli utenti finali prima dell'esecuzione dell'app. Le impostazioni vengono quindi fornite automaticamente quando l'app viene configurata nel dispositivo degli utenti finali e gli utenti finali non devono eseguire alcuna azione. Le impostazioni di configurazione sono univoche per ogni app. 

È possibile creare e usare i criteri di configurazione delle app per specificare le impostazioni di configurazione sia per app iOS che Android. Queste impostazioni di configurazione consentono di personalizzare un'app tramite la gestione e la configurazione delle app. Le impostazioni dei criteri di configurazione vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione. 

Ad esempio, un'impostazione di configurazione dell'app potrebbe richiedere di specificare i dettagli seguenti:

- Un numero di porta personalizzato
- Impostazione della lingua
- Impostazioni di sicurezza
- Impostazioni di personalizzazione, ad esempio il logo aziendale

Se gli utenti finali dovessero immettere queste impostazioni, invece, potrebbero farlo in modo non corretto. I criteri di configurazione delle app possono contribuire a garantire la coerenza all'interno dell'azienda e a ridurre le chiamate al supporto tecnico da parte degli utenti finali che tentano di configurare le impostazioni autonomamente. Con i criteri di configurazione delle app l'adozione di nuove app può risultare più semplice e rapida.

I parametri di configurazione disponibili vengono decisi in ultimo dagli sviluppatori dell'app. È necessario esaminare la documentazione del fornitore dell'applicazione per verificare se un'app supporta la configurazione e quali configurazioni sono disponibili. Per alcune applicazioni, Intune popolerà le impostazioni di configurazione disponibili. 

> [!NOTE]
> Nel Google Play Store gestito le app che supportano la configurazione verranno contrassegnate come tali:
> 
> ![Screenshot di un'app configurata](./media/app-configuration-policies-overview/configured-app.png)
>
> Quando si usano i dispositivi gestiti come tipo di registrazione per i dispositivi Android, verranno visualizzate solo le app da [Google Play gestito](https://play.google.com/work) e non da [Google Play Store](https://play.google.com/store/apps). Google Play Store gestito, noto anche come Android for Work (AfW) e Android Enterprise, sono le app nel profilo di lavoro che contengono le versioni delle app che supportano la configurazione dell'app.

È possibile assegnare criteri di configurazione delle app a un gruppo di utenti finali e dispositivi tramite una combinazione di [assegnazioni di inclusione ed esclusione](apps-inc-exl-assignments.md). Dopo aver aggiunto un criterio di configurazione dell'app, è possibile impostare le assegnazioni per i criteri di configurazione dell'app. Quando si impostano le assegnazioni per i criteri, è possibile scegliere di includere ed escludere i [gruppi](../fundamentals/groups-add.md) di utenti finali ai quali vengono applicati i criteri. Quando si sceglie di includere uno o più gruppi, è possibile selezionare i gruppi specifici da includere o selezionare i gruppi predefiniti. I gruppi predefiniti includono **Tutti gli utenti**, **Tutti i dispositivi** e **Tutti gli utenti + Tutti i dispositivi**.

Sono disponibili due opzioni per l'uso dei criteri di configurazioni delle app con Intune:
- **Dispositivi gestiti**: il dispositivo è gestito da Intune come provider di gestione di dispositivi mobili (MDM). L'app deve essere progettata per supportare la configurazione dell'app.
- **App gestite** - Un'app che è stata sviluppata per integrare Intune App SDK. Questo scenario è noto come gestione di applicazioni per dispositivi mobili senza registrazione ([MAM-WE](app-management.md#mobile-application-management-mam-basics)). È anche possibile eseguire il wrapping di un'app per implementare e supportare Intune App SDK. Per altre informazioni sul wrapping di un'app, vedere [Preparare le app line-of-business per i criteri di protezione delle app](../developer/apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Le app gestite da Intune effettueranno la sincronizzazione con un intervallo di 30 minuti per lo stato dei criteri di configurazione delle app di Intune, quando vengono distribuite in combinazione con i criteri di protezione delle app di Intune. Se all'utente non sono assegnati criteri di protezione delle app di Intune, l'intervallo di sincronizzazione dei criteri di configurazione delle app di Intune viene impostato su 720 minuti.

## <a name="apps-that-support-app-configuration"></a>App che supportano la configurazione delle app

### <a name="managed-devices"></a>Dispositivi gestiti
È possibile usare i criteri di configurazione delle app per le app che li supportano. Per supportare la configurazione delle app in Intune, le app devono essere scritte in modo da poter usare le configurazioni delle app definite dal sistema operativo. Per altri dettagli sulle chiavi di configurazione dell'app supportate, rivolgersi al fornitore dell'app.

### <a name="managed-apps"></a>App gestite
È possibile preparare un'app line-of-business incorporando [Intune App SDK](../developer/app-sdk.md) nell'app oppure eseguendo il wrapping dell'app dopo lo sviluppo tramite lo [strumento di wrapping delle app di Intune](../developer/apps-prepare-mobile-application-management.md). Intune App SDK mira a ridurre al minimo la quantità di modifiche del codice richieste da uno sviluppatore di app. Per altre informazioni, vedere [Panoramica di Intune App SDK](../developer/app-sdk.md). Per un confronto tra Intune App SDK e lo strumento di wrapping delle app di Intune, vedere [Preparare le app line-of-business per i criteri di protezione delle app](../developer/apps-prepare-mobile-application-management.md#feature-comparison).

Selezionando **App gestite** come **Tipo di registrazione del dispositivo** si fa riferimento in modo specifico alle app configurate dai criteri di configurazione di Intune in un dispositivo che non è registrato nella gestione dei dispositivi, mentre l'opzione **Dispositivi gestiti** si applica alle app distribuite tramite il canale MDM e quindi gestite da Intune. Selezionare la scelta appropriata in base a queste descrizioni. 

![Tipo di registrazione del dispositivo](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> Per le app con più identità, come Microsoft Outlook, è possibile prendere in considerazione le preferenze dell'utente. L'opzione Posta in arrivo evidenziata, ad esempio, rispetta l'impostazione dell'utente e non modifica la configurazione. Altri parametri consentono di controllare se un utente può o meno modificare l'impostazione. Per altre informazioni, vedere [Distribuzione delle impostazioni di configurazione delle app di Outlook per iOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Convalidare i criteri di configurazione delle app applicati

È possibile convalidare i criteri di configurazione delle app usando i tre metodi seguenti:

   1. Visivamente nel dispositivo. Il comportamento dell'app di destinazione corrisponde a quello applicato nei criteri di configurazione delle app?
   2. Tramite i log di diagnostica (vedere la sezione Log di diagnostica più avanti).
   3. Nel portale di Intune. La sezione **Monitoraggio** di un criterio può fornire lo stato pertinente:

      ![Primo screenshot dello stato di installazione del dispositivo](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![Secondo screenshot dello stato di installazione del dispositivo](./media/app-configuration-policies-overview/device-install-status-2.png)

      Inoltre, in **Intune** -> **Dispositivi** -> **Tutti i dispositivi** sul lato sinistro dello schermo, l'opzione **Configurazione app** visualizzerà tutti i criteri assegnati e il relativo stato:

      ![Screenshot della configurazione dell'app](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>Log di diagnostica

### <a name="ios-configuration-on-unmanaged-devices"></a>Configurazione di iOS in dispositivi non gestiti

È possibile convalidare la configurazione di iOS con il **log di diagnostica Intune** in dispositivi non gestiti per la configurazione di app gestite.

1. Se non è già installato nel dispositivo, scaricare e installare **Intune Managed Browser** dall'App Store. Per altre informazioni, vedere [App protette di Microsoft Intune](apps-supported-intune-apps.md).
2. Avviare **Intune Managed Browser** e selezionare **informazioni** > **guidaintune** dalla barra di spostamento.
3. Fare clic sul pulsante **Attività iniziali**.
4. Fare clic su **Condividi i log**.
5. Usare l'app di posta elettronica scelta per inviare il log a se stessi, in modo che possa essere visualizzato sul PC. 
6. Esaminare il file **IntuneMAMDiagnostics.txt** nel visualizzatore di file di testo.
7. Cercare `ApplicationConfiguration`. I risultati saranno simili a quanto riportato di seguito:

    ``` JSON
        {
            (
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.BlockListURLs";
                    Value = "https://www.aol.com";
                },
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.bookmarks";
                    Value = "Outlook Web|https://outlook.office.com||Bing|https://www.bing.com";
                }
            );
        },
        {
            ApplicationConfiguration =             
            (
                {
                Name = IntuneMAMUPN;
                Value = "CMARScrubbedM:13c45c42712a47a1739577e5c92b5bc86c3b44fd9a27aeec3f32857f69ddef79cbb988a92f8241af6df8b3ced7d5ce06e2d23c33639ddc2ca8ad8d9947385f8a";
                },
                {
                Name = "com.microsoft.outlook.Mail.NotificationsEnabled";
                Value = false;
                }
            );
        }
    ```

I dettagli di configurazione dell'applicazione devono corrispondere ai criteri di configurazione dell'applicazione configurati per il tenant. 

![Configurazione dell'app interessata](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>Configurazione di iOS in dispositivi gestiti

È possibile convalidare la configurazione di iOS con il **log di diagnostica Intune** in dispositivi gestiti per la configurazione di app gestite.

1. Se non è già installato nel dispositivo, scaricare e installare **Intune Managed Browser** dall'App Store. Per altre informazioni, vedere [App protette di Microsoft Intune](apps-supported-intune-apps.md).
2. Avviare **Intune Managed Browser** e selezionare **informazioni** > **guidaintune** dalla barra di spostamento.
3. Fare clic sul pulsante **Attività iniziali**.
4. Fare clic su **Condividi i log**.
5. Usare l'app di posta elettronica scelta per inviare il log a se stessi, in modo che possa essere visualizzato sul PC. 
6. Esaminare il file **IntuneMAMDiagnostics.txt** nel visualizzatore di file di testo.
7. Cercare `AppConfig`. I risultati devono corrispondere ai criteri di configurazione dell'applicazione configurati per il tenant.

### <a name="android-configuration-on-managed-devices"></a>Configurazione di Android in dispositivi gestiti

È possibile convalidare la configurazione di iOS con il **log di diagnostica Intune** in dispositivi gestiti per la configurazione di app gestite.

Per raccogliere i log da un dispositivo Android, l'utente o l'utente finale deve scaricare i log dal dispositivo tramite una connessione USB (o tramite l'**Esplora file**  equivalente nel dispositivo). Seguire questa procedura:

1. Connettere il dispositivo Android al computer con il cavo USB.
2. Nel computer cercare una directory il cui nome è uguale a quello del dispositivo. In tale directory individuare `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal`.
3. Nella cartella `com.microsoft.windowsintune.companyportal` aprire la cartella File, quindi aprire `OMADMLog_0`.
3. Cercare `AppConfigHelper` per trovare i messaggi relativi alla configurazione dell'app. I risultanti saranno simili al blocco di dati seguente:

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>Supporto dell'API Graph per la configurazione delle app

È anche possibile usare l'API Graph per eseguire attività di configurazione delle app. Per informazioni dettagliate, vedere il [riferimento dell'API Graph sulla configurazione di destinazione MAM](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="using-logs-to-show-a-configuration-parameter"></a>Uso dei log per visualizzare un parametro di configurazione
Quando i log mostrano un parametro di configurazione confermato per l'applicazione ma che non sembra funzionare, potrebbe essersi verificato un problema con l'implementazione della configurazione da parte dello sviluppatore dell'app. Rivolgersi prima a tale sviluppatore oppure controllare la sua Knowledge Base potrebbe consentire di evitare una chiamata al supporto tecnico di Microsoft. Se si tratta di un problema relativo alla modalità di gestione della configurazione all'interno di un'app, sarà necessario risolverlo una versione aggiornata futura dell'app.

## <a name="next-steps"></a>Passaggi successivi

### <a name="managed-devices"></a>Dispositivi gestiti

- Informazioni sull'uso della configurazione delle app con i dispositivi iOS.  Vedere [Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti](app-configuration-policies-use-ios.md).
- Informazioni sull'uso della configurazione delle app con i dispositivi Android.  Vedere [Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>App gestite

- Informazioni sull'uso della configurazione delle app con le app gestite. Vedere [Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi](app-configuration-policies-managed-app.md).
