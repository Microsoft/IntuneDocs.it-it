---
title: Report di crittografia e chiavi di BitLocker in Microsoft Intune
titleSuffix: Microsoft Intune
description: Visualizzare un report sullo stato della crittografia dei dispositivi e accedere alle chiavi di ripristino di BitLocker all'interno del portale di Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bccfc952202ed9db5bdc5f68bbbba57c61b37b13
ms.sourcegitcommit: b3a1c5b0b24f0e52cf318defe10f3d27a2770009
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2019
ms.locfileid: "67316940"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>Monitorare BitLocker e la crittografia dei dispositivi  
Intune offre una posizione centralizzata per identificare lo stato della crittografia dei dispositivi Windows 10 e consente di accedere a informazioni importanti per BitLocker dai dispositivi, come disponibili in Azure Active Directory (Azure AD).  

- Il [report di crittografia](#encryption-report) fornisce informazioni dettagliate sulla conformità e sullo stato della crittografia di un dispositivo. I dettagli del report possono aiutare a identificare i problemi che impediscono la corretta crittografia dei dispositivi che si vuole proteggere.  
- La [visualizzazione dei dettagli di BitLocker](#bitlocker-recovery-keys) consente di visualizzare informazioni come l'ID chiave e le chiavi di ripristino per i dispositivi dal portale di Intune.  

## <a name="encryption-report"></a>Report di crittografia
È possibile usare il report di crittografia per visualizzare informazioni dettagliate sullo stato della crittografia dei dispositivi Windows 10.  

Per trovare il report, accedere a [Intune](https://aka.ms/intuneportal) e passare a **Configurazione del dispositivo**, quindi in *Monitoraggio*, selezionare **Report di crittografia**.  

### <a name="prerequisites"></a>Prerequisiti:
Per essere visualizzato nel report di crittografia, un dispositivo deve eseguire Windows versione 1607 o successiva.  

### <a name="report-details"></a>Dettagli del report
Il report visualizza il valore di **Nome dispositivo** per i dispositivi Windows 10 e informazioni generali per ogni dispositivo, tra cui:  
- **Versione sistema operativo**: versione di Windows.  
- **Versione TPM**: versione del chip TPM (Trusted Platform Module) nel dispositivo.  
- **Conformità con la crittografia**: valutazione della conformità dei dispositivi per il supporto della crittografia BitLocker. I dispositivi possono essere identificati come:
  - **Pronto**: il dispositivo può essere crittografato usando criteri MDM, che richiedono che il dispositivo abbia un chip TPM e soddisfi i requisiti di SKU e versione di Windows 10 seguenti:
    - Versione 1703 o successiva dell'edizione Business, Enterprise, Education
    - Versione 1809 o successiva dell'edizione Pro  
  
    Per altre informazioni, vedere [BitLocker configuration service provider](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (Provider di servizi di configurazione BitLocker) nella documentazione di Windows.  

  - **Non pronto**: il dispositivo non ha funzionalità di crittografia complete, ma supporta comunque la crittografia. Ad esempio, il dispositivo potrebbe essere crittografato manualmente da un utente oppure tramite Criteri di gruppo, che è possibile impostare per consentire la crittografia senza un chip TPM.
  - **Non applicabile**: non sono disponibili informazioni sufficienti per classificare il dispositivo.  

- **Stato crittografia**: indica se l'unità del sistema operativo è crittografata. 


### <a name="device-encryption-status"></a>Stato della crittografia del dispositivo
Quando si seleziona un dispositivo, Intune visualizza il riquadro **Stato della crittografia del dispositivo**.

Questo riquadro fornisce le informazioni seguenti:  
- **Nome dispositivo**: nome del dispositivo visualizzato.  
- **Conformità con la crittografia**: valutazione della conformità dei dispositivi per il supporto della crittografia BitLocker. Un dispositivo può avere un stato della crittografia *Crittografato* anche se l'impostazione di Conformità con la crittografia è *Non pronto*, a causa dell'assenza di un chip TPM. Vedere la sezione precedente relativa alla conformità con la crittografia per maggiori informazioni.
- **Stato crittografia**: indica se l'unità del sistema operativo è crittografata. Possono trascorrere fino a 24 ore prima che Intune inizi a segnalare lo stato di crittografia di un dispositivo o una modifica di tale stato.  
- **Profili**: elenco dei profili di *Configurazione dispositivo* che si applicano al dispositivo e che includono le impostazioni e il tipo di profilo seguenti:  
  - Tipo di profilo = *Endpoint Protection*  
  - Impostazioni > Crittografia di Windows > Crittografa i dispositivi = *Richiesto*  

  Questo elenco può essere utile nell'individuazione di singoli criteri da esaminare nel caso in cui il riepilogo dello stato del profilo dovesse segnalare problemi.  

- **Riepilogo dello stato del profilo**: riepilogo dei profili che si applicano al dispositivo. Il riepilogo rappresenta la condizione meno favorevole tra tutti i profili applicabili. Se, ad esempio, un profilo determina un errore, per il riepilogo dello stato del profilo verrà visualizzato *Errore*.  
- **Dettagli stato**: dettagli avanzati sullo stato di crittografia del dispositivo. 
  > [!NOTE]  
  > Intune mostra le informazioni di *Dettagli stato* solo per i dispositivi che eseguono l'*aggiornamento di Windows 10 di aprile 2019* o una versione successiva.
  
  Questo campo visualizza le informazioni per ogni errore applicabile che è possibile rilevare. È possibile usare queste informazioni per comprendere il motivo per cui un dispositivo potrebbe non essere pronto per la crittografia.  

  Di seguito sono riportati alcuni esempi dei dettagli dello stato che Intune può segnalare:  

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
   - TPM non è disponibile per BitLocker perché non è presente, non è più disponibile nel Registro di sistema o il sistema operativo si trova su un'unità rimovibile.  
   - TPM non è pronto per BitLocker.  
   - La rete non è disponibile ma è necessaria per il backup della chiave di ripristino.  

## <a name="bitlocker-recovery-keys"></a>Chiavi di ripristino di BitLocker
Intune offre l'accesso al pannello di Azure AD per BitLocker, per consentire di visualizzare gli ID delle chiavi di BitLocker e le chiavi di ripristino per i dispositivi Windows 10 dal portale di Intune.  Per essere accessibile, il dispositivo deve avere le chiavi depositate in Azure AD. 
1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), passare a **Dispositivi** e quindi in *Gestisci* selezionare **Tutti i dispositivi**.
2. Selezionare un dispositivo nell'elenco e in *Monitoraggio* selezionare **Chiavi di ripristino**.  
  
Quando le chiavi sono presenti in Azure AD, sono disponibili le informazioni seguenti:
- ID chiave BitLocker
- Chiave di ripristino di BitLocker
- Tipo unità  

Quando le chiavi non sono presenti in Azure AD, Intune visualizzerà il messaggio *Non sono state trovate chiavi BitLocker per questo dispositivo*.  

Le informazioni per BitLocker vengono ottenute tramite il [provider di servizi di configurazione BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp). Il provider di servizi di configurazione (CSP) BitLocker è supportato in Windows 10 versione 1703 e successive e in Windows 10 Pro versione 1809 e successive. 

## <a name="next-steps"></a>Passaggi successivi
Creare criteri di [conformità dei dispositivi](compliance-policy-create-windows.md) per i dispositivi Windows 10 per configurare BitLocker e la crittografia.
