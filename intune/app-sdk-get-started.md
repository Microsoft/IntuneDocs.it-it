---
title: Introduzione a Microsoft Intune App SDK
description: Abilitare rapidamente un'app per dispositivi mobili per la gestione di applicazioni mobili (MAM) con Microsoft Intune.
keywords: ''
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0df56da9fff72124bb44a2c73e63d88cb6542938
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introduzione a Microsoft Intune App SDK

Questa guida illustra come abilitare rapidamente un'app per dispositivi mobili per i criteri di protezione delle app con Microsoft Intune. Può essere utile per capire i vantaggi di Intune App SDK descritti nella [panoramica di Intune App SDK](app-sdk.md).

Intune App SDK supporta scenari simili in iOS e Android ed è progettato per offrire un'esperienza coerente nelle diverse piattaforme agli amministratori IT. A causa delle limitazioni delle piattaforme, tuttavia, il supporto di alcune funzionalità può essere leggermente diverso.

## <a name="register-your-store-app-with-microsoft"></a>Registrare l'app store in Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Se l'app è interna all'organizzazione e non sarà disponibile pubblicamente:

*Non è necessario* registrare l'app. Per le app line-of-business interne, l'amministratore IT distribuirà l'app internamente. Intune rileverà che l'app è stata creata con l'SDK e consentirà all'amministratore IT di applicare i criteri di protezione delle app. È possibile passare alla sezione [Abilitare un'app iOS o Android per i criteri di protezione delle app](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Se l'app verrà rilasciata a un app store pubblico, ad esempio l'App Store Apple o Google Play:

È prima di tutto _**necessario**_ registrare l'app in Microsoft Intune e accettare le condizioni di registrazione. Gli amministratori IT possono quindi applicare i criteri di protezione delle app all'app gestita che verrà inserita nell'elenco delle app partner di Intune.

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

Se l'app è basata su Xamarin, usare questa variante dell'SDK:

* [Binding Xamarin per Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)

Si consiglia di registrarsi per un account GitHub utile per eseguire operazioni di biforcazione ed estrazione dal repository. GitHub consente agli sviluppatori di comunicare con il team del prodotto Microsoft, aprire problemi e ricevere risposte rapide, visualizzare le note sulla versione e fornire commenti e suggerimenti a Microsoft. Per domande su Intune App SDK GitHub, contattare msintuneappsdk@microsoft.com.

## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Abilitare un'app iOS o Android per i criteri di protezione delle app

Per integrare Intune App SDK nelle app, è necessario consultare una delle guide per gli sviluppatori seguenti:

* **[Guida per gli sviluppatori di Microsoft Intune App SDK per iOS](app-sdk-ios.md)**: questo documento descrive in dettaglio come abilitare app iOS native con Intune App SDK.

* **[Guida a Microsoft Intune App SDK per sviluppatori di Android](app-sdk-android.md)**: questo documento descrive in dettaglio come abilitare app Android native con Intune App SDK.

* **[Binding Xamarin per Microsoft Intune App SDK](app-sdk-xamarin.md)**: questo documento contiene informazioni per compilare app per iOS e Android usando Xamarin per i criteri di protezione delle app di Intune.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Abilitare un'app iOS o Android per l'accesso condizionale basato su app
 
 Oltre ad abilitare l'app per i criteri di protezione delle app, è necessario soddisfare i requisiti seguenti affinché l'app possa funzionare correttamente con l'accesso condizionale basato su app di Azure Active Directory (AAD):
 
 * L'app deve essere compilata con la [libreria di autenticazione di Azure Active Directory ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) e abilitata per l'autenticazione con broker AAD.
 
 * L'[ID client AAD](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application) per l'app deve essere univoco sulle piattaforme iOS e Android.
 
## <a name="configure-telemetry-for-your-app"></a>Configurazione della telemetria per l'app

Microsoft Intune raccoglie i dati sulle statistiche di utilizzo dell'app.

* **Intune App SDK per iOS**: l'SDK registra i dati della telemetria SDK negli eventi di utilizzo per impostazione predefinita. Questi dati vengono inviati a Microsoft Intune.

    * Se si sceglie di non inviare i dati della telemetria a Microsoft Intune dall'app, è necessario disabilitare la trasmissione della telemetria SDK impostando la proprietà `MAMTelemetryDisabled` su "YES" nel dizionario IntuneMAMSettings.

* **Intune App SDK per Android**: Intune App SDK per Android non controlla la raccolta di dati dall'app. Per impostazione predefinita, l'applicazione Portale aziendale registra dati di telemetria. Questi dati vengono inviati a Microsoft Intune. In base ai criteri Microsoft, non vengono raccolte informazioni personali. 

    * Se l'utente finale sceglie di non inviare questi dati, deve disattivare la telemetria in Impostazioni nell'app Portale aziendale. Per altre informazioni, vedere [Disattivare la raccolta dati di utilizzo di Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 


 Il numero di versione delle app line-of-business iOS e Android è visibile <!-- 1380712 -->

## <a name="line-of-business-app-version-numbers"></a>Numeri di versione di app line-of-business

Nelle app line-of-business in Intune viene ora visualizzato il numero di versione per le app iOS e Android. Il numero viene visualizzato nel portale di Azure nell'elenco delle app e nel pannello della panoramica dell'app. Gli utenti finali possono visualizzare il numero dell'app nell'app Portale aziendale e nel portale Web.

### <a name="full-version-number"></a>Numero di versione completo

Il numero di versione completo identifica una versione specifica dell'app. Il numero viene visualizzato come _Versione_(_Build_). Ad esempio, 2.2(2.2.17560800). 

Il numero di versione completo include due componenti:

 - **Versione**  
   Il numero di versione è il numero di versione leggibile dell'app. Viene usato dagli utenti finali per identificare diverse versioni dell'app.

 - **Numero di build**  
    Il numero di build è un numero interno che può essere usato nel rilevamento delle app e per gestire l'app a livello di codice. Il numero di build si riferisce a un'iterazione dell'app che fa riferimento alle modifiche nel codice.

### <a name="version-and-build-number-in-android-and-ios"></a>Numero di versione e di build in Android e iOS

Sia Android che iOS usano il numero di versione e di build per i riferimenti alle app. Tuttavia, entrambi hanno significati che sono specifici del sistema operativo. Nella tabella seguente viene illustrato come sono correlati questi termini.

Quando si sviluppa un'applicazione line-of-business per l'uso in Intune, ricordarsi di usare sia il numero di versione che il numero di build. Le funzionalità di gestione delle app di Intune si basano su un elemento **CFBundleVersion** (per iOS) e **PackageVersionCode** (per Android) significativo. Questi numeri sono inclusi nel manifesto dell'app. 

Intune|iOS|Android|Descrizione|
|---|---|---|---|
Numero versione|CFBundleShortVersionString|PackageVersionName |Questo numero indica una versione specifica dell'app per gli utenti finali.|
Numero build|CFBundleVersion|PackageVersionCode |Questo numero viene usato per indicare un'iterazione nel codice dell'app.|

#### <a name="ios"></a>iOS

- **CFBundleShortVersionString**  
    Specifica il numero di versione del bundle. Questo numero identifica una versione rilasciata dell'app. Il numero viene usato dagli utenti finali per fare riferimento all'app.
  - **CFBundleVersion**  
    La versione di build del bundle, che identifica un'iterazione del bundle. Il numero può indicare un bundle rilasciato o non rilasciato. Il numero viene usato per il rilevamento dell'app.

#### <a name="android"></a>Android

 - **PackageVersionName**  
    Il numero di versione visualizzato dagli utenti. Questo attributo può essere impostato come una stringa non elaborata o come un riferimento a una risorsa di stringa. La stringa non ha altri scopi se non la visualizzazione da parte degli utenti.
 - **PackageVersionCode**  
    Un numero di versione interno. Questo numero viene usato solo per determinare se una versione è più recente rispetto a un'altra. I valori più alti indicano versioni più recenti. Non si tratta della versione 

## <a name="next-steps-after-integration"></a>Passaggi successivi dopo l'integrazione

### <a name="test-your-app"></a>Test dell'app
Dopo aver completato i passaggi necessari per integrare l'app per iOS o Android con Intune App SDK, è necessario assicurarsi che tutti i criteri di protezione delle app siano abilitati e funzionanti per l'utente e l'amministratore IT. Per testare l'app integrata, è necessario quanto segue:

* **Account di prova per Microsoft Intune**: per testare le funzionalità di protezione delle app di Intune nelle app gestite da Intune, è necessario un account di Microsoft Intune.

    * Gli ISV che abilitano le proprie app dello store iOS e Android per i criteri di protezione delle app di Intune, riceveranno un codice promozionale al termine della registrazione in Microsoft Intune, come descritto nel passaggio relativo alla registrazione. Con il codice promozionale sarà possibile richiedere una versione di valutazione di Microsoft Intune per un anno di uso esteso.

    * Se si sta sviluppando un'app line-of-business che non verrà inviata allo store, l'accesso a Microsoft Intune deve essere fornito dall'organizzazione. Si può anche richiedere un mese di valutazione gratuita con [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).

* **Criteri di protezione delle app di Intune**: per testare l'app con tutti i criteri di protezione delle app di Intune, è necessario conoscere il comportamento previsto per ogni impostazione dei criteri. Vedere le descrizioni dei [criteri di protezione delle app iOS](/intune-classic/deploy-use/ios-mam-policy-settings) e dei [criteri di protezione delle app Android](/intune-classic/deploy-use/android-mam-policy-settings).

* **Risoluzione dei problemi**: se si verificano problemi durante i test manuali dell'esperienza utente per l'app, vedere [Risolvere i problemi relativi alla gestione di applicazioni mobili](/intune-classic/troubleshoot/troubleshoot-mam). Questo articolo offre assistenza per i problemi comuni, le finestre di dialogo e i messaggi di errore che possono presentarsi nelle app gestite da Intune. 

### <a name="badge-your-app-optional"></a>Aggiungere il logo all'app (facoltativo)

Dopo aver verificato che i criteri di protezione delle app di Intune funzionano correttamente in un'app, è possibile aggiungere all'icona dell'app il logo di protezione delle app di Intune.

Questo logo segnala agli amministratori IT, agli utenti finali e ai potenziali clienti di Intune che l'app supporta i criteri di protezione delle app di Intune, favorendo così l'utilizzo e l'adozione dell'app da parte dei clienti di Intune.

Il logo è un'icona a forma di valigetta, come illustrato negli esempi seguenti:

![Esempio di logo 1](./media/badge-example-1.png) ![Esempio di logo 2](./media/badge-example-2.png)

**Cosa serve per aggiungere il logo all'app**:

* Un'applicazione per la modifica di immagini che supporta la lettura di file con estensione **eps** oppure un'applicazione Adobe in grado di leggere file con estensione **ai**.

* È possibile trovare [linee guida e asset per l'aggiunta del logo alle app di Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) nella sezione dedicata a Microsoft Intune di GitHub.
