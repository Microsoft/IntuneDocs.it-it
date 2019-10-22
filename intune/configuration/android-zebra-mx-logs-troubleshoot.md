---
title: Usare i log StageNow nei dispositivi Android zebra in Microsoft Intune-Azure | Microsoft Docs
description: Vedere problemi comuni e soluzioni quando si usa StageNow nei dispositivi Android con Microsoft Intune. Viene anche illustrato come ottenere i log e vedere esempi di come leggere i log per ottenere esito positivo o negativo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7ed93c86d3fbe7ed7a6ac5d4b1a3494fb55f2bc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506982"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Risolvere i problemi e vedere i potenziali problemi nei dispositivi Android zebra in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In Microsoft Intune, è possibile usare [Zebra Mobility Extensions (MX) per gestire i dispositivi Android Zebra](android-zebra-mx-overview.md). Quando si usano i dispositivi Zebra, è possibile creare i profili in StageNow per gestire le impostazioni e caricarli in Intune. Intune usa l'app StageNow per applicare le impostazioni nei dispositivi. L'app StageNow crea anche un file di log dettagliato nel dispositivo usato per la risoluzione dei problemi.

Questa funzionalità si applica a:

- Android

Ad esempio, è possibile creare un profilo in StageNow per configurare un dispositivo. Quando si crea il profilo StageNow, l'ultimo passaggio genera un file per il test del profilo. Questo file viene utilizzato con l'app StageNow sul dispositivo.

In un altro esempio, è possibile creare un profilo in StageNow e testarlo. In Intune si aggiunge il profilo StageNow, quindi lo si assegna ai dispositivi Zebra. Quando si controlla lo stato del profilo assegnato, il profilo mostra uno stato di alto livello.

In entrambi i casi, è possibile ottenere altri dettagli dal file di log StageNow, che viene salvato nel dispositivo ogni volta che viene applicato un profilo StageNow.

Alcuni problemi non sono correlati al contenuto del profilo StageNow e non vengono riflessi nei log.

Questo articolo illustra come leggere i log StageNow ed elenca alcuni altri problemi potenziali con i dispositivi zebra che potrebbero non essere riflessi nei log.

Per informazioni su questa funzionalità [, usare e gestire i dispositivi Zebra con le estensioni Zebra Mobility](android-zebra-mx-overview.md) .

## <a name="get-the-logs"></a>Ottenere i log

### <a name="use-the-stagenow-app-on-the-device"></a>Usare l'app StageNow nel dispositivo
Quando si esegue il test di un profilo direttamente usando StageNow nel computer in, invece di usare [Intune per distribuire il profilo](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), l'app StageNow nel dispositivo salva i log dal test. Per ottenere il file di log, usare l'opzione **More (...)** nell'app StageNow sul dispositivo.

### <a name="get-logs-using-android-debug-bridge"></a>Ottenere i log con Android Debug Bridge
Per ottenere i log dopo che il profilo è già stato distribuito con Intune, connettere il dispositivo a un computer con [Android Debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) (apre il sito Web di Android).

Nel dispositivo i log vengono salvati in `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Ottenere i log dalla posta elettronica
Per ottenere i log dopo che il profilo è già stato distribuito con Intune, gli utenti finali possono inviare un messaggio di posta elettronica ai log usando un'app di posta elettronica nel dispositivo. Nel dispositivo Zebra aprire l'app Portale aziendale e [inviare i log](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). L'uso della funzionalità di invio dei log crea anche un ID evento imprevisto PowerLift, a cui è possibile fare riferimento se si contatta il supporto tecnico Microsoft.

## <a name="read-the-logs"></a>Leggere i log

Quando si esaminano i log, si verifica un errore ogni volta che viene visualizzato il tag `<characteristic-error>`. I dettagli dell'errore vengono scritti nel tag `<parm-error>` > `desc` proprietà.

## <a name="error-types"></a>Tipi di errore

I dispositivi Zebra includono diversi livelli di segnalazione degli errori:

- Il CSP non è supportato nel dispositivo. Ad esempio, il dispositivo non è un dispositivo cellulare e non ha un gestore cellulare.
- La versione di MX o OSX non corrisponde. Ogni CSP è con versione. Per una matrice di supporto completa, vedere la [documentazione di zebra](http://techdocs.zebra.com/mx/) (apre il sito Web di zebra).
- Il dispositivo segnala un altro problema o errore.

## <a name="examples"></a>Esempi

Ad esempio, si dispone del profilo di input seguente:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

Nel log, il codice XML è identico all'input. Questo output corrispondente indica che il profilo è stato applicato correttamente al dispositivo senza errori:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

In un altro esempio, l'input è il seguente:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

Il log mostra un errore, in quanto contiene un tag `<characteristic-error>`. In questo scenario, il profilo ha tentato di installare un pacchetto Android (APK) che non esiste nel percorso specificato:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Altri potenziali problemi con i dispositivi Zebra

Questa sezione elenca altri possibili problemi che possono verificarsi quando si usano dispositivi Zebra con l'amministratore del dispositivo. Questi problemi non vengono segnalati nei registri StageNow.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView non aggiornata

Quando i dispositivi meno recenti effettuano l'accesso con l'app Portale aziendale, gli utenti potrebbero visualizzare un messaggio che indica che il componente WebView di sistema non è aggiornato e deve essere aggiornato. Se il dispositivo ha Google Play installato, connetterlo a Internet e verificare la disponibilità di aggiornamenti. Se il dispositivo non ha Google Play installato, ottenere la versione aggiornata del componente e applicarlo ai dispositivi. In alternativa, eseguire l'aggiornamento al sistema operativo più recente del dispositivo emesso da Zebra.

### <a name="management-actions-take-a-long-time"></a>Le azioni di gestione importano molto tempo

Se Google Play servizi non sono disponibili, il completamento di alcune attività potrebbe richiedere fino a 8 ore. [Le limitazioni dell'app portale aziendale Intune per Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (apre un altro sito Web Microsoft) potrebbero essere una risorsa efficace.

### <a name="device-spoofing-suspected-shows-in-intune"></a>Mostra "spoofing di dispositivi sospetti" in Intune

Questo errore indica che Intune sospetta che un dispositivo Android non Zebra stia segnalando il modello e il produttore come dispositivo Zebra.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Portale aziendale app è precedente alla versione minima richiesta

Intune può aggiornare la versione minima richiesta dell'app Portale aziendale. Se Google Play non è installato nel dispositivo, l'app Portale aziendale non viene aggiornata automaticamente. Se la versione minima richiesta è più recente della versione installata, l'app Portale aziendale smette di funzionare. Eseguire l'aggiornamento all'app Portale aziendale più recente usando [sideload nei dispositivi Zebra](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Passaggi successivi

[Lavagne di discussione Zebra](https://developer.zebra.com/community/home/discussions) (apre il sito Web di zebra)

[Usare e gestire dispositivi Zebra con Mobility Extensions di Zebra in Intune](android-zebra-mx-overview.md)
