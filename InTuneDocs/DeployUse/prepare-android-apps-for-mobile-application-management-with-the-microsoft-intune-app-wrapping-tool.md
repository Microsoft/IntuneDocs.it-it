---
title: Eseguire la disposizione testo delle app Android con lo strumento per la disposizione testo per app | Microsoft Intune
description: Usare le informazioni in questo argomento per informazioni su come eseguire la disposizione testo per app Android senza modificare il codice dell'app stessa. Preparare le app in modo da applicare i criteri di gestione delle app mobili.
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 07/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: matgates
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c72c8e1a764af73ba4d421ca6637ee91ab7bca0a
ms.openlocfilehash: 76ee04237d54b4c171df74e8c134f003bbc32966


---

# Preparare le app per Android per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune
Usare lo **strumento per la disposizione testo per app di Microsoft Intune per Android** per modificare il comportamento delle app per Android interne in modo da configurare le funzionalità dell'app senza modificare il codice dell'app stessa.

Lo strumento è un'applicazione della riga di comando di Windows che viene eseguito in PowerShell e crea un 'wrapper' intorno all'app. Dopo l'elaborazione è possibile modificare la funzionalità dell'app usando i [criteri di gestione dell'applicazione per dispositivi mobili](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) configurati.

Se l'app sta usando Azure Active Directory Authentication Library (ADAL), è necessario completare i passaggi in [Come eseguire la disposizione testo per app che usano Azure Active Directory Library](#how-to-wrap-apps-that-use-the-azure-active-directory-library) prima di eseguire la disposizione testo per l'app. Se non si è sicuri se l'app usa questa libreria, contattare lo sviluppatore dell'app.

Prima di eseguire lo strumento, vedere [Considerazioni sulla sicurezza per l'esecuzione dello strumento per la disposizione testo per app](#security-considerations-for-running-the-app-wrapping-tool). Per scaricare lo strumento, vedere la pagina per il download dello [strumento per la disposizione testo per app di Microsoft Intune per Android](https://www.microsoft.com/download/details.aspx?id=47267).

## Passaggio 1: Soddisfare i prerequisiti per l'uso dello strumento per la disposizione testo per app

-   È necessario eseguire l'applicazione di wrapping dello strumento su un computer Windows che eseguono Windows 7 o versioni successive.

-   L'applicazione di input deve essere un pacchetto di applicazione di Android valido **con estensione apk** file e:

    -   Non può essere crittografato

    -   No deve essere inclusa nell’utensile dell’applicazione di wrapping

    -   Deve essere scritto per Android 4.0 o versione successiva

-   L'applicazione deve sviluppata da o per l'azienda. È possibile utilizzare questo strumento per elaborare applicazioni scaricate dall'archivio Google Play.

-   Per eseguire lo strumento per la disposizione testo per app, è necessario installare la versione più recente di [Java Runtime Environment](http://java.com/download/) e quindi assicurarsi che la variabile del percorso Java sia stata impostata su **C:\ProgramData\Oracle\Java\javapath** nelle variabili di ambiente Windows. Per ulteriori informazioni, vedere la [documentazione Java](http://java.com/download/help/).

    > [!NOTE]
    > In alcuni casi, la versione a 32 bit di Java può causare problemi di memoria. Si consiglia di installare la versione a 64 bit.

## Passaggio 2: Installare lo strumento per la disposizione testo per app

1.  Da Microsoft Download Center, scaricare e aprire il file di installazione per lo strumento di ritorno a capo app a un computer Windows.

2.  Accettare il contratto di licenza, quindi completare l'installazione.

Prendere nota della cartella in cui è installato lo strumento. La posizione predefinita è **C:\Programmi (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**.

## Passaggio 3: Eseguire lo strumento per la disposizione testo per app

1.  Nel computer Windows in cui è stato installato lo strumento per la disposizione testo per app, aprire una finestra di PowerShell in modalità amministratore.

2.  Dalla cartella in cui è installato lo strumento, importare l'applicazione esegue il wrapping modulo PowerShell dello strumento:

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Eseguire lo strumento usando il comando **invoke-AppWrappingTool** insieme ai parametri seguenti. I parametri contrassegnati come "facoltativi" sono per le app che usano Azure Active Directory Library (ADAL). Per altre informazioni, vedere [Come eseguire la disposizione testo per app che usano Azure Active Directory Library](#how-to-wrap-apps-that-use-the-azure-active-directory-library).

|Parametro|Altre informazioni|Esempi|
|-------------|--------------------|---------|
|**-InputPath**&lt;Stringa&gt;|Percorso dell'app Android di origine (.apk).| |
|**-OutputPath**&lt;Stringa&gt;|Percorso dell'app Android di "output". Se il percorso della directory è uguale a quello per InputPath, il pacchetto non riuscirà.| |
|**-KeyStorePath**&lt;Stringa&gt;|Percorso al file keystore che contiene la coppia di chiavi pubblica/privata per la firma.| |
|**-KeyStorePassword**&lt;StringaSicura&gt;|Password usata per decrittografare il file keystore. Android richiede che tutti i pacchetti applicazioni (con estensione apk) siano firmati. Usare Java Key Tool per generare KeyStorePassword, come illustrato nell'esempio. Altre informazioni sull'[archivio chiavi](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html).|keytool.exe -genkey -v -keystore keystorefile -alias ks -keyalg RSA -keysize 2048 -validity 50000 |
|**-KeyAlias**&lt;Stringa&gt;|Nome della chiave da usare per la firma.| |
|**-KeyPassword**&lt;StringaSicura&gt;|Password usata per decrittografare la chiave privata da usare per la firma.| |
|**-SigAlg**&lt;StringaSicura&gt;|Nome dell'algoritmo di firma da usare per la firma. L'algoritmo deve essere compatibile con la chiave privata.|Esempi: SHA256withRSA, SHA1withRSA e MD5withRSA|
|**-ClientID**&lt;GUID&gt;|ID client di Azure Active Directory dell'app di input (facoltativo).| |
|**-AuthorityURI**&lt;URI&gt;|URI dell'autorità di Azure Active Directory dell'app di input (facoltativo).| |
|**-SkipBroker**&lt;ValoreBooleano&gt;|Indica se l'applicazione di input supporta Single Sign-On negoziato a livello di dispositivo (facoltativo). |**True** l'applicazione di input non supporta Single Sign-On negoziato a livello di dispositivo. Usare il parametro NonBrokerRedirectURI. **False**: l'applicazione di input supporta Single Sign-On negoziato a livello di dispositivo.|
|**-NonBrokerRedirectURI**&lt;URI&gt;|URI di reindirizzamento di Azure Active Directory da usare se SkipBroker è true (facoltativo).|  |


**&lt;CommonParameters&gt;**
 (facoltativo: supporta parametri PowerShell comuni, ad esempio verbose, debug e così via)

- Per un elenco di parametri comuni, vedere il [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx).

- Per visualizzare la Guida per lo strumento, immettere il comando:

    ```
    Help Invoke-AppWrappingTool
    ```
- Per altre informazioni sull'integrazione di Azure Active Directory (AAD), vedere [Come eseguire la disposizione testo per app che usano Azure Active Directory Library](#how-to-wrap-apps-that-use-the-azure-active-directory-library).

**Esempio:**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app.wrapped\HelloWorld_wrapped2.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\keystorefile" -keyAlias ks -SigAlg SHA1withRSA -Verbose

Sarà quindi richiesta la **KeyStorePassword** e la **KeyPassword**.

L'applicazione sottoposta a wrapping viene generata e salvata, insieme a un file di registro nel percorso di output specificato.

## Considerazioni sulla sicurezza per l'esecuzione dello strumento per la disposizione testo per app
Per evitare potenziali attacchi di spoofing, divulgazione di informazioni e l'elevazione dei privilegi:

-   Assicurarsi che l'applicazione line-of-business, applicazione di output e Java KeyStore siano nello stesso computer in cui è in esecuzione lo strumento di ritorno a capo app.

-   Importare l'applicazione di output nella console di Intune nello stesso computer in cui è in esecuzione lo strumento. Per altre informazioni su Java Key Tool, vedere lo [strumento per la generazione di chiavi](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html).

-   Se l'applicazione di output e lo strumento si trovano in un percorso UNC Universal Naming Convention () e non si esegue lo strumento e il file di input nello stesso computer, configurare l'ambiente per essere protetti utilizzando [Internet Protocol Security (IPsec)](http://en.wikipedia.org/wiki/IPsec) o [firma Server Message Block (SMB)](https://support.microsoft.com/en-us/kb/887429).

-   Assicurarsi che l'applicazione proviene da una fonte attendibile, soprattutto se si utilizza Azure Active Directory (ad), consentendo all'applicazione di accedere il token AAD durante il runtime.

-   Proteggere la directory di output che contiene l'applicazione sottoposta a wrapping. È possibile utilizzare una directory a livello di utente per l'output.

## Come eseguire la disposizione testo per app che usano Azure Active Directory Library
Se l'app usa Azure Active Directory Authentication Library (ADAL), è necessario completare questi passaggi per poter eseguire il wrapping dell'app.

### Passaggio 1: Verificare che i requisiti per ADAL siano soddisfatti
Per le app che usano ADAL, devono verificarsi le condizioni seguenti:

-   L'app deve includere una versione di ADAL maggiore o uguale a 1.0.2.

-   Lo sviluppatore deve concedere all'app l'accesso alla risorsa di gestione delle applicazioni per dispositivi mobili di Intune, come descritto in [Passaggio 3: Configurare l'accesso alla gestione delle applicazioni per dispositivi mobili in AAD](#step-3-configure-access-to-mobile-app-management-in-aad).

### Passaggio 2: Esaminare gli identificatori necessari per la registrazione dell'app
Nel passaggio successivo viene usato il portale di gestione di Azure per registrare le app che usano ADAL con Azure Active Directory (AAD) per ottenere gli identificatori univoci elencati nella tabella seguente. Questi identificatori vengono quindi forniti allo sviluppatore quando si integra ADAL con l'app.

|Identificatore|Altre informazioni|Valore predefinito|
|--------------|--------------------|-----------------|
|**ID client**|Identificatore GUID univoco generato per l'app dopo la registrazione con AAD.<br /><br />Se si conosce l'ID client dell'app, specificarne il valore. In caso contrario, usare il valore predefinito.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**URI dell'autorità**|Valore dell'URI (Uniform Resource Identifier) dell'autorità per oggetti AAD (ad esempio, utenti e gruppi).<br /><br />Il parametro AuthorityURI è facoltativo per lo strumento di wrapping dell'app. Se non si usa il parametro, viene usato l'URI predefinito.||
|**SkipBroker**|Valore che indica se il Portale aziendale verrà usato come broker.<br /><br />**True**: il portale aziendale non verrà usato per l'autenticazione ADAL.<br /><br />**False**: il portale aziendale verrà usato per l'autenticazione ADAL. Il Portale aziendale sta usando l'utente registrato per Single Sign On.||
|**URI di reindirizzamento non broker**|URI di accesso da usare quando ADAL non usa l'app del broker (Portale aziendale di Intune).|urn:ietf:wg:oauth:2.0:oob|
|**ID risorsa**|Puntatore alle risorse AAD dell'app.||

### Passaggio 3: Configurare l'accesso alla gestione delle app per dispositivi mobili in AAD
Prima di usare i valori di registrazione AAD di un'app nello strumento per la disposizione testo per app, lo sviluppatore deve concedere all'app l'accesso alla risorsa di gestione delle applicazioni per dispositivi mobili di Intune usando questa procedura:

1.  Accedere a un account AAD esistente nel portale di gestione di Azure.

2.  Scegliere la **registrazione dell'applicazione line-of-business esistente**.

3.  Nella sezione **Configura** scegliere **Configura l'accesso ad API Web di altre applicazioni**.

4.  Dal primo elenco a discesa nella sezione delle **autorizzazioni per altre applicazioni** scegliere **Gestione di applicazioni mobili di Intune**.

Ora è possibile usare l'ID client dell'app nello strumento di wrapping dell'app. L'ID client è disponibile nel portale di gestione di Azure Active Directory, come descritto nella tabella in [Passaggio 2: Esaminare gli identificatori necessari per la registrazione dell'app](#step-2-review-the-identifiers-you-need-to-get-when-you-register-the-app).

### Passaggio 4: Usare i valori dell'identificatore AAD nello strumento per la disposizione testo per app
Usando i valori dell'identificatore ottenuti nel processo di registrazione, immettere i valori come proprietà della riga di comando nello strumento di wrapping dell'app. È necessario specificare tutti i valori nella tabella affinché gli utenti finali possano eseguire l'autenticazione dell'app. Se non si specifica alcun valore, vengono usati i valori predefiniti.

|Identificatore|Parametro|
|--------------|-------------|
|ID client|ClientID|
|URI dell'autorità|Authority-URI|
|SkipBroker|SkipBroker|
|URI di reindirizzamento non broker|NonBrokerRedirectURI|
|ID risorsa|ResourceID|
Tenere presente quanto segue quando si esegue il wrapping dell'app:

-   Per verificare la corretta esecuzione dell'autenticazione, [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] recupera il token AAD associato a resource-id di MAM. Tuttavia, il token non viene usato nelle chiamate eseguite a loro volta per verificare la validità del token. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] legge solo il nome dell'entità utente dell'utente connesso per determinare l'accesso all'app. Il token AAD non viene usato per altre chiamate dei servizi.

-   Se si forniscono l'ID client e l'URI dell'autorità dell'applicazione client, si evitano richieste di accesso doppie. È necessario registrare l'ID client per abilitarlo all'accesso all'ID risorsa MAM di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] pubblicato nel dashboard AAD. Se non si registra l'ID client, gli utenti ricevono un errore di accesso quando viene eseguita l'app.


### Vedere anche
- [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Usare l'SDK per abilitare le app per la gestione delle applicazioni per dispositivi mobili](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Jul16_HO3-->


