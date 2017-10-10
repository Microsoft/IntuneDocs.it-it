---
title: Registrare il dispositivo iOS nella gestione delle spese per telecomunicazioni con Intune
description: Informazioni su come registrare un dispositivo iOS nella gestione delle spese per telecomunicazioni.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope: User help
ROBOTS: 
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 525e2024246946c9fd9fadefbe42d10dee5c2932
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2017
---
# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>Registrare il dispositivo iOS nella gestione delle spese per telecomunicazioni

È possibile che la propria organizzazione usi software per la gestione delle spese per telecomunicazioni al fine di verificare che i piani dati e voce vengano usati entro limiti accettabili. Al termine della registrazione del dispositivo verrà quindi chiesto di selezionare la categoria migliore per il dispositivo.

  ![Screenshot della schermata per la selezione della categoria migliore per un dispositivo iOS. Mostra una selezione di opzioni per la registrazione personale o aziendale.](./media/ios-enroll-10-tem-select-best-category.png)

Selezionare l'opzione appropriata. Si riceverà una notifica per l'installazione dell'app [__Datalert__](https://itunes.apple.com/app/datalert/id771029268?mt=8) dall'App Store. Datalert è l'app con cui l'organizzazione può misurare l'utilizzo dei dati. Se l'organizzazione ha configurato l'opzione Microsoft di registrazione o dell'istituto di istruzione, verrà chiesto di accedere con l'account aziendale o dell'istituto di istruzione. Se questa configurazione non è stata abilitata, è necessario specificare altre informazioni, ad esempio il numero di telefono, e verificare il dispositivo usando un codice per registrarlo nel servizio Datalert a partire dall'app.

  ![Screenshot della schermata iniziale dell'app Datalert, in cui viene chiesto di passare alla schermata successiva ed è riportata una breve spiegazione di come Datalert può aiutare a sfruttare al meglio il piano dati.](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Registrarsi in Datalert usando l'account aziendale o dell'istituto di istruzione

> [!NOTE]
> Per registrarsi in questo modo, è necessario avere installato l'app [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) e averla attivata nel telefono.

1. Selezionare __Enroll with Microsoft account__ (Registrarsi con un account Microsoft).

  ![Immagine della schermata Impostazioni dell'app Datalert, che offre un campo di numero di telefono per registrare un dispositivo nella metà superiore dello schermo e l'opzione "Registrarsi con un account Microsoft" nella parte inferiore, se si ha un account di Microsoft Office 365 e una sottoscrizione a Intune.](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. Si riceverà una notifica che __"Datalert" vuole aprire "Authenticator"__. Selezionare __Open__ (Apri).

  ![Immagine della finestra popup che richiede all'utente di aprire l'app Authenticator nella richiesta dell'app Datalert.](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. Accedere con l'account __Microsoft aziendale o dell'istituto di istruzione__. Il programma di installazione di Datalert verrà eseguito per alcuni istanti, quindi l'operazione dovrebbe essere completata. Toccare __Finish__ (Fine) quando l'operazione è completata.

## <a name="enroll-into-datalert-using-your-phone-number"></a>Registrarsi in Datalert tramite il numero di telefono

1. Specificare il numero di telefono del dispositivo.

  ![Screenshot dell'app Datalert in cui viene chiesto di specificare un numero di telefono.](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. Si riceverà quindi un codice di verifica tramite un messaggio SMS. Specificare il codice e toccare __OK__.

  ![Screenshot dell'app Datalert in cui viene chiesto di immettere il codice di verifica SMS.](./media/ios-enroll-13-tem-datalert-sms.png)

3. Dopo che si è specificato il codice di verifica, l'installazione di Datalert sarà completata. Toccare __Fine__. A questo punto sarà possibile monitorare i dati dall'app Datalert.

  ![Screenshot dell'app Datalert per il monitoraggio dell'utilizzo dei dati di oggi.](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

Al termine della registrazione, sarà possibile iniziare a esaminare l'utilizzo dei dati nell'app Datalert.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com).
