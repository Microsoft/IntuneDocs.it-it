---
title: Aggiungere app Mobile Threat Defense a dispositivi non registrati
titleSuffix: Microsoft Intune
description: Aggiungere app Mobile Threat Defense a dispositivi non registrati dagli utenti del dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72794459"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>Aggiungere app Mobile Threat Defense a dispositivi non registrati

Per impostazione predefinita, quando si usano i criteri di protezione delle app di Intune con Mobile Threat Defense, Intune esegue le attività necessarie per guidare l'utente finale nel dispositivo per l'installazione e l'accesso a tutte le app necessarie per abilitare le connessioni con i servizi pertinenti.

Gli utenti finali devono usare Microsoft Authenticator (iOS) per registrare il dispositivo e Mobile Threat Defense (Android e iOS) per ricevere notifiche quando viene identificata una minaccia nei dispositivi mobili e per ricevere indicazioni per risolvere la condizione di minaccia.

Facoltativamente, è anche possibile usare Intune per aggiungere e distribuire le app Microsoft Authenticator e Mobile Threat Defense (MTD).

> [!NOTE] 
> Questo articolo si applica a tutti i partner Mobile Threat Defense che supportano i criteri di protezione delle app: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).
> 
> Per i dispositivi non registrati, **non sono necessari criteri di configurazione delle app iOS** per configurare l'app Mobile Threat Defense per iOS usata con Intune. Si tratta di una differenza fondamentale rispetto ai dispositivi registrati in Intune. 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Configurare Microsoft Authenticator per iOS tramite Intune (facoltativo)
Quando si usano i criteri di protezione delle app di Intune con Mobile Threat Defense, Intune guiderà l'utente finale per l'installazione, l'accesso e la registrazione del dispositivo con Microsoft Authenticator (iOS).

Tuttavia, se si vuole rendere disponibile l'app agli utenti finali tramite il Portale aziendale Intune, vedere le istruzioni per l'[aggiunta di app dello store iOS a Microsoft Intune](../apps/store-apps-ios.md). Usare questo [URL di iOS App Store per Microsoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) durante l'esecuzione della sezione **Configurare le informazioni sull'app**. Non dimenticare di [assegnare l'app a gruppi con Intune](../apps/apps-deploy.md) come passaggio finale.

> [!NOTE] 
> Per i dispositivi iOS, perché gli utenti possano eseguire la verifica della propria identità in Azure AD, è necessario [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to). Nei dispositivi Android il portale aziendale Intune funge da broker per la verifica dell'identità degli utenti da parte di Azure AD.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Rendere disponibili app Mobile Threat Defense tramite Intune (facoltativo)
Quando si usano i criteri di protezione delle app di Intune con Mobile Threat Defense, Intune guiderà l'utente finale per l'installazione e l'accesso all'app client Mobile Threat Defense richiesta. 

Tuttavia, se si vuole rendere disponibile l'app agli utenti finali tramite il Portale aziendale Intune, è possibile seguire i passaggi seguenti nel [portale di Azure ](https://portal.azure.com/). Assicurarsi di avere familiarità con le procedure seguenti:

- [Aggiunta di un'app in Intune](../apps/apps-add.md).
- [Assegnazione di un'app con Intune](../apps/apps-deploy.md).

### <a name="making-lookout-for-work-available-to-end-users"></a>Rendere Lookout for Work disponibile per gli utenti finali
- **Android**  
  - Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](../apps/store-apps-android.md). Usare questo [URL di Play Store per l'app Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) durante il completamento della sezione **Configurare le informazioni sull'app**.

- **iOS**
  - Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](../apps/store-apps-ios.md). Usare questo [URL di iOS App Store per l'app Lookout for Work](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) durante il completamento della sezione **Configurare le informazioni sull'app**.

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>Rendere Zimperium disponibile per gli utenti finali
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - Vedere le istruzioni per [aggiungere app dello Store iOS a Microsoft Intune](../apps/store-apps-ios.md). Usare questo [URL di App Store per l'app Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) durante il completamento della sezione **Configurare le informazioni sull'app**.
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>Rendere Better Mobile disponibile per gli utenti finali 
- **Android**
  - Vedere le istruzioni per [aggiungere app di Android Store a Microsoft Intune](../apps/store-apps-android.md). Usare questo [URL di Play Store per l'app Active Shield](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) durante il completamento della sezione **Configurare le informazioni sull'app**.
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>Passaggi successivi  

- [Abilitare il connettore Mobile Threat Defense in Intune per i dispositivi non registrati](~/protect/mtd-enable-unenrolled-devices.md)

