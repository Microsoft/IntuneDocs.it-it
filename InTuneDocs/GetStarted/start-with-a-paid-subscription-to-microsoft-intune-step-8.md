---
title: Registrare dispositivi mobili e installare un'app | Microsoft Intune
description: Illustra come registrare i dispositivi mobili e installare un'app su un dispositivo registrato in Intune
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 8070a02be93673b83b13dc49d0fe545606bc6cee


---

# Registrare dispositivi mobili e installare un'app
Per configurare la gestione dei dispositivi mobili con Intune, è prima necessario impostare l'autorità di gestione dei dispositivi mobili, abilitare la gestione per le piattaforme dei dispositivi e registrare i dispositivi con l'app Portale aziendale. È quindi possibile distribuire l'app Microsoft Skype pubblicata nel passaggio 6.

## Abilitare la gestione dei dispositivi e registrare i dispositivi

1.  **Rendere Intune l'autorità di gestione dei dispositivi mobili** Nella [console di amministrazione di Intune](https://manage.microsoft.com/) fare clic su **Amministrazione** > **Gestione dei dispositivi mobili** e fare clic su **Imposta autorità MDM** in **Attività**.  Scegliere **Sì** nella finestra di dialogo dell'autorità MDM.
    ![Console di amministrazione. Impostare MDM su Intune](./media/mdmAuthority.png)

2.  **Abilitare la gestione dei dispositivi mobili per la piattaforma del dispositivo** Abilitare la gestione dei dispositivi mobili per la piattaforma del dispositivo da gestire. I requisiti variano a seconda della piattaforma:

    -   **iOS e Mac OS X**: vedere [Set up iOS and Mac management with Microsoft Intune](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) (Configurare la gestione dei dispositivi iOS e Mac con Microsoft Intune).

    -   **Windows Phone**: vedere [Set up Windows Phone management with Microsoft Intune](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) (Configurare la gestione dei dispositivi Windows Phone con Microsoft Intune).

    -   **Android**: i dispositivi mobili Android consentono agli utenti di eseguire la registrazione tramite l'app Portale aziendale disponibile da [Google Play](https://play.google.com/store/apps/details?id=com.skype.raider). Non sono richieste ulteriori operazioni di configurazione in Intune.

3.  **Registrare i dispositivi**:

    -   **Android**: installare l'app **Portale aziendale di Intune** di Microsoft Corporation disponibile in [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) e accedere con le credenziali utente di Intune aggiunte in precedenza.

    -   **iOS e Mac OS X**: installare l'app **Portale aziendale di Microsoft Intune** di Microsoft Corporation disponibile nell'App Store e accedere con le credenziali utente di Intune aggiunte in precedenza. Visualizzare i **dispositivi registrati** per aggiungere il dispositivo.

    -   **Windows Phone 8.1**: gli utenti installano l'app **Portale aziendale** di Microsoft Corporation disponibile in Windows Phone Store e accedono con le credenziali utente di Intune aggiunte in precedenza.  Visualizzare i **dispositivi registrati** per aggiungere il dispositivo.

    -   **Windows Phone 8.0**: gli utenti scelgono **Impostazioni di sistema** &gt; **app aziendali** e accedono con le credenziali utente di Intune aggiunte in precedenza. L'app Portale aziendale viene distribuita nel telefono dell’utente.

    Se viene richiesto un **indirizzo server**, immettere "manage.microsoft.com".

## Installare un'app su un dispositivo registrato
Nel [passaggio 6](start-with-a-paid-subscription-to-microsoft-intune-step-6.md) di questa Guida introduttiva è stata pubblicata l'applicazione Skype nel gruppo utenti di Intune personalizzato. Ora la stessa app verrà installata su un dispositivo appena registrato.

Aprire l'app Portale aziendale nel dispositivo mobile registrato, scegliere **App** e quindi installare **Microsoft Skype**.

Per altre informazioni sulla gestione dei dispositivi mobili con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], vedere [Get ready to enroll devices in Microsoft Intune](/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) (Prepararsi alla registrazione dei dispositivi in Microsoft Intune).


### Passaggi successivi
A questo punto, Ultimo passaggio della *Guida introduttiva di Intune* completato Ora che la configurazione iniziale è stata completata, è possibile attivare altre funzionalità di MDM.

>[!div class="step-by-step"]

>[&larr; **Registrare i dispositivi**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Attività successive alla configurazione** &rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Jul16_HO4-->


