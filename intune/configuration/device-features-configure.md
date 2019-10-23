---
title: Creare profili di dispositivo iOS o macOS in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di dispositivo iOS o macOS e quindi configurare le impostazioni per AirPrint, layout della schermata iniziale, notifiche delle app, dispositivi condivisi, Single Sign-On e filtro del contenuto Web in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54d7ccabf958c3b8532f1a115724559607783a57
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495229"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Aggiungere impostazioni relative alle funzionalità dei dispositivi iOS e macOS in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune include molte funzionalità e numerose impostazioni che consentono agli amministratori di controllare i dispositivi iOS e macOS. Gli amministratori sono ad esempio in grado di:

- Consentire agli utenti l'accesso alle stampanti AirPrint presenti nella rete
- Aggiungere alla schermata iniziale app e cartelle, nonché nuove pagine
- Scegliere se e come visualizzare le notifiche delle app
- Configurare la schermata di blocco in modo da visualizzare un messaggio o il tag asset, in particolare per i dispositivi condivisi
- Offrire agli utenti un'esperienza Single Sign-On sicura per la condivisione delle credenziali tra app diverse
- Filtrare i siti Web che usano un linguaggio non adatto ai minori e consentire o bloccare siti Web specifici

Intune usa "profili di configurazione" per creare e personalizzare queste impostazioni per le esigenze dell'organizzazione. Dopo aver aggiunto queste funzionalità in un profilo, è possibile eseguire il push o distribuire il profilo nei dispositivi iOS e macOS nell'organizzazione.

Questo articolo descrive le diverse funzionalità che è possibile configurare e le modalità di creazione di un profilo di configurazione del dispositivo. È anche possibile visualizzare tutte le impostazioni disponibili per i dispositivi [iOS](ios-device-features-settings.md) e [macOS](macos-device-features-settings.md).

## <a name="airprint"></a>AirPrint

AirPrint è una funzionalità di Apple che consente ai dispositivi di stampare su file su una rete wireless. In Intune è possibile aggiungere informazioni AirPrint ai dispositivi.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere [AirPrint in iOS](ios-device-features-settings.md#airprint) e [AirPrint in macOS](macos-device-features-settings.md#airprint).

Per maggiori dettagli su AirPrint, consultare le [informazioni su AirPrint](https://support.apple.com/HT201311) sul sito Web di Apple.

Si applica a:

- iOS 7.0 e versioni successive
- iPadOS 13.0 e versioni successive
- macOS 10.10 e versioni successive

## <a name="app-notifications"></a>Notifiche delle app

Scegliere la modalità di ricezione delle notifiche delle app nei dispositivi iOS e iPad. Ad esempio, da Intune inviare le notifiche delle app in modo che vengano visualizzate nel centro notifiche, appaiano nella schermata di blocco o riproducano un suono.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere le [notifiche delle app in iOS](ios-device-features-settings.md#app-notifications).

Per altre informazioni su questa funzionalità, vedere la sezione relativa alle [notifiche](https://developer.apple.com/notifications/) nel sito Web di Apple.

Si applica a:

- iOS 9.3 e versioni successive
- iPadOS 13.0 e versioni successive

## <a name="associated-domains"></a>Domini associati

I domini associati consentono di creare una relazione tra i domini, ad esempio `contoso.com`, e le app. Questa funzionalità consente di:

- Condividere i dati e le credenziali di accesso tra le app e i siti Web dell'organizzazione.
- Usare le funzionalità delle app basate sul sito Web, ad esempio l'estensione dell'app Single Sign-On, i collegamenti universali e il riempimento automatico delle password.

  Ad esempio, creare un dominio associato per consentire il riempimento automatico delle password per consigliare le credenziali, ad esempio una password, per i siti Web associati all'app.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere l'articolo sui [domini associati in macOS](macos-device-features-settings.md#associated-domains).

Per altre informazioni su questa funzionalità, vedere l'articolo sull'[impostazione dei domini associati di un'app](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains) nel sito Web di Apple.

Si applica a:

- macOS 10.15 e versioni successive

## <a name="home-screen-layout"></a>Layout della schermata iniziale

Queste impostazioni configurano il layout delle app e le cartelle nel dock e nelle schermate iniziali dei dispositivi iOS e iPadOS. È possibile scegliere le opzioni seguenti:

- Usare le impostazioni del **dock** per aggiungere app o cartelle allo schermo. Ad esempio, per visualizzare Safari e l'app di posta elettronica sul dock del dispositivo.
- Aggiungere le **pagine** che verranno visualizzate nella schermata iniziale e le app che verranno visualizzate in ogni pagina. Ad esempio, aggiungere una pagina **Contoso** e aggiungere l'app Impostazioni in questa pagina.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere l'articolo sul [layout della schermata Home in iOS](ios-device-features-settings.md#home-screen-layout).

Si applica a:

- iOS 9.3 e versioni successive
- iPadOS 13.0 e versioni successive

## <a name="lock-screen-message"></a>Messaggio della schermata di blocco

Usare queste impostazioni per visualizzare un messaggio o un testo personalizzato nella finestra di accesso e nella schermata di blocco. È ad esempio possibile immettere il messaggio "In caso di ritrovamento, restituire a" e visualizzare informazioni sul tag asset.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere l'articolo sulle [impostazioni dei messaggi della schermata di blocco in iOS](ios-device-features-settings.md#lock-screen-message).

Per altre informazioni sul messaggio della schermata di blocco, vedere [LockScreenMessage](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) sul sito Web di Apple.

Si applica a:

- iOS 9.3 e versioni successive
- iPadOS 13.0 e versioni successive

## <a name="login-items"></a>Elementi di accesso

Usare questa funzionalità per scegliere le app, le app personalizzate, i file e le cartelle che si aprono quando gli utenti accedono ai dispositivi. 

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere l'articolo sugli [elementi di accesso in macOS](macos-device-features-settings.md#login-items).

Si applica a:

- macOS 10.13 e versioni successive

## <a name="login-window"></a>Finestra di accesso

Controllare l'aspetto della schermata di accesso e delle funzioni disponibili agli utenti prima dell'accesso. Ad esempio, aggiungere un banner con un messaggio personalizzato, scegliere se deve essere visualizzato il pulsante di sospensione e altro ancora.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere l'articolo sulla [finestra di accesso in macOS](macos-device-features-settings.md#login-window).

Si applica a:

- macOS 10.7 e versioni successive

## <a name="single-sign-on"></a>Accesso Single Sign-On

La maggior parte delle app line-of-business (LOB) richiedono un certo livello di autenticazione utente per il supporto della sicurezza. In molti casi l'autenticazione richiede di immettere ripetutamente le stesse credenziali. Per migliorare l'esperienza utente, gli sviluppatori possono creare app che usano l'accesso Single Sign-On (SSO). L'uso dell'accesso Single Sign-On riduce il numero di volte in cui un utente deve immettere le credenziali.

Per usare l'accesso Single Sign-On, assicurarsi di avere:

- Un'app sviluppata in modo da cercare l'archivio delle credenziali utente in Single Sign-On sul dispositivo.
- Intune configurato per l'accesso Single Sign-On al dispositivo iOS.

![Riquadro Single Sign-On](./media/device-features-configure/sso-blade.png)

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere l'[accesso Single Sign-On in iOS](ios-device-features-settings.md#single-sign-on).

Si applica a:

- iOS 7.0 e versioni successive
- iPadOS 13.0 e versioni successive

## <a name="single-sign-on-app-extension"></a>Estensione dell'app Single Sign-On

Queste impostazioni configurano un'estensione dell'app che abilita l'accesso Single Sign-On (SSO) per i dispositivi iOS, iPadOS e macOS. La maggior parte delle app line-of-business e dei siti Web dell'organizzazione richiede un certo livello di autenticazione utente sicura. In molti casi l'autenticazione richiede di immettere ripetutamente le stesse credenziali. SSO consente agli utenti di accedere alle app e ai siti Web dopo aver immesso le credenziali una sola volta. Dopo l'accesso, gli utenti possono accedere automaticamente alle app e ai siti Web oppure usare Face ID, Touch ID o il passcode Apple per ottenere l'accesso.

In Intune usare queste impostazioni per configurare l'estensione Kerberos predefinita di Apple o per configurare un'estensione dell'app SSO creata dall'organizzazione. L'estensione dell'app SSO gestisce l'autenticazione per gli utenti. Queste impostazioni consentono di configurare estensioni dell'app SSO basate sulle credenziali, progettate per i flussi di autenticazione con richiesta di verifica e risposta. È possibile scegliere tra un'estensione con credenziali specifiche di Kerberos di Apple e un'estensione con credenziali generiche.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere gli articoli sull'[estensione dell'app SSO per iOS](ios-device-features-settings.md#single-sign-on-app-extension) e sull'[estensione dell'app SSO per macOS](macos-device-features-settings.md#single-sign-on-app-extension).

Per altre informazioni sullo sviluppo di un'estensione dell'app SSO, vedere l'articolo su [Enterprise SSO estendibile](https://developer.apple.com/videos/play/tech-talks/301) sul sito Web di Apple.

> [!NOTE]
> La funzionalità di **estensione dell'app Single Sign-On** è diversa dalla funzionalità **Single Sign-On**:
>
> - Le impostazioni dell'**estensione dell'app SSO** si applicano a iPadOS 13.0 (e versioni successive) e iOS 13.0 (e versioni successive). Le impostazioni di **Single Sign-On** si applicano a iPadOS 13.0 (e versioni successive) e iOS 7.0 (e versioni successive).
> - Un'**estensione dell'app Single Sign-On** gestisce l'autenticazione con il sistema operativo. In **Single Sign-On** un'app specifica gestisce l'autenticazione.
> - Quando si usa l'estensione dell'**app Single Sign-On** gli utenti possono accedere alle app e ai siti Web in modo invisibile all'utente o con Face ID, Touch ID o il pincode o passcode di Apple. Quando si usa l'accesso **Single Sign-On** gli utenti possono accedere ad app e siti Web usando un'altra app.
>
>    L'**estensione dell'app Single Sign-On** usa il sistema operativo Apple per l'autenticazione. Quindi, può offrire una migliore esperienza all'utente finale.
>
> - Dal punto di vista dello sviluppo, l'**estensione dell'app Single Sign-On** può usare qualsiasi tipo di autenticazione SSO delle credenziali. Con **Single Sign-On** è possibile usare solo l'autenticazione SSO Kerberos.  

Si applica a:

- iOS 13.0 e versioni successive
- iPadOS 13.0 e versioni successive
- macOS 10.15 e versioni successive

## <a name="wallpaper"></a>Wallpaper

Aggiungere un'immagine PNG, JPG o JPEG personalizzata ai dispositivi iOS con supervisione. Ad esempio, usare Intune per aggiungere un logo aziendale alla schermata di blocco dei dispositivi.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere le [impostazioni dello sfondo in iOS](ios-device-features-settings.md#wallpaper).

Si applica a:

- iOS
- iPadOS 13.0 e versioni successive

## <a name="web-content-filter"></a>Filtro contenuto Web

Queste impostazioni possono usare l'algoritmo AutoFilter integrato di Apple per valutare le pagine Web e bloccare il contenuto e il linguaggio non adatti ai minori. È anche possibile creare un elenco di collegamenti Web consentiti e di collegamenti Web limitati. Ad esempio, è possibile consentire l'apertura solo dei siti Web di `contoso`.

Per un elenco delle impostazioni che è possibile configurare in Intune, vedere il [filtro dei contenuti Web in iOS](ios-device-features-settings.md#web-content-filter).

Si applica a:

- iOS 7.0 e versioni successive
- iPadOS 13.0 e versioni successive

## <a name="create-a-device-profile"></a>Creare un profilo del dispositivo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di criterio valido è **macOS: Configura la schermata di accesso**.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:  
        - **iOS/iPadOS**
        - **macOS**
    - **Tipo di profilo**: selezionare **Funzionalità dei dispositivi**.

4. Le impostazioni configurabili variano in base alla piattaforma scelta. Scegliere la piattaforma per le impostazioni dettagliate:

    - [iOS/iPadOS](ios-device-features-settings.md)
    - [macOS](macos-device-features-settings.md)

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo verrà creato e visualizzato nell'elenco dei profili. Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo averlo creato, il profilo è pronto per l'assegnazione. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Visualizzare tutte le impostazioni delle funzionalità per i dispositivi [iOS](ios-device-features-settings.md) e [macOS](macos-device-features-settings.md).
