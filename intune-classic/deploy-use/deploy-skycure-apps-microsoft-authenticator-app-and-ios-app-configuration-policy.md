---
title: Distribuire app Skycure, l'app Microsoft Authenticator e i criteri di configurazione delle app iOS
description: Distribuire app Skycure, l'app Microsoft Authenticator e i criteri di configurazione iOS nel portale classico di Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d28cf8f4dca89b99deb32ce054db6b04e02edae6
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Distribuire app Skycure, l'app Microsoft Authenticator e i criteri di configurazione delle app iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>Prima di iniziare

-   I passaggi seguenti devono essere completati nel [portale classico di Intune](https://manage.microsoft.com/).

-   Usare lo stesso account di Azure AD configurato in precedenza nella console di gestione di Skycure che dovrebbe corrispondere all'account usato per accedere al portale classico di Intune.

-   Assicurarsi di avere familiarità con le procedure seguenti:

    -   [Distribuzione di un'app con Intune](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune).

    -   [Distribuzione dei criteri di configurazione delle app iOS](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>Per distribuire app Skycure, l'app Microsoft Authenticator e i criteri di configurazione delle app iOS

1.  Nel portale classico di Intune scegliere **App** &gt; **App** per visualizzare l'elenco di app che è possibile gestire.

2.  Selezionare le app seguenti:

    a.  Microsoft Authenticator

    b.  App Skycure per Android

    c.  App Skycure per iOS

       ![Portale classico di Intune - Tutte le app da distribuire](../media/mtp/skycure-deploy-app-1.png)

3.  Scegliere **Gestisci distribuzione**, selezionare il gruppo di sicurezza di Azure AD con gli utenti Skycure e quindi fare clic su **Avanti**.

4.  Nella pagina **Azione di distribuzione** selezionare l'opzione **Installazione richiesta** dall'elenco a discesa **Approvazione** e quindi fare clic su **Avanti**.

    ![Portale classico di Intune - Azione di distribuzione](../media/mtp/skycure-deploy-app-2.png)

5.  Nella pagina **Profilo VPN** selezionare l'opzione **Nessuno** dall'elenco a discesa **Criteri VPN** e quindi fare clic su **Avanti**.

6.  Nella pagina **Configurazione delle app per dispositivi mobili** selezionare i criteri di configurazione delle app iOS creati in precedenza dall'elenco a discesa **Criteri di configurazione dell'app** e quindi fare clic su **Fine**.

    ![Portale classico di Intune - Configurazione delle app per dispositivi mobili](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>Passaggi successivi

[Configurare l'integrazione di Skycure con Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)
