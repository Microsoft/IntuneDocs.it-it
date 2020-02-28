---
title: Suggerimenti per la risoluzione dei problemi relativi ai criteri di BitLocker in Microsoft Intune
titleSuffix: Microsoft Intune
description: Descrive come abilitare la crittografia BitLocker in un dispositivo usando i criteri di Intune e come verificare che i criteri siano stati distribuiti correttamente in un dispositivo.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3b32268d0b04dee84a737b9a1c768bc4fab7202
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556500"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Risolvere i problemi relativi ai criteri di BitLocker in Microsoft Intune

Questo articolo può essere utile agli amministratori di Intune per comprendere come i dispositivi Windows 10 configurano BitLocker in base ai criteri di Intune. Include inoltre indicazioni su come risolvere i problemi relativi alle impostazioni di BitLocker nei dispositivi gestiti con Intune.  

## <a name="understanding-bitlocker"></a>Informazioni su BitLocker

Crittografia unità BitLocker è un servizio offerto dai sistemi operativi Microsoft Windows che consente agli utenti di crittografare i dati sui dischi rigidi. BitLocker supporta la crittografia per le unità del sistema operativo, le unità dei supporti rimovibili e le unità dati fisse. Supporta inoltre l'utilizzo della crittografia a 256 bit per una migliore protezione dei dati sensibili.  

Con Microsoft Intune, sono disponibili i metodi seguenti per gestire BitLocker nei dispositivi Windows 10:

- **Criteri di configurazione del dispositivo** - Alcune opzioni predefinite dei criteri sono disponibili in Intune quando si crea un profilo di configurazione del dispositivo per gestire Endpoint Protection. Per trovare queste opzioni, [creare un profilo di dispositivo per Endpoint Protection](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings), selezionare **Windows 10 e versioni successive** per *Piattaforma* e quindi selezionare la categoria **Crittografia di Windows** per *Impostazioni*. 

   Per informazioni sulle opzioni e sulle funzionalità disponibili, vedere quanto riportato di seguito: [Crittografia di Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Baseline di sicurezza** - le [baseline di sicurezza](security-baselines.md) sono gruppi noti di impostazioni e valori predefiniti consigliati dal team di sicurezza competente per proteggere i dispositivi Windows. Diverse origini di baseline, come *Baseline di sicurezza di MDM* o *Baseline di Microsoft Defender ATP* possono gestire le stesse impostazioni e anche impostazioni diverse tra di loro. Possono inoltre gestire le stesse impostazioni gestite con i criteri di configurazione del dispositivo. 

Oltre a Intune, per hardware conforme a standby moderno e HSTI, quando si usa una di queste funzionalità, la Crittografia dispositivo di BitLocker viene attivata automaticamente ogni volta che l'utente aggiunge un dispositivo ad Azure AD. Azure AD offre un portale in cui viene anche eseguito il backup delle chiavi di ripristino, in modo che gli utenti possano recuperare la chiave di ripristino per la modalità self-service, se necessario.

È anche possibile che le impostazioni di BitLocker siano gestite diversamente, ad esempio tramite Criteri di gruppo oppure manualmente dall'utente del dispositivo.

Indipendentemente dalla modalità di applicazione delle impostazioni a un dispositivo, i criteri di BitLocker usano il [CSP di BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) per configurare la crittografia sul dispositivo. Il CSP di BitLocker è integrato in Windows e quando Intune distribuisce un criterio di BitLocker a un dispositivo assegnato, è il CSP di BitLocker nel dispositivo a scrivere i valori appropriati nel Registro di sistema di Windows per rendere effettive le impostazioni del criterio.

Per altre informazioni su BitLocker, vedere le risorse seguenti:

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Panoramica di BitLocker e domande frequenti sui requisiti](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Una volta acquisite le nozioni generali sul funzionamento di questi criteri, è possibile esaminare in che modo verificare se le impostazioni di BitLocker vengono applicate correttamente a un client Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Verificare l'origine delle impostazioni di BitLocker

Quando si esamina un problema di BitLocker in un dispositivo Windows 10, è importante innanzitutto determinare se il problema è correlato a Intune o a Windows. Una volta rilevata l'origine probabile dell'errore, è possibile impegnarsi a risolvere il problema in modo mirato e, se necessario, richiedere il supporto del team competente.  

Come primo passaggio, determinare se i criteri di Intune sono stati distribuiti correttamente nel dispositivo di destinazione. Nell'esempio seguente, un criterio di configurazione del dispositivo distribuisce le impostazioni di Crittografia di Windows (BitLocker), come illustrato:

![Criterio di configurazione del dispositivo di Crittografia di Windows con le impostazioni](./media/troubleshooting-bitlocker-policies/settings.png)

Come è possibile verificare se le impostazioni sono state applicate al dispositivo di destinazione? Di seguito sono illustrati alcuni modi per eseguire questa operazione.

### <a name="device-configuration-policy-device-status"></a>Stato del dispositivo nel criterio di configurazione del dispositivo  

Quando si usa un criterio di configurazione del dispositivo per configurare BitLocker, è possibile controllare lo stato del criterio nel portale di Intune.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** e quindi selezionare il profilo che contiene le impostazioni di BitLocker.

3. Dopo aver selezionato il profilo da visualizzare, selezionare **Stato del dispositivo**. Vengono elencati i dispositivi assegnati al profilo e la colonna *Stato del dispositivo* indica se un dispositivo ha distribuito il profilo in modo corretto.

Tenere presente che può verificarsi un ritardo tra il ricevimento di un criterio di BitLocker su un dispositivo e la crittografia completa dell'unità.  

### <a name="use-control-panel-on-the-client"></a>Usare il Pannello di controllo del client  

Su un dispositivo in cui è stato abilitato BitLocker ed è stata crittografata un'unità, è possibile visualizzare lo stato di BitLocker dal Pannello di controllo del dispositivo. Sul dispositivo aprire **Pannello di controllo** > **Sistema e sicurezza** > **Crittografia unità BitLocker**. La conferma viene visualizzata come illustrato nella figura seguente.  

![BitLocker è attivato nel Pannello di controllo](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Usare un prompt dei comandi  

Su un dispositivo in cui è stato abilitato BitLocker ed è stata crittografata un'unità, avviare il prompt dei comandi con credenziali di amministratore e quindi eseguire `manage-bde -status`. I risultati dovrebbero essere simili all'esempio seguente:  
risultato ![0A del comando status](./media/troubleshooting-bitlocker-policies/command.png)

Nell’esempio:

- La **protezione BitLocker** è **attiva**
- La **percentuale crittografata** è **100%**
- Il **metodo di crittografia** è **XTS-AES 256**

È anche possibile controllare le **protezioni con chiave** eseguendo il comando seguente:

```cmd
Manage-bde -protectors -get c:
```

In alternativa, con PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Esaminare la configurazione della chiave del Registro di sistema del dispositivo

Dopo aver distribuito i criteri di BitLocker in un dispositivo, visualizzare la chiave del Registro di sistema seguente nel dispositivo ed esaminare la configurazione delle impostazioni di BitLocker:  *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. Ad esempio:

![Chiave del Registro di sistema di BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Questi valori vengono configurati dal CSP di BitLocker. Verificare che i valori delle chiavi corrispondano alle impostazioni specificate nell'origine dei criteri di crittografia Windows di Intune. Per altre informazioni su ognuna di queste impostazioni, vedere [CSP BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> Anche il Visualizzatore eventi di Windows contiene varie informazioni correlate a BitLocker. La quantità di informazioni è troppo ampia per essere elencata in questo articolo, ma è sufficiente eseguire una ricerca di **API BitLocker** per ottenere molte informazioni utili.

### <a name="check-the-mdm-diagnostics-report"></a>Controllare il report di diagnostica MDM

Su un dispositivo in cui è abilitato BitLocker è possibile generare e visualizzare un report di diagnostica MDM dal dispositivo di destinazione per verificare che il criterio di BitLocker sia presente. La presenza delle impostazioni del criterio nel report è un'altra indicazione che il criterio è stato distribuito in modo corretto. Il video *Microsoft Helps* accessibile dal collegamento seguente illustra come acquisire un report di diagnostica MDM da un dispositivo Windows.

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Quando si analizza il report di diagnostica MDM, a prima vista il contenuto può sembrare un po' confuso. Di seguito è riportato un esempio che mostra come correlare il contenuto del report alle impostazioni definite in un criterio:

![Esempio di report di diagnostica MDM](./media/troubleshooting-bitlocker-policies/report.png)

Il risultato dell'output mostra i valori corrispondenti ai valori del criterio di BitLocker:

![Risultato dell'output con i valori ](./media/troubleshooting-bitlocker-policies/output.png)

Risultati dell'output di diagnostica MDM:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Fare riferimento alla [documentazione del CSP di BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) per determinare il significato dei singoli valori. A titolo esemplificativo, nell'immagine seguente è riportato un frammento di codice.

![Finalità dei valori](./media/troubleshooting-bitlocker-policies/shared-example.png)

In modo analogo, è possibile visualizzare tutti i valori e verificarli dal collegamento del CSP di BitLocker.

> [!TIP]
> Lo scopo principale del report di diagnostica MDM è quello di facilitare il supporto tecnico Microsoft durante la risoluzione dei problemi. Se si invia una richiesta di supporto per Intune e il problema riguarda i client Windows, è sempre consigliabile raccogliere questo report e includerlo nella richiesta di supporto.

## <a name="troubleshooting-bitlocker-policy"></a>Risoluzione dei problemi relativi al criterio di BitLocker

A questo punto dovrebbe essere chiaro come verificare che il criterio di BitLocker sia stato distribuito correttamente da Intune, che consegna la configurazione di BitLocker al CSP di BitLocker in Windows.

**Il criterio non riesce a raggiungere il dispositivo**. Quando il criterio di Intune non è presente in nessuna funzionalità:

- **Il dispositivo è registrato correttamente in Microsoft Intune?** Se non lo è, è necessario risolvere questo problema prima di passare a eventuali altri problemi specifici del criterio. Per informazioni sulla risoluzione dei problemi di registrazione di Windows, vedere [questo articolo](../enrollment/troubleshoot-windows-enrollment-errors.md).

- **È presente una connessione di rete attiva nel dispositivo?** Se il dispositivo è in modalità aereo o è disattivato o se si trova in un lungo senza connettività di rete, il criterio non viene recapitato né applicato finché la connettività non viene ripristinata.

- **Il criterio di BitLocker è stato distribuito all'utente o al gruppo di dispositivi corretto?** Verificare che l'utente o il dispositivo corretto sia un membro dei gruppi di destinazione della distribuzione.

**Il criterio è presente, ma non tutte le impostazioni sono state configurate correttamente**. Quando il criterio di Intune raggiunge il dispositivo, ma non tutte le configurazioni risultano impostate:

- **Non viene distribuito l'intero criterio o il problema è limitato ad alcune impostazioni?** Nel caso in cui non vengono applicate solo alcune impostazioni del criterio, tenere presente quanto segue:

  1. **Non tutte le impostazioni di BitLocker sono supportate in tutte le versioni di Windows**.
     Il criterio viene distribuito a un dispositivo come singola unità. Se pertanto alcune impostazioni si applicano e altre no, si può essere certi che il criterio è stato ricevuto. In questo scenario è possibile che le impostazioni non applicate non siano supportate dalla versione di Windows nel dispositivo. Per informazioni dettagliate sui requisiti di versione per ogni impostazione, vedere [CSP BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) nella documentazione di Windows.

  2. **Non tutti i componenti hardware includono il supporto per BitLocker**.
     Anche se si dispone della versione corretta di Windows, è possibile che l'hardware del dispositivo sottostante non soddisfi i requisiti per la crittografia BitLocker. I [requisiti di sistema per BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) sono riportati nella documentazione di Windows, ma è soprattutto importante verificare che il dispositivo disponga di un chip TPM compatibile (1.2 o versione successiva) e di un BIOS conforme a Trusted Computing Group (TCG) o di un firmware UEFI.
     
La **crittografia BitLocker non viene eseguita automaticamente**: i criteri di Endpoint Protection sono stati configurati, l'opzione "Avviso per la crittografia dischi di altro tipo" è stata impostata sul blocco e viene ancora visualizzata la crittografia guidata:

- **Verificare che la versione di Windows supporti la crittografia automatica** Questa operazione richiede almeno la versione 1803. Se l'utente non è un amministratore nel dispositivo, la versione minima richiesta è 1809. Nella versione 1809 è stato anche aggiunto il supporto per i dispositivi che non supportano la modalità di standby moderno

Il **dispositivo crittografato con BitLocker viene visualizzato come non conforme ai criteri di conformità di Intune**: il problema si verifica quando la crittografia BitLocker non viene completata. In base ad alcuni fattori, ad esempio le dimensioni del disco, il numero di file e le impostazioni di BitLocker, la crittografia BitLocker può richiedere molto tempo. Al termine della crittografia, il dispositivo verrà visualizzato come conforme. I dispositivi possono anche diventare temporaneamente non conformi immediatamente dopo un'installazione recente degli aggiornamenti di Windows.

**I dispositivi vengono crittografati con un algoritmo a 128 bit quando il criterio specifica 256 bit**: per impostazione predefinita, Windows 10 crittografa un'unità con la crittografia XTS-AES a 128 bit. Vedere questa guida per l' [Impostazione della crittografia a 256 bit per BitLocker durante l'Autopilot](https://techcommunity.microsoft.com/t5/intune-customer-success/setting-256-bit-encryption-for-bitlocker-during-autopilot-with/ba-p/323791#).


**Esempio di indagine**

- Si distribuisce un criterio di BitLocker a un dispositivo Windows 10 e l'impostazione **Crittografa i dispositivi** indica uno stato di **errore** nel portale.

- Come suggerito dal nome, questa impostazione consente a un amministratore di richiedere l'attivazione della crittografia usando *BitLocker > Crittografia dispositivo*. In base ai suggerimenti per la risoluzione dei problemi indicati in precedenza, si controlla prima di tutto il report di diagnostica MDM. Il report conferma che nel dispositivo è stato distribuito il criterio corretto:

  ![Il report conferma la distribuzione del criterio corretto nel dispositivo](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- È anche possibile verificare l'esito positivo dell'operazione nel Registro di sistema:

  ![Il valore di RequiredDeviceEncryption nel Registro di sistema è 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- A questo punto, si controlla lo stato del TPM usando PowerShell e si scopre che il TPM non è disponibile nel dispositivo:

  ![Verifica dello stato del TPM con PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Poiché BitLocker si basa sul TPM, è possibile dedurre che il problema di BitLocker non è correlato a Intune o al criterio, ma è dovuto al fatto che il dispositivo stesso non dispone di un chip TPM o che il TPM è disabilitato nel BIOS.

  Come altro suggerimento, è possibile verificare questa stessa condizione nel Visualizzatore eventi di Windows in **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **BitLocker API**. Nel registro eventi dell'**API BitLocker** è presente un ID evento 853 da cui risulta che il TPM non è disponibile:

  ![ID evento 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > È anche possibile controllare lo stato del TPM eseguendo **tpm.msc** sul dispositivo.

## <a name="summary"></a>Riepilogo

Quando si risolvono i problemi relativi al criterio di BitLocker con Intune e si può verificare che il criterio raggiunge il dispositivo previsto, è possibile sicuramente presupporre che il problema non sia direttamente correlato a Intune. È molto più probabile che si tratti di un problema relativo al sistema operativo Windows o all'hardware. In questo caso, iniziare a esaminare altre aree, come la configurazione del TPM o l'avvio UEFI e protetto.

## <a name="next-steps"></a>Passaggi successivi  

Di seguito sono elencate altre risorse che possono risultare utili quando si usa BitLocker:

- [Documentazione del prodotto BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Requisiti di sistema per BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Domande frequenti su BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Documentazione del CSP di BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Impostazioni del criterio di crittografia di Windows per Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Crittografia BitLocker automatica indipendente dall'hardware con AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Criteri CSP per la crittografia BitLocker nei dispositivi Autopilot](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Procedura dettagliata per la creazione e la distribuzione del criterio di BitLocker con Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
