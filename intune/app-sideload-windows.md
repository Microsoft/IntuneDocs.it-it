---
title: Trasferire localmente app per Windows e Windows Phone per Intune
description: Informazioni su come firmare le app line-of-business in modo da poter usare Intune per distribuirle.
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
ms.custom: intune-classic
ms.openlocfilehash: 06922f76643a6b95e994bf4e219ee3a4a85953c5
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Firmare le app line-of-business per poterle distribuire nei dispositivi Windows con Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

L'amministratore di Intune ha la possibilità di distribuire app line-of-business (LOB) in dispositivi Windows e Windows 10 Mobile, inclusa l'app Portale aziendale. Per distribuire app con estensione appx o xap nei dispositivi Windows 10 e Windows 10 Mobile oppure per distribuire qualsiasi app LOB in dispositivi Windows 8.1 o Windows Phone 8.1, è necessario ottenere un **certificato di firma codice mobile aziendale Symantec**. Solo il certificato Symantec è considerato trusted per queste app per i rispettivi dispositivi Windows. È possibile usare un'Autorità di certificazione propria per le app di Windows 10 e le app universali. Questo certificato è necessario al fine di:

-   Firmare l'app Portale aziendale per la distribuzione in PC Windows, dispositivi Windows 10 Mobile e dispositivi Windows Phone

-   Firmare applicazioni line-of-business dell'azienda così che Intune possa distribuirle in dispositivi Windows

La procedura seguente consente di ottenere il certificato necessario e di firmare le app. Sarà necessario registrarsi come sviluppatore Microsoft e quindi acquistare un certificato Symantec.


1. **Registrarsi come sviluppatore Microsoft**<br>
   [Registrarsi come sviluppatore Microsoft](http://go.microsoft.com/fwlink/?LinkId=268442) usando le informazioni sull'account aziendale usate al momento dell'accesso per l'acquisto dell'account aziendale. La richiesta di certificato di firma codice deve essere preventivamente autorizzata da un responsabile dell'azienda.

2. **Ottenere un certificato aziendale Symantec.**<br>
  Acquistare un certificato dal [sito Web Symantec](http://go.microsoft.com/fwlink/?LinkId=268441) utilizzando l’ID Symantec. Dopo aver acquistato il certificato, il responsabile aziendale dell'approvazione designato al momento della registrazione come sviluppatore Microsoft riceverà un messaggio di posta elettronica per approvare la richiesta del certificato. Per altre informazioni sui requisiti del certificato Symantec, vedere l'articolo relativo ai [motivi per i quali Windows Phone richiede un certificato Symantec](https://technet.microsoft.com/library/dn764959.aspx#BKMK_Symantec). Domande frequenti sulla registrazione dei dispositivi Windows.

3.  **Importare certificati**<br>
    Dopo che la richiesta è stata approvata, si riceve un messaggio di posta elettronica contenente le istruzioni per l'importazione dei certificati. Seguire le istruzioni nel messaggio di posta elettronica per importare i certificati.

4.  **Verificare i certificati importati**<br>
    Per verificare che i certificati siano stati importati correttamente, andare nello snap-in **Certificati**, fare clic con il pulsante destro del mouse su **Certificati** e selezionare **Trova certificati**. Nel campo **Contiene** immettere "Symantec", quindi fare clic su **Trova ora**. I certificati importati dovrebbero essere visualizzati nei risultati.

    ![Trovare il certificato Symantec](./media/wit.gif)

5. **Esportare un certificato di firma**<br>
    Dopo aver verificato che i certificati siano presenti, è possibile esportare il file con estensione pfx per firmare il portale aziendale. Selezionare il certificato Symantec con la "firma del codice" **Scopo designato** . Fare clic con il pulsante destro del mouse sul certificato della firma del codice e selezionare **Esporta**.

    ![Esportare il certificato per la firma](./media/wit-walk-cert2.gif)

    In **Esportazione guidata certificati**selezionare **Sì, esporta la chiave privata** e fare clic su **Avanti**. **Selezionare Scambio informazioni personali - PKCS #12 (.PFX)** e selezionare **Se possibile, includi tutti i certificati per percorso certificazione**. Completare la procedura guidata. Per altre informazioni, vedere la sezione [Esportare un certificato con la chiave privata](http://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Caricare l'app in Intune**<br>
    Caricare il file dell'app firmato e il certificato di firma del codice per rendere l'app disponibile agli utenti finali.

    1.  Nel portale di Azure fare clic su **Amministrazione** &gt; **Windows Phone**.

    2.  Fare clic su **Carica file app firmato** e accedere con l'ID amministratore di Intune.

    3.  Aggiungere il file di certificato (estensione pfx) esportato in **Certificato di firma codice** e creare una password per il certificato.

    4.  Completare la procedura guidata.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Esempio: scaricare, firmare e distribuire l'app Portale aziendale per dispositivi Windows

È possibile distribuire l'app Portale aziendale in dispositivi Windows, inclusi dispositivi Windows Phone e Windows 10 Mobile, con Intune invece di eseguire l'installazione da Microsoft Store. È necessario scaricare l'app Portale aziendale e firmarla con il certificato.  Questa operazione è necessaria solo se gli utenti non utilizzano lo Store aziendale e si desidera distribuire Portale aziendale nei dispositivi Windows Phone 8.1.


1.  **Scaricare Portale aziendale**

    Per distribuire l'app Portale aziendale con Intune, è possibile scaricare l'[app Portale aziendale di Microsoft Intune per Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) dall'Area download ed eseguire il file autoestraente (estensione exe). Questo file contiene due file:

    -   CompanyPortal.appx: app di installazione di Portale aziendale per Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1: uno script di PowerShell che è possibile usare per firmare il file dell’app Portale aziendale in modo che possa essere distribuita ai dispositivi Windows Phone 8.1

    In alternativa, è possibile scaricare l'app Portale aziendale di Windows Phone 8.1 (pacchetto con licenza offline) o Portale aziendale di Windows 10 (pacchetto con licenza offline) da [Microsoft Store per le aziende](http://businessstore.microsoft.com/). L'app Portale aziendale dovrà essere acquisita con una licenza offline e il pacchetto appropriato dovrà essere scaricato per l'uso offline. Le voci per la piattaforma Windows 8 e Windows Phone 8 nella selezione fanno riferimento alle controparti 8.1. Per informazioni dettagliate su come eseguire questa operazione con Intune, vedere [Manage apps you purchased from the Microsoft Store for Business](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune) (Gestire le app acquistate in Microsoft Store per le aziende).

2.  **Scaricare Windows Phone SDK** Scaricare Windows Phone 8.0 SDK (http://go.microsoft.com/fwlink/?LinkId=615570) e installare l'SDK nel computer. Questo SDK è necessario per generare un token di registrazione applicazione.

3.  **Generare un file AETX** Generare un file token di registrazione dell'applicazione con estensione aetx dal file PFX Symantec usando AETGenerator.exe, incluso nel Windows Phone 8.0 SDK. Per istruzioni su come creare un file AETX, vedere [Come generare un token di registrazione dell’applicazione per Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)

4.  **Scaricare il Windows SDK per Windows 8.1** Scaricare e installare il [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525). Si noti che lo script di PowerShell incluso con l'app Portale aziendale usa il percorso di installazione predefinito, `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Se si esegue l’installazione in un altro percorso, è necessario includere il percorso in un parametro del cmdlet.

5.  **Firmare il codice dell'app con PowerShell** Come amministratore, aprire **Windows PowerShell** sul computer host installato con il Windows SDK, il certificato di firma codice mobile aziendale Symantec, accedere al file Sign-WinPhoneCompanyPortal.ps1 ed eseguire lo script.

    **Esempio 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    In questo esempio viene firmato il file CompanyPortal.appx in C:\temp\ e viene prodotto il file CompanyPortalEnterpriseSigned.appx. Viene utilizzata la password PFX 1234 e l'ID dell'editore viene letto dal file PFX. Viene anche letto l’ID aziendale dal file cert.aetx.

    **Esempio 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    In questo esempio viene firmato il file CompanyPortal.appx in C:\temp\ e viene prodotto il file CompanyPortalEnterpriseSigned.appx. Viene utilizzata la password PFX 1234 e l'ID dell'editore specificato.

    **Parametri:**

    -   `-InputAppx` : il percorso locale del file CompanyPortal.appx tra virgolette singole. Ad esempio 'C:\temp\CompanyPortal.appx'

    -   `-OutputAppx` : il percorso locale e il nome file per l’app Portale aziendale firmata tra virgolette singole. Ad esempio 'C:\temp\CompanyPortalEnterpriseSigned.appx'

    -   `-PfxFilePath` : il percorso locale e il nome file per il file PFX esportato del certificato di Symantec. Ad esempio, 'C:\signing\cert.pfx'

    -   `-PfxPassword` : la password usata per firmare il file PFX tra virgolette singole. Ad esempio  '1234'

    -   `-AetxPath` : il percorso locale del file con estensione aetx usato per leggere l'ID aziendale, se l'argomento 'EnterpriseId' non è definito. È necessario specificare questo argomento oppure EnterpriseId. Ad esempio, 'C:\signing\cert.pfx'

    -   `-PublisherId`: l'ID autore dell'azienda. Se assente, viene usato il campo 'Subject' del certificato di firma codice mobile aziendale Symantec . Ad esempio, 'OID.0.9.2342.19200300.100.1.1=1000000001, CN = "Test, Inc.", OU = Test 1'

    -   `-SdkPath`: il percorso della cartella radice di Windows SDK per Windows 8.1. Questo argomento è facoltativo e l’impostazione predefinita è ${env:ProgramFiles(x86)} \Windows Kits\8.1.

    -   `-EnterpriseId`: l'ID azienda. È necessario specificare questo argomento oppure 'AetxPath'. Se questo argomento non viene specificato, l'ID azienda viene letto dal file AETX. Ad esempio, 1000000001.

6.  Distribuire l’app Portale aziendale di Windows Phone 8.1 (SSP.appx). Per istruzioni, vedere [Come aggiungere app line-of-business (LOB) per Windows Phone](lob-apps-windows-phone.md) ([portale classico](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Come rinnovare il certificato di firma codice aziendale Symantec

Il certificato Symantec usato per distribuire le app per dispositivi mobili Windows e Windows Phone deve essere rinnovato periodicamente.

1.  Attendere il messaggio di posta elettronica di rinnovo inviato da Symantec circa 14 giorni prima della scadenza del certificato. Questo messaggio di posta elettronica contiene le indicazioni di Symantec per il rinnovo del certificato aziendale.

    Per altre informazioni sui certificati Symantec, visitare [www.symantec.com](http://www.symantec.com) o chiamare il numero 1-877-438-8776 o 1-650-426-3400.

2.  Visitare il sito Web (ad esempio: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) e accedere con l’ID dell’editore Symantec e l’indirizzo di posta elettronica associato al certificato. Ricordare di usare lo stesso computer in cui sarà scaricato il certificato per avviare il rinnovo.

3.  Una volta approvato e pagato il rinnovo, scaricare il certificato.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Come installare il certificato aggiornato per le app line-of-business (LOB)

1.  Firmare la versione più recente dell'app line-of-business.

2.  Aprire il portale di Azure, passare ad **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows Phone** e fare clic su **Carica app firmata**.

3.  Caricare il portale aziendale appena firmato. Saranno necessari il file SSP.xap appena firmato e il nuovo file PFX ricevuto da Symantec oppure il token di registrazione dell'applicazione creato con questo nuovo file PFX.

4.  Una volta completato il caricamento, rimuovere la versione precedente di Portale aziendale attraverso l’area di lavoro **Software**  .

5.  Firmare tutte le app line-of-business aziendali nuove e aggiornate usando il nuovo certificato. Le applicazioni esistenti non devono essere firmate e distribuite di nuovo.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Distribuire manualmente l'app Portale aziendale di Windows 10
È possibile distribuire manualmente l'app Portale aziendale di Windows 10 direttamente da Intune, anche se non si è integrato Intune con Microsoft Store per le aziende.

 > [!NOTE]
 > Se si sceglie questa opzione, sarà necessario distribuire manualmente gli aggiornamenti ogni volta che verrà rilasciato un aggiornamento dell'app.

1. Accedere al proprio account di [Microsoft Store per le aziende](https://www.microsoft.com/business-store) e acquisire la versione con **licenza offline** dell'app Portale aziendale.  
2. Dopo aver acquisito l'app, selezionarla nella pagina **Inventario**.  
3. Selezionare **Windows 10 all devices** (Windows 10 - tutti i dispositivi) come **Piattaforma**, quindi specificare l'opzione di **Architettura** appropriata ed eseguire il download. Per questa app non è necessario un file di licenza di app.
![Immagine dei dettagli del pacchetto per Windows 10 (tutti i dispositivi) e l'architettura X86](./media/Win10CP-all-devices.png)
4. Scaricare tutti i pacchetti inclusi in "Framework richiesti". Questa operazione deve essere eseguita per le architetture x86, x64 e ARM, per un totale di 9 pacchetti, come illustrato di seguito.

![Immagine dei file di dipendenza da scaricare ](./media/Win10CP-dependent-files.png)
5. Prima di caricare l'app Portale aziendale in Intune, creare una cartella (ad esempio, C:&#92;Company Portal) con i pacchetti strutturati nel modo seguente:
  1. Inserire il pacchetto dell'app Portale aziendale in C:\Company Portal. Creare anche una sottocartella Dependencies in questa posizione.  
  ![Immagine della cartella Dependencies salvata con il file APPXBUN](./media/Win10CP-Dependencies-save.png)
  2. Inserire i nove pacchetti delle dipendenze nella cartella Dependencies.  
  Se le dipendenze non vengono inserite in questo formato, Intune non sarà in grado di riconoscerle e caricarle durante il caricamento del pacchetto. Pertanto questa operazione avrà esito negativo e restituirà l'errore seguente.  
  ![Nella cartella dell'applicazione non è presente la dipendenza delle app Windows per questo programma di installazione software. È possibile continuare a creare e a distribuire questa applicazione senza che sia possibile eseguirla fino a quando la dipendenza delle app Windows mancante non verrà fornita.](./media/Win10CP-error-message.png)
6. Tornare a Intune e caricare l'app Portale aziendale come una nuova app. Distribuirla come app necessaria al gruppo di utenti di destinazione desiderato.  

Per altre informazioni sul modo in cui Intune gestisce le dipendenze per le app universali, vedere [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Distribuzione di un appxbundle con dipendenze tramite MDM di Microsoft Intune).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Come aggiornare l'app Portale aziendale sui dispositivi degli utenti se hanno già installato le app precedenti dallo Store?
Se gli utenti hanno già installato le app Portale aziendale di Windows 8.1 o Windows Phone 8.1 dallo Store, queste dovrebbero essere aggiornate automaticamente alla nuova versione senza alcun intervento da parte dell'amministratore o dell'utente. Se l'aggiornamento non viene eseguito, chiedere agli utenti di controllare se hanno abilitato gli aggiornamenti automatici per le app dello Store sui dispositivi.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 trasferita localmente all'app Portale aziendale di Windows 10?
Il percorso di migrazione consigliato consiste nell'eliminare la distribuzione dell'app Portale aziendale di Windows 8.1 impostando l'azione di distribuzione su "Disinstalla". Al termine di questa operazione, l'app Portale aziendale di Windows 10 può essere distribuita usando una delle opzioni precedenti.  

Se è necessario trasferire localmente l'app e si è distribuita l'app Portale aziendale di Windows 8.1 senza firmarla con il certificato Symantec, per completare l'aggiornamento seguire i passaggi riportati nella sezione relativa alla distribuzione diretta tramite Intune.

Se è necessario trasferire localmente l'app e si è firmata e distribuita l'app Portale aziendale di Windows 8.1 con il certificato di firma codice Symantec, seguire i passaggi illustrati nella sezione seguente.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Come aggiornare l'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 firmata e trasferita localmente all'app Portale aziendale di Windows 10?
Il percorso di migrazione consigliato consiste nell'eliminare la distribuzione esistente dell'app Portale aziendale di Windows 8.1 o Windows Phone 8.1 impostando l'azione di distribuzione su "Disinstalla". Al termine di questa operazione, l'app Portale aziendale di Windows 10 può essere distribuita normalmente.  

In caso contrario, è necessario aggiornare e firmare l'app Portale aziendale di Windows 10 per assicurarsi che il percorso di aggiornamento venga rispettato.  

Se l'app Portale aziendale di Windows 10 viene firmata e distribuita in questo modo, sarà necessario ripetere questa procedura per ogni nuovo aggiornamento dell'app disponibile nello Store. L'app non verrà aggiornata automaticamente in caso di aggiornamento dello Store.  

Ecco come firmare e distribuire l'app in questo modo:

1. Scaricare lo script di firma di Microsoft Intune per l'app Portale aziendale di Windows 10 dall'indirizzo [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Per l'esecuzione di questo script è necessario che sia installato Windows 10 SDK nel computer host. Per scaricare Windows 10 SDK, visitare [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Scaricare l'app Portale aziendale di Windows 10 da Microsoft Store per le aziende, come descritto in precedenza.  
3. Eseguire lo script per firmare l'app Portale aziendale di Windows 10 con i parametri di input riportati nell'intestazione (descritti nella tabella seguente). Non è necessario passare le dipendenze allo script. Le dipendenze sono necessarie solo quando l'app viene caricata nella console di amministrazione di Intune.

|Parametro | Descrizione|
| ------------- | ------------- |
|InputWin10AppxBundle |Percorso in cui si trova il file appxbundle di origine. |
|OutputWin10AppxBundle |Percorso di output per il file appxbundle firmato. |
|Win81Appx | Percorso in cui si trova il file (con estensione appx) dell'app Portale aziendale per Windows 8.1 o Windows Phone 8.1.|
|PfxFilePath |Percorso del file (con estensione pfx) del certificato di firma codice di Symantec Enterprise Mobile. |
|PfxPassword| Password del certificato di firma codice di Symantec Enterprise Mobile. |
|PublisherId |ID editore dell'azienda. Se assente, viene usato il campo 'Subject' del certificato di firma codice mobile aziendale Symantec .|
|SdkPath | Percorso della cartella radice di Windows 10 SDK. Questo argomento è facoltativo e l'impostazione predefinita è ${env:ProgramFiles(x86)}\Windows Kits\10.|
Al termine dell'esecuzione, lo script genererà la versione firmata dell'app Portale aziendale di Windows 10. Sarà quindi possibile distribuire la versione firmata dell'app come app line-of-business tramite Intune, in modo da aggiornare le versioni attualmente distribuite alla nuova app.  
