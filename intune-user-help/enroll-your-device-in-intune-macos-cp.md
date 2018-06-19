---
title: Registrare il dispositivo macOS in Intune con il Portale aziendale | Microsoft Docs
description: Descrive come registrare un dispositivo macOS in Intune con l'app Portale aziendale
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 3dac9446d7a1097f5be4d0851cd78e8cbb86cc4e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831798"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Registrare il dispositivo macOS in Intune con l'app Portale aziendale

La possibilità di accedere alle app, ai dati e alle risorse dell'organizzazione semplifica lo svolgimento del proprio lavoro. L'organizzazione usa Intune per [gestire l'accesso a queste risorse](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md) ed è quindi necessario scaricare l'app Portale aziendale per macOS. Queste istruzioni sono relative a dispositivi macOS in OS X El Capitan 10.11+.


1. Trovare __Safari__ nel __Dock__ e aprire una nuova finestra, quindi aprire il [sito Web del portale aziendale](https://portal.manage.microsoft.com).

2. Accedere al sito Web del portale aziendale con l'account aziendale o dell'istituto di istruzione.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Dopo aver eseguito l'accesso, fare clic su **Menu** in alto a sinistra e selezionare **Dispositivi personali**.

   ![Screenshot della pagina di destinazione per il portale Web con il portale Web che mostra che non è possibile installare alcuna app, con il pulsante Dispositivi personali sotto.](./media/macOS_enroll_001_landing_page.png)

4. Nella pagina __Dispositivi personali__ verrà visualizzato un elenco di dispositivi registrati o semplicemente un banner. Ciò dipende dal fatto di avere già un dispositivo macOS registrato o meno. Per registrare un dispositivo che non è elencato, selezionare il banner che indica __If your device is listed, tap here to identify it. You can also tap here to enroll your device if it is not listed__ (Se il dispositivo è elencato, toccare qui per identificarlo. È anche possibile toccare qui per registrare il dispositivo se non è elencato). Se non si hanno dispositivi registrati, verrà visualizzato il banner **Non è stato registrato alcun dispositivo. Registrare questo dispositivo toccando qui.**

    ![Screenshot della pagina Dispositivi personali con un paio di dispositivi non identificati sopra il banner con la richiesta di registrare i dispositivi non inclusi nell'elenco o di identificare quelli non identificati.](./media/macOS_enroll_002_tap_here_banner.png)

5. Scaricare l'app Portale aziendale nel dispositivo macOS per continuare con la registrazione.

    ![Avviso che richiede all'utente di scaricare l'app Portale aziendale per macOS. In questo avviso il testo elencato nel passaggio precedente appare sopra un pulsante "Scarica" nell'angolo inferiore destro.](./media/macOS_enroll_IWP_CP_app_notice.png)

6. Il computer Mac verifica che sia possibile aprire in modo sicuro il file **CompanyPortal.pkg** scaricato. Aprire il programma di installazione e seguire la procedura di installazione.

7. Al termine della procedura di installazione aprire la cartella **Applicazioni** o il **Launchpad**, quindi aprire il **Portale aziendale**.

8. Il computer Mac mostrerà un messaggio che indica che **"CompanyPortal" è un'applicazione scaricata da Internet. Aprirla?** Fare clic su **Apri**.

   > [!NOTE]
   > Intune deve accedere al computer per assicurarsi che il dispositivo sia sufficientemente sicuro per accedere alle risorse dell'organizzazione. Se il computer rifiuta di aprire l'app Portale aziendale, provare a [disattivare Gatekeeper](https://support.apple.com/HT202491) e quindi ad aprire l'app.

9. La prima schermata visualizzata nell'app Portale aziendale richiede di **accedere** con lo stesso account aziendale o dell'istituto di istruzione usato per accedere al sito Web del Portale aziendale.

10. Il Portale aziendale conferma le informazioni sull'account, quindi mostra gli stati relativi a **Registrazione del dispositivo** e **Conformità del dispositivo**. Verranno visualizzati triangoli gialli che segnalano le azioni da eseguire per assicurare che il computer Mac possa essere usato al lavoro in tutta sicurezza. Fare clic su **Inizia** per avviare la [registrazione del dispositivo nella gestione](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).

11. Verrà avviata la registrazione del computer Mac nella gestione. È possibile che venga richiesto di specificare le informazioni di accesso del computer in questa fase. La registrazione può richiedere qualche minuto. Durante l'attesa è possibile eseguire altre operazioni nel computer. Al termine della configurazione dell'accesso aziendale viene visualizzato un messaggio relativo al completamento dell'operazione.

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
