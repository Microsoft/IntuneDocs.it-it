---
title: Impostare la gestione di Windows Phone 8.0 | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 06/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 61e9b6c3-8795-49b0-8ab2-a9a05ee3ea1f
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eed5855f3e27460146703ddf40fd935229a974e5
ms.openlocfilehash: 02f9b7c7abe2daf942299015bfdfb052755ec2de


---

# Configurare la gestione del dispositivo per Windows Phone 8.0

Windows Phone 8.0 richiede un certificato Symantec per installare l'app Portale aziendale di Intune e per consentire la gestione del dispositivo. È necessario un certificato anche per firmare applicazioni line-of-business. L'argomento seguente si riferisce solo a Windows Phone 8.0. Per gestire i dispositivi Windows Phone 8.1 o versioni successive, compresi i dispositivi Windows 10 Mobile, vedere [Set up Windows Phone and Windows 10 Mobile management with Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) (Impostare la gestione di Windows Phone e Windows 10 Mobile con Microsoft Intune).

> [!IMPORTANT]
> A partire da settembre 2016 l'app Portale aziendale per Windows 8.0 e Windows Phone 8.0 non sarà più disponibile per il download.

-   **Windows Phone 8**: Certificato richiesto
-   **Windows Phone 8.1 e Windows 10 Mobile** richiedono un certificato solo se:

    -   Si desidera distribuire l'app Portale aziendale con Intune

    -   Si intende distribuire applicazioni line-of-business , note anche come app "con sideload"


![Diagramma dei requisiti relativi ai certificati](../media/wpcertreqs.png)

  > [!IMPORTANT]
  > Il certificato Symantec usato per gestire alcuni dispositivi mobili Windows e Windows Phone [deve essere rinnovato periodicamente](renew-a-symantec-code-signing-certificate.md).

I requisiti di installazione per la gestione dei dispositivi mobili Windows Phone variano a seconda della modalità di gestione dei dispositivi.  L'impostazione di due CNAME nella registrazione DNS della società semplifica la registrazione. Se gli utenti devono scaricare l'app Portale aziendale dallo Store, dopo aver configurato le impostazioni DNS è sufficiente impostare Portale aziendale e indicare agli utenti come effettuare la registrazione.  Per Windows Phone 8.0 o Windows Phone 8.1 in cui verrà distribuito il Portale aziendale, è necessario un certificato Symantec per firmare il codice dell'app.

## Configurare i requisiti di installazione per abilitare la gestione di Windows Phone
1.  **Configurare Intune** Se non è ancora stato fatto, preparare la gestione del dispositivo mobile [impostando l'autorità di gestione del dispositivo mobile](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) su **Microsoft Intune** e configurando MDM.

2.  **Impostare un alias DNS per l'indirizzo del server di registrazione** (facoltativo)

    Un Alias DNS (tipo di record CNAME) semplifica agli utenti la registrazione dei dispositivi poiché durante la registrazione il nome del server viene inserito automaticamente.

    1.  Nella [console di amministrazione di Intune](http://manage.microsoft.com) fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows Phone**.

    2.  Digitare l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e fare clic su **Verifica il rilevamento automatico**.

    3.  Creare record di risorse DNS **CNAME** per il dominio aziendale. Il record di risorse CNAME deve contenere le informazioni seguenti:

        |Nome host|Punta a|TTL|
        |-------------|-------------|-------|
        |enterpriseenrollment.company_domain.com|enterpriseenrollment-s.manage.microsoft.com |1 ora|
        |enterpriseregistration.company_domain.com|enterpriseregistration.windows.net|1 ora|
        Ad esempio, se il sito Web della società è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a manage.microsoft.com. Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio.

        -   `enterpriseenrollment-s.manage.microsoft.com` : supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

        -   `enterpriseregistration.windows.net` : supporta l'aggiunta alla rete aziendale per dispositivi mobili. Supporta inoltre l'accesso condizionale per Windows 8.1

    ![Finestra di dialogo Impostazioni di gestione dei dispositivi mobili di Windows Phone](../media/windows-phone-enrollment.png)

3.  **Gestione del certificato per il supporto della firma dell'applicazione** [Richiesta per Windows Phone 8.0 e Windows Phone 8.1 che non accedono a Windows Phone Store o che necessitano di app line-of-business.]

    Per supportare l'app Portale aziendale per Windows Phone 8.0 e distribuire le app aziendali in Windows Phone 8.1 è necessario ottenere un **Certificato di firma codice mobile aziendale di Symantec**. Non è possibile usare un certificato rilasciato dall'autorità di certificazione perché i dispositivi Windows Phone considerano attendibile solo il certificato Symantec. Questo certificato è necessario al fine di:

    -   Firmare l'app Portale aziendale per la distribuzione in [!INCLUDE[winphone8_client_1](../includes/winphone8_client_1_md.md)] per la gestione di registrazione e telefono

    -   Firmare applicazioni line-of-business dell'azienda così che [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] possa distribuirle in Windows Phone

    La procedura seguente consente di ottenere i certificati necessari e firmare l'app Portale aziendale. È necessario disporre di un account Windows Phone Dev Center e acquistare un certificato Symantec.

    1.  **Accedere a Windows Phone Dev Center** Accedere a [Windows Phone Dev Center](http://go.microsoft.com/fwlink/?LinkId=268442) usando le informazioni dell'account aziendale che sono state immesse per l'accesso e per acquistare l'account aziendale. La richiesta di certificato di firma codice deve essere preventivamente autorizzata da un responsabile dell'azienda.

    2.  **Ottenere un certificato Symantec aziendale** Acquistare un certificato dal [sito Web Symantec](http://go.microsoft.com/fwlink/?LinkId=268441) usando il proprio ID Symantec. Dopo aver acquistato il certificato, l'approvatore aziendale nominato nell'account Windows Phone Dev Center riceverà un messaggio di posta elettronica che richiede l'approvazione della richiesta del certificato. Per altre informazioni sui requisiti del certificato Symantec, vedere l'articolo relativo ai [motivi per i quali Windows Phone richiede un certificato Symantec](https://technet.microsoft.com/en-us/library/dn764959.aspx#BKMK_Symantec). Domande frequenti sulla registrazione dei dispositivi Windows.

    3.  **Importare i certificati** Quando la richiesta è stata approvata, l'utente riceverà un messaggio di posta elettronica con le istruzioni su come importare i certificati. Seguire le istruzioni nel messaggio di posta elettronica per importare i certificati.

    4.  **Verificare i certificati importati** Per verificare che i certificati siano stati importati correttamente, accedere allo snap-in **Certificati**, fare clic con il tasto destro del mouse su **Certificati** e selezionare **Trova certificati**. Nel campo **Contiene** immettere "Symantec", quindi fare clic su **Trova ora**. I certificati importati dovrebbero essere visualizzati nei risultati.

        ![Trovare il certificato Symantec](../media/wit.gif)

    5.  **Esportare un certificato di firma** Dopo aver verificato che i certificati siano presenti, è possibile esportare il file con estensione pfx per la firma nel portale aziendale. Selezionare il certificato Symantec con "firma codice" in **Scopo designato**. Fare clic con il pulsante destro del mouse sul certificato della firma del codice e selezionare **Esporta**.

        ![Esportare il certificato per la firma](../media/wit-walk-cert2.gif)

        In **Esportazione guidata certificati**selezionare **Sì, esporta la chiave privata** e fare clic su **Avanti**. **Selezionare Scambio informazioni personali - PKCS #12 (.PFX)** e selezionare **Se possibile, includi tutti i certificati per percorso certificazione**. Completare la procedura guidata. Per altre informazioni, vedere la sezione [Esportare un certificato con la chiave privata](http://go.microsoft.com/fwlink/?LinkID=203031).

    6.  **Scaricare e firmare l'app Portale aziendale**

        Il supporto per la registrazione di Windows Phone richiede che l'app Portale aziendale di Windows Phone 8.0 sia firmata e caricata in Intune.

        1.  **Scaricare il portale aziendale** Scaricare il [portale aziendale di Intune per Windows Phone](http://go.microsoft.com/fwlink/?LinkId=268440) dall'Area download Microsoft. Il percorso di installazione predefinito è `C:\Program Files (x86)\Microsoft Corporation\Windows Intune Company Portal for Windows Phone`.

        2.  **Scaricare Windows Phone 8.0 SDK** Scaricare il [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=615570).

        3.  **Firmare il codice dell'app Portale aziendale** Usare l'app XAPSignTool scaricata con l'SDK per firmare il portale aziendale con il file pfx creato dal certificato Symantec. Per altre informazioni, vedere [Come firmare un'app aziendale usando XapSignTool](http://go.microsoft.com/fwlink/?LinkID=280195).

    7.  **Caricare l'app Portale aziendale in Intune** Caricare il file firmato dell'app Portale aziendale e il certificato con il codice firmato per rendere l'app disponibile agli utenti finali.

        1.  Nella [console di amministrazione di Intune](http://manage.microsoft.com) fare clic su **Amministrazione** &gt; **Windows Phone**.

        2.  Fare clic su **Carica file app firmato** e accedere con l'ID amministratore di Intune.

        3.  Nella pagina **Installazione software** per **Specificare il percorso dei file di installazione software** individuare il percorso dell'app Portale aziendale con codice firmato (estensione xap per Windows Phone 8.0 o appx per Windows Phone 8.1).

            Se si sta valutando Intune e caricando un file dell'app con codice firmato in un account di valutazione Intune, deselezionare la casella di controllo **Utilizza il file dell'app Portale aziendale firmato da un certificato di firma codice Symantec di esempio**.

        4.  Aggiungere il file di certificato (estensione pfx) esportato in **Certificato di firma codice** e creare una password per il certificato.

        5.  Nella pagina **Descrizione software** completare i campi tenendo presente che queste informazioni corrispondono ai dettagli relativi all'app visualizzati dagli utenti nel Portale aziendale.

        6.  Completare la procedura guidata. Gli utenti che registrano un dispositivo Windows Phone 8.0 riceveranno ora l'app Portale aziendale nei propri dispositivi durante la registrazione. Gli utenti di Windows Phone 8.1 possono installare l’app Portale aziendale dalla versione di archivio del portale aziendale.  Se i dispositivi Windows Phone 8.1 sono bloccati da Windows Phone Store o si desidera distribuire l'app Portale aziendale usando Intune, è necessario scaricare e firmare l'app Portale aziendale di Windows Phone 8.1 (SSP.appx).

4.  **Comunicare agli utenti che possono ottenere l'accesso alle risorse aziendali dal portale aziendale** Gli utenti devono sapere come registrare i loro dispositivi e cosa succede una volta che i loro dispositivi sono gestiti. [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)

## Distribuire l’app Portale aziendale di Windows Phone 8.1
È possibile distribuire l'app Portale aziendale nei dispositivi Windows Phone 8.1 con Intune anziché eseguire l'installazione da Windows Phone Store. È comunque necessario abilitare la registrazione dei dispositivi Windows Phone con i passaggi illustrati in precedenza utilizzando il certificato Symantec. È quindi necessario scaricare l'app Portale aziendale di Windows Phone 8.1 e firmarla con il certificato Symantec.  Questa operazione è necessaria solo se gli utenti non utilizzano lo Store aziendale e si desidera distribuire Portale aziendale nei dispositivi Windows Phone 8.1.


1.  **Scaricare Portale aziendale**

    Scaricare l'[app Portale aziendale di Microsoft Intune per Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) dall'Area download ed eseguire il file autoestraente (estensione exe). Questo file contiene due file:

    -   CompanyPortal.appx: app di installazione di Portale aziendale per Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1: uno script di PowerShell che è possibile usare per firmare il file dell’app Portale aziendale in modo che possa essere distribuita ai dispositivi Windows Phone 8.1

2.  **Scaricare Windows Phone SDK** Scaricare il [Windows Phone 8.0 SDK](http://go.microsoft.com/fwlink/?LinkId=615570) (http://go.microsoft.com/fwlink/?LinkId=268439) e installare l'SDK nel computer. Questo SDK è necessario per generare un token di registrazione applicazione.

3.  **Generare un file AETX** Generare un file token di registrazione dell'applicazione con estensione aetx dal file PFX Symantec usando AETGenerator.exe, incluso nel Windows Phone 8.0 SDK. Per istruzioni su come creare un file AETX, vedere [Come generare un token di registrazione dell’applicazione per Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)

4.  **Scaricare il Windows SDK per Windows 8.1** Scaricare e installare il [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525). Si noti che lo script di PowerShell incluso con l'app Portale aziendale usa il percorso di installazione predefinito, `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Se si esegue l’installazione in un altro percorso, è necessario includere il percorso in un parametro del cmdlet.

5.  **Firmare il codice dell'app con PowerShell** Come amministratore, aprire **Windows PowerShel**l sul computer host installato con il Windows SDK, il certificato di firma codice mobile aziendale Symantec, accedere al file Sign-WinPhoneCompanyPortal.ps1 ed eseguire lo script.

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

    -   `-OutputAppx` : il percorso locale e il nome file per l'app Portale aziendale firmata tra virgolette singole. Ad esempio 'C:\temp\CompanyPortal.appx'

    -   `-PfxFilePath` : il percorso locale e il nome file per il file con estensione pfx esportato del certificato Symantec. Ad esempio, 'C:\signing\cert.pfx'

    -   `-PfxPassword` : la password usata per firmare il file con estensione pfx tra virgolette singole. Ad esempio  '1234'

    -   `-AetxPath` : il percorso locale del file con estensione aetx usato per leggere l'ID aziendale se l'argomento 'EnterpriseId' non è definito. È necessario specificare questo argomento oppure EnterpriseId. Ad esempio, 'C:\signing\cert.pfx'

    -   `-PublisherId` : l'ID editore dell'azienda. Se assente, viene usato il campo 'Subject' del certificato di firma codice mobile aziendale Symantec . Ad esempio, 'OID.0.9.2342.19200300.100.1.1=1000000001, CN = "Test, Inc.", OU = Test 1'

    -   `-SdkPath` : il percorso della cartella root di Windows SDK per Windows 8.1. Questo argomento è facoltativo e l’impostazione predefinita è ${env:ProgramFiles(x86)} \Windows Kits\8.1.

    -   `-EnterpriseId` : l'ID azienda. È necessario specificare questo argomento oppure 'AetxPath'. Se questo argomento non viene specificato, l'ID azienda viene letto dal file AETX. Ad esempio, 1000000001.

6.  Distribuire l’app Portale aziendale di Windows Phone 8.1 (SSP.appx).

    > [!IMPORTANT]
    > È possibile installare contemporaneamente il file ssp.xap e il Portale aziendale dallo Store, il che potrebbe generare confusione per gli utenti. Per far sì che tutti gli utenti usino il file ssp.xap, creare un'app bloccata per la versione dello Store del Portale aziendale. Per far sì che tutti i dispositivi Windows Phone 8.1 usino solo la versione dello Store del Portale aziendale, scegliere tra queste tre opzioni:
    >
    > -   Se non si esegue il sideload delle app e non è necessario supportare Windows Phone 8.0, non caricare il file ssp.xap firmato.
    > -   Se sono necessarie app con sideload e non sono presenti dispositivi Windows Phone 8 in fase di registrazione, modificare la distribuzione del file ssp.xap creata automaticamente passando da "disponibile" a "disinstalla".
    > -   Se è necessario installare le app con sideload ed eseguire la registrazione e la ricezione del file ssp.xap nei dispositivi Windows Phone 8.0, creare una nuova distribuzione software del file ssp.xap e distribuirlo con l'azione **disinstalla** . I dispositivi Windows Phone 8.0 non supportano l'installazione o la disinstallazione forzata delle app, quindi ignoreranno la distribuzione. I dispositivi Windows Phone 8.1 supportano l'azione di disinstallazione e rimuoveranno il file ssp.xap.



<!--HONumber=Jun16_HO4-->


