---
title: Unenroll your device from Intune if you declined "Terms of Use" | Microsoft Docs
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
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1d91847166f0e2da22a322ac1a1483266b46d8ed
ms.openlocfilehash: e8dbf10fcc649bd71ac33bd07d1d79f825a91f73


---


# <a name="unenroll-your-device-from-intune-if-you-declined-terms-of-use"></a>Annullare la registrazione del dispositivo da Intune se sono state rifiutate le "Condizioni per l'utilizzo"

Il modo migliore per annullare la registrazione del dispositivo Android è accettare le Condizioni per l'utilizzo, accedere all'app Portale aziendale e quindi usare [queste istruzioni](unenroll-your-device-from-intune-android.md) per annullare la registrazione. Tuttavia, se le Condizioni per l'utilizzo sono state rifiutate durante il tentativo di accesso all'app Portale aziendale, non saranno consentiti altri tentativi di accesso all'app Portale aziendale e, pertanto, sarà necessario usare queste istruzioni "alternative" per annullare la registrazione del dispositivo.

Quando si disinstalla l'app Portale aziendale, viene anche annullata la registrazione del dispositivo da Intune. Il dispositivo non sarà più in grado di accedere alle risorse aziendali. Per altre informazioni su cosa accade quando viene annullata la registrazione, vedere [Cosa succede se si annulla la registrazione del dispositivo da Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md)

Prima di disinstallare l'app Portale aziendale, è necessario passare all'impostazione **Device Administrators** e disattivare **Portale aziendale**. La procedura può variare leggermente a seconda del dispositivo Android in uso.

Per annullare la registrazione del dispositivo da Intune e disinstallare l'app Portale aziendale:

1.  Passare a **Impostazioni** &gt; **Sicurezza &amp; Blocco schermo** &gt; **Amministratori dispositivo**.

    Al termine di questo passaggio la registrazione del dispositivo verrà immediatamente annullata.

2.  Deselezionare la casella accanto a **Portale aziendale** o disattivare il portale.

    Ora è possibile disinstallare l'app Portale aziendale.

Serve ancora assistenza? Contattare l'amministratore IT (accedere al [sito Web del portale aziendale](http://portal.manage.microsoft.com) per informazioni sui contatti) oppure scrivere al [team Microsoft Android](mailto:wintunedroidfbk@microsoft.com).



<!--HONumber=Dec16_HO3-->


