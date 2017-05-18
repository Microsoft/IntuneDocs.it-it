---
title: Ritirare le app | Documentazione Microsoft
description: Informazioni su come ritirare o disinstallare app con Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: d0c24549c4805da87c74247253905a96d6290969


---

# <a name="retire-apps-using-microsoft-intune"></a>Ritirare le app con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per ritirare un'app, è sufficiente disinstallarla. Quando si distribuiscono e si gestiscono le app con Intune, il processo di disinstallazione dell'app è uguale sia per dispositivi mobili che per PC Windows. Per il corretto completamento di questa procedura, l'app deve supportare il processo di disinstallazione.

## <a name="uninstall-an-app"></a>Disinstallare un'app

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **App**&gt;**App**.

2.  Selezionare l'app distribuita in precedenza e che ora deve essere disinstallata e quindi scegliere **Gestisci distribuzione**.

3.  Nella pagina **Azione di distribuzione** selezionare **Disinstalla** nella colonna **Approvazione** .

L'app verrà disinstallata la volta successiva che il dispositivo o il computer verificherà la disponibilità di app.

### <a name="see-also"></a>Vedere anche
[Aggiungere app in Microsoft Intune](add-apps.md)



<!--HONumber=Dec16_HO5-->


