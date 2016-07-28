---
title: Note sulla versione di Microsoft Intune | Microsoft Intune
description: Note sulla versione di Intune
keywords: 
author: Staciebarker
manager: arob98
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: b7643ccb64185adb1eb4326a19d56814d8667462


---

# Note sulla versione di Microsoft Intune.
Microsoft Intune è una soluzione di gestione client integrata basata su cloud che include strumenti, report e licenze di aggiornamento alla versione più recente di Windows. Consente inoltre di mantenere i computer aggiornati e protetti. Intune permette anche di gestire i dispositivi mobili in modo diretto oppure sulla rete tramite Exchange ActiveSync. Le note sulla versione seguenti descrivono informazioni importanti e problemi noti in Microsoft Intune.


## Gli utenti di Android non possono inviare messaggi di posta elettronica se è implementato l'accesso condizionale per Exchange Online.

Gli utenti che eseguono Samsung Android 5.1.1 e versioni successive sui loro dispositivi non possono inviare messaggi di posta elettronica se è stato configurato l'accesso condizionale per Exchange Online. Samsung riconosce che il problema risiede nel client di posta elettronica predefinito di Android 5.1.1 e versioni successive e sta attualmente cercando di mettere a punto una correzione.

**Soluzione alternativa 1:** consigliare agli utenti finali di usare l'app Outlook per Android.

**Soluzione alternativa 2:** per consentire agli utenti interessati dal problema di inviare messaggi di posta elettronica, seguire questa procedura:

1. Inserire l'utente interessato dal problema in un gruppo di sicurezza della sezione "gruppi di esenzione" dei criteri di accesso condizionale per Exchange Online.
2. Consentire all'utente di sincronizzare temporaneamente i messaggi di posta elettronica sul client di posta elettronica predefinito.
3. Rimuovere l'utente interessato dal gruppo di esenzione e confermare che può inviare messaggi di posta elettronica.

Microsoft continuerà a collaborare con Samsung per mettere a punto una correzione o altre soluzioni alternative.



## La modifica dei profili di accesso alla risorsa tra gruppi per iOS e Android può avere esito negativo.
**Problema:** quando si modificano i messaggi di posta elettronica o profili di accesso alle risorse SCEP (Simple Certificate Enrollment Protocol) tra i gruppi, i profili possono entrare in conflitto e generare un errore. Si supponga, ad esempio, che sia già presente un profilo di posta elettronica che punta al server di Exchange locale, destinato al Gruppo A. Si supponga quindi di creare un nuovo profilo di posta elettronica che punta a Exchange Online, destinato al Gruppo B. Se si spostano utenti dal Gruppo A al Gruppo B, i dispositivi manterranno il profilo di posta elettronica del server di Exchange locale e cercheranno di installare il profilo di posta elettronica di Exchange Online destinato al Gruppo B.

A questo punto, si verifica una delle condizioni seguenti: 
* Se i profili di posta elettronica A e B sono identici, il dispositivo rifiuta il profilo B perché tale profilo contiene già il profilo di posta elettronica A.
* Se il profilo di posta elettronica A è diverso dal profilo di posta elettronica B, come indicato nell'esempio precedente, il dispositivo finisce per avere due profili di posta elettronica.

**Nota:** per distinguere un profilo di posta elettronica dall'altro, vengono verificati il nome host e l'attributo usati per il nome utente.

In entrambi i casi, il profilo di accesso alla risorsa (profilo di posta elettronica) non è stato rimosso dal dispositivo per evitare la rimozione accidentale dell'accesso di un utente alla posta elettronica o al certificato SCEP del client.

**Soluzione alternativa**: nessuna.

## Quando si registra un dispositivo Windows 8.1 che deve autenticarsi presso un server proxy, il processo di registrazione ha esito negativo, senza fornire alcuna indicazione sulla causa dell'errore
**Problema:** quando si registra un dispositivo Windows 8.1 e il dispositivo deve autenticarsi a un server proxy durante la procedura di registrazione, se il dispositivo non ha memorizzato nella cache le credenziali del server proxy, la registrazione ha esito negativo. Quando le credenziali del server proxy non sono memorizzate nella cache del dispositivo, il processo di registrazione deve attendere che l'utente immetta tali credenziali. Tuttavia, la richiesta di fornire le credenziali del server di proxy non viene visualizzata durante il processo di registrazione. Pertanto il processo di registrazione non è in grado di autenticare il server proxy e all'utente non viene fornita alcuna indicazione su questo errore.

**Soluzione alternativa:** per i dispositivi Windows 8.1 che devono registrarsi a una rete che richiede l'uso di un server proxy autenticato, configurare e salvare le credenziali per il server proxy prima della registrazione del dispositivo. Per configurare e salvare le credenziali in un dispositivo Windows 8.1:

1.  Nel dispositivo Windows 8.1 aprire **Internet Explorer**.

2.  Quando vengono richieste le credenziali del server proxy, inserirle e selezionare l'opzione **Memorizza credenziali**.

3.  Registrare il dispositivo.

## La registrazione dei dispositivi Windows Phone 8.1 in Microsoft Intune non riesce se l'autenticazione dei dispositivi è abilitata in AD FS
**Problema:** quando si registra un dispositivo Windows Phone 8.1, la registrazione ha esito negativo se è abilitata l'impostazione facoltativa per l'autenticazione del dispositivo all'interno dei criteri di autenticazione globali in Active Directory Federated Services (AD FS).

**Soluzione alternativa:** disabilitare l'autenticazione del dispositivo nel server AD FS deselezionando **Abilita autenticazione dispositivo** in **Modifica criteri di autenticazione globali**. Per altre informazioni, vedere [Configurazione dei criteri di autenticazione](http://technet.microsoft.com/library/dn486781.aspx)


## Microsoft Intune App esegue il Wrapping dello strumento per Android non dispone della capacità di disinstallazione incorporata
**Problema:** lo **strumento Microsoft per la disposizione testo per app per Android** non dispone di una funzionalità integrata per la disinstallazione dello strumento.

**Soluzione alternativa:** passare al percorso in cui è installato lo strumento ed eliminare la directory. La posizione di installazione predefinita è **C:\Programmi (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Per altre informazioni sullo strumento per la disposizione testo per app, vedere [Preparare le app per Android per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## L'assistenza remota non è disponibile nei computer che eseguono Windows 8 o Windows 8.1
**Problema:** in questa versione, la funzionalità Assistenza remota non è disponibile nei computer che eseguono Windows 8 o Windows 8.1.

**Soluzione alternativa**: nessuna.

## Le notifiche di avviso per i destinatari aggiunti automaticamente potrebbero non funzionare
**Problema:** se un destinatario viene aggiunto automaticamente a una notifica di avviso, è possibile che non riceva le notifiche regolarmente.

**Soluzione alternativa:** per assicurarsi che i destinatari ricevano un messaggio di notifica, è necessario aggiungerli manualmente alle notifiche di avviso.

## Supporto per le lingue nel portale di anteprima di Azure
Il portale di anteprima di Azure è incorporato in una nuova piattaforma e supporta le lingue seguenti: cinese (semplificato), cinese (tradizionale), ceco, olandese, inglese, tedesco, ungherese, italiano, giapponese, portoghese (Brasile), portoghese (Portogallo), russo, spagnolo, francese, coreano, polacco, svedese e turco.

La console di amministrazione di Intune e Admin Console e le app mobili per l'utente finale supportano le lingue seguenti: danese, greco, finlandese, norvegese e romeno, oltre a tutte le lingue supportate dal portale di anteprima di Azure.



<!--HONumber=Jul16_HO3-->


