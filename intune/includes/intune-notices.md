---
title: includere il file
description: includere il file
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: d907c5256469e86410c9916d117d3e322d43cfc3
ms.sourcegitcommit: 2614d1b08b8a78cd792aebd2ca9848f391df8550
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67812503"
---
Questi avvisi forniscono importanti informazioni utili per prepararsi per le modifiche e le funzionalità di Intune future. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Aggiornare l'app Portale aziendale per Android alla versione più recente <!--4536963-->
Intune rilascia periodicamente aggiornamenti per l'app Portale aziendale per Android. Nel mese di novembre 2018 è stato rilasciato un aggiornamento del portale aziendale, che comprendeva un'opzione di back-end per prepararsi per la modifica di Google dalla piattaforma di notifica esistente a Google Firebase Cloud Messaging (FCM). Quando Google ritirerà la piattaforma di notifica esistente e passerà a FCM, gli utenti finali dovranno avere aggiornato l'app Portale aziendale almeno alla versione di novembre 2018 per poter continuare a comunicare con Google Play Store.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
I dati di telemetria indicano che esistono dispositivi con una versione dell'app Portale aziendale precedente a 5.0.4269.0. Se non sono installate questa versione o versioni successive dell'app Portale aziendale, le azioni per i dispositivi avviate da professionisti IT come la cancellazione, la reimpostazione della password, l'installazione delle app disponibili e richieste e la registrazione del certificato potrebbero non funzionare come previsto. Se i dispositivi sono registrati nella soluzione MDM di Intune, è possibile visualizzare le versioni e gli utenti dell'app Portale aziendale passando ad App client -App individuate. La selezione di versioni precedenti dell'app Portale aziendale consentirà di vedere quali utenti finali hanno i dispositivi in cui non è stata aggiornata l'app Portale aziendale.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Chiedere agli utenti finali dei dispositivi Android che non sono aggiornati di aggiornare l'app Portale aziendale tramite Google Play. Inviare notifica all'help desk nel caso un utente non abbia mantenuto l'aggiornamento automatico dell'app Portale aziendale. Vedere il collegamento in Informazioni aggiuntive per altre informazioni sulla piattaforma Google FCM e su questa modifica.

#### <a name="additional-information"></a>Informazioni aggiuntive
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Nuova esperienza con singola schermata presto disponibile in Intune <!--4593669-->
È in corso l'implementazione di esperienze aggiornate dell'interfaccia utente per la creazione e la modifica in Intune nel portale di Azure. Questa nuova esperienza consentirà di semplificare i flussi di lavoro esistenti usando un formato in stile procedura guidata sintetizzato in un solo pannello. Con questo aggiornamento scompariranno la distesa di pannelli o tutti i flussi di lavoro di creazione e modifica che richiedono il drill-down in lunghe sequenze di pannelli annidati. I flussi di lavoro di creazione verranno inoltre aggiornati per includere le assegnazioni (ad eccezione dell'assegnazione di app).

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
L'esperienza con singola schermata verrà implementata in Intune sia in portal.azure.com che in devicemanagement.microsoft.com nei prossimi mesi. Questo aggiornamento dell'interfaccia utente non avrà impatto sulle funzionalità dei criteri e dei profili esistenti, ma si noteranno leggere modifiche del flusso di lavoro. Quando si creano nuovi criteri, ad esempio, sarà possibile impostare alcune assegnazioni nell'ambito di questo flusso anziché dopo aver creato i criteri. Vedere il post di blog in Informazioni aggiuntive per visualizzare alcuni screenshot dell'aspetto della nuova esperienza nella console.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Non è necessario intraprendere alcuna azione, ma è possibile valutare l'eventuale necessità di aggiornare le istruzioni per i professionisti IT. La documentazione verrà aggiornata non appena questa esperienza verrà implementata nei vari pannelli in Intune nel portale di Azure.

#### <a name="additional-information"></a>Informazioni aggiuntive 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>Modifica prevista: Supporto di Intune per iOS 11 e versioni successive in settembre <!-- 4665342-->
Per il mese di settembre è previsto il rilascio di iOS 13 da Apple. La registrazione di Intune, il portale aziendale e Managed Browser supporteranno iOS 11 e versioni successive poco dopo il rilascio di iOS 13.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se le app per dispositivi mobili O365 sono supportate in iOS 11.0 e versioni successive, questa modifica potrebbe non interessare l'utente in quanto l'aggiornamento del sistema operativo o dei dispositivi è stato probabilmente già eseguito. Se tuttavia si hanno i dispositivi inclusi nell'elenco seguente o se si decide di registrare un dispositivo tra quelli elencati, tenere presente che questi dispositivi non supportano sistemi operativi successivi a iOS 10. Questi dispositivi dovranno essere aggiornati a un dispositivo che supporta iOS 11 o versione successiva:

- iPhone 5
- iPhone 5c
- iPad (quarta generazione)

A partire da luglio, nei dispositivi registrati in MDM con iOS 10 e il portale aziendale verrà visualizzato un messaggio di avviso per l'aggiornamento del sistema operativo o del dispositivo. Se si usano i criteri di protezione delle app, è anche possibile attivare l'impostazione di accesso "Richiedi un sistema operativo iOS minimo (solo avviso)".

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Controllare i report di Intune per vedere quali dispositivi o utenti possono essere interessati. Passare a **Dispositivi** > **Tutti i dispositivi** e filtrare in base al sistema operativo. È possibile aggiungere altre colonne per facilitare l'identificazione degli utenti dell'organizzazione che hanno dispositivi che eseguono iOS 10. Richiedere agli utenti finali di aggiornare i dispositivi a una versione supportata del sistema operativo prima di settembre.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Modifica prevista: Supporto per le versioni 8.1.1 e successive di Intune App SDK per iOS <!-- 3586942-->
A partire da settembre 2019, Intune supporterà le app iOS con Intune App SDK 8.1.1 e versioni successive. Le app create con versioni dell'SDK precedenti alla 8.1.1 non saranno più supportate. Questa modifica entrerà in vigore con il rilascio da parte di Apple di iOS 13, previsto intorno a settembre e anche annunciato in MC181399.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Con l'integrazione di Intune App SDK o del wrapping delle app, è possibile proteggere i dati aziendali da applicazioni e utenti non approvati tramite la crittografia dei dati. Intune App SDK per iOS userà per impostazione predefinita chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app di Intune. Dopo questa modifica, tutte le app iOS con versioni dell'SDK precedenti alla 8.1.1, che usano chiavi di crittografia a 128 bit, non saranno più in grado di condividere i dati con le applicazioni integrate con l'SDK 8.1.1 o che usano chiavi a 256 bit. Tutte le app iOS dovranno avere un SDK versione 8.1.1 o superiore per consentire la condivisione protetta dei dati.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Controllare le app Microsoft, di terze parti e line-of-business (LOB). È necessario assicurarsi che tutte le applicazioni protette con criteri di protezione delle app di Intune usino l'SDK versione 8.1.1 o successiva.

- Per le app line-of-business: Potrebbe essere necessario ripubblicare le app integrate con l'SDK versione 8.1.1 o successiva. È consigliabile usare la versione più recente dell'SDK. Per informazioni su come preparare le app line-of-business per i criteri di protezione delle app, vedere [Preparare le app line-of-business per i criteri di protezione delle app](../apps-prepare-mobile-application-management.md).
- Per le app Microsoft o di terze parti: Assicurarsi di distribuire agli utenti la versione più recente di queste app.

Se applicabile, aggiornare anche la documentazione o il materiale sussidiario per lo sviluppo per includere questa modifica relativa al supporto per l'SDK.

#### <a name="additional-information"></a>Informazioni aggiuntive
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Modifica prevista: Nuove impostazioni per gli aggiornamenti di Windows in Intune <!-- 4464404 -->
A partire dalla versione di agosto per il servizio Intune o 1908, verranno aggiunte nuove "impostazioni per la scadenza" che è possibile configurare al posto delle impostazioni "Consenti all'utente di riavviare (riavvio in caso di occupato)". È prevista la disabilitazione delle impostazioni di riavvio in caso di occupato nell'interfaccia utente nella versione 1909 o nell'aggiornamento di settembre e quindi la rimozione completa di queste impostazioni dalla console verso la fine di ottobre. 

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se si gestiscono i dispositivi Windows 10 nell'ambiente: 
- Con l'aggiornamento di Intune di agosto o la versione 1908 le nuove impostazioni di scadenza verranno visualizzate nella console oltre alle impostazioni di riavvio in caso di occupato precedenti.
- Quando vengono configurate entrambe le impostazioni precedenti e nuove, i valori delle impostazioni di scadenza avranno priorità rispetto ai valori dell'impostazione di riavvio in caso di occupato.
- Le impostazioni di scadenza sostituiranno l'opzione "Consenti all'utente di riavviare (riavvio in caso di occupato)" nella console nell'aggiornamento 1910.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Iniziare a usare le impostazioni di scadenza nella versione 1908, configurandole con i valori desiderati. Dopo averle configurate, è possibile impostare l'opzione di riavvio in caso di occupato su "Non configurato" per prepararsi per la rimozione dalla console in ottobre.

Se necessario, aggiornare la documentazione e gli eventuali script di automazione. 

Verranno pubblicati aggiornamenti e un promemoria nel centro messaggi prima di rimuovere le impostazioni di riavvio in caso di occupato.
