---
title: Registra utilizzo StageNow nei dispositivi Android le in Microsoft Intune - Azure | Microsoft Docs
description: Vedere i problemi comuni e soluzioni quando si usa StageNow nei dispositivi Android con Microsoft Intune. Anche informazioni su come ottenere i log e visualizzare esempi di come leggere i log operazioni riuscite e gli errori.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490542"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Risolvere i problemi e visualizzati i potenziali problemi di dispositivi Android le in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In Microsoft Intune, è possibile usare [le mobilità delle estensioni (MX) per gestire i dispositivi Android le](android-zebra-mx-overview.md). Quando si usano dispositivi zebrato, creare i profili in StageNow per gestire le impostazioni e caricarli in Intune. Intune Usa l'app StageNow per applicare le impostazioni nei dispositivi. L'app StageNow crea anche un file di log dettagliato nel dispositivo usato per risolvere i problemi.

Questa funzionalità si applica a:

- Android

Ad esempio, creare un profilo in StageNow per configurare un dispositivo. Quando si crea il profilo StageNow, l'ultimo passaggio genera un file per testare il profilo. È possibile usare questo file con l'app StageNow nel dispositivo.

In un altro esempio, si crea un profilo in StageNow ed eseguirne il test. In Intune, aggiungere il profilo StageNow e quindi assegnarlo ai dispositivi Zebra. Quando si archivia lo stato del profilo assegnato, il profilo indichi lo stato generale.

In entrambi i casi, è possibile ottenere altri dettagli dal file di registro StageNow, che viene salvato sul dispositivo ogni volta che si applica un profilo StageNow.

Alcuni problemi non sono correlati al contenuto del profilo StageNow e non vengono riflesse nei log.

Questo articolo illustra come leggere i log StageNow ed elenca alcuni altri potenziali problemi con dispositivi Zebra che potrebbero non essere disponibili nei log.

[Usare e gestire i dispositivi Zebra con le estensioni di mobilità](android-zebra-mx-overview.md) contiene altre informazioni su questa funzionalità.

## <a name="get-the-logs"></a>Ottenere i log

### <a name="use-the-stagenow-app-on-the-device"></a>Usare l'app StageNow sul dispositivo
Quando si testa un profilo direttamente in StageNow nel computer, anziché usare [Intune per distribuire il profilo](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), l'app StageNow sul dispositivo salva i log del test. Per ottenere il file di log, usare il **ulteriori (...)**  opzione nell'app StageNow sul dispositivo.

### <a name="get-logs-using-android-debug-bridge"></a>Ottenere i log tramite Bridge Debug Android
Per ottenere i log dopo che il profilo è già stato distribuito con Intune, connettere il dispositivo in un computer con [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) (apre i siti web di Android).

Nel dispositivo, i log vengono salvati in `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Ottenere i log di posta elettronica
Per ottenere i log dopo che il profilo è già stato distribuito con Intune, gli utenti finali tramite posta elettronica per i log usando un'app di posta elettronica nel dispositivo. Nel dispositivo zebrato, aprire l'app portale aziendale, e [inviare i log](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). Uso della funzionalità di trasmissione dei log crea anche un PowerLift agli eventi imprevisti ID, che è possibile fare riferimento a se il tentativo di contattare il supporto tecnico Microsoft.

## <a name="read-the-logs"></a>Leggere i log

Quando si esaminano i log, si verifica un errore ogni volta che viene visualizzato il `<characteristic-error>` tag. I dettagli dell'errore vengono scritti i `<parm-error>` tag > `desc` proprietà.

## <a name="error-types"></a>Tipi di errore

I dispositivi ZEBRA comprendono errori diversi livelli di creazione rapporti:

- Il provider CSP non è supportato nel dispositivo. Ad esempio, il dispositivo non è un dispositivo di rete e non dispone di un gestore di rete cellulare.
- Il record MX o OSX versione corrispondente. Viene applicato ogni CSP. Per una matrice di supporto completo, vedere [documentazione del Zebra](http://techdocs.zebra.com/mx/) (si apre in sito web delle).
- Il dispositivo segnala un altro problema o errore.

## <a name="examples"></a>Esempi

Ad esempio, hai il profilo di input seguente:

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

Nel log, il codice XML è identico all'input. Questo output corrispondenza indica che il profilo è stato applicato al dispositivo senza errori:

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

In un altro esempio, è necessario l'input seguente:

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

Il log viene visualizzato un errore, perché contiene un `<characteristic-error>` tag. In questo scenario, il profilo ha tentato di installare un pacchetto Android (APK) che non esiste nel percorso specificato:

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

## <a name="other-potential-issues-with-zebra-devices"></a>Altri potenziali problemi con dispositivi zebrato

Questa sezione sono elencati altri possibili problemi che riscontrabili quando si usano dispositivi Zebra con amministratore del dispositivo. Questi problemi non vengono segnalati nei log StageNow.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView non è aggiornato

Quando i dispositivi meno recenti accedere usando l'app portale aziendale, utenti potrebbero visualizzare un messaggio che il componente di System WebView non è aggiornato e deve aggiornato. Se il dispositivo è installato Google Play, connetterla a internet e verifica degli aggiornamenti disponibili. Se il dispositivo non ha installato Google Play, ottenere la versione aggiornata del componente e applicarlo ai dispositivi. In alternativa, aggiornare il dispositivo più recente del sistema operativo vystavitel Zebra.

### <a name="management-actions-take-a-long-time"></a>Le operazioni di gestione richiedono molto tempo

Se Google Play services non sono disponibili, alcune attività necessarie fino a 8 ore per terminare. [L'app portale aziendale di limitazioni di Intune per Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (si apre un altro sito web Microsoft) può essere un'ottima risorsa.

### <a name="device-spoofing-suspected-shows-in-intune"></a>"Dispositivo lo spoofing degli indirizzi sospetta" viene visualizzato in Intune

Questo errore indica che Intune sospetta che un dispositivo non - le Android segnala il modello e produttore come dispositivo Zebra.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>L'app portale aziendale è meno recente versione minima richiesta

Intune può aggiornare la versione minima richiesta dell'app portale aziendale. Se Google Play non è installato nel dispositivo, l'app portale aziendale non viene aggiornata automaticamente. Se la versione minima richiesta è più recente della versione installata, l'app portale aziendale smette di funzionare. Aggiornamento per l'app portale aziendale più recenti usando [sideload nei dispositivi Zebra](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Passaggi successivi

[Aree discussioni ZEBRA](https://developer.zebra.com/community/home/discussions) (si apre in sito web delle)

[Usare e gestire i dispositivi Zebra con le estensioni di mobilità in Intune](android-zebra-mx-overview.md)
