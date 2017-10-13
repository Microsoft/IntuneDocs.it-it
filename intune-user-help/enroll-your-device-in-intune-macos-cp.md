---
title: Registrare il dispositivo macOS in Intune con il Portale aziendale | Microsoft Docs
description: Descrive come registrare un dispositivo macOS in Intune con l'app Portale aziendale
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope: User help
ROBOTS: 
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: b40801633a130ac79b0ae5b4e1669320c70909e2
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2017
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Registrare il dispositivo macOS in Intune con l'app Portale aziendale

[!INCLUDE[macos-preview-1708](./includes/macos-preview-1708.md)]

La possibilità di accedere alle app, ai dati e alle risorse dell'organizzazione semplifica lo svolgimento del proprio lavoro. L'organizzazione usa Intune per [gestire l'accesso a queste risorse](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md) ed è quindi necessario scaricare l'app Portale aziendale per macOS. Queste istruzioni sono relative a dispositivi macOS in OS X El Capitan 10.11+.

  > [!NOTE]
  > Se si vuole registrare un dispositivo iOS, ad esempio un iPhone o iPad, [usare invece queste istruzioni](enroll-your-device-in-intune-ios.md).

1.  Nel __Dock__ trovare __Safari__ e andare a [aka.ms/macoscompanyportal](https://aka.ms/macoscompanyportal). 

2. Scaricare l'app. Il computer Mac verificherà che sia possibile aprire in modo sicuro il file **CompanyPortal.dmg** scaricato. Dopo l'apertura dalla cartella **Download**, trascinare l'app **CompanyPortal** nella cartella **Applicazioni**.

3. Aprire la cartella **Applicazioni** o il **Launchpad**, quindi aprire il **Portale aziendale**.

4. Il computer Mac mostrerà un messaggio che indica che **"CompanyPortal" è un'applicazione scaricata da Internet. Aprirla?** Fare clic su **Apri**.

  > [!NOTE]
  > Intune deve accedere al computer per assicurarsi che il dispositivo sia sufficientemente sicuro per accedere alle risorse dell'organizzazione. Se il computer rifiuta di aprire l'app Portale aziendale, provare a [disattivare Gatekeeper](https://support.apple.com/HT202491) e quindi ad aprire l'app.

6. La prima schermata visualizzata nell'app Portale aziendale richiede di **accedere** con lo stesso account aziendale o dell'istituto di istruzione usato per accedere al sito Web del Portale aziendale.

7. Il Portale aziendale conferma le informazioni sull'account, quindi mostra gli stati relativi a **Registrazione del dispositivo** e **Conformità del dispositivo**. Verranno visualizzati triangoli gialli che segnalano le azioni da eseguire per assicurare che il computer Mac possa essere usato al lavoro in tutta sicurezza. Fare clic su **Inizia** per avviare la [registrazione del dispositivo nella gestione](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).

8. Verrà avviata la registrazione del computer Mac nella gestione. È possibile che venga richiesto di specificare le informazioni di accesso del computer in questa fase. La registrazione può richiedere qualche minuto. Durante l'attesa è possibile eseguire altre operazioni nel computer. Al termine della configurazione dell'accesso aziendale viene visualizzato un messaggio relativo al completamento dell'operazione.

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://portal.manage.microsoft.com).
