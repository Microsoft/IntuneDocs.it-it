---
title: Aggiungere app Skycure, Microsoft Authenticator e i criteri di configurazione delle app iOS
description: Aggiungere app Skycure, Microsoft Authenticator e i criteri di configurazione delle app iOS nel portale classico di Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018d26f4-4a75-4e27-bb04-54f54106cb2f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3538b3b326ee45dfcc0912c89d1766e04d88051e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="add-skycure-apps-microsoft-authenticator-app-and-ios-configuration-policy"></a>Aggiungere app Skycure, Microsoft Authenticator e i criteri di configurazione delle app iOS

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

È necessario usare Intune per aggiungere e distribuire le app Skycure, consentendo così agli utenti finali di ricevere notifiche quando viene identificata una minaccia nei dispositivi mobili, e per ricevere indicazioni per risolvere le minacce.

È inoltre necessario usare l'app [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to), per la verifica delle identità degli utenti tramite Azure AD, e i criteri di configurazione delle app iOS, che segnalano all'app iOS Skycure di usare Intune e Single Sign-On (SSO) di Azure AD, per evitare agli utenti di digitare nome utente e password ogni volta che accedono all'app Skycure.

## <a name="before-you-begin"></a>Prima di iniziare

-   I passaggi seguenti devono essere completati nel [portale classico di Intune](https://manage.microsoft.com/).

-   Usare lo stesso account di Azure AD configurato in precedenza nella console di gestione di Skycure che dovrebbe corrispondere all'account usato per accedere al portale classico di Intune.

-   È necessario avere pronto il file di integrazione di Skycure, ovvero il file con estensione zip scaricato in precedenza dalla console di gestione di Skycure, che contiene il file **skycure\_configuration.plist** con i parametri dei criteri di configurazione delle app iOS.

-   Assicurarsi di avere familiarità con le procedure seguenti:

    -   [Aggiunta di un'app in Intune](/intune-classic/deploy-use/add-apps).

    -   [Aggiunta dei criteri di configurazione delle app iOS in Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-add-the-skycure-app-for-android"></a>Per aggiungere l'app Skycure per Android

1.  Nel portale classico di Intune scegliere **App** &gt; **Aggiungi app** per avviare Autore del software Microsoft Intune e quindi fare clic su **Avanti**.

2.  Nella pagina **Installazione software** scegliere **Collegamento esterno** e quindi incollare l'[URL dell'app Skycure per Android](https://play.google.com/store/apps/details?id=com.skycure.skycure) in **Specificare l'URL**.

    ![Autore del software Microsoft Intune - Specificare l'URL](../media/mtp/skycure-add-apps-1.png)

3.  Nella pagina **Descrizione software** immettere i valori di **Autore**, **Nome** e **Descrizione**, selezionare l'opzione **Visualizzare questo elemento come app in evidenza ed evidenziarlo nel Portale aziendale** e quindi fare clic su **Avanti**.

    ![Autore del software Microsoft Intune - Descrizione software](../media/mtp/skycure-add-apps-2.png)

4.  Fare clic su **Carica** e quindi su **Chiudi**.

## <a name="to-add-the-skycure-app-for-ios"></a>Per aggiungere l'app Skycure per iOS

1.  Nel portale classico di Intune scegliere **App** &gt; **Aggiungi app** per avviare Autore del software Microsoft Intune e quindi fare clic su **Avanti**.

2.  Nella pagina **Installazione software** scegliere **App iOS gestita dall'App Store** e quindi incollare l'[URL dell'app Skycure per iOS](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) in **Specificare l'URL**.

    ![Autore del software Microsoft Intune - App iOS gestita](../media/mtp/skycure-add-apps-3.png)

3.  Nella pagina **Descrizione software** immettere i valori di **Autore**, **Nome** e **Descrizione**, selezionare l'opzione **Visualizzare questo elemento come app in evidenza ed evidenziarlo nel Portale aziendale** e quindi fare clic su **Avanti**.

    ![Autore del software Microsoft Intune - Opzioni](../media/mtp/skycure-add-apps-4.png)

4.  Nella pagina **Requisiti** selezionare l'opzione **Qualsiasi** in **Tipo di dispositivo mobile** e quindi fare clic su **Avanti**.

5.  Fare clic su **Carica** e quindi su **Chiudi**.

## <a name="to-add-the-microsoft-authenticator-app-for-ios"></a>Per aggiungere l'app Microsoft Authenticator per iOS

1.  Nel portale classico di Intune scegliere **App** &gt; **Aggiungi app** per avviare Autore del software Microsoft Intune e quindi fare clic su **Avanti**.

2.  Nella pagina **Installazione software** scegliere **App iOS gestita dall'App Store** e quindi incollare l'[URL dell'app Microsoft Authenticator per iOS](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) in **Specificare l'URL**.

    ![Autore del software Microsoft Intune - App iOS gestita 2](../media/mtp/skycure-add-apps-5.png)

3.  Nella pagina **Descrizione software** immettere i valori di **Autore**, **Nome** e **Descrizione**, selezionare l'opzione **Visualizzare questo elemento come app in evidenza ed evidenziarlo nel Portale aziendale** e quindi fare clic su **Avanti**.

    ![Autore del software Microsoft Intune - App iOS gestita 3](../media/mtp/skycure-add-apps-6.png)

4.  Nella pagina **Requisiti** selezionare l'opzione **Qualsiasi** in **Tipo di dispositivo mobile** e quindi fare clic su **Avanti**.

5.  Fare clic su **Carica** e quindi su **Chiudi**.

## <a name="to-add-the-skycure-ios-app-configuration-policy"></a>Per aggiungere i criteri di configurazione delle app iOS Skycure

1.  Nel portale classico di Intune scegliere **Criteri** &gt; **Panoramica &gt; Aggiungi criterio**.

2.  Nell'elenco dei criteri espandere **iOS**, scegliere **Criteri di configurazione delle app per dispositivi mobili (iOS 8.0 e versioni successive)** e quindi **Crea criterio**.

    ![Criterio di configurazione delle app iOS](../media/mtp/skycure-add-apps-7.png)

3.  Nella sezione **Generale** della pagina **Crea criterio** specificare un nome e una descrizione facoltativa per il criterio di configurazione delle app iOS.

    a.  Aprire il file **skycure\_configuration.plist** usando un editor di testo come il Blocco note, copiare il contenuto e incollarlo nel corpo di **Criterio di configurazione delle app per dispositivi mobili**, scegliere **Convalida** e quindi **Salva criterio**.

       ![Criterio di configurazione delle app iOS 2](../media/mtp/skycure-add-apps-8.png)

## <a name="next-steps"></a>Passaggi successivi

[Distribuire app Skycure, l'app Microsoft Authenticator e i criteri di configurazione delle app iOS](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)
