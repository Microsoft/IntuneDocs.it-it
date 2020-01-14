---
title: Risolvere i problemi e rivedere i log dei profili dei dispositivi Wi-Fi in Microsoft Intune - Azure | Microsoft Docs
description: Individuare e risolvere i problemi dei profili di configurazione dei dispositivi Wi-Fi nei dispositivi Android, iOS e Windows in Microsoft Intune. Rivedere i log ed esaminare alcuni dei problemi comuni e le risoluzioni possibili.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70f471e7f4db7ddce89d8956474822375c684944
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547969"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Risolvere i problemi dei profili di configurazione dei dispositivi Wi-Fi in Microsoft Intune

In Intune è possibile creare profili di configurazione dei dispositivi che includono le impostazioni di connessione per la rete Wi-Fi. Usare queste impostazioni per connettere i dispositivi Android, iOS e Windows degli utenti alla rete dell'organizzazione.

Questo articolo illustra un profilo Wi-Fi applicato correttamente ai dispositivi. L'articolo include anche informazioni sui log, descrive i problemi comuni e altro ancora. Usare questo articolo per risolvere i problemi relativi ai profili Wi-Fi.

Per altre informazioni sui profili Wi-Fi in Intune, vedere [Aggiungere e usare le impostazioni Wi-Fi nei dispositivi](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Prima di iniziare

Gli esempi in questo articolo usano l'autenticazione del certificato SCEP per i profili di Intune. L'articolo presuppone anche che i profili radice trusted e SCEP funzionino correttamente nel dispositivo.

## <a name="android"></a>Android

In questa sezione viene illustrata l'esperienza dell'utente finale durante l'installazione dei profili di configurazione in un dispositivo Android.

### <a name="end-user-experience-example"></a>Esempio di esperienza dell'utente finale

In questo scenario viene usato un dispositivo Nokia 6.1. Prima di installare il profilo Wi-Fi nel dispositivo, installare i profili radice trusted e SCEP.

1. Gli utenti finali ricevono una notifica in cui viene richiesto di installare il profilo di certificato radice trusted:

    > [!div class="mx-imgBorder"]
    > ![Esempio di notifica dell'app Portale aziendale in Android per l'installazione del profilo di certificato radice trusted](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. La notifica successiva richiede di installare il profilo di certificato SCEP:

    > [!div class="mx-imgBorder"]
    > ![Esempio di notifica dell'app Portale aziendale in Android per l'installazione del profilo di certificato SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > Quando si usa un dispositivo Android gestito da un amministratore del dispositivo, l'elenco potrebbe includere più certificati. Quando un profilo di certificato viene revocato o rimosso, il certificato rimane nel dispositivo. In questo scenario selezionare il certificato più recente. Si tratta in genere dell'ultimo certificato visualizzato nell'elenco.
    >
    > Questa situazione non si verifica nei dispositivi Android Enterprise e Samsung Knox. Per altre informazioni, vedere [Gestire i dispositivi del profilo di lavoro Android](../enrollment/android-enterprise-overview.md) e [Rimuovere i certificati SCEP e PKCS](../protect/remove-certificates.md#android-knox-devices).

3. Successivamente gli utenti ricevono una notifica per l'installazione del profilo Wi-Fi:

    > [!div class="mx-imgBorder"]
    > ![Esempio di notifica dell'app Portale aziendale in Android per l'installazione del profilo di certificato SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. Al termine, la connessione Wi-Fi viene visualizzata come rete salvata:

    > [!div class="mx-imgBorder"]
    > ![Connessione Wi-Fi visualizzata come rete salvata](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>Rivedere i log dell'app Portale aziendale

In Android il file **Omadmlog.log** descrive in dettaglio le attività del profilo Wi-Fi installato nel dispositivo. Possono essere presenti fino a cinque file di log Omadmlog. Assicurarsi di ottenere il timestamp dell'ultima sincronizzazione che consente di individuare le voci di log correlate.

Nell'esempio seguente usare [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) per leggere i log e cercare "wifimgr":

> [!div class="mx-imgBorder"]
> ![Connessione Wi-Fi visualizzata come rete salvata](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

Il log seguente mostra i risultati della ricerca e il profilo Wi-Fi applicato correttamente:

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

Dopo aver installato il profilo Wi-Fi nel dispositivo, il profilo viene visualizzato nel **profilo di gestione**:

> [!div class="mx-imgBorder"]
> ![Profilo di gestione nel dispositivo iOS](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![Connessione Wi-Fi visualizzata come rete Wi-Fi nel dispositivo iOS](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>Rivedere i log della console iOS e del dispositivo

Nei dispositivi iOS il log dell'app Portale aziendale non include informazioni sui profili Wi-Fi. Per visualizzare i dettagli di installazione dei profili Wi-Fi, usare i log della console o del dispositivo:

1. Connettere il dispositivo iOS al computer Mac. Passare a **Applicazioni** > **Utilità** e aprire l'app Console.
2. In **Azione** selezionare **Includi messaggi di informazioni** e **Includi messaggi di debug**:

    > [!div class="mx-imgBorder"]
    > ![Includi messaggi di informazioni e Includi messaggi di debug nell'app Console iOS](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. Riprodurre lo scenario e salvare i log in un file di testo:

    1. Selezionare tutti i messaggi nella schermata corrente: **Modifica** > **Seleziona tutto**.
    2. Copiare i messaggi: **Modifica** > **Copia**.
    3. Incollare i dati di log in un editor di testo e salvare il file.

4. Per visualizzare informazioni dettagliate, cercare il file di log salvato. Quando il profilo viene installato correttamente, l'output ha un aspetto simile al log seguente:

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

Dopo aver installato il profilo Wi-Fi nel dispositivo, passare a **Impostazioni** > **Account** > **Accesso aziendale o dell'istituto di istruzione**. Selezionare l'account > **Informazioni**:

> [!div class="mx-imgBorder"]
> ![Accesso aziendale o dell'istituto di istruzione e selezionare Informazioni nel dispositivo Windows](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

In **Areas managed by Microsoft** (Aree gestite da Microsoft) viene visualizzato **Wi-Fi**:

> [!div class="mx-imgBorder"]
> ![L'elenco delle aree gestite da Microsoft include Wi-Fi in Windows](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Per visualizzare la connessione Wi-Fi, passare a **Impostazioni** > **Rete e Internet**  > **Wi-Fi**:

> [!div class="mx-imgBorder"]
> ![In Windows la connessione Wi-Fi è visualizzata come rete nota nelle impostazioni](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>Rivedere i log del Visualizzatore eventi

Nei dispositivi Windows i dettagli sui profili Wi-Fi vengono registrati nel Visualizzatore eventi:

1. Aprire l'app **Visualizzatore eventi**.
2. Nel menu **Visualizza** selezionare **Visualizza registri analitici e di debug**.
3. Espandere **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Amministrazione**

Viene visualizzato un output simile ai log seguenti:

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>Problemi comuni

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>Problema 1: Il profilo Wi-Fi non è distribuito nel dispositivo

- Verificare che il profilo Wi-Fi sia assegnato al gruppo corretto:

    1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **Dispositivi** > **Profili di configurazione**.
    2. Selezionare il profilo > **Assegnazioni**. Verificare che i gruppi selezionati siano corretti.
    3. In Endpoint Manager selezionare **Risoluzione dei problemi e supporto**. Esaminare le informazioni **Assegnazioni**.

- In Endpoint Manager selezionare **Risoluzione dei problemi e supporto**. Verificare che il dispositivo possa essere sincronizzato con Intune controllando l'orario **Ultima archiviazione**.

- Se il profilo Wi-Fi è collegato a profili radice trusted e SCEP, verificare che entrambi i profili siano distribuiti nel dispositivo. Il profilo Wi-Fi ha una dipendenza in questi profili.

- In Windows 10 e nei dispositivi più recenti rivedere il log delle informazioni di diagnostica MDM:

  1. Passare a **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**.
  2. Selezionare l'aziendale o dell'istituto di istruzione > **Informazioni**.
  3. Nella parte inferiore della pagina **Impostazioni** selezionare **Crea report**.
  4. Viene visualizzata una finestra che mostra il percorso dei file di log. Selezionare **Esporta**.
  5. Passare al percorso `\Users\Public\Documents\MDMDiagnostics` e visualizzare il report:

      > [!div class="mx-imgBorder"]
      > ![Informazioni di diagnostica MDM di esempio che mostrano la configurazione del profilo Wi-Fi nei dispositivi Windows 10](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > Per altre informazioni, vedere [Diagnosticare gli errori di MDM in Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).

- Nei dispositivi Android se i profili radice trusted e SCEP non sono installati nel dispositivo, nel file Omadmlog dell'app Portale aziendale viene visualizzata la voce seguente:

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - Quando i profili radice trusted e SCEP si trovano nel dispositivo Android e sono conformi, il profilo Wi-Fi potrebbe non trovarsi nel dispositivo. Questo problema si verifica quando il provider **CertificateSelector** dall'app Portale aziendale non trova un certificato che corrisponda ai criteri specificati. I criteri specifici possono essere nel modello di certificato o nel profilo SCEP.

    Se il certificato corrispondente non viene trovato, i certificati nel dispositivo non sono installati. Il profilo Wi-Fi non è applicato poiché non ha il certificato corretto. In questo scenario nel file Omadmlog dell'app Portale aziendale viene visualizzata la voce seguente:

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    Il log di esempio seguente mostra i certificati da escludere perché sono stati specificati i criteri di utilizzo chiavi avanzato (EKU) **Qualsiasi scopo**. I certificati assegnati al dispositivo, tuttavia, non hanno quel tipo di criteri EKU:

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    L'esempio seguente mostra il profilo SCEP immesso nei criteri EKU **Qualsiasi scopo**. Tuttavia, il profilo non è specificato nel modello di certificato nell'autorità di certificazione (CA). Per risolvere il problema, aggiungere l'opzione **Qualsiasi scopo** al modello di certificato. In alternativa, rimuovere l'opzione **Qualsiasi scopo** dal profilo SCEP.

    > [!div class="mx-imgBorder"]
    > ![In Android aggiungere Qualsiasi scopo al modello di certificato nell'autorità di certificazione](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![In Android aggiungere Qualsiasi scopo al profilo di configurazione del certificato SCEP in Intune](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - Verificare che tutti i certificati richiesti nella catena di certificati completa si trovino nel dispositivo Android. In caso contrario, il profilo Wi-Fi non può essere installato nel dispositivo. Per altre informazioni, vedere [Autorità di certificazione intermedia mancante](https://developer.android.com/training/articles/security-ssl#MissingCa) (apre il sito Web di Android).
  - Applicare filtri a Omadmlog con parole chiave per cercare le informazioni, ad esempio il certificato usato nel profilo Wi-Fi e l'applicazione corretta del profilo.

    Ad esempio, usare [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) per leggere i log. Usare la stringa di ricerca per filtrare "wifimgr":

    > [!div class="mx-imgBorder"]
    > ![Applicare un filtro a CMTrace per cercare i profili di configurazione WiFiMgr nei dispositivi Android](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    L'output sarà simile al log seguente:

    > [!div class="mx-imgBorder"]
    > ![Esempio di output del log CMTrace che mostra il profilo di configurazione di Intune WiFi applicato correttamente ai dispositivi](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    Se viene visualizzato un errore nel log, copiare il timestamp dell'errore e annullare il filtro applicato al log. Quindi usare l'opzione "Trova" con il timestamp per visualizzare cosa è accaduto immediatamente prima dell'errore.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>Problema 2: Il profilo Wi-Fi è distribuito nel dispositivo ma il dispositivo non è in grado di connettersi alla rete

Questo problema è in genere causato da elementi esterni a Intune. Le attività seguenti possono essere utili per individuare e risolvere i problemi di connettività:

- Connettersi manualmente alla rete usando un certificato con gli stessi criteri presenti nel profilo Wi-Fi.

  Se è possibile connettersi, esaminare le proprietà del certificato nella connessione manuale. Aggiornare quindi il profilo Wi-Fi di Intune con le stesse proprietà del certificato.
- Gli errori di connettività vengono in genere registrati nel log del server RADIUS. Ad esempio, il log dovrebbe indicare se il dispositivo ha provato a connettersi con il profilo Wi-Fi.

## <a name="need-more-help"></a>Servono altre informazioni?

- Usare i [forum degli utenti di Intune](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc) o [ottenere supporto da Microsoft](../fundamentals/get-support.md).

- Per altre informazioni sui profili Wi-Fi in Microsoft Intune, vedere gli articoli seguenti:

  - Aggiungere le impostazioni Wi-Fi per i dispositivi che eseguono [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md) e [Windows 10 e versioni successive](wi-fi-settings-windows.md).
  - [Suggerimento del supporto tecnico: Come configurare NDES per le distribuzioni di certificati SCEP in Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - Risolvere i problemi relativi alla [distribuzione del profilo di certificato SCEP](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) e alla [configurazione di NDES](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune).

- Per le ultime notizie, informazioni e suggerimenti tecnici, vedere i blog ufficiali:
  - [Blog del team di supporto di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Blog di Microsoft Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>Passaggi successivi

[Monitorare i profili](device-profile-monitor.md).
