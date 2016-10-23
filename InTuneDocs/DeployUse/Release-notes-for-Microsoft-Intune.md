---
title: Note sulla versione di Microsoft Intune | Microsoft Intune
description: Note sulla versione di Intune
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f1147e5fe766bc4642439c4ad23b2fdfbf74bb03
ms.openlocfilehash: da476088435d6ef8bd58ecad1b221254a30858cc


---

# Note sulla versione di Microsoft Intune.
Microsoft Intune è una soluzione di gestione client integrata basata su cloud che include strumenti, report e licenze di aggiornamento alla versione più recente di Windows e consente di mantenere i computer aggiornati e protetti. Intune permette anche di gestire i dispositivi mobili in modo diretto oppure sulla rete tramite Exchange ActiveSync. Le note sulla versione seguenti descrivono informazioni importanti e problemi noti in Microsoft Intune.


## Gli utenti di Android non possono inviare messaggi di posta elettronica se è implementato l'accesso condizionale per Exchange Online.

**Problema:** gli utenti che eseguono Samsung Android 5.1.1 e versioni successive nei loro dispositivi non possono inviare messaggi di posta elettronica se è stato impostato l'accesso condizionale per Exchange Online. Samsung riconosce che il problema risiede nel client di posta elettronica predefinito di Android 5.1.1 e versioni successive e sta cercando di mettere a punto una correzione.

**Soluzione alternativa 1:** consigliare agli utenti di usare l'app Outlook per Android.

**Soluzione alternativa 2:** per consentire agli utenti interessati di inviare messaggi di posta elettronica, seguire questa procedura:

1. Inserire tutti gli utenti interessati dal problema in un gruppo di sicurezza della sezione "Gruppi esentati" dei criteri di accesso condizionale per Exchange Online.
2. Consentire agli utenti di sincronizzare temporaneamente la posta elettronica nel client di posta elettronica predefinito.
3. Rimuovere gli utenti interessati dal gruppo esentato e verificare che ora possano inviare messaggi di posta elettronica.

Microsoft continuerà a collaborare con Samsung per mettere a punto una correzione o altre soluzioni alternative.



## La modifica dei profili di accesso alle risorse tra gruppi per iOS e Android può avere esito negativo
**Problema:** quando si modificano i messaggi di posta elettronica o i profili di accesso alle risorse SCEP (Simple Certificate Enrollment Protocol) tra gruppi, i profili possono entrare in conflitto e generare un errore. Si supponga, ad esempio, che sia già presente un profilo di posta elettronica che punta al server di Exchange locale, destinato al Gruppo A. Si supponga quindi di creare un nuovo profilo di posta elettronica che punta a Exchange Online, destinato al Gruppo B. Se si spostano utenti dal Gruppo A al Gruppo B, i dispositivi manterranno il profilo di posta elettronica del server di Exchange locale e cercheranno di installare il profilo di posta elettronica di Exchange Online destinato al Gruppo B.

A questo punto, si verifica una delle condizioni seguenti: 
* Se i profili di posta elettronica A e B sono identici, il dispositivo rifiuta il profilo B perché tale profilo contiene già il profilo di posta elettronica A.
* Se il profilo di posta elettronica A è diverso dal profilo di posta elettronica B, come indicato nell'esempio, il dispositivo finisce per avere due profili di posta elettronica.

> [!NOTE]
> Per distinguere un profilo di posta elettronica dall'altro, vengono verificati il nome host e l'attributo usati per il nome utente.

In entrambi i casi, il profilo di accesso alla risorsa (profilo di posta elettronica) non è stato rimosso dal dispositivo per evitare la rimozione accidentale dell'accesso di un utente alla posta elettronica o del certificato SCEP del client.

**Soluzione alternativa**: nessuna.

## Quando si registra un dispositivo Windows 8.1 che deve autenticarsi presso un server proxy, il processo di registrazione ha esito negativo, senza alcuna causa evidente
**Problema:** quando si registra un dispositivo Windows 8.1 e il dispositivo deve autenticarsi a un server proxy durante la procedura di registrazione, se il dispositivo non ha memorizzato nella cache le credenziali del server proxy, la registrazione ha esito negativo. Quando le credenziali del server proxy non sono memorizzate nella cache del dispositivo, il processo di registrazione deve attendere che l'utente immetta tali credenziali. Ma la richiesta di specificare le credenziali del server di proxy non viene visualizzata durante il processo di registrazione. Il risultato è che il processo di registrazione non riesce a effettuare l'autenticazione al server proxy. Per l'utente non viene visualizzata alcuna indicazione visibile di questo errore.

**Soluzione alternativa:** per i dispositivi Windows 8.1 che devono registrarsi a una rete che richiede l'uso di un server proxy autenticato, configurare e salvare le credenziali per il server proxy prima della registrazione del dispositivo. Per configurare e salvare le credenziali in un dispositivo Windows 8.1:

1.  Nel dispositivo Windows 8.1 aprire Internet Explorer.
2.  Quando vengono richieste le credenziali del server proxy, inserirle e quindi scegliere l'opzione **Memorizza credenziali**.
3.  Registrare il dispositivo.

## La registrazione dei dispositivi Windows Phone 8.1 in Microsoft Intune non riesce se l'autenticazione dei dispositivi è abilitata in AD FS
**Problema:** quando si registra un dispositivo Windows Phone 8.1, la registrazione ha esito negativo se è abilitata l'impostazione facoltativa per l'autenticazione del dispositivo all'interno dei criteri di autenticazione globali in Active Directory Federation Services (AD FS).

**Soluzione alternativa:** disabilitare l'autenticazione del dispositivo nel server AD FS deselezionando **Abilita autenticazione dispositivo** in **Modifica criteri di autenticazione globali**. Per altre informazioni, vedere [Configurazione dei criteri di autenticazione](http://technet.microsoft.com/library/dn486781.aspx).


## Microsoft Intune App esegue il Wrapping dello strumento per Android non dispone della capacità di disinstallazione incorporata
**Problema:** lo **strumento Microsoft per la disposizione testo per app per Android** non dispone di una funzionalità integrata per la disinstallazione dello strumento.

**Soluzione alternativa:** passare al percorso in cui è installato lo strumento ed eliminare la directory. La posizione di installazione predefinita è **C:\Programmi (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Per altre informazioni sullo strumento per la disposizione testo per app, vedere [Preparare le app per Android per la gestione con lo strumento per la disposizione testo per app](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## L'assistenza remota non è disponibile nei computer che eseguono Windows 8 o Windows 8.1
**Problema:** in questa versione, la funzionalità Assistenza remota non è disponibile nei computer che eseguono Windows 8 o Windows 8.1.

**Soluzione alternativa**: nessuna.

## Le notifiche di avviso per i destinatari aggiunti automaticamente potrebbero non funzionare
**Problema:** i destinatari aggiunti automaticamente a una notifica di avviso potrebbero non ricevere le notifiche regolarmente.

**Soluzione alternativa:** per assicurarsi che i destinatari ricevano le notifiche dei messaggi, è necessario aggiungerli manualmente alle notifiche di avviso.

## Supporto per le lingue nel portale di Azure
Il portale di Azure supporta le lingue seguenti: cinese (semplificato), cinese (tradizionale), ceco, olandese, inglese, tedesco, ungherese, italiano, giapponese, portoghese (Brasile), portoghese (Portogallo), russo, spagnolo, francese, coreano, polacco, svedese e turco.

La console di amministrazione di Intune e le app mobili per l'utente supportano le lingue seguenti: danese, greco, finlandese, norvegese e romeno, oltre a tutte le lingue supportate dal portale di Azure.



<!--HONumber=Oct16_HO2-->


