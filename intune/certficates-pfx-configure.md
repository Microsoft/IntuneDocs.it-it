---
title: Configurare e gestire i certificati PKCS con Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune di Azure: informazioni su come configurare l&quot;infrastruttura e quindi creare e assegnare i certificati SCEP con Intune.'
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 04/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e189ebd1-6ca1-4365-9d5d-fab313b7e979
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 16fa26ae8ed06c4959807b30e430fd69fc503936
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017



---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>Configurare e gestire i certificati PKCS con Intune
[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Questo argomento illustra come configurare l'infrastruttura e quindi creare e assegnare profili certificato PKCS con Intune.

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
-  **Server Proxy applicazione Web**  (facoltativo): è possibile usare un server che esegue Windows Server 2012 R2 o versione successiva come Server Proxy applicazione Web (WAP). Questa configurazione:
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
|**Certificato CA radice attendibile**|Questo certificato viene esportato come file con estensione **CER** dalla CA emittente o da qualsiasi dispositivo che considera attendibile la CA emittente, e viene assegnato ai dispositivi usando il profilo certificato della CA attendibile.<br /><br />Viene usato un certificato CA radice attendibile per ogni piattaforma di sistema e lo si associa con ogni profilo del certificato radice attendibile creato.<br /><br />È possibile usare certificati CA radice attendibili aggiuntivi, se necessario. Ad esempio, è possibile farlo per fornire un trust a un'autorità di certificazione che firma i certificati di autenticazione del server per i punti di accesso Wi-Fi.|


## <a name="configure-your-infrastructure"></a>Configurare l'infrastruttura
Prima di poter configurare i profili certificato, è necessario completare i passaggi seguenti. Questi passaggi richiedono la conoscenza di Windows Server 2012 R2 e dei Servizi certificati Active Directory (ADCS):

- **Passaggio 1**: configurare modelli di certificato nell'autorità di certificazione.
- **Passaggio 2**: abilitare, installare e configurare il Connettore di certificati di Intune.

## <a name="step-1---configure-certificate-templates-on-the-certification-authority"></a>Passaggio 1: configurare modelli di certificato nell'autorità di certificazione

### <a name="to-configure-the-certification-authority"></a>Per configurare l'autorità di certificazione

1.  Nella CA emittente usare lo snap-in Modelli di certificato per creare un nuovo modello personalizzato o copiare e modificare un modello esistente (ad esempio, il modello Utente) per l'uso con il profilo PKCS.

    Il modello deve includere quanto segue:

    -   Specificare un **nome visualizzato** descrittivo per il modello.

    -   Nella scheda **Nome soggetto** selezionare **Fornisci nella richiesta**. (La sicurezza viene applicata con il modulo dei criteri di Intune per NDES).

    -   Nella scheda **Estensioni** verificare che la **descrizione dei criteri dell'applicazione** includa **Autenticazione client**.

        > [!IMPORTANT]
        > Per i modelli di certificato iOS e macOS, nella scheda **Estensioni** modificare **Utilizzo chiavi** e verificare che l'opzione **Firma come prova dell'origine** non sia selezionata.

2.  Esaminare il **periodo di validità** nella scheda **Generale** del modello. Per impostazione predefinita, Intune usa il valore configurato nel modello. Tuttavia, è possibile configurare la CA per consentire al richiedente di specificare un valore diverso, che è poi possibile impostare dalla console di amministrazione di Intune. Per usare sempre il valore nel modello, ignorare il resto del passaggio.

    > [!IMPORTANT]
    > iOS e macOS usano sempre il valore impostato nel modello, indipendentemente dalle altre configurazioni definite.

    Per configurare la CA in modo che consenta al richiedente di specificare il periodo di validità, eseguire questi comandi nella CA:

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  Nella CA emittente usare lo snap-in dell'autorità di certificazione per pubblicare il modello di certificato.

    a.  Selezionare il nodo **Modelli di certificato**, fare clic su **Azione**-&gt; **Nuovo** &gt; **Modello di certificato da rilasciare** e quindi selezionare il modello creato nel passaggio 2.

    b.  Verificare che il modello sia stato pubblicato visualizzandolo nella cartella **Modelli di certificato** .

4.  Nel computer della CA assicurarsi che il computer che ospita il Connettore di certificati di Intune abbia l'autorizzazione di registrazione per poter accedere al modello usato nella creazione del profilo PKCS. Impostare l'autorizzazione nella scheda **Sicurezza** delle proprietà del computer della CA.

## <a name="step-2---enable-install-and-configure-the-intune-certificate-connector"></a>Passaggio 2: abilitare, installare e configurare il Connettore di certificati di Intune
In questo passaggio verranno eseguite le operazioni seguenti:

- Abilitare il supporto per il Connettore di certificati
- Scaricare, installare e configurare Connettore di certificati.

### <a name="to-enable-support-for-the-certificate-connector"></a>Per abilitare il supporto per il Connettore di certificati

1.  Accedere al portale Azure.
2.  Scegliere **Altri servizi** > **Altro** > **Intune**.
3.  Nel pannello **Intune** scegliere **Configura i dispositivi**.
2.  Nel pannello **Configurazione del dispositivo** scegliere **Installazione** > **Autorità di certificazione**.
2.  Nel **passaggio 1** scegliere **Abilita**.

### <a name="to-download-install-and-configure-the-certificate-connector"></a>Scaricare, installare e configurare il Connettore di certificati

1.  Nel pannello **Configura i dispositivi** scegliere **Installazione** > **Autorità di certificazione**.
2.  Scegliere **Scarica il connettore del certificato**.
2.  Al termine del download, eseguire il programma di installazione scaricato (**ndesconnectorssetup.exe**).
  Eseguire il programma di installazione nel computer che può connettersi all'autorità di certificazione. Scegliere l'opzione di distribuzione PFX e quindi fare clic su **Installa**. Al termine dell'installazione, procedere alla creazione di un profilo certificato come descritto in [Configure certificate profiles](certificates-configure.md) (Configurare i profili certificato).

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


### <a name="how-to-create-a-pkcs-certificate-profile"></a>Come creare un profilo certificato PKCS

Nel portale di Azure selezionare il carico di lavoro **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili fare clic su **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo certificato PKCS.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo per questo certificato PKCS:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Certificato PKCS**.
7. Nel pannello **Certificato PKCS** è possibile configurare le impostazioni seguenti:
    - **Soglia di rinnovo (%)**: specificare la percentuale di durata residua del certificato prima che il dispositivo ne richieda il rinnovo.
    - **Periodo di validità del certificato**: se il comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** è stato eseguito nella CA emittente, che consente un periodo di validità personalizzato, è possibile specificare la quantità di tempo rimanente prima della scadenza del certificato.<br>È possibile specificare un valore inferiore, ma non superiore rispetto al periodo di validità nel modello di certificato indicato. Ad esempio, se il periodo di validità del certificato nel modello di certificato è di due anni, è possibile specificare un valore di un anno ma non un valore di cinque anni. Inoltre, il valore deve essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente.
    - **Provider di archiviazione chiavi (KSP)** (Windows 10) Specificare dove archiviare la chiave per il certificato. Scegliere tra uno dei seguenti valori:
        - **Registra nel provider di archiviazione chiavi Trusted Platform Module (TPM) se presente, altrimenti nel provider di archiviazione chiavi software**
        - **Registra nel provider di archiviazione chiavi Trusted Platform Module (TPM) oppure genera errore**
        - **Registra in Passport oppure genera errore (Windows 10 e versioni successive)**
        - **Registra nel provider di archiviazione chiavi software**
    - **Autorità di certificazione**: un'autorità di certificazione globale eseguita in un'edizione Enterprise di Windows Server 2008 R2 o versioni successive. L'opzione CA autonoma non è supportata. Per istruzioni su come configurare un'autorità di certificazione, vedere [Installare l'autorità di certificazione](http://technet.microsoft.com/library/jj125375.aspx). Se la CA esegue Windows Server 2008 R2, è necessario [installare l'hotfix di KB2483564](http://support.microsoft.com/kb/2483564/).
    - **Nome dell'autorità di certificazione**: immettere il nome dell'autorità di certificazione.
    - **Nome modello di certificato**: immettere il nome di un modello di certificato configurato per essere usato dal servizio Registrazione dispositivi di rete e che è stato aggiunto a una CA emittente.
    Assicurarsi che il nome corrisponda esattamente a uno dei modelli del certificato elencati nel registro di sistema del server che esegue il servizio Registrazione dispositivi di rete. Accertarsi di specificare il nome del modello del certificato e non il nome visualizzato del modello del certificato. 
    Per trovare i nomi dei modelli di certificato, individuare la seguente chiave: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. I modelli di certificato verranno visualizzati come i valori per **EncryptionTemplate**, **GeneralPurposeTemplate**e **SignatureTemplate**. Per impostazione predefinita, il valore per i tre modelli di certificato è IPSECIntermediateOffline, che è associato al nome visualizzato del modello **IPSec (Offline request)**. 
    - **Formato nome soggetto**: dall'elenco, selezionare in che modo Intune crea automaticamente il nome soggetto nella richiesta certificato. Se il certificato è per un utente, è anche possibile includere l'indirizzo di posta elettronica dell'utente nel nome del soggetto. È possibile scegliere tra:
        - **Non configurato**
        - **Nome comune**
        - **Nome comune incluso l'indirizzo di posta elettronica**
        - **Nome comune come indirizzo di posta elettronica**
    - **Nome alternativo soggetto**: specificare in che modo Intune crea automaticamente i valori per il nome alternativo soggetto (SAN) nella richiesta certificato. Ad esempio, se si seleziona un tipo di certificato utente, è possibile includere il nome dell'entità utente (UPN) nel nome alternativo oggetto. Se il certificato client verrà usato per eseguire l'autenticazione in un server dei criteri di rete, è necessario impostare il nome alternativo oggetto sul nome dell'entità utente.
    - **Utilizzo chiave esteso** (Android): scegliere **Aggiungi** per aggiungere valori per lo scopo designato del certificato. Nella maggior parte dei casi il certificato richiederà l' **Autenticazione Client** in modo che l'utente o il dispositivo possa eseguire l'autenticazione a un server. È comunque possibile aggiungere altri utilizzi di chiavi secondo necessità. 
    - **Certificato radice** (Android): scegliere un profilo del certificato radice della CA già configurato e assegnato all'utente o al dispositivo. Questo certificato CA deve essere il certificato radice per l'autorità di certificazione che rilascerà il certificato che si sta configurando in questo profilo certificato. Questo è il profilo certificato attendibile creato in precedenza.
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="how-to-assign-the-certificate-profile"></a>Come assegnare il profilo certificato

Prima di assegnare i profili certificato ai gruppi, considerare quanto segue:

- Quando si assegnano i profili certificato ai gruppi, il file del certificato dal profilo certificato CA attendibile viene installato nel dispositivo. Il dispositivo usa il profilo certificato SCEP per creare una richiesta di certificato tramite il dispositivo.
- I profili certificato vengono installati solo nei dispositivi che eseguono la piattaforma usata durante la creazione del profilo.
- È possibile assegnare profili certificato alle raccolte di utenti o di dispositivi.
- Per pubblicare rapidamente un certificato in un dispositivo dopo la registrazione del dispositivo, assegnare il profilo certificato a un gruppo di utenti invece che a un gruppo di dispositivi. Se si assegna il profilo certificato a un gruppo di dispositivi, è necessario eseguire una registrazione completa dei dispositivi prima che questi ricevano i criteri.
- Sebbene ogni profilo venga assegnato separatamente, è necessario assegnare anche la CA radice attendibile e il profilo PKCS. In caso contrario, i criteri di certificato PKCS avranno esito negativo.

Per informazioni su come assegnare profili, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).

