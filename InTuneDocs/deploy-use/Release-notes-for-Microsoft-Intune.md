---
title: Note sulla versione di Microsoft Intune | Documentazione Microsoft
description: Note sulla versione di Intune
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f0e027d1c63435084c434c591fed7bb71b5c07f2
ms.openlocfilehash: 8369cc039ac1c4c24b29927a96360cd872f8e9bc
ms.lasthandoff: 03/08/2017


---

# <a name="release-notes-for-microsoft-intune"></a>Note sulla versione di Microsoft Intune.

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune è una soluzione di gestione client integrata basata su cloud che include strumenti, report e licenze di aggiornamento alla versione più recente di Windows e consente di mantenere i computer aggiornati e protetti. Intune permette anche di gestire i dispositivi mobili in modo diretto oppure sulla rete tramite Exchange ActiveSync. Le note sulla versione seguenti descrivono informazioni importanti e problemi noti in Microsoft Intune.

<!-- 3-6-17: customer asked if this is still current; Stacie asked Chris Baldwin about it. Chris said it's a Samsung issue, but that he hasn't heard any reports about it for months, so he suggested that I share that with the customer and remove this item from the release notes. I'm only going to comment it out in case it resurfaces.
## Android users can’t send email when conditional access for Exchange Online is implemented

**Issue:** Users running Samsung Android 5.1.1 and later on their devices can't send email when conditional access for Exchange Online has been set up. Samsung acknowledges that the issue is in its built-in email client in Android 5.1.1 and later, and is investigating a fix.

**Workaround 1:** Advise users to use the Outlook app for Android.

**Workaround 2:** To let affected users send email, you can follow these steps:

1. Put each affected user in a security group in the “exempted groups” section of the conditional access policy for Exchange Online.
2. Let the user temporarily sync email on the built-in email client.
3. Remove the affected user from the exempted group, and confirm that the user can now send email.

Microsoft will continue to work closely with Samsung on a fix or additional workarounds.
-->


## <a name="changing-resource-access-profiles-between-groups-for-ios-and-android-might-fail"></a>La modifica dei profili di accesso alle risorse tra gruppi per iOS e Android può avere esito negativo
**Problema:** quando si modificano i messaggi di posta elettronica o i profili di accesso alle risorse SCEP (Simple Certificate Enrollment Protocol) tra gruppi, i profili possono entrare in conflitto e generare un errore. Si supponga, ad esempio, che sia già presente un profilo di posta elettronica che punta al server di Exchange locale, destinato al Gruppo A. Si supponga quindi di creare un nuovo profilo di posta elettronica che punta a Exchange Online, destinato al Gruppo B. Se si spostano utenti dal Gruppo A al Gruppo B, i dispositivi manterranno il profilo di posta elettronica del server di Exchange locale e cercheranno di installare il profilo di posta elettronica di Exchange Online destinato al Gruppo B.

A questo punto, si verifica una delle condizioni seguenti: 
* Se i profili di posta elettronica A e B sono identici, il dispositivo rifiuta il profilo B perché tale profilo contiene già il profilo di posta elettronica A.
* Se il profilo di posta elettronica A è diverso dal profilo di posta elettronica B, come indicato nell'esempio, il dispositivo finisce per avere due profili di posta elettronica.

> [!NOTE]
> Per distinguere un profilo di posta elettronica dall'altro, vengono verificati il nome host e l'attributo usati per il nome utente.

In entrambi i casi, il profilo di accesso alla risorsa (profilo di posta elettronica) non è stato rimosso dal dispositivo per evitare la rimozione accidentale dell'accesso di un utente alla posta elettronica o del certificato SCEP del client.

**Soluzione alternativa**: nessuna.

## <a name="when-you-enroll-a-windows-81-device-that-must-authenticate-to-a-proxy-server-the-enrollment-process-fails-with-no-visible-cause"></a>Quando si registra un dispositivo Windows 8.1 che deve autenticarsi presso un server proxy, il processo di registrazione ha esito negativo, senza alcuna causa evidente
**Problema:** quando si registra un dispositivo Windows 8.1 e il dispositivo deve autenticarsi a un server proxy durante la procedura di registrazione, se il dispositivo non ha memorizzato nella cache le credenziali del server proxy, la registrazione ha esito negativo. Quando le credenziali del server proxy non sono memorizzate nella cache del dispositivo, il processo di registrazione deve attendere che l'utente immetta tali credenziali. Ma la richiesta di specificare le credenziali del server di proxy non viene visualizzata durante il processo di registrazione. Il risultato è che il processo di registrazione non riesce a effettuare l'autenticazione al server proxy. Per l'utente non viene visualizzata alcuna indicazione visibile di questo errore.

**Soluzione alternativa:** per i dispositivi Windows 8.1 che devono registrarsi a una rete che richiede l'uso di un server proxy autenticato, configurare e salvare le credenziali per il server proxy prima della registrazione del dispositivo. Per configurare e salvare le credenziali in un dispositivo Windows 8.1:

1.  Nel dispositivo Windows 8.1 aprire Internet Explorer.
2.  Quando vengono richieste le credenziali del server proxy, inserirle e quindi scegliere l'opzione **Memorizza credenziali**.
3.  Registrare il dispositivo.

## <a name="windows-phone-81-devices-fail-to-enroll-with-microsoft-intune-when-device-authentication-is-enabled-in-ad-fs"></a>La registrazione dei dispositivi Windows Phone 8.1 in Microsoft Intune non riesce se l'autenticazione dei dispositivi è abilitata in AD FS
**Problema:** quando si registra un dispositivo Windows Phone 8.1, la registrazione ha esito negativo se è abilitata l'impostazione facoltativa per l'autenticazione del dispositivo all'interno dei criteri di autenticazione globali in Active Directory Federation Services (AD FS).

**Soluzione alternativa:** disabilitare l'autenticazione del dispositivo nel server AD FS deselezionando **Abilita autenticazione dispositivo** in **Modifica criteri di autenticazione globali**. Per altre informazioni, vedere [Configurazione dei criteri di autenticazione](http://technet.microsoft.com/library/dn486781.aspx).


## <a name="microsoft-intune-app-wrapping-tool-for-android-has-no-built-in-uninstall-capability"></a>Microsoft Intune App esegue il Wrapping dello strumento per Android non dispone della capacità di disinstallazione incorporata
**Problema:** lo **strumento Microsoft per la disposizione testo per app per Android** non dispone di una funzionalità integrata per la disinstallazione dello strumento.

**Soluzione alternativa:** passare al percorso in cui è installato lo strumento ed eliminare la directory. La posizione di installazione predefinita è **C:\Programmi (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Per altre informazioni sullo strumento per la disposizione testo per app, vedere [Preparare le app per Android per la gestione con lo strumento per la disposizione testo per app](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## <a name="remote-assistance-is-not-available-on-computers-that-run-windows-8-or-windows-81"></a>L'assistenza remota non è disponibile nei computer che eseguono Windows 8 o Windows 8.1
**Problema:** in questa versione, la funzionalità Assistenza remota non è disponibile nei computer che eseguono Windows 8 o Windows 8.1.

**Soluzione alternativa**: nessuna.

## <a name="alert-notifications-for-recipients-that-are-automatically-added-might-not-work"></a>Le notifiche di avviso per i destinatari aggiunti automaticamente potrebbero non funzionare
**Problema:** i destinatari aggiunti automaticamente a una notifica di avviso potrebbero non ricevere le notifiche regolarmente.

**Soluzione alternativa:** per assicurarsi che i destinatari ricevano le notifiche dei messaggi, è necessario aggiungerli manualmente alle notifiche di avviso.

## <a name="language-support-in-the-azure-portal"></a>Supporto per le lingue nel portale di Azure
Il portale di Azure supporta le lingue seguenti: cinese (semplificato), cinese (tradizionale), ceco, olandese, inglese, tedesco, ungherese, italiano, giapponese, portoghese (Brasile), portoghese (Portogallo), russo, spagnolo, francese, coreano, polacco, svedese e turco.

La console di amministrazione di Intune e le app mobili per l'utente supportano le lingue seguenti: danese, greco, finlandese, norvegese e romeno, oltre a tutte le lingue supportate dal portale di Azure.

