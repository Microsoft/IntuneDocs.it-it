---
title: Risoluzione dei problemi di registrazione dei dispositivi Windows in Microsoft Intune
titleSuffix: Microsoft Intune
description: Suggerimenti per la risoluzione di alcuni dei problemi più comuni quando si registrano i dispositivi Windows in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e8af18192a3a15fee15dd2204ada572e6a67be1c
ms.sourcegitcommit: 6c74ff568267d85fd1d44fda75e3e24ead87cb2b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2019
ms.locfileid: "70063013"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Risolvere i problemi di registrazione dei dispositivi Windows in Microsoft Intune

Questo articolo aiuta gli amministratori di Intune a comprendere e risolvere i problemi durante la registrazione di dispositivi Windows in Intune.

## <a name="prerequisites"></a>Prerequisiti
Prima di iniziare la risoluzione dei problemi, è importante raccogliere alcune informazioni di base. Queste informazioni possono essere utili per comprendere meglio il problema e ridurre il tempo necessario per trovare una soluzione.

Raccogliere le seguenti informazioni sul problema:
- È stata assegnata una licenza di Intune valida all'utente? Per poter registrare i dispositivi, è necessario che agli utenti venga assegnata la licenza necessaria.
- È installato l'aggiornamento più recente nel dispositivo Windows? Alcune funzionalità di Intune funzionano solo con la versione più recente di Windows. Sono disponibili numerose correzioni per i problemi noti disponibili tramite Windows Update. L'applicazione di tutti gli aggiornamenti più recenti spesso corregge un problema di registrazione dei dispositivi Windows. 
- Qual è il messaggio di errore esatto?
- Dove viene visualizzato il messaggio di errore?
- Quando è iniziato il problema? La registrazione è già stata elaborata? 
- Quale piattaforma (Android, iOS, Windows) presenta il problema?
- Quanti utenti sono interessati? Tutti gli utenti sono interessati o solo alcuni?
- Quanti dispositivi sono interessati? Tutti i dispositivi sono interessati o solo alcuni?
- Che cos'è l'autorità MDM? Se è System Center Configuration Manager, quale versione di Configuration Manager si sta usando?
- Come viene eseguita la registrazione? BYOD (Bring Your Own Device) o Apple Device Enrollment Program (DEP) con i profili di registrazione?

## <a name="error-messages"></a>Messaggi di errore

### <a name="this-user-is-not-authorized-to-enroll"></a>Questo utente non è autorizzato a eseguire la registrazione.

Errore 0x801c003: "l'utente non è autorizzato a eseguire la registrazione. È possibile riprovare o contattare l'amministratore di sistema con il codice di errore (0x801c0003). "
Errore 80180003: "Si è verificato un errore. Questo utente non è autorizzato a eseguire la registrazione. È possibile riprovare o contattare l'amministratore di sistema con il codice di errore 80180003 ".

**Motivo:** Una delle condizioni seguenti: 

- L'utente ha già registrato il numero massimo di dispositivi consentiti in Intune.    
- Il dispositivo è bloccato dalle restrizioni relative al tipo di dispositivo.    
- Il computer esegue Windows 10 Home. Tuttavia, la registrazione in Intune o l'aggiunta di Azure AD è supportata solo in Windows 10 Pro e versioni successive.

#### <a name="resolution"></a>Soluzione
Esistono diverse soluzioni possibili per questo problema:

##### <a name="remove-devices-that-were-enrolled"></a>Rimuovere i dispositivi registrati
1. Accedere al [portale di Azure](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).    
2. Passare a **utenti** > **tutti gli utenti**.    
3. Selezionare l'account utente interessato e quindi fare clic su **dispositivi**.    
4. Selezionare tutti i dispositivi inutilizzati o indesiderati, quindi fare clic su **Elimina**. 

##### <a name="increase-the-device-enrollment-limit"></a>Aumentare il limite di registrazione dispositivi

> [!NOTE]
> Questo metodo aumenta il limite di registrazione del dispositivo per tutti gli utenti, non solo per l'utente interessato.

1. Accedere al [portale di Azure](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).
2. Passare a **registrazione** > del dispositivo**Restrizioni registrazione**e quindi selezionare **limitazioni limite del dispositivo**.    
3. Aumentare il valore del **limite del dispositivo**. 

##### <a name="check-device-type-restrictions"></a>Controllare le restrizioni sul tipo di dispositivi
1. Accedere al [portale di Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) con un account di amministratore globale.
2. Passare a **registrazione** > del dispositivo**Restrizioni registrazione**, quindi selezionare la restrizione **predefinita** in **restrizioni del tipo di dispositivo**.    
3. Selezionare **piattaforme**, quindi selezionare **Consenti** per **Windows (MDM)** .

    > [!IMPORTANT]
    > Se l'impostazione corrente è già **consentita**, modificarla in **blocco**, salvare l'impostazione e quindi modificarla di nuovo per **consentire** e salvare di nuovo l'impostazione. Questa operazione Reimposta l'impostazione di registrazione.

4. Attendere circa 15 minuti, quindi registrare di nuovo il dispositivo interessato.    

##### <a name="upgrade-windows-10-home"></a>Aggiornare Windows 10 Home
[Aggiornare Windows 10 Home a Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) o a una versione successiva. 



### <a name="this-user-is-not-allowed-to-enroll"></a>L'utente non è autorizzato a eseguire la registrazione.

Errore 0x801c0003: "l'utente non è autorizzato a eseguire la registrazione. È possibile riprovare o contattare l'amministratore di sistema con il codice di errore 801c0003. "

**Motivo:** Gli **utenti possono aggiungere dispositivi a Azure ad** impostazione è impostata su **nessuno**. In questo modo si impedisce ai nuovi utenti di aggiungersi ai dispositivi Azure AD. Di conseguenza, la registrazione di Intune ha esito negativo.

#### <a name="resolution"></a>Soluzione
1. Accedere al [portale di Azure](https://portal.azure.com/) come amministratore.    
2. Passare a **Azure Active Directory** > **dispositivi** > **Impostazioni dispositivo**.    
3. Impostare**Gli utenti possono aggiungere dispositivi ad Azure AD** su **Tutti**.    
4. Registrare di nuovo il dispositivo.   

### <a name="the-device-is-already-enrolled"></a>Il dispositivo è già registrato.

Errore 8018000a: "si è verificato un problema. Il dispositivo è già registrato.  È possibile contattare l'amministratore di sistema con il codice di errore 8018000a. "

**Motivo:** Una delle condizioni seguenti è vera:
- Un altro utente ha già registrato il dispositivo in Intune o è stato aggiunto al dispositivo per Azure AD. Per determinare se questo è il caso, passare a **Impostazioni** > **account** > **accesso**società. Cercare un messaggio simile al seguente: "un altro utente del sistema è già connesso a un lavoro o a un'istituto di istruzione. Rimuovere la connessione aziendale o dell'Istituto di istruzione e riprovare ".    
- Il Configuration Manager agente client è installato nel computer.    

#### <a name="resolution"></a>Soluzione

Per risolvere il problema, usare uno dei metodi seguenti:

##### <a name="remove-the-other-work-or-school-account"></a>Rimuovere l'altro account aziendale o dell'Istituto di istruzione
1. Disconnettersi da Windows, quindi accedere usando l'altro account registrato o aggiunto al dispositivo.    
2. Passare a **Impostazioni** > **account** > **accesso attività**, quindi rimuovere l'account aziendale o dell'Istituto di istruzione.
3. Disconnettersi da Windows e quindi accedere con l'account.    
4. Registrare il dispositivo in Intune o aggiungere il dispositivo a Azure AD. 

##### <a name="remove-the-configuration-manager-client"></a>Rimuovere il client di Configuration Manager
Rimuovere il client di Configuration Manager, quindi registrare di nuovo il dispositivo.



### <a name="this-account-is-not-allowed-on-this-phone"></a>Questo account non è consentito in questo telefono.

Errore: "questo account non è consentito in questo telefono. Verificare che le informazioni fornite siano corrette, quindi riprovare o richiedere supporto dall'azienda. "

**Motivo:** L'utente che ha tentato di registrare il dispositivo non dispone di una licenza di Intune valida.

#### <a name="resolution"></a>Soluzione
Assegnare una licenza di Intune valida all'utente e quindi registrare il dispositivo.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>L'endpoint delle condizioni per l'utilizzo di MDM non è configurato correttamente.

**Motivo:** Una delle condizioni seguenti è vera: 
 - Si usa la gestione di dispositivi mobili (MDM) per Office 365 e Intune nel tenant e l'utente che prova a registrare il dispositivo non dispone di una licenza di Intune valida o di una licenza di Office 365.     
- I termini e le condizioni MDM in Azure AD sono vuoti o non contengono l'URL corretto.    

#### <a name="resolution"></a>Soluzione

Per risolvere il problema, usare uno dei metodi seguenti: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Assegnare una licenza valida all'utente
Passare all'interfaccia di [amministrazione di Microsoft 365](https://portal.office.com/adminportal/home)e quindi assegnare una licenza di Intune o Office 365 all'utente.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Correggere l'URL delle condizioni per l'utilizzo di MDM
  1. Accedere al [portale di Azure](https://portal.azure.com/) e quindi selezionare **Azure Active Directory**.    
  2. Selezionare **Mobility (MDM e MAM)** , quindi fare clic su **Microsoft Intune**.    
  3. Selezionare **Ripristina URL MDM predefiniti**. Verificare che l' **URL delle condizioni per l'utilizzo di MDM** sia impostato su **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Scegliere **Salva**.    


### <a name="something-went-wrong"></a>Si è verificato un errore.

Errore 80180026: "Si è verificato un errore. Confermare di usare le informazioni di accesso corrette e che l'organizzazione usa questa funzionalità. È possibile riprovare o contattare l'amministratore di sistema con il codice di errore 80180026 ".

**Motivo:** Questo errore può verificarsi quando si tenta di aggiungere un computer Windows 10 a Azure AD e sono soddisfatte entrambe le condizioni seguenti: 
- La registrazione automatica di MDM è abilitata in Azure.    
- Il client PC Intune (agente PC Intune) o l'agente client di Configuration Manager è installato nel computer Windows 10.

#### <a name="resolution"></a>Soluzione
Per risolvere il problema, usare uno dei metodi seguenti:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Disabilitare la registrazione automatica MDM in Azure.
1. Accedere al [portale di Azure](https://portal.azure.com/).    
2. Passare a **Azure Active Directory** > **Mobility (MDM e MAM)**  > **Microsoft Intune**.    
3. Impostare **ambito utente MDM** su **nessuno**, quindi fare clic su **Salva**.    
     
##### <a name="uninstall"></a>Uninstall
Disinstallare il client PC Intune o Configuration Manager agente client dal computer.    

### <a name="the-software-cannot-be-installed"></a>Impossibile installare il software.

Errore: "Impossibile installare il software, 0x80cf4017."

**Motivo:** Il software client non è aggiornato.

#### <a name="resolution"></a>Soluzione
1. Accedere a [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Passare ad **Amministrazione** > **Download software client**, quindi fare clic su **Scarica software client**.    
3. Salvare il pacchetto di installazione, quindi installare il software client. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>Il certificato dell'account non è valido e potrebbe essere scaduto.

Errore: "Il certificato dell'account non è valido e potrebbe essere scaduto, 0x80cf4017".

**Motivo:** Il software client non è aggiornato.

#### <a name="resolution"></a>Soluzione
1. Accedere a [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Passare ad **Amministrazione** > **Download software client**, quindi fare clic su **Scarica software client**.    
3. Salvare il pacchetto di installazione, quindi installare il software client.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>L'organizzazione non supporta questa versione di Windows. 

Errore: "si è verificato un problema. L'organizzazione non supporta questa versione di Windows.  (0x80180014) "

**Motivo:** La registrazione di Windows MDM è disabilitata nel tenant di Intune.

#### <a name="resolution"></a>Soluzione
Per risolvere il problema in un ambiente Intune autonomo, attenersi alla procedura seguente: 
 
1. Accedere al [portale di Azure](https://portal.azure.com/) come amministratore.    
2. Selezionare **Intune** a sinistra e quindi passare > a registrazione del **dispositivo** **Restrizioni registrazione**.    
3. In **restrizioni sul tipo di dispositivi**fare clic su **piattaforme**, quindi selezionare **Consenti** per **Windows (MDM)** .    
4. Fare clic su **Save**.    
 
Per risolvere questo problema in MDM ibrido con Intune e Configuration Manager, seguire questa procedura: 
1. Aprire la console di Configuration Manager.    
2. Selezionare **Amministrazione**, quindi fare clic su **servizi cloud**.    
3. Fare clic con il pulsante destro del mouse su **Microsoft Intune sottoscrizione**e quindi scegliere **Configura piattaforme > Windows**.    
4. Selezionare **Abilita registrazione** > Windows**applica** > **OK**.  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Si è verificato un errore durante l'installazione durante la registrazione in blocco.

**Motivo:** Gli account utente Azure AD nel pacchetto di account (Package_GUID) per il rispettivo pacchetto di provisioning non possono aggiungere dispositivi ai Azure AD. Questi account di Azure AD vengono creati automaticamente quando si configura un pacchetto di provisioning con Windows Configuration designer (WCD) o l'app set up School PC e questi account vengono quindi usati per aggiungere i dispositivi ai Azure AD.

#### <a name="resolution"></a>Soluzione
1. Accedere al [portale di Azure](https://portal.azure.com/) come amministratore.    
2. Passare a **Azure Active Directory > dispositivi > impostazioni del dispositivo**.    
3. Impostare**Gli utenti possono aggiungere dispositivi ad Azure AD** su **Tutti** o **Selezionato**.

   Se si sceglie **selezionato**, fare clic su **selezionato**e quindi su **Aggiungi membri** per aggiungere tutti gli utenti che possono aggiungere i propri dispositivi a Azure ad. Verificare che siano stati aggiunti tutti gli account Azure AD per il pacchetto di provisioning.
 
Per altre informazioni su come creare un pacchetto di provisioning per Windows Configuration designer, vedere [creare un pacchetto di provisioning per Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Per altre informazioni sull'app per la configurazione dei PC scolastici, vedere [usare l'app per la configurazione dei PC scolastici](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Registrazione MDM automatica: non riuscita 

Quando si tenta di registrare automaticamente un dispositivo Windows 10 con Criteri di gruppo, si verificano i problemi seguenti: 
- In utilità di pianificazione, in **Microsoft** > **Windows** > **EnterpriseMgmt**, il risultato dell'ultima esecuzione della **pianificazione creata dal client di registrazione per la registrazione automatica in MDM dall'attività AAD** è il seguente: **Evento 76: registrazione MDM automatica: non riuscita (codice errore Win32 sconosciuto: 0x8018002b)**       
- In Visualizzatore eventi, l'evento seguente viene registrato in **registri applicazioni e servizi/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-provider/admin**:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Motivo:** Una delle condizioni seguenti è vera: 
- Il nome UPN contiene un dominio non verificato o non instradabile, ad esempio. local ( joe@contoso.locallike).    
- L' **ambito utente MDM** è impostato su **None**. 

#### <a name="resolution"></a>Soluzione
Se il nome UPN contiene un dominio non verificato o non instradabile, attenersi alla seguente procedura: 

1. Nel server in cui viene eseguito Active Directory Domain Services (AD DS), aprire **Active Directory utenti e computer** digitando **DSA. msc** nella finestra di dialogo **Esegui** , quindi fare clic su **OK**.    
2. Fare clic su **utenti** nel dominio, quindi eseguire le operazioni seguenti:  
    - Se è presente un solo utente interessato, fare clic con il pulsante destro del mouse sull'utente e quindi scegliere **Proprietà**. Nella scheda **account** , nell'elenco a discesa SUFFISSo UPN in **nome accesso utente**, selezionare un suffisso UPN valido, ad esempio contoso.com, quindi fare clic su **OK**.    
    - Se sono presenti più utenti interessati, selezionare gli utenti dal menu **azione** , quindi fare clic su **Proprietà**. Nella scheda **account** selezionare la casella di controllo **suffisso UPN** , selezionare un suffisso UPN valido, ad esempio contoso.com, nell'elenco a discesa, quindi fare clic su **OK**.
3. Attendere la sincronizzazione successiva o forzare una sincronizzazione Delta dal server di sincronizzazione eseguendo i comandi seguenti in un prompt di PowerShell con privilegi elevati:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Se l' **ambito utente MDM** è impostato su **None**, attenersi alla procedura seguente: 
 
1. Accedere al [portale di Azure](https://portal.azure.com/) e quindi selezionare **Azure Active Directory**.
2. Selezionare **Mobility (MDM e MAM)** , quindi selezionare **Microsoft Intune**.    
3. Impostare l' **ambito utente MDM** su **tutti**. In alternativa, impostare l' **ambito utente MDM** su **some**e selezionare i gruppi che possono registrare automaticamente i dispositivi Windows 10.    
4. Impostare l' **ambito utente Mam** su **None**.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Si è verificato un errore durante la creazione del profilo di Autopilot.

**Motivo:** Il formato di denominazione specificato del modello di nome dispositivo non soddisfa i requisiti. Si usi, ad esempio, il carattere minuscolo per la macro seriale, ad esempio% Serial% anziché% SERIAL%.

#### <a name="resolution"></a>Soluzione

Verificare che il formato di denominazione soddisfi i requisiti seguenti:

- Creare un nome univoco per i dispositivi. I nomi non devono superare i 15 caratteri e possono contenere lettere (a-z, A-Z), numeri (0-9) e trattini (-).
- I nomi non possono contenere solo numeri.
- I nomi non possono contenere spazio vuoto.
- Usare la macro %SERIAL% per aggiungere un numero di serie specifico per l'hardware. In alternativa, usare la macro% RAND: < # of digits >% per aggiungere una stringa casuale di numeri, la stringa contiene < numero di cifre > cifre. Ad esempio, MYPC-% RAND: 6% genera un nome, ad esempio MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Si è verificato un errore. OOBEIDPS.

**Motivo:** Questo problema si verifica in presenza di un proxy, di un firewall o di un altro dispositivo di rete che blocca l'accesso al provider di identità (IdP).

#### <a name="resolution"></a>Soluzione
Assicurarsi che l'accesso richiesto ai servizi basati su Internet per Autopilot non sia bloccato. Per ulteriori informazioni, vedere [requisiti di rete di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Registrazione del dispositivo per la gestione mobile (non riuscita: 3, 0x801C03EA).

**Motivo:** Il dispositivo dispone di un chip TPM che supporta la versione 2,0, ma non è ancora stato aggiornato alla versione 2,0.

#### <a name="resolution"></a>Soluzione
Aggiornare il chip TPM alla versione 2,0.

Se il problema persiste, controllare se lo stesso dispositivo si trova in due gruppi assegnati, a ogni gruppo assegnato un profilo di Autopilot diverso. Se si trova in due gruppi, determinare quale profilo di Autopilot deve essere applicato al dispositivo, quindi rimuovere l'assegnazione dell'altro profilo.

Per altre informazioni su come distribuire un dispositivo Windows in modalità tutto schermo con Autopilot, vedere [distribuzione di un chiosco multimediale con Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Protezione dell'hardware (errore: 0x800705B4).

Errore 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Motivo:** Il dispositivo Windows di destinazione non soddisfa uno dei requisiti seguenti:

- Il dispositivo deve avere un chip TPM 2,0 fisico. I dispositivi con TPMs virtuali, ad esempio macchine virtuali Hyper-V, o i chip TPM 1,2 non funzionano con la modalità di distribuzione automatica.
- Nel dispositivo deve essere in esecuzione una delle seguenti versioni di Windows:
    - Windows 10 Build 1703 o versione successiva.
    - Se viene usato Aggiunta ad Azure AD ibrido, Windows 10 Build 1809 o versione successiva.


#### <a name="resolution"></a>Soluzione
Verificare che il dispositivo di destinazione soddisfi entrambi i requisiti descritti nella sezione relativa alle **cause** .

Per altre informazioni su come distribuire un dispositivo Windows in modalità tutto schermo con Autopilot, vedere [distribuzione di un chiosco multimediale con Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Si è verificato un errore. Codice errore 80070774.

Errore 0x80070774: si è verificato un problema. Confermare di usare le informazioni di accesso corrette e che l'organizzazione usa questa funzionalità. È possibile riprovare o contattare l'amministratore di sistema con il codice di errore 80070774.

Questo problema si verifica in genere prima che il dispositivo venga riavviato in uno scenario di Azure AD ibrido Autopilot, quando si verifica il timeout del dispositivo durante la schermata di accesso iniziale. Significa che il controller di dominio non è stato trovato o è stato raggiunto correttamente a causa di problemi di connettività. O che il dispositivo sia entrato in uno stato che non può essere aggiunto al dominio.

**Motivo:** La causa più comune è che Aggiunta ad Azure AD ibrido viene usato e la funzionalità assegna utente è configurata nel profilo di Autopilot. Con la funzionalità assegna utente viene eseguito un Azure AD join sul dispositivo durante la schermata di accesso iniziale che inserisce il dispositivo in uno stato in cui non può partecipare al dominio locale. Pertanto, la funzionalità assegna utente deve essere utilizzata solo negli scenari con Azure AD di join di Autopilot standard.  La funzionalità non deve essere utilizzata negli scenari Aggiunta ad Azure AD ibrido.

#### <a name="resolution"></a>Soluzione

1. Passare alla registrazione del**dispositivo** > di **Intune** >  **dispositivi**di**registrazione** > Windows.
2. Selezionare il dispositivo in cui si è verificato il problema > fare clic sui puntini di sospensione (...) sul lato più a destra.
3. Selezionare **Annulla assegnazione utente** e attendere il completamento del processo.
4. Verificare che il profilo Azure AD ibrido Autopilot venga assegnato prima di ritentare la configurazione guidata.

#### <a name="second-resolution"></a>Seconda risoluzione
Se il problema persiste, nel server che ospita il connettore Intune di aggiunta al dominio offline, verificare se l'evento con ID 30312 è registrato nel registro del servizio del connettore ODJ. L'evento 30312 è simile al seguente:

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

Questo problema è in genere causato dalla delega non corretta delle autorizzazioni all'unità organizzativa in cui vengono creati i dispositivi Windows Autopilot. Per ulteriori informazioni, vedere [aumentare il limite di account computer nell'unità organizzativa](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Aprire **Utenti e computer di Active Directory (DSA.msc)**.
2. Fare clic con il pulsante destro del mouse sull'unità organizzativa che si userà per creare i computer aggiunti ad Azure AD ibrido > **Delega controllo**.
3. Nella procedura **Delega guidata del controllo** scegliere **Avanti** > **Aggiungi** > **Tipi di oggetto**.
4. Nella finestra di dialogo **Tipi di oggetto** selezionare la casella di controllo **Computer** > **OK**.
5. Nel riquadro **Seleziona utenti**, **computer** o **gruppi**, nella casella **Immettere i nomi degli oggetti da selezionare**, immettere il nome del computer in cui è installato Connector.
6. Selezionare **Controlla nomi** per convalidare la voce > **OK** > **Avanti**.
7. Selezionare **Crea un'attività personalizzata per eseguire la delega** > **Avanti**.
8. Selezionare la casella di controllo **Solo i seguenti oggetti contenuti nella cartella**, quindi selezionare le caselle di controllo **Oggetto computer**, **Crea gli oggetti selezionati in questa cartella** e **Elimina gli oggetti selezionati in questa cartella**.
9. Selezionare **Avanti**.
10. In **Autorizzazioni** selezionare la casella di controllo **Controllo completo**. Questa azione consente di selezionare tutte le altre opzioni.
11. Selezionare**fine** **successivo** > .

## <a name="next-steps"></a>Passaggi successivi

- [Risolvere i problemi di registrazione dei dispositivi in Intune](troubleshoot-device-enrollment-in-intune.md)
- [Porre una domanda nel forum di Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consulta il Blog del team di supporto di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Consulta il Blog di Microsoft Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Ottenere supporto per Microsoft Intune](https://docs.microsoft.com/intune/get-support) 
