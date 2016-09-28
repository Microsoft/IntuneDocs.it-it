---
title: Reimpostare il passcode del dispositivo dal sito Web del portale aziendale | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bff97f79c6e88bbf55c2c3a259891bb6206b690b
ms.openlocfilehash: 57e3175af6364e7dacbf8941f10292fc9dc58b15


---


# Reimpostare il passcode del dispositivo dal sito Web del portale aziendale

Se il PIN o la password di un dispositivo registrati in Intune viene smarrita, è possibile usare il [sito Web del portale aziendale](http://portal.manage.microsoft.com) per reimpostarla. Il sito Web del portale aziendale è una pagina Web che è possibile usare per gestire computer e dispositivi registrati in Intune e per svolgere la maggior parte delle attività eseguibili tramite l'app Portale aziendale.

> [!NOTE]
> È possibile che il pulsante Reimposta passcode non venga visualizzato nel sito Web del portale aziendale. Ciò dipende da come l'amministratore IT ha configurato Intune. La reimpostazione del passcode non è supportato nei dispositivi Windows 8.1 e Windows RT.

Per reimpostare il passcode:

1.  Aprire il [sito Web del portale aziendale](http://portal.manage.microsoft.com) e toccare il dispositivo di cui si vuole reimpostare il passcode.

2.  Toccare **Reimposta passcode**.

    ![resetp-passcode-option-on-company-portal-website](./media/iwp-screen-with-all-options.png)

3.  Toccare **Disconnetti** e quindi accedere con le credenziali aziendali o dell'istituto di istruzione. È necessario eseguire l'accesso entro cinque minuti.

    ![sign-out-sign-back-in](./media/iwp-2-sign-out.png)

4.  Toccare **Reimposta passcode**.

    ![tap-reset-passcode](./media/iwp-3-tap-reset-passcode-after-signin.png)

    Controllare la tabella per verificare il funzionamento di Reimposta passcode nel dispositivo.

    |Piattaforma|Support|
    |------------|-----------|
    |Android|Crea un nuovo passcode temporaneo, alfanumerico.|
    |iOS|Rimuove il passcode dal dispositivo e non ne crea uno nuovo temporaneo. Se si usa ID tocco, è necessario configurarlo nuovamente sul dispositivo, poiché verrà rimosso quando si reimposta il passcode.|
    |Windows 10 (solo per dispositivi mobili)|Crea un nuovo passcode temporaneo, alfanumerico. Windows Hello è supportato.|
    |Windows Phone 8.1|Crea un nuovo passcode temporaneo, numerico.|
    Dopo aver sbloccato il dispositivo, è possibile impostare un nuovo passcode su **Impostazioni** nel dispositivo.

5.  Per sbloccare il dispositivo e quindi impostare un nuovo passcode o modificare il passcode temporaneo, passare a **Impostazioni** sul dispositivo.

    Per visualizzare una notifica di conferma della reimpostazione della password, fare clic sul flag di notifica nella parte superiore destra del sito Web del portale aziendale.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).





<!--HONumber=Sep16_HO3-->


