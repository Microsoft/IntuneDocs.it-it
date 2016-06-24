---
# required metadata

title: Configurare l'infrastruttura di certificazione | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3a435650-3891-4754-8abc-4bbac244f33b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurare l'infrastruttura di certificazione
Questo argomento descrive cosa è necessario per creare e distribuire i profili di certificato.

Per eseguire qualsiasi autenticazione basata su certificati all'interno dell'azienda, è necessaria un'autorità di certificazione dell'organizzazione.

Per usare i profili di certificato SCEP, oltre all'autorità di certificazione dell'organizzazione, è anche necessario:

-   Un server che esegue il servizio Registrazione dispositivi di rete

-   Il Connettore di certificati di Intune, che è installato nel server Windows Server 2012 R2 che esegue NDES

Per usare i profili di certificato PFX, oltre all'autorità di certificazione dell'organizzazione, è anche necessario:

-  Un computer che può comunicare con l'autorità di certificazione. In alternativa, usare il computer dell'autorità di certificazione stesso.

-  Il Connettore di certificati di Intune, che viene eseguito sul computer che può comunicare con l'autorità di certificazione.

## Infrastruttura locale


-    **Dominio di Active Directory**: tutti i server elencati in questa sezione (tranne il server proxy applicazione Web) devono essere aggiunti al dominio di Active Directory.

-  **Autorità di certificazione** (CA): un'autorità di certificazione dell'organizzazione (CA) eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versioni successive. L'opzione CA autonoma non è supportata. Per istruzioni su come configurare un'autorità di certificazione, vedere [Installare l'autorità di certificazione](http://technet.microsoft.com/library/jj125375.aspx).
    Se la CA esegue Windows Server 2008 R2, è necessario [installare l'hotfix di KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Server NDES** (solo SCEP): sui server che eseguono Windows Server 2012 R2 o versioni successive è necessario installare il Servizio Registrazione dispositivi di rete (NDES). Intune non supporta l'uso di NDES se viene eseguito su un server con Enterprise CA. Vedere [Linee guida per il servizio Registrazione dispositivi di rete](http://technet.microsoft.com/library/hh831498.aspx) per istruzioni su come configurare Windows Server 2012 R2 per ospitare il Servizio Registrazione dispositivi di rete.|
-  **Computer che possono comunicare con Autorità di certificazione** (solo PFX): in alternativa, è possibile usare il computer di Autorità di certificazione.
-  **Connettore di certificati di Microsoft Intune**: usare la console di amministrazione di Intune per scaricare il programma di installazione del **Connettore di certificati** (**ndesconnectorssetup.exe**). È quindi possibile eseguire **ndesconnectorssetup.exe** nel computer in cui si vuole installare Connettore di certificati. Per i profili certificato PFX installare Connettore di certificati nel computer che comunica con l'autorità di certificazione.
-  **Server Proxy applicazione Web ** (facoltativo): è possibile usare un server che esegue Windows Server 2012 R2 o versioni successive come Server Proxy applicazione Web (WAP). Questa configurazione:
    -  Consente ai dispositivi di ricevere i certificati usando una connessione Internet.
    -  Vale come raccomandazione di sicurezza quando i dispositivi usano la connessione a Internet per ricevere e rinnovare i certificati.

> [!NOTE]           
> -    Il server che ospita WAP [deve installare un aggiornamento](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) che abilita il supporto per gli URL lunghi usati dal servizio Registrazione dispositivi di rete. Questo aggiornamento è incluso nell' [aggiornamento cumulativo di dicembre 2014](http://support.microsoft.com/kb/3013769)oppure può essere scaricato singolarmente da [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Il server che ospita WAP deve avere un certificato SSL che corrisponde al nome pubblicato ai client esterni e riconosciuto come attendibile dal server NDES. Questi certificati consentono al server WAP di chiudere la connessione SSL dai client e creare una nuova connessione SSL nel server NDES.
Per informazioni sui certificati per WAP, vedere la sezione sulla **pianificazione dei certificati** in [Pianificazione della pubblicazione di applicazioni mediante il proxy applicazione Web](https://technet.microsoft.com/library/dn383650.aspx). Per informazioni generali sui server proxy applicazione Web, vedere [Utilizzo di proxy applicazione Web](http://technet.microsoft.com/library/dn584113.aspx)


### Certificati e modelli

|Oggetto|Dettagli|
|----------|-----------|
|**Modello di certificato**|Questo modello viene configurato nella CA emittente.|
|**Certificato di autenticazione client**|Richiesto dalla CA emittente o dalla CA pubblica, questo certificato viene installato nel server NDES.|
|**Certificato di autenticazione server**|Richiesto dalla CA emittente o dalla CA pubblica, questo certificato SSL viene installato e associato in IIS nel server NDES.|
|**Certificato CA radice attendibile**|Viene esportato come file **.cer** dalla CA emittente o da qualsiasi dispositivo che consideri attendibile la CA emittente e viene distribuito ai dispositivi mediante il profilo del certificato CA attendibile.<br /><br />Viene usato un certificato CA radice attendibile per ogni piattaforma di sistema e lo si associa con ogni profilo del certificato radice attendibile creato.<br /><br />È possibile usare certificati CA radice attendibili aggiuntivi, se necessario. Ad esempio, è possibile farlo per fornire un trust a un'autorità di certificazione che firma i certificati di autenticazione del server per i punti di accesso Wi-Fi.|

### Account

|Nome|Dettagli|
|--------|-----------|
|**Account di servizio NDES**|Specificare un account utente di dominio da usare come account del servizio NDES.|

## Configurare l'infrastruttura
Prima di configurare i profili di certificato, è necessario completare le seguenti attività, che richiedono una conoscenza preliminare di Windows Server 2012 R2 e Servizi certificati Active Directory (ADCS):

**Attività 1:** configurare i modelli di certificato nell'autorità di certificazione

**Attività 2**, solo per profili SCEP: configurare i prerequisiti nel server NDES

**Attività 3**, solo per profili SCEP: configurare NDES per l'uso con Intune

**Attività 4:** abilitare, installare e configurare il Connettore di certificati di Intune

## Attività 1: configurare i modelli di certificato nell'autorità di certificazione
In questa attività sarà possibile:

-   Creare un account del servizio NDES

    > [!NOTE] Per revocare i certificati, l'account del servizio NDES ha bisogno dei diritti *Rilascio e gestione certificati* per ogni modello di certificato usato da un profilo certificato.

-   Configurare un modello di certificato per NDES

-   Pubblicare il modello di certificato per NDES

##### Per configurare l'autorità di certificazione

1.  Creare un account utente di dominio da usare come account del servizio NDES. L'account viene specificato quando si configurano i modelli nella CA emittente prima di installare e configurare NDES.

2.  Nella CA emittente usare lo snap-in Modelli di certificato per creare un nuovo modello personalizzato o copiare un modello esistente (ad esempio, il modello Utente) e modificarlo per l'utilizzo con NDES.

    Il modello deve avere le seguenti configurazioni:

    -   Specificare un **nome visualizzato** descrittivo per il modello.

    -   Nella scheda **Nome soggetto** selezionare **Fornisci nella richiesta**. (La sicurezza viene applicata con il modulo dei criteri di Intune per NDES).

    -   Nella scheda **Estensioni** verificare che la **descrizione dei criteri dell'applicazione** includa **Autenticazione client**.

        > [!IMPORTANT] Per i modelli di certificato iOS e Mac OS X, nella scheda **Estensioni** modificare **Utilizzo chiavi** e verificare che l'opzione **Firma come prova dell'origine** non sia selezionata.

    -   Nella scheda **Sicurezza** aggiungere l'account del servizio NDES e dargli le autorizzazioni di **registrazione** al modello.

3.  Esaminare il **periodo di validità** nella scheda **Generale** del modello. Per impostazione predefinita, Intune usa il valore configurato nel modello. Tuttavia, è possibile configurare la CA per consentire al richiedente di specificare un valore diverso, che è poi possibile impostare dalla console di amministrazione di Intune. Per usare sempre il valore nel modello, ignorare il resto del passaggio.

    > [!IMPORTANT] Le piattaforme iOS e Mac OS X usano sempre il valore impostato nel modello, indipendentemente da altre configurazioni.

    Per configurare la CA in modo che consenta al richiedente di specificare il periodo di validità, eseguire questi comandi nella CA:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  Nella CA emittente usare lo snap-in dell'autorità di certificazione per pubblicare il modello di certificato.

    1.  Selezionare il nodo **Modelli di certificato**, fare clic su **Azione**-&gt; **Nuovo** &gt; **Modello di certificato da rilasciare**, quindi selezionare il modello creato nel passaggio 2.

    2.  Verificare che il modello sia stato pubblicato visualizzandolo nella cartella **Modelli di certificato** .

5.  Per i profili PFX: nel computer della CA assicurarsi che il computer che ospita il Connettore di certificati di Intune abbia l'autorizzazione di registrazione per poter accedere al modello usato nella creazione del profilo PFX. Impostare l'autorizzazione nella scheda **Sicurezza** delle proprietà del computer della CA.

## Attività 2 (solo profilo SCEP): configurare i prerequisiti nel server NDES
In questa attività sarà possibile:

-   Aggiungere NDES a Windows Server e configurare IIS per supportare NDES

-   Aggiungere l'account del servizio NDES al gruppo IIS_IUSR

-   Impostare SPN per l'account del servizio NDES

##### Per configurare i prerequisiti per il server NDES

1.  Nel server che ospiterà NDES, è necessario accedere come **amministratore dell'organizzazione**, quindi usare la [procedura guidata per l'aggiunta di ruoli e funzionalità](https://technet.microsoft.com/library/hh831809.aspx) per installare NDES:

    1.  Nella procedura guidata selezionare **Servizi certificati Active Directory** per ottenere l'accesso ai servizi di ruolo AD CS. Selezionare il **servizio Registrazione dispositivi di rete**, deselezionare **Autorità di certificazione**, quindi completare la procedura guidata.

        > [!TIP]
        > Nella pagina **Stato dell'installazione** della procedura guidata, non fare clic su **Chiudi**. Fare clic, invece, sul collegamento per **configurare i Servizi certificati Active Directory nel server di destinazione**. Si apre la procedura guidata **Configurazione AD CS** che verrà usata per l'attività successiva. Dopo aver aperto Configurazione AD CS, è possibile chiudere la procedura guidata per l'aggiunta di ruoli e funzionalità.

    2.  Quando NDES viene aggiunto al server, la procedura guidata installa anche IIS. Verificare che IIS abbia le seguenti configurazioni:

        -   **Server Web** &gt; **Sicurezza** &gt; **Filtro richieste**

        -   **Server Web** &gt; **Sviluppo applicazioni** &gt; **ASP.NET 3.5**. Installando ASP.NET 3.5 verrà installato anche .NET Framework 3.5. Quando si installa .NET Framework 3.5, installare la funzionalità di base di **.NET Framework 3.5** e **Attivazione HTTP**.

        -   **Server Web** &gt; **Sviluppo applicazioni** &gt; **ASP.NET 4.5**. Installando ASP.NET 4,5 verrà installato anche .NET Framework 4.5. Quando si installa .NET Framework 4.5, installare la funzionalità di base di **.NET Framework 4.5**, **ASP.NET 4.5** e la funzionalità **Servizi WCF** &gt; **Attivazione HTTP**.

        -   **Strumenti di gestione** &gt; **Compatibilità gestione IIS 6** &gt; **Compatibilità metabase IIS 6**

        -   **Strumenti di gestione** &gt; **Compatibilità gestione IIS 6** &gt; **Compatibilità WMI con IIS 6**

2.  Nel server aggiungere l'account del servizio NDES come membro del gruppo **IIS_IUSR**.

3.  Eseguire questo comando per impostare SPN dell'account del servizio NDES:

    -   **setspn -s http /&lt;nome DNS del server NDES&gt; &lt;nome di dominio&gt;\&lt;Nome account del servizio NDES&gt;**

    Ad esempio, se il server NDES è denominato **Server01**, il dominio è **Contoso.com**e l'account del servizio è **NDESService**, usare:

    -   **setspn –s http/Server01.contoso.com contoso\NDESService**

## Attività 3 (solo per profilo SCEP): configurare NDES per l'uso con Microsoft Intune 
In questa attività sarà possibile:

-   Configurare NDES per l'utilizzo con la CA emittente

-   Associare il certificato di autenticazione server (SSL) in IIS

-   Configurare il filtro richieste in IIS

##### Per configurare NDES per l'uso con Intune

1.  Nel server NDES aprire la procedura guidata Configurazione AD CS, quindi completare le seguenti configurazioni.

    > [!TIP]
    > Se nell'attività precedente è stato selezionato il collegamento, questa procedura guidata è già aperta. In caso contrario, aprire Server Manager per accedere alla configurazione di post-distribuzione per i Servizi certificati Active Directory.

    -   Nella pagina **Servizi di ruolo** selezionare **Servizio Registrazione dispositivi di rete**.

    -   Nella pagina **Account del servizio per NDES** specificare l'account del servizio NDES.

    -   Nella pagina **CA per NDES** fare clic su **Seleziona**, quindi selezionare la CA emittente in cui è stato configurato il modello di certificato.

    -   Nella pagina **Crittografia per NDES** impostare la lunghezza della chiave per soddisfare i requisiti aziendali.

    Nella pagina **Conferma** fare clic su **Configura** per completare la procedura guidata.

2.  Dopo aver completato la procedura guidata, modificare la seguente chiave del Registro di sistema nel server NDES:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    Per modificare questa chiave, identificare lo **scopo** del modello del certificato, come disponibile nella relativa scheda **Gestione richiesta**, quindi modificare la voce corrispondente nel Registro di sistema sostituendo i dati esistenti con il nome del modello di certificato (non il nome visualizzato del modello) specificato nell'attività 1. Nella tabella seguente viene eseguito il mapping lo scopo del modello di certificato per i valori del Registro di sistema:

    |Scopo del modello di certificato (nella scheda Gestione richieste)|Valore del Registro di sistema da modificare|Valore visualizzato nella console di amministrazione di Intune per il profilo SCEP|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Firma|SignatureTemplate|Firma digitale|
    |Crittografia|EncryptionTemplate|Crittografia chiave|
    |Firma e crittografia|GeneralPurposeTemplate|Crittografia chiave<br /><br />Firma digitale|
    Ad esempio, se lo scopo del modello di certificato è **Crittografia**, modificare il valore **EncryptionTemplate** in modo che corrisponda al nome del modello di certificato.

3.  Dopo aver modificato il Registro di sistema, eseguire **iisreset** nel server per forzare l'acquisizione delle modifiche recenti alla configurazione.

##### Per installare e associare i certificati nel server NDES

1.  Nel server NDES richiedere e installare un certificato **autenticazione server** dalla CA interna o dalla CA pubblica. Quindi associare questo certificato SSL in IIS.

    > [!TIP]
    > Dopo aver associato il certificato SSL in IIS, installare anche un certificato di autenticazione client. Questo certificato può essere emesso da qualsiasi CA considerata attendibile dal server NDES. Sebbene non sia una procedura consigliata, è possibile usare lo stesso certificato per l'autenticazione server e client, a condizione che il certificato abbia un utilizzo chiavi avanzato (EKU). Esaminare i seguenti passaggi per informazioni su questi certificati di autenticazione.

    1.  Dopo aver ottenuto il certificato di autenticazione server, aprire **Gestione IIS**, selezionare **Sito Web predefinito** nel riquadro **Connessioni** , quindi fare clic su **Binding** nel riquadro **Azioni** .

    2.  Fare clic su **Aggiungi**, impostare **Tipo** su **https**, quindi verificare che la porta sia **443**. (Per la configurazione autonoma di Intune è supportata solo la porta 443).

    3.  Per **Certificato SSL**, specificare il certificato di autenticazione server.

        > [!NOTE] Se il server NDES usa un nome esterno e uno interno per un unico indirizzo di rete, il certificato di autenticazione server deve avere un **Nome soggetto** con un nome server pubblico esterno e **Nome alternativo soggetto** che include il nome server interno.

2.  Nel server NDES, richiedere e installare un **certificato di autenticazione client** dalla CA interna o pubblica. Può essere lo stesso certificato del certificato di autenticazione server, se il certificato ha entrambe le funzionalità.

    Il certificato di autenticazione client deve avere le seguenti proprietà:

    **Utilizzo chiavi avanzato**: deve includere **Autenticazione client**

    **Nome soggetto**: deve essere uguale al nome DNS del server in cui si installa il certificato (server NDES).

##### Per configurare il Filtro richieste di IIS

1.  Nel server NDES aprire **Gestione IIS**, selezionare **Sito Web predefinito** nel riquadro **Connessioni** , quindi aprire **Filtro richieste**.

2.  Fare clic su **Modifica impostazioni funzionalità**, quindi impostare quanto segue:

    **Lunghezza massima stringa di query (byte)** = **65534**

    **Lunghezza massima URL (byte)** = **65534**

3.  Esaminare la seguente chiave del Registro di sistema:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Verificare che i seguenti valori siano impostati come voci DWORD:

    Nome: **MaxFieldLength**, con un valore decimale di **65534**

    Nome: **MaxRequestBytes**, con un valore decimale di **65534**

4.  Riavviare il server NDES. Il server è pronto per supportare Connettore di certificati.

## Attività 4: abilitare, installare e configurare Connettore di certificati di Intune per i certificati SCEP e PFX.
In questa attività sarà possibile:

Abilitare il supporto per NDES in Intune

Scaricare, installare e configurare Connettore di certificati nel server NDES

##### Per abilitare il supporto per Connettore di certificati

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com) e fare clic su **Amministrazione** &gt; **Connettore di certificati**.

2.  Fare clic su **Configura Connettore di certificati locale**.

3.  Selezionare **Abilita Connettore di certificati**, quindi fare clic su **OK**.

##### Per scaricare, installare e configurare Connettore di certificati

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com) e quindi fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Connettore di certificati** &gt; **Scarica Connettore di certificati**.

2.  Al termine del download, eseguire il programma di installazione scaricato (**ndesconnectorssetup.exe**):

    -   Per i certificati PFX, eseguire il programma di installazione sul computer che può connettersi all'autorità di certificazione. Scegliere l'opzione di distribuzione PFX, quindi fare clic su Installa. Al termine dell'installazione, procedere alla creazione di un profilo certificato come descritto in [Configure Intune certificate profiles](configure-intune-certificate-profiles.md) (Configurare i profili certificato di Intune).

    -   Per i certificati SCEP, eseguire il programma di installazione in un server Windows Server 2012 R2

    Per l'opzione SCEP, il programma di installazione installa anche il modulo di criteri per NDES e il servizio Web CRP. (Il servizio Web CRP, CertificateRegistrationSvc, viene eseguito come applicazione in IIS).

    > [!NOTE]
    > Quando si installa NDES per la configurazione autonoma di Intune, il servizio CRP viene installato automaticamente con Connettore di certificati. Quando si usa Intune con Configuration Manager, viene installato il punto di registrazione certificati come ruolo separato del sistema del sito.

3.  Quando viene chiesto il certificato client di Connettore di certificati, fare clic su **Seleziona**e selezionare il **certificato di autenticazione client** installato nel server NDES nell'Attività 3.

    Dopo aver selezionato il certificato di autenticazione client, viene visualizzato di nuovo il **certificato client per Connettore di certificati di Microsoft Intune** . Anche se il certificato selezionato non viene visualizzato, fare clic su **Avanti** per visualizzare le proprietà del certificato. Fare clic su **Avanti**, quindi su **Installa**.

4.  Al termine della procedura guidata, prima di chiuderla, fare clic su **Avvia l'interfaccia utente di Connettore di certificati**.

    > [!TIP] Se si chiude la procedura guidata prima di avviare l'interfaccia utente di Connettore di certificati, è possibile riaprirla con il comando seguente:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Nell'interfaccia utente di **Connettore di certificati** :

    Fare clic su **Accedi** e immettere le credenziali di amministratore del servizio di Intune oppure le credenziali di amministratore tenant con autorizzazioni di amministrazione globali.

    Se l'organizzazione usa un server proxy e il proxy è necessario al server NDES per accedere a Internet, fare clic su **Usa server proxy**, quindi specificare il nome del server proxy, la porta e le credenziali dell'account per la connessione.

    Selezionare la scheda **Avanzate** , quindi fornire le credenziali per un account con l'autorizzazione **Rilascio e gestione certificati** sulla CA emittente, quindi fare clic su **Applica**.

    Ora è possibile chiudere l'interfaccia utente di Connettore di certificati.

6.  Aprire il prompt dei comandi e digitare **services.msc**, quindi premere **Invio**, fare clic con il pulsante destro del mouse su **Servizio Intune Connector** e scegliere **Riavvia**

Per confermare che il servizio sia in esecuzione, aprire un browser e immettere il seguente URL, che deve restituire un errore **403** :

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

### Passaggi successivi
A questo punto è possibile configurare i profili certificato come descritto in [Configure Intune certificate profiles](configure-intune-certificate-profiles.md) (Configurare i profili certificato di Intune).


<!--HONumber=May16_HO4-->


