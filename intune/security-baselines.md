---
title: Usare le baseline di sicurezza in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o configurare le impostazioni di sicurezza di gruppo consigliate per proteggere utenti e dati nei dispositivi con Microsoft Intune per la gestione dei dispositivi mobili. Abilitare BitLocker, configurare Windows Defender Advanced Threat Protection, controllare Internet Explorer, usare SmartScreen, impostare criteri di sicurezza locali, richiedere una password, bloccare i download da Internet e altro ancora.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d78adf8e7d6d2ce05951171e6248dcc8c389945d
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55070203"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Creare una baseline di sicurezza di Windows 10 in Intune

Le baseline di sicurezza sono una funzionalità in anteprima disponibile per i dispositivi che eseguono Windows 10 e versioni successive. Questa funzionalità include molte impostazioni di Intune per la protezione e la sicurezza di utenti e dispositivi. Consente anche di configurare automaticamente queste impostazioni con i valori consigliati dai team responsabili della sicurezza. Ad esempio, la baseline abilita automaticamente BitLocker, richiede automaticamente una password per sbloccare un dispositivo, disabilita automaticamente l'autenticazione di base e altro ancora.

Questa funzionalità si applica a:

- Windows 10 versione 1809 e successive

> [!NOTE]
> Mentre le baseline di sicurezza sono in anteprima, Microsoft sconsiglia l'uso dei profili in un ambiente di produzione, perché le baseline potrebbero subire modifiche nel corso della fase di anteprima.

L'obiettivo dell'uso delle baseline di sicurezza è fornire un flusso di lavoro end-to-end sicuro quando si lavora con Microsoft 365. Alcuni dei vantaggi sono i seguenti:

- Una baseline di sicurezza include le procedure consigliate e le raccomandazioni per le impostazioni con effetti sulla sicurezza. Partner di Intune con lo stesso team di sicurezza per Windows che crea le baseline di sicurezza di Criteri di gruppo. Queste raccomandazioni si basano su linee guida e una vasta esperienza.
- Se si ha familiarità con Intune e non si sa da dove iniziare, le baseline di sicurezza rappresentano un vantaggio. È possibile creare e distribuire rapidamente un profilo sicuro, sapendo che si sta contribuendo alla protezione delle risorse e dei dati dell'organizzazione.
- Se si usano Criteri di gruppo, la migrazione a Intune per la gestione è molto più semplice con queste baseline. Queste baseline sono incluse in modo nativo in Intune e includono un'esperienza di gestione moderna.

Le baseline di sicurezza creano un "profilo di configurazione" in Intune. Questo profilo include tutte le impostazioni nella baseline. È quindi possibile applicare o assegnare il profilo a utenti, gruppi e dispositivi.

Dopo aver assegnato il profilo, è possibile monitorare sia il profilo che la baseline. Ad esempio, è possibile visualizzare i dispositivi che corrispondono o meno alla baseline.

Questo articolo illustra come usare le baseline di sicurezza per creare, assegnare e monitorare il profilo.

[Baseline della sicurezza di Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) è un'ottima risorsa per scoprire di più su questa funzionalità. [Mobile device management](https://docs.microsoft.com/windows/client-management/mdm/) (Gestione di dispositivi mobili) è una valida fonte di informazioni su MDM e sulle funzionalità disponibili per i dispositivi Windows.

## <a name="co-managed-devices"></a>Dispositivi con co-gestione

Le baseline di sicurezza nei dispositivi gestiti da Intune sono paragonabili ai dispositivi con co-gestione con Configuration Manager. I dispositivi con co-gestione usano System Center Configuration Manager e Microsoft Intune per gestire contemporaneamente i dispositivi Windows 10. Questa funzionalità consente di collegare gli investimenti esistenti per Configuration Manager ai vantaggi di Intune tramite il cloud. La [panoramica della co-gestione](https://docs.microsoft.com/sccm/comanage/overview) è un'ottima risorsa se si usa Configuration Manager e si vogliono sfruttare anche i vantaggi del cloud.

Quando si usano dispositivi con co-gestione, è necessario trasferire il carico di lavoro **Configurazione del dispositivo** (le relative impostazioni) in Intune. In [Co-management workloads](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) (Carichi di lavoro di co-gestione) sono disponibili altre informazioni.

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com/) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Baseline di sicurezza (anteprima)**. È disponibile un elenco delle baseline disponibili. Le nuove baseline aggiunte verranno visualizzate in questo elenco:

    ![Visualizzare un elenco delle baseline di sicurezza attualmente disponibili in Intune](./media/security-baselines/available-baselines.png)

3. Selezionare la baseline che si vuole usare > **Crea profilo**.
4. In **Informazioni di base** immettere le proprietà seguenti:

    - **Nome**: immettere un nome per il profilo della baseline di sicurezza. Immettere ad esempio `pilot Windows 10 MDM baseline - Oct 2018`.
    - **Description**: immettere un testo che descriva gli scopi di questa baseline. Nella descrizione è possibile immettere il testo preferito. È facoltativa, ma decisamente consigliata.

5. Espandere **Impostazioni**. Nell'elenco vengono visualizzate tutte le impostazioni incluse nella baseline di sicurezza e l'azione automatica corrispondente. Le impostazioni e i relativi valori sono quelli consigliati e possono essere modificati.

    ![Espandere l'impostazione per visualizzare tutte le impostazioni in questa baseline di sicurezza in Intune](./media/security-baselines/sample-list-of-settings.png)

    Espandere alcune delle impostazioni per controllare i relativi valori. Ad esempio, espandere **Windows Defender**. Notare alcune delle impostazioni e dei valori corrispondenti:

    ![Vedere alcune delle impostazioni di Windows Defender impostate automaticamente in Intune](./media/security-baselines/expand-windows-defender.png)

6. **Creare** il profilo. 
7. Selezionare **Profili**. Il profilo viene creato e visualizzato nell'elenco, ma non è ancora operativo. È ora necessario assegnare il profilo.

## <a name="assign-the-profile"></a>Assegnare il profilo

Dopo averlo creato, il profilo è pronto per l'assegnazione a utenti, dispositivi e gruppi. Dopo l'assegnazione, il profilo e le relative impostazioni vengono applicati agli utenti, i dispositivi e i gruppi scelti.

1. In Intune selezionare **Baseline di sicurezza** > scegliere una baseline > **Profili**.
2. Selezionare il profilo > **Assegnazioni**.

    ![Scegliere il profilo della baseline di sicurezza in Intune e fare clic su Assegnazioni per distribuire il profilo](./media/security-baselines/assignments.png)

3. Nella scheda **Includi**, aggiungere i gruppi, gli utenti o i dispositivi a cui si vogliono applicare i criteri.

    > [!TIP]
    > Si noti che è anche possibile **escludere** gruppi. Se si applicano i criteri a **Tutti gli utenti**, valutare la possibilità di escludere i gruppi di amministratori. In caso di problemi, è meglio evitare che gli amministratori rimangano bloccati.

4. **Salvare** le modifiche.

Dopo il salvataggio viene eseguito il push del profilo nei dispositivi quando vengono rilevati da Intune. Il push può quindi avvenire anche immediatamente.

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

- La migrazione da Criteri di gruppo Active Directory locali a una soluzione cloud pura usando Azure Active Directory (AD) con Microsoft Intune è un viaggio. Per semplificare il processo, esistono oggetti Criteri di gruppo complementari per dispositivi aggiunti ad Active Directory ibrido e ad Azure AD. Questi dispositivi possono ottenere le impostazioni MDM dal cloud (Intune) e le impostazioni di Criteri di gruppo dal controller di dominio locale, in base alle esigenze.

## <a name="next-steps"></a>Passaggi successivi

Controllare lo stato e monitorare la [baseline e il profilo](security-baselines-monitor.md).
