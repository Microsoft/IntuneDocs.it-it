---
title: Che cosa avviene se si annulla la registrazione del dispositivo Windows da Intune? | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08f31db90f324ef5f93076c4e13bfa5328a15adc
ms.openlocfilehash: ebd1300c490f3d69110a5f1920fd25d1dc5cb850


---


# Che cosa avviene se si annulla la registrazione del dispositivo Windows da Intune?

Usare i collegamenti sul lato destro della pagina in "Contenuto di questo articolo" per trovare informazioni sul tipo di dispositivo in uso.


## Windows 10, Windows 8.1, Windows 8, Windows 7, Vista

-   Il dispositivo non sarà più visualizzato nel Portale aziendale e non sarà più possibile installare le app dal Portale aziendale.

-   Il software client Intune, se è installato, verrà rimosso dal computer.

-   Il software Intune Endpoint Protection verrà rimosso dal computer. Se nel computer è installato un altro software di protezione da virus che è disabilitato, sarà possibile abilitarlo di nuovo dopo aver rimosso Intune Endpoint Protection. Controllare il computer dopo che è stato rimosso dal Portale aziendale.

    > [!IMPORTANT]
    > Se l'altro software di protezione da virus non viene riabilitato o non sono installati altri software di protezione da virus, il computer potrebbe essere vulnerabile a virus e malware.

-   Non saranno più applicabili le impostazioni che sono state modificate nel dispositivo quando è stato aggiunto, ad esempio la disattivazione della fotocamera.

-   Il computer non riceverà più gli aggiornamenti software automatici o gli aggiornamenti del software antivirus dal servizio Intune. Tuttavia, a seconda della configurazione, il computer potrebbe continuare a ricevere gli aggiornamenti da Windows Server Update Services, Windows Update o Microsoft Update.

Inoltre, per Windows 8.1:

-   Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

-   Alcune applicazioni di posta elettronica, ad esempio Windows Mail, non potranno più accedere alla posta elettronica aziendale archiviata sul dispositivo.

-   Potrebbe non essere possibile connettersi alla rete aziendale usando il Wi-Fi o una rete privata virtuale.

-   Dal dispositivo potrebbe non essere più possibile accedere ad alcune risorse della società, quali condivisioni di file o siti Web interni.

## Windows 10 Mobile e Windows Phone 8.1

-   L'app Portale aziendale viene disinstallata dal dispositivo, il che significa che il dispositivo non sarà più visualizzato nel Portale aziendale e non sarà possibile installare le app dall'app Portale aziendale o dal sito Web del Portale aziendale.

-   Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

-   Non saranno più valide le impostazioni che sono state modificate nel dispositivo quando è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza.

    > [!IMPORTANT]
    > L'unica eccezione sono i criteri di crittografia che saranno ancora validi. Se i criteri aziendali richiedevano la crittografia del dispositivo Windows Phone, l'unico modo per decrittografare il dispositivo è di reimpostare il telefono usando il menu **Impostazioni** del dispositivo Windows Phone.

## Windows RT che esegue Windows 8.1

-   L'app Portale aziendale viene disinstallata dal dispositivo, il che significa che il dispositivo non sarà più visualizzato nel Portale aziendale e non sarà possibile installare le app dal Portale aziendale.

-   Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

-   Non saranno più valide le impostazioni che sono state modificate nel dispositivo quando è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza.

-   Potrebbe non essere più possibile connettersi alla rete aziendale usando il Wi-Fi o una rete privata virtuale.

-   Dal dispositivo potrebbe non essere più possibile accedere ad alcune risorse della società, quali condivisioni di file o siti Web interni.

-   Alcune applicazioni di posta elettronica, ad esempio Windows Mail, non potranno più accedere alla posta elettronica aziendale archiviata sul dispositivo.

Quando si rimuove il dispositivo Windows RT, si verifica quanto segue:

-   L'app Portale aziendale viene disinstallata dal dispositivo, il che significa che il dispositivo non sarà più visualizzato nel Portale aziendale e non sarà possibile installare le app dal Portale aziendale.

-   Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

-   Non saranno più valide le impostazioni che sono state modificate nel dispositivo quando è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza.

Per informazioni, contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).




<!--HONumber=Oct16_HO2-->


