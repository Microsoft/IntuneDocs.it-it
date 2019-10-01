---
title: Impostazioni di conformità di Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi Windows 10, Windows Holographic e Surface Hub in Microsoft Intune. Verificare la conformità nella versione minima e massima del sistema operativo, impostare le restrizioni relative alla password e la lunghezza, verificare la presenza di soluzioni antivirus di partner, abilitare la crittografia nell'archiviazione dati e così via.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cda6c5f5ffa2244376e318e81a38a1ed410a443f
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71305053"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di Windows 10 e versioni successive per contrassegnare un dispositivo come conforme o non conforme in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi Windows 10 e versioni successive in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per richiedere BitLocker, impostare una versione minima e massima del sistema operativo, impostare un livello di rischio tramite Microsoft Defender Advanced Threat Protection (ATP) e così via.

Questa funzionalità si applica a:

- Windows 10 e versioni successive
- Windows Holographic for Business
- Surface Hub

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). In **Piattaforma** selezionare **Windows 10 e versioni successive**.

## <a name="device-health"></a>Device health

- **Richiedi BitLocker**: se si imposta **Richiedi**, il dispositivo può proteggere dall'accesso non autorizzato i dati archiviati nell'unità, quando il sistema viene spento o viene messo in stato di ibernazione. Crittografia unità BitLocker di Windows crittografa tutti i dati archiviati nel volume del sistema operativo Windows. BitLocker usa il TPM per proteggere il sistema operativo Windows e i dati utente Consente anche di assicurarsi che un computer non venga manomesso, anche se viene perso, rubato o lasciato incustodito. Se il computer è dotato di un TPM compatibile, BitLocker usa il TPM per bloccare le chiavi di crittografia che proteggono i dati. Di conseguenza, non è possibile accedere alle chiavi finché il TPM non verifica lo stato del computer.

  Quando si imposta **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

- **Richiedi l'abilitazione dell'avvio sicuro nel dispositivo**: quando si imposta **Richiedi**, il sistema viene forzato per poter avviare uno stato attendibile predefinito. Quando è abilitato, i componenti di base usati per avviare il computer devono avere le firme di crittografia corrette considerate attendibili dall'organizzazione che ha prodotto il dispositivo. Il firmware UEFI verifica la firma prima di consentire l'avvio del computer. Se tutti i file vengono manomessi, con conseguente compromissione della firma, il sistema non viene avviato.

  Quando si imposta **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

  > [!NOTE]
  > L'impostazione **Richiedi l'abilitazione dell'avvio sicuro nel dispositivo** è supportata in alcuni dispositivi TPM 1.2 e 2.0. Per i dispositivi che non supportano TPM 2.0 o versione successiva, lo stato dei criteri in Intune viene indicato come **Non conforme**. Per altre informazioni sulle versioni supportate, vedere [Attestazione dell'integrità dei dispositivi](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Richiedi l'integrità del codice**: l'integrità del codice è una funzionalità che verifica l'integrità di un driver o di un file di sistema ogni volta che viene caricato in memoria. Quando si imposta **Richiedi**, l'integrità del codice rileva se un driver o un file di sistema non firmato viene caricato nel kernel. Rileva anche se un file di sistema viene modificato da software dannoso eseguito da un account utente con privilegi di amministratore.

  Quando si imposta **Non configurato** (impostazione predefinita), questa impostazione non viene tenuta in considerazione per la valutazione della conformità.

Altre risorse:

- In [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) (CSP di attestazione dell'integrità) sono disponibili informazioni su come funziona il servizio di attestazione dell'integrità.
- [Support Tip: Using Device Health Attestation Settings as Part of Your Intune Compliance Policy ](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643) (Suggerimento per il supporto: uso delle impostazioni per l'attestazione dell'integrità dei dispositivi come parte dei criteri di conformità di Intune)

## <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: immettere la versione minima ammessa, usando il formato **numerico major.minor.build.CU**. Per ottenere il valore corretto, aprire un prompt dei comandi e digitare `ver`. Il comando `ver` restituisce la versione nel formato seguente:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando un dispositivo ha una versione precedente rispetto alla versione del sistema operativo immessa, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo. Dopo l'aggiornamento, potrà accedere alle risorse aziendali.

- **Versione massima del sistema operativo**: immettere la versione massima consentita nel formato **numerico major.minor.build.revision**. Per ottenere il valore corretto, aprire un prompt dei comandi e digitare `ver`. Il comando `ver` restituisce la versione nel formato seguente:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente finale viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché la regola non viene modificata in modo da consentire la versione del sistema operativo.

- **Versione minima richiesta del sistema operativo per i dispositivi mobili**: immettere la versione minima consentita, usando il formato numerico major.minor.build.

  Quando un dispositivo ha una versione precedente rispetto alla versione del sistema operativo immessa, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo. Dopo l'aggiornamento, potrà accedere alle risorse aziendali.

- **Versione massima richiesta del sistema operativo per i dispositivi mobili**: immettere la versione massima consentita, usando il formato numerico major.minor.build.

  Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente finale viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché la regola non viene modificata in modo da consentire la versione del sistema operativo.

- **Build valide dei sistemi operativi**: immettere un intervallo per le versioni dei sistemi operativi accettabili, incluse la versione minima e quella massima. È anche possibile **esportare** un elenco di file con valori delimitati da virgole (CSV) dei numeri di build del sistema operativo consentiti.

## <a name="configuration-manager-compliance"></a>Conformità di Configuration Manager

Si applica solo ai dispositivi con co-gestione che eseguono Windows 10 e versioni successive. I dispositivi solo Intune restituiscono uno stato non disponibile.

- **Richiedi la conformità del dispositivo da System Center Configuration Manager**: scegliere **Richiedi** per forzare la conformità di tutte le impostazioni (elementi di configurazione) in System Center Configuration Manager. 

  È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo non è conforme in Intune.
  
  Con lo stato **Non configurato**, Intune non verifica la conformità delle impostazioni di Configuration Manager.

## <a name="system-security"></a>Protezione del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo. Quando **non è configurato**, Intune non valuta la conformità del dispositivo per le impostazioni della password.
- **Password semplici**: impostare questa opzione su **Blocca** per impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**. Impostare l'opzione su **Non configurata** per consentire agli utenti di creare password come **1234** o **1111**.
- **Tipo di password**: scegliere il tipo di password o il PIN necessario. Le opzioni disponibili sono:

  - **Impostazione predefinita del dispositivo**: Richiedi una password, un PIN numerico o un PIN alfanumerico
  - **Numeric**: richiedere una password o un PIN numerico
  - **Alfanumerico**: richiedere una password o un PIN alfanumerico. Scegliere anche la **complessità della password**: 
    
    - **Richiedi cifre e lettere minuscole**
    - **Richiedi cifre, lettere minuscole e lettere maiuscole**
    - **Richiedi cifre, lettere minuscole, lettere maiuscole e caratteri speciali**

    > [!TIP]
    > I criteri alfanumerici per le password possono essere complessi. Invitiamo gli amministratori a leggere i CSP per ulteriori informazioni:
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters consente CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password.
- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)** : immettere il numero di giorni prima della scadenza della password (da 1 a 730). Alla scadenza, sarà necessario crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non è possibile usare.
- **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività (Mobile e Holographic)** : imporre agli utenti di immettere la password ogni volta che il dispositivo torna attivo dopo uno stato di inattività.

  > [!IMPORTANT]
  > La modifica dei requisiti per la password in un desktop di Windows interessa gli utenti al successivo accesso, ossia quando il dispositivo passa dallo stato inattivo allo stato attivo. Agli utenti con password che soddisfano i requisiti viene comunque chiesto di cambiare la password.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**: scegliere **Rendi obbligatorio** per crittografare l'archivio dati nei dispositivi.

  > [!NOTE]
  > L'impostazione **Encryption of data storage on a device** (Crittografia dell'archivio dati in un dispositivo) verifica in modo generico la presenza di crittografia nel dispositivo. Per impostare la crittografia in modo più affidabile, è consigliabile usare **Richiedi BitLocker**, che sfrutta Attestazione dell'integrità del dispositivo di Windows per convalidare lo stato di Bitlocker a livello di TPM.

### <a name="device-security"></a>Sicurezza del dispositivo

- **Firewall**: impostare su **Richiedi** per attivare Microsoft Defender Firewall e impedire agli utenti di disattivarla. **Non configurato** (impostazione predefinita) non controlla Microsoft Defender Firewall né modifica le impostazioni esistenti.

  [CSP firewall](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

- **Trusted Platform Module (TPM)** : se impostato su **Richiedi**, Intune verifica la conformità della versione. Il dispositivo è conforme se la versione del chip TPM è maggiore di 0 (zero). Il dispositivo non è conforme se non è presente una versione del TPM nel dispositivo. Quando **non è configurato**, Intune non controlla la versione del chip TPM nel dispositivo.

  [DeviceStatus CSP-nodo DeviceStatus/TPM/SpecificationVersion](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivirus**: se impostata come **obbligatoria**, è possibile verificare la conformità usando le soluzioni antivirus registrate nel [Centro sicurezza PC Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), ad esempio Symantec e Microsoft Defender. Se **non configurata**, Intune non verifica la presenza di soluzioni antivirus installate nel dispositivo.
- **Antispyware**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando le soluzioni antispyware registrate nel [Centro sicurezza PC Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), ad esempio Symantec e Microsoft Defender. Se **non configurata**, Intune non verifica la presenza di soluzioni antispyware installate nel dispositivo.

### <a name="defender"></a>Defender

- **Microsoft Defender antimalware**: impostare su **Richiedi** per attivare il servizio anti-malware di Microsoft Defender e impedire agli utenti di disattivarlo. **Non configurato** (impostazione predefinita) non controlla il servizio né modifica le impostazioni esistenti.
- **Versione minima di Microsoft Defender antimalware**: immettere la versione minima consentita del servizio Microsoft Defender anti-malware. Immettere ad esempio `4.11.0.0`. Quando viene lasciato vuoto, è possibile usare qualsiasi versione di Microsoft Defender anti-malware Service.
- **Microsoft Defender antimalware Security Intelligence**-aggiornato: controlla gli aggiornamenti della protezione da virus e minacce per la protezione di Windows nei dispositivi. **Richiedi** impone a Microsoft Defender Security Intelligence di essere aggiornato. **Non configurato** (impostazione predefinita) non impone alcun requisito.

  [Gli aggiornamenti di intelligence per la sicurezza per Microsoft Defender Antivirus e altri antimalware Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates) hanno maggiori informazioni sulle funzionalità di intelligence per la sicurezza.

- **Protezione in tempo reale**: la **richiesta** attiva la protezione in tempo reale, che esegue l'analisi di malware, spyware e altro software indesiderato. **Non configurato** (impostazione predefinita) non controlla questa funzionalità né modifica le impostazioni esistenti.

  [CSP Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

- **Richiedi che il dispositivo si trovi al massimo al punteggio di rischio del computer**: usare questa impostazione per considerare la valutazione del rischio dei servizi Threat Defense come condizione di conformità. Scegliere il livello di minaccia massimo consentito:

  - **Cancella**: questa opzione è la più sicura, perché il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.
  - **Media**: il dispositivo viene valutato come conforme se le minacce esistenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato non conforme.
  - **Alta**: questa opzione è la meno sicura e consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.
  
  Per configurare Microsoft Defender ATP (Advanced Threat Protection) come servizio di difesa dalle minacce, vedere [Abilitare Microsoft Defender ATP con l'accesso condizionale](advanced-threat-protection.md).

Selezionare **OK** > **Crea** per salvare le modifiche.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business usa la piattaforma **Windows 10 e versioni successive**. Windows Holographic for Business supporta l' impostazione seguente:

- **Sicurezza del sistema** > **Crittografia** > **Crittografia dell'archivio dati nel dispositivo**.

Per verificare la crittografia del dispositivo in Microsoft HoloLens, vedere [Verificare la crittografia dispositivo](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub usa la piattaforma **Windows 10 e versioni successive**. I dispositivi Surface Hub sono supportati sia per la conformità sia per l'accesso condizionale. Per abilitare queste funzionalità in Surface Hub, è consigliabile [abilitare la registrazione automatica di Windows 10](windows-enroll.md) in Intune (richiede Azure Active Directory (Azure AD)) e impostare i dispositivi Surface Hub come gruppi di dispositivi. Per la conformità e per il funzionamento dell'accesso condizionale, i dispositivi Surface Hub devono essere aggiunti ad Azure AD.

Per informazioni, vedere [Configurare la registrazione dei dispositivi Windows](windows-enroll.md).

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi Windows 8.1](compliance-policy-create-windows-8-1.md).
