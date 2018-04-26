---
title: Usare i certificati SCEP con Microsoft Intune - Azure | Microsoft Docs
description: Per usare i certificati SCEP in Microsoft Intune, configurare il dominio AD locale, creare un'autorità di certificazione, configurare il server NDES e installare il connettore di certificati di Intune. Quindi creare un profilo certificato SCEP e assegnare il profilo ai gruppi.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dabf8d67b4d0bd7252f306d6b21949cf501eca8d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>Configurare e usare i certificati SCEP con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra come configurare l'infrastruttura e quindi creare e assegnare i profili certificato Simple Certificate Enrollment Protocol (SCEP) con Intune.

## <a name="configure-on-premises-infrastructure"></a>Configurare l'infrastruttura locale

- **Dominio di Active Directory**: tutti i server elencati in questa sezione (tranne il server proxy applicazione Web) devono essere aggiunti al dominio di Active Directory.

- **Autorità di certificazione** (CA): un'autorità di certificazione dell'organizzazione (CA) eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versioni successive. L'opzione CA autonoma non è supportata. Per informazioni dettagliate, vedere [Install the Certification Authority](http://technet.microsoft.com/library/jj125375.aspx) (Installare l'autorità di certificazione).
    Se la CA esegue Windows Server 2008 R2, è necessario [installare l'hotfix di KB2483564](http://support.microsoft.com/kb/2483564/).

- **Server NDES**: nei server che eseguono Windows Server 2012 R2 o versioni successive è necessario installare il servizio Registrazione dispositivi di rete (NDES, Network Device Enrollment Service). Intune non supporta l'uso di NDES se viene eseguito su un server con Enterprise CA. Vedere [Linee guida per il servizio Registrazione dispositivi di rete](http://technet.microsoft.com/library/hh831498.aspx) per istruzioni su come configurare Windows Server 2012 R2 per ospitare il Servizio Registrazione dispositivi di rete.
Il server NDES deve appartenere al dominio che ospita la CA e non trovarsi nello stesso server di questa. Altre informazioni sulla distribuzione del server NDES in una foresta separata, in una rete isolata o in un dominio interno sono disponibili in [Uso di un Modulo criteri con il servizio Registrazione dispositivi di rete](https://technet.microsoft.com/library/dn473016.aspx).

- **Connettore di certificati di Microsoft Intune**: usare il portale di Azure per scaricare il programma di installazione del **Connettore di certificati** (**ndesconnectorssetup.exe**). È quindi possibile eseguire **ndesconnectorssetup.exe** nel server che ospita il ruolo del servizio Registrazione dispositivi di rete (NDES) in cui si vuole installare il Connettore di certificati. 
- **Server proxy applicazione Web**  (facoltativo): usare un server che esegue Windows Server 2012 R2 o versioni successive come server proxy applicazione Web (WAP, Web Application Proxy) . Questa configurazione:
  -  Consente ai dispositivi di ricevere i certificati usando una connessione Internet.
  -  Vale come raccomandazione di sicurezza quando i dispositivi usano la connessione a Internet per ricevere e rinnovare i certificati.

> [!NOTE]
> - Il server che ospita WAP [deve installare un aggiornamento](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) che abilita il supporto per gli URL lunghi usati dal servizio Registrazione dispositivi di rete. Questo aggiornamento è incluso nell' [aggiornamento cumulativo di dicembre 2014](http://support.microsoft.com/kb/3013769)oppure può essere scaricato singolarmente da [KB3011135](http://support.microsoft.com/kb/3011135).
> - Il server WAP deve avere un certificato SSL che corrisponde al nome pubblicato nei client esterni e deve riconoscere come attendibile il certificato SSL usato nel server NDES. Questi certificati consentono al server WAP di chiudere la connessione SSL dai client e creare una nuova connessione SSL nel server NDES.
> 
>   Per informazioni sui certificati per WAP, vedere [Pianificare i certificati](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates).
> 
>   Per informazioni generali sui server WAP, vedere [Utilizzo di Proxy applicazione Web](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="network-requirements"></a>Requisiti di rete

Da Internet alla rete perimetrale, aprire la porta 443 da tutti gli host o da tutti gli indirizzi IP in Internet al server NDES.

Dalla rete perimetrale a una rete attendibile, aprire tutte le porte e consentire tutti i protocolli necessari per l'accesso al dominio per il server NDES appartenente al dominio. Il server NDES deve accedere ai server di certificazione, ai server DNS, ai server di Configuration Manager e ai controller di dominio.

È consigliabile pubblicare il server NDES tramite un proxy, ad esempio [Proxy di applicazione di Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [Proxy di accesso Web](https://technet.microsoft.com/library/dn584107.aspx) o un proxy di terze parti.

### <a name="certificates-and-templates"></a>Certificati e modelli

|Oggetto|Dettagli|
|----------|-----------|
|**Modello di certificato**|Configurare questo modello nella CA emittente.|
|**Certificato di autenticazione client**|Necessario alla CA emittente o alla CA pubblica, questo certificato viene installato nel server NDES.|
|**Certificato di autenticazione server**|Necessario alla CA emittente o alla CA pubblica, questo certificato SSL viene installato e associato in IIS nel server NDES.|
|**Certificato CA radice attendibile**|Questo certificato viene esportato come file con estensione **cer** dalla CA radice o da qualsiasi dispositivo che considera attendibile la CA radice e viene assegnato ai dispositivi tramite il profilo certificato CA attendibile.<br /><br />Viene usato un certificato CA radice attendibile per ogni piattaforma di sistema e lo si associa con ogni profilo del certificato radice attendibile creato.<br /><br />È possibile usare certificati CA radice attendibili aggiuntivi, se necessario. Ad esempio, è possibile farlo per fornire un trust a un'autorità di certificazione che firma i certificati di autenticazione del server per i punti di accesso Wi-Fi.|

### <a name="accounts"></a>Account

|Name|Dettagli|
|--------|-----------|
|**Account di servizio NDES**|Specificare un account utente di dominio da usare come account del servizio NDES.|

## <a name="configure-your-infrastructure"></a>Configurare l'infrastruttura
Prima di configurare i profili certificato, completare le attività seguenti. Le attività seguenti presuppongono la conoscenza di Windows Server 2012 R2 e di Servizi certificati Active Directory (ADCS):

**Passaggio 1**: creare un account del servizio NDES

**Passaggio 2**: configurare i modelli di certificato nell'autorità di certificazione

**Passaggio 3**: configurare i prerequisiti nel server NDES

**Passaggio 4**: configurare NDES per l'uso con Intune

**Passaggio 5**: abilitare, installare e configurare il Connettore di certificati di Intune

#### <a name="step-1---create-an-ndes-service-account"></a>Passaggio 1: creare un account del servizio NDES

Creare un account utente di dominio da usare come account del servizio NDES. Specificare l'account quando si configurano i modelli nella CA emittente prima di installare e configurare NDES. Assicurarsi che l'utente abbia i diritti predefiniti, **accesso locale**, **accesso come servizio** e **accesso come processo batch**. In alcune organizzazioni sono attivi criteri di protezione avanzata che disabilitano tali diritti.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Passaggio 2: configurare i modelli di certificato nell'autorità di certificazione
In questa attività sarà possibile:

- Configurare un modello di certificato per NDES
- Pubblicare il modello di certificato per NDES

##### <a name="configure-the-certification-authority"></a>Configurare l'autorità di certificazione

1. Accedere come amministratore dell'organizzazione.

2. Nell'unità di certificazione emittente, usare lo snap-in Modelli di certificato per creare un nuovo modello personalizzato. In alternativa copiare un modello esistente, quindi aggiornare il modello esistente (ad esempio, il modello Utente) per l'uso con NDES.

   >[!NOTE]
   > Il modello di certificato NDES deve essere basato su un modello di certificato v2 (che include la compatibilità con Windows 2003).

   Il modello deve avere le seguenti configurazioni:

   - Specificare un **Nome visualizzato modello** descrittivo per il modello.

   - In **Nome soggetto** selezionare **Inserisci nella richiesta**. (La sicurezza viene applicata con il modulo dei criteri di Intune per NDES).

   - In **Estensioni** verificare che la **descrizione dei criteri dell'applicazione** includa **Autenticazione client**.

     > [!IMPORTANT]
     > Per i modelli di certificato iOS e macOS, nella scheda **Estensioni** modificare **Utilizzo chiavi** e verificare che l'opzione **Firma come prova dell'origine** non sia selezionata.

   - In **Sicurezza** aggiungere l'account del servizio NDES e assegnare all'account le autorizzazioni di **registrazione** al modello. È necessario che gli amministratori di Intune che creano profili SCEP abbiano i diritti di **lettura** per selezionare il modello durante la creazione dei profili.

     > [!NOTE]
     > Per revocare i certificati, l'account del servizio NDES ha bisogno dei diritti *Rilascio e gestione certificati* per ogni modello di certificato usato da un profilo di certificato.

3. Esaminare il **periodo di validità** nella scheda **Generale** del modello. Per impostazione predefinita, Intune usa il valore configurato nel modello. È tuttavia possibile configurare la CA per consentire al richiedente di immettere un valore diverso, che è poi possibile impostare dalla console di amministrazione di Intune. Per usare sempre il valore nel modello, ignorare il resto del passaggio.

   > [!IMPORTANT]
   > iOS e macOS usano sempre il valore impostato nel modello, indipendentemente dalle altre configurazioni definite.

Esempio di configurazione del modello:

![Modello, scheda di gestione delle richieste](./media/scep_ndes_request_handling.png)

![Modello, scheda relativa al nome soggetto](./media/scep_ndes_subject_name.jpg)

![Modello, scheda della sicurezza](./media/scep_ndes_security.jpg)

![Modello, scheda delle estensioni](./media/scep_ndes_extensions.jpg)

![Modello, scheda dei requisiti di rilascio](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> Per i criteri di applicazione, aggiungere solo i criteri necessari. Verificare le scelte effettuate con gli amministratori della sicurezza.

Configurare la CA in modo che consenta al richiedente di immettere il periodo di validità:

1. Nella CA eseguire i comandi seguenti:
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. Nella CA emittente usare lo snap-in dell'autorità di certificazione per pubblicare il modello di certificato.
   Selezionare il nodo **Modelli di certificato**, fare clic su **Azione** > **Nuovo** > **Modello di certificato da rilasciare**, quindi selezionare il modello creato nel passaggio 2.

3. Verificare che il modello sia stato pubblicato visualizzandolo nella cartella **Modelli di certificato** .

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Passaggio 3: configurare i prerequisiti nel server NDES
In questa attività sarà possibile:

- Aggiungere NDES a Windows Server e configurare IIS per supportare NDES
- Aggiungere l'account del servizio NDES al gruppo IIS_IUSR
- Impostare SPN per l'account del servizio NDES

1. Nel server che ospita NDES, accedere come **amministratore dell'organizzazione**, quindi usare l'[Aggiunta guidata ruoli e funzionalità](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) per installare NDES:

   1. Nella procedura guidata selezionare **Servizi certificati Active Directory** per ottenere l'accesso ai servizi di ruolo AD CS. Selezionare il **servizio Registrazione dispositivi di rete**, deselezionare **Autorità di certificazione**, quindi completare la procedura guidata.

      > [!TIP]
      > In **Stato dell'installazione** non selezionare **Chiudi**. Selezionare invece il collegamento per **configurare i Servizi certificati Active Directory nel server di destinazione**. Si apre la procedura guidata **Configurazione AD CS**, che viene usata per l'attività successiva. Dopo aver aperto Configurazione AD CS, è possibile chiudere la procedura guidata per l'aggiunta di ruoli e funzionalità.

   2. Quando NDES viene aggiunto al server, la procedura guidata installa anche IIS. Verificare che IIS abbia le seguenti configurazioni:

   3. **Server Web** > **Sicurezza** > **Filtro richieste**

   4. **Server Web** > **Sviluppo applicazioni** > **ASP.NET 3.5**. Installando ASP.NET 3.5 viene installato anche .NET Framework 3.5. Quando si installa .NET Framework 3.5, installare la funzionalità di base di **.NET Framework 3.5** e **Attivazione HTTP**.

   5. **Server Web** > **Sviluppo applicazioni** > **ASP.NET 4.5**. Installando ASP.NET 4.5 viene installato anche .NET Framework 4.5. Quando si installa .NET Framework 4.5, installare anche la funzionalità di base **.NET Framework 4.5**, **ASP.NET 4.5** e la funzionalità **Servizi WCF** > **Attivazione HTTP**.

   6. **Strumenti di gestione** > **Compatibilità gestione IIS 6** > **Compatibilità metabase IIS 6**

   7. **Strumenti di gestione** > **Compatibilità gestione IIS 6** > **Compatibilità IIS 6 WMI**

   8. Nel server aggiungere l'account del servizio NDES come membro del gruppo **IIS_IUSR**.

2. Al prompt dei comandi con privilegi elevati, eseguire questo comando per impostare il nome SPN dell'account del servizio NDES:

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    Ad esempio, se il server NDES è denominato **Server01**, il dominio è **Contoso.com**e l'account del servizio è **NDESService**, usare:

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Passaggio 4: configurare NDES per l'uso con Intune
In questa attività sarà possibile:

- Configurare NDES per l'utilizzo con la CA emittente
- Associare il certificato di autenticazione server (SSL) in IIS
- Configurare il filtro richieste in IIS

1. Nel server NDES aprire la procedura guidata Configurazione AD CS, quindi completare gli aggiornamenti seguenti:

    > [!TIP]
    > Se nell'attività precedente è stato selezionato il collegamento, questa procedura guidata è già aperta. In caso contrario, aprire Server Manager per accedere alla configurazione di post-distribuzione per i Servizi certificati Active Directory.

   - In **Servizi ruolo** selezionare **Servizio Registrazione dispositivi di rete**.
   - Nella pagina **Account del servizio per NDES** specificare l'account del servizio NDES.
   - In **CA per NDES** fare clic su **Seleziona**, quindi selezionare la CA emittente in cui è stato configurato il modello di certificato.
   - In **Crittografia per NDES** impostare la lunghezza della chiave in modo da soddisfare i requisiti aziendali.
   - Nella pagina **Conferma** selezionare **Configura** per completare la procedura guidata.

2. Dopo il completamento della procedura guidata, modificare la seguente chiave del Registro di sistema nel server NDES:

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    Per aggiornare questa chiave, identificare il valore **Scopo** del modello del certificato (disponibile nella scheda **Gestione richieste**). Aggiornare la voce del Registro di sistema corrispondente sostituendo i dati esistenti con il nome del modello di certificato (non il nome visualizzato del modello) specificato nell'attività 1. Nella tabella seguente viene eseguito il mapping lo scopo del modello di certificato per i valori del Registro di sistema:

    |Scopo del modello di certificato (nella scheda Gestione richieste)|Valore del Registro di sistema da modificare|Valore visualizzato nella console di amministrazione di Intune per il profilo SCEP|
    |---|---|---|
    |Firma|SignatureTemplate|Firma digitale|
    |Crittografia|EncryptionTemplate|Crittografia chiave|
    |Firma e crittografia|GeneralPurposeTemplate|Crittografia chiave<br/>Firma digitale|

    Ad esempio, se lo scopo del modello di certificato è **Crittografia**, modificare il valore **EncryptionTemplate** in modo che corrisponda al nome del modello di certificato.

3. Il server NDES riceve URL (query) lunghi, che richiedono l'aggiunta di due voci del Registro di sistema:


   |                        Percorso                        |      Valore      | Tipo  |      Dati       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (decimale) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (decimale) |


4. In IIS Manager selezionare **Sito Web predefinito** > **Filtro richieste** > **Modifica impostazioni funzionalità**. Impostare **Lunghezza massima URL** e **Lunghezza massima stringa di query** su *65534*, come visualizzato di seguito:

    ![Lunghezza massima URL IIS e lunghezza query](./media/SCEP_IIS_max_URL.png)

5. Riavviare il server. L'esecuzione di **iisreset** nel server non è sufficiente per finalizzare le modifiche.
6. Passare a `http://*FQDN*/certsrv/mscep/mscep.dll`. Viene visualizzata una pagina NDES simile alla seguente:

    ![Test NDES](./media/SCEP_NDES_URL.png)

    Se viene visualizzato l'errore **503 - Servizio non disponibile**, controllare nel visualizzatore eventi. È probabile che il pool di applicazioni si sia arrestato perché l'utente NDES non dispone di un diritto. Tali diritti sono descritti nell'attività 1.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>Installare e associare i certificati nel server NDES

1. Nel server NDES richiedere e installare un certificato **autenticazione server** dalla CA interna o dalla CA pubblica. Quindi associare questo certificato SSL in IIS.

    > [!TIP]
    > Dopo aver associato il certificato SSL in IIS, installare un certificato di autenticazione client. Questo certificato può essere emesso da qualsiasi CA considerata attendibile dal server NDES. Sebbene non sia una procedura consigliata, è possibile usare lo stesso certificato per l'autenticazione server e client, a condizione che il certificato abbia entrambi gli EKU. Esaminare i seguenti passaggi per informazioni su questi certificati di autenticazione.

   1. Dopo avere ottenuto il certificato di autenticazione del server, aprire **IIS Manager** e selezionare **Sito Web predefinito**. Nel riquadro **Azioni** selezionare **Binding**.

   2. Selezionare **Aggiungi**, impostare **Tipo** su **https**, quindi verificare che la porta sia **443**. Per la configurazione autonoma di Intune è supportata solo la porta 443.

   3. Per **Certificato SSL** specificare il certificato di autenticazione server.

      > [!NOTE]
      > Se il server NDES usa un nome esterno e uno interno per un unico indirizzo di rete, il certificato di autenticazione server deve avere:
      > - Un **Nome soggetto** con un nome server pubblico esterno
      > - Un **Nome alternativo soggetto** che include il nome server interno

2. Nel server NDES, richiedere e installare un **certificato di autenticazione client** dalla CA interna o pubblica. Può essere lo stesso certificato del certificato di autenticazione server, se il certificato ha entrambe le funzionalità.

    Il certificato di autenticazione client deve avere le seguenti proprietà:

    - **Utilizzo chiavi avanzato**: questo valore deve includere **Autenticazione client**.

    - **Nome soggetto**: deve essere uguale al nome DNS del server in cui si installa il certificato (server NDES).

##### <a name="configure-iis-request-filtering"></a>Configurare il filtro di richieste IIS

1. Nel server NDES aprire **Gestione IIS**, selezionare **Sito Web predefinito** nel riquadro **Connessioni** e aprire **Filtro richieste**.

2. Selezionare **Modifica impostazioni funzionalità**, quindi impostare i valori seguenti:

    - **Lunghezza massima stringa di query (byte)** = **65534**
    - **Lunghezza massima URL (byte)** = **65534**

3. Esaminare la seguente chiave del Registro di sistema:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    Verificare che i seguenti valori siano impostati come voci DWORD:

    - Nome: **MaxFieldLength**, con un valore decimale di **65534**
    - Nome: **MaxRequestBytes**, con un valore decimale di **65534**

4. Riavviare il server NDES. Il server è pronto per supportare Connettore di certificati.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Passaggio 5: abilitare, installare e configurare il Connettore di certificati di Intune
In questa attività sarà possibile:

- Abilitare il supporto per NDES in Intune.
- Scaricare, installare e configurare il Connettore di certificati nel server che ospita il ruolo del servizio Registrazione dispositivi di rete (NDES) nell'ambiente in uso. Per aumentare la scala dell'implementazione di NDES nell'organizzazione, è possibile installare più server NDES con un Connettore di certificati di Microsoft Intune in ogni server NDES.

##### <a name="download-install-and-configure-the-certificate-connector"></a>Scaricare, installare e configurare il connettore di certificati
![Download connettore](./media/certificates-download-connector.png)

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione dispositivo** e quindi selezionare **Autorità di certificazione**.
4. Selezionare **Aggiungi** e quindi **Scaricare il file del connettore**. Salvare il file scaricato in un percorso a cui è possibile accedere dal server in cui verrà installato.
5. Al completamento del download, eseguire il programma di installazione scaricato (**ndesconnectorssetup.exe**) nel server che ospita il ruolo del servizio Registrazione dispositivi di rete (NDES). Il programma di installazione installa anche il modulo di criteri per NDES e il servizio Web CRP. (Il servizio Web CRP, CertificateRegistrationSvc, viene eseguito come applicazione in IIS).

    > [!NOTE]
    > Quando si installa NDES per la configurazione autonoma di Intune, il servizio CRP viene installato automaticamente con Connettore di certificati. Quando si usa Intune con Configuration Manager, viene installato il punto di registrazione certificati come ruolo separato del sistema del sito.

6. Quando viene chiesto il certificato client di Connettore di certificati, scegliere **Seleziona** e selezionare il certificato di **autenticazione client** installato nel server NDES nell'Attività 3.

    Dopo aver selezionato il certificato di autenticazione client, viene visualizzato di nuovo il **certificato client per Connettore di certificati di Microsoft Intune** . Anche se il certificato selezionato non viene visualizzato, selezionare **Avanti** per visualizzare le proprietà del certificato. Selezionare **Avanti** e quindi **Installa**.

7. Al termine della procedura guidata, prima di chiuderla, fare clic su **Launch the Certificate Connector UI** (Avvia l'interfaccia utente di Connettore di certificati).

    > [!TIP]
    > Se si chiude la procedura guidata prima di avviare l'interfaccia utente di Connettore di certificati, è possibile riaprirla con il comando seguente:
    >
    > <install_Path>\NDESConnectorUI\NDESConnectorUI.exe

8. Nell'interfaccia utente di **Connettore di certificati** :

    Selezionare **Accedi** e immettere le credenziali di amministratore del servizio di Intune oppure le credenziali di amministratore tenant con le autorizzazioni di amministrazione globali.

    > [!IMPORTANT]
    > All'account utente deve essere assegnata una licenza di Intune valida. Se l'account utente non ha una licenza di Intune valida, l'esecuzione di NDESConnectorUI.exe non riesce.

    Se l'organizzazione usa un server proxy e il proxy è necessario al server NDES per accedere a Internet, selezionare **Usa server proxy**, quindi specificare il nome del server proxy, la porta e le credenziali dell'account per la connessione.

    Selezionare la scheda **Avanzate** e quindi immettere le credenziali per un account con l'autorizzazione **Rilascio e gestione certificati** sulla CA emittente. Scegliere **Applica** per applicare le modifiche.

    Ora è possibile chiudere l'interfaccia utente di Connettore di certificati.

9. Aprire un prompt dei comandi, immettere **services.msc**, quindi premere **INVIO**. Fare clic con il pulsante destro del mouse su **Servizio Intune Connector** e scegliere **Riavvia**.

Per confermare che il servizio sia in esecuzione, aprire un browser e immettere il seguente URL. L'operazione dovrebbe restituire un errore **403**:

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

## <a name="create-a-scep-certificate-profile"></a>Creare un profilo certificato SCEP

1. Nel portale di Azure, aprire Microsoft Intune.
2. Selezionare **Configurazione del dispositivo**, scegliere **Profili** e quindi selezionare **Crea profilo**.
3. Immettere **Nome** e **Descrizione** per il profilo certificato SCEP.
4. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo per questo certificato SCEP. Attualmente, è possibile selezionare una delle piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:
   - **Android**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 e versioni successive**
   - **Windows 10 e versioni successive**
5. Nell'elenco a discesa **Tipo di profilo** selezionare **Certificato SCEP**.
6. Nel riquadro **Certificato SCEP** configurare le impostazioni seguenti:

   - **Periodo di validità del certificato**: se nella CA emittente è stato eseguito il comando `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE`, che consente un periodo di validità personalizzato, è possibile specificare la quantità di tempo rimanente prima della scadenza del certificato.<br>È possibile immettere un valore inferiore, ma non superiore, al periodo di validità presente nel modello di certificato. Se ad esempio il periodo di validità del certificato nel modello di certificato è di due anni, è possibile immettere un valore di un anno ma non un valore di cinque anni. Inoltre, il valore deve essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente. 
   - **Provider di archiviazione chiavi (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): specificare dove viene archiviata la chiave per il certificato. Scegliere tra uno dei seguenti valori:
     - **Registra nel provider di archiviazione chiavi Trusted Platform Module (TPM) se presente, altrimenti nel provider di archiviazione chiavi software**
     - **Registra nel provider di archiviazione chiavi Trusted Platform Module (TPM) oppure genera errore**
     - **Registra in Passport oppure genera errore (Windows 10 e versioni successive)**
     - **Registra nel provider di archiviazione chiavi software**

   - **Formato nome soggetto**: selezionare nell'elenco la modalità con la quale Intune crea automaticamente il nome soggetto nella richiesta certificato. Se il certificato è per un utente, è anche possibile includere l'indirizzo di posta elettronica dell'utente nel nome del soggetto. Scegliere tra:
     - **Non configurato**
     - **Nome comune**
     - **Nome comune incluso l'indirizzo di posta elettronica**
     - **Nome comune come indirizzo di posta elettronica**
     - **IMEI (International Mobile Equipment Identity)**
     - **Numero di serie**
     - **Personalizzato**: quando si seleziona questa opzione, viene visualizzato un altro campo a discesa. Usare questo campo per immettere un formato di nome soggetto personalizzato. Le due variabili supportate per il nome personalizzato sono **CN (Nome comune)** ed **E (Posta elettronica)**. **CN (Nome comune)** può essere impostata su una delle variabili seguenti:
       - **CN={{UserName}}**: nome principale dell'utente, ad esempio janedoe@contoso.com
       - **CN={{AAD_Device_ID}}**: ID assegnato quando si registra un dispositivo in Azure Active Directory (AD). Questo ID è in genere usato per l'autenticazione con Azure AD.
       - **CN={{SERIALNUMBER}}**: numero di serie (SN) unico usato in genere dal produttore per identificare un dispositivo
       - **CN={{IMEINumber}}**: numero unico IMEI (International Mobile Equipment Identity) usato per identificare un telefono cellulare
       - **CN={{OnPrem_Distinguished_Name}}**: sequenza di nomi distinti relativi separati da virgole, ad esempio `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

       > [!TIP]
       > Usare la variabile `{{OnPrem_Distinguished_Name}}`, assicurarsi di sincronizzare l'attributo utente `onpremisesdistingishedname` usando [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

       Usando una combinazione di una o più di queste variabili e stringhe statiche è possibile creare un formato di nome soggetto personalizzato, ad esempio: **CN={{UserName}},E={{EmailAddress}},OU=Cellulare,O=Settore Finanze,L=Redmond,ST=Washington,C=USA**. <br/> In questo esempio è stato creato un formato di nome soggetto che, oltre alle variabili CN ed E, usa stringhe per i valori Unità organizzativa, Organizzazione, Località, Stato e Paese. L'argomento [Funzione CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) visualizza questa funzione e le relative stringhe supportate.




- **Nome alternativo soggetto**: specificare in che modo Intune crea automaticamente i valori per il nome alternativo soggetto (SAN) nella richiesta certificato. Se ad esempio si seleziona un tipo di certificato utente, è possibile includere il nome dell'entità utente (UPN) nel nome alternativo soggetto. Se il certificato client viene usato per eseguire l'autenticazione in un server dei criteri di rete, è necessario impostare il nome alternativo oggetto sul nome dell'entità utente.
- **Utilizzo chiavi**: specificare le opzioni d'uso della chiave per il certificato. Le opzioni disponibili sono:
  - **Crittografia chiave**: consentire lo scambio di chiavi solo quando la chiave viene crittografata.
  - **Firma digitale**: consentire lo scambio di chiavi soltanto se una firma digitale consente di proteggere la chiave.
- **Dimensioni chiave (bit)**: selezionare il numero di bit contenuti nella chiave.
- **Algoritmo hash** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): selezionare uno dei tipi di algoritmo hash disponibili da usare con il certificato. Selezionare il livello di sicurezza più avanzato supportato dai dispositivi che verranno connessi.
- **Certificato radice**: scegliere un profilo del certificato radice della CA già configurato e assegnato all'utente o al dispositivo. Questo certificato CA deve essere il certificato radice per l'autorità di certificazione che rilascia il certificato che si sta configurando in questo profilo certificato.
- **Utilizzo chiavi avanzato**: scegliere **Aggiungi** per aggiungere valori per lo scopo designato del certificato. Nella maggior parte dei casi il certificato richiede l' **Autenticazione Client** in modo che l'utente o il dispositivo possa eseguire l'autenticazione in un server. È comunque possibile aggiungere altri utilizzi di chiavi secondo necessità.
- **Impostazioni di registrazione**
  - **Soglia di rinnovo (%)**: specificare la percentuale di durata residua del certificato prima che il dispositivo ne richieda il rinnovo.
  - **URL server SCEP**: specificare uno o più URL per i server NDES che emettono certificati tramite SCEP.
  - Selezionare **OK**, quindi **Crea** per creare il profilo.

Il profilo viene creato e visualizzato nel riquadro dell'elenco dei profili.

## <a name="assign-the-certificate-profile"></a>Assegnare il profilo certificato

Prima di assegnare i profili certificato ai gruppi, considerare quanto segue:

- Quando si assegnano i profili certificato ai gruppi, il file del certificato dal profilo certificato CA attendibile viene installato nel dispositivo. Il dispositivo usa il profilo certificato SCEP per creare una richiesta certificato.
- I profili certificato vengono installati solo nei dispositivi che eseguono la piattaforma usata durante la creazione del profilo.
- È possibile assegnare profili certificato alle raccolte di utenti o di dispositivi.
- Per pubblicare rapidamente un certificato in un dispositivo dopo la registrazione del dispositivo, assegnare il profilo certificato a un gruppo di utenti invece che a un gruppo di dispositivi. Se si assegna il profilo certificato a un gruppo di dispositivi, è necessario eseguire una registrazione completa dei dispositivi prima che questi ricevano i criteri.
- Sebbene ogni profilo venga assegnato separatamente, è anche necessario assegnare la CA radice attendibile e il profilo SCEP o PKCS. In caso contrario, i criteri di certificato SCEP o PKCS hanno esito negativo.

    > [!NOTE]
    > Per iOS, se si distribuiscono più profili di risorse che usano lo stesso profilo di certificato, è possibile che vengano visualizzate più copie del certificato nel profilo di gestione.
    
Per informazioni su come assegnare profili, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).
