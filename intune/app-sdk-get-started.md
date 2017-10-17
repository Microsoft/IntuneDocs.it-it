---
title: Introduzione a Microsoft Intune App SDK
description: Abilitare rapidamente un'app per dispositivi mobili per la gestione di applicazioni mobili (MAM) con Microsoft Intune.
keywords: 
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0e55246f8f089a998fa4a04fe07e5e54408d8513
ms.sourcegitcommit: f3b8fb8c47fd2c9941ebbe2c047b7d0a093e5a83
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2017
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introduzione a Microsoft Intune App SDK

Questa guida illustra come abilitare rapidamente un'app per dispositivi mobili per i criteri di protezione delle app con Microsoft Intune. Può essere utile per capire i vantaggi di Intune App SDK descritti nella [panoramica di Intune App SDK](app-sdk.md).

Intune App SDK supporta scenari simili in iOS e Android ed è progettato per offrire un'esperienza coerente nelle diverse piattaforme agli amministratori IT. A causa delle limitazioni delle piattaforme, tuttavia, il supporto di alcune funzionalità può essere leggermente diverso.

## <a name="register-your-store-app-with-microsoft"></a>Registrare l'app store in Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Se l'app è interna all'organizzazione e non sarà disponibile pubblicamente:

*Non è necessario* registrare l'app. Per le app line-of-business interne, l'amministratore IT distribuirà l'app internamente. Intune rileverà che l'app è stata creata con l'SDK e consentirà all'amministratore IT di applicare i criteri di protezione delle app. È possibile passare alla sezione [Abilitare un'app iOS o Android per i criteri di protezione delle app](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Se l'app verrà rilasciata a un app store pubblico, ad esempio l'App Store Apple o Google Play:

È prima di tutto _**necessario**_ registrare l'app in Microsoft Intune e accettare le condizioni di registrazione. Gli amministratori IT possono applicare i criteri di protezione delle app all'app abilitata, che verrà elencata come partner di app di Intune.

Fino alla conclusione della registrazione e all'avvenuta conferma da parte del team di Microsoft Intune, gli amministratori di Intune non potranno applicare i criteri di protezione delle app al collegamento diretto dell'app. Microsoft aggiungerà l'app anche alla relativa [pagina dei partner di Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Verrà quindi visualizzata l'icona dell'app per mostrare che supporta i criteri di protezione delle app di Intune.

Per avviare il processo di registrazione, riempire il [questionario per partner di app di Microsoft Intune](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u).

Microsoft userà gli indirizzi di posta elettronica specificati nelle risposte al questionario per contattare gli utenti e continuare il processo di registrazione. Lo stesso indirizzo verrà usato anche per contattare l'utente per eventuali chiarimenti.

> [!NOTE]
> Tutte le informazioni raccolte nel questionario e nella corrispondenza tramite posta elettronica con il team di Microsoft Intune rispetteranno l'[Informativa sulla privacy Microsoft](https://www.microsoft.com/privacystatement/default.aspx).

**Cosa accade durante il processo di registrazione**:

1. Dopo l'invio del questionario, si verrà contattati da Microsoft all'indirizzo di posta elettronica specificato nella registrazione per confermare la ricezione o per richiedere altre informazioni necessarie al completamento della registrazione.

2. Dopo che il team di Intune ha ricevuto tutte le informazioni necessarie, verrà inviato il contratto per i partner di app di Microsoft Intune da firmare. In questo contratto sono indicate le condizioni che la società deve accettare per poter diventare partner di app di Microsoft Intune.

3. Sarà inviata una conferma quando l'app è registrata correttamente con il servizio di Microsoft Intune e quando l'app è disponibile sul sito dei [partner di Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

4. Infine, verrà aggiunto un collegamento diretto dell'app al prossimo aggiornamento mensile dei servizi di Intune. Ad esempio, se le informazioni di registrazione vengono completate nel mese di luglio, il collegamento diretto sarà supportato a metà agosto.

Se il collegamento diretto dell'app dovesse cambiare, sarà necessario registrare di nuovo l'app.

> [!NOTE]
> È necessario comunicare se l'app viene aggiornata con una nuova versione di Intune App SDK.



## <a name="download-the-sdk-files"></a>Scaricare i file SDK

I file di Intune App SDK per iOS e Android nativi sono ospitati in un account Microsoft GitHub. I repository pubblici contengono rispettivamente i file SDK per iOS e Android nativi:

* [Intune App SDK per iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Intune App SDK per Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Se l'app è basata su Xamarin o Cordova, usare queste varianti dell'SDK:

* [Componente Xamarin per Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Plug-in Cordova per Intune App SDK](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Si consiglia di registrarsi per un account GitHub utile per eseguire operazioni di biforcazione ed estrazione dal repository. GitHub consente agli sviluppatori di comunicare con il team del prodotto Microsoft, aprire problemi e ricevere risposte rapide, visualizzare le note sulla versione e fornire commenti e suggerimenti a Microsoft. Per domande su Intune App SDK GitHub, contattare msintuneappsdk@microsoft.com.





## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Abilitare un'app iOS o Android per i criteri di protezione delle app

Per integrare Intune App SDK nelle app, è necessario consultare una delle guide per gli sviluppatori seguenti:

* **[Guida per gli sviluppatori di Microsoft Intune App SDK per iOS](app-sdk-ios.md)**: questo documento descrive in dettaglio come abilitare app iOS native con Intune App SDK.

* **[Guida a Microsoft Intune App SDK per sviluppatori di Android](app-sdk-android.md)**: questo documento descrive in dettaglio come abilitare app Android native con Intune App SDK.

* **[Plug-in Cordova per Microsoft Intune App SDK](app-sdk-cordova.md)**: questo documento fornisce informazioni per compilare app per iOS e Android usando Cordova per i criteri di protezione delle app di Intune.

* **[Componente Xamarin per Microsoft Intune App SDK](app-sdk-xamarin.md)**: questo documento fornisce informazioni per compilare app per iOS e Android usando Xamarin per i criteri di protezione delle app di Intune.




## <a name="configure-telemetry-for-your-app"></a>Configurazione della telemetria per l'app

Microsoft Intune raccoglie i dati sulle statistiche di utilizzo dell'app.

* **Intune App SDK per iOS**: l'SDK registra i dati della telemetria SDK negli eventi di utilizzo per impostazione predefinita. Questi dati vengono inviati a Microsoft Intune.

    * Se si sceglie di non inviare i dati della telemetria a Microsoft Intune dall'app, è necessario disabilitare la trasmissione della telemetria SDK impostando la proprietà `MAMTelemetryDisabled` su "YES" nel dizionario IntuneMAMSettings.


* **Intune App SDK per Android**: i dati della telemetria non vengono registrati con l'SDK.

## <a name="next-steps-after-integration"></a>Passaggi successivi dopo l'integrazione

### <a name="test-your-app"></a>Test dell'app
Dopo aver completato i passaggi necessari per integrare l'app per iOS o Android con Intune App SDK, è necessario assicurarsi che tutti i criteri di protezione delle app siano abilitati e funzionanti per l'utente e l'amministratore IT. Per testare l'app integrata, è necessario quanto segue:

* **Account di prova per Microsoft Intune**: per testare le funzionalità di protezione delle app di Intune nelle app abilitate per Intune, è necessario un account di Microsoft Intune.

    * Gli ISV che abilitano le proprie app dello store iOS e Android per i criteri di protezione delle app di Intune, riceveranno un codice promozionale al termine della registrazione in Microsoft Intune, come descritto nel passaggio relativo alla registrazione. Con il codice promozionale sarà possibile richiedere una versione di valutazione di Microsoft Intune per un anno di uso esteso.

    * Se si sta sviluppando un'app line-of-business che non verrà inviata allo store, l'accesso a Microsoft Intune deve essere fornito dall'organizzazione. Si può anche richiedere un mese di valutazione gratuita con [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).

* **Criteri di protezione delle app di Intune**: per testare l'app con tutti i criteri di protezione delle app di Intune, è necessario conoscere il comportamento previsto per ogni impostazione dei criteri. Vedere le descrizioni dei [criteri di protezione delle app iOS](/intune-classic/deploy-use/ios-mam-policy-settings) e dei [criteri di protezione delle app Android](/intune-classic/deploy-use/android-mam-policy-settings).

* **Risoluzione dei problemi**: se si verificano problemi durante i test manuali dell'esperienza utente per l'app, vedere [Risolvere i problemi relativi alla gestione di applicazioni mobili](/intune-classic/troubleshoot/troubleshoot-mam). Questo articolo offre assistenza per i problemi comuni, le finestre di dialogo e i messaggi di errore che possono presentarsi nelle app abilitate per Intune. 

### <a name="badge-your-app-optional"></a>Aggiungere il logo all'app (facoltativo)

Dopo aver verificato che i criteri di protezione delle app di Intune funzionano correttamente in un'app, è possibile aggiungere all'icona dell'app il logo di protezione delle app di Intune.

Questo logo segnala agli amministratori IT, agli utenti finali e ai potenziali clienti di Intune che l'app supporta i criteri di protezione delle app di Intune, favorendo così l'utilizzo e l'adozione dell'app da parte dei clienti di Intune.

Il logo è un'icona a forma di valigetta, come illustrato negli esempi seguenti:

![Esempio di logo 1](./media/badge-example-1.png) ![Esempio di logo 2](./media/badge-example-2.png)

**Cosa serve per aggiungere il logo all'app**:

* Un'applicazione per la modifica di immagini che supporta la lettura di file con estensione **eps** oppure un'applicazione Adobe in grado di leggere file con estensione **ai**.

* È possibile trovare [linee guida e asset per l'aggiunta del logo alle app di Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) nella sezione dedicata a Microsoft Intune di GitHub.
