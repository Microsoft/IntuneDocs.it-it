---
title: "Novità dell&quot;anteprima di Microsoft Intune | Anteprima di Intune in Azure | Documentazione Microsoft"
description: "Anteprima di Intune in Azure: novità dell&quot;anteprima di Intune di Azure"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/02/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e405363f9d0a89b1589b01d18ee8d2861b07ec60
ms.openlocfilehash: 70007f5501fba37964a0a54807c0e0f565510a74


---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Novità dell'anteprima di Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Con il progresso dell'anteprima pubblica e l'aggiunta di altre funzionalità, verrà inviata notifica qui.

<!--## February 2017-->

<!--### Custom app categories <!--748805
You can now create, edit, and assign categories for apps you add to Intune. Currently, categories can only be specified in English.
See [How to add an app to Intune](/intune-azure/manage-apps/add-apps).-->

<!--### Display device categories <!--814654
You can now view the device category as a column in the device list. You can also edit the category from the properties section of the device properties blade.-->

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



<!--HONumber=Feb17_HO1-->


