---
title: Introduzione a Microsoft Intune App SDK | Microsoft Intune
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: a042f0c6206e9aaf4ec0eb012a70930aa95ecc47


---

# Introduzione a Microsoft Intune App SDK

Questa guida introduttiva illustra come abilitare rapidamente un'app per dispositivi mobili per la gestione di applicazioni mobili con Microsoft Intune. Può essere utile per capire i vantaggi di Intune App SDK descritti nella [panoramica di Intune App SDK](intune-app-sdk.md).

Questa guida descrive i passaggi principali necessari per abilitare la gestione delle app mobili in un'app con Microsoft Intune. Intune App SDK supporta scenari simili su più piattaforme e mira a creare un'esperienza coerente nelle diverse piattaforme per gli amministratori IT. A causa delle limitazioni delle piattaforme, tuttavia, il supporto di alcune funzionalità può essere leggermente diverso.

# Guida introduttiva

## Registrarsi a Microsoft Connect

Intune App SDK è attualmente accessibile tramite Microsoft Connect e prevede che si esegua l'accesso. A questo scopo, richiedere un [account Microsoft](https://connect.microsoft.com/ConfigurationManagervnext/InvitationUse.aspx?ProgramID=8967&InvitationID=8967-YJYJ-8G6X) usando il proprio indirizzo di posta elettronica aziendale.

La registrazione resterà in sospeso fino a quando il team Intune non prenderà in esame la richiesta. Il tempo di risposta è generalmente di 2-3 giorni lavorativi. Dopo l'approvazione, si riceverà una notifica tramite posta elettronica con i collegamenti per scaricare Intune App SDK per le piattaforme in uso e tutte le guide correlate. Queste guide sono accessibili anche sul sito MSDN.

## Registrare l'app store in Microsoft Intune

**Se l'app abilitata è interna all'azienda e non verrà resa disponibile sull'app store di Apple o Google**: non è necessario registrare l'app. Per queste app interne, l'amministratore IT le caricherà direttamente nella console di Microsoft Intune per la distribuzione, Intune rileverà che l'app è stata compilata con l'SDK e offrirà all'amministratore IT la possibilità di applicare i criteri MAM. È possibile passare alla sezione [Abilitare un'app per dispositivi mobili iOS e Android per MAM con l'SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Se si è un ISV che sviluppa un'app che verrà resa disponibile ai clienti tramite l'app store di Apple o Google**: è necessario innanzitutto registrare l'app in Microsoft Intune e accettare le condizioni di registrazione. In questa fase è possibile fornire il collegamento diretto dell'app. In seguito, un amministratore IT potrà applicare i criteri MAM di Intune all'app. Fino alla conclusione della registrazione e all'avvenuta conferma da parte del team di Intune, il collegamento diretto dell'app non avrà la possibilità di applicare i criteri MAM nella console di amministrazione. Microsoft gestisce anche un sito Web per i partner di Microsoft Intune in cui verrà registrata l'app affinché i clienti sappiano che supporta i criteri MAM di Microsoft Intune.

Per avviare il processo di registrazione, **esaminare e firmare** il [contratto per i partner di Microsoft Intune](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806). In questo contratto sono indicate le condizioni che la società deve accettare per poter diventare partner di app di Microsoft Intune. Per visualizzare il documento, è necessario eseguire l'accesso. Il contratto è reperibile nel sito Microsoft Connect per Intune App SDK, nella scheda Sondaggi, oppure qui. Verrà anche chiesto di specificare il nome dell'app, il nome della società, nonché il collegamento diretto all'app per l'app store di Google o iTunes.

![Microsoft Connect](../media/microsoft-connect.png)

L'indirizzo di posta elettronica della registrazione verrà usato per confermare la ricezione e completare il processo di registrazione. Lo stesso indirizzo verrà usato anche per contattare l'utente per eventuali chiarimenti.

**Cosa accade durante il processo di registrazione**: dopo l'invio del modulo, si verrà contattati da Microsoft all'indirizzo di posta elettronica fornito per la registrazione per confermare la ricezione o per richiedere altre informazioni per completare la registrazione. Si verrà contattati anche al termine della registrazione dell'app in Microsoft Intune e quando l'app è disponibile sul sito dei partner di Microsoft Intune. Una volta confermata la ricezione delle informazioni, il collegamento diretto dell'app verrà incluso nel successivo aggiornamento mensile del servizio Intune. Ad esempio, se le informazioni di registrazione vengono completate nel mese di luglio, il collegamento diretto dell'app sarà supportato a metà agosto. Se in futuro il collegamento diretto all'app store dovesse cambiare, sarà necessario registrare nuovamente l'app. È necessario anche comunicare se l'app viene aggiornata con una nuova versione di Intune App SDK.

**Nota**: tutte le informazioni raccolte nel modulo precedente e nella corrispondenza tramite posta elettronica con il team di Intune rispetteranno l' [Informativa sulla privacy Microsoft](https://www.microsoft.com/en-us/privacystatement/default.aspx).

## Abilitare un'app per dispositivi mobili iOS e Android per MAM con l'SDK

Per abilitare un'app per dispositivi mobili iOS, è necessario quanto segue:

1. **[Manuale dello sviluppatore di Microsoft Intune App SDK per iOS](intune-app-sdk-ios.md)**: questo documento descrive in dettaglio come abilitare l'app per dispositivi mobili iOS con Intune App SDK. Il documento è disponibile nella cartella della documentazione scaricata insieme al pacchetto di Intune App SDK.
2. **Intune App SDK per iOS**: nell'ambito del pacchetto Intune App SDK scaricato da Microsoft Intune è presente una cartella "Intune App SDK for iOS". Questa cartella include tutto il contenuto di Intune App SDK per iOS.

Per abilitare un'app per dispositivi mobili Android con Intune App SDK, è necessario quanto segue:

1. **[Manuale dello sviluppatore di Microsoft Intune App SDK per Android](intune-app-sdk-android.md)**: questo documento descrive in dettaglio come abilitare l'app per dispositivi mobili Android con Intune App SDK. Il documento è disponibile nella cartella della documentazione scaricata insieme al pacchetto di Intune App SDK.
2. **Intune App SDK per Android**: nell'ambito del pacchetto Intune App SDK scaricato da Microsoft Intune è presente una cartella "Intune App SDK for Android". Questa cartella include tutto il contenuto di Intune App SDK per Android.

## Disattivazione della telemetria per l'app

**Intune App SDK per iOS**: l'SDK registra i dati della telemetria SDK negli eventi di utilizzo per impostazione predefinita. Questi dati vengono inviati a Microsoft Intune.

Se si sceglie di non inviare i dati della telemetria SDK a Microsoft Intune dall'applicazione, è **necessario disabilitare** la trasmissione della telemetria SDK impostando la proprietà `MAMTelemetryDisabled` su ‘YES’ in `IntuneMAMSettings`.

**Intune App SDK per Android**: i dati della telemetria SDK non vengono registrati con l'SDK.

## Testare l'app abilitata per MAM con Microsoft Intune

Dopo aver completato i passaggi necessari per abilitare (integrare Intune App SDK) il proprio Intune App SDK per iOS o Android, è necessario assicurarsi che tutti i criteri di gestione delle app siano abilitati e funzionanti per l'utente finale e l'amministratore IT. Per testare l'app abilitata, è necessario quanto segue:

1. **Test dell'app abilitata per MAM con Microsoft Intune**: questo documento illustra in dettaglio come testare le app iOS e Android abilitate per MAM con Microsoft Intune. Il documento è disponibile nella cartella della documentazione scaricata insieme al pacchetto di Intune App SDK.
2. **Account di Microsoft Intune**: per testare le app abilitate per MAM con Microsoft Intune, è necessario un account di Microsoft Intune. Quando un ISV abilita le proprie app dello store iOS e Android per MAM, riceverà un codice promozionale al termine della registrazione in Microsoft Intune come descritto nel passaggio relativo alla registrazione. Con il codice promozionale sarà possibile richiedere una versione di valutazione di Microsoft Intune per 1 anno di utilizzo esteso. Se si sta sviluppando un'app line-of-business che non verrà inviata allo store, l'accesso a Microsoft Intune deve essere fornito dall'organizzazione. Si può anche richiedere 1 mese di valutazione gratuita con [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).




<!--HONumber=Jul16_HO3-->


