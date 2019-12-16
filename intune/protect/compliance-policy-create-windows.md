---
title: Impostazioni di conformità di Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi Windows 10, Windows Holographic e Surface Hub in Microsoft Intune. Verificare la conformità nella versione minima e massima del sistema operativo, impostare le restrizioni relative alla password e la lunghezza, verificare la presenza di soluzioni antivirus di partner, abilitare la crittografia nell'archiviazione dati e così via.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60a87340c1a275b8fb878ef2f3891cca23fc9c85
ms.sourcegitcommit: f5108039f0ade52e95ea3ac1da1aa16d02224af3
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2019
ms.locfileid: "74946660"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di Windows 10 e versioni successive per contrassegnare un dispositivo come conforme o non conforme in Intune

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi Windows 10 e versioni successive in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per richiedere BitLocker, impostare una versione minima e massima del sistema operativo, impostare un livello di rischio tramite Microsoft Defender Advanced Threat Protection (ATP) e così via.

Questa funzionalità si applica a:

- Windows 10 e versioni successive
- Windows Holographic for Business
- Surface Hub

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). In **Piattaforma** selezionare **Windows 10 e versioni successive**.

## <a name="device-health"></a>Integrità del dispositivo

### <a name="windows-health-attestation-service-evaluation-rules"></a>Regole di valutazione del servizio di attestazione dell'integrità di Windows

- **Richiedi BitLocker**:  
   Crittografia unità BitLocker di Windows crittografa tutti i dati archiviati nel volume del sistema operativo Windows. BitLocker utilizza il Trusted Platform Module (TPM) per proteggere il sistema operativo Windows e i dati utente. Consente anche di assicurarsi che un computer non venga manomesso, anche se viene perso, rubato o lasciato incustodito. Se il computer è dotato di un TPM compatibile, BitLocker usa il TPM per bloccare le chiavi di crittografia che proteggono i dati. Di conseguenza, non è possibile accedere alle chiavi finché il TPM non verifica lo stato del computer.  

   - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
   - **Rendi obbligatorio**: il dispositivo può proteggere dall'accesso non autorizzato i dati archiviati nell'unità quando il sistema viene spento o viene messo in stato di ibernazione.  


- **Richiedi l'abilitazione dell'avvio sicuro nel dispositivo**:  
    - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
    - **Richiedi** : il sistema viene forzato a eseguire l'avvio in uno stato attendibile predefinito. I componenti di base usati per avviare il computer devono avere le firme di crittografia corrette considerate attendibili dall'organizzazione che ha prodotto il dispositivo. Il firmware UEFI verifica la firma prima di consentire l'avvio del computer. Se tutti i file vengono manomessi, con conseguente compromissione della firma, il sistema non viene avviato.

  > [!NOTE]
  > L'impostazione **Richiedi l'abilitazione dell'avvio sicuro nel dispositivo** è supportata in alcuni dispositivi TPM 1.2 e 2.0. Per i dispositivi che non supportano TPM 2.0 o versione successiva, lo stato dei criteri in Intune viene indicato come **Non conforme**. Per altre informazioni sulle versioni supportate, vedere [Attestazione dell'integrità dei dispositivi](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Richiedi l'integrità del codice**:  
  l'integrità del codice è una funzionalità che verifica l'integrità di un driver o di un file di sistema ogni volta che viene caricato in memoria.
  - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
  -  **Rendi obbligatorio**: richiedere l'integrità del codice che rileva se un driver o un file di sistema non firmato viene caricato nel kernel. Viene anche rilevato se un file di sistema viene modificato da software dannoso o eseguito da un account utente con privilegi di amministratore.

Altre risorse:

- Per informazioni dettagliate sul funzionamento del servizio di attestazione dell'integrità, vedere [CSP di attestazione dell'integrità](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Support Tip: Using Device Health Attestation Settings as Part of Your Intune Compliance Policy ](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643) (Suggerimento per il supporto: uso delle impostazioni per l'attestazione dell'integrità dei dispositivi come parte dei criteri di conformità di Intune)

## <a name="device-properties"></a>Proprietà dispositivo

### <a name="operating-system-version"></a>Versione del sistema operativo

- **Versione minima del sistema operativo**:  
  immettere la versione minima consentita, usando il formato **principale.secondario.build.numero aggiornamento cumulativo**. Per ottenere il valore corretto, aprire un prompt dei comandi e digitare `ver`. Il comando `ver` restituisce la versione nel formato seguente:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando un dispositivo ha una versione precedente rispetto alla versione del sistema operativo immessa, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo. Dopo l'aggiornamento, potrà accedere alle risorse aziendali.

- **Versione massima del sistema operativo**:  
  immettere la versione massima consentita, usando il formato **principale.secondario.build.numero revisione**. Per ottenere il valore corretto, aprire un prompt dei comandi e digitare `ver`. Il comando `ver` restituisce la versione nel formato seguente:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente finale viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché la regola non viene modificata in modo da consentire la versione del sistema operativo.

- **Versione minima del sistema operativo per dispositivi mobili**:  
  immettere la versione minima consentita, usando il formato principale.secondario.numero di build.

  Quando un dispositivo ha una versione precedente rispetto alla versione del sistema operativo immessa, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo. Dopo l'aggiornamento, potrà accedere alle risorse aziendali.

- **Versione massima del sistema operativo per dispositivi mobili**:  
  immettere la versione massima consentita, usando il formato principale.secondario.numero di build.

  Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente finale viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché la regola non viene modificata in modo da consentire la versione del sistema operativo.

- **Build valide dei sistemi operativi**:  
  immettere un intervallo per le versioni dei sistemi operativi accettabili, incluse la versione minima e quella massima. È anche possibile **esportare** un elenco di file con valori delimitati da virgole (CSV) dei numeri di build del sistema operativo consentiti.

## <a name="configuration-manager-compliance"></a>Conformità di Configuration Manager

Si applica solo ai dispositivi con co-gestione che eseguono Windows 10 e versioni successive. I dispositivi solo Intune restituiscono uno stato non disponibile.

- **Richiedi la conformità del dispositivo da System Center Configuration Manager**:  
  - **Non configurato** (*impostazione predefinita*): Intune non verifica la conformità delle impostazioni di Configuration Manager.
  - **Rendi obbligatorio**: richiedere la conformità di tutte le impostazioni (elementi di configurazione) in System Center Configuration Manager.  

    È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo non è conforme in Intune.

## <a name="system-security"></a>Protezione del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
  - **Rendi obbligatorio**: gli utenti devono immettere una password prima di accedere al dispositivo. 

- **Password semplici**:  
  - **Non configurato** (*impostazione predefinita*): gli utenti possono creare password semplici, ad esempio **1234** o **1111**.
  - **Blocca**: impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**.

- **Tipo di password**:  
  scegliere il tipo di password o il PIN obbligatorio. Le opzioni disponibili sono:
  - **Impostazione predefinita del dispositivo** (*impostazione predefinita*): richiedere una password, un PIN numerico o un PIN alfanumerico
  - **Numerico** : richiedere una password o un PIN numerico
  - **Alfanumerico** : richiedere una password o un PIN alfanumerico.  
  
  Quando è impostato su *alfanumerico*, sono disponibili le impostazioni seguenti:  
  - **Complessità password**:  
    Le opzioni disponibili sono: 
    - **Richiedi cifre e lettere minuscole** (*impostazione predefinita*)
    - **Richiedi cifre, lettere minuscole e lettere maiuscole**
    - **Richiedi cifre, lettere minuscole, lettere maiuscole e caratteri speciali**

    > [!TIP]
    > I criteri alfanumerici per le password possono essere complessi. Invitiamo gli amministratori a leggere i CSP per ulteriori informazioni:
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters consente CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Lunghezza minima password**:  
  immettere il numero minimo di cifre o caratteri che la password deve avere.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**:  
  immettere il tempo di inattività prima che l'utente debba immettere nuovamente la password.

- **Scadenza password (giorni)** :  
  immettere il numero di giorni che mancano alla scadenza della password, quando l'utente deve creare una nuova password (da 1 a 730).

- **Numero di password precedenti di cui impedire il riutilizzo**:  
  immettere il numero di password usate in precedenza che non è possibile usare.

- **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività (Mobile e Holographic)** :  
  - **Non configurato** (*impostazione predefinita*)
  - **Rendi obbligatorio**: richiedere agli utenti di immettere la password ogni volta che il dispositivo torna attivo dopo uno stato di inattività.

  > [!IMPORTANT]
  > La modifica dei requisiti per la password in un desktop di Windows interessa gli utenti al successivo accesso, ossia quando il dispositivo passa dallo stato inattivo allo stato attivo. Agli utenti con password che soddisfano i requisiti viene comunque chiesto di cambiare la password.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**:  
  Questa impostazione si applica a tutte le unità in un dispositivo.
  - **Non configurato** (*impostazione predefinita*)
  - **Rendi obbligatorio**: usare *Rendi obbligatorio* per crittografare l'archivio dati nei dispositivi.

  > [!NOTE]
  > L'impostazione **Encryption of data storage on a device** (Crittografia dell'archivio dati in un dispositivo) verifica in modo generico la presenza di crittografia nel dispositivo. Per impostare la crittografia in modo più affidabile, è consigliabile usare **Richiedi BitLocker**, che sfrutta Attestazione dell'integrità del dispositivo di Windows per convalidare lo stato di Bitlocker a livello di TPM.

### <a name="device-security"></a>Sicurezza del dispositivo  

- **Firewall**:  
  - **Non configurato** (*impostazione predefinita*): Intune non controlla Microsoft Defender Firewall né modifica le impostazioni esistenti.
  - **Richiedi** : attivare Microsoft Defender Firewall e impedire agli utenti di disattivarla.  

  [CSP firewall](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Se il dispositivo si sincronizza immediatamente dopo un riavvio o esegue immediatamente la sincronizzazione dalla sospensione, questa impostazione potrebbe indicare un **errore**. Questo scenario potrebbe non influire sullo stato di conformità generale del dispositivo. Per valutare nuovamente lo stato di conformità, [sincronizzare manualmente il dispositivo](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

- **Trusted Platform Module (TPM)** :  
  - **Non configurato** (*impostazione predefinita*): Intune non controlla la versione del chip TPM nel dispositivo.
  - **Richiedi** : Intune verifica la conformità della versione del chip TPM. Il dispositivo è conforme se la versione del chip TPM è maggiore di **0** (zero). Il dispositivo non è conforme se non è presente una versione del TPM nel dispositivo.  

  [DeviceStatus CSP-nodo DeviceStatus/TPM/SpecificationVersion](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivirus**:  
  - **Non configurato** (*impostazione predefinita)* : Intune non verifica la presenza di soluzioni antivirus installate nel dispositivo. 
  - **Rendi obbligatorio**: verificare la conformità usando le soluzioni antivirus registrate nel [Centro sicurezza PC Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), ad esempio Symantec e Microsoft Defender.

- **Antispyware**:  
  - **Non configurato** (*impostazione predefinita*): Intune non verifica la presenza di soluzioni antispyware installate nel dispositivo.
  - **Rendi obbligatorio**: verificare la conformità usando le soluzioni antispyware registrate nel [Centro sicurezza PC Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), ad esempio Symantec e Microsoft Defender.  

### <a name="defender"></a>Defender

*Con Windows 10 desktop sono supportate le seguenti impostazioni di conformità.*

- **Microsoft Defender Antimalware**:  
  - **Non configurato** (*impostazione predefinita*): Intune non controlla il servizio né modifica le impostazioni esistenti.
  - **Richiedi** : attiva il servizio anti-malware di Microsoft Defender e impedisce agli utenti di disattivarlo.

- **Versione minima di Microsoft Defender antimalware**:  
  Immettere la versione minima consentita del servizio Microsoft Defender anti-malware. Immettere ad esempio `4.11.0.0`. Quando viene lasciato vuoto, è possibile usare qualsiasi versione di Microsoft Defender anti-malware Service.  

  *Per impostazione predefinita, non è configurata alcuna versione*.

- **Microsoft Defender antimalware Security Intelligence**è aggiornato:  
  Controlla gli aggiornamenti della protezione da virus e minacce per la protezione di Windows nei dispositivi.
  - **Non configurato** (*impostazione predefinita*): Intune non impone alcun requisito.
  - **Richiedi** : impone l'aggiornamento di Microsoft Defender Security Intelligence.

  [Defender/Health/SignatureOutOfDate CSP](https://docs.microsoft.com/windows/client-management/mdm/defender-csp)
  
  Per ulteriori informazioni, vedere [Security Intelligence Updates for Microsoft Defender Antivirus and other Microsoft antimalware](https://www.microsoft.com/en-us/wdsi/defenderupdates).

- **Protezione in tempo reale**:  
  - **Non configurato** (*impostazione predefinita*): Intune non controlla questa funzionalità né modifica le impostazioni esistenti.
  - **Richiedi** : consente di attivare la protezione in tempo reale, che esegue l'analisi di malware, spyware e altro software indesiderato.  

  [CSP Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Regole di Microsoft Defender Advanced Threat Protection

- **Richiedi che il dispositivo si trovi al massimo al punteggio di rischio del computer**:  
  usare questa impostazione per considerare la valutazione del rischio dei servizi Threat Defense come condizione di conformità. Scegliere il livello di minaccia massimo consentito:
  - **Non configurato** (*impostazione predefinita*)  
  - **Cancella**: questa opzione è la più sicura poiché il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce esistenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato non conforme.
  - **Alto**: questa opzione è la meno sicura e consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.
  
  Per configurare Microsoft Defender ATP (Advanced Threat Protection) come servizio di difesa dalle minacce, vedere [Abilitare Microsoft Defender ATP con l'accesso condizionale](advanced-threat-protection.md).


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business usa la piattaforma **Windows 10 e versioni successive**. Windows Holographic for Business supporta l' impostazione seguente:

- **Sicurezza del sistema** > **Crittografia** > **Crittografia dell'archivio dati nel dispositivo**.

Per verificare la crittografia del dispositivo in Microsoft HoloLens, vedere [Verificare la crittografia dispositivo](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub usa la piattaforma **Windows 10 e versioni successive**. I dispositivi Surface Hub sono supportati sia per la conformità sia per l'accesso condizionale. Per abilitare queste funzionalità in Surface Hub, è consigliabile [abilitare la registrazione automatica di Windows 10](../enrollment/windows-enroll.md) in Intune (richiede Azure Active Directory (Azure AD)) e impostare i dispositivi Surface Hub come gruppi di dispositivi. Per la conformità e per il funzionamento dell'accesso condizionale, i dispositivi Surface Hub devono essere aggiunti ad Azure AD.

Per informazioni, vedere [Configurare la registrazione dei dispositivi Windows](../enrollment/windows-enroll.md).

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](../fundamentals/scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi Windows 8.1](compliance-policy-create-windows-8-1.md).
