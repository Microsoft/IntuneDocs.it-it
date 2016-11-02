---
title: Introduzione a Microsoft Intune App SDK | Microsoft Intune
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed1008c786285821c608a8404805c6615c60507f
ms.openlocfilehash: c80868fdee79df62aae0aa64e378be5dcc9664ae


---

# Introduzione a Microsoft Intune App SDK

Questa guida introduttiva illustra come abilitare rapidamente un'app per dispositivi mobili per la gestione di applicazioni mobili con Microsoft Intune. Può essere utile per capire i vantaggi di Intune App SDK descritti nella [panoramica di Intune App SDK](intune-app-sdk.md).

Questa guida descrive i passaggi principali necessari per abilitare la gestione delle app mobili in un'app con Microsoft Intune. Intune App SDK supporta scenari simili su più piattaforme e mira a creare un'esperienza coerente nelle diverse piattaforme per gli amministratori IT. A causa delle limitazioni delle piattaforme, tuttavia, il supporto di alcune funzionalità può essere leggermente diverso.

# Guida introduttiva

## Registrare l'app store in Microsoft

**Se l'app è interna all'azienda e non viene resa disponibile a un app store pubblico**:

**Non è necessario** registrare l'app. Per le app line-of-business interne, l'amministratore IT distribuirà l'app internamente. Intune rileverà che l'app è stata creata con l'SDK e consentirà all'amministratore IT di applicare le impostazioni dei criteri MAM. È possibile passare alla sezione [Abilitare un'app mobile iOS e Android per MAM con l'SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Se l'applicazione verrà rilasciata a un app store pubblico, ad esempio l'App Store Apple o Google Play**: 

**È necessario** innanzitutto registrare l'app con Microsoft Intune e accettare le condizioni di registrazione. Dopo la registrazione, gli amministratori IT possono applicare le impostazioni dei criteri di gestione delle applicazioni mobili di Intune all'app abilitata, che verrà elencata come partner di app di Intune. Fino alla conclusione della registrazione e all'avvenuta conferma da parte del team di Microsoft Intune, gli amministratori di Intune non potranno applicare i criteri di gestione delle applicazioni mobili al collegamento diretto dell'app. Microsoft aggiungerà l'app anche alla propria [pagina partner di Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps), in cui verrà visualizzata l'icona dell'app per mostrare il supporto dei criteri di gestione delle applicazioni mobili di Microsoft Intune.

Per avviare il processo di registrazione, riempire il **[questionario per partner di app di Microsoft Intune](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u)**. 

Microsoft userà gli indirizzi di posta elettronica specificati nelle risposte al questionario per contattare gli utenti e continuare il processo di registrazione. Lo stesso indirizzo verrà usato anche per contattare l'utente per eventuali chiarimenti.

> [!NOTE]
> Tutte le informazioni raccolte nel modulo precedente e nella corrispondenza tramite posta elettronica con il team di Microsoft Intune rispetteranno l'[Informativa sulla privacy Microsoft](https://www.microsoft.com/en-us/privacystatement/default.aspx).

**Cosa accade durante il processo di registrazione**: 

1. dopo l'invio del modulo, si verrà contattati da Microsoft all'indirizzo di posta elettronica specificato nella registrazione per confermare la ricezione o per richiedere altre informazioni necessarie al completamento della registrazione. 
2. Dopo che il team di Intune ha ricevuto tutte le informazioni necessarie, verrà inviato il contratto per i partner di app di Microsoft Intune da firmare. In questo contratto sono indicate le condizioni che la società deve accettare per poter diventare partner di app di Microsoft Intune. 
3. Sarà inviata una conferma quando l'app è registrata correttamente con il servizio di Microsoft Intune e quando l'app è disponibile sul sito dei [partner di Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps). 
4. Infine, verrà aggiunto un collegamento diretto dell'app al prossimo aggiornamento mensile dei servizi di Intune. Ad esempio, se le informazioni di registrazione vengono completate nel mese di luglio, il collegamento diretto dell'app sarà supportato a metà agosto. 

Se il collegamento diretto all'app store dovesse cambiare, sarà necessario registrare di nuovo l'app. È necessario anche comunicare se l'app viene aggiornata con una nuova versione di Intune App SDK.



## Scaricare i file SDK

I file di Intune App SDK per iOS e Android nativi sono ospitati in un account Microsoft GitHub. I repository pubblici riportati di seguito contengono rispettivamente i file SDK per iOS e Android:

* [Intune App SDK per iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Intune App SDK per Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

**Se l'app è basata su Xamarin o Cordova, usare gli strumenti di sviluppo seguenti**:

* [Componente Xamarin per Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Plug-in Cordova per Intune App SDK](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Si consiglia di registrarsi per un account GitHub utile per eseguire operazioni di biforcazione ed estrazione dal repository. GitHub consente agli sviluppatori di comunicare con il team del prodotto Microsoft, aprire problemi e ricevere risposte rapide, visualizzare le note sulla versione e fornire commenti e suggerimenti a Microsoft. Per domande relative all'account e ai repository GitHub, contattare msintuneappsdk@microsoft.com.





## Abilitare un'app per dispositivi mobili iOS e Android per MAM con l'SDK

Per integrare Intune App SDK nell'app nativa per iOS, vedere: 

* **[Manuale dello sviluppatore di Microsoft Intune App SDK per iOS](intune-app-sdk-ios.md)**: questo documento descrive in dettaglio come abilitare l'app per dispositivi mobili iOS con Intune App SDK. 


Per integrare Intune App SDK nell'app per Android, vedere:

* **[Manuale dello sviluppatore di Microsoft Intune App SDK per Android](intune-app-sdk-android.md)**: questo documento descrive in dettaglio come abilitare l'app per dispositivi mobili Android con Intune App SDK. 

La documentazione per il componente Xamarin di Intune App SDK e il plug-in Cordova per Intune App SDK si trova nei rispettivi repository di GitHub. 


## Configurazione della telemetria per l'app

Microsoft Intune raccoglie i dati sulle statistiche di utilizzo dell'app.

* **Intune App SDK per iOS**: l'SDK registra i dati della telemetria SDK negli eventi di utilizzo per impostazione predefinita. Questi dati vengono inviati a Microsoft Intune.

    * Se si sceglie di non inviare i dati della telemetria a Microsoft Intune dall'app, è necessario disabilitare la trasmissione della telemetria SDK impostando la proprietà `MAMTelemetryDisabled` su "YES" nel dizionario IntuneMAMSettings.

* **Intune App SDK per Android**: i dati della telemetria non vengono registrati con l'SDK.

## Testare l'app abilitata per MAM con Microsoft Intune

Dopo aver completato i passaggi necessari per integrare l'app per iOS o Android con Intune App SDK, è necessario assicurarsi che tutti i criteri di gestione delle app siano abilitati e funzionanti per l'utente finale e l'amministratore IT. Per testare l'app integrata, è necessario quanto segue:

<!--TODO-->

* **Test dell'app abilitata per la gestione delle applicazioni mobili con Microsoft Intune**: questo documento illustra in dettaglio come testare le app iOS e Android abilitate per la gestione delle applicazioni mobili con Microsoft Intune. È possibile trovare il documento nei repository GitHub degli SDK.

* **Account di Microsoft Intune**: per testare le app abilitate per MAM con Microsoft Intune, è necessario un account di Microsoft Intune. 
    * Quando un ISV abilita le proprie app dello store iOS e Android per la gestione delle applicazioni mobili di Intune, si riceverà un codice promozionale al termine della registrazione in Microsoft Intune come descritto nel passaggio relativo alla registrazione. Con il codice promozionale sarà possibile richiedere una versione di valutazione di Microsoft Intune per 1 anno di utilizzo esteso. 
    * Se si sta sviluppando un'app line-of-business che non verrà inviata allo store, l'accesso a Microsoft Intune deve essere fornito dall'organizzazione. Si può anche richiedere 1 mese di valutazione gratuita con [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).




<!--HONumber=Oct16_HO3-->


