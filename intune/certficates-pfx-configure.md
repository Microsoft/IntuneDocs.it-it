---
title: Usare certificati con chiave pubblica e privata in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare certificati PKCS (Public Key Cryptography Standards) con Microsoft Intune, inclusi i passaggi per esportare un certificato radice, configurare il modello di certificato, scaricare e installare il connettore di certificati di Intune (servizio Registrazione dispositivi di rete), creare un profilo di configurazione del dispositivo e creare un profilo certificato PKCS in Azure e nell'autorità di certificazione.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/19/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 985ca70dba2a5a486947bd2de08e7f8934e90d75
ms.sourcegitcommit: 2545ffb75b8d9290718d3a67acdcbea2f279090f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263713"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurare e usare i certificati PKCS con Intune

Intune supporta l'uso di certificati con coppia di chiavi pubblica e privata (PKCS). Questo articolo fornisce informazioni utili per configurare l'infrastruttura necessaria, ad esempio i connettori di certificati locali, esportare un certificato PKCS e quindi aggiungere il certificato a un profilo di configurazione del dispositivo in Intune.

Microsoft Intune include impostazioni predefinite per utilizzare i certificati PKCS per l’accesso e l’autenticazione delle risorse dell’organizzazione. I certificati consentono di autenticare e proteggere l'accesso alle risorse aziendali, ad esempio una rete VPN o Wi-Fi. Queste impostazioni vengono distribuite nei dispositivi usando i profili di configurazione dei dispositivi in Intune.


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

- **Connettore di certificati di Intune** (anche detto *connettore di certificati del servizio Registrazione dispositivi di rete*):  
  Nel portale di Intune passare a **Configurazione dispositivo** > **Connettori di certificati** > **Aggiungi** e seguire le indicazioni in *Passaggi per l'installazione del connettore per PKCS #12*. Usare il collegamento per il download nel portale per avviare il download del programma di installazione del connettore di certificati **NDESConnectorSetup.exe**.  

  Il connettore elabora le richieste di certificati PKCS usati per l'autenticazione o la firma S/MIME della posta elettronica.

  Il connettore di certificati del servizio Registrazione dispositivi di rete supporta anche la modalità FIPS (Federal Information Processing Standard). FIPS non è obbligatorio, ma è possibile emettere e revocare i certificati quando è abilitato.

- **Connettore di certificati PFX per Microsoft Intune**:  
   Se si prevede di usare la crittografia S/MIME per la posta elettronica, usare il portale di Intune per scaricare il connettore per i *certificati PFX importati*.  Passare a **Configurazione dispositivo** > **Connettori di certificati** > **Aggiungi** e seguire le indicazioni in *Passaggi per l'installazione del connettore per certificati PFX importati*. Usare il collegamento per il download nel portale per avviare il download del programma di installazione **PfxCertificateConnectorBootstrapper.exe**. 

  Questo connettore gestisce le richieste per i file PFX importati in Intune per la crittografia S/MIME della posta elettronica per un utente specifico.  

  Questo connettore consente l'aggiornamento automatico quando diventano disponibili nuove versioni. Per usare la funzionalità di aggiornamento, è necessario:
  - Installare il connettore di certificati PFX per Microsoft Intune nel server.
  - Per ricevere automaticamente gli aggiornamenti importanti, assicurarsi che i firewall siano aperti per consentire al connettore di contattare **autoupdate.msappproxy.net** sulla porta **443**.  


- **Windows Server**:  
  Si usa un server Windows per ospitare:

  - Connettore di certificati di Microsoft Intune: per scenari di autenticazione e firma S/MIME della posta elettronica
  - Connettore di certificati PFX per Microsoft Intune: per scenari di crittografia S/MIME della posta elettronica.

  È possibile installare entrambi i connettori (*connettore di certificati di Microsoft Intune* e *connettore di certificati PFX*) nello stesso server.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Esportare il certificato radice dall'autorità di certificazione globale (enterprise)

Per l'autenticazione di un dispositivo con una VPN, una rete Wi-Fi o altre risorse, un dispositivo richiede un certificato della CA radice o intermedio. La procedura seguente illustra come ottenere il certificato richiesto dall'autorità di certificazione globale (enterprise).

**Usare una riga di comando**:  
1. Accedere al server dell'autorità di certificazione radice con l'account amministratore.
 
2. Passare a **Start** > **Esegui** e quindi immettere **Cmd** per aprire il prompt dei comandi. 
    
3. Specificare **certutil -ca.cert ca_name.cer** per esportare il certificato radice come file denominato *ca_name.cer*.



## <a name="configure-certificate-templates-on-the-ca"></a>Configurare i modelli di certificato nella CA

1. Accedere all'autorità di certificazione globale (enterprise) con un account che abbia privilegi amministrativi.
2. Aprire la console **Autorità di certificazione**, fare clic con il pulsante destro del mouse su **Modelli di certificato** e selezionare **Gestisci**.
3. Trovare il modello di certificato **User**, fare clic con il pulsante destro del mouse su di esso e scegliere **Duplica modello**. Vengono visualizzate le **proprietà di Nuovo modello**.

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

## <a name="download-install-and-configure-the-certificate-connectors"></a>Scaricare, installare e configurare i connettori di certificati

### <a name="microsoft-intune-certificate-connector"></a>Connettore di certificati di Microsoft Intune

> [!IMPORTANT]  
> Il connettore di certificati di Microsoft Intune non può essere installato nell'autorità di certificazione (CA) emittente, ma deve invece essere istallato in un server Windows distinto.  

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione dispositivo** > **Connettori di certificati** > **Aggiungi**.
3. Scaricare e salvare il file del connettore in un percorso a cui è possibile accedere dal server in cui si installa il connettore.

    ![Download del connettore del servizio Registrazione dispositivi di rete](media/certificates-pfx-configure/download-ndes-connector.png)
 

4. Al termine del download, accedere al server. Quindi:

    1. Assicurarsi che sia installato.NET Framework 4.5 o versione successiva, perché è richiesto da NDES Connector per i certificati. .NET Framework 4.5 è incluso automaticamente con Windows Server 2012 R2 e versioni più recenti.
    2. Eseguire il programma di installazione (NDESConnectorSetup.exe) e accettare il percorso predefinito. Il connettore viene installato in `\Program Files\Microsoft Intune\NDESConnectorUI`. Selezionare **Distribuzione PFX** nelle opzioni di installazione. Continuare e completare l'installazione.
    3. Per impostazione predefinita, il servizio Connector viene eseguito con l'account di sistema locale. Se è necessario un proxy per l'accesso a Internet, verificare che l'account del servizio locale possa accedere alle impostazioni del proxy nel server.

5. NDES Connector apre la scheda **Registrazione**. Per abilitare la connessione a Intune, selezionare **Accedi** e specificare un account con autorizzazioni amministrative globali.
6. Nella scheda **Avanzate** è consigliabile lasciare selezionata l'opzione **Usa l'account di sistema del computer (impostazione predefinita)** .
7. **Applica** > **Chiudi**
8. Tornare al portale di Intune (**Intune** > **Configurazione dispositivo** > **Connettori di certificati**). Dopo alcuni istanti, viene visualizzato un segno di spunta verde e lo **stato della connessione** è **attivo**. Il server del connettore ora può comunicare con Intune.
9. Se si ha un proxy web nel proprio ambiente di rete, possono essere necessarie operazioni di configurazione aggiuntive per abilitare il funzionamento del connettore. Per altre informazioni, vedere [Usare server proxy locali esistenti](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) nella documentazione di Azure Active Directory.

> [!NOTE]  
> Il connettore di certificati di Microsoft Intune supporta TLS 1.2. Se TLS 1.2 è installato nel server che ospita il connettore, il connettore usa TLS 1.2. In caso contrario, viene usato TLS 1.1. Attualmente, TLS 1.1 viene usato per l'autenticazione tra i dispositivi e il server.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>Connettore di certificati PFX per Microsoft Intune

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione dispositivo** > **Connettori di certificati** > **Aggiungi**
3. Scaricare e salvare il connettore di certificati PFX per Microsoft Intune. Salvarlo in una posizione accessibile dal server in cui si intende installare il connettore.
4. Al termine del download, accedere al server. Quindi:

    1. Assicurarsi che sia installato.NET Framework 4.6 o versione successiva, perché è richiesto dal connettore di certificati PFX per Microsoft Intune. Se .NET Framework 4.6 non è installato, il programma di installazione lo installa automaticamente.
    2. Eseguire il programma di installazione (PfxCertificateConnectorBootstrapper.exe) e accettare il percorso predefinito, che installa il connettore in `Program Files\Microsoft Intune\PFXCertificateConnector`.
    3. Il servizio Connector viene eseguito con l'account di sistema locale. Se è necessario un proxy per l'accesso a Internet, verificare che l'account del servizio locale possa accedere alle impostazioni del proxy nel server.

5. Dopo l'installazione, il connettore di certificati PFX per Microsoft Intune consente di aprire la scheda **Registrazione**. Per abilitare la connessione a Intune, selezionare **Accedi** e specificare un account con autorizzazioni di amministratore globale o di amministratore di Intune.
6. Chiudere la finestra.
7. Tornare al portale di Azure (**Intune** > **Configurazione dispositivo** > **Connettori di certificati**). Dopo alcuni istanti, viene visualizzato un segno di spunta verde e lo **stato della connessione** è **attivo**. Il server del connettore ora può comunicare con Intune.

## <a name="create-a-trusted-certificate-profile"></a>Creare un profilo certificato attendibile

1. Nel [portale di Azure](https://portal.azure.com) passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
    ![Passare a Intune e creare un nuovo profilo per un certificato attendibile](media/certificates-pfx-configure/certificates-pfx-configure-profile-new.png)

2. Immettere le proprietà seguenti:

    - **Nome** del profilo
    - Inserire eventualmente una descrizione
    - **Piattaforma** in cui distribuire il profilo
    - Impostare **Tipo di profilo** su **Certificato attendibile**

3. Accedere a **Impostazioni** e specificare il file CER del certificato CA radice esportato in precedenza.

   > [!NOTE]
   > In base alla piattaforma scelta nel **passaggio 2**, si può avere o meno la possibilità di scegliere l'**archivio di destinazione** per il certificato.

   ![Creare un profilo e caricare un certificato attendibile](media/certificates-pfx-configure/certificates-pfx-configure-profile-fill.png) 

4. Selezionare **OK** > **Crea** per salvare il profilo.
5. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creare un profilo certificato PKCS

1. Nel [portale di Azure](https://portal.azure.com) passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
2. Immettere le proprietà seguenti:

    - **Nome** del profilo
    - Inserire eventualmente una descrizione
    - **Piattaforma** in cui distribuire il profilo
    - Impostare **Tipo di profilo** su **Certificato PKCS**

3. Accedere a **Impostazioni** e immettere le proprietà seguenti:

    - **Soglia di rinnovo (%)** : il valore consigliato è 20%.
    - **Periodo di validità del certificato**: se il modello di certificato non è stato cambiato, questa opzione può essere impostata su un anno.
    - **Provider di archiviazione chiavi (KSP)** : per Windows, selezionare la posizione in cui archiviare le chiavi nel dispositivo.
    - **Autorità di certificazione**: visualizza il nome di dominio completo (FQDN, Fully Qualified Domain Name) interno dell'autorità di certificazione globale (enterprise).
    - **Nome dell'autorità di certificazione**: specifica il nome dell'autorità di certificazione globale (enterprise), ad esempio "Contoso Certification Authority" (Autorità di certificazione Contoso).
    - **Nome modello di certificato**: nome del modello creato in precedenza. Ricordarsi che, per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*.
    - **Formato nome soggetto**: impostare questa opzione su **Nome comune**, se non diversamente richiesto.
    - **Nome alternativo soggetto**: impostare questa opzione su **Nome dell'entità utente (UPN)** , se non diversamente richiesto.

4. Selezionare **OK** > **Crea** per salvare il profilo.
5. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Creare un profilo certificato PKCS importato

È possibile importare in Intune certificati rilasciati in precedenza a un utente specifico da qualsiasi autorità di certificazione. I certificati importati vengono installati in ogni dispositivo registrato dall'utente in questione. La crittografia S/MIME della posta elettronica rappresenta lo scenario più comune per l'importazione di certificati PFX esistenti in Intune. Un utente può avere più certificati con cui crittografare la posta elettronica. Le chiavi private di tali certificati devono essere presenti in tutti i dispositivi perché sia possibile decrittografare la posta elettronica crittografata in precedenza.

Per importare certificati in Intune, è possibile usare i [cmdlet di PowerShell disponibili in GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Dopo aver importato i certificati in Intune, creare un profilo **certificato PKCS importato** e assegnarlo ai gruppi di Azure Active Directory.

1. Nel [portale di Azure](https://portal.azure.com) passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
2. Immettere le proprietà seguenti:

    - **Nome** del profilo
    - Inserire eventualmente una descrizione
    - **Piattaforma** in cui distribuire il profilo
    - Impostare **Tipo di profilo** su **Certificato PKCS importato**

3. Accedere a **Impostazioni** e immettere le proprietà seguenti:

    - **Scopo designato**: scopo designato dei certificati importati per questo profilo. Un amministratore può avere certificati importati con scopi designati diversi (ad esempio autenticazione, firma S/MIME o crittografia S/MIME). Lo scopo designato selezionato nel profilo certificato corrisponde al profilo certificato con i certificati importati corretti.
    - **Periodo di validità del certificato**: se il modello di certificato non è stato cambiato, questa opzione può essere impostata su un anno.
    - **Provider di archiviazione chiavi (KSP)** : per Windows, selezionare la posizione in cui archiviare le chiavi nel dispositivo.

4. Selezionare **OK** > **Crea** per salvare il profilo.
5. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](device-profile-assign.md).

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

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

[Usare i certificati SCEP](certificates-scep-configure.md) o [Rilasciare certificati PKCS da un servizio Web di gestione dell'infrastruttura a chiave pubblica DigiCert](certificates-digicert-configure.md).


