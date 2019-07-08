---
title: Usare le baseline di sicurezza in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o configurare le impostazioni di sicurezza di Windows consigliate per proteggere utenti e dati nei dispositivi con Microsoft Intune per la gestione dei dispositivi mobili. Abilitare BitLocker, configurare Microsoft Defender Advanced Threat Protection, controllare Internet Explorer, usare SmartScreen, impostare criteri di sicurezza locali, richiedere una password, bloccare i download da Internet e altro ancora.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93e470175829008b72b5b8991188f3c92e38a567
ms.sourcegitcommit: 690e680e854b7d707421c5e06f134e493f4f4194
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416840"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>Usare le baseline di sicurezza per configurare i dispositivi Windows 10 in Intune

Le baseline di sicurezza di Intune sono utili per la sicurezza e la protezione di dispositivi e utenti. Le baseline di sicurezza sono gruppi preconfigurati di impostazioni di Windows che consentono di applicare un gruppo di impostazioni e valori predefiniti noti, consigliati dai team di sicurezza pertinenti. Quando si crea un profilo di baseline di sicurezza in Intune, si crea un profilo di *configurazione del dispositivo*.

Questa funzionalità si applica a:

- Windows 10 versione 1809 e successive

Le baseline di sicurezza vengono distribuite a gruppi di utenti o dispositivi in Intune e le impostazioni si applicano ai dispositivi che eseguono Windows 10 o versioni successive. Ad esempio, la *MDM Security Baseline* (Baseline di sicurezza MDM) abilita automaticamente BitLocker per le unità rimovibili, richiede automaticamente una password per sbloccare un dispositivo, disabilita automaticamente l'autenticazione di base e altro ancora. Quando un valore predefinito non funziona per l'ambiente specifico, è possibile personalizzare la baseline per applicare le impostazioni necessarie.  

Tipi di baseline separati possono includere le stesse impostazioni, ma usare valori predefiniti diversi per queste impostazioni. È importante conoscere le impostazioni predefinite nelle baseline che si sceglie di usare per poter quindi modificare ogni baseline per adattarla alle specifiche esigenze dell'organizzazione.  

> [!NOTE]
> Microsoft sconsiglia di usare le versioni di anteprima delle baseline di sicurezza in ambiente di produzione. Le impostazioni in una baseline di anteprima potrebbero cambiare nel corso della fase di anteprima. 

L'obiettivo dell'uso delle baseline di sicurezza è avere un flusso di lavoro end-to-end sicuro quando si lavora con Microsoft 365. Alcuni dei vantaggi sono i seguenti:

- Una baseline di sicurezza include le procedure consigliate e le raccomandazioni per le impostazioni con effetti sulla sicurezza. Partner di Intune con lo stesso team di sicurezza per Windows che crea le baseline di sicurezza di Criteri di gruppo. Queste raccomandazioni si basano su linee guida e una vasta esperienza.
- Se non si ha familiarità con Intune e non si sa da dove iniziare, le baseline di sicurezza rappresentano un vantaggio. È possibile creare e distribuire rapidamente un profilo sicuro, sapendo che si sta contribuendo alla protezione delle risorse e dei dati dell'organizzazione.
- Se si usano Criteri di gruppo, la migrazione a Intune per la gestione è molto più semplice con queste baseline. Queste baseline sono incluse in modo nativo in Intune e includono un'esperienza di gestione moderna.



[Baseline della sicurezza di Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) è un'ottima risorsa per scoprire di più su questa funzionalità. [Mobile device management](https://docs.microsoft.com/windows/client-management/mdm/) (Gestione di dispositivi mobili) è una valida fonte di informazioni su MDM e sulle funzionalità disponibili per i dispositivi Windows.

## <a name="security-baseline-versions-and-instances"></a>Versioni e istanze delle baseline di sicurezza
Periodicamente diventano disponibili nuovi aggiornamenti per una baseline. Ogni istanza di una nuova versione di una baseline può aggiungere o rimuovere impostazioni o introdurre altre modifiche. Ad esempio, quando diventano disponibili nuove impostazioni di Windows 10 con le nuove versioni di Windows 10, la baseline di sicurezza MDM potrebbe ricevere una nuova istanza di versione che include le impostazioni più recenti.  

Nella console di Intune è possibile visualizzare le baseline di sicurezza disponibili e relative informazioni. Le informazioni disponibili includono il numero di profili esistenti che usano tale tipo di baseline, il numero di istanze separate del tipo di baseline disponibili e la data di disponibilità, o pubblicazione, dell'ultima istanza più recente.  L'esempio seguente mostra il riquadro per una baseline di sicurezza MDM molto usata:  

![Riquadro della baseline](./media/security-baselines/baseline-tile.png)

Per visualizzare informazioni sulle versioni di baseline usate, selezionare una baseline e quindi selezionare **Versioni**. Intune visualizza informazioni dettagliate sulle versioni usate dai profili. Nel riquadro Versioni è possibile selezionare una singola versione per visualizzare ulteriori dettagli sui profili che usano tale versione. È anche possibile selezionare due versioni diverse e quindi scegliere **Compare baselines** (Confronta baseline) per scaricare un file CSV con informazioni dettagliate sulle differenze.  

![Confrontare le baseline](./media/security-baselines/compare-baselines.png)

Quando si crea un *profilo* di baseline di sicurezza, il profilo usa automaticamente l'istanza della baseline di sicurezza rilasciata più di recente.  È possibile continuare a usare e modificare i profili creati in precedenza che usano un'istanza di versione precedente della baseline, incluse le baseline create con una versione di anteprima. 

I profili di baseline di sicurezza supportano una [modifica della versione](#change-the-baseline-instance-for-a-profile) della baseline in uso. Questo significa che quando viene pubblicata una nuova versione, non è necessario creare un nuovo profilo di baseline per sfruttarne i vantaggi. Al contrario, quando si è pronti, è possibile selezionare un profilo di baseline e quindi usare l'opzione predefinita per cambiare la versione dell'istanza per il profilo.  

## <a name="available-security-baselines"></a>Baseline di sicurezza disponibili 

Sono disponibili le istanze di baseline di sicurezza seguenti per l'uso con Intune. Usare i collegamenti per visualizzare le impostazioni per l'istanza più recente di ogni baseline. 

- **Baseline di sicurezza MDM**
  - [Baseline di sicurezza MDM per la primavera 2019 (19H1)](security-baseline-settings-mdm.md)
  - [Anteprima: Baseline della sicurezza MDM per ottobre 2018](security-baseline-settings-mdm-archive.md)

- **Baseline di Windows Defender ATP**  
  *(Per usare questa baseline, l'ambiente deve soddisfare i prerequisiti per l'uso di [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites))* .
  - [Anteprima: Baseline di Windows Defender ATP](security-baseline-settings-defender-atp.md)  

È possibile continuare a usare e modificare i profili creati in precedenza basati su un modello di anteprima, anche quando tale modello di anteprima non è più disponibile per la creazione di nuovi profili. 

## <a name="prerequisites"></a>Prerequisiti
- Per gestire le baseline in Intune, l'account deve avere il ruolo predefinito [Gestione profili e criteri](role-based-access-control.md#built-in-roles).

- Per usare alcune baseline potrebbe essere necessario avere una sottoscrizione attiva per servizi aggiuntivi, ad esempio Microsoft Defender ATP.  

## <a name="co-managed-devices"></a>Dispositivi con co-gestione

Le baseline di sicurezza nei dispositivi gestiti da Intune sono paragonabili ai dispositivi con co-gestione con Configuration Manager. I dispositivi con co-gestione usano System Center Configuration Manager e Microsoft Intune per gestire contemporaneamente i dispositivi Windows 10. Questa funzionalità consente di collegare gli investimenti esistenti per Configuration Manager ai vantaggi di Intune tramite il cloud. La [panoramica della co-gestione](https://docs.microsoft.com/sccm/comanage/overview) è un'ottima risorsa se si usa Configuration Manager e si vogliono sfruttare anche i vantaggi del cloud.

Quando si usano dispositivi con co-gestione, è necessario trasferire il carico di lavoro **Configurazione del dispositivo** (le relative impostazioni) in Intune. In [Co-management workloads](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) (Carichi di lavoro di co-gestione) sono disponibili altre informazioni.

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e quindi selezionare **Sicurezza dei dispositivi** > **Baseline di sicurezza** per visualizzare l'elenco delle baseline disponibili.


    ![Selezionare una baseline di sicurezza da configurare](./media/security-baselines/available-baselines.png)

2. Selezionare la baseline che si vuole usare e quindi selezionare **Crea profilo**.  

3. Nella scheda **Informazioni di base** specificare le proprietà seguenti:

    - **Nome**: immettere un nome per il profilo della baseline di sicurezza. Ad esempio, immettere *Profilo standard per Defender ATP*.

    - **Description**: immettere un testo che descriva gli scopi di questa baseline. Nella descrizione è possibile immettere il testo preferito. La descrizione è facoltativa ma consigliata.  

   Selezionare **Avanti** per passare alla scheda successiva. Dopo essersi spostati in una nuova scheda, è possibile selezionare il nome della scheda per tornare alla scheda visualizzata in precedenza.  

4. Nella scheda Impostazioni di configurazione visualizzare i gruppi di **Impostazioni** disponibili nella baseline selezionata. È possibile espandere un gruppo per visualizzare le impostazioni in tale gruppo e i valori predefiniti per queste impostazioni nella baseline. Per trovare impostazioni specifiche:
   - Selezionare un gruppo per espandere ed esaminare le impostazioni disponibili.  
   - Usare la barra di *ricerca* e specificare parole chiave per filtrare la visualizzazione in modo da visualizzare solo i gruppi che contengono i criteri di ricerca.  
 
   Per ogni impostazione in una baseline è disponibile una configurazione predefinita per tale versione della baseline. Riconfigurare le impostazioni predefinite in base alle specifiche esigenze aziendali. Baseline diverse potrebbero contenere la stessa impostazione e usare valori predefiniti diversi per l'impostazione, a seconda della finalità della baseline. 

    ![Espandere un gruppo per visualizzare le impostazioni per tale gruppo](./media/security-baselines/sample-list-of-settings.png)

5. Nella scheda **Tag di ambito** selezionare **Select scope tags** (Seleziona tag di ambito) per aprire il riquadro *Selezionare i tag* per assegnare tag di ambito al profilo. 

6. Nella scheda **Assegnazioni** selezionare **Selezionare i gruppi da includere** e quindi assegnare la baseline a uno o più gruppi. Usare **Selezionare i gruppi da escludere** per mettere a punto l'assegnazione.  

   ![Assegnare un profilo](./media/security-baselines/assignments.png)
  
7. Quando si è pronti per distribuire la baseline, passare alla scheda **Rivedi e crea** ed esaminare i dettagli per la baseline. Selezionare **Crea** per salvare e distribuire il profilo.  

   Non appena si crea il profilo, ne viene eseguito il push al gruppo assegnato e il profilo potrebbe essere applicato immediatamente.

   > [!TIP]  
   > Se si salva un profilo senza prima assegnarlo a gruppi, è possibile modificarlo in seguito a tale scopo.  

   ![Rivedere la baseline](./media/security-baselines/review.png) 

  
8. Dopo aver creato il profilo, è possibile modificarlo passando a **Sicurezza dei dispositivi** > **Baseline di sicurezza**, selezionare il tipo di baseline configurato e quindi selezionare **Profili**.  Selezionare il profilo nell'elenco dei profili disponibili e quindi selezionare **Proprietà**. È possibile modificare le impostazioni da tutte le schede di configurazione disponibili e quindi selezionare **Verifica e salva** per eseguire il commit delle modifiche.  

## <a name="change-the-baseline-instance-for-a-profile"></a>Modificare l'istanza della baseline per un profilo
I profili di baseline supportano la modifica dell'istanza della baseline usata dal profilo. È possibile selezionare un'istanza precedente o, più comunemente, un'istanza più recente della stessa baseline.  Non è possibile cambiare il profilo per usare due baseline diverse, ad esempio passare dall'uso di una baseline per Defender ATP all'uso della baseline di sicurezza MDM. 

Quando si configura una modifica della versione della baseline sarà disponibile un'opzione per scaricare un file CSV in cui sono elencate le modifiche tra le due versioni della baseline coinvolte. Viene anche offerta la possibilità di mantenere tutte le personalizzazioni nella versione della baseline originale e di applicarle alla nuova versione o di implementare tutte le impostazioni predefinite disponibili nella nuova versione della baseline selezionata. 

Al momento del salvataggio, dopo il completamento della conversione, la baseline viene ridistribuita immediatamente ai gruppi assegnati.  

**Durante la conversione**:
- Le nuove impostazioni che non erano presenti nella versione originale in uso vengono aggiunte e impostate per l'uso dei valori predefiniti.  

- Le impostazioni non incluse nella nuova versione della baseline selezionata vengono rimosse e non verranno più applicate da questo profilo di baseline di sicurezza.  

  Quando un'impostazione non è più gestita da un profilo di baseline, tale impostazione non viene reimpostata nel dispositivo. Al contrario, l'impostazione nel dispositivo rimane impostata sull'ultima configurazione fino a quando un altro processo gestisce l'impostazione per modificarla. Un profilo di base diverso, un'impostazione di Criteri di gruppo o una configurazione manuale eseguita nel dispositivo sono esempi di processi che possono modificare un'impostazione dopo averne interrotto la gestione. 

### <a name="to-change-the-instance-for-a-baseline"></a>Per modificare l'istanza per una baseline  

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionare **Sicurezza dei dispositivi** > **Baseline di sicurezza**, quindi selezionare il riquadro per il tipo di baseline che include il profilo da modificare.  

2. Selezionare quindi **Profili**, selezionare la casella di controllo per il profilo che si vuole modificare e quindi selezionare **Cambia versione**.  

   ![selezionare una baseline](./media/security-baselines/select-baseline.png)  

3. Nel riquadro **Cambia versione** usare l'elenco a discesa **Select a security baseline to update to** (Selezionare una baseline di sicurezza per l'aggiornamento) e selezionare l'istanza di versione da usare.  

   ![selezionare una versione](./media/security-baselines/select-instance.png)  
 
4. Selezionare **Review update** (Verifica aggiornamento) per scaricare un file CSV che visualizza la differenza tra la versione di istanza corrente dei profili e la nuova versione selezionata. Esaminare questo file in modo da conoscere le impostazioni aggiunte e rimosse, nonché i valori predefiniti per queste impostazioni nel profilo aggiornato.  

   Quando si è pronti, continuare con il passaggio successivo.  

5. Scegliere una delle due opzioni per **Select a method to update the profile** (Selezionare un metodo per aggiornare il profilo): 
   - **Accept baseline changes but keep my existing setting customizations** (Accetta le modifiche della baseline ma mantieni le personalizzazioni delle impostazioni esistenti) - Questa opzione consente di mantenere le personalizzazioni apportate al profilo della baseline e di applicarle alla nuova versione che si è scelto di usare.
   - **Accept baseline changes and discard existing setting customizations** (Accetta le modifiche della baseline e ignora le personalizzazioni delle impostazioni esistenti) - Questa opzione sovrascrive completamente il profilo originale. Il profilo aggiornato userà i valori predefiniti per tutte le impostazioni.  

6. Selezionare **Invia**. Il profilo viene aggiornato alla versione della baseline selezionata e al termine della conversione la baseline viene ridistribuita immediatamente ai gruppi assegnati.

## <a name="remove-a-security-baseline-assignment"></a>Rimuovere un'assegnazione della baseline di sicurezza
Quando un'impostazione della baseline di sicurezza non è più applicabile a un dispositivo oppure le impostazioni in una baseline vengono impostate su *Non configurato*, per queste impostazioni in un dispositivo non viene ripristinata una configurazione gestita in precedenza. Le impostazioni precedentemente gestite nel dispositivo mantengono invece le ultime configurazioni ricevute dalla baseline fino a quando un altro processo non aggiorna tali impostazioni nel dispositivo.  

Altri processi che potrebbero modificare le impostazioni nel dispositivo in un secondo momento includono l'aggiunta o la modifica di una baseline della sicurezza, un profilo di configurazione del dispositivo, configurazioni di Criteri di gruppo o la modifica manuale dell'impostazione nel dispositivo.  





## <a name="q--a"></a>Domande e risposte

#### <a name="why-these-settings"></a>Perché queste impostazioni?

Per la creazione di queste raccomandazioni, il team di sicurezza di Microsoft può contare su anni di esperienza di collaborazione diretta con gli sviluppatori di Windows e la community sulla sicurezza. Le impostazioni in questa baseline sono considerate le opzioni di configurazione correlate alla sicurezza più rilevanti. In ogni nuova build di Windows, il team adatta le raccomandazioni alle nuove funzionalità rilasciate.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Esiste una differenza nelle raccomandazioni per le baseline di sicurezza di Windows per Criteri di gruppo rispetto a quelle per Intune?

La scelta e l'organizzazione delle impostazioni per ogni baseline sono state decise dal team di sicurezza Microsoft. Intune include tutte le impostazioni pertinenti nella baseline di sicurezza di Intune. Esistono alcune impostazioni nella baseline per Criteri di gruppo specifiche di un controller di dominio locale. Queste impostazioni vengono escluse dalle raccomandazioni di Intune. Tutte le altre impostazioni sono uguali.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Le baseline di sicurezza di Intune sono conformi a CIS o NSIT?

In senso stretto, no. Il team di sicurezza di Microsoft si consulta con varie organizzazioni, come CIS, per definire le raccomandazioni. Tuttavia, la definizione "conforme a CIS" non è ufficialmente applicabile alle baseline Microsoft.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Di quali certificazioni dispongono le baseline di sicurezza Microsoft? 

- Microsoft continua a pubblicare baseline di sicurezza per Criteri di gruppo (GPO) e [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), come ha fatto per molti anni. Queste baseline sono usate da molte organizzazioni. Le raccomandazioni incluse nelle baseline derivano dalla collaborazione del team di sicurezza Microsoft con clienti aziendali e agenzie esterne, tra le quali il Dipartimento della difesa (DoD, Department of Defense), NIST (National Institute of Standards e Technology) e altri. Microsoft condivide sia le raccomandazioni che le baseline con queste organizzazioni. Anche queste organizzazioni pubblicano raccomandazioni proprie, molto vicine a quelle di Microsoft. In concomitanza con la continua crescita delle soluzioni di gestione dei dispositivi mobili (MDM) nel cloud, Microsoft ha creato raccomandazioni MDM equivalenti per queste baseline di Criteri di gruppo. Queste baseline aggiuntive sono integrate in Microsoft Intune e includono report di conformità per utenti, gruppi e dispositivi che seguono (o non seguono) la baseline.

- Molti clienti usano le raccomandazioni delle baseline di Intune come punto di partenza e quindi le personalizzano in base alle esigenze specifiche per IT e sicurezza. La **baseline di sicurezza MDM** per Windows 10 RS5 di Microsoft è la prima baseline rilasciata. Questa baseline è realizzata come infrastruttura generica che consente ai clienti di importare altre baseline di sicurezza basate su CIS, NIST e altri standard. Attualmente, è disponibile per Windows ed è previsto che includerà anche iOS e Android.

- La migrazione da Criteri di gruppo Active Directory locali a una soluzione cloud pura usando Azure Active Directory (AD) con Microsoft Intune è un viaggio. Per semplificare, sono disponibili modelli di Criteri di gruppo inclusi in [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) che possono agevolare la gestione di dispositivi AD ibridi o aggiunti ad Azure AD. Questi dispositivi possono ottenere le impostazioni MDM dal cloud (Intune) e le impostazioni di Criteri di gruppo dal controller di dominio locale, in base alle esigenze.

## <a name="next-steps"></a>Passaggi successivi
- Visualizzare le impostazioni nelle versioni più recenti delle baseline disponibili:  
  - [Baseline di sicurezza MDM](security-baseline-settings-mdm.md)  
  - [Baseline di Windows Defender ATP](security-baseline-settings-defender-atp.md)  

- Controllare lo stato e monitorare la [baseline e il profilo](security-baselines-monitor.md).
