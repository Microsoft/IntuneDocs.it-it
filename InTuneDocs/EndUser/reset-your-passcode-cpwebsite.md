---
title: Come reimpostare il passcode del dispositivo dal sito Web del portale aziendale | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: beba9603ffb43d025132d2d86f0996ff505a9019
ms.openlocfilehash: f9d66fe07173245ff831f204dd120598ad7564db


---

# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Come reimpostare il passcode del dispositivo dal sito Web del portale aziendale

Se il PIN o la password di un dispositivo registrati in Intune viene smarrita, è possibile usare il [sito Web del portale aziendale](http://portal.manage.microsoft.com) per reimpostarla. È possibile usare il sito Web del portale aziendale per gestire computer e dispositivi registrati in Intune e per svolgere la maggior parte delle attività eseguibili tramite l'app Portale aziendale.

> [!NOTE]
> È possibile che non venga visualizzato il pulsante **Reimposta passcode** sul sito Web del portale aziendale. In questo caso, contattare l'amministratore IT per supporto tramite il sito Web del portale aziendale.

Per reimpostare il passcode:

1.  Aprire il [sito Web del portale aziendale](http://portal.manage.microsoft.com) e scegliere il dispositivo di cui si vuole reimpostare il passcode.

2.  Scegliere **Reimposta passcode**.

    ![Dettagli del dispositivo con il pulsante Reimposta passcode](./media/iwp-screen-with-all-options.png)

3.  Scegliere **Disconnetti** e quindi accedere di nuovo con le credenziali aziendali o dell'istituto di istruzione. È necessario eseguire l'accesso entro cinque minuti.

    ![Messaggio di reimpostazione con il pulsante di disconnessione](./media/iwp-2-sign-out.png)

4.  Scegliere **Reimposta passcode**.

    ![Messaggio che spiega cosa avviene quando si reimposta il passcode](./media/iwp-3-tap-reset-passcode-after-signin.png)

    Controllare la tabella per verificare il funzionamento di **Reimposta passcode** con il dispositivo in uso.

    |Tipo di dispositivo|Cosa accade con la reimpostazione|
    |------------|-----------|
    |Android|Viene rimosso il passcode esistente e viene creato un passcode temporaneo con lettere e numeri|
    |iOS|Viene rimosso il passcode esistente senza crearne uno temporaneo. Se si usa il sensore di impronte digitali Touch ID per aprire il dispositivo o effettuare acquisti, sarà necessario reimpostarlo.|
    |Windows 10 Mobile|Viene rimosso il passcode esistente e viene creato un passcode temporaneo con lettere e numeri. Se si usa il riconoscimento facciale di Windows Hello per eseguire l'accesso, la funzione continuerà a essere supportata.|
    |Windows Phone 8.1|Viene rimosso il passcode esistente e viene creato un passcode temporaneo con numeri.|

    5.  Sbloccare il dispositivo e impostare un nuovo passcode o modificare il passcode temporaneo in **Impostazioni** sul dispositivo.

    Per visualizzare una notifica di conferma della reimpostazione della password, fare clic sul flag di notifica nella parte superiore destra del sito Web del portale aziendale.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).



<!--HONumber=Jan17_HO1-->


