---
title: Aggiungere e assegnare app MTD a Microsoft Intune | Microsoft Intune
description: Usare Intune per aggiungere app Mobile Threat Defense (MTD), l'app Microsoft Authenticator e criteri di configurazione di iOS nel portale di Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d08a7332ba96f552b488ad3f5d00004d0445d7ec
ms.sourcegitcommit: 6058c611d5a54076121af1d327a43ad861a43f8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2019
ms.locfileid: "53995998"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Aggiungere e assegnare app Mobile Threat Defense (MTD) con Intune

> [!NOTE] 
> Questo argomento si applica a tutti i partner Mobile Threat Defense.

È possibile usare Intune per aggiungere e distribuire app Mobile Threat Defense (MTD), consentendo così agli utenti finali di ricevere notifiche quando viene identificata una minaccia nei dispositivi mobili e per ricevere indicazioni per risolvere le minacce.


## <a name="before-you-begin"></a>Prima di iniziare

La procedura seguente deve essere completata nel [Portale di Azure](https://portal.azure.com/). Assicurarsi di avere familiarità con le procedure seguenti:

  -   [Aggiunta di un'app in Intune](apps-add.md).
  -   [Aggiunta dei criteri di configurazione delle app iOS in Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
  -   [Assegnazione di un'app con Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

> [!TIP]
> Nei dispositivi Android il portale aziendale Intune funge da broker per la verifica dell'identità degli utenti da parte di Azure AD.

## <a name="configure-microsoft-authenticator-for-ios"></a>Configurare Microsoft Authenticator per iOS
Per i dispositivi iOS, perché gli utenti possano eseguire la verifica della propria identità in Azure AD, è necessario [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to). Sono anche necessari i criteri di configurazione delle app iOS, che impostano l'app iOS MTD da usare con Intune.

Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dello Store dell'app Microsoft Authenticator ](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) nel **passaggio 12** nella sezione **Configurare le informazioni sull'app**.

## <a name="configure-mtd-applications"></a>Configurare applicazioni MTD

Scegliere la sezione corrispondente al provider MTD:

  - [Lookout for Work](#configure-lookout-for-work-apps)
  - [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
  - [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
  - [Zimperium](#configure-zimperium-apps)
  - [Pradeo](#configure-pradeo-apps)
  - [Better Mobile](#configure-better-mobile-apps)

### <a name="configure-lookout-for-work-apps"></a>Configurare app Lookout for Work

- **Android**
  - Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dell'App Store di Google per Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) nel **passaggio 7**.

- **iOS**

  - Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dell'App Store iOS per l'app Lookout for Work](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) nel **passaggio 12** nella sezione **Configurare le informazioni sull'app**.

-   **App Lookout for Work al di fuori dell'Apple Store**
    - È necessario firmare di nuovo l'app Lookout for Work per iOS. Lookout distribuisce l'app Lookout for Work per iOS all'esterno dell'App Store di iOS. Prima di distribuire l'app, è necessario firmare di nuovo l'app usando il proprio iOS Enterprise Developer Certificate.
    - Per istruzioni dettagliate su come firmare di nuovo l'app Lookout for Work per iOS, vedere [Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714) (Processo per firmare di nuovo l'app Lookout for Work per iOS) nel sito Web Lookout.

    - **Abilitare l'autenticazione di Azure AD per gli utenti dell'app Lookout for Work per iOS.**

        1. Passare al [Portale di Azure](https://portal.azure.com), accedere con le credenziali personali e quindi passare alla pagina dell'applicazione.

        2. Aggiungere l'**app Lookout for Work per iOS** come **applicazione client nativa**.

        3. Sostituire **com.lookout.enterprise.nomesocietà** con l'ID bundle del cliente selezionato durante l'accesso a IPA.

        4.  Aggiungere l'URI di reindirizzamento aggiuntivo: **&lt;portaleaziendale://code/>** seguito da una versione con codifica URL dell'URI di reindirizzamento originale.

        5.  Aggiungere le **autorizzazioni delegate** all'app.

        > [!NOTE] 
        > Per altri dettagli, vedere [Configurare un'applicazione client nativa con Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

     - **Aggiungere il file ipa di Lookout for Work.**

        - Caricare il file con estensione ipa nuovamente firmato come descritto nell'argomento [Aggiungere app LOB per iOS in Intune](lob-apps-ios.md). È anche necessario impostare la versione iOS minima su iOS 8.0 o successiva.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Configurare app di Symantec Endpoint Protection Mobile

 - **Android**

    - Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Nel **passaggio 7** usare questo [URL dello Store dell'app SEP Mobile](https://play.google.com/store/apps/details?id=com.skycure.skycure).  Per **Sistema operativo minimo** selezionare **Android 4.0 (Ice Cream Sandwich)**.

 - **iOS**

    - Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Nel **passaggio 12** usare questo [URL dello Store dell'app SEP Mobile](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) nella sezione **Configurare le informazioni sull'app**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Configurare app di Check Point SandBlast Mobile

 - **Android**

    - Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dell'App Store di Check Point SandBlast Mobile](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) al **passaggio 7**.

 - **iOS**

    - Contattare [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) per ottenere l'app iOS. Vedere le istruzioni per [aggiungere app dello Store iOS in Microsoft Intune](store-apps-ios.md), quindi usare l'URL di Apple Store al **passaggio 12** della sezione **Configurare le informazioni sull'app**.

### <a name="configure-zimperium-apps"></a>Configurare app di Zimperium

 - **Android**

    - Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dell'App Store di Zimperium](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) nel **passaggio 7**.

 - **iOS**

    - Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dell'App Store di Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) nel **passaggio 12** nella sezione **Configurare le informazioni sull'app**.

### <a name="configure-pradeo-apps"></a>Configurare app di Pradeo

 - **Android**

    - Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dello store delle app Pradeo](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) nel **passaggio 7**.

 - **iOS**

    - Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dello store delle app Pradeo](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) nel **passaggio 12** nella sezione **Configurare le informazioni sull'app**.

### <a name="configure-better-mobile-apps"></a>Configurare le app di Better Mobile

 - **Android**

    - Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](store-apps-android.md). Usare questo [URL dell'App Store di Active Shield](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) nel **passaggio 7**.

 - **iOS**

    - Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](store-apps-ios.md). Usare questo [URL dell'App Store di ActiveShield](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) nel **passaggio 12** nella sezione **Configurare le informazioni sull'app**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>Configurare le app MTD con criteri di configurazione di app iOS

### <a name="lookout-for-work-app-configuration-policy"></a>Criteri di configurazione delle app Lookout for Work

- Creare i criteri di configurazione delle app iOS come descritto nell'articolo relativo all'[uso dei criteri di configurazione delle app per iOS](app-configuration-policies-use-ios.md).

### <a name="sep-mobile-app-configuration-policy"></a>Criteri di configurazione delle app SEP Mobile

-   Usare lo stesso account di Azure AD configurato in precedenza nella [console di gestione di Symantec Endpoint Protection Management](https://aad.skycure.com) che deve corrispondere all'account usato per accedere al portale classico di Intune.

-   È necessario **scaricare** il file dei criteri di configurazione dell'app iOS: 
    -   Passare alla [console di gestione di Symantec Endpoint Protection Management](https://aad.skycure.com) e accedere con le credenziali di amministratore.

    -   Andare a **Settings** (Impostazioni) e sotto **Integrations** (Integrazioni) scegliere **Intune**. Scegliere **EMM Integration Selection** (Selezione integrazione EMM). Scegliere **Microsoft** e quindi salvare la selezione.

    -   Fare clic sul collegamento **Integration setup files** (File di installazione dell'integrazione) e salvare il file \*.zip generato. Il file con estensione zip contiene il file ***.plist** che verrà usato per creare i criteri di configurazione dell'app iOS in Intune.

    -   Vedere le istruzioni per [l'uso di criteri di configurazione di app Microsoft Intune per iOS](app-configuration-policies-use-ios.md) per aggiungere i criteri di configurazione dell'app SEP Mobile per iOS.

    - Al **passaggio 8** usare l'opzione **Immettere i dati XML**, copiare il contenuto del file ***.plist** e incollarlo nel corpo dei criteri di configurazione.

> [!NOTE]
> Se non è possibile recuperare i file, contattare il [supporto aziendale per Symantec Endpoint Protection Mobile](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Criteri di configurazione delle app Check Point SandBlast Mobile

- Vedere le istruzioni per l'[uso dei criteri di configurazione di app Microsoft Intune per iOS](app-configuration-policies-use-ios.md) per aggiungere i criteri di configurazione dell'app Check Point SandBlast Mobile per iOS.
    - Al **passaggio 8** usare l'opzione **Immettere i dati XML**, copiare il contenuto seguente e incollarlo nel corpo dei criteri di configurazione.

```
<dict><key>MDM</key><string>INTUNE</string></dict>
```

### <a name="zimperium-app-configuration-policy"></a>Criteri di configurazione delle app Zimperium

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

### <a name="better-mobile-app-configuration-policy"></a>Criteri di configurazione delle app Better Mobile

- Vedere le istruzioni per [l'uso di criteri di configurazione di app Microsoft Intune per iOS](app-configuration-policies-use-ios.md) per aggiungere i criteri di configurazione dell'app Better Mobile per iOS.
    - Al **passaggio 8** usare l'opzione **Immettere i dati XML**, copiare il contenuto seguente e incollarlo nel corpo dei criteri di configurazione. Sostituire l'URL `https://client.bmobi.net` con l'URL della console appropriato.

```
<dict>
<key>better_server_url</key>
<string>https://client.bmobi.net</string>
<key>better_udid</key>
<string>{{aaddeviceid}}</string>
<key>better_user</key>
<string>{{userprincipalname}}</string>
</dict>
```

## <a name="assign-apps-to-groups"></a>Assegnare app ai gruppi

- Questo passaggio si applica a tutti i partner MTD. Vedere le istruzioni per l'[assegnazione di app a gruppi con Intune](apps-deploy.md).

## <a name="next-steps"></a>Passaggi successivi

- [Configurare i criteri di conformità dei dispositivi per MTD](mtd-device-compliance-policy-create.md)
