---
title: Eseguire il wrapping delle app Android con lo strumento di wrapping delle app | Documentazione Microsoft
description: Usare le informazioni in questo articolo per scoprire come eseguire il wrapping delle app Android senza doverne modificare il codice. Preparare le app in modo da applicare i criteri di gestione delle app mobili.
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a89c2b26daf2b3b4da57e0c190f772e078681bee
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="prepare-android-apps-for-mobile-application-management-with-the-intune-app-wrapping-tool"></a>Preparare le app per Android per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare lo strumento di wrapping delle app di Microsoft Intune per Android per modificare il comportamento delle app Android interne, limitandone le funzionalità senza modificare il codice.

Lo strumento è un'applicazione della riga di comando di Windows che viene eseguito in PowerShell e crea un wrapper intorno all'app Android. Dopo aver eseguito il wrapping dell'app, è possibile modificarne le funzionalità configurando i [criteri di gestione delle app mobili](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) in Intune.


Prima di eseguire lo strumento, vedere [Considerazioni sulla sicurezza per l'esecuzione dello strumento di wrapping delle app](#security-considerations-for-running-the-app-wrapping-tool). Per scaricare lo strumento, visitare la pagina dello [strumento di wrapping delle app di Microsoft Intune per Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) in GitHub.



## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Soddisfare i prerequisiti per l'uso dello strumento di wrapping delle app

-   È necessario eseguire lo strumento di wrapping delle app in un computer Windows che esegue Windows 7 o versioni successive.

-   L'app di input deve essere un pacchetto di applicazione Android valido con estensione apk e:

    -   Non può essere crittografata.
    -   Non può essere stata sottoposta a wrapping in precedenza con lo strumento di wrapping delle app di Intune.
    -   Deve essere scritta per Android 4.0 o versione successiva.

-   L'app deve essere sviluppata da o per l'azienda. Non è possibile usare questo strumento su app scaricate da Google Play Store.

-   Per eseguire lo strumento di wrapping delle app, è necessario installare la versione più recente di [Java Runtime Environment](http://java.com/download/) e quindi assicurarsi che la variabile del percorso Java sia stata impostata su C:\ProgramData\Oracle\Java\javapath nelle variabili di ambiente Windows. Per altre informazioni vedere la [documentazione Java](http://java.com/download/help/).

    > [!NOTE]
    > In alcuni casi, la versione a 32 bit di Java può causare problemi di memoria. È consigliabile installare la versione a 64 bit.

- Android richiede che tutti i pacchetti dell'app (con estensione apk) siano firmati. Lo strumento keytool Java consente di generare le credenziali necessarie per firmare l'app di output di cui è stato eseguito il wrapping. Ad esempio, il comando seguente usa il file eseguibile Java keytool.exe per generare chiavi utilizzabili dallo strumento di wrapping delle app per firmare l'app di output di cui viene eseguito il wrapping.

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    Questo esempio genera una coppia di chiavi (una chiave pubblica e una chiave privata associata di 2.048 bit) con l'algoritmo RSA, quindi esegue il wrapping della chiave pubblica in un certificato autofirmato X.509 v3 che viene archiviato come catena di certificati a elemento singolo. Questa catena di certificati e la chiave privata vengono archiviati in una nuova voce keystore denominata "mykeystorefile" e identificata dall'alias "mykeyalias". La voce keystore è valida per 50.000 giorni.

    Il comando richiederà l'immissione di password per il keystore e la chiave. Usare password sicure, ma prenderne nota perché saranno necessarie per eseguire lo strumento di wrapping delle app.

    Per informazioni dettagliate vedere gli argomenti relativi a [keytool](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) e [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) di Java nel sito della documentazione Oracle.

## <a name="install-the-app-wrapping-tool"></a>Installare lo strumento di wrapping delle app

1.  Dal [repository GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) scaricare il file di installazione InstallAWT.exe dello strumento di wrapping delle app di Intune per Android in un computer Windows. Aprire il file di installazione.

2.  Accettare il contratto di licenza e quindi finire l'installazione.

Prendere nota della cartella in cui è installato lo strumento. La posizione predefinita è C:\Programmi (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>Eseguire lo strumento di wrapping delle app

1.  Nel computer Windows in cui è stato installato lo strumento di wrapping delle app, aprire una finestra di PowerShell in modalità amministratore.

2.  Dalla cartella in cui è installato lo strumento, importare il modulo di PowerShell dello strumento di wrapping delle app:

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
|**-OutputPath**&lt;Stringa&gt;|Percorso dell'app Android di output. Se il percorso della directory è uguale a quello per InputPath, il pacchetto non riuscirà.| |
|**-KeyStorePath**&lt;Stringa&gt;|Percorso del file dell'archivio chiavi che contiene la coppia di chiavi pubblica/privata per la firma.|Per impostazione predefinita i file dell'archivio chiavi vengono archiviati in "C:\Programmi (x86)\Java\jreX.X.X_XX\bin". |
|**-KeyStorePassword**&lt;SecureString&gt;|Password usata per decrittografare il file keystore. Android richiede che tutti i pacchetti di applicazioni (con estensione apk) siano firmati. Usare keytool Java per generare KeyStorePassword. Altre informazioni sulla classe KeyStore Java sono disponibili [qui](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html).| |
|**-KeyAlias**&lt;Stringa&gt;|Nome della chiave da usare per la firma.| |
|**-KeyPassword**&lt;SecureString&gt;|Password usata per decrittografare la chiave privata da usare per la firma.| |
|**-SigAlg**&lt;SecureString&gt;| (Facoltativo) Nome dell'algoritmo di firma da usare per la firma. L'algoritmo deve essere compatibile con la chiave privata.|Esempi: SHA256withRSA, SHA1withRSA e MD5withRSA|
| **&lt;Parametri comuni&gt;** | (Facoltativo) Il comando supporta parametri PowerShell comuni, come verbose e debug. |


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
Eseguire lo strumento di wrapping delle app sull'app nativa HelloWorld.apk.
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Verranno quindi richiesti i valori di **KeyStorePassword** e **KeyPassword**. Immettere le credenziali usate per creare il file keystore.

L'applicazione sottoposta a wrapping e un file di log vengono generati e salvati nel percorso di output specificato.

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Considerazioni sulla sicurezza per l'esecuzione dello strumento di wrapping delle app
Per evitare potenziali attacchi di spoofing, divulgazione di informazioni e l'elevazione dei privilegi:

-   Assicurarsi che l'applicazione line-of-business (LOB) di input, l'applicazione di output e Java KeyStore siano nello stesso computer Windows in cui è in esecuzione lo strumento di wrapping delle app.

-   Importare l'applicazione di output alla console di Intune, nello stesso computer in cui è in esecuzione lo strumento. Per altre informazioni sullo strumento keytool Java, vedere [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html).

-   Se l'applicazione di output e lo strumento si trovano in un percorso UNC (Universal Naming Convention) e non si eseguono lo strumento e il file di input nello stesso computer, configurare l'ambiente per la protezione con [IPSec (Internet Protocol Security)](http://wikipedia.org/wiki/IPsec) o la [firma SMB (Server Message Block)](https://support.microsoft.com/kb/887429).

-   Assicurarsi che l'applicazione provenga da una fonte attendibile.

-   Proteggere la directory di output che contiene l'applicazione di cui è stato eseguito il wrapping. È possibile utilizzare una directory a livello di utente per l'output.

### <a name="see-also"></a>Vedere anche
- [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Usare l'SDK per abilitare le app per la gestione delle applicazioni mobili](use-the-sdk-to-enable-apps-for-mobile-application-management.md)

