---
title: Usare certificati PFX importati in Microsoft Intune - Azure | Microsoft Docs
description: Usare i certificati PKCS (Public Key Cryptography Standards) importati con Microsoft Intune, inclusa l'importazione di certificati, la configurazione del modello di certificato, l'installazione del connettore di certificati PFX importati di Intune e creare un profilo per il certificato PKCS importato.
keywords: ''
author: ralms
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: fead8b9d69f5356876c0b3a2a4ce02e9b754128e
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999335"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Configurare e usare i certificati PKCS importati con Intune

Microsoft Intune supporta l'uso di certificati PKCS importati, comunemente usati per la crittografia S/MIME con profili di posta elettronica. Determinati profili di posta elettronica in Intune supportano un'opzione che consente di abilitare S/MIME, dove è possibile definire un certificato di firma S/MIME e un certificato di crittografia S/MIME.

La crittografia S/MIME è complessa perché la posta elettronica è crittografata con un certificato specifico. È necessario avere la chiave privata del certificato che ha crittografato il messaggio di posta elettronica nel dispositivo in cui si sta leggendo il messaggio, in modo che possa essere decrittografato. I certificati di crittografia vengono rinnovati regolarmente, quindi potrebbe essere necessario avere la cronologia della crittografia in tutti i dispositivi per assicurarsi di poter leggere i messaggi più datati.  Poiché si deve usare lo stesso certificato nei vari dispositivi, non è possibile usare i profili dei certificati [SCEP](certificates-scep-configure.md) o [PKCS](certficates-pfx-configure.md) per questo scopo, poiché i meccanismi di recapito dei certificati inviano un unico certificato per dispositivo. 

Per altre informazioni sull'uso di s/MIME con Intune, vedere [Usare s/MIME per crittografare la posta elettronica](certificates-s-mime-encryption-sign.md).

## <a name="requirements"></a>Requisiti

Per usare i certificati PKCS importati con Intune, è necessaria l'infrastruttura seguente:

- **Connettore di certificati PFX per Microsoft Intune**:  
  Ogni tenant di Intune supporta una sola istanza di questo connettore. È possibile installare questo connettore nello stesso server di un'istanza del connettore di certificati di Microsoft Intune.

  Questo connettore gestisce le richieste per i file PFX importati in Intune per la crittografia S/MIME della posta elettronica per un utente specifico.  

  Questo connettore consente l'aggiornamento automatico quando diventano disponibili nuove versioni. Per usare la funzionalità di aggiornamento, è necessario verificare che i firewall siano aperti per consentire al connettore di contattare **autoupdate.msappproxy.net** sulla porta **443**.  

  Per altre informazioni su tutti gli endpoint di rete a cui accede il connettore, vedere [Requisiti di configurazione di rete di Intune e larghezza di banda](../fundamentals/network-bandwidth-use.md).


- **Windows Server**:  
  Usare Windows Server per ospitare il connettore di certificati PFX per Microsoft Intune.  Il connettore viene usato per elaborare le richieste per i certificati importati in Intune.

  Intune supporta l'installazione del *connettore di certificati di Microsoft Intune* nello stesso server del *connettore di certificati PFX per Microsoft Intune*.

  Per supportare il connettore, il server deve eseguire .NET 4.6 Framework o versione successiva. Se .NET 4.6 Framework non è installato quando si avvia l'installazione del connettore, il programma di installazione del connettore lo installerà automaticamente.

- **Visual Studio 2015 o versione successiva** (facoltativo): Si usa Visual Studio per compilare il modulo PowerShell helper con i cmdlet per l'importazione dei certificati PFX in Microsoft Intune. Per ottenere i cmdlet helper di PowerShell, vedere [PFXImport PowerShell Project](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) su GitHub.

## <a name="how-it-works"></a>Come funziona

Quando si usa Intune per distribuire un **certificato PFX importato** a un utente, in aggiunta al dispositivo sono disponibili due componenti: 

- **Servizio Intune**: Archivia i certificati PFX in uno stato crittografato e gestisce la distribuzione del certificato al dispositivo dell'utente.  Le password che proteggono le chiavi private dei certificati vengono crittografate prima di essere caricate usando un modulo di protezione hardware o la crittografia di Windows, verificando che Intune non possa accedere alla chiave privata in qualsiasi momento.
- **Connettore di certificati PFX per Microsoft Intune**: Quando un dispositivo richiede un certificato PFX importato in Intune, la password crittografata, il certificato e la chiave pubblica del dispositivo vengono inviati al connettore.  Il connettore decrittografa la password usando la chiave privata locale e quindi crittografa di nuovo la password (e tutti i profili plist se si usa iOS) con la chiave del dispositivo prima di inviare di nuovo il certificato a Intune.  Intune recapita quindi il certificato al dispositivo e il dispositivo è in grado di decrittografarlo con la chiave privata del dispositivo e di installare il certificato.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>Scaricare, installare e configurare il connettore di certificati PFX per Microsoft Intune

1. Nel portale di [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) selezionare **Configurazione dispositivo** > **Connettori di certificati** > **Aggiungi**.

   ![Download del connettore di certificati PFX per Microsoft Intune](./media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

2. Seguire le indicazioni per scaricare il *connettore di certificati PFX per Microsoft Intune* in un percorso accessibile dal server in cui si intende installare il connettore.
3. Al termine del download, accedere al server ed eseguire il programma di installazione (PfxCertificateConnectorBootstrapper.exe).  
   - Quando si accetta il percorso di installazione predefinito, il connettore viene installato in `Program Files\Microsoft Intune\PFXCertificateConnector`.
   - Il servizio Connector viene eseguito con l'account di sistema locale. Se è necessario un proxy per l'accesso a Internet, verificare che l'account del servizio locale possa accedere alle impostazioni del proxy nel server.

4. Dopo l'installazione, il connettore di certificati PFX per Microsoft Intune consente di aprire la scheda **Registrazione**. Per abilitare la connessione a Intune, selezionare **Accedi** e specificare un account con autorizzazioni di amministratore globale o di amministratore di Intune.

   > [!WARNING]
   > Per impostazione predefinita, in Windows Server la **Configurazione sicurezza avanzata IE** è impostata su **On** e questo può causare problemi di accesso a Office 365.

5. Chiudere la finestra.
6. Nel portale di Intune tornare a **Configurazione dispositivo** > **Connettori di certificati**. Dopo alcuni istanti, viene visualizzato un segno di spunta verde e lo **stato della connessione** è **attivo**. Il server del connettore ora può comunicare con Intune.

## <a name="import-pfx-certificates-to-intune"></a>Importare certificati PFX in Intune

Usare [Microsoft Graph](https://docs.microsoft.com/graph) per importare i certificati PFX degli utenti in Intune. L'helper [PFXImport PowerShell Project su GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) offre i cmdlet che consentono di semplificare le operazioni.

Se si preferisce usare una soluzione personalizzata con Graph, usare il [tipo di risorsa userPFXCertificate](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>Creare i cmdlet "PFXImport PowerShell Project"

Per usare i cmdlet PowerShell, compilare il progetto autonomamente con Visual Studio. Il processo è semplice e, benché possa essere eseguito sul server, è consigliabile eseguirlo nella workstation.  

1. Passare alla radice del repository [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) su GitHub e quindi scaricare o clonare il repository con Git nel computer.

   ![Pulsante di download di GitHub](./media/certificates-imported-pfx-configure/github-download.png)

2. Passare a `.\Intune-Resource-Access-develop\src\PFXImportPowershell\` e aprire il progetto con Visual Studio usando il file **PFXImportPS.sln**.
3. In alto modificare **Debug** in **Versione**.
4. Passare a **Compila** e selezionare **Compila PFXImportPS**. Dopo alcuni istanti viene visualizzata la **conferma della compilazione riuscita** in basso a sinistra in Visual Studio.

   ![Opzione Compila di Visual Studio](./media/certificates-imported-pfx-configure/vs-build-release.png)

5. Il processo di compilazione crea una nuova cartella con il modulo PowerShell in `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   La cartella **Release** verrà usata per i passaggi successivi.

### <a name="create-the-encryption-public-key"></a>Creare la chiave pubblica di crittografia

Importare i certificati PFX e le relative chiavi private in Intune. La password che protegge la chiave privata è crittografata con una chiave pubblica archiviata in locale. È possibile usare la crittografia di Windows, un modulo di sicurezza hardware o un altro tipo di crittografia per generare e archiviare le coppie di chiavi pubblica/privata.  A seconda del tipo di crittografia usata, la coppia di chiavi pubblica/privata può essere esportata in formato di file per il backup.

Il modulo di PowerShell offre i metodi che consentono di creare una chiave usando la crittografia di Windows. È anche possibile usare altri strumenti per creare una chiave.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>Per creare la chiave di crittografia usando la crittografia di Windows

1. Copiare la cartella *Release* creata da Visual Studio nel server in cui è stato installato il **connettore di certificati PFX per Microsoft Intune**. La cartella contiene il modulo di PowerShell.  
2. Nel server aprire *PowerShell* come amministratore e quindi passare alla cartella *Release* che contiene il modulo di PowerShell.
3. Per importare il modulo, eseguire `Import-Module .\IntunePfxImport.psd1`.
4. Quindi, eseguire `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]  
   > Il provider da usare deve essere selezionato di nuovo quando si importano i certificati PFX. È possibile usare il **provider di archiviazione chiavi per software Microsoft**, sebbene sia supportato l'uso di un provider diverso. Anche il nome della chiave è solo un esempio ed è possibile usare un nome di chiave diverso a scelta.  

   Se si intende importare il certificato dalla workstation, è possibile esportare la chiave in un file con il comando seguente: `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path to write to>"`

   La chiave privata deve essere importata nel server che ospita il connettore di certificati PFX per Microsoft Intune in modo che i certificati PFX importati possano essere elaborati correttamente.  

#### <a name="to-use-a-hardware-security-module-hsm"></a>Per usare un modulo di protezione hardware  

È possibile usare un modulo di protezione hardware per generare e archiviare la coppia di chiavi pubblica/privata. Per altre informazioni, vedere la documentazione del fornitore del modulo di protezione hardware.

### <a name="import-pfx-certificates"></a>Importare i certificati PFX 

Il processo seguente usa i cmdlet PowerShell come esempio di importazione dei certificati PFX. È possibile scegliere opzioni diverse a seconda dei requisiti.

Le opzioni includono:  
- Scopo designato (raggruppa i certificati in base a un tag):  
  - non assegnato
  - smimeEncryption
  - smimeSigning


- Schema spaziatura interna:  
  - pkcs1
  - oaepSha1
  - oaepSha256
  - oaepSha384
  - oaepSha512

Selezionare il provider di archiviazione chiavi che corrisponde al provider usato per creare la chiave.

#### <a name="to-import-the-pfx-certificate"></a>Per importare il certificato PFX  

1. Esportare i certificati da un'autorità di certificazione (CA) seguendo la documentazione del provider.  Per i servizi certificati Microsoft Active Directory è possibile usare questo [script di esempio](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b).   
2. Nel server aprire *PowerShell* come amministratore e quindi passare alla cartella *Release* che contiene il modulo di PowerShell.
3. Per importare il modulo, eseguire `Import-Module .\IntunePfxImport.psd1`  
4. Per eseguire l'autenticazione a Graph di Intune, eseguire `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > Quando viene eseguita l'autenticazione per Graph, è necessario specificare le autorizzazioni per l'ID app. Se è la prima volta che si usa questa utilità, è necessario un *amministratore globale*. I cmdlet PowerShell usano lo stesso ID app usato con gli [esempi di PowerShell per Intune](https://github.com/microsoftgraph/powershell-intune-samples).   
5. Convertire la password per ogni file PFX che si sta importando in una stringa sicura eseguendo `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`.  
6. Per creare un oggetto **UserPFXCertificate**, eseguire `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>"`

   ad esempio `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption" "pkcs1"`

   > [!NOTE]  
   > Quando si importa il certificato da un sistema diverso dal server in cui è installato il connettore, usare il comando seguente che include il percorso del file di chiave: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. Importare l'oggetto **UserPFXCertificate** in Intune eseguendo `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`

8. Per verificare che il certificato è stato importato, eseguire `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UserList "<UserUPN>"`

Per altre informazioni sugli altri comandi disponibili, vedere il file Leggimi in [PFXImport PowerShell Project su GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Creare un profilo certificato PKCS importato

Dopo aver importato i certificati in Intune, creare un profilo **certificato PKCS importato** e assegnarlo ai gruppi di Azure Active Directory.

1. Nel portale di [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) passare a **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
2. Immettere le proprietà seguenti:

   - **Nome** del profilo
   - Inserire eventualmente una descrizione
   - **Piattaforma** in cui distribuire il profilo
   - Impostare **Tipo di profilo** su **Certificato PKCS importato**

3. Accedere a **Impostazioni** e immettere le proprietà seguenti:

   - **Scopo designato**: Specificare lo scopo designato dei certificati importati per questo profilo. Gli amministratori possono importare certificati con scopi designati diversi, ad esempio firma S/MIME o crittografia S/MIME. Lo scopo designato selezionato nel profilo certificato corrisponde al profilo certificato con i certificati importati corretti. Lo scopo designato è un tag usato per raggruppare i certificati importati e non garantisce che i certificati importati con tale tag soddisfino lo scopo designato.  
   - **Periodo di validità del certificato**: A meno che non sia stato modificato il periodo di validità nel modello di certificato, il valore predefinito di questa opzione è un anno.  
   - **Provider di archiviazione chiavi (KSP)** : per Windows, selezionare la posizione in cui archiviare le chiavi nel dispositivo.  

4. Selezionare **OK** > **Crea** per salvare il profilo.
5. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](../configuration/device-profile-assign.md).



