---
title: Eseguire la disposizione testo delle app Android con lo strumento per la disposizione testo per app | Microsoft Intune
description: Usare le informazioni in questo argomento per informazioni su come eseguire la disposizione testo per app Android senza modificare il codice dell'app stessa. Preparare le app in modo da applicare i criteri di gestione delle app mobili.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69d8ff8eecd238cfbbf0b01671b80e6ee77ae357
ms.openlocfilehash: c041fbbbec9e1812427d9810489d35480ae8c09b


---

# Preparare le app per Android per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune
Usare lo **strumento di wrapping delle app di Microsoft Intune per Android** per modificare il comportamento delle app Android interne, limitando le funzionalità dell'app senza modificare il codice dell'app stessa.

Lo strumento è un'applicazione della riga di comando di Windows che viene eseguito in PowerShell e crea un 'wrapper' intorno all'app per Android. Dopo l'elaborazione è possibile modificare la funzionalità dell'app usando i [criteri di gestione dell'applicazione per dispositivi mobili](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) configurati.


Prima di eseguire lo strumento, vedere [Considerazioni sulla sicurezza per l'esecuzione dello strumento per la disposizione testo per app](#security-considerations-for-running-the-app-wrapping-tool). Per scaricare lo strumento, vedere la pagina per il download dello [strumento per la disposizione testo per app di Microsoft Intune per Android](https://www.microsoft.com/download/details.aspx?id=47267).

>[!IMPORTANT]
>Questa versione dello strumento di wrapping delle app per Android, che supporta i dispositivi non registrati in Intune Mobile Device Management (MDM), è disponibile in anteprima pubblica. Per partecipare all'anteprima pubblica è possibile scaricare lo strumento da [questo repository GitHub](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview).

>Lo scenario è descritto nell'argomento [Proteggere app e dati line-of-business su dispositivi non registrati](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).


## Passaggio 1: Soddisfare i prerequisiti per l'uso dello strumento per la disposizione testo per app

-   È necessario eseguire l'applicazione di wrapping dello strumento su un computer Windows che eseguono Windows 7 o versioni successive.

-   L'app di input deve essere un pacchetto di applicazione Android valido con estensione **.apk** e:

    -   Non può essere crittografato

    -   Non deve essere incluso nello strumento di wrapping delle app di Intune
    -   Deve essere scritto per Android 4.0 o versione successiva

-   L'applicazione deve sviluppata da o per l'azienda. Non è possibile usare questo strumento su app scaricate da Google Play Store.

-   Per eseguire lo strumento per la disposizione testo per app, è necessario installare la versione più recente di [Java Runtime Environment](http://java.com/download/) e quindi assicurarsi che la variabile del percorso Java sia stata impostata su **C:\ProgramData\Oracle\Java\javapath** nelle variabili di ambiente Windows. Per altre informazioni vedere la [documentazione Java](http://java.com/download/help/).

    > [!NOTE]
    > In alcuni casi, la versione a 32 bit di Java può causare problemi di memoria. Si consiglia di installare la versione a 64 bit.

- Android richiede che tutti i pacchetti dell'app (.apks) siano provvisti di firma. Java Key Tool consente di generare le credenziali necessarie per firmare l'app di output con wrapper. Ad esempio il comando che segue usa il file eseguibile Java **keytool.exe** per generare chiavi usabili dallo strumento di wrapping delle app per firmare l'app di output con wrapper.

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    Questo esempio genera una coppia di chiavi (una chiave pubblica e una chiave privata associata di 2048 bit) mediante l'algoritmo RSA, quindi esegue il wrapping della chiave pubblica in un certificato autofirmato X.509 v3 che viene archiviato come catena di certificati a elemento singolo. Questa catena di certificati e la chiave privata vengono archiviati in una nuova voce keystore denominata "mykeystorefile" e identificata dall'alias "mykeyalias". La voce keystore è valida per 50.000 giorni.

    Il comando richiederà l'immissione di password per il keystore e la chiave. Usare password sicure e complesse, prestando attenzione a non dimenticarle perché saranno necessarie in un secondo momento per eseguire lo strumento di wrapping delle app.

    Per informazioni dettagliate vedere gli argomenti relativi a [keytool](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) e [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) di Java nel sito della documentazione Oracle.

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

3.  Eseguire lo strumento usando il comando **invoke-AppWrappingTool** che ha la sintassi seguente:
    ```
    Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
    -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
    ```

 La tabella che segue descrive le proprietà del comando **invoke-AppWrappingTool**:

|Proprietà|Informazioni|Esempio|
|-------------|--------------------|---------|
|**-InputPath**&lt;Stringa&gt;|Percorso dell'app Android di origine (.apk).| |
|**-OutputPath**&lt;Stringa&gt;|Percorso dell'app Android di "output". Se il percorso della directory è uguale a quello per InputPath, il pacchetto non riuscirà.| |
|**-KeyStorePath**&lt;Stringa&gt;|Percorso al file keystore che contiene la coppia di chiavi pubblica/privata per la firma.|Per impostazione predefinita i keystore vengono archiviati in "C:\Programmi (x86)\Java\jreX.X.X_XX\bin". |
|**-KeyStorePassword**&lt;StringaSicura&gt;|Password usata per decrittografare il file keystore. Android richiede che tutti i pacchetti applicazioni (con estensione apk) siano firmati. Usare Java Key Tool per generare KeyStorePassword. Altre informazioni sul keystore Java sono disponibili [qui](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html).| |
|**-KeyAlias**&lt;Stringa&gt;|Nome della chiave da usare per la firma.| |
|**-KeyPassword**&lt;StringaSicura&gt;|Password usata per decrittografare la chiave privata da usare per la firma.| |
|**-SigAlg**&lt;StringaSicura&gt;| (Facoltativo) Nome dell'algoritmo di firma da usare per la firma. L'algoritmo deve essere compatibile con la chiave privata.|Esempi: SHA256withRSA, SHA1withRSA e MD5withRSA|
| **&lt;Parametri comuni&gt;** | (Facoltativo) Il comando supporta parametri PowerShell comuni, ad esempio verbose, debug e così via. |


- Per un elenco di parametri comuni, vedere il [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx).

- Per visualizzare informazioni dettagliate sull'uso dello strumento, immettere il seguente comando:

    ```
    Help Invoke-AppWrappingTool
    ```

**Esempio:**

Importare il modulo PowerShell.
```
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1" 
```
Eseguire lo strumento di wrapping delle app **HelloWorld.apk**. 
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Sarà quindi richiesta la **KeyStorePassword** e la **KeyPassword**. Immettere le credenziali usate per creare il file keystore.

L'applicazione sottoposta a wrapping viene generata e salvata, insieme a un file di registro nel percorso di output specificato.

## Considerazioni sulla sicurezza per l'esecuzione dello strumento per la disposizione testo per app
Per evitare potenziali attacchi di spoofing, divulgazione di informazioni e l'elevazione dei privilegi:

-   Assicurarsi che l'applicazione line-of-business (LOB) di input, l'applicazione di output e Java KeyStore siano nello stesso computer Windows in cui è in esecuzione lo strumento di wrapping delle app.

-   Importare l'applicazione di output alla console di Intune, nello stesso computer in cui è in esecuzione lo strumento. Per altre informazioni su Java Key Tool, vedere lo [strumento per la generazione di chiavi](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html).

-   Se l'applicazione di output e lo strumento si trovano in un percorso UNC Universal Naming Convention () e non si esegue lo strumento e il file di input nello stesso computer, configurare l'ambiente per essere protetti utilizzando [Internet Protocol Security (IPsec)](http://en.wikipedia.org/wiki/IPsec) o [firma Server Message Block (SMB)](https://support.microsoft.com/en-us/kb/887429).

-   Assicurarsi che l'applicazione provenga da una fonte attendibile.

-   Proteggere la directory di output che contiene l'applicazione sottoposta a wrapping. È possibile utilizzare una directory a livello di utente per l'output.



### Vedere anche
- [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Usare l'SDK per abilitare le app per la gestione delle applicazioni per dispositivi mobili](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Sep16_HO4-->


