---
title: Aggiungere e assegnare app MTD in Intune
titleSuffix: Intune on Azure
description: Aggiungere app MTD, l'app Microsoft Authenticator e i criteri di configurazione delle app iOS in Intune in Azure
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7b3fb86648a86b161eadfc071bdacbfd4ea0222f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Aggiungere e assegnare app Mobile Threat Defense (MTD) con Intune

È possibile usare Intune per aggiungere e distribuire app MTD, consentendo così agli utenti finali di ricevere notifiche quando viene identificata una minaccia nei dispositivi mobili e per ricevere indicazioni per risolvere le minacce.

Per i dispositivi iOS, perché gli utenti possano eseguire la verifica della propria identità in Azure AD, è necessario [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to). Sono anche necessari i criteri di configurazione delle app iOS, che indicano l'app iOS MTD da usare con Intune.

> [!TIP]
> Nei dispositivi Android i portale aziendale Intune funge da broker per la verifica dell'identità degli utenti da parte di Azure AD.

## <a name="before-you-begin"></a>Prima di iniziare

-   La procedura seguente deve essere completata nel [Portale di Azure](https://portal.azure.com/).

-   Assicurarsi di avere familiarità con le procedure seguenti:

    -   [Aggiunta di un'app in Intune](apps-add.md).

    -   [Aggiunta dei criteri di configurazione delle app iOS in Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

    -   [Assegnazione di un'app con Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

    -   [ Aggiunta di criteri di configurazione delle app iOS](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-add-apps"></a>Per aggiungere app

### <a name="skycure-app-for-android"></a>App Skycure per Android

- Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dello Store dell'app Skycure](https://play.google.com/store/apps/details?id=com.skycure.skycure) nel **passaggio 7**.

### <a name="skycure-app-for-ios"></a>App Skycure per iOS

- Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dello Store dell'app Skycure](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) nel **passaggio 5** nella sezione **Configurare le informazioni sull'app**.

### <a name="microsoft-authenticator-app-for-ios"></a>App Microsoft Authenticator per iOS

- Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dello Store dell'app Microsoft Authenticator ](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) nel **passaggio 5** nella sezione **Configurare le informazioni sull'app**.

### <a name="lookout-for-work-android-app"></a>App Android Lookout for Work

- Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dell'App Store di Google per Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) nel **passaggio 7**.

### <a name="lookout-for-work-ios-app"></a>App iOS Lookout for Work

- Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dell'App Store iOS per l'app Lookout for Work](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) nel **passaggio 5** nella sezione **Configurare le informazioni sull'app**.

### <a name="lookout-for-work-app-outside-the-apple-store"></a>App Lookout for Work di fuori dell'Apple Store

È necessario firmare di nuovo l'app Lookout for Work per iOS. Lookout distribuisce l'app Lookout for Work per iOS all'esterno dell'App Store di iOS. Prima di distribuire l'app, è necessario firmare di nuovo l'app usando il proprio iOS Enterprise Developer Certificate.

Per istruzioni dettagliate su come firmare di nuovo l'app Lookout for Work per iOS, vedere [Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714) (Processo per firmare di nuovo l'app Lookout for Work per iOS) nel sito Web Lookout.

#### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Abilitare l'autenticazione di Azure AD per l'app Lookout for Work per iOS

Consentire l'autenticazione di Azure Active Directory agli utenti iOS seguendo questa procedura:

1. Passare al [Portale di Azure](https://portal.sazure.com), accedere con le credenziali personali e quindi passare alla pagina dell'applicazione.
  
2. Aggiungere l'**app Lookout for Work per iOS** come **applicazione client nativa**.

3. Sostituire **com.lookout.enterprise.nomesocietà** con l'ID bundle del cliente selezionato durante l'accesso a IPA.

4.  Aggiungere l'URI di reindirizzamento aggiuntivo: **&lt;portaleaziendale://code/>** seguito da una versione con codifica URL dell'URI di reindirizzamento originale.

5.  Aggiungere le **autorizzazioni delegate** all'app.

    > [!NOTE] 
    > Per altri dettagli, vedere [Configurare un'applicazione client nativa con Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

#### <a name="add-the-lookout-for-work-ipa-file"></a>Aggiungere il file ipa di Lookout for Work

- Caricare il file con estensione ipa nuovamente firmato come descritto nell'argomento [Aggiungere app LOB per iOS in Intune](lob-apps-ios.md). È anche necessario impostare la versione iOS minima su iOS 8.0 o successiva.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>Per associare l'app MTD ai criteri di configurazione di app iOS

### <a name="for-skycure"></a>Per Skycure

-   Usare lo stesso account di Azure AD configurato in precedenza nella console di gestione di Skycure, che dovrebbe corrispondere all'account usato per accedere alla console classica di Intune.

-   È necessario avere pronto il file di integrazione di Skycure, ovvero il file con estensione zip scaricato in precedenza dalla console di gestione di Skycure, che contiene il file **skycure\_configuration.plist** con i parametri dei criteri di configurazione delle app iOS.

- Vedere le istruzioni per [l'uso di criteri di configurazione di app Microsoft Intune per iOS](app-configuration-policies-use-ios.md) per aggiungere i criteri di configurazione dell'app Skycure per iOS.
    - Nel passaggio 8, usare l'opzione **Immettere i dati XML**, copiare il contenuto del file **skycure_configuration.plist** e incollarlo nel corpo dei criteri di configurazione.

È anche possibile copiare il contenuto di **skycure_configuration.plist** da qui:

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-lookout"></a>Per Lookout

- Creare i criteri di configurazione delle app iOS come descritto nell'argomento relativo all'[uso di criteri di configurazione delle app per iOS](app-configuration-policies-use-ios.md).

## <a name="to-assign-mtd-apps"></a>Per assegnare app MTD

- Vedere le istruzioni per [l'assegnazione di app a gruppi con Intune](apps-deploy.md).

## <a name="next-steps"></a>Passaggi successivi

[Configurare l'integrazione di Skycure con Intune](skycure-mtd-connector-integration.md)
[Set up the Lookout integration with Intune](lookout-mtd-connector-integration.md) (Configurare l'integrazione di Lookout con Intune)
