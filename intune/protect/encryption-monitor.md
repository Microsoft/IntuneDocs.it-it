---
title: Report di crittografia per i dispositivi crittografati in Microsoft Intune
titleSuffix: Microsoft Intune
description: Visualizzare un report sullo stato della crittografia dei dispositivi iOS o Windows e accedere alle chiavi di ripristino di FileVault e BitLocker all'interno del portale di Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5d9508c5d69b0790efa37ee633f8216bfd2bb30c
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164670"
---
# <a name="monitor-device-encryption-with-intune"></a>Monitorare la crittografia dei dispositivi con Intune

Il report di crittografia di Microsoft Intune è una posizione centralizzata che consente di visualizzare i dettagli sullo stato di crittografia di un dispositivo e di trovare le opzioni per gestire le chiavi di ripristino del dispositivo. Le opzioni relative alle chiavi di ripristino disponibili dipendono dal tipo del dispositivo che si sta visualizzando.

Per trovare il report, accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Selezionare **Dispositivi** > **Monitoraggio** e quindi in *Configurazione* selezionare **Report sulla crittografia**.

## <a name="view-encryption-details"></a>Visualizzare i dettagli di crittografia

Il report di crittografia visualizza dettagli comuni a tutti i dispositivi supportati gestiti. Le sezioni seguenti offrono informazioni dettagliate sulle informazioni che Intune presenta nel report.

### <a name="prerequisites"></a>Prerequisiti

Il report di crittografia supporta la creazione di report per i dispositivi che eseguono le seguenti versioni di sistema operativo:

- macOS 10.13 o versioni successive
- Windows versione 1607 o successiva

### <a name="report-details"></a>Dettagli del report

Il riquadro Report sulla crittografia visualizza l'elenco dei dispositivi gestiti con dettagli di alto livello su tali dispositivi. È possibile selezionare un dispositivo nell'elenco per eseguire il drill-in e visualizzare altri dettagli nel riquadro [Stato della crittografia del dispositivo](#device-encryption-status) relativo al dispositivo selezionato.

- **Nome dispositivo**: nome del dispositivo.
- **Sistema operativo**: piattaforma del dispositivo, ad esempio Windows o macOS.
- **Versione del sistema operativo**: versione di Windows o di macOS del dispositivo.
- **Versione TPM**  *(solo per Windows 10)* : versione del chip TPM (Trusted Platform Module) nel dispositivo Windows 10.
- **Conformità con la crittografia**: valutazione della conformità dei dispositivi per il supporto di una tecnologia di crittografia applicabile, ad esempio BitLocker o FileVault. I dispositivi vengono identificati come:
  - **Pronto**: Il dispositivo può essere crittografato usando i criteri MDM, in base ai quali il dispositivo deve soddisfare i requisiti seguenti:

    **Per i dispositivi macOS**:
    - macOS versione 10.13 o successiva

    **Per i dispositivi Windows 10**:
    - versione 1703 o successiva dell'edizione *Business*, *Enterprise* o *Education* oppure versione 1809 o successiva dell'edizione *Pro*
    - Il dispositivo deve avere un chip TPM

    Per altre informazioni, vedere [BitLocker configuration service provider](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (Provider di servizi di configurazione BitLocker) nella documentazione di Windows.

  - **Non pronto**: il dispositivo non ha funzionalità di crittografia complete, ma supporta comunque la crittografia. Un dispositivo Windows, ad esempio, può essere crittografato manualmente da un utente oppure tramite Criteri di gruppo, che è possibile impostare per consentire la crittografia senza un chip TPM.
  - **Non applicabile**: non sono disponibili informazioni sufficienti per classificare il dispositivo.

- **Stato crittografia**: indica se l'unità del sistema operativo è crittografata.

- **Nome entità utente**: utente primario del dispositivo.

### <a name="device-encryption-status"></a>Stato della crittografia del dispositivo

Quando si seleziona un dispositivo dal report di crittografia, Intune visualizza il riquadro **Stato della crittografia del dispositivo**. Questo riquadro fornisce le informazioni seguenti:

- **Nome dispositivo**: nome del dispositivo visualizzato.

- **Conformità con la crittografia**: valutazione della conformità dei dispositivi per il supporto della crittografia tramite i criteri MDM.

  Ad esempio: anche se un dispositivo Windows 10 presenta una conformità corrispondente a *Non pronto*, è comunque possibile che supporti la crittografia. Per essere designato come *Pronto*, il dispositivo Windows 10 deve avere un chip TPM. I chip TPM non sono obbligatori per il supporto della crittografia. Per altre informazioni, vedere *Conformità con la crittografia* nella sezione precedente.

- **Stato crittografia**: indica se l'unità del sistema operativo è crittografata. Possono trascorrere fino a 24 ore prima che Intune segnali lo stato di crittografia di un dispositivo o una modifica di tale stato. Questo tempo include quello richiesto per la crittografia del sistema operativo, oltre al tempo richiesto al dispositivo per la segnalazione a Intune.

  Per velocizzare la creazione di report sullo stato di crittografia di FileVault prima della normale archiviazione del dispositivo, chiedere agli utenti di sincronizzare i dispositivi al termine della crittografia.

- **Profili**: elenco dei profili di *Configurazione dispositivo* validi per il dispositivo e configurati con i valori seguenti:

  - macOS:
    - Tipo di profilo = *Endpoint Protection*
    - Impostazioni > FileVault > FileVault = *Abilita*

  - Windows 10:
    - Tipo di profilo = *Endpoint Protection*
    - Impostazioni > Crittografia di Windows > Crittografa i dispositivi = *Richiedi*

  È possibile usare l'elenco dei profili per individuare singoli criteri da esaminare nel caso in cui *Riepilogo dello stato del profilo* dovesse segnalare problemi.

- **Riepilogo dello stato del profilo**: riepilogo dei profili che si applicano al dispositivo. Il riepilogo rappresenta la condizione meno favorevole tra i profili applicabili. Se, ad esempio, solo uno di diversi profili determina un errore, *Riepilogo dello stato del profilo* visualizza *Errore*.

  Per visualizzare altri dettagli di uno stato, passare a **Intune** > **Configurazione del dispositivo** > **Profili** e selezionare il profilo. Facoltativamente, selezionare **Stato del dispositivo** e quindi un dispositivo.

- **Dettagli stato**: dettagli avanzati sullo stato di crittografia del dispositivo.

  > [!IMPORTANT]
  > Per i dispositivi Windows 10, Intune visualizza le informazioni *Dettagli stato* solo per i dispositivi che eseguono l'*aggiornamento di Windows 10 di aprile 2019* o un aggiornamento successivo.

  Questo campo visualizza le informazioni per ogni errore applicabile che è possibile rilevare. È possibile usare queste informazioni per comprendere il motivo per cui un dispositivo potrebbe non essere pronto per la crittografia.

  Di seguito sono riportati alcuni esempi dei dettagli dello stato che Intune può segnalare:

  **macOS**:
  - la chiave di ripristino non è ancora stata recuperata e archiviata. È probabile che il dispositivo non sia stato sbloccato o che non sia stato archiviato.

    *Tenere in considerazione: questo risultato non rappresenta necessariamente una condizione di errore, ma uno stato temporaneo che può essere dovuto a un intervallo nel dispositivo in cui è necessario configurare il deposito delle chiavi di ripristino prima che la richiesta di crittografia venga inviata al dispositivo stesso. Questo stato potrebbe anche indicare che il dispositivo rimane bloccato o non è stato recentemente sincronizzato con Intune. Infine, poiché la crittografia FileVault viene avviata solo quando un dispositivo viene collegato per la ricarica, è possibile che un utente riceva una chiave di ripristino per un dispositivo non ancora crittografato*.

  - L'utente sta posticipando la crittografia o sta attualmente eseguendo la crittografia.

    *Tenere in considerazione: l'utente non si è ancora disconnesso dopo aver ricevuto la richiesta di crittografia (operazione necessaria perché FileVault possa crittografare il dispositivo) oppure l'utente ha decrittografato manualmente il dispositivo. Intune non può impedire a un utente di decrittografare il dispositivo.*

  - Il dispositivo è già crittografato. Per continuare, l'utente del dispositivo deve decrittografare il dispositivo.

    *Tenere in considerazione: Intune non è in grado di configurare FileVault in un dispositivo già crittografato. L'utente deve invece decrittografare manualmente il dispositivo prima di poterlo gestire con criteri di configurazione del dispositivo e Intune*.

  - In macOS Catalina e versioni successive, FileVault richiede che l'utente approvi il profilo di gestione.

    *Tenere in considerazione: A partire da macOS versione 10.15 (Catalina), le impostazioni di registrazione approvate dall'utente possono comportare il requisito dell'approvazione manuale della crittografia FileVault da parte dell'utente. Per altre informazioni, vedere [Registrazione approvata dall'utente](../enrollment/macos-enroll.md)* nella documentazione di Intune.

  - Sconosciuto.

    *Tenere in considerazione: Una delle possibili cause di uno stato sconosciuto è che il dispositivo è bloccato e Intune non può avviare il processo di deposito o di crittografia. Dopo che il dispositivo sarà stato sbloccato, il processo potrà continuare*.

  **Windows 10**:
  - I criteri di BitLocker richiedono il consenso utente per l'avvio della Crittografia guidata unità BitLocker per iniziare la crittografia del volume del sistema operativo, ma l'utente non ha fornito il consenso.

  - Il metodo di crittografia del volume del sistema operativo non corrisponde ai criteri di BitLocker.

  - I criteri di BitLocker richiedono una protezione tramite TPM per proteggere il volume del sistema operativo ma la protezione tramite TPM non viene usata.

  - I criteri di BitLocker richiedono una protezione tramite solo TPM per il volume del sistema operativo ma la protezione tramite TPM non viene usata.

  - I criteri di BitLocker richiedono una protezione tramite TPM e PIN per il volume del sistema operativo ma la protezione tramite TPM e PIN non viene usata.

  - I criteri di BitLocker richiedono una protezione tramite TPM e chiave di avvio per il volume del sistema operativo ma la protezione tramite TPM e chiave di avvio non viene usata.

  - I criteri di BitLocker richiedono una protezione tramite TPM, PIN e chiave di avvio per il volume del sistema operativo ma la protezione tramite TPM, PIN e chiave di avvio non viene usata.

  - Il volume del sistema operativo non è protetto.

  - Non è stato possibile eseguire il backup della chiave di ripristino.

  - Un'unità fissa non è protetta.

  - Il metodo di crittografia dell'unità fissa non corrisponde ai criteri di BitLocker.

  - Per crittografare le unità, i criteri di BitLocker richiedono che l'utente acceda come amministratore oppure, se il dispositivo è aggiunto ad Azure AD, che il criterio AllowStandardUserEncryption sia impostato su 1.

  - L'Ambiente ripristino Windows non è configurato.

  - TPM non è disponibile per BitLocker perché non è presente, non è più disponibile nel Registro di sistema o il sistema operativo si trova in un'unità rimovibile.

  - TPM non è pronto per BitLocker.

  - La rete non è disponibile ma è necessaria per il backup della chiave di ripristino.

## <a name="export-report-details"></a>Esportare i dettagli del report

Durante la visualizzazione del riquadro Report sulla crittografia è possibile selezionare **Esporta** per creare il download di un *file con estensione csv* dei dettagli del report. Questo report include i dettagli di alto livello del riquadro *Report sulla crittografia* e i dettagli di *Stato della crittografia del dispositivo* per ogni dispositivo gestito.

![Esportare i dettagli](./media/encryption-monitor/export.png)

Questo report può essere utile per identificare i problemi di gruppi di dispositivi. È ad esempio possibile usare il report per identificare un elenco di dispositivi macOS che segnalano *FileVault is already enabled by the user* (FileVault già abilitato dall'utente). Questo messaggio identifica i dispositivi che devono essere decrittografati manualmente perché Intune possa gestirne le impostazioni di FileVault.

## <a name="filevault-recovery-keys"></a>Chiavi di ripristino di FileVault

Quando Intune esegue per la prima volta la crittografia di un dispositivo macOS con FileVault, viene creata una chiave di ripristino personale. Al momento della crittografia, il dispositivo visualizza la chiave personale una sola volta per l'utente finale.

Per i dispositivi gestiti, Intune può depositare una copia della chiave di ripristino personale. Il deposito delle chiavi consente agli amministratori di Intune di ruotare le chiavi per favorire la protezione dei dispositivi e agli utenti di recuperare una chiave di ripristino personale smarrita o ruotata.

Intune supporta più opzioni per la rotazione e il ripristino delle chiavi di ripristino personali. È opportuno eseguire la rotazione delle chiavi se la chiave personale corrente viene smarrita o si ritiene che sia a rischio.

> [!IMPORTANT]
> I dispositivi crittografati dagli utenti e non da Intune non possono essere gestiti da Intune. Questo significa che Intune non può depositare la chiave di ripristino personale di questi dispositivi, né gestire la rotazione delle chiavi di ripristino. Perché Intune possa gestire FileVault e le chiavi di ripristino dei dispositivi, gli utenti devono decrittografare i dispositivi e quindi consentire a Intune di crittografarli.

### <a name="rotate-recovery-keys"></a>Ruotare le chiavi di ripristino

- **Rotazione automatica**: un amministratore può configurare l'impostazione di FileVault Rotazione della chiave di ripristino personale in modo da generare periodicamente nuove chiavi di ripristino in modo automatico. Quando viene generata una nuova chiave per un dispositivo, la chiave non viene visualizzata per l'utente. L'utente deve invece ottenere la chiave da un amministratore o tramite l'app Portale aziendale.

- **Rotazione manuale**: un amministratore può visualizzare le informazioni relative ai dispositivi gestiti con Intune e crittografati con FileVault. Può quindi scegliere di ruotare manualmente le chiavi di ripristino per i dispositivi aziendali. Non è possibile ruotare le chiavi di ripristino per i dispositivi personali.

  Per ruotare una chiave di ripristino:

  1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
  
  2. Selezionare **Dispositivi** > **Tutti i dispositivi**.
  
  3. Dall'elenco dei dispositivi selezionare il dispositivo crittografato di cui si vuole ruotare la chiave, quindi in Monitoraggio selezionare **Chiavi di ripristino**.
  
  4. Nel riquadro Chiavi di ripristino selezionare **Ruota la chiave di ripristino di FileVault**.

     Alla successiva sincronizzazione del dispositivo con Intune la chiave personale verrà ruotata. Quando necessario, l'utente finale può ottenere la nuova chiave tramite il portale aziendale.

### <a name="recover-recovery-keys"></a>Ripristinare chiavi di ripristino

- **Amministratore**: gli amministratori non possono visualizzare le chiavi di ripristino personali per i dispositivi crittografati con FileVault.

- **Utente finale**: gli utenti finali possono usare il sito Web Portale aziendale da qualsiasi dispositivo per visualizzare la chiave di ripristino personale corrente per tutti i propri dispositivi gestiti. Non è possibile visualizzare le chiavi di ripristino dall'app Portale aziendale.

  Per visualizzare una chiave di ripristino:
  
  1. Da un qualsiasi dispositivo accedere al *Portale aziendale Intune*.

  2. Nel portale passare a **Dispositivi** e selezionare il dispositivo macOS crittografato con FileVault.

  3. Selezionare **Ottieni la chiave di ripristino**. Verrà visualizzata la chiave di ripristino corrente.

## <a name="bitlocker-recovery-keys"></a>Chiavi di ripristino di BitLocker

Intune offre l'accesso al pannello di Azure AD per BitLocker, per consentire di visualizzare gli ID delle chiavi di BitLocker e le chiavi di ripristino per i dispositivi Windows 10 dal portale di Intune. Per essere accessibile, il dispositivo deve avere le chiavi depositate in Azure AD.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Tutti i dispositivi**.

3. Selezionare un dispositivo nell'elenco e in *Monitoraggio* selezionare **Chiavi di ripristino**.
  
   Quando le chiavi sono presenti in Azure AD, sono disponibili le informazioni seguenti:
   - ID chiave BitLocker
   - Chiave di ripristino di BitLocker
   - Tipo unità

   Quando le chiavi non sono presenti in Azure AD, Intune visualizzerà il messaggio *Non sono state trovate chiavi BitLocker per questo dispositivo*.

Le informazioni per BitLocker vengono ottenute tramite il [provider di servizi di configurazione BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp). Il provider di servizi di configurazione (CSP) BitLocker è supportato in Windows 10 versione 1703 e successive e in Windows 10 Pro versione 1809 e successive.

## <a name="next-steps"></a>Passaggi successivi

Creare criteri di [conformità dei dispositivi](compliance-policy-create-windows.md).
