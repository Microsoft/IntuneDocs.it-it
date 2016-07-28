---
title: Configurare l'infrastruttura di certificazione per PFX | Microsoft Intune
description: Creare e distribuire profili certificato con estensione pfx.
keywords: 
author: nbigman
manager: Arob98
ms.date: 05/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 72288296d966b9b9fae4fd721b4460528213f626
ms.openlocfilehash: f654dba31198115851feeeec90f04b8ad767e549



---
# Configurare l'infrastruttura di certificazione
Questo argomento descrive cosa è necessario per creare e distribuire i profili certificato con estensione pfx.

Per eseguire qualsiasi autenticazione basata su certificati all'interno dell'azienda, è necessaria un'autorità di certificazione dell'organizzazione.

Per usare i profili di certificato PFX, oltre all'autorità di certificazione dell'organizzazione, è anche necessario:

-   Un computer che può comunicare con l'autorità di certificazione. In alternativa, è possibile usare il computer dell'autorità di certificazione stessa.

 -  Il Connettore di certificati di Intune, che viene eseguito sul computer che può comunicare con l'autorità di certificazione.

## Descrizione dell'infrastruttura locale


-    **Dominio di Active Directory**: tutti i server elencati in questa sezione (tranne il server proxy applicazione Web) devono essere aggiunti al dominio di Active Directory.

-  **Autorità di certificazione** (CA): un'autorità di certificazione dell'organizzazione (CA) eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versioni successive. L'opzione CA autonoma non è supportata. Per istruzioni su come configurare un'autorità di certificazione, vedere [Installare l'autorità di certificazione](http://technet.microsoft.com/library/jj125375.aspx).
    Se la CA esegue Windows Server 2008 R2, è necessario [installare l'hotfix di KB2483564](http://support.microsoft.com/kb/2483564/).

 -  **Computer che possono comunicare con Autorità di certificazione**: in alternativa, è possibile usare il computer dell'autorità di certificazione stessa.
-  **Connettore di certificati di Microsoft Intune**: usare la console di amministrazione di Intune per scaricare il programma di installazione del **Connettore di certificati** (**ndesconnectorssetup.exe**). È quindi possibile eseguire **ndesconnectorssetup.exe** nel computer in cui si vuole installare Connettore di certificati. Per i profili certificato PFX installare Connettore di certificati nel computer che comunica con l'autorità di certificazione.
-  **Server Proxy applicazione Web ** (facoltativo): è possibile usare un server che esegue Windows Server 2012 R2 o versioni successive come Server Proxy applicazione Web (WAP). Questa configurazione:
    -  Consente ai dispositivi di ricevere i certificati usando una connessione Internet.
    -  Vale come raccomandazione di sicurezza quando i dispositivi usano la connessione a Internet per ricevere e rinnovare i certificati.

 > [!NOTE]           
> -    Il server che ospita WAP [deve installare un aggiornamento](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) che abilita il supporto per gli URL lunghi usati dal servizio Registrazione dispositivi di rete. Questo aggiornamento è incluso nell' [aggiornamento cumulativo di dicembre 2014](http://support.microsoft.com/kb/3013769)oppure può essere scaricato singolarmente da [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Il server che ospita WAP deve avere un certificato SSL che corrisponde al nome pubblicato ai client esterni e riconosciuto come attendibile dal server NDES. Questi certificati consentono al server WAP di chiudere la connessione SSL dai client e creare una nuova connessione SSL nel server NDES.
    Per informazioni sui certificati per WAP, vedere la sezione sulla **pianificazione dei certificati** in [Pianificazione della pubblicazione di applicazioni mediante il proxy applicazione Web](https://technet.microsoft.com/library/dn383650.aspx). Per informazioni generali sui server WAP (Web Application Proxy, proxy di applicazioni Web), vedere [Utilizzo di Proxy applicazione Web](http://technet.microsoft.com/library/dn584113.aspx).|


### Certificati e modelli

|Oggetto|Dettagli|
|----------|-----------|
|**Modello di certificato**|Questo modello viene configurato nella CA emittente.|
|**Certificato CA radice attendibile**|Viene esportato come file **.cer** dalla CA emittente o da qualsiasi dispositivo che consideri attendibile la CA emittente e viene distribuito ai dispositivi mediante il profilo del certificato CA attendibile.<br /><br />Viene usato un certificato CA radice attendibile per ogni piattaforma di sistema e lo si associa con ogni profilo del certificato radice attendibile creato.<br /><br />È possibile usare certificati CA radice attendibili aggiuntivi, se necessario. Ad esempio, è possibile farlo per fornire un trust a un'autorità di certificazione che firma i certificati di autenticazione del server per i punti di accesso Wi-Fi.|


## Configurare l'infrastruttura
Prima di configurare i profili di certificato, è necessario completare le seguenti attività, che richiedono una conoscenza preliminare di Windows Server 2012 R2 e Servizi certificati Active Directory (ADCS):

**Attività 1**: Configurare i modelli di certificato nell'autorità di certificazione **Attività 2**: Abilitare, installare e configurare Connettore di certificati di Intune

### Attività 1: configurare i modelli di certificato nell'autorità di certificazione
In questa attività verrà pubblicato il modello di certificato

##### Per configurare l'autorità di certificazione

1.  Nella CA emittente usare lo snap-in Modelli di certificato per creare un nuovo modello personalizzato o copiare un modello esistente (ad esempio, il modello Utente) e modificarlo per l'uso con file con estensione .pFX.

    Il modello deve avere le seguenti configurazioni:

    -   Specificare un **nome visualizzato** descrittivo per il modello.

    -   Nella scheda **Nome soggetto** selezionare **Fornisci nella richiesta**. (La sicurezza viene applicata con il modulo dei criteri di Intune per NDES).

    -   Nella scheda **Estensioni** verificare che la **descrizione dei criteri dell'applicazione** includa **Autenticazione client**.

        > [!IMPORTANT]
        > Per i modelli di certificato iOS e Mac OS X, nella scheda **Estensioni** modificare **Utilizzo chiavi** e verificare che **Firma come prova dell'origine** non sia selezionato.


3.  Esaminare il **periodo di validità** nella scheda **Generale** del modello. Per impostazione predefinita, Intune usa il valore configurato nel modello. Tuttavia, è possibile configurare la CA per consentire al richiedente di specificare un valore diverso, che è poi possibile impostare dalla console di amministrazione di Intune. Per usare sempre il valore nel modello, ignorare il resto del passaggio.

    > [!IMPORTANT]
    > Le piattaforme iOS e Mac OS X usano sempre il valore impostato nel modello, indipendentemente da altre configurazioni.

    Per configurare la CA in modo che consenta al richiedente di specificare il periodo di validità, eseguire questi comandi nella CA:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  Nella CA emittente usare lo snap-in dell'autorità di certificazione per pubblicare il modello di certificato.

    1.  Selezionare il nodo **Modelli di certificato**, fare clic su **Azione**-&gt; **Nuovo** &gt; **Modello di certificato da rilasciare**, quindi selezionare il modello creato nel passaggio 2.

    2.  Verificare che il modello sia stato pubblicato visualizzandolo nella cartella **Modelli di certificato** .

5.  Nel computer della CA assicurarsi che il computer che ospita Connettore di certificati di Intune abbia l'autorizzazione di registrazione per poter accedere al modello usato nella creazione del profilo PFX. Impostare l'autorizzazione nella scheda **Sicurezza** delle proprietà del computer della CA.

### Attività 2: abilitare, installare e configurare il Connettore di certificati di Intune
In questa attività sarà possibile:

Scaricare, installare e configurare Connettore di certificati

##### Per abilitare il supporto per Connettore di certificati

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com) e fare clic su **Amministrazione** &gt; **Connettore di certificati**.

2.  Fare clic su **Configura Connettore di certificati locale**.

3.  Selezionare **Abilita Connettore di certificati**, quindi fare clic su **OK**.

##### Per scaricare, installare e configurare Connettore di certificati

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com) e quindi fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Connettore di certificati** &gt; **Scarica Connettore di certificati**.

2.  Al termine del download, eseguire il programma di installazione scaricato (**ndesconnectorssetup.exe**):

  Eseguire il programma di installazione nel computer che può connettersi all'autorità di certificazione. Scegliere l'opzione di distribuzione PFX, quindi fare clic su Installa. Al termine dell'installazione, procedere alla creazione di un profilo certificato come descritto in [Configure certificate profiles](configure-intune-certificate-profiles.md) (Configurare i profili certificato).

   <!-- Not sure about step 3 below -->

3.  Quando viene richiesto il certificato client di Connettore di certificati, fare clic su **Seleziona** e selezionare il **certificato di autenticazione client** installato nel corso dell'Attività 3.

    Dopo aver selezionato il certificato di autenticazione client, viene visualizzato di nuovo il **certificato client per Connettore di certificati di Microsoft Intune** . Anche se il certificato selezionato non viene visualizzato, fare clic su **Avanti** per visualizzare le proprietà del certificato. Fare clic su **Avanti**, quindi su **Installa**.

4.  Al termine della procedura guidata, prima di chiuderla, fare clic su **Avvia l'interfaccia utente di Connettore di certificati**.

    > [!TIP]
    > Se si chiude la procedura guidata prima di avviare l'interfaccia utente di Connettore di certificati, è possibile riaprirla con il comando seguente:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Nell'interfaccia utente di **Connettore di certificati** :

    Fare clic su **Accedi** e immettere le credenziali di amministratore del servizio di Intune oppure le credenziali di amministratore tenant con autorizzazioni di amministrazione globali.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    Selezionare la scheda **Avanzate** , quindi fornire le credenziali per un account con l'autorizzazione **Rilascio e gestione certificati** sulla CA emittente, quindi fare clic su **Applica**.

    Ora è possibile chiudere l'interfaccia utente di Connettore di certificati.

6.  Aprire il prompt dei comandi e digitare **services.msc**, quindi premere **Invio**, fare clic con il pulsante destro del mouse su **Servizio Intune Connector** e scegliere **Riavvia**.

Per confermare che il servizio sia in esecuzione, aprire un browser e immettere il seguente URL, che deve restituire un errore **403** :

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

### Passaggi successivi
A questo punto è possibile configurare i profili certificato come descritto in [Configure certificate profiles](Configure-Intune-certificate-profiles.md) (Configurare i profili certificato).



<!--HONumber=Jul16_HO3-->


