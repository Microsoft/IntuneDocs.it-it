---
title: Che cosa avviene quando si installa l&quot;app Portale aziendale e si registra il dispositivo Windows in Intune? | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9ddbcde20fac83289c4622f69538ff00fa0cb65b
ms.openlocfilehash: 2d56c2f23fd70ab0ca593d1ad5d60889e5855a7a


---


# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo Windows in Intune?

Quando si installa l'app Portale aziendale e la si usa per registrare un dispositivo Windows o Windows Phone, si consente all'amministratore IT di gestire il dispositivo per garantire la sicurezza dei dati dell'azienda o dell'istituto di istruzione. Questo argomento descrive cosa avviene per i dispositivi precedenti a Windows 10. Per i dispositivi Windows 10, vedere l'[argomento correlato](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md).

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>Che cosa avviene a tutti i dispositivi Windows dopo l'iscrizione?
Mediante la registrazione del dispositivo Windows o Windows Phone in Intune è possibile:

-   Accedere alla rete aziendale e ai file della posta elettronica e di lavoro.

-   Ottenere app aziendali dal sito Web del portale aziendale. Per Windows 7 e Windows Vista è possibile ottenere app aziendali solo dal sito Web del portale aziendale.

-   Configurare automaticamente l'account di posta elettronica aziendale o dell'istituto di istruzione.

-   Ripristinare le impostazioni di fabbrica del telefono se questo viene smarrito o rubato.

Quando si registra un dispositivo, vengono concesse all'amministratore IT le autorizzazioni per eseguire le operazioni seguenti:

-   Ripristinare le impostazioni predefinite del dispositivo impostate dal produttore. Questa operazione è utile se il dispositivo viene smarrito o rubato.

-   Rimuovere solo le app aziendali e i file correlati alla società. *Impostazioni e dati personali non vengono rimossi.*

-   L'amministratore IT può vedere il software installato nel dispositivo, incluso il software installato personalmente dall'utente.

-   Impostare requisiti per il dispositivo, ad esempio richiedere una password del dispositivo o un PIN per consentire la protezione dei dati aziendali. L'amministratore IT può anche limitare il numero di immissioni di una password errata e impedire l'accesso al dispositivo se tale numero viene superato.

-   Richiedere all'utente di crittografare i dati del dispositivo per proteggere i dati aziendali in caso di furto o smarrimento del dispositivo.

-   Richiedere di accettare i termini e le condizioni.

-   Impedire lo scatto di foto di dati correlati alla società.

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>Che cosa accade a tutti i PC Windows dopo l'iscrizione?

-  Verrà installato software nel computer per consentire all'amministratore IT di gestire il computer e all'utente di accedere alle risorse aziendali, come app e informazioni sul supporto. L'amministratore IT può aggiornare automaticamente il software.

-  Intune Endpoint Protection può essere installato nel computer. Questo software controlla l'eventuale presenza di virus e malware.

-  L'amministratore IT può raccogliere o eliminare dati dal disco rigido del computer.

-  L'amministratore IT può installare app e aggiornamenti nel computer.

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>Che cosa accade ogni otto ore dopo la registrazione del dispositivo?
Ogni otto ore circa i dispositivi registrati eseguono le operazioni seguenti:

-   Download degli aggiornamenti di criteri o app resi disponibili dall'amministratore IT.

-   Invio degli aggiornamenti dell'inventario hardware.

-   Invio degli aggiornamenti dell'inventario delle app aziendali.

Per eventuali domande, contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).



<!--HONumber=Nov16_HO1-->


