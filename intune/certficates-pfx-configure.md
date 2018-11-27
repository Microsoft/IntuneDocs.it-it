---
title: Usare i certificati PKCS con Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare certificati PKCS (Public Key Cryptography Standards) con Microsoft Intune, inclusi i passaggi per esportare un certificato radice, configurare il modello di certificato, scaricare e installare il connettore di certificati di Microsoft Intune (NDES), creare un profilo di configurazione del dispositivo, creare un profilo certificato PKCS in Azure e nell'autorità di certificazione.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 70d1594220b3315db2c7d7eeb01a915aaf2ec995
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186733"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurare e usare i certificati PKCS con Intune

> [!IMPORTANT]
> Sono in corso alcuni miglioramenti alla funzionalità S/MIME descritti in questo articolo. Di conseguenza, la funzionalità S/MIME viene temporaneamente rimossa in Intune. Quando questa funzionalità viene rilasciata, questa nota verrà rimossa.

I certificati consentono di autenticare e proteggere l'accesso alle risorse aziendali, ad esempio una rete VPN o Wi-Fi. In questo articolo viene illustrato come esportare un certificato PKCS e quindi aggiungerlo a un profilo di Intune.

## <a name="requirements"></a>Requisiti

Per usare i certificati PKCS con Intune, verificare se è disponibile l'infrastruttura seguente:

- **Dominio di Active Directory**: tutti i server elencati in questa sezione devono essere aggiunti al dominio di Active Directory.

  Per altre informazioni sull'installazione e la configurazione di Active Directory Domain Services, vedere l'articolo relativo a [progettazione e pianificazione di AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autorità di certificazione** (CA): un'autorità di certificazione (CA) globale (enterprise)

  Per altre informazioni sull'installazione e la configurazione di Servizi certificati Active Directory (AD CS), vedere la [guida dettagliata di AD CS](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune richiede l'esecuzione di Servizi certificati Active Directory con un'autorità di certificazione globale (enterprise), non con un'autorità di certificazione autonoma (Standalone).

- **Un client**: per la connessione all'autorità di certificazione globale (enterprise)

- **Certificato radice**: una copia esportata del certificato radice dall'autorità di certificazione globale (enterprise)

- **Connettore di certificati di Microsoft Intune**: usare il portale di Azure per scaricare il programma di installazione del **Connettore di certificati** (**NDESConnectorSetup.exe**). 

  Il connettore elabora le richieste di certificati PKCS usati per l'autenticazione o la firma S/MIME della posta elettronica.

  Il connettore di certificati del servizio Registrazione dispositivi di rete supporta anche la modalità FIPS (Federal Information Processing Standard). FIPS non è obbligatorio, ma è possibile emettere e revocare i certificati quando è abilitato.

- **Connettore di certificati PFX per Microsoft Intune**: se si prevede di usare la crittografia S/MIME per la posta elettronica, scaricare dal portale di Azure il programma di installazione del **connettore di certificati PFX per Microsoft Intune** ( **PfxCertificateConnectorBootstrapper.exe**). Il connettore elabora le richieste di file PFX importati in Intune per la crittografia S/MIME della posta elettronica per un utente specifico.

- **Windows Server**: ospita quanto segue:

  - Connettore di certificati di Microsoft Intune (NDESConnectorSetup.exe) per gli scenari di autenticazione e firma S/MIME della posta elettronica
  - Connettore di certificati PFX per Microsoft Intune (PfxCertificateConnectorBootstrapper.exe) per gli scenari di crittografia S/MIME della posta elettronica.

  È possibile eseguire entrambi i connettori (**il connettore di certificati di Microsoft Intune** e **il connettore di certificati PFX per Microsoft Intune**) nello stesso server.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Esportare il certificato radice dall'autorità di certificazione globale (enterprise)

Per l'autenticazione con una VPN, una rete Wi-Fi e altre risorse, è necessario un certificato della CA radice o intermedio per ogni dispositivo. La procedura seguente illustra come ottenere il certificato richiesto dall'autorità di certificazione globale (enterprise).

1. Accedere all'autorità di certificazione globale (enterprise) con un account che abbia privilegi amministrativi.
2. Aprire un prompt dei comandi come amministratore.
3. Esportare il certificato CA radice (estensione CER) in un percorso a cui è possibile accedere in un secondo momento.
4. Al termine della procedura guidata, prima di chiuderla, fare clic su **Avvia l'interfaccia utente di Connettore di certificati**.

   `certutil -ca.cert certnew.cer`

   Per altre informazioni, vedere [Operazioni certutil per la gestione dei certificati](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configurare i modelli di certificato nell'autorità di certificazione

1. Accedere all'autorità di certificazione globale (enterprise) con un account che abbia privilegi amministrativi.
2. Aprire la console **Autorità di certificazione**, fare clic con il pulsante destro del mouse su **Modelli di certificato** e selezionare **Gestisci**.
3. Trovare il modello di certificato **User**, fare clic con il pulsante destro del mouse su di esso e scegliere **Duplica modello**. Vengono visualizzate le **proprietà di Nuovo modello**.

    > [!NOTE]
    > Per scenari di firma e crittografia S/MIME della posta elettronica, molti amministratori usano certificati separati per la firma e la crittografia. Se si usa Servizi certificati Microsoft Active Directory, è possibile usare il modello **Solo firma di Exchange** per i certificati di firma S/MIME per la posta elettronica e il modello **Utente di Exchange** per i certificati di crittografia S/MIME.  Se si usa un'autorità di certificazione di terze parti, è consigliabile rivedere il materiale sussidiario per configurare i modelli di firma e crittografia.

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
13. Per consentire al server di gestire i certificati per conto di utenti e dispositivi registrati in Intune, eseguire i passaggi seguenti:

    1. Fare clic con il pulsante destro del mouse sull'autorità di certificazione e scegliere **Proprietà**.
    2. Nella scheda della sicurezza aggiungere l'account computer relativo al server in cui sono in esecuzione i connettori (il **connettore di certificati di Microsoft Intune** e il **connettore di certificati PFX per Microsoft Intune**). Assegnare all'account le autorizzazioni **Rilascio e gestione certificati** e **Richiesta certificati**.

14. Disconnettersi dall'autorità di certificazione globale (enterprise).

## <a name="download-install-and-configure-the-certificate-connectors"></a>Scaricare, installare e configurare i connettori di certificati

### <a name="microsoft-intune-certificate-connector"></a>Connettore di certificati di Microsoft Intune

> [!IMPORTANT] 
> Connettore di certificati di Microsoft Intune **deve** essere installato in un server Windows separato. Non può essere installato nell'Autorità di certificazione (CA) emittente.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Autorità di certificazione** > **Aggiungi**.
3. Scaricare e salvare il file del connettore. Salvarlo in una posizione accessibile dal server in cui si intende installare il connettore.

    ![ConnectorDownload][ConnectorDownload]

4. Al termine del download, accedere al server. Quindi:

    1. Assicurarsi che sia installato.NET Framework 4.5 o versione successiva, perché è richiesto da NDES Connector per i certificati. .NET Framework 4.5 è incluso automaticamente con Windows Server 2012 R2 e versioni più recenti.
    2. Eseguire il programma di installazione (NDESConnectorSetup.exe) e accettare il percorso predefinito. Il connettore viene installato in `\Program Files\Microsoft Intune\NDESConnectorUI`. Selezionare **Distribuzione PFX** nelle opzioni di installazione. Continuare e completare l'installazione.
    3. Per impostazione predefinita, il servizio Connector viene eseguito con l'account di sistema locale. Se è necessario un proxy per l'accesso a Internet, verificare che l'account del servizio locale possa accedere alle impostazioni del proxy nel server.

5. NDES Connector apre la scheda **Registrazione**. Per abilitare la connessione a Intune, selezionare **Accedi** e specificare un account con autorizzazioni amministrative globali.
6. Nella scheda **Avanzate** è consigliabile lasciare selezionata l'opzione **Usa l'account di sistema del computer (impostazione predefinita)**.
7. **Applica** > **Chiudi**
8. Tornare al portale di Azure (**Intune** > **Configurazione dispositivo** > **Autorità di certificazione**). Dopo alcuni istanti, viene visualizzato un segno di spunta verde e lo **stato della connessione** è **attivo**. Il server del connettore ora può comunicare con Intune.

> [!NOTE]
> Il supporto di TLS 1.2 è incluso con il connettore di certificati di Microsoft Intune. Se pertanto il server in cui è installato il connettore di certificati di Microsoft Intune supporta TLS 1.2, viene usato questo protocollo. Se il server non supporta TLS 1.2, viene usato TLS 1.1. Attualmente, TLS 1.1 viene usato per l'autenticazione tra i dispositivi e il server.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>Connettore di certificati PFX per Microsoft Intune

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Autorità di certificazione** > **Aggiungi**
3. Scaricare e salvare il connettore di certificati PFX per Microsoft Intune. Salvarlo in una posizione accessibile dal server in cui si intende installare il connettore.
4. Al termine del download, accedere al server. Quindi:

    1. Assicurarsi che sia installato.NET Framework 4.6 o versione successiva, perché è richiesto dal connettore di certificati PFX per Microsoft Intune. Se .NET Framework 4.6 non è installato, il programma di installazione lo installa automaticamente.
    2. Eseguire il programma di installazione (PfxCertificateConnectorBootstrapper.exe) e accettare il percorso predefinito. Il connettore viene installato in `Program Files\Microsoft Intune\PFXCertificateConnector`.
    3. Il servizio Connector viene eseguito con l'account di sistema locale. Se è necessario un proxy per l'accesso a Internet, verificare che l'account del servizio locale possa accedere alle impostazioni del proxy nel server.

5. Dopo l'installazione, il connettore di certificati PFX per Microsoft Intune consente di aprire la scheda **Registrazione**. Per abilitare la connessione a Intune, selezionare **Accedi** e specificare un account con autorizzazioni di amministratore globale o di amministratore di Intune.
6. Chiudere la finestra.
7. Tornare al portale di Azure (**Intune** > **Configurazione dispositivo** > **Autorità di certificazione**). Dopo alcuni istanti, viene visualizzato un segno di spunta verde e lo **stato della connessione** è **attivo**. Il server del connettore ora può comunicare con Intune.

## <a name="create-a-trusted-certificate-profile"></a>Creare un profilo certificato attendibile

1. Nel [portale di Azure](https://portal.azure.com) passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**.

   ![NavigateIntune][NavigateIntune]

2. Immettere le seguenti proprietà:

    - **Nome** del profilo
    - Inserire eventualmente una descrizione
    - **Piattaforma** in cui distribuire il profilo
    - Impostare **Tipo di profilo** su **Certificato attendibile**

3. Accedere a **Impostazioni** e specificare il file CER del certificato CA radice esportato in precedenza.

   > [!NOTE]
   > In base alla piattaforma selezionata nel **passaggio 3**, si può avere la possibilità di scegliere l'**archivio di destinazione** per il certificato.

   ![ProfileSettings][ProfileSettings]

4. Selezionare **OK** > **Crea** per salvare il profilo.
5. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creare un profilo certificato PKCS

1. Nel [portale di Azure](https://portal.azure.com) passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
2. Immettere le seguenti proprietà:

    - **Nome** del profilo
    - Inserire eventualmente una descrizione
    - **Piattaforma** in cui distribuire il profilo
    - Impostare **Tipo di profilo** su **Certificato PKCS**

3. Accedere a **Impostazioni** e immettere le proprietà seguenti:

    - **Soglia di rinnovo (%)**: il valore consigliato è 20%.
    - **Periodo di validità del certificato**: se il modello di certificato non è stato cambiato, questa opzione può essere impostata su un anno.
    - **Provider di archiviazione chiavi (KSP)**: per Windows, selezionare la posizione in cui archiviare le chiavi nel dispositivo.
    - **Autorità di certificazione**: visualizza il nome di dominio completo (FQDN, Fully Qualified Domain Name) interno dell'autorità di certificazione globale (enterprise).
    - **Nome dell'autorità di certificazione**: specifica il nome dell'autorità di certificazione globale (enterprise), ad esempio "Contoso Certification Authority" (Autorità di certificazione Contoso).
    - **Nome del modello di certificato**: nome del modello creato in precedenza. Ricordarsi che, per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*.
    - **Formato nome soggetto**: impostare questa opzione su **Nome comune**, se non diversamente richiesto.
    - **Nome alternativo del soggetto**: impostare questa opzione su **Nome dell'entità utente (UPN)**, se non diversamente richiesto.

4. Selezionare **OK** > **Crea** per salvare il profilo.
5. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Creare un profilo certificato PKCS importato

È possibile importare in Intune certificati rilasciati in precedenza per un utente specifico da qualsiasi autorità di certificazione. I certificati importati vengono installati in ogni dispositivo registrato dall'utente in questione. La crittografia S/MIME della posta elettronica rappresenta lo scenario più comune per l'importazione di certificati PFX esistenti in Intune. Un utente può avere più certificati con cui crittografare la posta elettronica. Le chiavi private di tali certificati devono essere presenti in tutti i dispositivi perché sia possibile decrittografare la posta elettronica crittografata in precedenza.

Per importare certificati in Intune, è possibile usare i [cmdlet di PowerShell disponibili in GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Dopo aver importato i certificati in Intune, creare un profilo **certificato PKCS importato** e assegnarlo ai gruppi di Azure Active Directory.

1. Nel [portale di Azure](https://portal.azure.com) passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
2. Immettere le seguenti proprietà:

    - **Nome** del profilo
    - Inserire eventualmente una descrizione
    - **Piattaforma** in cui distribuire il profilo
    - Impostare **Tipo di profilo** su **Certificato PKCS importato**

3. Accedere a **Impostazioni** e immettere le proprietà seguenti:

    - **Scopo designato**: scopo designato dei certificati importati per questo profilo. Un amministratore può avere certificati importati con scopi designati diversi (ad esempio autenticazione, firma S/MIME o crittografia S/MIME). Lo scopo designato selezionato nel profilo certificato corrisponde al profilo certificato con i certificati importati corretti.
    - **Periodo di validità del certificato**: se il modello di certificato non è stato cambiato, questa opzione può essere impostata su un anno.
    - **Provider di archiviazione chiavi (KSP)**: per Windows, selezionare la posizione in cui archiviare le chiavi nel dispositivo.

4. Selezionare **OK** > **Crea** per salvare il profilo.
5. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](device-profile-assign.md).

## <a name="next-steps"></a>Passaggi successivi
[Usare i certificati SCEP](certificates-scep-configure.md) o [Rilasciare certificati PKCS da un servizio Web di gestione PKI Symantec](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Passare a Intune nel portale di Azure e creare un nuovo profilo per un certificato attendibile"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Creare un profilo e caricare un certificato attendibile"
[ConnectorDownload]: ./media/certificates-download-connector.png "Scaricare il connettore di certificati dal portale di Azure"  
