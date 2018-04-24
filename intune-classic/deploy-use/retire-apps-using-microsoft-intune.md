---
title: Ritirare le app
description: Informazioni su come ritirare o disinstallare app con Intune.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a3fadf497e5db147d12ecf1e32343e94222c65e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="retire-apps-using-microsoft-intune"></a>Ritirare le app con Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Per ritirare un'app, è sufficiente disinstallarla. Quando si distribuiscono e si gestiscono le app con Intune, il processo di disinstallazione dell'app è uguale sia per dispositivi mobili che per PC Windows. Per il corretto completamento di questa procedura, l'app deve supportare il processo di disinstallazione.

## <a name="uninstall-an-app"></a>Disinstallare un'app

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **App** &gt; **App**.

2.  Selezionare l'app distribuita in precedenza e che ora deve essere disinstallata e quindi scegliere **Gestisci distribuzione**.

3.  Nella pagina **Azione di distribuzione** selezionare **Disinstalla** nella colonna **Approvazione** .

L'app verrà disinstallata la volta successiva che il dispositivo o il computer verificherà la disponibilità di app.

### <a name="see-also"></a>Vedere anche
[Aggiungere app in Microsoft Intune](add-apps.md)
