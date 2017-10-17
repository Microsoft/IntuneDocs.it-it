---
title: Informazioni su Android for Work
description: "Intune gestisce Android for Work per offrire funzionalità di gestione aggiuntive e privacy quando gli utenti usano i dispositivi Android personali per il lavoro."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 17c066ee7208790a591272ae5e1edc99cf2141a4
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="manage-android-for-work-devices-with-intune"></a>Gestire dispositivi Android for Work con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Android for Work è un set di funzionalità e servizi dei dispositivi Android che separa le app e i dati personali da quelli lavorativi inclusi in un profilo di lavoro. Android for Work offre funzionalità di gestione e privacy aggiuntive quando gli utenti usano i dispositivi Android personali per lavoro. Intune consente la distribuzione di app e risorse aziendali ai dispositivi Android for Work per assicurarsi che le informazioni di lavoro e quelle personali restino separate. Dopo la corretta implementazione, le app e i dati a cui accedono rimangono esclusivamente all'interno dell'ambiente Android for Work nel dispositivo.

## <a name="supported-devices"></a>Dispositivi supportati

La gestione di Android for Work si basa su funzionalità che fanno parte del sistema operativo Android più recente. Android for Work è attualmente supportato nei dispositivi che eseguono Android 5.0 Lollipop e versioni successive che supportano profili di lavoro. Per i dispositivi che non supportano Android for Work, rimangono disponibili le funzionalità di gestione convenzionali di Android. Altre informazioni sui [requisiti per Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Onboarding

Prima di registrare i dispositivi Android for Work, è necessario eseguire alcuni passaggi di onboarding. Questa procedura consente di stabilire una connessione tra il tenant di Intune e il servizio Play for Work di Google, che è parte integrante del processo di distribuzione e gestione delle app Android for Work. Altre informazioni sull'[abilitazione della registrazione dei dispositivi Android for Work](/intune-classic/deploy-use/set-up-android-for-work).

## <a name="work-profile-management"></a>Gestione del profilo di lavoro

Quando si gestisce un dispositivo Android for Work con Intune, non si gestisce l'intero dispositivo. Le funzionalità di gestione hanno effetti solo sul profilo di lavoro creato nel dispositivo durante la registrazione. Qualsiasi app distribuita nel dispositivo con Intune viene installata nel profilo di lavoro. Le icone dell'app nel profilo di lavoro vengono visualizzate con una valigetta arancione per differenziare le applicazioni di lavoro da quelle personali nel dispositivo. Tutti i dati e le app Android all'esterno della parte dedicata ad Android for Work del dispositivo rimangono personali e sotto il controllo dell'utente finale. Gli utenti possono installare qualsiasi app nello spazio del dispositivo destinato ai dati personali, mentre gli amministratori possono gestire e monitorare le azioni e le applicazioni eseguite nell'ambito del profilo di lavoro.

Intune offre una gamma di impostazioni generali predefinite che è possibile configurare nei dispositivi Android for Work. Altre informazioni sulle [Impostazioni dei criteri di Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="app-publishing-and-distribution"></a>Distribuzione e pubblicazione di app

Il servizio Google Play for Work è parte integrante della distribuzione e della gestione di app in Android for Work. Tutte le app distribuite in dispositivi Android for Work nel profilo di lavoro provengono dal servizio Play for Work. Per gestire e distribuire le app in Play Store, accedere al sito Web Google Play con le credenziali di amministratore della società per la gestione di Google. È possibile approvare le app per la distribuzione di Android for Work in modo che vengano visualizzate nei profili di lavoro dei dispositivi. Queste app vengono quindi sincronizzate con la console di Intune e possono essere distribuite e gestite tramite Intune. Le app line-of-business (LOB) sviluppate dall'organizzazione devono essere pubblicate in Play for Work usando la console per la pubblicazione di app Android di Google. Le app LOB devono essere configurate nella console di pubblicazione di app Android per limitare l'accesso all'organizzazione.

Le app possono essere installate senza interazioni con l'utente e senza richiedere all'utente di consentire l'**installazione da origini sconosciute**. Per cercare e installare app facoltative o disponibili, l'utente può usare lo store Play for Work nel proprio dispositivo. Altre informazioni sulla [distribuzione di app per Android for Work](/intune-classic/deploy-use/android-for-work-apps).

## <a name="app-configuration"></a>Configurazione delle app

Android for Work offre un'infrastruttura per distribuire i valori di configurazione delle app alle app che li supportano. Specificando i valori di configurazione per le app di lavoro, è possibile assicurarsi che vengano impostate correttamente quando gli utenti le avviano per la prima volta. Per il supporto della configurazione delle app è necessario che gli sviluppatori creino le app Android in modo specifico per supportare valori di configurazione gestiti. Ciò rende possibile usare Intune per specificare e applicare queste impostazioni di configurazione. Altre informazioni sulle [impostazioni di configurazione delle app Android for Work](afw-app-configuration-policy.md).

## <a name="email-configuration"></a>Configurazione della posta elettronica

Android for Work non offre un'app di posta elettronica predefinita o un oggetto profilo di posta elettronica nativo simile a quello fornito da iOS. Le configurazioni per la posta elettronica possono essere invece impostate tramite l'applicazione di impostazioni di configurazione delle app alle app di posta elettronica che le supportano. Gmail e Nine Work sono due app client Exchange ActiveSync (EAS) disponibili in Play Store che possono essere configurate con la configurazione delle app Android for Work.

Intune offre modelli di configurazione per le app Gmail e Nine Work gestite come app di lavoro. Altre app di posta elettronica che supportano i profili di configurazione delle app possono essere configurate con i criteri di configurazione delle app per dispositivi mobili.

Se si usa l'accesso condizionale di Exchange ActiveSync per dispositivi Android for Work, è necessario usare l'app di posta elettronica Gmail o Nine Work. Sono anche supportate l'app Microsoft Outlook per Android e qualsiasi altra app di posta elettronica che usa l'autenticazione moderna tramite ADAL. Altre informazioni sui [profili di posta elettronica per la posta elettronica aziendale](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="app-protection-policies"></a>Criteri di protezione delle app

I criteri di protezione delle app applicati sono completamente supportati nel profilo di lavoro e nel profilo personale. È possibile pubblicare app line-of-business nella console di pubblicazione di app Android all'indirizzo https://play.google.com/apps/publish. Questa console include un'opzione per impostare le app come private per l'organizzazione. Altre informazioni sulle [Impostazioni dei criteri di conformità per Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md). Per informazioni generali sui criteri protezione delle app, vedere l'articolo sui [criteri di protezione delle app](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

## <a name="vpn-profiles"></a>Profili VPN

Il supporto VPN è simile ai profili VPN Android. Sono disponibili gli stessi provider di VPN e le stesse opzioni di configurazione di base per la gestione di Android for Work con due differenze:

-  **VPN con ambito profilo di lavoro**: le connessioni VPN si limitano alle app distribuite nel profilo di lavoro. Solo le app gestite da Android for Work possono usare la connessione VPN. Le app personali nel dispositivo non possono usare una connessione VPN gestita.

-  **VPN specifica per app**: se un provider di VPN supporta la configurazione di connessioni VPN specifiche per le app e offre la possibilità di configurare VPN per app tramite il profilo di configurazione delle app Android for Work, è possibile configurare una connessione VPN specifica per app in Intune. Contattare il provider della connessione VPN per verificare se supporta questa funzionalità. Altre informazioni sui [profili di connessione VPN](vpn-connections-in-microsoft-intune.md).

## <a name="certificate-profiles"></a>Profili certificato

Le stesse opzioni di configurazione del profilo certificato disponibili per la gestione Android sono disponibili nei dispositivi Android for Work. Android for Work offre API per la gestione avanzata dei certificati. Le funzionalità di gestione avanzata dei certificati consentono di:

- Assicurarsi che la distribuzione dei certificati sia invisibile all'utente.
-  Assicurarsi che i certificati distribuiti vengano rimossi completamente quando un dispositivo viene ritirato da Intune e il profilo di lavoro viene rimosso.
-  Offrire comunicazioni migliori per informare gli utenti che il certificato è stato distribuito e configurato dal proprio reparto IT tramite il servizio di gestione.

Altre informazioni sui [profili certificato](secure-resource-access-with-certificate-profiles.md).

## <a name="wi-fi-profiles"></a>Profili Wi-Fi

I profili Wi-Fi gestiti da Android for Work vengono eliminati quando il dispositivo viene ritirato da Intune e il profilo di lavoro viene eliminato. Altre informazioni sui [profili Wi-Fi](wi-fi-connections-in-microsoft-intune.md).

## <a name="next-steps"></a>Passaggi successivi
[Abilitare la registrazione di dispositivi Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

[Distribuzione di app per Android for Work](/intune-classic/deploy-use/android-for-work-apps)
