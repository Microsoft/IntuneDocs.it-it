---
title: Eccezioni dei criteri di trasferimento dei dati per le app
titleSuffix: Microsoft Intune
description: Creare eccezioni per i criteri di trasferimento dei dati di gestione per applicazioni mobili (MAM) di Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b860b68bbf8940a89533159885f471f5337ca0e8
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Come creare eccezioni per i criteri di trasferimento dei dati di gestione per applicazioni mobili (MAM) di Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In qualità di amministratore, è possibile creare eccezioni per i criteri di trasferimento dei dati di gestione per applicazioni mobili (MAM) di Intune. Un'eccezione consente di scegliere in modo specifico quali app non gestite possono trasferire i dati da e verso le app gestite. Le app non gestite che si include nell'elenco di eccezioni devono essere considerate attendibili da IT. 

>[!WARNING] 
> L'utente è responsabile di apportare modifiche ai criteri relativi alle eccezioni per il trasferimento dei dati. Le aggiunte a questi criteri consentono alle app non gestite (app non gestite da Intune) di accedere ai dati protetti dalle applicazioni gestite. L'accesso ai dati protetti può comportare minacce per la protezione dei dati. Aggiungere le eccezioni di trasferimento dei dati solo per le app che l'organizzazione deve usare, ma che non supportano i criteri di protezione delle app di Intune. È anche possibile aggiungere solo le eccezioni per le app che non si considerano a rischio di perdita di dati.

Nei criteri di protezione dell'applicazione di Intune, se si imposta **Consenti all'app di trasferire i dati ad altre app** su **App gestite da criteri**, l'app può trasferire i dati solo alle app gestite da Intune. Se è necessario consentire il trasferimento dei dati ad app specifiche che non supportano i criteri di protezione delle app di Intune, è possibile creare eccezioni a questi criteri usando **Selezionare le app da esentare**. Le esenzioni consentono alle applicazioni gestite da Intune di richiamare le applicazioni non gestite in base al protocollo URL (iOS) o al nome del pacchetto (Android). Per impostazione predefinita, Intune aggiunge le applicazioni native più importanti a questo elenco di eccezioni. 

> [!NOTE]
> La modifica o l'aggiunta alle eccezioni dei criteri di trasferimento dei dati non influisce su altri criteri di protezione dell'app, ad esempio taglia, copia e incolla restrizioni. 

## <a name="ios-data-transfer-exceptions"></a>Eccezioni per il trasferimento dei dati iOS
Per i criteri destinati a iOS, è possibile configurare eccezioni per il trasferimento dei dati tramite il protocollo URL. Per aggiungere un'eccezione, vedere la documentazione offerta dallo sviluppatore dell'app per trovare informazioni sui protocolli URL supportati. Per altre informazioni sulle eccezioni per il trasferimento dei dati iOS, vedere [Impostazioni dei criteri di protezione delle app per iOS - Esenzioni per il trasferimento dei dati](app-protection-policy-settings-ios.md#data-transfer-exemptions).

## <a name="android-data-transfer-exceptions"></a>Eccezioni per il trasferimento dei dati Android
Per i criteri destinati ad Android, è possibile configurare eccezioni per il trasferimento dei dati tramite il nome del pacchetto dell'app. È possibile accedere alla pagina di **Google Play** Store dell'app a cui si vuole aggiungere un'eccezione per trovare il nome del pacchetto dell'app. Per altre informazioni sulle eccezioni per il trasferimento dei dati Android, vedere [Impostazioni dei criteri di protezione delle app per Android - Esenzioni per il trasferimento dei dati](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> È possibile trovare l'ID pacchetto di un'app selezionando l'app in Google Play Store. L'ID del pacchetto è contenuto nell'URL della pagina dell'app. Ad esempio, l'ID pacchetto dell'app Microsoft Word è **com.microsoft.office.word**.

### <a name="example"></a>Esempio
Aggiungendo il pacchetto **Webex** come un'eccezione per i criteri di trasferimento dei dati MAM, i collegamenti Webex presenti all'interno di un messaggio di posta elettronica di Outlook possono essere aperti direttamente nell'applicazione Webex. Il trasferimento dei dati rimarrà limitato nelle altre applicazioni non gestite.

- Esempio **Webex** iOS: per esentare l'app **Webex** in modo che possa essere chiamata dalle app gestite da Intune, è necessario aggiungere un'eccezione per il trasferimento dei dati per la stringa seguente: <code>wbx</code>
    
 - Esempio **Maps** iOS: per esentare l'app **Maps** nativa in modo che possa essere chiamata dalle app gestite da Intune, è necessario aggiungere un'eccezione per il trasferimento dei dati per la stringa seguente: <code>maps</code>

- Esempio **Webex** Android: per esentare l'app **Webex** in modo che possa essere chiamata dalle app gestite da Intune, è necessario aggiungere un'eccezione per il trasferimento dei dati per la stringa seguente: <code>com.cisco.webex.meetings</code>
    
- Esempio **SMS** Android: per esentare l'app **SMS** nativa in modo che possa essere chiamata dalle app gestite da Intune in diverse app di messaggistica e dispositivi Android, è necessario aggiungere le eccezioni per il trasferimento dei dati per le stringhe seguenti: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>Passaggi successivi

- [Creare e distribuire i criteri di protezione delle app](app-protection-policies.md)
- [Impostazioni dei criteri di protezione delle app per iOS - Esenzioni per il trasferimento dei dati](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Impostazioni dei criteri di protezione delle app per Android - Esenzioni per il trasferimento dei dati](app-protection-policy-settings-android.md#data-transfer-exemptions)
