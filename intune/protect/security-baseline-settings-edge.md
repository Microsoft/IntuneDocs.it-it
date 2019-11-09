---
title: Impostazioni di base per la sicurezza di Intune per Microsoft Edge
titleSuffix: Microsoft Intune
description: Impostazioni di base della sicurezza supportate da Intune per la gestione del browser Microsoft Edge
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c75029c60609b0383e2f647e5b94144d4186248c
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754871"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Impostazioni di base di Microsoft Edge per Intune

Visualizzare le impostazioni di base del Web browser Microsoft Edge supportate da Microsoft Intune. Le impostazioni predefinite di base Microsoft Edge rappresentano la configurazione consigliata per i browser Microsoft Edge e potrebbero non corrispondere alle impostazioni predefinite di base per altri tipi di base di sicurezza.

> [!NOTE]
> Microsoft Edge baseline è in anteprima pubblica. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **Impedisci l'esclusione dei prompt di Microsoft Defender SmartScreen per i siti**  
  **Impostazione predefinita**: Abilitato  
  CSP Microsoft Edge: [browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  Questa impostazione criterio consente di decidere se gli utenti possono ignorare gli avvisi di Microsoft Defender SmartScreen relativi a siti Web potenzialmente dannosi. 
  - Se si abilita questa impostazione, gli utenti non potranno ignorare gli avvisi di Microsoft Defender SmartScreen e non potranno continuare a eseguire il sito. 
  - Se si disattiva o non si configura questa impostazione, gli utenti possono ignorare gli avvisi di Microsoft Defender SmartScreen e continuare con il sito.

- **Versione minima di SSL abilitata**  
  **Impostazione predefinita**: Abilitato  

  Impostare una versione minima supportata di SSL. Se si imposta questo criterio su *non configurato*, Microsoft Edge usa una versione minima predefinita di *TLS 1,0*. Quando è impostato su *abilitato*, è possibile selezionare una versione minima tra i valori seguenti:

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **Versione minima di SSL abilitata**  
    **Impostazione predefinita**: TLS 1,2

- **Impedisci l'esclusione di avvisi di Microsoft Defender SmartScreen sui download**  
  **Impostazione predefinita**: Abilitato  
  CSP Microsoft Edge: [browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  Questo criterio consente di determinare se gli utenti possono eseguire l'override degli avvisi di Microsoft Defender SmartScreen sui download non verificati.
  - Se si Abilita questo criterio, gli utenti dell'organizzazione non possono ignorare gli avvisi di Microsoft Defender SmartScreen e non è possibile completare i download non verificati.
  - Se si disabilita o non si configura questo criterio, gli utenti possono ignorare gli avvisi di Microsoft Defender SmartScreen e completare i download non verificati.

- **Consenti agli utenti di procedere dalla pagina di avviso SSL**  
  **Impostazione predefinita**: Disabilitato  
  CSP Microsoft Edge: [browser/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  Microsoft Edge Visualizza una pagina di avviso quando gli utenti visitano siti che contengono errori SSL. Se si imposta questo criterio su *abilitato* o *non configurato*, gli utenti possono fare clic su queste pagine di avviso. Quando questo criterio è *disabilitato*, gli utenti non possono fare clic su una pagina di avviso. 

- **Impostazione predefinita di Adobe Flash**  
  **Impostazione predefinita**: Abilitato  
  CSP Microsoft Edge: [browser/AllowFlash](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflash)e [browser/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  Determina se i siti Web che non sono coperti da' PluginsAllowedForUrls ' o ' PluginsBlockedForUrls ' possono eseguire automaticamente il plug-in Adobe Flash. 

  - Selezionare "BlockPlugins" per bloccare Adobe Flash in tutti i siti
  - Selezionare "ClickToPlay" per consentire l'esecuzione di Adobe Flash, ma richiedere all'utente di fare clic sul segnaposto per avviarlo.
  
   In ogni caso, i criteri ' PluginsAllowedForUrls ' è PluginsBlockedForUrls ' hanno la precedenza su' DefaultPluginsSetting '. La riproduzione automatica è consentita solo per i domini elencati in modo esplicito nel criterio ' PluginsAllowedForUrls '. 
   Se si vuole abilitare la riproduzione automatica per tutti i siti, è consigliabile aggiungere http://* e https://* a questo elenco. 
   
   - Se si imposta questo criterio su *non configurato*, l'utente può modificare questa impostazione manualmente. * 2 = blocca il plug-in Adobe Flash * 3 = fare clic per riprodurre il primo set di opzioni ' 1' Consenti-tutti, ma questa funzionalità è ora gestita solo dal criterio ' PluginsAllowedForUrls '. I criteri esistenti che utilizzano ' 1' funzioneranno in modalità clic per la riproduzione.  
 
  - **Impostazione predefinita di Adobe Flash**  
    **Impostazione predefinita**: blocca il plug-in Adobe Flash

- **Abilita isolamento sito per ogni sito**  
  **Impostazione predefinita**: Abilitato  

  Il criterio ' SitePerProcess ' può essere usato per impedire agli utenti di rifiutare esplicitamente il comportamento predefinito dell'isolamento di tutti i siti. È anche possibile usare il criterio IsolateOrigins per isolare le origini aggiuntive con granularità fine.

  - Quando questo criterio è impostato su *abilitato*, gli utenti non possono rifiutare esplicitamente il comportamento predefinito in cui ogni sito viene eseguito in un proprio processo. 
  - Se si usa *disabilitato* o *non configurato*, un utente può rifiutare esplicitamente l'isolamento del sito. Ad esempio, usando la voce "Disabilita isolamento sito" in edge://flags. La disabilitazione del criterio o la mancata configurazione dei criteri non comporta la disattivazione dell'isolamento del sito.

- **Schemi di autenticazione supportati**  
  **Impostazione predefinita**: Abilitato  

  Specifica gli schemi di autenticazione HTTP supportati. È possibile configurare i criteri usando i valori seguenti:' Basic ',' digest ',' NTLM ' è Negotiate '. Separare più valori con virgole. Se non si configura questo criterio, vengono usati tutti e quattro gli schemi.
 
  - **Schemi di autenticazione supportati**  
    Selezionare una delle opzioni seguenti: 
    - Basic
    - Digest
    - NTLM *(selezionato per impostazione predefinita)*
    - Negotiate *(selezionato per impostazione predefinita)*

- **Consentire il salvataggio delle password in gestione password**  
  **Impostazione predefinita**: Disabilitato  
  CSP Microsoft Edge: [browser/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Abilitare Microsoft Edge per salvare le password utente. 
  - Se si Abilita questo criterio, gli utenti possono salvare le proprie password in Microsoft Edge. La volta successiva che visitano il sito, Microsoft Edge immetterà la password automaticamente. 
  - Se si disabilita questo criterio, gli utenti non possono salvare nuove password, ma possono comunque usare le password salvate in precedenza. 
  
  Quando si imposta questo criterio su *abilitato* o *disabilitato*, gli utenti non possono modificare o eseguire l'override di questi criteri in Microsoft Edge. 
  
  Se si imposta questa opzione su *non configurato*, gli utenti possono salvare le password, oltre a disattivare questa funzionalità.

- **Controllare le estensioni che non possono essere installate**  
  **Impostazione predefinita**: Abilitato  

  Elencare le estensioni specifiche che gli utenti non possono installare in Microsoft Edge. Quando si distribuisce questo criterio, tutte le estensioni in questo elenco installate in precedenza sono disabilitate e l'utente non sarà in grado di abilitarle. Se si rimuove un elemento dall'elenco di estensioni bloccate, tale estensione viene automaticamente riabilitata in qualsiasi punto in cui è stata installata in precedenza.
  
  Usare **\*** per bloccare tutte le estensioni non elencate in modo esplicito nell'elenco Consenti. Se questo criterio è impostato su *non configurato*, gli utenti possono installare qualsiasi estensione in Microsoft Edge. 
  
  Valore di esempio: extension_id1 extension_id2.  
  <br>
  - **ID estensione che l'utente deve impedire di installare (o * per tutti)**  
    Selezionare **Aggiungi** e specificare estensioni aggiuntive. **\*** è selezionata per impostazione predefinita.

- **Configurare Microsoft Defender SmartScreen**  
  **Impostazione predefinita**: Abilitato  
  CSP Microsoft Edge: [browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  Questa impostazione criterio consente di configurare se abilitare Microsoft Defender SmartScreen. Microsoft Defender SmartScreen fornisce messaggi di avviso che consentono di proteggere gli utenti da potenziali truffe di phishing e da software dannoso. 
  
  - Per impostazione predefinita, Microsoft Defender SmartScreen è attivato. Se si abilita questa impostazione, Microsoft Defender SmartScreen viene attivato e gli utenti non possono disattivarlo.
  - Se si disabilita questa impostazione, Microsoft Defender SmartScreen viene disattivato e gli utenti non possono attivarlo. 
  - Se è impostato su *non configurato*, gli utenti possono scegliere se usare Microsoft Defender SmartScreen. 
  
  Questo criterio è disponibile solo per le istanze di Windows che fanno parte di un dominio di Microsoft Active Director o per le istanze di Windows 10 Pro o Enterprise registrate per la gestione dei dispositivi.

- **Consenti host di messaggistica nativa a livello di utente (installati senza autorizzazioni di amministratore)**  
  **Impostazione predefinita**: Disabilitato  

  Consente di installare gli host di messaggistica nativa a livello di utente. 
  - Se si disabilita questo criterio, Microsoft Edge utilizzerà solo gli host di messaggistica nativa installati a livello di sistema. Per impostazione predefinita, se non si configura questo criterio, Microsoft Edge consente l'utilizzo degli host di messaggistica nativa a livello di utente.

## <a name="next-steps"></a>Passaggi successivi

[Usare le linee di base di sicurezza in Intune](security-baselines.md)
