---
title: includere il file
description: includere il file
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732623"
---
Questi avvisi forniscono importanti informazioni utili per prepararsi per le modifiche e le funzionalità di Intune future. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Modifica del flusso di lavoro di registrazione con il portale aziendale Intune nei dispositivi iOS aziendali che eseguono l'autenticazione con Assistente configurazione <!-- 1927359 -->
È prevista una modifica imminente del flusso di lavoro per la registrazione dei dispositivi iOS tramite uno dei metodi di registrazione dei dispositivi aziendali di Apple: Apple Configurator, Apple Business Manager, Apple School Manager o Apple Device Enrollment Program (DEP) quando si usa Assistente configurazione per l'autenticazione. Questa modifica si applica solo ai dispositivi registrati con affinità utente.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Dopo la distribuzione di questa modifica, i profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono essere autenticati i dispositivi e se ricevere l'app Portale aziendale. Sarà disponibile un flusso di lavoro migliorato per registrare i dispositivi iOS tramite i metodi elencati in precedenza. 

- Durante la registrazione di nuovi dispositivi e l'autenticazione con Assistente configurazione, sarà possibile scegliere se distribuire o meno automaticamente l'app Portale aziendale. Gli utenti finali non vedranno più la schermata "Identifica il dispositivo" e la schermata "Conferma il dispositivo" nel flusso di registrazione.  
- Nei dispositivi già registrati con Assistente configurazione tramite uno dei metodi di registrazione dei dispositivi aziendali di Apple, è necessario intervenire se si vuole abilitare l'accesso condizionale. Sarà necessario [configurare criteri di configurazione delle app](https://aka.ms/enrollment_setup_assistant) con un file XML specifico per effettuare il push dell'app Portale aziendale in questi dispositivi.  Se si sceglie di eseguire il push dell'app Portale aziendale in questo modo, gli utenti finali non vedranno più la schermata "Identifica il dispositivo" e la schermata "Conferma il dispositivo" nel flusso di registrazione. 
- Dopo l'implementazione di questa modifica, se l'app Portale aziendale non è stata distribuita con il profilo di configurazione app indicato in precedenza e se gli utenti finali scaricano l'app Portale aziendale dall'App Store, gli utenti potranno accedere ma verrà visualizzato un messaggio di errore. Non saranno in grado di usare l'app per l'accesso condizionale. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Se si prevede di usare il flusso di lavoro modificato, sarà necessario aggiornare le istruzioni per gli utenti finali per indicare che:

- Gli utenti finali non vedranno più le due schermate indicate in precedenza nel flusso di registrazione. 
- Dovranno eseguire l'accesso al portale aziendale quando viene distribuito automaticamente e non scaricarlo dall'App Store. 

È possibile scegliere di creare subito i criteri di configurazione delle app eventualmente necessari, in preparazione per questa modifica. Quando questo nuovo flusso di lavoro verrà implementato, nella console verranno visualizzati i profili di registrazione aggiornati. Si riceverà anche notifica di questa implementazione tramite il centro messaggi. Sarà quindi necessario intervenire in modo che gli utenti finali possano eseguire la registrazione tramite DEP autenticandosi con Assistente configurazione e in modo da poter usare il portale aziendale per l'accesso condizionale.

#### <a name="additional-information"></a>Informazioni aggiuntive 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Aggiornare l'app Portale aziendale per Android alla versione più recente <!--4536963-->
Intune rilascia periodicamente aggiornamenti per l'app Portale aziendale per Android. Nel mese di novembre 2018 è stato rilasciato un aggiornamento del portale aziendale, che comprendeva un'opzione di back-end per prepararsi per la modifica di Google dalla piattaforma di notifica esistente a Google Firebase Cloud Messaging (FCM). Quando Google ritirerà la piattaforma di notifica esistente e passerà a FCM, gli utenti finali dovranno avere aggiornato l'app Portale aziendale almeno alla versione di novembre 2018 per poter continuare a comunicare con Google Play Store.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
I dati di telemetria indicano che esistono dispositivi con una versione dell'app Portale aziendale precedente a 5.0.4269.0. Se non sono installate questa versione o versioni successive dell'app Portale aziendale, le azioni per i dispositivi avviate da professionisti IT come la cancellazione, la reimpostazione della password, l'installazione delle app disponibili e richieste e la registrazione del certificato potrebbero non funzionare come previsto. Se i dispositivi sono registrati nella soluzione MDM di Intune, è possibile visualizzare le versioni e gli utenti dell'app Portale aziendale passando ad App client -App individuate. La selezione di versioni precedenti dell'app Portale aziendale consentirà di vedere quali utenti finali hanno i dispositivi in cui non è stata aggiornata l'app Portale aziendale.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Chiedere agli utenti finali dei dispositivi Android che non sono aggiornati di aggiornare l'app Portale aziendale tramite Google Play. Inviare notifica all'help desk nel caso un utente non abbia mantenuto l'aggiornamento automatico dell'app Portale aziendale. Vedere il collegamento in Informazioni aggiuntive per altre informazioni sulla piattaforma Google FCM e su questa modifica.

#### <a name="additional-information"></a>Informazioni aggiuntive
https://firebase.google.com/docs/cloud-messaging/