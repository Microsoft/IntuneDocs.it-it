---
# required metadata

title: Aggiungere app | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Aggiungere app con Microsoft Intune
Prima di iniziare la distribuzione di app con Microsoft Intune, prendersi il tempo necessario per acquisire familiarità con i concetti introdotti in questo argomento. Queste considerazioni consentono di comprendere quali app è possibile distribuire in quale piattaforma e i prerequisiti da rispettare prima di procedere.

## Tipi di app che è possibile distribuire con Intune
È possibile distribuire app in tutti i tipi di dispositivi supportati da Intune. A seconda del tipo di app da distribuire, il processo e i dispositivi supportati variano. Usare le informazioni seguenti per comprendere che cosa è possibile distribuire.


### **Windows Installer (&#42;.exe, &#42;.msi)**
- Questo tipo di app deve supportare l'installazione invisibile all'utente senza input dell'utente. La documentazione dell'app deve includere le opzioni della riga di comando rilevanti per l'installazione automatica dell'app, ad esempio, **/q**. È disponibile [qui](https://support.microsoft.com/en-us/kb/227091) un elenco di opzioni della riga di comando comuni.
- Le cartelle e i file aggiuntivi richiesti dal programma di installazione dell'app devono essere disponibili nel percorso specificato per i file di installazione dell'app.
- Nella maggior parte dei casi, i file di Windows Installer (.msi) e Windows Installer Patch (.msp) non richiedono alcun argomento della riga di comando per essere installati da Intune. Verificare la documentazione dell'app. Se sono necessari argomenti di riga di comando, essi devono essere inseriti come coppia Nome=Valore (ad esempio TRANSFORMS=custom_transform.mst).

Questo tipo di app viene caricato nello spazio di memorizzazione cloud.
### **Pacchetto app per Android (file &#42;.apk)**
Questo tipo di app viene caricato nello spazio di memorizzazione cloud.
### **Pacchetto app per iOS (file &#42;.ipa)**
- Per distribuire le app per iOS, è necessario un pacchetto con estensione ipa valido.
- Il pacchetto con estensione ipa deve essere stato firmato da Apple e la data di scadenza indicata nel profilo di provisioning deve essere valida. Intune è in grado di distribuire applicazioni iOS con certificato aziendale. Non tutte le app Apple con certificato di sviluppatore sono supportate.
- L'azienda deve essere registrata al programma iOS Developer Enterprise Program.
- Assicurarsi che il firewall dell'organizzazione consenta l'accesso ai siti Web di provisioning e certificazione iOS.
- Non è necessario distribuire un file manifesto (con estensione plist) con l'app.

Questo tipo di app viene caricato nello spazio di memorizzazione cloud.

Attualmente gli utenti finali non possono installare applicazioni aziendali direttamente dall'app Portale aziendale di Intune per iOS. Si tratta di restrizioni per le applicazioni che vengono pubblicate in App Store iOS (vedere [linee guida di revisione di App Store](https://developer.apple.com/app-store/review/guidelines/)). Gli utenti possono accedere alle app aziendali, incluse le app gestite di App Store e i pacchetti dell'app line-of-business, avviando l'app Portale aziendale sul dispositivo e toccando il riquadro App aziendali. In questo modo si apre il browser e gli utenti vengono reindirizzati al portale Web Intune.

### **Pacchetto app Windows Phone (&#42;.xap, .appx, .appxbundle)**
- Per distribuire le app serve un certificato di firma codice mobile aziendale. Per altre informazioni vedere [Set up Windows Phone management with Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) (Configurare la gestione dei dispositivi Windows Phone con Microsoft Intune).

Questo tipo di app viene caricato nello spazio di memorizzazione cloud.

Per informazioni sull'installazione di app line-of-business della piattaforma UWP (Universal Windows Platform) con Intune, vedere di seguito.

### **Pacchetto app Windows (.appx, .appxbundle)**
- Per distribuire le app serve un certificato di firma codice mobile aziendale. Per altre informazioni vedere [Set up Windows device management with Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md) (Configurare la gestione dei dispositivi Windows con Microsoft Intune).

Questo tipo di app viene caricato nello spazio di memorizzazione cloud.
### **Windows Installer tramite MDM (&#42;.msi)**
Questo tipo di programma di installazione consente di creare e distribuire le app basate su Windows Installer nei PC registrati che eseguono Windows 10.<br /><br />Quando si usa questo tipo di programma di installazione, considerare gli aspetti seguenti:
- È possibile caricare solo un singolo file con estensione msi.
- Per il rilevamento delle app vengono usati il codice e la versione prodotto del file.
- Verrà usato il comportamento di riavvio predefinito dell'app. Intune non controlla questo comportamento.
- I pacchetti MSI per utente vengono installati per un singolo utente.
- I pacchetti MSI per computer vengono installati per tutti gli utenti del dispositivo.
- I pacchetti MSI dual mode vengono attualmente installati solo per tutti gli utenti del dispositivo.
- Gli aggiornamenti delle app sono supportati quando il codice prodotto MSI di ogni versione è lo stesso.

Questo tipo di app viene caricato nello spazio di memorizzazione cloud.
### **Collegamento esterno**
Viene usato quando sono disponibili i seguenti elementi:
- **URL** che consente agli utenti di scaricare un'app dall'App Store.
- **Collegamento** a un'app basata sul Web eseguita dal Web browser.

Le app basate su collegamenti esterni non sono archiviate nello spazio di archiviazione nel cloud Intune.
### **App iOS gestita dall'App Store**
Consente di gestire e distribuire app iOS gratuite dall'App Store. Consente inoltre di associare i [criteri di gestione delle applicazioni mobili](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) con [app compatibili](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) e controllarne lo stato nella console di amministrazione.<br /><br />Le app iOS gestite non vengono archiviate nello spazio di memorizzazione cloud di Intune.
> [!TIP] Le opzioni per i dispositivi mobili non sono disponibili finché non si [imposta l'autorità di gestione dei dispositivi mobili](get-ready-to-enroll-devices-in-microsoft-intune.md) in Intune.

## Supporto per app della piattaforma UWP (Universal Windows Platform)
Nei PC Windows 10 non è necessario disporre di una chiave di trasferimento locale per installare le app line-of-business. Tuttavia, la chiave del Registro di sistema **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** deve avere un valore pari a **1** per abilitare il sideload.

Se la chiave del Registro di sistema non è configurata, Intune imposterà automaticamente questo valore su**1** la prima volta che si distribuisce un'app nel dispositivo. Se questo valore è stato impostato su **0**, Intune non può modificare automaticamente il valore e la distribuzione delle app line-of-business avrà esito negativo.

Le app line-of-business della piattaforma UWP devono essere firmate con un certificato di firma codice attendibile su ogni dispositivo in cui l'applicazione viene distribuita. È possibile usare i certificati da un'infrastruttura a chiave pubblica (PKI) interna o un certificato da una radice pubblica di terze parti installato nel dispositivo.

Nei dispositivi Windows 10 Mobile, è possibile usare un certificato di firma codice non Symantec per firmare le app universali con estensione **appx**. Per le app con estensione **xap** e per i pacchetti **appx** compilati per Windows Phone 8.1 che si vuole installare nei dispositivi Windows 10 Mobile, è necessario usare un certificato di firma codice Symantec.

## Passaggi successivi 

In seguito sarà necessario aggiungere le app nella console di Intune prima di distribuirle. È possibile aggiungere app sia per i [dispositivi registrati](add-apps-for-mobile-devices-in-microsoft-intune.md) che per i [PC Windows gestiti con il software client di Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

<!--HONumber=Jun16_HO2-->


