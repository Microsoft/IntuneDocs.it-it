---
title: Usare certificati con chiave pubblica e privata in Microsoft Intune - Azure | Microsoft Docs
description: Usare i certificati PKCS (Public Key Cryptography Standards) con Microsoft Intune. Sono incluse informazioni sull'uso di certificati radice e modelli di certificato, l'installazione del Connettore certificati di Intune (NDES) e sui profili di configurazione dei dispositivi per un certificato PKCS.
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
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3db085e6e88f8f57eb0276afa77290df8574568f
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801686"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurare e usare i certificati PKCS con Intune

Intune supporta l'uso di certificati con coppia di chiavi pubblica e privata (PKCS). Questo articolo fornisce informazioni utili per configurare l'infrastruttura necessaria, ad esempio i connettori di certificati locali, esportare un certificato PKCS e quindi aggiungere il certificato a un profilo di configurazione del dispositivo in Intune.

Microsoft Intune include impostazioni predefinite per utilizzare i certificati PKCS per l’accesso e l’autenticazione delle risorse dell’organizzazione. I certificati consentono di autenticare e proteggere l'accesso alle risorse aziendali, ad esempio una rete VPN o Wi-Fi. Queste impostazioni vengono distribuite nei dispositivi usando i profili di configurazione dei dispositivi in Intune.

Per informazioni sull'uso di certificati PKCS importati, vedere [Certificati PFX importati](certificates-imported-pfx-configure.md).


## <a name="requirements"></a>Requisiti

Per usare i certificati PKCS con Intune, è necessaria l'infrastruttura seguente:

- **Dominio di Active Directory**:  
  tutti i server elencati in questa sezione devono essere aggiunti al dominio di Active Directory.

  Per altre informazioni sull'installazione e sulla configurazione di Active Directory Domain Services, vedere [Pianificazione e progettazione di Active Directory Domain Services](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autorità di certificazione**:  
   Un'autorità di certificazione globale (enterprise).

  Per altre informazioni sull'installazione e sulla configurazione di Servizi certificati Active Directory (AD CS), vedere [Active Directory Certificate Services Step-by-Step Guide](https://technet.microsoft.com/library/cc772393) (Guida dettagliata di Servizi certificati Active Directory).

  > [!WARNING]  
  > Intune richiede l'esecuzione di Servizi certificati Active Directory con un'autorità di certificazione globale (enterprise), non con un'autorità di certificazione autonoma (Standalone).

- **Un client**:  
  Per la connessione alla CA globale (enterprise).

- **Certificato radice**:  
  Una copia del certificato radice esportato dall'autorità di certificazione globale (enterprise).

- **Connettore di certificati di Microsoft Intune** (anche detto *connettore di certificati del servizio Registrazione dispositivi di rete*):  
  Nel portale di Intune passare a **Configurazione dispositivo** > **Connettori di certificati** > **Aggiungi** e seguire le indicazioni in *Passaggi per l'installazione del connettore per PKCS #12*. Usare il collegamento per il download nel portale per avviare il download del programma di installazione del connettore di certificati **NDESConnectorSetup.exe**.  

  Intune supporta fino a 100 istanze di questo connettore per ogni tenant. Ogni istanza del connettore deve trovarsi in un server Windows separato. È possibile installare un'istanza di questo connettore nello stesso server di un'istanza del connettore di certificati PFX per Microsoft Intune. Quando si usano più connettori, l'infrastruttura del connettore supporta la disponibilità elevata e il bilanciamento del carico perché qualsiasi istanza del connettore disponibile può elaborare le richieste di certificati PKCS. 

  Il connettore elabora le richieste di certificati PKCS usati per l'autenticazione o la firma S/MIME della posta elettronica.

  Il connettore di certificati di Microsoft Intune supporta anche la modalità FIPS (Federal Information Processing Standard). FIPS non è obbligatorio, ma è possibile emettere e revocare i certificati quando è abilitato.

- **Connettore di certificati PFX per Microsoft Intune**:  
  Se si prevede di usare la crittografia S/MIME per la posta elettronica, usare il portale di Intune per scaricare il *Connettore dei certificati PFX* che supporta l'importazione di certificati PFX.  Passare a **Configurazione dispositivo** > **Connettori di certificati** > **Aggiungi** e seguire le indicazioni in *Passaggi per l'installazione del connettore per certificati PFX importati*. Usare il collegamento per il download nel portale per avviare il download del programma di installazione **PfxCertificateConnectorBootstrapper.exe**. 

  Ogni tenant di Intune supporta una sola istanza di questo connettore. È possibile installare questo connettore nello stesso server di un'istanza del connettore di certificati di Microsoft Intune.

  Questo connettore gestisce le richieste per i file PFX importati in Intune per la crittografia S/MIME della posta elettronica per un utente specifico.  

  Questo connettore consente l'aggiornamento automatico quando diventano disponibili nuove versioni. Per usare la funzionalità di aggiornamento, è necessario:
  - Installare il connettore dei certificati PFX per Microsoft Intune nel server.  
  - Per ricevere automaticamente gli aggiornamenti importanti, assicurarsi che i firewall siano aperti per consentire al connettore di contattare **autoupdate.msappproxy.net** sulla porta **443**.   

  Per altre informazioni sugli endpoint di rete a cui accedono Intune e il connettore, vedere [Endpoint di rete per Microsoft Intune](../fundamentals/intune-endpoints.md).

- **Windows Server**:  
  Si usa un server Windows per ospitare:

  - Connettore di certificati di Microsoft Intune: per scenari di autenticazione e firma S/MIME della posta elettronica
  - Connettore di certificati PFX per Microsoft Intune: per scenari di crittografia S/MIME della posta elettronica.

  Intune supporta l'installazione del *connettore di certificati PFX* nello stesso server del *connettore di certificati di Microsoft Intune*.
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Esportare il certificato radice dall'autorità di certificazione globale (enterprise)

Per l'autenticazione di un dispositivo con una VPN, una rete Wi-Fi o altre risorse, un dispositivo richiede un certificato della CA radice o intermedio. La procedura seguente illustra come ottenere il certificato richiesto dall'autorità di certificazione globale (enterprise).

**Usare una riga di comando**:  
1. Accedere al server dell'autorità di certificazione radice con l'account amministratore.
 
2. Passare a **Start** > **Esegui** e quindi immettere **Cmd** per aprire il prompt dei comandi. 
    
3. Specificare **certutil -ca.cert ca_name.cer** per esportare il certificato radice come file denominato *ca_name.cer*.



## <a name="configure-certificate-templates-on-the-ca"></a>Configurare i modelli di certificato nella CA

1. Accedere all'autorità di certificazione globale (enterprise) con un account che abbia privilegi amministrativi.
2. Aprire la console **Autorità di certificazione**, fare clic con il pulsante destro del mouse su **Modelli di certificato** e selezionare **Gestisci**.
3. Trovare il modello di certificato **Utente**, fare clic con il pulsante destro del mouse su di esso e scegliere **Duplica modello** per aprire **Proprietà nuovo modello**.

    > [!NOTE]
    > Per scenari di firma e crittografia S/MIME della posta elettronica, molti amministratori usano certificati separati per la firma e la crittografia. Se si usa Servizi certificati Microsoft Active Directory, è possibile usare il modello **Solo firma di Exchange** per i certificati di firma S/MIME per la posta elettronica e il modello **Utente di Exchange** per i certificati di crittografia S/MIME.  Se si usa un'autorità di certificazione di terze parti è consigliabile rivedere il le istruzioni di tale autorità per la configurazione dei modelli di firma e crittografia.

4. Nella scheda **Compatibilità**:

    - Impostare **Autorità di certificazione** su **Windows Server 2008 R2**
    - Impostare **Destinatario certificato** su **Windows 7 / Server 2008 R2**

5. Nella scheda **Generale** impostare **Nome visualizzato modello** su un valore significativo.

    > [!WARNING]
    > Per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*. Annotare il nome del modello, sarà necessario in un secondo momento.

6. In **Gestione richiesta** selezionare **Rendi la chiave privata esportabile**.
7. In **Crittografia** verificare che il campo **Dimensioni minime chiave** sia impostato su 2048.
8. In **Nome soggetto** scegliere **Inserisci nella richiesta**.
9. In **Estensioni** verificare che nell'area **Criteri di applicazione** siano presenti Crittografia file system, Posta elettronica sicura e Autenticazione client.

    > [!IMPORTANT]
    > Per i modelli di certificato iOS, accedere alla scheda **Estensioni**, aggiornare **Utilizzo chiavi** e verificare che l'opzione **Firma come prova dell'origine** non sia selezionata.

10. In **Sicurezza** aggiungere l'account computer relativo al server in cui si installa il connettore di certificati di Microsoft Intune. Assegnare all'account le autorizzazioni **Lettura** e **Registrazione**.
11. Selezionare **Applica** > **OK** per salvare il modello di certificato. Chiudere la **Console dei modelli di certificato**.
12. Nella console **Autorità di certificazione** fare clic con il pulsante destro del mouse su **Modelli di certificato** > **Nuovo** > **Modello di certificato da rilasciare**. Scegliere il modello creato nei passaggi precedenti. Selezionare **OK**.
13. Per consentire al server di gestire i certificati per gli utenti e i dispositivi registrati, eseguire i passaggi seguenti:

    1. Fare clic con il pulsante destro del mouse sull'autorità di certificazione e scegliere **Proprietà**.
    2. Nella scheda della sicurezza aggiungere l'account computer relativo al server in cui sono in esecuzione i connettori (il **connettore di certificati di Microsoft Intune** e il **connettore di certificati PFX per Microsoft Intune**). 
    3. Assegnare all'account le autorizzazioni **Rilascio e gestione certificati** e **Richiesta certificati**.

14. Disconnettersi dall'autorità di certificazione globale (enterprise).

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Scaricare, installare e configurare il connettore di certificati di Microsoft Intune

> [!IMPORTANT]  
> Il connettore di certificati di Microsoft Intune non può essere installato nell'autorità di certificazione (CA) emittente, ma deve invece essere istallato in un server Windows distinto.  

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Connettori di certificati** >  **+Aggiungi**.

3. Fare clic su *Scaricare il software del connettore del certificato* per il connettere per PKCS #12 e salvare il file in un percorso a cui è possibile accedere dal server in cui si installerà il connettore.

   ![Download del connettore di certificati di Microsoft Intune](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. Al termine del download, accedere al server. Quindi:

    1. Assicurarsi che sia installato.NET Framework 4.5 o versione successiva, perché è richiesto da NDES Connector per i certificati. .NET Framework 4.5 è incluso automaticamente con Windows Server 2012 R2 e versioni più recenti.
    2. Eseguire il programma di installazione (NDESConnectorSetup.exe) e accettare il percorso predefinito. Il connettore viene installato in `\Program Files\Microsoft Intune\NDESConnectorUI`. Selezionare **Distribuzione PFX** nelle opzioni di installazione. Continuare e completare l'installazione.
    3. Per impostazione predefinita, il servizio Connector viene eseguito con l'account di sistema locale. Se è necessario un proxy per l'accesso a Internet, verificare che l'account del servizio locale possa accedere alle impostazioni del proxy nel server.

5. Il connettore di certificati di Microsoft Intune apre la scheda **Registrazione**. Per abilitare la connessione a Intune, selezionare **Accedi** e specificare un account con autorizzazioni amministrative globali.
6. Nella scheda **Avanzate** è consigliabile lasciare selezionata l'opzione **Usa l'account di sistema del computer (impostazione predefinita)** .
7. **Applica** > **Chiudi**
8. Tornare al portale di Intune (**Intune** > **Configurazione dispositivo** > **Connettori di certificati**). Dopo alcuni istanti, viene visualizzato un segno di spunta verde e lo **stato della connessione** è **attivo**. Il server del connettore ora può comunicare con Intune.
9. Se si ha un proxy web nel proprio ambiente di rete, possono essere necessarie operazioni di configurazione aggiuntive per abilitare il funzionamento del connettore. Per altre informazioni, vedere [Usare server proxy locali esistenti](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) nella documentazione di Azure Active Directory.

> [!NOTE]  
> Il connettore di certificati di Microsoft Intune supporta TLS 1.2. Se TLS 1.2 è installato nel server che ospita il connettore, il connettore usa TLS 1.2. In caso contrario, viene usato TLS 1.1. Attualmente, TLS 1.1 viene usato per l'autenticazione tra i dispositivi e il server.

## <a name="create-a-trusted-certificate-profile"></a>Creare un profilo certificato attendibile

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

   ![Passare a Intune e creare un nuovo profilo per un certificato attendibile](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Immettere le proprietà seguenti:

    - **Nome** del profilo
    - Inserire eventualmente una descrizione
    - **Piattaforma** in cui distribuire il profilo
    - Impostare **Tipo di profilo** su **Certificato attendibile**

4. Selezionare **Impostazioni** e specificare il file con estensione cer del certificato CA radice esportato in precedenza.

   > [!NOTE]
   > In base alla piattaforma scelta nel **passaggio 2**, si può avere o meno la possibilità di scegliere l'**archivio di destinazione** per il certificato.

   ![Creare un profilo e caricare un certificato attendibile](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. Selezionare **OK** > **Crea** per salvare il profilo.

6. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](../configuration/device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creare un profilo certificato PKCS

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare e passare a **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

3. Immettere le proprietà seguenti:

    - **Nome** del profilo
    - Inserire eventualmente una descrizione
    - **Piattaforma** in cui distribuire il profilo
    - Impostare **Tipo di profilo** su **Certificato PKCS**

4. Selezionare **Impostazioni** e configurare le proprietà che si applicano alla piattaforma selezionata:
   
   |Impostazione     | Piattaforma     | Dettagli   |
   |------------|------------|------------|
   |**Soglia di rinnovo (%)**        |Tutto         |il valore consigliato è 20%  | 
   |**Periodo di validità del certificato**  |Tutto         |se il modello di certificato non è stato cambiato, questa opzione può essere impostata su un anno. |
   |**Provider di archiviazione chiavi (KSP)**   |Windows 10  | per Windows, selezionare la posizione in cui archiviare le chiavi nel dispositivo. |
   |**Autorità di certificazione**      |Tutto         |visualizza il nome di dominio completo (FQDN, Fully Qualified Domain Name) interno dell'autorità di certificazione globale (enterprise).  |
   |**Nome dell'autorità di certificazione** |Tutto         |specifica il nome dell'autorità di certificazione globale (enterprise), ad esempio "Contoso Certification Authority" (Autorità di certificazione Contoso). |
   |**Tipo di certificato**             |macOS       |Selezionare un tipo: <br> **-** I certificati di tipo **Utente** possono contenere attributi sia relativi agli utenti che ai dispositivi nel soggetto e nel nome alternativo del soggetto del certificato. <br><br>**-** I certificati di tipo **Dispositivo** possono contenere solo attributi relativi ai dispositivi nel soggetto e nel nome alternativo del soggetto del certificato. Usare il tipo Dispositivo per scenari quali i dispositivi senza utente, ad esempio i chioschi multimediali o altri dispositivi condivisi.  <br><br> Questa selezione influisce sul formato del nome soggetto. |
   |**Formato nome soggetto**          |Tutto         |Per la maggior parte delle piattaforme impostare questa opzione su **Nome comune**, se non diversamente richiesto.<br><br>Per macOS, il formato del nome soggetto è determinato dal tipo di certificato. Vedere [Formato del nome soggetto per macOS](#subject-name-format-for-macos) più avanti in questo articolo. |
   |**Nome alternativo soggetto**     |Tutto         |impostare questa opzione su **Nome dell'entità utente (UPN)** , se non diversamente richiesto. |
   |**Utilizzo chiavi avanzato**           |**-** Amministratore di dispositivi Android <br>**-** Android Enterprise (*Proprietario del dispositivo*, *Profilo di lavoro*) <br> **-** Windows 10 |I certificati richiedono in genere l'*Autenticazione Client* in modo che l'utente o il dispositivo possa eseguire l'autenticazione a un server. |
   |**Consenti a tutte le app l'accesso alla chiave privata** |macOS  |Impostare su **Abilita** per concedere alle app configurate per l'accesso al dispositivo Mac associato la chiave privata dei certificati PKCS. <br><br> Per altre informazioni su questa impostazione, vedere *AllowAllAppsAccess* nella sezione Certificate Payload (Payload del certificato) del documento [Configuration Profile Reference](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) (Informazioni di riferimento sui profili di configurazione) nella documentazione per sviluppatori Apple. |
   |**Certificato radice**             |**-** Amministratore di dispositivi Android <br> **-** Android Enterprise (*Proprietario del dispositivo*, *Profilo di lavoro*) |Selezionare un profilo del certificato CA radice assegnato in precedenza. |

5. Selezionare **OK** > **Crea** per salvare il profilo.

6. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](../configuration/device-profile-assign.md).

   > [!NOTE]
   > Nei dispositivi con un profilo Android Enterprise, i certificati installati usando un profilo di certificato PKCS non sono visibili nel dispositivo. Per verificare la corretta distribuzione del certificato, controllare lo stato del profilo nella console di Intune.

### <a name="subject-name-format-for-macos"></a>Formato del nome soggetto per macOS

Quando si crea un profilo di certificato PKCS macOS, le opzioni per il formato del nome soggetto dipendono dal tipo di certificato selezionato, **Utente** o **Dispositivo**.  

> [!NOTE]  
> L'uso di PKCS per ottenere certificati presenta un problema noto ([lo stesso problema rilevato per SCEP](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters)) quando il nome del soggetto nella richiesta di firma del certificato risultante include uno dei caratteri seguenti come carattere di escape (preceduto da una barra rovesciata \\):
> - \+
> - ;
> - ,
> - =

- **Tipo di certificato utente**  
  Le opzioni di formato per *Formato nome soggetto* includono due variabili: **CN (Nome comune)** ed **E (Posta elettronica)** . **CN (Nome comune)** può essere impostata su una delle variabili seguenti:

  - **CN={{UserName}}** : nome dell'entità utente (UPN) dell'utente, ad esempio janedoe@contoso.com.
  - **CN={{AAD_Device_ID}}** : ID assegnato quando si registra un dispositivo in Azure Active Directory (AD). Questo ID è in genere usato per l'autenticazione con Azure AD.
  - **CN={{SERIALNUMBER}}** : numero di serie (SN) univoco usato in genere dal produttore per identificare un dispositivo.
  - **CN={{IMEINumber}}** : numero IMEI (International Mobile Equipment Identity) univoco usato per identificare un telefono cellulare.
  - **CN={{OnPrem_Distinguished_Name}}** : sequenza di nomi distinti relativi separati da virgola, ad esempio *CN=Giorgia Fanucci,OU=UserAccounts,DC=corp,DC=contoso,DC=com*.

    Per usare la variabile *{{OnPrem_Distinguished_Name}}* , assicurarsi di sincronizzare l'attributo utente *onpremisesdistinguishedname* usando [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

  - **CN={{onPremisesSamAccountName}}** : gli amministratori possono sincronizzare l'attributo samAccountName da Active Directory ad Azure AD usando Azure AD Connect in un attributo denominato *onPremisesSamAccountName*. Intune può sostituire tale variabile come parte di una richiesta di emissione di certificati nel soggetto di un certificato. L'attributo samAccountName è il nome di accesso utente usato per supportare i client e i server da una versione precedente di Windows (precedente a Windows 2000). Il formato del nome di accesso dell'utente è: *NomeDomino\utenteTest* o solo *utenteTest*.

    Per usare la variabile *{{onPremisesSamAccountName}}* , assicurarsi di sincronizzare l'attributo utente *onPremisesSamAccountName* usando [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

  Usando una combinazione di una o più variabili e stringhe statiche, è possibile creare un formato di nome soggetto personalizzato, ad esempio:  
  - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
  
  Questo esempio include un formato di nome soggetto che usa le variabili CN ed E, oltre a stringhe per i valori di unità organizzativa (OU), organizzazione (O), località (L), stato (S) e paese (C). L'argomento [Funzione CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) visualizza questa funzione e le relative stringhe supportate.

- **Tipo di certificato dispositivo**  
  Le opzioni di formato per il formato del nome soggetto includono le variabili seguenti: 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{SerialNumber}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullyQualifiedDomainName}}** *(applicabile solo per Windows e i dispositivi aggiunti a un dominio)*
  - **{{MEID}}**

  È possibile specificare queste variabili, seguite dal testo per la variabile, nella casella di testo. Ad esempio, il nome comune per un dispositivo denominato *Dispositivo1* può essere aggiunto come **CN={{DeviceName}}Dispositivo1**.

  > [!IMPORTANT]  
  > - Quando si specifica una variabile, racchiudere il nome della variabile tra parentesi graffe { }, come illustrato nell'esempio, per evitare un errore.  
  > - Le proprietà del dispositivo usate nel *soggetto* o nel *nome alternativo del soggetto* di un certificato del dispositivo, ad esempio **IMEI**, **SerialNumber** e **FullyQualifiedDomainName**, sono proprietà soggette a spoofing da parte di un utente con accesso al dispositivo.
  > - Un dispositivo deve supportare tutte le variabili specificate in un profilo di certificato, affinché tale profilo possa essere installato nel dispositivo.  Ad esempio, se si usa **{{IMEI}}** nel nome del soggetto di un profilo SCEP e il profilo viene assegnato a un dispositivo che non ha un numero IMEI, l'installazione del profilo avrà esito negativo.  
 


## <a name="whats-new-for-connectors"></a>Novità dei connettori

Periodicamente vengono rilasciati aggiornamenti per i due connettori di certificati. Quando un connettore viene aggiornato, le modifiche vengono illustrate qui.

Il *connettore di certificati PFX per Microsoft Intune* [supporta gli aggiornamenti automatici](#requirements), mentre il *connettore di certificati di Intune* viene aggiornato manualmente.

### <a name="may-17-2019"></a>17 maggio 2019

- **Connettore dei certificati PFX per Microsoft Intune - versione 6.1905.0.404**  
  Modifiche in questa versione:  
  - È stato risolto un problema a causa del quale i certificati PFX esistenti continuano a essere rielaborati e di conseguenza il connettore smette di elaborare le nuove richieste. 

### <a name="may-6-2019"></a>6 maggio 2019

- **Connettore di certificati PFX per Microsoft Intune - versione 6.1905.0.402**  
  Modifiche in questa versione:  
  - L'intervallo di polling per il connettore è stato ridotto da 5 minuti a 30 secondi.
 
### <a name="april-2-2019"></a>2 aprile 2019

- **Connettore di certificati di Intune - versione 6.1904.1.0**  
  Modifiche in questa versione:  
  - È stato risolto un problema a causa del quale può verificarsi un errore di registrazione in Intune dopo avere eseguito l'accesso al connettore con un account amministratore globale.  
  - Include correzioni relative all'affidabilità della revoca dei certificati.  
  - Include correzioni relative alle prestazioni per aumentare la velocità di elaborazione delle richieste di certificati PKCS.  

- **Connettore di certificati PFX per Microsoft Intune - versione 6.1904.0.401**
  > [!NOTE]  
  > L'aggiornamento automatico per questa versione del connettore PFX sarà disponibile dopo l'11 aprile 2019.  

  Modifiche in questa versione:  
  - È stato risolto un problema a causa del quale può verificarsi un errore di registrazione in Intune dopo avere eseguito l'accesso al connettore con un account amministratore globale.  


## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](../configuration/device-profile-assign.md) e [monitorarne lo stato](../configuration/device-profile-monitor.md).

[Usare SCEP per i certificati ](certificates-scep-configure.md) o [Rilasciare certificati PKCS da un servizio Web di gestione PKI Symantec](certificates-digicert-configure.md).
