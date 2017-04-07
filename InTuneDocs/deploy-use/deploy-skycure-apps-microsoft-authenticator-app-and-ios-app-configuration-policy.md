---
title: Distribuire app Skycure, l&quot;app Microsoft Authenticator e i criteri di configurazione delle app iOS | Microsoft Docs
description: Distribuire app Skycure, l&quot;app Microsoft Authenticator e i criteri di configurazione iOS nella console classica di Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 86fd9d7212277f9524eb4d7f225df2c7beda1313
ms.openlocfilehash: 9f09a070ec120064bdd64bfb05a39ec9e484606c
ms.lasthandoff: 03/21/2017


---

# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Distribuire app Skycure, l'app Microsoft Authenticator e i criteri di configurazione delle app iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>Prima di iniziare

-   I passaggi seguenti devono essere completati nella [console classica di Intune](https://manage.microsoft.com/).

-   Usare lo stesso account di Azure AD configurato in precedenza nella console di gestione di Skycure, che dovrebbe corrispondere all'account usato per accedere alla console classica di Intune.

-   Assicurarsi di avere familiarità con le procedure seguenti:

    -   [Distribuzione di un'app con Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

    -   [Distribuzione dei criteri di configurazione delle app iOS](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>Per distribuire app Skycure, l'app Microsoft Authenticator e i criteri di configurazione delle app iOS

1.  Nella console classica di Intune scegliere **App** &gt; **App** per visualizzare l'elenco di app che è possibile gestire.

2.  Selezionare le app seguenti:

    a.  Microsoft Authenticator

    b.  App Skycure per Android

    c.  App Skycure per iOS

       ![Console classica di Intune - Tutte le app da distribuire](../media/mtp/skycure-deploy-app-1.png)

3.  Scegliere **Gestisci distribuzione**, selezionare il gruppo di sicurezza di Azure AD con gli utenti Skycure e quindi fare clic su **Avanti**.

4.  Nella pagina **Azione di distribuzione** selezionare l'opzione **Installazione richiesta** dall'elenco a discesa **Approvazione** e quindi fare clic su **Avanti**.

    ![Console classica di Intune - Azione di distribuzione](../media/mtp/skycure-deploy-app-2.png)

5.  Nella pagina **Profilo VPN** selezionare l'opzione **Nessuno** dall'elenco a discesa **Criteri VPN** e quindi fare clic su **Avanti**.

6.  Nella pagina **Configurazione delle app per dispositivi mobili** selezionare i criteri di configurazione delle app iOS creati in precedenza dall'elenco a discesa **Criteri di configurazione dell'app** e quindi fare clic su **Fine**.

    ![Console classica di Intune - Configurazione delle app per dispositivi mobili](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>Passaggi successivi

[Configurare l'integrazione di Skycure con Intune](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune)

