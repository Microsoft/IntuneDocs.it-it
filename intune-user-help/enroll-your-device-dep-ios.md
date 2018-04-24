---
title: Registrare il dispositivo iOS con Device Enrollment Program | Microsoft Docs
description: Descrive come registrare un dispositivo iOS in Intune con DEP
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 9d1154d942069ad69294d4235c894f88513dd848
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-your-ios-device-in-intune-with-the-device-enrollment-program"></a>Registrare il dispositivo iOS in Intune con Device Enrollment Program

Device Enrollment Program viene offerto da Apple per consentire alle aziende di gestire in modo semplice un numero elevato di dispositivi iOS. Se la società ha consentito agli utenti di usare i dispositivi personali, eseguire la [normale procedura di registrazione iOS](enroll-your-device-in-intune-ios.md) anziché quella indicata in questa pagina. Se invece la società ha fornito agli utenti dispositivi iOS specificando che fanno parte di Device Enrollment Program, continuare a leggere.

1. Accendere il dispositivo iOS. 
2. Dopo avere selezionato la **lingua**, connettere il dispositivo al Wi-Fi.
3. Nella schermata **Set up iOS device** (Configura dispositivo iOS) scegliere: 
 
   - **Set up as new device** (Configura come nuovo dispositivo)
   - **Restore from iCloud Backup** (Ripristina da backup iCloud)
   - **Restore from iTunes Backup** (Ripristina da backup iTunes)

4. Dopo la connessione al Wi-Fi, verrà visualizzata la schermata **Configuration** (Configurazione) contenente il messaggio **[Your Company] will automatically configure your device** ([Società] configurerà automaticamente il dispositivo).

   **Configuration allows [Your Company] to manage this device over the air (La configurazione consente a [società] di gestire il dispositivo in modalità wireless). An administrator can help you set up email and network accounts, install and configure apps, and manage settings remotely (Un amministratore può consentire di configurare gli account di posta elettronica e di rete, installare e configurare le app e gestire le impostazioni in modalità remota). An administrator may disable features, install and remove apps, monitor and restrict your Internet traffic and remotely erase this device** (Un amministratore può disattivare le funzionalità, installare e rimuovere app, monitorare e limitare il traffico Internet e cancellare in remoto il dispositivo).
 
   **Configuration is provided by: [Your Company's] iOS Team [Address]** (La configurazione è specificata da: team iOS [società]).

5. Eseguire l'accesso con l'ID Apple. L'accesso consente di installare l'app Portale aziendale e il profilo di gestione che consentono all'azienda di concedere l'accesso alle risorse, come la posta elettronica e le app. 
6. Accettare **termini e condizioni** e decidere se inviare le informazioni di diagnostica a Apple.
7. Dopo avere completato la registrazione, il dispositivo potrebbe chiedere di eseguire altre azioni, Alcune di queste operazioni potrebbero essere l'immissione della password per l'accesso alla posta elettronica e l'impostazione di un passcode.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
