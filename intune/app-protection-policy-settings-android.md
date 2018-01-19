---
title: Impostazioni dei criteri di protezione delle app per Android
titlesuffix: Azure portal
description: Questo argomento descrive le impostazioni dei criteri di protezione delle app per dispositivi Android."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 01/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6be20f8297db39da8d96ab152b632c4258d91a39
ms.sourcegitcommit: 0795870bfe941612259ebec0fe313a783a44d9b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="android-app-protection-policy-settings"></a>Impostazioni dei criteri di protezione delle app per Android
Le impostazioni dei criteri descritte in questo argomento possono essere [configurate](app-protection-policies.md) per il criterio di protezione delle app nel pannello **Impostazioni** del portale di Azure.
Ci sono due categorie di impostazioni dei criteri: impostazioni di rilocazione dei dati e impostazioni di accesso. In questo argomento il termine *app gestite da criteri* si riferisce alle app configurate con criteri di protezione delle app.

##  <a name="data-relocation-settings"></a>Impostazioni di rilocazione dei dati

| Impostazione | Uso | Valori predefiniti |
|------|------|------|
| **Impedisci backup in Android** | Scegliere **Sì** per impedire all'app di eseguire il backup di dati aziendali o dell'istituto di istruzione nel [servizio di backup Android](https://developer.android.com/google/backup/index.html). Scegliere **No** per consentire all'app di eseguire il backup di dati aziendali o dell'istituto di istruzione.| Sì |
| **Consenti all'app di trasferire i dati ad altre app** | Specificare le app da cui questa app può ricevere dati: <ul><li> **App gestite da criteri**: consente il trasferimento solo ad altre app gestite da criteri.</li> <li>**Tutte le app**: consente il trasferimento a qualsiasi app. </li> <li>**Nessuna**: non consente il trasferimento a nessuna app, incluse le altre app gestite da criteri.</li></ul> <p>Esistono alcuni servizi e app esenti ai quali Intune può consentire il trasferimento dei dati. Vedere [Esenzioni per il trasferimento dei dati](#Data-transfer-exemptions) per un elenco completo di app e servizi.<p>**Nota:** Intune attualmente non supporta la funzionalità Android Instant Apps. Intune blocca qualsiasi connessione dati da o verso l'app.  Per altre informazioni su [Android Instant Apps](https://developer.android.com/topic/instant-apps/index.html) vedere la documentazione per sviluppatori di Android.</p>| Tutte le app |
| **Consenti all'app di ricevere i dati da altre app** | Specificare le app che possono trasferire dati a questa app: <ul><li>**App gestite da criteri**: consente il trasferimento solo da altre app gestite da criteri.</li><li>**Tutte le app**: consente il trasferimento dei dati da qualsiasi app.</li><li>**Nessuna**: non consente il trasferimento da alcuna app, incluse le altre app gestite da criteri. </li></ul> <p>Esistono alcuni servizi e app esenti, dai quali Intune può consentire il trasferimento dei dati. Vedere [Esenzioni per il trasferimento dei dati](#Data-transfer-exemptions) per un elenco completo di app e servizi. | Tutte le app |
| **Impedisci "Salva con nome"** | Scegliere **Sì** per disabilitare l'uso dell'opzione Salva con nome in questa app. Scegliere **No** per consentire l'uso di Salva con nome. <p><br>**Selezionare i servizi di archiviazione in cui è possibile salvare i dati aziendali** <br>Gli utenti possono salvare nei servizi selezionati (OneDrive for Business, SharePoint e archiviazione locale). Tutti gli altri servizi verranno bloccati.</p> | No <br><br> 0 selezionato |
| **Limita le operazioni taglia, copia e incolla con le altre app** | Specificare quando è possibile usare le azioni taglia, copia e incolla con questa app. È possibile scegliere tra: <ul><li>**Bloccato**: non consente le azioni taglia, copia e incolla tra questa app e altre app.</li><li>**App gestite da criteri**: consente le azioni taglia, copia e incolla tra questa app e altre app gestite da criteri.</li><li>**App gestite da criteri con Incolla in**: consente le azioni taglia o copia tra questa app e altre app gestite da criteri. I dati da qualsiasi app possono essere incollati in questa app.</li><li>**Qualsiasi app**: nessuna restrizione per le azioni taglia, copia e incolla in e da questa app. | Qualsiasi app |
|**Limita il contenuto Web per la visualizzazione in Managed Browser** | Scegliere **Sì** per imporre l'apertura dei collegamenti Web nell'app con l'app Managed Browser. <br><br> Per i dispositivi non registrati in Intune, i collegamenti Web nelle app gestite da criteri possono essere aperti solo nell'app Managed Browser. <br><br> Se si usa Intune per gestire i dispositivi, vedere [Gestire l'accesso a Internet usando criteri di browser gestiti con Microsoft Intune](app-configuration-managed-browser.md). | No |
| **Crittografa dati app** | Scegliere **Sì** per abilitare la crittografia dei dati aziendali o dell'istituto di istruzione in questa app. Intune usa uno schema di crittografia OpenSSL AES a 128 bit insieme al sistema di archivio chiavi Android per crittografare i dati dell'app in modo sicuro. I dati vengono crittografati in modo sincrono durante le operazioni di I/O dei file. Il contenuto nella memoria del dispositivo è sempre crittografato. <br><br> Il metodo di crittografia **non** è certificato FIPS 140-2.  | Sì |
| **Disabilita la crittografia delle app quando è abilitata la crittografia del dispositivo** | Scegliere **Sì** per disabilitare la crittografia delle app per le risorse di archiviazione delle app interne quando la crittografia dei dispositivi viene rilevata in un dispositivo registrato. <br><br>**Nota:** Intune può rilevare solo la registrazione del dispositivo con MDM Intune. Le risorse di archiviazione delle app esterne saranno tuttavia crittografate perché i dati non siano accessibili da applicazioni non gestite. | Sì |
| **Disabilita sincronizzazione contatti** | Scegliere **Sì** per impedire all'app di salvare dati nell'app Contatti nativa nel dispositivo. Se si sceglie **No**, l'app può salvare dati nell'app Contatti nativa nel dispositivo. <br><br>Quando si esegue una cancellazione selettiva per rimuovere dati aziendali o dell'istituto di istruzione dall'app, i contatti sincronizzati direttamente dall'app nell'app Contatti nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook. | No |
| **Disabilita stampa** | Scegliere **Sì** per impedire all'app di stampare dati aziendali o dell'istituto di istruzione. | No |

  >[!NOTE]
  >Il metodo di crittografia per l'impostazione **Crittografa dati app** **non** è certificato FIPS 140-2.

  ## <a name="data-transfer-exemptions"></a>Esenzioni per il trasferimento dei dati

  Esistono alcune app e servizi della piattaforma esenti, per i quali i criteri di protezione delle app di Intune possono consentire il trasferimento dei dati in entrambe le direzioni. Ad esempio, tutte le app abilitate per Intune in Android devono essere in grado di trasferire i dati a e da Google Text-to-Speech, in modo da consentire la lettura a voce alta del testo dallo schermo del dispositivo mobile. Questo elenco è soggetto a modifiche e include le app e i servizi considerati utili per una produttività sicura.

  ### <a name="full-exemptions"></a>Esenzioni complete

  Queste app e servizi dispongono di autorizzazioni complete per il trasferimento di dati a e da app gestite da Intune.

  |Nome app/servizio | Descrizione |
  | ------ | ---- |
  | com.android.phone | App nativa del telefono
  | com.android.vending | Google Play Store |
  | com.android.documentsui | Selettore documenti Android|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html), necessario per molte app tra cui Outlook. |
  | com.android.webview |[Webview](https://developer.android.com/reference/android/webkit/WebView.html), necessario per molte app tra cui Outlook.|
  | com.google.android.tts | Sintesi vocale di Google |
  | com.android.providers.settings | Impostazioni di sistema Android |
  | com.azure.authenticator | App Azure Authenticator, necessaria per il completamento dell'autenticazione in molte configurazioni. |
  | com.microsoft.windowsintune.companyportal | Intune Portale aziendale|

  ### <a name="conditional-exemptions"></a>Esenzioni condizionali
  Queste app e servizi sono autorizzati al trasferimento di dati a e da app gestite da Intune solo se si verificano determinate condizioni.

  |Nome app/servizio | Descrizione | Condizione per l'esenzione|
  | ------ | ---- | --- |
  | com.Android.Chrome | Browser Google Chrome | Chrome viene usato per alcuni componenti WebView in Android 7.0 e versioni successive e non viene mai nascosto. Tuttavia il flusso di dati a e dall'app è sempre soggetto a restrizioni.
  | com.skype.raider | Skype | L'app Skype è consentita solo per determinate azioni che generano una chiamata telefonica. |
  | com.android.providers.media | Provider di contenuti multimediali Android | Il provider di contenuti multimediali è consentito solo per l'azione di selezione della suoneria. |
  | com.google.android.gms; com.google.android.gsf | Pacchetti di Google Play Services | Questi pacchetti sono consentiti per le azioni di Google Cloud Messaging, ad esempio per le notifiche push. |



##  <a name="access-settings"></a>Impostazioni di accesso

| Impostazione | Uso | Valori predefiniti |
|------|------|------|
| **Richiedi PIN per l'accesso** | Scegliere **Sì** per richiedere un PIN per usare questa app. All'utente viene richiesto di impostare questo PIN alla prima esecuzione dell'app in un contesto aziendale o dell'istituto di istruzione. Valore predefinito = **Sì**.<br><br> Configurare le impostazioni seguenti per la complessità del PIN: <ul><li>**Numero di tentativi prima della reimpostazione del PIN**: specifica il numero di tentativi di immissione del PIN che è possibile eseguire prima che all'utente venga richiesto di reimpostare il PIN. Valore predefinito = **5**.</li><li> **Consenti PIN semplice**: scegliere **Sì** per consentire agli utenti di usare sequenze PIN semplici, come 1234 o 1111. Scegliere **No** per impedire l'uso di sequenze semplici. Valore predefinito = **Sì**. </li><li> **Lunghezza PIN**: specificare il numero minimo di cifre in una sequenza di PIN. Valore predefinito = **4**. <br><br> Il formato di questa impostazione dei criteri supporta un numero intero positivo.</li><li> **Consenti impronta digitale anziché PIN (Android 6.0+)**: scegliere **Sì** per consentire all'utente di usare l'[autenticazione con impronta digitale](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) invece di un PIN per accedere all'app. Valore predefinito = **Sì**.</li></ul> Nei dispositivi Android è possibile consentire all'utente di confermare l'identità usando l'[autenticazione con impronta digitale Android](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) invece di un PIN. Quando l'utente prova a usare l'app usando il proprio account aziendale o dell'istituto di istruzione, gli viene richiesto di identificarsi con l'impronta digitale invece che immettendo un PIN. </li></ul>| Richiedi PIN: sì <br><br> Tentativi prima della reimpostazione del PIN: 5 <br><br> Consenti PIN semplice: sì <br><br> Lunghezza PIN: 4 <br><br> Consenti impronta digitale: sì |
| **Richiedi credenziali aziendali per l'accesso** | Scegliere **Sì** per richiedere all'utente di accedere con il proprio account aziendale o dell'istituto di istruzione anziché immettere un PIN per accedere all'app. Se questa opzione è impostata su **Sì**, ha la priorità sulle richieste di PIN o ID tocco.  | No |
| **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted** |Scegliere **Sì** per impedire l'esecuzione dell'app nei dispositivi jailbroken o rooted. L'utente potrà comunque usare le app per le attività personali, ma dovrà usare un dispositivo diverso per accedere ai dati aziendali o dell'istituto di istruzione nell'app. | Sì |
| **Controlla di nuovo i requisiti di accesso dopo (minuti)** | Configurare le seguenti impostazioni: <ul><li>**Timeout**: numero di minuti che devono trascorrere prima che vengano ricontrollati i requisiti di accesso definiti in precedenza nei criteri. Ad esempio, se l'amministratore attiva il PIN nei criteri, l'utente deve immettere il PIN quando apre un'app abilitata per Intune. Se si usa questa impostazione, l'utente non dovrà immettere il PIN per le app abilitate per Intune per altri **30 minuti** (valore predefinito). <br><br> **Nota:** in Android il PIN è condiviso tra tutte le app abilitate per Intune. Il timer del PIN viene reimpostato quando l'app non è più in primo piano nel dispositivo. Per tutta la durata del timeout definito in questa impostazione, l'utente non dovrà immettere il PIN per le app abilitate per Intune che condividono il PIN stesso. <br><br> Il formato di questa impostazione dei criteri supporta un numero intero positivo.<br></li><li>**Periodo di prova offline**: numero di minuti per cui è consentita l'esecuzione di app MAM offline. Specificare il periodo (in minuti) prima che vengano ricontrollati i requisiti di accesso per l'app. Valore predefinito: **720** minuti (12 ore). Alla scadenza di questo periodo, l'app richiederà l'autenticazione utente per AAD per poter continuare l'esecuzione.<br><br> Il formato di questa impostazione dei criteri supporta un numero intero positivo.</li></ul>| Timeout: 30 <br><br> Offline: 720 |
| **Intervallo offline (giorni) prima della cancellazione dei dati dell'app** | Trascorso questo intervallo di esecuzione offline (numero di giorni definito dall'amministratore), l'app chiederà all'utente di connettersi alla rete e ripetere l'autenticazione. Se l'utente viene autenticato correttamente, può continuare ad accedere ai dati e l'intervallo offline viene reimpostato.  Se l'autenticazione non riesce, l'app eseguirà una cancellazione selettiva dell'account utenti e dei dati.  Vedere [Come cancellare solo i dati aziendali dalle app gestite da Intune](https://docs.microsoft.com/en-us/intune/apps-selective-wipe) per altre informazioni sui dati che vengono rimossi con una cancellazione selettiva.<br><br> Il formato di questa impostazione dei criteri supporta un numero intero positivo. | 90 giorni |
| **Blocca acquisizione schermo e Assistente per Android (Android 6.0+)** | Scegliere **Sì** per bloccare le funzionalità di acquisizione schermo e **Assistente per Android** del dispositivo quando si usa questa app. Se si sceglie **Sì** verrà anche sfocata l'immagine di anteprima della funzione Switch quando si usa questa app con un account aziendale o dell'istituto di istruzione. | No |
| **Disabilita il PIN dell'app quando il PIN del dispositivo è gestito** | Scegliere **Sì** per disabilitare il PIN dell'app quando viene rilevato un blocco del dispositivo in un dispositivo registrato. | No |
| **Require minimum Android operating system** (Richiedi un sistema operativo Android minimo) | Scegliere **Sì** per richiedere un sistema operativo Android minimo per usare l'app. All'utente verrà impedito l'accesso se la versione di Android nel dispositivo non soddisfa il requisito.<br><br> Il formato di questa impostazione dei criteri supporta principale.secondaria, principale.secondaria.build, principale.secondaria.build.revisione.| No |
| **Require minimum Android operating system (Warning only)** (Richiedi un sistema operativo Android minimo (solo avviso)) | Scegliere **Sì** per richiedere un sistema operativo Android minimo per usare l'app. L'utente visualizzerà una notifica se la versione di Android nel dispositivo non soddisfa il requisito. Questa notifica può essere chiusa.<br><br> Il formato di questa impostazione dei criteri supporta principale.secondaria, principale.secondaria.build, principale.secondaria.build.revisione. | No |
| **Richiedi una versione minima dell'app** | Scegliere **Sì** per richiedere una versione minima dell'app per usare l'app. All'utente verrà impedito l'accesso se la versione dell'app nel dispositivo non soddisfa il requisito.<br><br>Poiché spesso gli schemi di numerazione delle versioni sono diversi per le varie app, creare un criterio con una versione minima di un'app come destinazione (ad esempio, "Criteri versione Outlook"). <br><br> Il formato di questa impostazione dei criteri supporta principale.secondaria, principale.secondaria.build, principale.secondaria.build.revisione.| No | 
| **Richiedi una versione minima dell'app (solo avviso)** | Scegliere **Sì** per consigliare una versione minima dell'app per usare questa app. L'utente visualizzerà una notifica se la versione dell'app nel dispositivo non soddisfa il requisito. Questa notifica può essere chiusa.<br><br>Poiché spesso gli schemi di numerazione delle versioni sono diversi per le varie app, creare un criterio con una versione minima di un'app come destinazione (ad esempio, "Criteri versione Outlook"). <br><br> Il formato di questa impostazione dei criteri supporta principale.secondaria, principale.secondaria.build, principale.secondaria.build.revisione.| No | 
| **Require Minimum Android Patch Version** (Richiedi una versione minima della patch di Android) | Scegliere **Sì** per richiedere una versione minima della patch di protezione di Android rilasciata da Google. All'utente verrà impedito l'accesso se la patch di protezione di Android nel dispositivo non soddisfa il requisito.<br><br> Il formato di questa impostazione dei criteri supporta il formato di data AAAA-MM-GG. | No |
| **Require Minimum Android Patch Version (Warning Only)** (Richiedi una versione minima della patch Android (solo avviso)) | Scegliere **Sì** per richiedere una versione minima della patch di protezione di Android rilasciata da Google. L'utente visualizzerà una notifica se la patch di protezione di Android nel dispositivo non soddisfa il requisito. Questa notifica può essere chiusa.<br><br> Il formato di questa impostazione dei criteri supporta il formato di data AAAA-MM-GG. | No |
