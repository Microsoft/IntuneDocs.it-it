---
title: Configurare l'infrastruttura per supportare i profili di certificato SCEP con Microsoft Intune - Azure | Microsoft Docs
description: Per usare SCEP in Microsoft Intune, configurare il dominio AD locale, creare un'autorità di certificazione, configurare il server del servizio Registrazione dispositivi di rete e installare Connettore di certificati di Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86640c831e8836a72ad5a0a7d5023ff7d836a43a
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801566"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Configurare l'infrastruttura per il supporto di SCEP con Intune

Intune supporta l'uso di SCEP (Simple Certificate Enrollment Protocol) per [autenticare le connessioni alle app e alle risorse aziendali](certificates-configure.md). SCEP usa il certificato dell'autorità di certificazione (CA) per proteggere lo scambio di messaggi per la richiesta di firma del certificato. Quando l'infrastruttura supporta SCEP, è possibile usare i profili di *certificato SCEP* di Intune (un tipo di profilo di dispositivo in Intune) per distribuire i certificati nei dispositivi. Connettore di certificati di Microsoft Intune è necessario per usare i profili di certificato SCEP con Intune quando si usa un'autorità di certificazione di Servizi certificati Active Directory. Il connettore non è obbligatorio quando si usano [autorità di certificazione di terze parti](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration). 

Le informazioni contenute in questo articolo consentono di configurare l'infrastruttura per il supporto di SCEP quando si usa Servizi certificati Active Directory. Dopo la configurazione dell'infrastruttura, è possibile [creare e distribuire profili di certificato SCEP](certificates-profile-scep.md) con Intune.

> [!TIP]
> Intune supporta anche l'uso di [certificati PKCS (Public Key Cryptography Standards) #12](certficates-pfx-configure.md).

## <a name="prerequisites-for-using-scep-for-certificates"></a>Prerequisiti per l'uso di SCEP per i certificati

Prima di procedere, assicurarsi di aver [creato e distribuito un profilo di *certificato attendibile*](certificates-configure.md#export-the-trusted-root-ca-certificate) nei dispositivi che useranno i profili di certificato SCEP. I profili di certificato SCEP fanno riferimento direttamente al profilo di certificato attendibile usato per il provisioning dei dispositivi con un certificato CA radice attendibile.

### <a name="servers-and-server-roles"></a>Server e ruoli del server

L'infrastruttura locale seguente deve essere eseguita su server aggiunti a un dominio in Active Directory, ad eccezione del server proxy applicazione Web.

- **Autorità di certificazione** - Usare un'autorità di certificazione (CA) dell'organizzazione (enterprise) di Servizi certificati Microsoft Active Directory eseguita in un'edizione Enterprise di Windows Server 2008 R2 con Service Pack 1 o versioni successive. La versione di Windows Server in uso deve essere supportata da Microsoft. L'opzione CA autonoma non è supportata. Per altre informazioni, vedere [Installare l'autorità di certificazione](https://technet.microsoft.com/library/jj125375.aspx). Se la CA esegue Windows Server 2008 R2 SP1, è necessario [installare l'hotfix da KB2483564](https://support.microsoft.com/kb/2483564/).

- **Ruolo del server Servizio Registrazione dispositivi di rete** - È necessario configurare un ruolo del server Servizio Registrazione dispositivi di rete (NDES) in Windows Server 2012 R2 o versione successiva. In una sezione successiva di questo articolo viene illustrata in dettaglio l'[installazione del servizio Registrazione dispositivi di rete](#set-up-ndes).

  - Il server che ospita il servizio Registrazione dispositivi di rete deve essere aggiunto a un dominio e incluso stessa foresta della CA globale (enterprise).
  - Non è possibile usare il servizio Registrazione dispositivi di rete installato nel server che ospita la CA globale (enterprise).
  - Connettore di certificati di Microsoft Intune verrà installato nello stesso server che ospita il servizio Registrazione dispositivi di rete.

  Per altre informazioni sul servizio Registrazione dispositivi di rete, vedere [Linee guida per il servizio Registrazione dispositivi di rete](https://technet.microsoft.com/library/hh831498.aspx) nella documentazione di Windows Server e [Uso di un Modulo criteri con il servizio Registrazione dispositivi di rete](https://technet.microsoft.com/library/dn473016.aspx).

- **Connettore di certificati di Microsoft Intune** - Connettore di certificati di Microsoft Intune è necessario per usare i profili di certificato SCEP con Intune. Questo articolo include istruzioni per l'[installazione di questo connettore](#install-the-intune-certificate-connector).

  Il connettore supporta la modalità FIPS (Federal Information Processing Standard). FIPS non è obbligatorio, ma quando è abilitato è possibile emettere e revocare i certificati.
  - Il connettore deve essere eseguito nello stesso server del ruolo del server Servizio Registrazione dispositivi di rete, ovvero un server che esegue Windows Server 2012 R2 o versione successiva.
  - .NET Framework 4.5 è richiesto dal connettore ed è incluso automaticamente in Windows Server 2012 R2.
  - La sicurezza avanzata di Internet Explorer [deve essere disabilitata nel server che ospita il servizio Registrazione dispositivi di rete](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) e Connettore di certificati di Microsoft Intune.

L'infrastruttura locale seguente è facoltativa:

Per consentire ai dispositivi su Internet di ottenere i certificati, è necessario pubblicare l'URL del servizio Registrazione dispositivi di rete esternamente alla rete aziendale. È possibile usare Azure AD Application Proxy, il server proxy applicazione Web o un altro proxy inverso.

- **Azure AD Application Proxy** (facoltativo) - È possibile usare Azure AD Application Proxy invece di un server proxy applicazione Web dedicato per pubblicare l'URL del servizio Registrazione dispositivi di rete in Internet. In questo modo, sia i dispositivi Intranet che i dispositivi con connessione Internet possono ottenere i certificati. Per altre informazioni, vedere [Come fornire l'accesso remoto sicuro alle applicazioni locali](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

- **Server proxy applicazione Web**  (facoltativo) - Usare un server che esegue Windows Server 2012 R2 o versioni successive come server proxy applicazione Web per pubblicare l'URL del servizio Registrazione dispositivi di rete in Internet.  In questo modo, sia i dispositivi Intranet che i dispositivi con connessione Internet possono ottenere i certificati.

  Il server che ospita WAP [deve installare un aggiornamento](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) che abilita il supporto per gli URL lunghi usati dal servizio Registrazione dispositivi di rete. Questo aggiornamento è incluso nell' [aggiornamento cumulativo di dicembre 2014](https://support.microsoft.com/kb/3013769)oppure può essere scaricato singolarmente da [KB3011135](https://support.microsoft.com/kb/3011135).

  Il server proxy applicazione Web deve avere un certificato SSL che corrisponde al nome pubblicato nei client esterni e deve riconoscere come attendibile il certificato SSL usato nel computer che ospita il servizio Registrazione dispositivi di rete NDES. Questi certificati consentono al server proxy applicazione Web di chiudere la connessione SSL dai client e creare una nuova connessione SSL al servizio Registrazione dispositivi di rete.

  Per altre informazioni, vedere [Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) (Pianificare i certificati per WAP) e le [informazioni generali sui server WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="accounts"></a>Account

- **Account del servizio Registrazione dispositivi di rete** - Prima di configurare il servizio Registrazione dispositivi di rete, identificare un account utente di dominio da usare come account del servizio Registrazione dispositivi di rete. L'account viene specificato quando si configurano i modelli nella CA emittente prima di installare e configurare il servizio Registrazione dispositivi di rete.

  Questo account deve avere i diritti seguenti nel server che ospita il servizio Registrazione dispositivi di rete:

  - **Accesso locale**
  - **Accesso come servizio**
  - **Accesso come processo batch**

  Per altre informazioni, vedere [Creare un account utente di dominio che funga da account di servizio per il servizio Registrazione dispositivi di rete](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account).

- **Accesso al computer che ospita il servizio Registrazione dispositivi di rete** - Sarà necessario un account utente di dominio con le autorizzazioni per installare e configurare i ruoli del server Windows nel server in cui si installa il servizio Registrazione dispositivi di rete.

- **Accesso all'autorità di certificazione** - Sarà necessario un account utente di dominio con i diritti per gestire l'autorità di certificazione.

### <a name="network-requirements"></a>Requisiti di rete

È consigliabile pubblicare il servizio Registrazione dispositivi di rete tramite un proxy inverso, ad esempio [Azure AD Application Proxy, proxy di accesso Web](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/) o un proxy di terze parti. Se non si usa un proxy inverso, consentire il traffico TCP sulla porta 443 da tutti gli host e gli indirizzi IP su Internet al servizio Registrazione dispositivi di rete.

Consentire tutte le porte e i protocolli necessari per la comunicazione tra il servizio Registrazione dispositivi di rete e qualsiasi infrastruttura di supporto nell'ambiente in uso. Ad esempio, il computer che ospita il servizio Registrazione dispositivi di rete deve comunicare con l'autorità di certificazione, i server DNS, i controller di dominio e a volte anche con altri servizi o server all'interno dell'ambiente, ad esempio Configuration Manager.

### <a name="certificates-and-templates"></a>Certificati e modelli

Quando si usa SCEP, vengono usati i certificati e i modelli seguenti.

|Oggetto    |Dettagli    |
|----------|-----------|
|**Modello di certificato SCEP**         |Modello che verrà configurato nella CA emittente usata per soddisfare le richieste SCEP dei dispositivi. |
|**Certificato di autenticazione client** |Richiesto dalla CA emittente o dalla CA pubblica.<br /> Questo certificato viene installato nel computer che ospita il servizio Registrazione dispositivi di rete e viene usato da Connettore di certificati di Microsoft Intune.<br /> Se per il certificato sono impostati gli utilizzi della chiave per l'*autenticazione client* e *server* (**Utilizzo chiavi avanzato**) nel modello di CA usato per emettere il certificato. È quindi possibile usare lo stesso certificato per l'autenticazione server e client. |
|**Certificato di autenticazione server** |Certificato del server Web richiesto dalla CA emittente o dalla CA pubblica.<br /> Questo certificato SSL viene installato e associato in IIS nel computer che ospita il servizio Registrazione dispositivi di rete.<br />Se per il certificato sono impostati gli utilizzi della chiave per l'*autenticazione client* e *server* (**Utilizzo chiavi avanzato**) nel modello di CA usato per emettere il certificato. È quindi possibile usare lo stesso certificato per l'autenticazione server e client. |
|**Certificato CA radice attendibile**       |Per usare un profilo di certificato SCEP, i dispositivi devono considerare attendibile l'autorità di certificazione (CA) radice attendibile. Usare un *profilo di certificato attendibile* in Intune per eseguire il provisioning del certificato CA radice attendibile per utenti e dispositivi. <br/><br/> **-** Usare un singolo certificato CA radice attendibile per ogni piattaforma di sistema operativo e associare tale certificato a ogni profilo di certificato radice attendibile creato. <br /><br /> **-** È possibile usare certificati CA radice attendibili aggiuntivi, se necessario. Ad esempio, è possibile usare certificati aggiuntivi per fornire un trust a un'autorità di certificazione che firma i certificati di autenticazione del server per i punti di accesso Wi-Fi. Creare certificati CA radice attendibili aggiuntivi per le CA emittenti.  Nel profilo di certificato SCEP creato in Intune, assicurarsi di specificare il profilo CA radice attendibile per la CA emittente.<br/><br/> Per informazioni sul profilo di certificato attendibile, vedere [Esportare il certificato CA radice attendibile](certificates-configure.md#export-the-trusted-root-ca-certificate) e [Creare profili di certificato attendibili](certificates-configure.md#create-trusted-certificate-profiles) in *Usare i certificati per l'autenticazione in Intune*. |

## <a name="configure-the-certification-authority"></a>Configurare l'autorità di certificazione

Le sezioni seguenti descrivono come:

- Configurare e pubblicare il modello richiesto per il servizio Registrazione dispositivi di rete
- Impostare le autorizzazioni necessarie per la revoca dei certificati.

Per le informazioni nelle sezioni seguenti è richiesta la conoscenza di Windows Server 2012 R2 o versioni successive e dei Servizi certificati Active Directory.

### <a name="access-your-issuing-ca"></a>Accedere alla CA emittente

1. Accedere alla CA emittente con un account di dominio con diritti sufficienti per gestire la CA.

2. Aprire la console MMC (Microsoft Management Console) Autorità di certificazione. **Eseguire** 'certsrv.msc' oppure in **Server Manager** fare clic su **Strumenti** e quindi fare clic su **Autorità di certificazione**.

3. Selezionare il nodo **Modelli di certificato**, fare clic su **Azione** > **Gestisci**.

### <a name="create-the-scep-certificate-template"></a>Creare il modello di certificato SCEP

1. Creare un modello di certificato v2 (con compatibilità con Windows 2003) da usare come modello di certificato SCEP. È possibile scegliere le opzioni seguenti:

   - Usare lo snap-in *Modelli di certificato* per creare un nuovo modello personalizzato.
   - Copiare un modello esistente (ad esempio, il modello Utente) e quindi aggiornare la copia da usare come modello per il servizio Registrazione dispositivi di rete.

2. Configurare le impostazioni seguenti nelle schede specificate del modello:

   - **Generale**:

     - Deselezionare **Pubblica certificato in Active Directory**.
     - Specificare un **Nome visualizzato modello** descrittivo in modo da poter identificare questo modello in un secondo momento.

   - **Nome soggetto**:

     - Selezionare **Inserisci nella richiesta**. La sicurezza viene applicata dal modulo dei criteri di Intune per il servizio Registrazione dispositivi di rete.

       ![Modello, scheda relativa al nome soggetto](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)

   - **Estensioni**:

     - Assicurarsi che **Descrizione di Criteri di applicazione** includa **Autenticazione client**.

       > [!IMPORTANT]
       > Aggiungere solo i criteri di applicazione necessari. Verificare le scelte effettuate con gli amministratori della sicurezza.

     - Per i modelli di certificato iOS e macOS, modificare anche **Utilizzo chiavi** e assicurarsi che l'opzione **Firma come prova dell'origine** non sia selezionata.

     ![Modello, scheda delle estensioni](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **Sicurezza**:

     - Aggiungere l'**account del servizio Registrazione dispositivi di rete**. Questo account richiede le autorizzazioni **Lettura** e **Registrazione** per questo modello.

     - Aggiungere altri account per gli amministratori di Intune che creeranno profili SCEP. Questi account richiedono autorizzazioni **Lettura** per il modello per consentire a questi amministratori di passare a questo modello durante la creazione di profili SCEP.

     ![Modello, scheda della sicurezza](./media/certificates-scep-configure/scep-ndes-security.jpg)

   - **Gestione richieste**:

     L'immagine seguente è un esempio. La configurazione potrebbe variare.  

     ![Modello, scheda di gestione delle richieste](./media/certificates-scep-configure/scep-ndes-request-handling.png)

   - **Requisiti di rilascio**:

     L'immagine seguente è un esempio. La configurazione potrebbe variare.

     ![Modello, scheda dei requisiti di rilascio](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)

3. Salvare il modello di certificato.

### <a name="create-the-client-certificate-template"></a>Creare il modello di certificato client

Connettore di certificati di Intune richiede un certificato con l'utilizzo chiavi avanzato *Autenticazione client* e il nome soggetto uguale al nome di dominio completo (FQDN) del computer in cui è installato il connettore. È necessario un modello con le proprietà seguenti:

- **Estensioni** > **Criteri di applicazione** deve contenere **Autenticazione client**
- **Nome soggetto** > **Inserisci nella richiesta**.

Se è già disponibile un modello che include queste proprietà, è possibile riutilizzarlo. In caso contrario, creare un nuovo modello duplicandone uno esistente o creando un modello personalizzato.

### <a name="create-the-server-certificate-template"></a>Creare il modello di certificato server

Le comunicazioni tra i dispositivi gestiti e IIS nel server del servizio Registrazione dispositivi di rete usano HTTPS, che richiede l'uso di un certificato. Per emettere questo certificato, è possibile usare il modello di certificato **Server Web**. In alternativa, se si preferisce un modello dedicato, sono necessarie le proprietà seguenti:

- **Estensioni** > **Criteri di applicazione** deve contenere **Autenticazione server**
- **Nome soggetto** > **Inserisci nella richiesta**.

> [!NOTE]
> Se è disponibile un certificato che soddisfa entrambi i requisiti dai modelli di certificato client e server, è possibile usare un solo certificato sia per IIS che per Connettore di certificati di Intune.

### <a name="grant-permissions-for-certificate-revocation"></a>Concedere le autorizzazioni per la revoca dei certificati

Affinché Intune sia in grado di revocare i certificati non più richiesti, è necessario concedere le autorizzazioni nell'autorità di certificazione.

In Connettore di certificati di Intune è possibile usare l'**account di sistema** del server del servizio Registrazione dispositivi di rete o un account specifico, ad esempio l'**account del servizio Registrazione dispositivi di rete**.

1. Nella console dell'autorità di certificazione fare clic con il pulsante destro del mouse sul nome della CA e scegliere **Proprietà**.

2. Nella scheda **Sicurezza** fare clic su **Aggiungi**.

3. Concedere l'autorizzazione **Rilascio e gestione certificati**:

   - Se si sceglie di usare l'**account di sistema** del server del servizio Registrazione dispositivi di rete, specificare le autorizzazioni per il server del servizio Registrazione dispositivi di rete.
   - Se si sceglie di usare l'**account del servizio Registrazione dispositivi di rete**, specificare invece le autorizzazioni per tale account.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>Modificare il periodo di validità del modello di certificato

È facoltativo modificare il periodo di validità del modello di certificato.  

Dopo aver [creato il modello di certificato SCEP](#create-the-scep-certificate-template), è possibile modificare il modello per verificare il **periodo di validità** nella scheda **Generale**.

Per impostazione predefinita, Intune usa il valore configurato nel modello. È tuttavia possibile configurare la CA per consentire al richiedente di immettere un valore diverso, che può essere impostato dalla console di Intune.

> [!IMPORTANT]
> Per iOS e macOS, usare sempre un valore impostato nel modello.

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Per configurare un valore che può essere impostato dalla console di Intune

1. Nella CA eseguire i comandi seguenti:

   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   -**net stop certsvc**
   -**net start certsvc**

2. Nella CA emittente usare lo snap-in dell'autorità di certificazione per pubblicare il modello di certificato. Selezionare il nodo **Modelli di certificato**, selezionare **Azione** > **Nuovo** > **Modello di certificato da rilasciare** e quindi selezionare il modello di certificato creato nella sezione precedente.

3. Verificare che il modello sia stato pubblicato visualizzandolo nella cartella **Modelli di certificato**.

## <a name="set-up-ndes"></a>Configurare il servizio Registrazione dispositivi di rete

Le procedure seguenti consentono di configurare il servizio Registrazione dispositivi di rete (NDES) per l'uso con Intune. Per altre informazioni, vedere [Linee guida per il servizio Registrazione dispositivi di rete](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11)).

### <a name="install-the-ndes-service"></a>Installare il servizio Registrazione dispositivi di rete

1. Nel server che ospiterà il servizio Registrazione dispositivi di rete, accedere come **amministratore dell'organizzazione**, quindi usare l'[Aggiunta guidata ruoli e funzionalità](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) per installare il servizio Registrazione dispositivi di rete:

   1. Nella procedura guidata selezionare **Servizi certificati Active Directory** per ottenere l'accesso ai servizi di ruolo AD CS. Selezionare **Servizio Registrazione dispositivi di rete**, deselezionare **Autorità di certificazione** e quindi completare la procedura guidata.

      > [!TIP]
      > In **Stato dell'installazione** non selezionare **Chiudi**. Selezionare invece il collegamento per **configurare i Servizi certificati Active Directory nel server di destinazione**. Verrà visualizzata la procedura guidata **Configurazione Servizi certificati Active Directory**, che verrà usata per la procedura successiva di questo articolo *Configurare il servizio Registrazione dispositivi di rete*. Dopo aver aperto Configurazione AD CS, è possibile chiudere la procedura guidata per l'aggiunta di ruoli e funzionalità.

   2. Quando NDES viene aggiunto al server, la procedura guidata installa anche IIS. Verificare che IIS abbia le configurazioni seguenti:

      - **Server Web** > **Sicurezza** > **Filtro richieste**
      - **Server Web** > **Sviluppo applicazioni** > **ASP.NET 3.5**

        Installando ASP.NET 3.5 viene installato anche .NET Framework 3.5. Quando si installa .NET Framework 3.5, installare la funzionalità di base di **.NET Framework 3.5** e **Attivazione HTTP**.

      - **Server Web** > **Sviluppo applicazioni** > **ASP.NET 4.5**

        Installando ASP.NET 4.5 viene installato anche .NET Framework 4.5. Quando si installa .NET Framework 4.5, installare anche la funzionalità di base **.NET Framework 4.5**, **ASP.NET 4.5** e la funzionalità **Servizi WCF** > **Attivazione HTTP**.

      - **Strumenti di gestione** > **Compatibilità gestione IIS 6** > **Compatibilità metabase IIS 6**
      - **Strumenti di gestione** > **Compatibilità gestione IIS 6** > **Compatibilità IIS 6 WMI**
      - Nel server aggiungere l'account del servizio Registrazione dispositivi di rete come membro del gruppo locale **IIS_IUSR**.

2. Nel computer che ospita il servizio Registrazione dispositivi di rete, eseguire il comando seguente in un prompt dei comandi con privilegi elevati. Il comando seguente imposta il nome dell'entità servizio dell'account del servizio Registrazione dispositivi di rete:

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`

   Ad esempio, se il computer che ospita il servizio Registrazione dispositivi di rete è denominato **Server01**, il dominio è **Contoso.com** e l'account del servizio è **NDESService**, usare:

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>Configurare il servizio Registrazione dispositivi di rete

1. Nel computer che ospita il servizio Registrazione dispositivi di rete aprire la procedura guidata **Configurazione Servizi certificati Active Directory** e quindi seguire questa procedura:

   > [!TIP]
   > Se si sta continuando dall'ultima procedura e si è fatto clic sul collegamento **Configurare Servizi certificati Active Directory nel server di destinazione**, la procedura guidata dovrebbe essere già aperta. In caso contrario, aprire Server Manager per accedere alla configurazione di post-distribuzione per i Servizi certificati Active Directory.

   - In **Servizi ruolo** selezionare **Servizio Registrazione dispositivi di rete**.
   - In **Account del servizio per il servizio Registrazione dispositivi di rete** specificare l'account del servizio Registrazione dispositivi di rete.
   - In **CA per NDES** fare clic su **Seleziona** e quindi selezionare la CA emittente in cui è stato configurato il modello di certificato.
   - In **Crittografia per NDES** impostare la lunghezza della chiave in modo da soddisfare i requisiti aziendali.
   - Nella pagina **Conferma** selezionare **Configura** per completare la procedura guidata.

2. Dopo il completamento della procedura guidata, modificare la seguente chiave del Registro di sistema nel computer che ospita il servizio Registrazione dispositivi di rete:

   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

   Per aggiornare questa chiave, identificare il valore **Scopo** dei modelli di certificato (disponibile nella scheda **Gestione richieste**). Aggiornare quindi la voce del Registro di sistema corrispondente sostituendo i dati esistenti con il nome del modello di certificato, non il nome visualizzato del modello, specificato durante la [creazione del modello di certificato](#create-the-scep-certificate-template).

   Nella tabella seguente viene eseguito il mapping lo scopo del modello di certificato per i valori del Registro di sistema:

   |Scopo del modello di certificato (nella scheda Gestione richieste)|Valore del Registro di sistema da modificare|Valore visualizzato nella console di amministrazione di Intune per il profilo SCEP|
   |------------------------|-------------------------|---|
   |Firma               |SignatureTemplate        |Firma digitale |
   |Crittografia              |EncryptionTemplate       |Crittografia chiave  |
   |Firma e crittografia|GeneralPurposeTemplate   |Crittografia chiave <br/> Firma digitale |

   Ad esempio, se lo scopo del modello di certificato è **Crittografia**, modificare il valore **EncryptionTemplate** in modo che corrisponda al nome del modello di certificato.

3. Configurare il filtro delle richieste IIS per aggiungere il supporto in IIS per gli URL lunghi (query) ricevuti dal servizio Registrazione dispositivi di rete.

   1. In Gestione IIS selezionare **Sito Web predefinito** > **Filtro richieste** > **Modifica impostazioni funzionalità** per aprire la pagina **Modifica impostazioni di filtro richieste**.

   2. Configurare le seguenti impostazioni:

      - **Lunghezza massima URL (byte)** = 65534
      - **Lunghezza massima stringa di query in (byte)** = 65534

   3. Selezionare **OK** per salvare la configurazione e chiudere Gestione IIS.

   4. Convalidare questa configurazione visualizzando la chiave del Registro di sistema seguente per verificare che abbia i valori indicati:

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

      I valori seguenti sono impostati come voci DWORD:

      - Nome: **MaxFieldLength**, con un valore decimale di **65534**
      - Nome: **MaxRequestBytes**, con un valore decimale di **65534**

4. Riavviare il server che ospita il servizio Registrazione dispositivi di rete. Non usare **iisreset**. iireset non completa le modifiche necessarie.

5. Passare a *http://* FQDN_Server */certsrv/mscep/mscep.dll*. Viene visualizzata una pagina del servizio Registrazione dispositivi di rete simile alla seguente:

   ![Test NDES](./media/certificates-scep-configure/scep-ndes-url.png)

   Se l'indirizzo Web restituisce l'errore **503 servizio non disponibile**, controllare il visualizzatore degli eventi del computer. Questo errore si verifica in genere quando il pool di applicazioni viene arrestato a causa di un'[autorizzazione per l'account del servizio Registrazione dispositivi di rete](#accounts) mancante.
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>Installare e associare i certificati nel server che ospita il servizio Registrazione dispositivi di rete

> [!TIP]
> Nella procedura seguente è possibile usare un solo certificato per l'*autenticazione server* e per l'*autenticazione client* quando tale certificato è configurato per soddisfare i criteri di entrambi gli usi. I criteri per ogni uso sono descritti nei passaggi 1 e 3 della procedura seguente.

1. Richiedere un certificato di **autenticazione server** dalla CA interna o dalla CA pubblica e quindi installare il certificato nel server.

   Se il server usa un nome esterno e uno interno per un unico indirizzo di rete, il certificato di autenticazione server deve avere:

   - Un **Nome soggetto** con un nome server pubblico esterno.
   - Un **Nome alternativo soggetto** che include il nome server interno.

2. Associare il certificato di autenticazione server in IIS:

   1. Dopo avere installato il certificato di autenticazione del server, aprire **Gestione IIS** e selezionare **Sito Web predefinito**. Nel riquadro **Azioni** selezionare **Associazioni**.

   1. Selezionare **Aggiungi**, impostare **Tipo** su **https**, quindi verificare che la porta sia **443**.
   
   1. Per **Certificato SSL**, specificare il certificato di autenticazione server.

3. Nel server NDES, richiedere e installare un **certificato di autenticazione client** dalla CA interna o pubblica.

   Il certificato di autenticazione client deve avere le seguenti proprietà:

   - **Utilizzo chiavi avanzato**: questo valore deve includere **Autenticazione client**.
   - **Nome soggetto**: il valore deve essere uguale al nome DNS del server in cui si installa il certificato (server del servizio Registrazione dispositivi di rete).

4. Il server che ospita il servizio Registrazione dispositivi di rete è ora pronto per supportare Connettore di certificati di Intune.

## <a name="install-the-intune-certificate-connector"></a>Installare Connettore di certificati di Intune

Connettore di certificati di Microsoft Intune viene installato nel server in cui è in esecuzione il servizio Registrazione dispositivi di rete. Non è supportato l'uso del servizio Registrazione dispositivi di rete o di Connettore di certificati di Intune nello stesso server dell'autorità di certificazione (CA) emittente.

### <a name="to-install-the-certificate-connector"></a>Per installare Connettore di certificati

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Connettori di certificati** > **Aggiungi**.

3. Scaricare e salvare il connettore per il file SCEP. Salvarlo in una posizione accessibile dal server in cui si intende installare il connettore.

   ![Download connettore](./media/certificates-scep-configure/download-certificates-connector.png)

4. Al completamento del download, passare al server che ospita il ruolo del servizio Registrazione dispositivi di rete (NDES). Quindi:

   1. Assicurarsi che .NET Framework 4.5 sia installato, perché è richiesto da Connettore di certificati di Intune. .NET Framework 4.5 è incluso automaticamente in Windows Server 2012 R2 e versioni più recenti.

   2. Eseguire il programma di installazione (**NDESConnectorSetup.exe**). Il programma di installazione installa anche il modulo dei criteri per il servizio Registrazione dispositivi di rete e il servizio Web del punto di registrazione certificati di IIS. Il servizio Web del punto di registrazione certificati, *CertificateRegistrationSvc*, viene eseguito come applicazione in IIS.

      - Quando si installa NDES per la configurazione autonoma di Intune, il servizio CRP viene installato automaticamente con Connettore di certificati.
      - Quando si usa Intune con Configuration Manager, viene installato il punto di registrazione certificati come ruolo del sistema del sito di Configuration Manager.

5. Quando viene richiesto il certificato client per Connettore di certificati, scegliere **Seleziona** e selezionare il certificato di **autenticazione client** installato nel server del servizio Registrazione dispositivi di rete durante il passaggio 3 della procedura [Installare e associare i certificati nel server che ospita il servizio Registrazione dispositivi di rete](#install-and-bind-certificates-on-the-server-that-hosts-ndes) più indietro in questo articolo.

   Dopo aver selezionato il certificato di autenticazione client, si torna all'area **certificato client per Connettore di certificati di Microsoft Intune**. Anche se il certificato selezionato non viene visualizzato, selezionare **Avanti** per visualizzare le proprietà del certificato. Selezionare **Avanti** e quindi **Installa**.

6. Al termine della procedura guidata, prima di chiuderla, fare clic su **Launch the Certificate Connector UI** (Avvia l'interfaccia utente di Connettore di certificati).

   Se si chiude la procedura guidata prima di avviare l'interfaccia utente di Connettore di certificati, è possibile riaprirla con il comando seguente:

   *<install_Path>\NDESConnectorUI\NDESConnectorUI.exe*

7. Nell'interfaccia utente di **Connettore di certificati** :

   1. Selezionare **Accedi** e immettere le credenziali di amministratore del servizio di Intune oppure le credenziali di amministratore tenant con le autorizzazioni di amministrazione globali.

   2. All'account usato deve essere assegnata una licenza di Intune valida.

   3. Dopo aver eseguito l'accesso, Connettore di certificati di Intune scarica un certificato da Intune. Questo certificato viene usato per l'autenticazione tra il connettore e Intune. Se l'account usato non ha una licenza di Intune, il connettore (NDESConnectorUI.exe) non riesce a ottenere il certificato da Intune.  

      Se l'organizzazione usa un server proxy e il proxy è necessario per consentire al server del servizio Registrazione dispositivi di rete di accedere a Internet, selezionare **Usa server proxy**. Immettere quindi il nome del server proxy, la porta e le credenziali dell'account per la connessione.

   4. Selezionare la scheda **Avanzate** e quindi immettere le credenziali per un account con l'autorizzazione **Rilascio e gestione certificati** sulla CA emittente. Scegliere **Applica** per applicare le modifiche.  

    5. Ora è possibile chiudere l'interfaccia utente di Connettore di certificati.

8. Aprire un prompt dei comandi, immettere **services.msc**, quindi premere **INVIO**. Fare clic con il pulsante destro del mouse su **Servizio Intune Connector** > **Riavvia**.

Per confermare che il servizio sia in esecuzione, aprire un browser e immettere il seguente URL. L'operazione dovrebbe restituire un errore **403**: `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Connettore di certificati di Intune supporta TLS 1.2. Se il server che ospita il connettore supporta TLS 1.2, viene usato TLS 1.2. Se il server non supporta TLS 1.2, viene usato TLS 1.1. Attualmente, TLS 1.1 viene usato per l'autenticazione tra i dispositivi e il server.

## <a name="next-steps"></a>Passaggi successivi

[Creare un profilo certificato SCEP](certificates-profile-scep.md)  
[Risolvere i problemi relativi a Connettore di certificati di Intune](troubleshoot-certificate-connector-events.md)
