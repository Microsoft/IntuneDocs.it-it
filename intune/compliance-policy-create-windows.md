---
title: Creare criteri di conformità per i dispositivi Windows in Microsoft Intune- Azure | Microsoft Docs
description: Creare o configurare i criteri di conformità dei dispositivi di Microsoft Intune per dispositivi Windows Phone 8.1, Windows 8.1 e versioni successive e Windows 10 e versioni successive. Verificare la conformità del sistema operativo minimo e massimo, impostare le restrizioni e la lunghezza per la password, richiedere BitLocker, impostare il livello di minaccia accettabile e abilitare la crittografia per l'archiviazione dati, inclusi Surface Hub e Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bb79a6c18ff8b6eec20f4ce8813d8dea188215e7
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Aggiungere i criteri di conformità per i dispositivi Windows in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I criteri di conformità di un dispositivo Windows in Intune specificano le regole e le impostazioni che i dispositivi Windows devono soddisfare per essere considerati conformi. Questi criteri con accesso condizionale possono essere usati per consentire o bloccare l'accesso alle risorse aziendali. È anche possibile ottenere i report di dispositivo e intraprendere azioni per la mancata conformità. I criteri di conformità dei dispositivi vengono creati per ogni piattaforma nel portale di Intune in Azure. Per altre informazioni sui criteri di conformità e sui requisiti, vedere [Introduzione alla conformità dei dispositivi](device-compliance-get-started.md).

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

---------------------------

| **Impostazione di criteri** | **Windows 8.1 e versioni successive** | **Windows Phone 8.1 e versioni successive** |
|----| ----| --- |
| **Configurazione di PIN o password** | Corretto | Corretto |   
| **Crittografia dispositivo** | Non applicabile | Corretto |   
| **Dispositivo jailbroken o rooted** | Non applicabile | Non applicabile |  
| **Profilo di posta elettronica** | Non applicabile | Non applicabile |   
| **Versione minima del sistema operativo** | In quarantena | In quarantena |   
| **Versione massima del sistema operativo** | In quarantena | In quarantena |   
| **Attestazione dell'integrità di Windows** | In quarantena: Windows 10 e Windows 10 Mobile|Non applicabile: Windows 8.1 |

-------------------------------

**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Per **Piattaforma** selezionare **Windows Phone 8.1**, **Windows 8.1 e versioni successive** o **Windows 10 e versioni successive**.
6. Scegliere **Configura impostazioni** e immettere le impostazioni **Integrità del dispositivo**, **Proprietà del dispositivo** e **Sicurezza del sistema**. Al termine, fare clic su **OK** e su **Crea**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Impostazioni dei criteri per i dispositivi Windows 8.1

Queste impostazioni dei criteri si applicano ai dispositivi che eseguono le piattaforme seguenti:

- Windows Phone 8.1
- Windows 8.1 e versioni successive

### <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e quindi ottenere l'accesso alle risorse aziendali.
- **Versione massima consentita del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali viene bloccato. All'utente viene richiesto di contattare l'amministratore IT. Finché la regola non viene modificata per poter consentire la versione del sistema operativo usata dal dispositivo, quest'ultimo non può accedere alle risorse aziendali.

I PC Windows 8.1 restituiscono la versione **3**. Se la regola della versione del sistema operativo è impostata su Windows 8.1 per Windows, il dispositivo risulta non conforme anche se il sistema operativo installato è Windows 8.1.

### <a name="system-security"></a>Protezione del sistema

#### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo.
- **Password semplici**: impostare questa opzione su **Blocca** per impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**. Impostare l'opzione su **Non configurata** per consentire agli utenti di creare password come **1234** o **1111**.
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password.

  Per i dispositivi che eseguono Windows e prevedono l'accesso con un account Microsoft, i criteri di conformità non eseguono correttamente la convalida:
  - Se la lunghezza minima della password è maggiore di otto caratteri
  - Oppure, se il numero minimo di set di caratteri è maggiore di due

- **Tipo di password**: scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).
  
  - **Numero di caratteri non alfanumerici nella password:** se **Tipo di password richiesto** è impostato su **Alfanumerico**, questa impostazione specifica il numero minimo di set di caratteri che la password deve contenere. I quattro set di caratteri sono:
    - Lettere minuscole
    - Lettere maiuscole
    - Simboli
    - Numeri

    Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa. Per i dispositivi che eseguono Windows e prevedono l'accesso con un account Microsoft, i criteri di conformità non eseguono correttamente la convalida se la lunghezza minima della password è maggiore di otto caratteri e il numero minimo di set di caratteri è maggiore di due.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non è possibile usare.

#### <a name="encryption"></a>Crittografia

- **Richiedi crittografia sui dispositivi mobili**: **richiedere** la crittografia del dispositivo per la connessione alle risorse di archiviazione dati.

## <a name="windows-10-and-later-policy-settings"></a>Impostazioni dei criteri per Windows 10 e versioni successive

### <a name="device-health"></a>Device health

- **Richiedi BitLocker**: quando Bitlocker è abilitato, il dispositivo può proteggere dall'accesso non autorizzato i dati archiviati nell'unità, quando il sistema viene spento o passa alla modalità di ibernazione. Crittografia unità BitLocker di Windows crittografa tutti i dati archiviati nel volume del sistema operativo Windows. BitLocker usa il TPM per proteggere il sistema operativo Windows e i dati utente Consente inoltre di garantire che un computer non venga manomesso, anche se viene perso, rubato o lasciato incustodito. Se il computer è dotato di un TPM compatibile, BitLocker usa il TPM per bloccare le chiavi di crittografia che proteggono i dati. Di conseguenza, non è possibile accedere alle chiavi finché il TPM non ha verificato lo stato del computer.
- **Richiedi l'abilitazione dell'avvio sicuro nel dispositivo**: quando è abilitato l'avvio protetto, il sistema viene forzato a eseguire l'avvio in uno stato attendibile predefinito. Inoltre, quando è abilitato l'avvio protetto, i componenti di base usati per avviare il computer devono avere le firme di crittografia corrette considerate attendibili dall'organizzazione che ha prodotto il dispositivo. Il firmware UEFI verifica la firma prima di consentire l'avvio del computer. Se un file è stato manomesso modificandone la firma, il sistema non verrà avviato.
- **Richiedi l'integrità del codice**: l'integrità del codice è una funzionalità che verifica l'integrità di un driver o di un file di sistema ogni volta che viene caricato in memoria. L'integrità del codice rileva se un driver o un file di sistema non firmato viene caricato nel kernel o se un file di sistema è stato modificato da software dannoso eseguito da un account utente con privilegi di amministratore.
- **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo**: usare questa impostazione per considerare la valutazione del rischio dei servizi Threat Defense come condizione di conformità. Scegliere il livello di minaccia massimo consentito:
  - **Protetto**: questa opzione è la più sicura, perché il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello, il dispositivo viene considerato non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Media**: il dispositivo viene valutato come conforme se le minacce esistenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questa opzione è la meno sicura e consente tutti i livelli di minaccia. Potrebbe essere utile usare questa soluzione solo per la creazione di report.

Per informazioni su come funziona il servizio di attestazione dell'integrità, vedere l'articolo relativo al [CSP per l'attestazione dell'integrità](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).

### <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima richiesta del sistema operativo**: immettere il numero major.minor.build.CU. Il numero di build.CU deve corrispondere alla versione restituita dal comando `ver` o `winver`.

  Quando un dispositivo ha una versione precedente rispetto alla versione del sistema operativo specificata, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.

- **Versione massima consentita del sistema operativo**: immettere il numero major.minor.build.CU. Il numero di build.CU deve corrispondere alla versione restituita dal comando `ver` o `winver`.

  Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali risulterà bloccato e l'utente dovrà contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.

- **Versione minima richiesta del sistema operativo per i dispositivi mobili**: immettere il numero major.minor.build.

  Quando un dispositivo ha una versione precedente rispetto alla versione del sistema operativo specificata, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.

- **Versione massima richiesta del sistema operativo per i dispositivi mobili**: immettere il numero major.minor.build.

  Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali risulterà bloccato e l'utente dovrà contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.

- **Build valide dei sistemi operativi**: immettere un intervallo per le versioni dei sistemi operativi accettabili, incluse la versione minima e quella massima.

### <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

#### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo.
- **Password semplici**: impostare questa opzione su **Blocca** per impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**. Impostare l'opzione su **Non configurata** per consentire agli utenti di creare password come **1234** o **1111**.
- **Tipo di password**: scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).

  - **Numero di caratteri non alfanumerici nella password:** se **Tipo di password richiesto** è impostato su **Alfanumerico**, questa impostazione specifica il numero minimo di set di caratteri che la password deve contenere. I quattro set di caratteri sono:
    - Lettere minuscole
    - Lettere maiuscole
    - Simboli
    - Numeri

    Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password.
- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non è possibile usare.
- **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività (Mobile e Holographic)**: imporre agli utenti di immettere la password ogni volta che il dispositivo torna attivo dopo uno stato di inattività.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**: scegliere **Rendi obbligatorio** per crittografare l'archivio dati nei dispositivi.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business usa la piattaforma **Windows 10 e versioni successive**. Windows Holographic for Business supporta l' impostazione seguente:

- **Sicurezza del sistema** > **Crittografia** > **Crittografia dell'archivio dati nel dispositivo**.

Per verificare la crittografia del dispositivo in Microsoft HoloLens, vedere [Verificare la crittografia dispositivo](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub
Surface Hub usa la piattaforma **Windows 10 e versioni successive**. Surface Hub è supportato sia per la conformità che per l'accesso condizionale. Per abilitare queste funzionalità in Surface Hub, è consigliabile [abilitare la registrazione automatica di Windows 10](windows-enroll.md) in Intune (richiede anche Azure Active Directory) e impostare i dispositivi Surface Hub come gruppi di dispositivi. Per la conformità e l'accesso condizionale alla funzione, i dispositivi Surface Hub devono essere appartenenti ad Azure Active Directory.

Per informazioni, vedere [Configurare la registrazione dei dispositivi Windows](windows-enroll.md).

## <a name="assign-user-or-device-groups"></a>Assegnare gruppi di utenti o dispositivi

1. Scegliere un criterio configurato. I criteri esistenti sono in **Conformità del dispositivo** > **Criteri**.
2. Selezionare il criterio e scegliere **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure AD.
3. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi di utenti o dispositivi a cui si vuole applicare questo criterio e scegliere **Salva** per distribuire il criterio.

Il criterio è stato applicato. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

## <a name="next-steps"></a>Passaggi successivi
[Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md)  
[Monitorare i criteri di conformità dei dispositivi Intune](compliance-policy-monitor.md)
