---
title: Aggiungere e assegnare app MTD a Microsoft Intune
titleSuffix: 
description: Usare Intune per aggiungere app Mobile Threat Defense (MTD), l'app Microsoft Authenticator e criteri di configurazione di iOS nel portale di Azure.
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fc71620fee1b1df907a4027c1c57cd91b53032e
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Aggiungere e assegnare app Mobile Threat Defense (MTD) con Intune

> [!NOTE] 
> Questo argomento si applica a tutti i partner Mobile Threat Defense.

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

### <a name="all-mtd-partners"></a>Tutti i partner MTD

#### <a name="microsoft-authenticator-app-for-ios"></a>App Microsoft Authenticator per iOS

- Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dello Store dell'app Microsoft Authenticator ](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) nel **passaggio 5** nella sezione **Configurare le informazioni sull'app**.

### <a name="lookout"></a>Lookout

#### <a name="android"></a>Android
- Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dell'App Store di Google per Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) nel **passaggio 7**.

#### <a name="ios"></a>iOS

- Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dell'App Store iOS per l'app Lookout for Work](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) nel **passaggio 5** nella sezione **Configurare le informazioni sull'app**.

#### <a name="lookout-for-work-app-outside-the-apple-store"></a>App Lookout for Work di fuori dell'Apple Store

È necessario firmare di nuovo l'app Lookout for Work per iOS. Lookout distribuisce l'app Lookout for Work per iOS all'esterno dell'App Store di iOS. Prima di distribuire l'app, è necessario firmare di nuovo l'app usando il proprio iOS Enterprise Developer Certificate.

Per istruzioni dettagliate su come firmare di nuovo l'app Lookout for Work per iOS, vedere [Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714) (Processo per firmare di nuovo l'app Lookout for Work per iOS) nel sito Web Lookout.

##### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Abilitare l'autenticazione di Azure AD per l'app Lookout for Work per iOS

Consentire l'autenticazione di Azure Active Directory agli utenti iOS seguendo questa procedura:

1. Passare al [Portale di Azure](https://portal.azure.com), accedere con le credenziali personali e quindi passare alla pagina dell'applicazione.
  
2. Aggiungere l'**app Lookout for Work per iOS** come **applicazione client nativa**.

3. Sostituire **com.lookout.enterprise.nomesocietà** con l'ID bundle del cliente selezionato durante l'accesso a IPA.

4.  Aggiungere l'URI di reindirizzamento aggiuntivo: **&lt;portaleaziendale://code/>** seguito da una versione con codifica URL dell'URI di reindirizzamento originale.

5.  Aggiungere le **autorizzazioni delegate** all'app.

    > [!NOTE] 
    > Per altri dettagli, vedere [Configurare un'applicazione client nativa con Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

##### <a name="add-the-lookout-for-work-ipa-file"></a>Aggiungere il file ipa di Lookout for Work

- Caricare il file con estensione ipa nuovamente firmato come descritto nell'argomento [Aggiungere app LOB per iOS in Intune](lob-apps-ios.md). È anche necessario impostare la versione iOS minima su iOS 8.0 o successiva.

### <a name="skycure"></a>Skycure

#### <a name="android"></a>Android

- Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dello Store dell'app Skycure](https://play.google.com/store/apps/details?id=com.skycure.skycure) nel **passaggio 7**.

#### <a name="ios"></a>iOS

- Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dello Store dell'app Skycure](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) nel **passaggio 5** nella sezione **Configurare le informazioni sull'app**.

### <a name="check-point-sandblast-mobile"></a>Check Point SandBlast Mobile

#### <a name="android"></a>Android

- Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dell'App Store di Check Point SandBlast Mobile](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) al **passaggio 7**.

#### <a name="ios"></a>iOS

- Contattare [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) per ottenere l'app iOS. Vedere le istruzioni per [aggiungere app dello Store iOS in Microsoft Intune](store-apps-ios.md), quindi usare l'URL di Apple Store al **passaggio 5** della sezione **Configurare le informazioni sull'app**.

### <a name="zimperium"></a>Zimperium

#### <a name="android"></a>Android

- Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dell'App Store di Zimperium](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) nel **passaggio 7**.

#### <a name="ios"></a>iOS

- Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dell'App Store di Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) nel **passaggio 5** nella sezione **Configurare le informazioni sull'app**.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>Per associare l'app MTD ai criteri di configurazione di app iOS

### <a name="for-lookout"></a>Per Lookout

- Creare i criteri di configurazione delle app iOS come descritto nell'argomento relativo all'[uso di criteri di configurazione delle app per iOS](app-configuration-policies-use-ios.md).

### <a name="for-skycure"></a>Per Skycure

-   Usare lo stesso account di Azure AD configurato in precedenza nella [console di gestione di Skycure](https://aad.skycure.com) che dovrebbe corrispondere all'account usato per accedere al portale classico di Intune.

-   È necessario **scaricare** il file dei criteri di configurazione dell'app iOS: 
    -   Passare alla [console di gestione di Skycure](https://aad.skycure.com) e accedere con le credenziali di aministratore.
    
    -   Scegliere **Settings** (Impostazioni) &gt; **Device Management Integrations** (Integrazioni di gestione dei dispositivi) &gt; **EMM Integration Selection** (Selezione integrazione EMM), quindi scegliere **Microsoft Intune** e infine salvare la selezione.
    
    -   Fare clic sul collegamento **Integration setup files** (File di installazione dell'integrazione) e salvare il file \*.zip generato. Il file con estensione zip contiene il file **skycure\_configuration.plist** che verrà usato per creare i criteri di configurazione dell'app iOS in Intune.
    
    -   Vedere le istruzioni per [l'uso di criteri di configurazione di app Microsoft Intune per iOS](app-configuration-policies-use-ios.md) per aggiungere i criteri di configurazione dell'app Skycure per iOS.
    
    - Al **passaggio 8** usare l'opzione **Immettere i dati XML**, copiare il contenuto del file **skycure_configuration.plist** e incollarlo nel corpo dei criteri di configurazione.

È anche possibile copiare il contenuto di **skycure_configuration.plist** da qui:

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-check-point-sandblast-mobile"></a>Per Check Point SandBlast Mobile

- Vedere le istruzioni per l'[uso dei criteri di configurazione di app Microsoft Intune per iOS](app-configuration-policies-use-ios.md) per aggiungere i criteri di configurazione dell'app Check Point SandBlast Mobile per iOS.
    - Al **passaggio 8** usare l'opzione **Immettere i dati XML**, copiare il contenuto seguente e incollarlo nel corpo dei criteri di configurazione.

```
<dict><key>MDM</key><string>INTUNE</string></dict>

```

### <a name="for-zimperium"></a>Per Zimperium

- Vedere le istruzioni per [l'uso di criteri di configurazione di app Microsoft Intune per iOS](app-configuration-policies-use-ios.md) per aggiungere i criteri di configurazione delle app di Zimperium per iOS.
    - Al **passaggio 8** usare l'opzione **Immettere i dati XML**, copiare il contenuto seguente e incollarlo nel corpo dei criteri di configurazione.

```
<dict>
<key>provider</key><string>Intune</string>
<key>userprincipalname</key><string>{{userprincipalname}}</string>
<key>deviceid</key>
<string>{{deviceid}}</string>
<key>serialnumber</key>
<string>{{serialnumber}}</string>
<key>udidlast4digits</key>
<string>{{udidlast4digits}}</string>
</dict>

```

## <a name="to-assign-apps-all-mtd-partners"></a>Per assegnare le app (tutti i partner MTD)

- Vedere le istruzioni per l'[assegnazione di app a gruppi con Intune](apps-deploy.md).

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere criteri di conformità dei dispositivi per MTD](mtd-device-compliance-policy-create.md)
