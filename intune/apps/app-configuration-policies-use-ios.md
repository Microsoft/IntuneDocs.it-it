---
title: Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti
titleSuffix: Microsoft Intune
description: Informazioni su come usare i criteri di configurazione delle app per specificare i dati di configurazione per un'app iOS in fase di esecuzione.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6cee01676a98da714d7047e6a45713e8673786ea
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507493"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Usare i criteri di configurazione delle app in Microsoft Intune per specificare impostazioni di configurazione personalizzate per un'app iOS. Queste impostazioni di configurazione consentono di personalizzare un'app in base alle indicazioni del fornitore dell'app stessa. È necessario ottenere queste impostazioni di configurazione (chiavi e valori) dal fornitore dell'app. Per configurare l'app, specificare le impostazioni come chiavi e valori oppure come file XML contenente le chiavi e valori.

L'amministratore di Microsoft Intune può controllare gli account utente che vengono aggiunti alle applicazioni di Microsoft Office nei dispositivi gestiti. Può limitare l'accesso agli account utente consentiti dell'organizzazione e bloccare gli account personali nei dispositivi registrati. Le applicazioni di supporto elaborano la configurazione dell'app e rimuovono e bloccano gli account non approvati. Le impostazioni dei criteri di configurazione vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione.

Dopo aver aggiunto un criterio di configurazione dell'app, è possibile impostare le assegnazioni per i criteri di configurazione dell'app. Quando si impostano le assegnazioni per i criteri, è possibile scegliere di includere ed escludere i gruppi di utenti ai quali vengono applicati i criteri. Quando si sceglie di includere uno o più gruppi, è possibile selezionare i gruppi specifici da includere o selezionare i gruppi predefiniti. I gruppi predefiniti includono **Tutti gli utenti**, **Tutti i dispositivi**, e **Tutti gli utenti + Tutti i dispositivi**. 

> [!NOTE]
> Intune fornisce per praticità i gruppi **Tutti gli utenti** e **Tutti i dispositivi** creati in precedenza nella console con le ottimizzazioni predefinite. È consigliabile usare questi gruppi per scegliere tutti gli utenti e tutti i dispositivi invece dei gruppi 'Tutti gli utenti' o 'Tutti i dispositivi' che potrebbero essere stati creati manualmente.

Dopo aver selezionato i gruppi inclusi per i criteri di configurazione dell'applicazione, è anche possibile scegliere i gruppi specifici da escludere. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Questo tipo di criteri è attualmente disponibile solo per i dispositivi che eseguono iOS 8.0 e versioni successive. Supporta i tipi di installazione di app seguenti:
>
> - **App iOS gestita dall'App Store**
> - **Pacchetto app per iOS**
>
> Per altre informazioni sui tipi di installazione delle app, vedere [How to add an app to Microsoft Intune](apps-add.md) (Come aggiungere un'app a Microsoft Intune). Per altre informazioni sull'incorporamento della configurazione dell'app nel pacchetto dell'app con estensione IPA per i dispositivi gestiti, vedere Managed App Configuration (Configurazione delle app gestite) nella [documentazione per sviluppatori iOS](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html).

## <a name="create-an-app-configuration-policy"></a>Creare criteri di configurazione delle app

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Scegliere il carico di lavoro **App client**.
4. Scegliere **Criteri di configurazione dell'app** nel gruppo **Gestisci** e quindi scegliere **Aggiungi**.
5. Impostare i dettagli seguenti:
    - **Nome** - Nome del profilo che viene visualizzato nel portale di Azure.
    - **Descrizione** - Descrizione del profilo che viene visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo** - Scegliere **Dispositivi gestiti** per i dispositivi che sono stati registrati in Intune.
6. Selezionare **iOS** per **Piattaforma**.
7. Scegliere **App associata**. Nel riquadro **App associata** scegliere l'app gestita alla quale applicare la configurazione e selezionare **OK**.
8. Nel riquadro **Aggiungi i criteri di configurazione** scegliere **Impostazioni di configurazione**.
9. Selezionare **Formato delle impostazioni di configurazione**. Per aggiungere informazioni di configurazione, selezionare uno dei metodi seguenti:
    - **Usare la finestra di progettazione della configurazione**
    - **Immettere i dati XML**<br><br>
    Per informazioni dettagliate sull'uso della finestra di progettazione della configurazione, vedere [Usare Progettazione configurazione](#use-configuration-designer). Per informazioni dettagliate sull'immissione di dati XML, vedere [Immettere i dati XML](#enter-xml-data). 
10. Dopo aver aggiunto le informazioni di configurazione, scegliere **OK** e quindi scegliere **Aggiungi** per aggiungere i criteri di configurazione. Viene visualizzato il riquadro di panoramica dei criteri di configurazione.
11. Selezionare **Assegnazioni** per visualizzare le opzioni di inclusione ed esclusione. 

    ![Screenshot della scheda Includi in Assegnazioni](./media/app-configuration-policies-use-ios/app-config-policy01.png)
12. Selezionare **Tutti gli utenti** nella scheda **Includi**.

    ![Screenshot delle assegnazioni dei criteri - opzione di elenco a discesa Tutti gli utenti](./media/app-configuration-policies-use-ios/app-config-policy02.png)
13. Selezionare la scheda **Escludi**. 
14. Fare clic su **Selezionare i gruppi da escludere** per visualizzare il riquadro correlato.

    ![Screenshot delle assegnazioni dei criteri - Pannello Selezionare i gruppi da escludere](./media/app-configuration-policies-use-ios/app-config-policy03.png)
15. Scegliere i gruppi da escludere e quindi fare clic su **Seleziona**.

    >[!NOTE]
    >Quando si aggiunge un gruppo, se sono già stati inclusi altri gruppi per un tipo di assegnazione specifico, tale gruppo risulterà preselezionato e non potrà essere modificato per gli altri tipi di assegnazione di inclusione. Di conseguenza, tale gruppo non potrà essere usato come gruppo escluso.
16. Fare clic su **Save**.

## <a name="use-configuration-designer"></a>Usare Progettazione configurazione

Microsoft Intune fornisce impostazioni di configurazione univoche per un'app. È possibile usare la finestra di progettazione della configurazione per le app disponibili in dispositivi registrati o non registrati in Microsoft Intune. La finestra di progettazione consente di configurare chiavi e valori di configurazione specifici utili per creare il codice XML sottostante. È anche necessario specificare il tipo di dati per ogni valore. Queste impostazioni vengono fornite automaticamente alle app al momento dell'installazione.

### <a name="add-a-setting"></a>Aggiungere un'impostazione

1. Per ogni chiave e valore nella configurazione, impostare:
   - **Chiave di configurazione** - Chiave che identifica in modo univoco la configurazione specifica delle impostazioni.
   - **Tipo di valore** - Il tipo di dati del valore di configurazione. I tipi includono Integer, Real, String o Boolean.
   - **Valore di configurazione** - Valore per la configurazione.
2. Scegliere **OK** per specificare le impostazioni di configurazione.

### <a name="delete-a-setting"></a>Eliminare un'impostazione

1. Scegliere i puntini di sospensione ( **...** ) accanto all'impostazione.
2. Selezionare **Elimina**.

I caratteri \{\{ e \}\} vengono usati solo dai tipi di token e non devono essere usati per altri scopi.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Consentire solo gli account dell'organizzazione configurati nelle app con identità multiple 

Per i dispositivi iOS, usare le coppie chiave/valore seguenti:

| **Key** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valori** | <ul><li>**Attivata**: l'unico account consentito è l'account utente gestito definito dalla chiave [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).</li><li>**Disabled** (o qualsiasi valore che non corrisponda a **Enabled** senza distinzione di maiuscole/minuscole): è consentito qualsiasi account.</li></ul> |.

   > [!NOTE]
   > Se si consentono solo account dell'organizzazione configurati con identità multiple, è necessario usare OneDrive per iOS 10.34 o versione successiva, Outlook per iOS 2.99.0 o versione successiva o Edge per iOS 44.8.7 o versione successiva e all'app devono essere destinati [criteri di protezione delle app Intune](app-protection-policy.md).

## <a name="enter-xml-data"></a>Immettere i dati XML

È possibile digitare o incollare un elenco di proprietà XML contenente le impostazioni di configurazione dell'app per i dispositivi registrati in Intune. Il formato dell'elenco di proprietà XML varia a seconda dell'app da configurare. Per altre informazioni sul formato esatto da usare, contattare il fornitore dell'app.

Intune convalida il formato XML. Tuttavia Intune non verifica se l'elenco di proprietà XML (PList) funziona con l'app di destinazione.

Per altre informazioni sugli elenchi di proprietà XML:

- Vedere [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Informazioni sugli elenchi di proprietà XML) nella libreria per gli sviluppatori iOS.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Formato di esempio per file XML di configurazione delle app

Quando si crea un file di configurazione di app, è possibile specificare uno o più dei seguenti valori usando questo formato:

```xml
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
</dict>
```

### <a name="supported-xml-plist-data-types"></a>Tipi di dati supportati nell'elenco di proprietà XML

Intune supporta i tipi di dati seguenti in un elenco di proprietà:

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; o &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>Token usati nell'elenco di proprietà

Intune supporta anche i tipi di token seguenti nell'elenco di proprietà:
- \{\{userprincipalname\}\}, ad esempio **John@contoso.com**
- \{\{mail\}\}, ad esempio **John@contoso.com**
- \{\{partialupn\}\}, ad esempio **John**
- \{\{accountid\}\}, ad esempio **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}, ad esempio **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}, ad esempio **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}, ad esempio **John Doe**
- \{\{serialnumber\}\}, ad esempio **F4KN99ZUG5V2** (per dispositivi iOS)
- \{\{serialnumberlast4digits\}\}, ad esempio **G5V2** (per dispositivi iOS)
- \{\{aaddeviceid\}\}, ad esempio, **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>Configurare l'app Portale aziendale per supportare i dispositivi DEP iOS

Le registrazioni DEP (Device Enrollment Program, il programma di registrazione dei dispositivi di Apple) non sono compatibili con la versione di App Store dell'app Portale aziendale. La procedura seguente, tuttavia, consente di configurare l'app Portale aziendale in modo che supporti i dispositivi DEP iOS.

1. In Intune nel portale di Azure:
    - Aggiungere Portale aziendale Intune, se necessario. A tale scopo, passare a **Intune** > **App client** > **App** > **Aggiungi**.
    - Passare ad **App client** > **Criteri di configurazione dell'app** per creare criteri di configurazione per l'app Portale aziendale.
2. Creare criteri di configurazione dell'app con il codice XML che segue. Altre informazioni su come creare criteri di configurazione delle app e immettere dati XML sono disponibili in [Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti](app-configuration-policies-use-ios.md) o, per la gestione dei dispositivi mobili ibrida, in [Applicare le impostazioni alle app iOS con i criteri di configurazione app in System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-ios-apps-with-app-configuration-policies).

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. Distribuire l'app Portale aziendale a dispositivi con criteri di configurazione mirati per i gruppi desiderati. Assicurarsi di distribuire i criteri solo a gruppi di dispositivi già registrati nel programma DEP.
4. Indicare agli utenti finali di accedere all'app Portale aziendale quando viene installata automaticamente.

## <a name="monitor-ios--app-configuration-status-per-device"></a>Monitorare lo stato di configurazione delle app iOS per ogni dispositivo 
Dopo che è stato assegnato un criterio di configurazione, è possibile monitorare lo stato di configurazione delle app iOS per ogni dispositivo gestito. Da **Microsoft Intune** nel portale di Azure selezionare **Dispositivi** > **Tutti i dispositivi**. Dall'elenco dei dispositivi gestiti selezionare un dispositivo specifico per visualizzare il relativo pannello. Nel pannello del dispositivo selezionare **Configurazione dell'app**.  

## <a name="additional-information"></a>Informazioni aggiuntive

- [Distribuzione delle impostazioni di configurazione delle app di Outlook per iOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Passaggi successivi

Procedere con l'[assegnazione](apps-deploy.md) e il [monitoraggio](apps-monitor.md) dell'app.
