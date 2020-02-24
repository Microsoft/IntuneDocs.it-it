---
title: Eccezioni dei criteri di trasferimento dei dati per le app
titleSuffix: Microsoft Intune
description: Creare eccezioni per i criteri di trasferimento dei dati dei criteri di protezione app di Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09c8a8819c288663936174e9317267c39eac63bc
ms.sourcegitcommit: ecaff388038fb800f2e646f8efcf8f3b1e2fd1b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/18/2020
ms.locfileid: "77437852"
---
# <a name="how-to-create-exceptions-to-the-intune-app-protection-policy-app-data-transfer-policy"></a>Come creare eccezioni per i criteri di trasferimento dei dati dei criteri di protezione app di Intune

Un amministratore può creare eccezioni per i criteri di trasferimento dei dati dei criteri di protezione app di Intune. Un'eccezione consente di scegliere in modo specifico quali app non gestite possono trasferire i dati da e verso le app gestite. IT deve considerare attendibili le app non gestite incluse nell'elenco di eccezioni. 

>[!WARNING] 
> L'utente è responsabile di apportare modifiche ai criteri relativi alle eccezioni per il trasferimento dei dati. Le aggiunte a questi criteri consentono alle app non gestite (app non gestite da Intune) di accedere ai dati protetti dalle applicazioni gestite. L'accesso ai dati protetti può comportare minacce per la protezione dei dati. Aggiungere le eccezioni di trasferimento dei dati solo per le app che l'organizzazione deve usare, ma che non supportano i criteri di protezione delle app di Intune. È anche possibile aggiungere solo le eccezioni per le app che non si considerano a rischio di perdita di dati.

Nei criteri di protezione dell'applicazione di Intune, se si imposta **Consenti all'app di trasferire i dati ad altre app** su **App gestite da criteri**, l'app può trasferire i dati solo alle app gestite da Intune. Se è necessario consentire il trasferimento dei dati ad app specifiche che non supportano i criteri di protezione delle app di Intune, è possibile creare eccezioni a questi criteri usando **Selezionare le app da esentare**. Le esenzioni consentono alle applicazioni gestite da Intune di richiamare le applicazioni non gestite in base al protocollo URL (iOS) o al nome del pacchetto (Android). Per impostazione predefinita, Intune aggiunge le applicazioni native più importanti a questo elenco di eccezioni. 

> [!NOTE]
> La modifica o l'aggiunta alle eccezioni dei criteri di trasferimento dei dati non influisce su altri criteri di protezione dell'app, ad esempio taglia, copia e incolla restrizioni. 

## <a name="ios-data-transfer-exceptions"></a>Eccezioni per il trasferimento dei dati iOS
Per i criteri destinati a iOS/iPadOS, è possibile configurare eccezioni per il trasferimento dei dati tramite il protocollo URL. Per aggiungere un'eccezione, vedere la documentazione offerta dallo sviluppatore dell'app per trovare informazioni sui protocolli URL supportati. Per altre informazioni sulle eccezioni per il trasferimento dei dati iOS/iPadOS, vedere [Impostazioni dei criteri di protezione delle app per iOS/iPadOS - Esenzioni per il trasferimento dei dati](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> Microsoft non offre un metodo che consenta di trovare manualmente il protocollo dell'URL per la creazione di eccezioni delle app per le applicazioni di terze parti. 

## <a name="android-data-transfer-exceptions"></a>Eccezioni per il trasferimento dei dati Android
Per i criteri destinati ad Android, è possibile configurare eccezioni per il trasferimento dei dati tramite il nome del pacchetto dell'app. È possibile accedere alla pagina di **Google Play** Store dell'app a cui si vuole aggiungere un'eccezione per trovare il nome del pacchetto dell'app. Per altre informazioni sulle eccezioni per il trasferimento dei dati Android, vedere [Impostazioni dei criteri di protezione delle app per Android - Esenzioni per il trasferimento dei dati](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> È possibile trovare l'ID pacchetto di un'app selezionando l'app in Google Play Store. L'ID del pacchetto è contenuto nell'URL della pagina dell'app. Ad esempio, l'ID pacchetto dell'app Microsoft Word è **com.microsoft.office.word**.

### <a name="example"></a>Esempio
Aggiungendo il pacchetto **Webex** come un'eccezione per i criteri di trasferimento dei dati MAM, i collegamenti Webex presenti all'interno di un messaggio di posta elettronica di Outlook possono essere aperti direttamente nell'applicazione Webex. Il trasferimento dei dati rimarrà limitato nelle altre applicazioni non gestite.

- Esempio **Webex** iOS/iPadOS:   per esentare l'app **Webex** in modo che possa essere chiamata dalle app gestite da Intune, è necessario aggiungere un'eccezione per il trasferimento dei dati per la stringa seguente: <code>wbx</code>
    
- Esempio **Mappe** iOS/iPadOS:   per esentare l'app **Maps** nativa in modo che possa essere chiamata dalle app gestite da Intune, è necessario aggiungere un'eccezione per il trasferimento dei dati per la stringa seguente: <code>maps</code>

- Esempio **Webex** Android:   per esentare l'app **Webex** in modo che possa essere chiamata dalle app gestite da Intune, è necessario aggiungere un'eccezione per il trasferimento dei dati per la stringa seguente: <code>com.cisco.webex.meetings</code>
    
- Esempio **SMS** Android:   per esentare l'app **SMS** nativa in modo che possa essere chiamata dalle app gestite da Intune in diverse app di messaggistica e dispositivi Android, è necessario aggiungere le eccezioni per il trasferimento dei dati per le stringhe seguenti: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

- Esempio **Programma di installazione** Android: Per esentare l'app **Programma di installazione dei certificati** nativa in modo che Outlook per Android possa installare un certificato S/MIME (inviato come allegato di posta elettronica) nell'archivio chiavi Android, è necessario aggiungere l'eccezione per il trasferimento dei dati per la stringa seguente: <code>com.android.certinstaller</code>. Per altre informazioni, vedere [Applicazione di etichette di riservatezza e protezione in Outlook per iOS/iPadOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/sensitive-labeling-and-protection-outlook-for-ios-android).

## <a name="next-steps"></a>Passaggi successivi

- [Creare e distribuire i criteri di protezione delle app](app-protection-policies.md)
- [Impostazioni dei criteri di protezione delle app per iOS - Esenzioni per il trasferimento dei dati](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Impostazioni dei criteri di protezione delle app per Android - Esenzioni per il trasferimento dei dati](app-protection-policy-settings-android.md#data-transfer-exemptions)
