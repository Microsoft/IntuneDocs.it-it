---
title: Configurare l&quot;infrastruttura di certificazione di Intune per PKCS | Anteprima di Intune in Azure | Documentazione Microsoft
description: "Anteprima di Intune in Azure: informazioni sulle modalità di configurazione dell&quot;infrastruttura per l&quot;uso di certificati PKCS con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e189ebd1-6ca1-4365-9d5d-fab313b7e979
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f05e0018fb202ab5774e935c3f59855e4aa2e75
ms.openlocfilehash: 74f2cc7221e737371d7db97ec25d872578df273d



---
# <a name="configure-your-intune-certificate-infrastructure-for-pkcs"></a>Configurare l'infrastruttura di certificazione di Intune per PKCS
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Questo argomento descrive cosa è necessario per creare e distribuire i profili di certificato PKCS con Intune.

Per eseguire qualsiasi autenticazione basata su certificati all'interno dell'azienda, è necessaria un'autorità di certificazione dell'organizzazione.

Per usare i profili di certificato PKCS, oltre all'autorità di certificazione dell'organizzazione, è anche necessario:

-   Un computer che può comunicare con l'autorità di certificazione. In alternativa, è possibile usare il computer dell'autorità di certificazione stessa.

-  Il Connettore di certificati di Intune, che viene eseguito sul computer che può comunicare con l'autorità di certificazione.

## <a name="important-terms"></a>Termini importanti


-    **Dominio di Active Directory**: tutti i server elencati in questa sezione (tranne il server proxy applicazione Web) devono essere aggiunti al dominio di Active Directory.

-  **Autorità di certificazione**: un'autorità di certificazione dell'organizzazione (CA) eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versione successiva. L'opzione CA autonoma non è supportata. Per istruzioni su come configurare un'autorità di certificazione, vedere [Installare l'autorità di certificazione](http://technet.microsoft.com/library/jj125375.aspx).
    Se la CA esegue Windows Server 2008 R2, è necessario [installare l'hotfix di KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Computer che possono comunicare con Autorità di certificazione**: in alternativa, è possibile usare il computer dell'autorità di certificazione stessa.
-  **Connettore di certificati di Microsoft Intune**: dal portale di Azure scaricare il programma di installazione di **Connettore di certificati** (**ndesconnectorssetup.exe**). È quindi possibile eseguire **ndesconnectorssetup.exe** nel computer in cui si vuole installare Connettore di certificati. Per i profili di certificato PKCS installare il Connettore di certificati nel computer che comunica con l'autorità di certificazione.
-  **Server Proxy applicazione Web ** (facoltativo): è possibile usare un server che esegue Windows Server 2012 R2 o versione successiva come Server Proxy applicazione Web (WAP). Questa configurazione:
    -  Consente ai dispositivi di ricevere i certificati usando una connessione Internet.
    -  Vale come raccomandazione di sicurezza quando i dispositivi usano la connessione a Internet per ricevere e rinnovare i certificati.

 > [!NOTE]           
> -    Il server che ospita WAP [deve installare un aggiornamento](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) che abilita il supporto per gli URL lunghi usati dal servizio Registrazione dispositivi di rete (NDES). Questo aggiornamento è incluso nell' [aggiornamento cumulativo di dicembre 2014](http://support.microsoft.com/kb/3013769)oppure può essere scaricato singolarmente da [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Il server che ospita WAP deve avere un certificato SSL che corrisponde al nome pubblicato ai client esterni e riconosciuto come attendibile dal server NDES. Questi certificati consentono al server WAP di chiudere la connessione SSL dai client e creare una nuova connessione SSL nel server NDES.
    Per informazioni sui certificati per WAP, vedere la sezione sulla **pianificazione dei certificati** in [Pianificazione della pubblicazione di applicazioni mediante il proxy applicazione Web](https://technet.microsoft.com/library/dn383650.aspx). Per informazioni generali sui server WAP (Web Application Proxy, proxy di applicazioni Web), vedere [Utilizzo di Proxy applicazione Web](http://technet.microsoft.com/library/dn584113.aspx).|


## <a name="certificates-and-templates"></a>Certificati e modelli

|Oggetto|Dettagli|
|----------|-----------|
|**Modello di certificato**|Questo modello viene configurato nella CA emittente.|
|**Certificato CA radice attendibile**|Viene esportato come file **.cer** dalla CA emittente o da qualsiasi dispositivo che consideri attendibile la CA emittente e viene distribuito ai dispositivi mediante il profilo del certificato CA attendibile.<br /><br />Viene usato un certificato CA radice attendibile per ogni piattaforma di sistema e lo si associa con ogni profilo del certificato radice attendibile creato.<br /><br />È possibile usare certificati CA radice attendibili aggiuntivi, se necessario. Ad esempio, è possibile farlo per fornire un trust a un'autorità di certificazione che firma i certificati di autenticazione del server per i punti di accesso Wi-Fi.|


## <a name="configure-your-infrastructure"></a>Configurare l'infrastruttura
Prima di poter configurare i profili certificato, è necessario completare le attività seguenti. Le attività seguenti presuppongono la conoscenza di Windows Server 2012 R2 e di Servizi certificati Active Directory (ADCS):

- **Attività 1**: configurare i modelli di certificato nell'autorità di certificazione.
- **Attività 2**: abilitare, installare e configurare il Connettore di certificati di Intune.

## <a name="task-1---configure-certificate-templates-on-the-certification-authority"></a>Attività 1: configurare i modelli di certificato nell'autorità di certificazione
In questa attività verrà pubblicato il modello di certificato.

### <a name="to-configure-the-certification-authority"></a>Per configurare l'autorità di certificazione

1.  Nella CA emittente usare lo snap-in Modelli di certificato per creare un nuovo modello personalizzato o copiare e modificare un modello esistente (ad esempio, il modello Utente) per l'uso con il profilo PKCS.

    Il modello deve includere quanto segue:

    -   Specificare un **nome visualizzato** descrittivo per il modello.

    -   Nella scheda **Nome soggetto** selezionare **Fornisci nella richiesta**. (La sicurezza viene applicata con il modulo dei criteri di Intune per NDES).

    -   Nella scheda **Estensioni** verificare che la **descrizione dei criteri dell'applicazione** includa **Autenticazione client**.

        > [!IMPORTANT]
        > Per i modelli di certificato iOS e Mac OS X, nella scheda **Estensioni** modificare **Utilizzo chiavi** e verificare che **Firma come prova dell'origine** non sia selezionato.

2.  Esaminare il **periodo di validità** nella scheda **Generale** del modello. Per impostazione predefinita, Intune usa il valore configurato nel modello. Tuttavia, è possibile configurare la CA per consentire al richiedente di specificare un valore diverso, che è poi possibile impostare dalla console di amministrazione di Intune. Per usare sempre il valore nel modello, ignorare il resto del passaggio.

    > [!IMPORTANT]
    > Le piattaforme iOS e Mac OS X usano sempre il valore impostato nel modello, indipendentemente da altre configurazioni.

    Per configurare la CA in modo che consenta al richiedente di specificare il periodo di validità, eseguire questi comandi nella CA:

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  Nella CA emittente usare lo snap-in dell'autorità di certificazione per pubblicare il modello di certificato.

    a.  Selezionare il nodo **Modelli di certificato**, fare clic su **Azione**-&gt; **Nuovo** &gt; **Modello di certificato da rilasciare** e quindi selezionare il modello creato nel passaggio 2.

    b.  Verificare che il modello sia stato pubblicato visualizzandolo nella cartella **Modelli di certificato** .

4.  Nel computer della CA assicurarsi che il computer che ospita il Connettore di certificati di Intune abbia l'autorizzazione di registrazione per poter accedere al modello usato nella creazione del profilo PKCS. Impostare l'autorizzazione nella scheda **Sicurezza** delle proprietà del computer della CA.

## <a name="task-2---enable-install-and-configure-the-intune-certificate-connector"></a>Attività 2: abilitare, installare e configurare il Connettore di certificati di Intune
In questa attività sarà possibile:

Scaricare, installare e configurare Connettore di certificati.

### <a name="to-enable-support-for-the-certificate-connector"></a>Per abilitare il supporto per Connettore di certificati

1.  Accedere al portale Azure.
2.  Scegliere **Altri servizi** > **Altro** > **Intune**.
3.  Nel pannello **Intune** scegliere **Configura i dispositivi**.
2.  Nel pannello **Configurazione del dispositivo** scegliere **Installazione** > **Autorità di certificazione**.
2.  Nel **passaggio 1** scegliere **Abilita**.

### <a name="to-download-install-and-configure-the-certificate-connector"></a>Per scaricare, installare e configurare Connettore di certificati

1.  Nel pannello **Configura i dispositivi** scegliere **Installazione** > **Autorità di certificazione**.
2.  Scegliere **Scarica il connettore del certificato**.
2.  Al termine del download, eseguire il programma di installazione scaricato (**ndesconnectorssetup.exe**).
  Eseguire il programma di installazione nel computer che può connettersi all'autorità di certificazione. Scegliere l'opzione di distribuzione PFX e quindi fare clic su **Installa**. Al termine dell'installazione, procedere alla creazione di un profilo certificato come descritto in [Configure certificate profiles](how-to-configure-certificates.md) (Configurare i profili certificato).

3.  Quando viene richiesto il certificato client di Connettore di certificati, scegliere **Seleziona** e selezionare il certificato di **autenticazione client** installato.

    Dopo aver selezionato il certificato di autenticazione client, viene visualizzato di nuovo il **certificato client per Connettore di certificati di Microsoft Intune** . Anche se il certificato selezionato non viene visualizzato, scegliere **Avanti** per visualizzare le proprietà del certificato. Scegliere **Avanti** e quindi **Installa**.

4.  Al termine della procedura guidata, prima di chiuderla, fare clic su **Avvia l'interfaccia utente di Connettore di certificati**.

    > [!TIP]
    > Se si chiude la procedura guidata prima di avviare l'interfaccia utente di Connettore di certificati, è possibile riaprirla con il comando seguente:
    >
    > **&lt;percorso_installazione&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Nell'interfaccia utente di **Connettore di certificati** :

    a. Scegliere **Accedi** e immettere le credenziali di amministratore del servizio di Intune oppure le credenziali di amministratore tenant con autorizzazioni di amministrazione globali.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b. Selezionare la scheda **Avanzate** e quindi fornire le credenziali per un account con l'autorizzazione **Rilascio e gestione certificati** sulla CA emittente.

    c. Scegliere **Applica**.

    Ora è possibile chiudere l'interfaccia utente di Connettore di certificati.

6.  Aprire un prompt dei comandi e digitare**services.msc**. Premere **INVIO**, fare clic con il pulsante destro del mouse su **Servizio Intune Connector** e scegliere **Riavvia**.

Per confermare che il servizio sia in esecuzione, aprire un browser e immettere il seguente URL, che deve restituire un errore **403** :

**http://&lt;FQDN_del_server_NDES&gt;/certsrv/mscep/mscep.dll**

### <a name="next-steps"></a>Passaggi successivi
A questo punto è possibile configurare i profili di certificato come descritto in [How to configure certificates with Microsoft Intune](how-to-configure-certificates.md) (Come configurare i certificati con Microsoft Intune).



<!--HONumber=Feb17_HO1-->


