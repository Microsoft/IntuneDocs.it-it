---
title: Registrare i dispositivi mobili della valutazione | Microsoft Intune
description: Come registrare dispositivi mobili e installare un'app quando si esegue l'iscrizione per una valutazione gratuita di 30 giorni di Intune
keywords: 
author: Staciebarker
manager: arob98
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: 2424d52f800ae61dbadc0a3ae73c2b3f24d936c3


---

# Registrare i dispositivi mobili della valutazione e installare un'app
Per configurare la gestione dei dispositivi mobili con Intune, è prima necessario impostare l'autorità di gestione dei dispositivi mobili, abilitare la gestione per le piattaforme dei dispositivi e registrare i dispositivi con l'app Portale aziendale. È quindi possibile distribuire l'app Microsoft Skype pubblicata.

## Preparare il servizio per la gestione dei dispositivi

1.  **Rendere Intune l'autorità di gestione dei dispositivi mobili**

    Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Amministrazione**&gt;** Gestione dei dispositivi mobili**. Scegliere **Attività** > **Imposta autorità MDM**, quindi scegliere **Sì** nella finestra di dialogo **Autorità MDM**.

2.  **Abilitare la gestione dei dispositivi mobili per la piattaforma del dispositivo**

    Abilitare la gestione dei dispositivi mobili per la piattaforma del dispositivo da gestire. I requisiti variano a seconda della piattaforma:

    -   **iOS e Mac OS X**: vedere [Configurare la gestione dei dispositivi iOS e Mac](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).

    -   **Android**: i dispositivi mobili Android consentono agli utenti di effettuare la registrazione tramite l'app Portale aziendale disponibile da Google Play. Non sono richieste ulteriori operazioni di configurazione in Intune.

    -   **Windows Phone**: vedere [Configurare la gestione di Windows Phone e Windows 10 Mobile con Microsoft Intune](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune).

## Registrare dispositivi di test

### iOS e Mac OS X
Installare l'app **Portale aziendale di Microsoft Intune** di Microsoft Corporation, disponibile in App Store, quindi accedere con le credenziali utente di Intune aggiunte in precedenza. Visualizzare i **dispositivi registrati** per aggiungere il dispositivo.

### Android
Installare l'app **Portale aziendale di Intune** di Microsoft Corporation, disponibile in [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) e accedere con le credenziali utente di Intune aggiunte in precedenza.

### Windows Phone 8.1
Gli utenti installano l'app **Portale aziendale** di Microsoft Corporation, disponibile in Windows Phone Store e accedono con le credenziali utente di Intune aggiunte in precedenza.  Visualizzare i **dispositivi registrati** per aggiungere il dispositivo.

 ### Windows Phone 8.0
 Gli utenti fanno clic su **Impostazioni di sistema**&gt;**App aziendali** e accedono con le credenziali utente di Intune aggiunte in precedenza. L'app Portale aziendale viene distribuita nel telefono dell’utente.

Se viene richiesto un **indirizzo server**, immettere "manage.microsoft.com".


## Installare l'applicazione distribuita in precedenza
Aprire l'app Portale aziendale nel dispositivo mobile, scegliere **App** e quindi installare **Microsoft Skype**.

Per altre informazioni sulla gestione dei dispositivi mobili con Intune, vedere [Prepararsi alla registrazione dei dispositivi in Microsoft Intune](/Intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune).

### Passaggi successivi
A questo punto, il passaggio 5 della procedura di *valutazione di Microsoft Intune* è stato completato.

>[!div class="step-by-step"]

>[&larr; **Creare criteri**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)     [**Opzioni e funzionalità aggiuntive** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)  



<!--HONumber=Jul16_HO3-->


