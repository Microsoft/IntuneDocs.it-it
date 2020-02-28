---
title: Risoluzione dei problemi di registrazione dei dispositivi Windows in Microsoft Intune
titleSuffix: Microsoft Intune
description: Suggerimenti per la risoluzione di alcuni dei problemi più comuni quando si registrano dispositivi Windows in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dae8e92209a8640ab3254e073d3043d390c3791b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514252"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Risolvere i problemi di registrazione dei dispositivi Windows in Microsoft Intune

Questo articolo aiuta gli amministratori di Intune a comprendere e risolvere i problemi durante la registrazione di dispositivi Windows in Intune.

## <a name="prerequisites"></a>Prerequisiti
Prima di iniziare la risoluzione dei problemi, è importante raccogliere alcune informazioni di base. Queste informazioni possono essere utili per comprendere meglio il problema e ridurre il tempo necessario per trovare una soluzione.

Raccogliere le informazioni seguenti sul problema:
- All'utente è assegnata una licenza di Intune valida? Per poter registrare i dispositivi, è necessario che agli utenti venga assegnata la licenza necessaria.
- Nel dispositivo Windows è installato l'aggiornamento più recente? Alcune funzionalità di Intune funzionano solo con la versione più recente di Windows. Tramite Windows Update sono disponibili numerose correzioni per i problemi noti. L'applicazione di tutti gli aggiornamenti più recenti spesso corregge i problemi di registrazione dei dispositivi Windows. 
- Qual è il messaggio di errore esatto?
- Dove viene visualizzato il messaggio di errore?
- Quando è iniziato il problema? La registrazione è già stata elaborata? 
- Quale piattaforma (Android, iOS/iPad, Windows) presenta il problema?
- Quanti utenti sono interessati? Sono interessati tutti gli utenti o solo alcuni?
- Quanti dispositivi sono interessati? Sono interessati tutti i dispositivi o solo alcuni?
- Che cos'è l'autorità MDM?
- Come viene eseguita la registrazione? BYOD (Bring Your Own Device) o Apple Device Enrollment Program (DEP) comprende profili di registrazione?

## <a name="error-messages"></a>Messaggi di errore

### <a name="this-user-is-not-authorized-to-enroll"></a>L'utente non è autorizzato per la registrazione.

Errore 0x801c003: "L'utente non è autorizzato per la registrazione. È possibile provare a ripetere l'operazione oppure contattare l'amministratore di sistema comunicando il codice errore (0x801c0003)".
Errore 80180003: "Si è verificato un errore. L'utente non è autorizzato per la registrazione. È possibile provare a ripetere l'operazione oppure contattare l'amministratore di sistema comunicando il codice errore 80180003".

**Causa:** una delle condizioni seguenti: 

- L'utente ha già registrato il numero massimo di dispositivi consentiti in Intune.    
- Il dispositivo è bloccato dalle restrizioni relative al tipo di dispositivo.    
- Il computer esegue Windows 10 Home ma la registrazione in Intune o l'aggiunta ad Azure AD è supportata solo in Windows 10 Pro e versioni superiori.

#### <a name="resolution"></a>Soluzione
Esistono diverse soluzioni possibili per questo problema:

##### <a name="remove-devices-that-were-enrolled"></a>Rimuovere i dispositivi registrati
1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).    
2. Passare a **Utenti** > **Tutti gli utenti**.    
3. Selezionare l'account utente interessato e quindi fare clic su **Dispositivi**.    
4. Selezionare tutti i dispositivi inutilizzati o indesiderati e quindi fare clic su **Elimina**. 

##### <a name="increase-the-device-enrollment-limit"></a>Aumentare il limite di registrazione dispositivi

> [!NOTE]
> Questo metodo aumenta il limite per la registrazione di dispositivi per tutti gli utenti, non solo per l'utente interessato.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Passare a **Dispositivi** > **Restrizioni registrazione** > **Impostazione predefinita** (in **Restrizione sul limite di dispositivi**) > **Proprietà** > **Modifica** (accanto a **Limite di dispositivi**) > aumentare il **Limite di dispositivi** (massimo 15) > **Verifica e salva**.    
 

##### <a name="check-device-type-restrictions"></a>Controllare le restrizioni sul tipo di dispositivi
1. Accedere all'[Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) con un account amministratore globale.
2. Passare a **Dispositivi** > **Restrizioni registrazione** e quindi selezionare la restrizione **predefinita** in **Restrizioni sul tipo di dispositivi**.    
3. Selezionare **Piattaforme** e quindi selezionare **Consenti** per **Windows (MDM)** .

    > [!IMPORTANT]
    > Se l'impostazione corrente è già **Consenti**, modificarla in **Blocca**, salvare l'impostazione e quindi modificarla di nuovo in **Consenti** e salvarla nuovamente. Questa operazione reimposta l'impostazione di registrazione.

4. Attendere circa 15 minuti e quindi registrare di nuovo il dispositivo interessato.    

##### <a name="upgrade-windows-10-home"></a>Aggiornare Windows 10 Home
[Aggiornare Windows 10 Home a Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) o a una versione superiore. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Utente non autorizzato per la registrazione

Errore 0x801c0003: "This user is not allowed to enroll" (L'utente non è autorizzato per la registrazione). "È possibile riprovare o contattare l'amministratore di sistema specificando il codice errore 801c0003".

**Motivo:** l'impostazione **Gli utenti possono aggiungere dispositivi ad Azure AD** corrisponde a **Nessuno**. Questa impostazione impedisce a nuovi utenti di aggiungersi a dispositivi Azure AD. La registrazione di Intune ha quindi esito negativo.

#### <a name="resolution"></a>Soluzione
1. Accedere al [portale di Azure](https://portal.azure.com/) come amministratore.    
2. Passare ad **Azure Active Directory** > **Dispositivi** > **Impostazioni dei dispositivi**.    
3. Impostare**Gli utenti possono aggiungere dispositivi ad Azure AD** su **Tutti**.    
4. Registrare di nuovo il dispositivo.   

### <a name="the-device-is-already-enrolled"></a>Il dispositivo è già registrato.

Errore 8018000a: "Si è verificato un problema. Il dispositivo è già registrato.  È possibile provare a ripetere l'operazione oppure contattare l'amministratore di sistema comunicando il codice errore 8018000a".

**Causa:** una delle condizioni seguenti è vera:
- Un altro utente ha già registrato il dispositivo in Intune o ha aggiunto il dispositivo ad Azure AD. Per stabilire se è effettivamente così, passare a **Impostazioni** > **Account** > **Accesso società**. Cercare un messaggio simile al seguente: "Un altro utente del sistema è già connesso all'azienda o all'istituto di istruzione. Rimuovi la connessione all'azienda o all'istituto di istruzione e riprova".    

#### <a name="resolution"></a>Soluzione

Per risolvere il problema, usare uno dei metodi seguenti:

##### <a name="remove-the-other-work-or-school-account"></a>Rimuovere l'altro account aziendale o dell'istituto di istruzione
1. Disconnettersi da Windows, quindi accedere usando l'altro account registrato o aggiunto al dispositivo.    
2. Passare a **Impostazioni** > **Account** > **Accesso società** e quindi rimuovere l'account aziendale o dell'istituto di istruzione.
3. Disconnettersi da Windows e quindi accedere con il proprio account.    
4. Registrare il dispositivo in Intune o aggiungere il dispositivo ad Azure AD. 



### <a name="this-account-is-not-allowed-on-this-phone"></a>Account non consentito per il telefono in uso

Errore: "This account is not allowed on this phone" (Questo account non è consentito in questo telefono). "Make sure the information you provided is correct, and then try again or request support from your company" (Assicurarsi che le informazioni specificate siano corrette e quindi riprovare o chiedere assistenza alla società).

**Motivo:** l'utente che ha tentato di registrare il dispositivo non ha una licenza di Intune valida.

#### <a name="resolution"></a>Soluzione
Assegnare una licenza di Intune valida all'utente e quindi registrare il dispositivo.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>L'endpoint delle condizioni per l'utilizzo della gestione di dispositivi mobili (MDM, Mobile Device Management) non è configurato correttamente.

**Causa:** una delle condizioni seguenti è vera: 
 - Nel tenant viene usata la gestione di dispositivi mobili per Office 365 e Intune e l'utente che prova a registrare il dispositivo non ha una licenza di Intune o di Office 365 valida.     
- I termini e le condizioni della gestione di dispositivi mobili in Azure AD sono vuoti o non contengono l'URL corretto.    

#### <a name="resolution"></a>Soluzione

Per risolvere il problema, usare uno dei metodi seguenti: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Assegnare una licenza valida all'utente
Passare all'[Interfaccia di amministrazione di Microsoft 365](https://portal.office.com/adminportal/home) e quindi assegnare una licenza di Intune o di Office 365 all'utente.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Correggere l'URL delle condizioni per l'utilizzo di MDM
  1. Accedere al [portale di Azure](https://portal.azure.com/) e quindi selezionare **Azure Active Directory**.    
  2. Selezionare **Mobility (MDM e MAM)** e quindi fare clic su **Microsoft Intune**.    
  3. Selezionare **Ripristina URL MDM predefiniti**. Verificare che l'**URL delle condizioni per l'utilizzo di MDM** sia impostato su **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Scegliere **Salva**.    


### <a name="something-went-wrong"></a>Si è verificato un errore.

Errore 80180026: "Si è verificato un errore. Assicurarsi che le informazioni di accesso siano corrette e che l'azienda usi questa funzionalità. È possibile provare a ripetere l'operazione oppure contattare l'amministratore di sistema comunicando il codice errore 80180026".

**Motivo:** questo errore può verificarsi quando si tenta di aggiungere un computer Windows 10 ad Azure AD e sono soddisfatte entrambe le condizioni seguenti: 
- In Azure è abilitata la registrazione automatica MDM.    
- Nel computer Windows 10 è installato il client del computer Intune (agente del computer Intune).

#### <a name="resolution"></a>Soluzione
Per risolvere il problema, usare uno dei metodi seguenti:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Disabilitare la registrazione automatica MDM in Azure.
1. Accedere al [portale di Azure](https://portal.azure.com/).    
2. Passare ad **Azure Active Directory** > **Mobility (MDM e MAM)**  > **Microsoft Intune**.    
3. Impostare **Ambito utente MDM** su **Nessuno** e quindi fare clic su **Salva**.    
     
##### <a name="uninstall"></a>Uninstall
Disinstallare l'agente client del computer Intune dal computer.    

### <a name="the-software-cannot-be-installed"></a>Impossibile installare il software.

Errore: "Impossibile installare il software, 0x80cf4017".

**Motivo:** il software client non è aggiornato.

#### <a name="resolution"></a>Soluzione
1. Accedere a [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Passare ad **Amministrazione** > **Download software client** e quindi fare clic su **Scarica software client**.    
3. Salvare il pacchetto di installazione e quindi installare il software client. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>Il certificato dell'account non è valido e potrebbe essere scaduto.

Errore: "Il certificato dell'account non è valido e potrebbe essere scaduto, 0x80cf4017".

**Motivo:** il software client non è aggiornato.

#### <a name="resolution"></a>Soluzione
1. Accedere a [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Passare ad **Amministrazione** > **Download software client** e quindi fare clic su **Scarica software client**.    
3. Salvare il pacchetto di installazione e quindi installare il software client.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Versione di Windows non supportata dall'organizzazione 

Errore: "Si è verificato un problema. La tua organizzazione non supporta questa versione di Windows.  (0x80180014) "

**Motivo:** la registrazione MDM di Windows è disabilitata nel tenant di Intune.

#### <a name="resolution"></a>Soluzione
Per risolvere il problema in un ambiente Intune autonomo, seguire questa procedura: 
 
1. Nell'[Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **Restrizioni registrazione** > scegliere una restrizione di tipo di dispositivo.    
2. Scegliere **Proprietà** > **Modifica** (accanto a **Impostazioni piattaforma**) > **Consenti** per **Windows (MDM)** .    
3. Fare clic su **Verifica e salva**.    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Errore di installazione durante la registrazione in blocco

**Motivo:** gli account utente Azure AD nel pacchetto di account (Package_GUID) per il pacchetto di provisioning corrispondente non sono autorizzati ad aggiungere dispositivi ad Azure AD. Questi account Azure AD vengono creati automaticamente quando si configura un pacchetto di provisioning con Progettazione configurazione di Windows o l'app Configura PC scolastici e questi account vengono quindi usati per aggiungere i dispositivi ad Azure AD.

#### <a name="resolution"></a>Soluzione
1. Accedere al [portale di Azure](https://portal.azure.com/) come amministratore.    
2. Passare ad **Azure Active Directory > Dispositivi > Impostazioni dei dispositivi**.    
3. Impostare**Gli utenti possono aggiungere dispositivi ad Azure AD** su **Tutti** o **Selezionato**.

   Se si sceglie **Selezionato**, fare clic su **Selezionato** e quindi su **Aggiungi membri** per aggiungere tutti gli utenti che possono aggiungere i propri dispositivi ad Azure AD. Verificare che siano stati aggiunti tutti gli account Azure AD per il pacchetto di provisioning.
 
Per altre informazioni su come creare un pacchetto di provisioning per Progettazione configurazione di Windows, vedere [Creare un pacchetto di provisioning per Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Per altre informazioni sull'app Configura PC scolastici, vedere [Usare l'app Configura PC scolastici](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Registrazione MDM automatica non riuscita 

Quando si tenta di registrare automaticamente un dispositivo Windows 10 con Criteri di gruppo, si verificano i problemi seguenti: 
- In Utilità di pianificazione, in **Microsoft** > **Windows** > **EnterpriseMgmt**, il risultato dell'ultima esecuzione dell'attività **Schedule created by enrollment client for automatically enrolling in MDM from AAD** (Pianificazione creata dal client di registrazione per la registrazione automatica in MDM da AAD) è il seguente: **Event 76 Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x8018002b)** (Evento 76: registrazione MDM automatica: non riuscita (codice errore Win32 sconosciuto: 0x8018002b))       
- In Visualizzatore eventi, in **Registri applicazioni e servizi/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-provider/Admin** viene registrato l'evento seguente:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Causa:** una delle condizioni seguenti è vera: 
- Il nome UPN contiene un dominio non verificato o non instradabile, ad esempio .local (come joe@contoso.local).    
- L'impostazione di **Ambito utente MDM** corrisponde a **Nessuno**. 

#### <a name="resolution"></a>Soluzione
Se il nome UPN contiene un dominio non verificato o non instradabile, eseguire questa procedura: 

1. Nel server che esegue Active Directory Domain Services (AD DS) aprire **Utenti e computer di Active Directory** digitando **dsa.msc** nella finestra di dialogo **Esegui** e quindi fare clic su **OK**.    
2. Fare clic su **Utenti** nel proprio dominio e quindi eseguire le operazioni seguenti:  
    - Se è interessato un solo utente, fare clic con il pulsante destro del mouse sull'utente e quindi scegliere **Proprietà**. Nella scheda **Account**, nell'elenco a discesa del suffisso UPN in **Nome accesso utente**, selezionare un suffisso UPN valido, ad esempio contoso.com, e quindi fare clic su **OK**.    
    - Se sono interessati più utenti, selezionare gli utenti, selezionare il menu **Azione** e quindi fare clic su **Proprietà**. Nella scheda **Account** selezionare la casella di controllo **Suffisso UPN**, selezionare un suffisso UPN valido, ad esempio contoso.com, nell'elenco a discesa e quindi fare clic su **OK**.
3. Attendere la sincronizzazione successiva o forzare una sincronizzazione Delta dal server di sincronizzazione eseguendo i comandi seguenti in un prompt di PowerShell con privilegi elevati:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Se l'impostazione di **Ambito utente MDM** corrisponde a **Nessuno**, eseguire questa procedura: 
 
1. Accedere al [portale di Azure](https://portal.azure.com/) e quindi selezionare **Azure Active Directory**.
2. Selezionare **Mobility (MDM e MAM)** e quindi selezionare **Microsoft Intune**.    
3. Impostare **Ambito utente MDM** su **Tutti**. In alternativa, impostare **Ambito utente MDM** su **Alcuni** e selezionare i gruppi che possono registrare automaticamente i propri dispositivi Windows 10.    
4. Impostare **Ambito utente MAM** su **Nessuno**.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Errore durante la creazione del profilo di Autopilot

**Motivo:** il formato di denominazione specificato del modello di nome dispositivo non soddisfa i requisiti. Ad esempio, sono stati usati caratteri minuscoli per la macro Serial, come %serial% anziché %SERIAL%.

#### <a name="resolution"></a>Soluzione

Verificare che il formato di denominazione soddisfi i requisiti seguenti:

- Creare un nome univoco per i dispositivi. I nomi non devono superare i 15 caratteri e possono contenere lettere (a-z, A-Z), numeri (0-9) e trattini (-).
- I nomi non possono contenere solo numeri.
- I nomi non devono contenere alcuno spazio vuoto.
- Usare la macro %SERIAL% per aggiungere un numero di serie specifico per l'hardware. In alternativa, usare la macro %RAND:<n. di cifre>% per aggiungere una stringa casuale di numeri. La stringa contiene <n. di cifre > cifre. Ad esempio, MYPC-% RAND:6% genera un nome, ad esempio MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Si è verificato un errore. OOBEIDPS.

**Motivo:** questo problema si verifica in presenza di un proxy, di un firewall o di un altro dispositivo di rete che blocca l'accesso al provider di identità (IdP).

#### <a name="resolution"></a>Soluzione
Assicurarsi che l'accesso necessario ai servizi basati su Internet per Autopilot non sia bloccato. Per altre informazioni, vedere [Requisiti di rete di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Registrazione del dispositivo per la gestione per dispositivi mobili (errore: 3, 0x801C03EA)

**Motivo:** il dispositivo ha un chip TPM che supporta la versione 2.0, ma non è stato ancora aggiornato a tale versione.

#### <a name="resolution"></a>Soluzione
Aggiornare il chip TPM alla versione 2.0.

Se il problema persiste, controllare se lo stesso dispositivo si trova in due gruppi assegnati, a ognuno dei quali è assegnato un profilo di Autopilot diverso. Se si trova in due gruppi, determinare quale profilo di Autopilot deve essere applicato al dispositivo e quindi rimuovere l'assegnazione dell'altro profilo.

Per altre informazioni su come distribuire un dispositivo Windows in modalità tutto schermo con Autopilot, vedere [Distribuzione di un chiosco multimediale con Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Protezione dell'hardware (errore: 0x800705B4)

Errore 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Motivo:** il dispositivo Windows di destinazione non soddisfa uno dei requisiti seguenti:

- Il dispositivo deve avere un chip TPM 2.0 fisico. I dispositivi con TPM virtuali, ad esempio le macchine virtuali Hyper-V, o i chip TPM 1.2 non funzionano con la modalità di distribuzione automatica.
- Nel dispositivo deve essere in esecuzione una delle versioni di Windows seguenti:
    - Windows 10 build 1703 o versione successiva.
    - Se si usa Aggiunta ad Azure AD ibrido, Windows 10 build 1809 o versione successiva.


#### <a name="resolution"></a>Soluzione
Verificare che il dispositivo di destinazione soddisfi entrambi i requisiti descritti nella sezione **Motivo**.

Per altre informazioni su come distribuire un dispositivo Windows in modalità tutto schermo con Autopilot, vedere [Distribuzione di un chiosco multimediale con Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Si è verificato un errore. Codice errore 80070774.

Errore 0x80070774: si è verificato un errore. Assicurarsi che le informazioni di accesso siano corrette e che l'azienda usi questa funzionalità. È possibile provare a ripetere l'operazione oppure contattare l'amministratore di sistema comunicando il codice errore 80070774.

Questo problema si verifica in genere prima che il dispositivo venga riavviato in uno scenario Autopilot di Azure AD ibrido, se si verifica il timeout del dispositivo durante la schermata di accesso iniziale. Significa che il controller di dominio non è stato trovato o raggiunto correttamente a causa di problemi di connettività. In alternativa, significa che il dispositivo è entrato in uno stato che non ne consente l'aggiunta al dominio.

**Motivo:** la causa più comune è l'uso di Aggiunta ad Azure AD ibrido e la configurazione della funzionalità Assegna utente nel profilo di Autopilot. Se usata, durante la visualizzazione della schermata di accesso iniziale la funzionalità Assegna utente esegue un'aggiunta ad Azure AD per il dispositivo, ponendolo in uno stato a causa del quale non può unirsi al dominio locale. La funzionalità Assegna utente deve quindi essere usata solo all'interno di scenari Autopilot di Aggiunta ad Azure AD standard.  La funzionalità non deve essere usata all'interno di scenari Aggiunta ad Azure AD ibrido.

#### <a name="resolution"></a>Soluzione

1. Nell'[Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere > **Dispositivi** > **Windows** > **Dispositivi Windows**.
2. Selezionare il dispositivo in cui si è verificato il problema > fare clic sui puntini di sospensione (...) all'estrema destra.
3. Selezionare **Annulla l'assegnazione utente** e attendere il completamento del processo.
4. Verificare che il profilo di Autopilot di Azure AD ibrido sia assegnato prima di ritentare la Configurazione guidata.

#### <a name="second-resolution"></a>Seconda soluzione
Se il problema persiste, nel server che ospita il connettore Intune di aggiunta a un dominio offline, verificare se l'evento con ID 30312 è registrato nel log del servizio del connettore ODJ. L'evento 30312 è simile al seguente:

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

Questo problema è in genere causato dalla delega non corretta di autorizzazioni all'unità organizzativa in cui vengono creati i dispositivi Windows Autopilot. Per altre informazioni, vedere [Aumentare il limite di account computer nell'unità organizzativa](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Aprire **Utenti e computer di Active Directory (DSA.msc)** .
2. Fare clic con il pulsante destro del mouse sull'unità organizzativa che si userà per creare i computer aggiunti ad Azure AD ibrido > **Delega controllo**.
3. Nella procedura **Delega guidata del controllo** scegliere **Avanti** > **Aggiungi** > **Tipi di oggetto**.
4. Nella finestra di dialogo **Tipi di oggetto** selezionare la casella di controllo **Computer** > **OK**.
5. Nel riquadro **Seleziona utenti**, **computer** o **gruppi**, nella casella **Immettere i nomi degli oggetti da selezionare**, immettere il nome del computer in cui è installato Connector.
6. Selezionare **Controlla nomi** per convalidare l'immissione> **OK** > **Avanti**.
7. Selezionare **Crea un'attività personalizzata per eseguire la delega** > **Avanti**.
8. Selezionare la casella di controllo **Solo i seguenti oggetti contenuti nella cartella**, quindi selezionare le caselle di controllo **Oggetto computer**, **Crea gli oggetti selezionati in questa cartella** e **Elimina gli oggetti selezionati in questa cartella**.
9. Selezionare **Avanti**.
10. In **Autorizzazioni** selezionare la casella di controllo **Controllo completo**. Questa azione consente di selezionare tutte le altre opzioni.
11. Selezionare **Avanti** > **Fine**.

### <a name="the-enrollment-status-page-times-out-before-the-sign-in-screen"></a>La pagina Stato della registrazione raggiunge il timeout prima della schermata di accesso

**Motivo:** questo problema può comparire se si verificano tutte le condizioni seguenti:
- Si sta usando la pagina Stato della registrazione per tenere traccia di app di Microsoft Store per le aziende.
- Sono attivi criteri di accesso condizionale di Azure AD che richiedono che un dispositivo sia contrassegnato come controllo conforme.
- Questi criteri si applicano a tutte le app cloud e a Windows.

#### <a name="resolution"></a>Risoluzione:
Tentare una delle operazioni seguenti:
- Assegnare i criteri di conformità di Intune ai dispositivi. Assicurarsi che sia possibile determinare la conformità prima dell'accesso utente.
- Usare licenze offline per le app dello Store. In questo modo, il client Windows non deve eseguire alcuna verifica con Microsoft Store prima di determinare la conformità del dispositivo.



## <a name="next-steps"></a>Passaggi successivi

- [Risolvere i problemi di registrazione dei dispositivi in Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Porre una domanda nel forum di Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Controllare il blog del team di supporto di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Controllare il blog di Microsoft Enterprise Mobility + Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Ottenere supporto per Microsoft Intune](../fundamentals/get-support.md)
- [Individuare gli errori di registrazione di co-gestione](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
