---
title: Suggerimenti per la risoluzione dei problemi relativi ai criteri di BitLocker in Microsoft Intune
titleSuffix: Microsoft Intune
description: Viene descritto come abilitare la crittografia BitLocker in un dispositivo usando i criteri di Intune e come verificare che i criteri siano stati distribuiti correttamente in un dispositivo.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 197ad888dc8a07cc35efbaec538fde93c76c81c3
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817625"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Risolvere i problemi relativi ai criteri di BitLocker in Microsoft Intune

Questo articolo può aiutare gli amministratori di Intune a comprendere come i dispositivi Windows 10 configurano BitLocker in base ai criteri di Intune. Questo articolo fornisce anche indicazioni su come risolvere i problemi relativi alle impostazioni di BitLocker nei dispositivi gestiti con Intune.  

## <a name="understanding-bitlocker"></a>Informazioni su BitLocker

Crittografia unità BitLocker è un servizio offerto dai sistemi operativi Microsoft Windows che consente agli utenti di crittografare i dati sui dischi rigidi. BitLocker supporta la crittografia per le unità del sistema operativo, le unità di supporto rimovibili e le unità dati fisse. BitLocker supporta inoltre l'utilizzo della crittografia a 256 bit per una migliore protezione dei dati sensibili.  

Con Microsoft Intune, sono disponibili i metodi seguenti per gestire BitLocker nei dispositivi Windows 10:

- **Criteri di configurazione del dispositivo **-alcune opzioni predefinite dei criteri sono disponibili nella console di amministrazione di Intune in **Device Configuration** > **Endpoint Protection** > **Windows Encryption Policy**. Qui è possibile trovare tutte le opzioni e le funzionalità disponibili: [crittografia di Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- Le linee di base di **sicurezza** -  le linee di[base di sicurezza](security-baselines.md) sono gruppi noti di impostazioni e valori predefiniti consigliati dal team di sicurezza pertinente per proteggere i dispositivi Windows. Diverse origini di base, ad esempio la baseline di *sicurezza MDM* o la *baseline Microsoft Defender ATP* , possono gestire le stesse impostazioni e le impostazioni diverse. Possono anche gestire le stesse impostazioni gestite con i criteri di configurazione del dispositivo. 

Oltre a Intune, è possibile che le impostazioni di BitLocker siano gestite in altri modi, ad esempio Criteri di gruppo, o impostate manualmente da un utente del dispositivo.

Indipendentemente dal modo in cui le impostazioni vengono applicate a un dispositivo, i criteri BitLocker usano il [CSP di BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) per configurare la crittografia nel dispositivo. Il CSP di BitLocker è integrato in Windows e quando Intune distribuisce i criteri di BitLocker in un dispositivo assegnato, è il CSP di BitLocker nel dispositivo che scrive i valori appropriati nel registro di sistema di Windows in modo che le impostazioni dei criteri possano avere effetto.

Per ulteriori informazioni su BitLocker, vedere le risorse riportate di seguito.

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Panoramica di BitLocker e domande frequenti sui requisiti](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Ora che si dispone di una conoscenza generale del funzionamento di questi criteri e del relativo funzionamento, vedere come verificare se le impostazioni di BitLocker si applicano correttamente a un client Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Verificare l'origine delle impostazioni di BitLocker

Quando si esamina un problema di BitLocker in un dispositivo Windows 10, è importante innanzitutto determinare se il problema è correlato a Intune o a Windows. Una volta rilevata la probabile fonte di errore, è possibile concentrare l'attenzione sulla risoluzione dei problemi nel posto giusto e, se necessario, ottenere supporto dal team corretto.  

Come primo passaggio, determinare se i criteri di Intune sono stati distribuiti correttamente nel dispositivo di destinazione. Nell'esempio seguente si dispone di un criterio di configurazione del dispositivo che distribuisce le impostazioni di crittografia di Windows (BitLocker), come illustrato: 

![Criteri di configurazione del dispositivo di crittografia Windows con le impostazioni](./media/troubleshooting-bitlocker-policies/settings.png)

Come è possibile verificare che le impostazioni siano state applicate al dispositivo di destinazione? Di seguito sono riportati alcuni modi per eseguire questa operazione.

### <a name="device-configuration-policy-device-status"></a>Stato dispositivo criteri di configurazione del dispositivo  

Quando si usano i criteri di configurazione del dispositivo per configurare BitLocker, è possibile controllare lo stato del criterio nel portale di Intune. Nel portale passare a **Configurazione dispositivo** > **profili** > selezionare il profilo che contiene le impostazioni di BitLocker e quindi selezionare **stato del dispositivo**. Sono elencati i dispositivi assegnati al profilo e la colonna *stato dispositivo* indica se il profilo è stato distribuito correttamente da un dispositivo. 

Si noti che è possibile che si verifichi un ritardo tra un dispositivo che riceve un criterio di BitLocker e che l'unità sia completamente crittografata.  

 
### <a name="use-control-panel-on-the-client"></a>Usare il pannello di controllo sul client  

In un dispositivo che ha abilitato BitLocker e crittografato un'unità, è possibile visualizzare lo stato di BitLocker da un pannello di controllo dei dispositivi. Sul dispositivo aprire il **Pannello di controllo** > **sistema e sicurezza** > **crittografia unità BitLocker**. La conferma viene visualizzata come illustrato nella figura seguente.  

![BitLocker è attivato nel pannello di controllo](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Usare un prompt dei comandi  

In un dispositivo che ha abilitato BitLocker e crittografato un'unità, avviare il prompt dei comandi con credenziali di amministratore, quindi eseguire `manage-bde -status`. I risultati dovrebbero essere simili all'esempio seguente:  
risultato ![0A del comando status](./media/troubleshooting-bitlocker-policies/command.png)

Nell'esempio: 
- La **protezione BitLocker** è **attiva**,  
- La **percentuale crittografata** è **100%**  
- Il **metodo di crittografia** è **XTS-AES 256**.  

È anche possibile controllare le **protezioni con chiave** eseguendo il comando seguente:

```cmd
Manage-bde -protectors -get c:
```

In alternativa, con PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Esaminare la configurazione della chiave del registro di sistema Devices   

Dopo che i criteri di BitLocker sono stati distribuiti correttamente in un dispositivo, visualizzare la seguente chiave del registro di sistema nel dispositivo in cui è possibile esaminare la configurazione delle impostazioni di BitLocker: *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker* . Ad esempio:

![Chiave del registro di sistema di BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Questi valori vengono configurati dal CSP di BitLocker. Verificare che i valori delle chiavi corrispondano alle impostazioni specificate nell'origine dei criteri di crittografia Windows di Intune. Per ulteriori informazioni su ognuna di queste impostazioni, vedere [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> Windows Visualizzatore eventi conterrà anche le varie informazioni relative a BitLocker. Sono presenti troppi elenchi da elencare, ma la ricerca di **API BitLocker** fornirà numerose informazioni utili.

### <a name="check-the-mdm-diagnostics-report"></a>Controllare il report di diagnostica MDM  

In un dispositivo in cui è abilitato BitLocker è possibile generare e visualizzare un report di diagnostica MDM dal dispositivo di destinazione per verificare che i criteri di BitLocker siano presenti. Se è possibile visualizzare le impostazioni dei criteri nel report, è un'altra indicazione che il criterio è stato distribuito correttamente. Il video *Microsoft helps* nel collegamento seguente illustra come acquisire un report di diagnostica MDM da un dispositivo Windows. 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Quando si analizza il report di diagnostica MDM, il contenuto può sembrare un po' confuso alla prima. Di seguito è riportato un esempio in cui viene illustrato come correlare gli elementi del report con le impostazioni in un criterio:

![Esempio di report di diagnostica MDM](./media/troubleshooting-bitlocker-policies/report.png)

Il risultato dell'output Mostra i valori che corrispondono ai valori dei criteri di BitLocker:

![Risultato output Mostra i valori ](./media/troubleshooting-bitlocker-policies/output.png)

Risultati di output di diagnostica MDM:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

È possibile fare riferimento alla [documentazione di BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) per verificare il significato di ogni valore. Per questo esempio, un frammento di codice viene condiviso nell'immagine seguente.

![Finalità dei valori](./media/troubleshooting-bitlocker-policies/shared-example.png)

 Analogamente, è possibile visualizzare tutti i valori e verificarli dal collegamento BitLocker CSP.

> [!TIP]
> Lo scopo principale del report di diagnostica MDM è assistere supporto tecnico Microsoft durante la risoluzione dei problemi. Se si apre un caso di supporto per Intune e il problema riguarda i client Windows, è sempre consigliabile raccogliere il report e includerlo nella richiesta di supporto.

## <a name="troubleshooting-bitlocker-policy"></a>Risoluzione dei problemi relativi ai criteri BitLocker

A questo punto dovrebbe essere opportuno verificare che i criteri di BitLocker siano stati distribuiti correttamente da Intune, il che consente la configurazione di BitLocker per BitLocker in WIndows.  

**Il criterio non riesce a raggiungere il dispositivo** , quando i criteri di Intune non sono presenti in alcuna capacità:  
- **Il dispositivo è registrato correttamente in Microsoft Intune?** In caso contrario, è necessario risolverlo prima di risolvere eventuali problemi specifici del criterio. Per informazioni sulla risoluzione dei problemi di registrazione di Windows, vedere [qui](../enrollment/troubleshoot-windows-enrollment-errors.md).  
- **Esiste una connessione di rete attiva sul dispositivo?** Se il dispositivo è in modalità aereo o è disattivato o se l'utente ha il dispositivo in un percorso senza servizio, il criterio non verrà recapitato o applicato finché non viene ripristinata la connettività di rete.  
- **Il criterio BitLocker è stato distribuito all'utente o al gruppo di dispositivi corretto?** Verificare che l'utente o il dispositivo corretto sia un membro dei gruppi di destinazione.  

Il **criterio è presente, ma non tutte le impostazioni sono state configurate correttamente** . quando il criterio di Intune raggiunge il dispositivo, ma non tutte le configurazioni sono impostate:  
- **La distribuzione dell'intero criterio ha esito negativo o solo alcune impostazioni che non si applicano?** Se ci si trova a dover affrontare uno scenario in cui non si applicano solo alcune impostazioni dei criteri, verificare le seguenti considerazioni:

  1. **Non tutte le impostazioni di BitLocker sono supportate in tutte le versioni di Windows**.  
  Il criterio si arresta in un dispositivo come una singola unità, quindi se alcune impostazioni si applicano e altre no, è possibile essere certi che il criterio stesso sia stato ricevuto. In questo scenario è possibile che la versione di Windows nel dispositivo non supporti le impostazioni problematiche. Per informazioni dettagliate sui requisiti di versione per ogni impostazione, vedere [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) nella documentazione di Windows.  

  1. **BitLocker non è supportato in tutti i componenti hardware**.  
  Anche se si dispone della versione corretta di Windows, è possibile che l'hardware del dispositivo sottostante non soddisfi i requisiti per la crittografia BitLocker. È possibile trovare i [requisiti di sistema per BitLocker (https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) nella documentazione di Windows, ma gli aspetti principali da verificare sono che il dispositivo disponga di un chip TPM compatibile (1,2 o versione successiva) e di un BIOS conforme a Trusted Computing Group (TCG) o un firmware UEFI.

**Esempio di analisi** : si distribuisce un criterio di BitLocker in un dispositivo Windows 10 e l'impostazione **Crittografa dispositivi** indica uno stato di **errore** nel portale.

- Come suggerisce il nome, questa impostazione consente a un amministratore di richiedere l'abilitazione della crittografia utilizzando *BitLocker > crittografia del dispositivo*. Usando i suggerimenti per la risoluzione dei problemi indicati in precedenza, è prima di tutto necessario controllare il report di diagnostica MDM. Il report conferma che nel dispositivo è stato distribuito il criterio corretto:

  ![Il report conferma la distribuzione del criterio corretto nel dispositivo](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- È anche possibile verificare l'esito positivo nel registro di sistema:

  ![Il valore del registro di sistema RequiredDeviceEncryption Mostra 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- A questo punto, si controlla lo stato del TPM usando PowerShell e si scopre che TPM non è disponibile nel dispositivo:

  ![Stato del TPM verificato con PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Poiché BitLocker si basa su TPM, è possibile concludere che BitLocker non ha esito negativo a causa di un problema con Intune o con il criterio, ma piuttosto perché il dispositivo stesso non dispone di un chip TPM o TPM è disabilitato nel BIOS.

  Come suggerimento aggiuntivo, è possibile verificare lo stesso nel Visualizzatore eventi di Windows in **registri applicazioni e servizi** > **Windows** > **API BitLocker**. Nel registro eventi dell' **API BitLocker** è presente un ID evento 853 che indica che il TPM non è disponibile:

  ![ID evento 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > È anche possibile controllare lo stato del TPM eseguendo **TPM. msc** nel dispositivo.



## <a name="summary"></a>Riepilogo

Quando si risolvono i problemi relativi ai criteri di BitLocker con Intune e si può verificare che i criteri raggiungano il dispositivo previsto, è preferibile presupporre che il problema non sia direttamente correlato a Intune. Il problema è più probabile di un problema con il sistema operativo Windows o l'hardware. In questo caso, iniziare a cercare in altre aree, ad esempio la configurazione del TPM o UEFI e l'avvio protetto.

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>Passaggi successivi  

Di seguito sono riportate altre risorse che potrebbero essere utili quando si utilizza BitLocker:

- [Documentazione del prodotto BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Requisiti di sistema per BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Domande frequenti su BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Documentazione di BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Impostazioni dei criteri di crittografia di Windows per Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Crittografia automatica BitLocker indipendente dall'hardware con AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Criteri CSP per la crittografia BitLocker nei dispositivi pilota automatici](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Procedura dettagliata per la creazione e la distribuzione di criteri BitLocker con Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)