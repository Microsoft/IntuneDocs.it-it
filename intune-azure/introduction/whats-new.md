---
title: "Novità dell&quot;anteprima di Microsoft Intune | Anteprima di Intune in Azure | Documentazione Microsoft"
description: "Novità dell&quot;anteprima di Intune in Azure"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9852fdb9d1bfeede4931f0ead2fa0898dfcacb0b
ms.openlocfilehash: a05c7464b3f2fbca467d44218904671529320dda
ms.lasthandoff: 02/15/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Novità dell'anteprima di Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Con il progresso dell'anteprima pubblica e l'aggiunta di altre funzionalità, verrà inviata notifica qui.

## <a name="february-2017"></a>Febbraio 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Possibilità di limitare la registrazione di dispositivi mobili <!--747600, 795782-->
Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.

* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.  
* Solo per iOS e Android è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Visualizzare tutte le azioni nei dispositivi gestiti <!--677150-->
Il nuovo report __Azioni del dispositivo__ mostra gli utenti che hanno eseguito azioni remote come il ripristino delle impostazioni predefinite nei dispositivi e lo stato dell'azione. Vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](https://docs.microsoft.com/intune-azure/manage-devices/what-is).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->
Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Come aggiungere un'app in Intune).

### <a name="display-device-categories---814654--"></a>Visualizzare le categorie di dispositivi <!--814654-->
È ora possibile visualizzare la categoria dei dispositivi come colonna dell'elenco dei dispositivi. È inoltre possibile modificare la categoria nella sezione delle proprietà del pannello delle proprietà del dispositivo. Vedere [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Come aggiungere un'app in Intune). 

## <a name="january-2017"></a>Gennaio 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Assegnare app line-of-business indipendentemente dalla registrazione dei dispositivi <!--748823-->
È ora possibile assegnare app line-of-business e app dallo store agli utenti, indipendentemente dal fatto che i loro dispositivi siano o meno registrati in Intune. Se il dispositivo dell'utente non è registrato in Intune, l'utente dovrà usare il sito Web del portale aziendale per installare l'app assegnata, anziché l'app Portale aziendale. Vedere [Che cos'è la gestione delle app?](/intune-azure/manage-apps/what-is-app-management)

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Risolvere il problema nel caso in cui i dispositivi iOS non sono attivi o la console di amministrazione non è in grado di comunicare con i dispositivi
Quando i dispositivi degli utenti perdono la connessione con Intune è possibile indicare nuovi passaggi per la risoluzione dei problemi per ripristinare l'accesso alle risorse aziendali. Vedere [I dispositivi sono inattivi o la console di amministrazione non è in grado di comunicare con i dispositivi](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>Dicembre 2016 (versione iniziale)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integrazione della gestione delle spese di telecomunicazione nell'anteprima pubblica del portale di Azure<!--747605-->
Stiamo iniziando a presentare in anteprima l'integrazione con i servizi di gestione delle spese di telecomunicazione di terze parti nel portale di Azure. È possibile usare Intune per imporre limiti al consumo dei dati sia nazionale che in roaming. Queste integrazioni iniziano con [Saaswedo](http://www.saaswedo.com). Per abilitare questa funzionalità nel tenant di prova, [contattare il supporto tecnico Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

- Distribuire e gestire le applicazioni da un archivio su dispositivi iOS, Android e Windows
- Distribuire e gestire le app line-of-business (LOB) su dispositivi iOS, Android e Windows
- Distribuire e gestire le app acquistate con Volume Purchase Program su dispositivi iOS e Windows
- Distribuire e gestire le app Web su dispositivi Android, iOS e Windows
- Profili di configurazione app gestiti da iOS
- Configurare i criteri di protezione delle app e distribuire app line-of-business su dispositivi non registrati su Intune
- Profili VPN, VPN per app, Wi-Fi, posta elettronica e profili di certificato
- Criteri di conformità
- Accesso condizionale per Azure AD
- Accesso condizionale per Exchange locale
- Registrazione del dispositivo
- Controllo di accesso in base ai ruoli

## <a name="deprecated-features-in-the-azure-portal"></a>Funzionalità deprecate nel portale di Azure

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Supporto per la revisione riga per riga degli identificatori di hardware
Il portale di Azure non supporta la revisione riga per riga di ID hardware per numeri IMEI e numeri di serie Apple. Nella console di Intune classica è possibile importare informazioni da un file con estensione CSV e sovrascrivere i dettagli esistenti con gli identificatori hardware singoli. Il portale di Azure prevede un'unica ed efficiente opzione che sovrascrive in automatico i dettagli per tutti gli identificatori hardware o ignora i nuovi dettagli per gli identificatori esistenti.

#### <a name="how-this-affects-you"></a>Conseguenza sull'utente
Nel portale di Azure l'utente non sarà in grado di decidere, riga per riga, quale IMEI aggiornare. La console di Intune classica continuerà a supportare questa funzionalità.

#### <a name="how-to-get-ready-for-this-change"></a>Come prepararsi a questo cambiamento
Forniamo questa informazione in anticipo in modo tale che, se l'utente ne è interessato, può comunicare il cambiamento ai propri amministratori del supporto. Questa modifica coinciderà con la migrazione al portale di Azure, prevista per la prima metà del 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Supporto per i profili predefiniti di registrazione di dispositivi aziendali in DEP di Apple
Il portale di Azure non supporta il profilo di registrazione di dispositivi aziendali "predefinito" per i numeri di serie del dispositivo DEP di Apple. Questa funzionalità, disponibile nella console di Intune classica, è stata sospesa per evitare che i profili venissero assegnati involontariamente. Nel portale di Azure i numeri di serie sincronizzati da un account DEP di Apple non saranno inizialmente assegnati a un profilo di registrazione di dispositivi aziendali.

#### <a name="how-this-affects-you"></a>Conseguenza sull'utente
Nel portale di Azure non sarà possibile impostare un criterio di profilo predefinito per tutti i dispositivi Apple. La console di Intune classica continuerà a supportare questa funzionalità.

#### <a name="how-to-get-ready-for-this-change"></a>Come prepararsi a questo cambiamento
Forniamo questa informazione in anticipo in modo tale che, se l'utente ne è interessato, può comunicare il cambiamento ai propri amministratori del supporto. Questa modifica coinciderà con la migrazione al portale di Azure, prevista per la prima metà del 2017.

