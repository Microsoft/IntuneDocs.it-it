---
title: Si verificano errori durante la registrazione del dispositivo iOS in Intune | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 57b6bb6076b24299fb54626aa55850bf8c0c2428
ms.openlocfilehash: df491807386c80dce0f45822fbc64acefda59eb3


---

# <a name="you-see-errors-while-trying-to-enroll-your-ios-device-in-intune"></a>Si verificano errori durante la registrazione del dispositivo iOS in Intune

La tabella seguente elenca gli errori che potrebbero verificarsi durante la registrazione del dispositivo iOS in Intune. Condividere il collegamento con l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

|Messaggio di errore|Problema|Informazioni per l'amministratore IT|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Nessun criterio di registrazione|Verificare che siano stati configurati tutti i prerequisiti di registrazione, ad esempio il certificato APNS (Apple Push Notification Service), e che sia abilitato "iOS come piattaforma". Per le istruzioni, vedere [Configurare la gestione dei dispositivi iOS e Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceCapReached|Sono già stati registrati troppi dispositivi mobili.|L'utente deve rimuovere dal Portale aziendale uno dei dispositivi mobili attualmente registrati prima di poterne registrare un altro. Vedere le istruzioni relative al tipo di dispositivo in uso: [Android](unenroll-your-device-from-intune-android.md), [iOS](unenroll-your-device-from-intune-ios.md) o [Windows](unenroll-your-device-from-intune-windows.md).|
|APNSCertificateNotValid|Si è verificato un problema con il certificato che consente al dispositivo mobile di comunicare con la rete aziendale.<br /><br />Contattare gli amministratori IT segnalando di aver ricevuto il messaggio **APNSCertificateNotValid** durante il tentativo di registrazione del dispositivo mobile. Suggerire agli amministratori di consultare questa tabella per trovare la soluzione.|Apple Push Notification Service (APNS) offre un canale per contattare i dispositivi iOS registrati. Se non sono state eseguite le procedure per ottenere un certificato APNS o se il certificato è scaduto, i tentativi di registrazione avranno esito negativo e verrà visualizzato questo messaggio.<br /><br />Esaminare le informazioni sulla configurazione degli utenti in [Sincronizzare Active Directory e aggiungere utenti a Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) e [Organizzazione di utenti e dispositivi](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|AccountNotOnboarded|Si è verificato un problema con il certificato che consente al dispositivo mobile di comunicare con la rete aziendale.<br /><br />Contattare gli amministratori IT segnalando di aver ricevuto il messaggio **APNSNotOnboarded** durante il tentativo di registrazione del dispositivo mobile. Suggerire agli amministratori di consultare questa tabella per trovare la soluzione.|Apple Push Notification Service (APNS) offre un canale per contattare i dispositivi iOS registrati. Se non sono state eseguite le procedure per ottenere un certificato APNS o se il certificato è scaduto, i tentativi di registrazione avranno esito negativo e verrà visualizzato questo messaggio.<br /><br />Per altre informazioni, vedere [Configurare la gestione dei dispositivi iOS e Mac con Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Il problema potrebbe essere causato dal tentativo di registrare un dispositivo non iOS. Il tipo di dispositivo mobile che si sta provando a registrare non è supportato.<br /><br />Verificare che nel dispositivo sia in esecuzione iOS 8.0 o versione successiva.<br /><br />Contattare gli amministratori IT segnalando di aver ricevuto il messaggio **DeviceTypeNotSupported** durante il tentativo di registrazione del dispositivo mobile. Suggerire agli amministratori di consultare questa tabella per trovare la soluzione.|Verificare che nel dispositivo dell'utente sia in esecuzione iOS 8.0 o versione successiva.|
|UserLicenseTypeInvalid|Non è possibile registrare il dispositivo mobile perché l'account utente non è ancora membro di un gruppo di utenti obbligatorio.<br /><br />Contattare gli amministratori IT segnalando di aver ricevuto il messaggio **UserLicenseTypeInvalid** durante il tentativo di registrazione del dispositivo mobile. Suggerire agli amministratori di consultare questa tabella per trovare la soluzione.|Per poter registrare un dispositivo, gli utenti devono essere membri del gruppo di utenti appropriato. Questo messaggio indica che l'utente ha il tipo di licenza errato per l'autorità di gestione dei dispositivi mobili designata. Questo errore di Intune viene visualizzato, ad esempio, se Intune è stato designato come autorità di gestione dei dispositivi mobili e l'utente usa una licenza per System Center 2012 R2 Configuration Manager.<br /><br />Per altre informazioni, vedere quanto segue:<br /><br />Vedere l'articolo [Configurare la gestione dei dispositivi iOS e Mac con Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) e le informazioni sulla configurazione degli utenti in [Sincronizzare Active Directory e aggiungere utenti a Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) e [Organizzazione di utenti e dispositivi](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|MdmAuthorityNotDefined|L'amministratore IT deve impostare la modalità di gestione dei dispositivi mobili usata in azienda.<br /><br />Contattare gli amministratori IT segnalando di aver ricevuto il messaggio **MdmAuthorityNotDefined** durante il tentativo di registrazione del dispositivo mobile. Suggerire agli amministratori di consultare questa tabella per trovare la soluzione.|L'autorità di gestione dei dispositivi mobili non è stata designata in Intune.<br /><br />Rivedere il primo punto del "Passaggio 6: Registrare dispositivi mobili e installare un'app" in [Iniziare con una versione di valutazione gratuita di 30 giorni di Microsoft Intune](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|



<!--HONumber=Dec16_HO1-->


