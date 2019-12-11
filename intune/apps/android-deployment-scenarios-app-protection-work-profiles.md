---
title: Criteri di protezione delle app e profili di lavoro in Microsoft Intune - Azure | Microsoft Docs
description: Differenze, vantaggi e svantaggi quando si sceglie se usare i criteri di protezione delle app o i profili di lavoro per i dispositivi Android Enterprise personali o BYOD in Microsoft Intune. Confronto delle differenze e delle funzionalità ottenibili con i criteri di protezione delle app senza registrazione (APP-WE) e con i profili di lavoro Android Enterprise.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d0b4f8d5124924d013e7ac131dafc947a95c7b65
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059787"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Criteri di protezione delle applicazioni e profili di lavoro in Intune su dispositivi Android Enterprise

In molte organizzazioni gli amministratori devono garantire la protezione di risorse e dati su dispositivi diversi. Una delle sfide è la protezione delle risorse degli utenti con dispositivi Android Enterprise personali, detti anche dispositivi BYOD (Bring-Your-Own Device). Microsoft Intune supporta due scenari di distribuzione Android per i dispositivi BYOD:

- Criteri di protezione delle app senza registrazione (APP-WE)
- Profili di lavoro Android Enterprise

Gli scenari di distribuzione con criteri di protezione delle app senza registrazione e con profili di lavoro Android includono le seguenti funzionalità, importanti per gli ambienti BYOD:

1. **Protezione e separazione dei dati gestiti dall'organizzazione**: entrambe le soluzioni proteggono i dati dell'organizzazione implementando controlli di prevenzione della perdita dei dati (DLP) sui dati gestiti dall'organizzazione. Queste protezioni impediscono la divulgazione accidentale di dati protetti, ad esempio impediscono che un utente finale condivida accidentalmente dati di questo tipo con un'app o un account personale. Garantiscono anche che il dispositivo che accede ai dati è integro e non compromesso.

2. **Privacy dell'utente finale**: i criteri APP-WE e i profili di lavoro Android Enterprise separano nel dispositivo i contenuti dell'utente finale dai dati gestiti dall'amministratore MDM (Mobile Device Management). In entrambi gli scenari gli amministratori IT applicano criteri (come l'autenticazione solo tramite PIN) alle app o alle identità gestite dall'organizzazione. Gli amministratori IT non possono leggere, effettuare l'accesso o cancellare i dati di proprietà o controllati dagli utenti finali.

La scelta tra i criteri di protezione delle app senza registrazione (APP-WE) o i profili di lavoro Android Enterprise per la distribuzione BYOD dipende dai requisiti e dalle esigenze operative. Lo scopo di questo articolo è offrire indicazioni per facilitare la scelta.

## <a name="about-intune-app-protection-policies"></a>Informazioni sui criteri di protezione delle app di Intune

I criteri di protezione delle app di Intune (APP) sono criteri di protezione dati destinati agli utenti. I criteri implementano la protezione dalla perdita di dati a livello dell'applicazione. I criteri APP di Intune richiedono agli sviluppatori di abilitare le funzionalità APP nelle app che creano.

L'abilitazione di APP nelle singole app per Android può avvenire in diversi modi:

1. **Integrazione nativa nelle app proprietarie Microsoft**: i criteri APP di Intune sono già incorporati nelle app di Microsoft Office per Android e in altre app Microsoft. Queste app di Office come Word, OneDrive, Outlook e così via non richiedono altre personalizzazioni per l'applicazione dei criteri. Gli utenti finali possono installare direttamente queste app da Google Play Store.

2. **Integrazione nelle build delle app da parte degli sviluppatori tramite il SDK Intune**: gli sviluppatori di app possono integrare il SDK di Intune nel codice sorgente e ricompilare le app con il supporto delle funzionalità dei criteri APP di Intune.

3. **Integrazione tramite lo strumento di wrapping delle app di Intune**: alcuni clienti compilano app per Android (file con estensione apk) senza accedere al codice sorgente. Senza il codice sorgente, lo sviluppatore non può eseguire l'integrazione con il SDK di Intune. Senza il SDK non è possibile abilitare i criteri APP nell'app. Lo sviluppatore deve modificare o riscrivere il codice dell'app in modo che supporti i criteri APP.

    Per facilitare l'integrazione, Intune include lo **Strumento di wrapping delle app** per le app Android (APK) esistenti e crea un'app che riconosce i criteri APP.

    Per altre informazioni su questo strumento, vedere [Preparare le app line-of-business per i criteri di protezione delle app](../developer/apps-prepare-mobile-application-management.md).

Per un elenco delle app già abilitate con criteri APP, vedere [Le app gestite da Intune includono un set completo di criteri di protezione delle applicazioni mobili](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="deployment-scenarios"></a>Scenari di distribuzione

Questa sezione descrive le caratteristiche importanti degli scenari di distribuzione con i criteri di protezione delle app senza registrazione (APP-WE) e con i criteri di lavoro Android Enterprise.

### <a name="app-we"></a>APP-WE

Una distribuzione APP-WE (criteri di protezione delle app senza registrazione) definisce i criteri per le app e non per i dispositivi. In genere, in questo scenario i dispositivi non sono registrati o gestiti da un'autorità MDM, ad esempio Intune. Per la protezione delle app e l'accesso ai dati aziendali, gli amministratori usano app gestibili con criteri APP e implementano criteri di protezione dati in tali app.

Questa funzionalità si applica a:

- Android 4.4 e versioni successive

> [!TIP]
> Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md).

Gli scenari APP-WE sono destinati agli utenti finali che richiedono un footprint dei dati aziendali ridotto sui dispositivi e non sono interessati alla registrazione in MDM. L'amministratore deve comunque garantire la protezione dei dati. Questi dispositivi non sono gestiti. Pertanto le attività e le funzionalità MDM comuni, come WiFi, VPN per i dispositivi mobili e gestione dei certificati non appartengono a questo scenario di distribuzione.

### <a name="android-enterprise-work-profiles"></a>Profili di lavoro Android Enterprise

I profili di lavoro sono lo scenario di distribuzione principale di Android Enterprise e l'unico scenario considerato nei casi d'uso BYOD. Il profilo di lavoro è una partizione separata creata a livello del sistema operativo Android, che può essere gestita da Intune.

Questa funzionalità si applica a:

- Dispositivi Android 5.0 e versioni successive con Google Mobile Services

Un profilo di lavoro include le funzionalità seguenti:

- **Funzionalità MDM tradizionali**: Le funzionalità MDM essenziali, come la gestione del ciclo di vita delle app con Google Play gestito, sono disponibili in tutti gli scenari Android Enterprise. La versione gestita di Google Play garantisce un'esperienza affidabile di installazione e aggiornamento di app senza interventi dell'utente. Il settore IT può anche eseguire il push delle impostazioni di configurazione app alle app aziendali. Questo approccio non richiede agli utenti finali di consentire installazioni da origini sconosciute. Con i profili di lavoro sono disponibili altre attività MDM comuni come la distribuzione dei certificati, la configurazione delle reti WiFi/VPN e l'impostazione di passcode del dispositivo.

- **DLP sul limite del profilo di lavoro**: come per i criteri APP-WE, il settore IT può applicare criteri di protezione dati. Con un profilo di lavoro, i criteri di prevenzione della perdita dei dati (DLP) vengono applicati a livello di profilo di lavoro, non a livello di app. Ad esempio, la protezione da operazioni copia e incolla viene applicata dalle impostazioni APP applicate a un'app, oppure viene implementata dal profilo di lavoro. Quando l'app viene distribuita in un profilo di lavoro, gli amministratori possono sospendere la protezione da operazioni copia e incolla nel profilo di lavoro disattivando questo criterio al livello APP.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Suggerimenti per ottimizzare l'esperienza con il profilo di lavoro

### <a name="when-to-use-app-within-work-profiles"></a>Quando usare i criteri APP all'interno dei profili di lavoro

I criteri APP di Intune e i profili di lavoro sono tecnologie complementari che possono essere usate insieme o separatamente. A livello di architettura, entrambe le soluzioni applicano criteri a livelli diversi: APP al livello delle singole app e il profilo di lavoro al livello del profilo. La distribuzione di app gestite con un criterio APP a un'app in un profilo di lavoro è uno scenario valido e supportato. L'uso dei criteri APP, dei profili di lavoro o di una combinazione delle due soluzioni dipende dai requisiti di prevenzione della perdita dei dati.

Le impostazioni dei profili di lavoro e dei criteri APP possono integrarsi tra loro e garantire copertura aggiuntiva se un profilo non soddisfa i requisiti di protezione dati dell'organizzazione. Ad esempio, i profili di lavoro non includono a livello nativo controlli per impedire a un'app di salvare dati in un percorso di archiviazione cloud non attendibile. I criteri APP includono questa funzionalità. Si può decidere che la prevenzione della perdita dei dati garantita dal profilo di lavoro è sufficiente e scegliere di non usare i criteri APP. Oppure si può decidere che è necessaria la protezione garantita da una combinazione delle due soluzioni.

### <a name="suppress-app-policy-for-work-profiles"></a>Eliminare i criteri APP per i profili di lavoro

In certi casi è necessario supportare singoli utenti che hanno più dispositivi: dispositivi non gestiti in uno scenario APP-WE e dispositivi gestiti con i profili di lavoro.

Ad esempio, si richiede agli utenti finali di immettere un PIN quando aprono un'app di lavoro. A seconda del dispositivo, le funzionalità PIN vengono gestite dai criteri APP o dal profilo di lavoro. Per i dispositivi APP-WE, la funzionalità PIN per l'avvio è implementata dai criteri APP. Per i dispositivi con il profilo di lavoro, è possibile usare il PIN del dispositivo o quello del profilo di lavoro implementato dal sistema operativo. Per implementare questo scenario, configurare le impostazioni dei criteri APP in modo che non vengano applicate *quando* un'app viene distribuita in un profilo di lavoro. Se non si esegue questa configurazione l'utente finale deve immettere un PIN per il dispositivo e immettere di nuovo un PIN al livello dei criteri APP.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Controllare il comportamento delle identità multiple nei profili di lavoro

Le applicazioni Office, come Outlook e OneDrive, hanno un comportamento a identità multiple. Da un'unica istanza dell'applicazione l'utente finale può aggiungere connessioni a più account o percorsi di archiviazione cloud distinti. All'interno dell'applicazione i dati recuperati da queste posizioni possono essere separati o uniti. L'utente può anche cambiare contesto tra identità personali (user@outlook.com) e identità dell'organizzazione (user@contoso.com).

Quando si usano i profili di lavoro, può essere utile disabilitare questo comportamento con identità multiple. Se lo si disabilita, le istanze con badge dell'app nel profilo di lavoro possono essere configurate solo con un'identità dell'organizzazione. Usare l'impostazione di configurazione app Account consentiti per il supporto delle app Office per Android.

Per altre informazioni, vedere [Deploying Outlook for iOS and Android app configuration settings](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) (Distribuzione di impostazioni di configurazione app per iOS e Android).

## <a name="when-to-use-intune-app"></a>Quando usare i criteri APP di Intune

L'uso dei criteri APP di Intune è consigliato in diversi scenari di gestione di dispositivi mobili aziendali.

### <a name="older-devices-running-android-44-51-are-being-used"></a>Uso di dispositivi meno recenti che eseguono Android 4.4-5.1

Ufficialmente qualsiasi dispositivo Android 5.0 o versioni successive con Google Mobile Services supporta i profili di lavoro e può essere gestito con questa soluzione. Tuttavia alcuni dispositivi Android 5.0 e 5.1 di OEM specifici non supportano i profili di lavoro.

Se si usano versioni che non supportano i profili di lavoro (e per garantire la prevenzione della perdita dei dati dell'organizzazione nei dispositivi) è necessario usare le funzionalità dei criteri APP di Intune.

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>MDM non implementata, nessuna registrazione, servizi Google non disponibili

Alcuni clienti non implementano nessuna modalità di gestione dei dispositivi, inclusa la gestione dei profili di lavoro, per diversi motivi:

- Motivi legali e di responsabilità
- Coerenza dell'esperienza utente
- Ambiente dei dispositivi Android molto eterogeneo
- Connettività ai servizi di Google non disponibile, ma necessaria per la gestione dei profili di lavoro.

Ad esempio i clienti con sede o utenti in Cina non possono usare la gestione dei dispositivi Android, perché i servizi Google sono bloccati. In questi casi, usare i criteri APP di Intune per la prevenzione della perdita dei dati.

## <a name="summary"></a>Riepilogo

Se si usa Intune, per il programma per dispositivi Android personali (BYOD) sono disponibili sia i criteri di protezione delle app senza registrazione (APP-WE) sia i profili di lavoro Android Enterprise. La scelta tra i criteri APP-WE e i profili di lavoro dipende dai requisiti e dalle esigenze operative. In sintesi, è consigliabile usare i profili di lavoro se nei dispositivi gestiti è necessario eseguire attività MDM come la distribuzione di certificati, il push di app e così via. Usare invece APP-WE se non si vuole o non si può gestire i dispositivi e si usano solo app che supportano i criteri APP di Intune.

## <a name="next-steps"></a>Passaggi successivi
[Iniziare a usare i criteri di protezione delle app](app-protection-policy.md) oppure [registrare i dispositivi](../enrollment/android-enroll.md).
