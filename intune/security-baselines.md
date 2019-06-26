---
title: Usare le baseline di sicurezza in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o configurare le impostazioni di sicurezza di gruppo consigliate per proteggere utenti e dati nei dispositivi con Microsoft Intune per la gestione dei dispositivi mobili. Abilitare BitLocker, configurare Microsoft Defender Advanced Threat Protection, controllare Internet Explorer, usare SmartScreen, impostare criteri di sicurezza locali, richiedere una password, bloccare i download da Internet e altro ancora.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb1ddcadcac1ec9b4730a5dcd66abca111d80196
ms.sourcegitcommit: 14f4e97de5699394684939e6f681062b5d4c1671
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67251213"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Creare una baseline di sicurezza di Windows 10 in Intune

Le baseline di sicurezza sono una funzionalità in anteprima disponibile per i dispositivi che eseguono Windows 10 e versioni successive. Questa funzione include molte impostazioni supportate da Intune per la protezione e la sicurezza di utenti e dispositivi. Consente anche di configurare automaticamente queste impostazioni con i valori consigliati dai team responsabili della sicurezza. Ad esempio, la baseline abilita automaticamente BitLocker, richiede automaticamente una password per sbloccare un dispositivo, disabilita automaticamente l'autenticazione di base e altro ancora.

Questa funzionalità si applica a:

- Windows 10 versione 1809 e successive

> [!NOTE]
> Mentre le baseline di sicurezza sono in anteprima, Microsoft sconsiglia l'uso dei profili in un ambiente di produzione, perché le baseline potrebbero subire modifiche nel corso della fase di anteprima. Quando le baseline di sicurezza sono disponibili a livello generale, i profili esistenti non vengono convertiti nei profili di sicurezza più recenti.

L'obiettivo dell'uso delle baseline di sicurezza è fornire un flusso di lavoro end-to-end sicuro quando si lavora con Microsoft 365. Alcuni dei vantaggi sono i seguenti:

- Una baseline di sicurezza include le procedure consigliate e le raccomandazioni per le impostazioni con effetti sulla sicurezza. Partner di Intune con lo stesso team di sicurezza per Windows che crea le baseline di sicurezza di Criteri di gruppo. Queste raccomandazioni si basano su linee guida e una vasta esperienza.
- Se si ha familiarità con Intune e non si sa da dove iniziare, le baseline di sicurezza rappresentano un vantaggio. È possibile creare e distribuire rapidamente un profilo sicuro, sapendo che si sta contribuendo alla protezione delle risorse e dei dati dell'organizzazione.
- Se si usano Criteri di gruppo, la migrazione a Intune per la gestione è molto più semplice con queste baseline. Queste baseline sono incluse in modo nativo in Intune e includono un'esperienza di gestione moderna.

Le baseline di sicurezza creano un "profilo di configurazione" in Intune. Questo profilo include tutte le impostazioni nella baseline. È quindi possibile applicare o assegnare il profilo a utenti, gruppi e dispositivi.

Dopo aver assegnato il profilo, è possibile monitorare sia il profilo che la baseline. Ad esempio, è possibile visualizzare i dispositivi che corrispondono o meno alla baseline.

Questo articolo è un valido aiuto per usare le baseline di sicurezza per creare, assegnare e monitorare il profilo.

[Baseline della sicurezza di Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) è un'ottima risorsa per scoprire di più su questa funzionalità. [Mobile device management](https://docs.microsoft.com/windows/client-management/mdm/) (Gestione di dispositivi mobili) è una valida fonte di informazioni su MDM e sulle funzionalità disponibili per i dispositivi Windows.

## <a name="available-security-baselines"></a>Baseline di sicurezza disponibili  

Sono disponibili le baseline di sicurezza seguenti da usare con Intune.
- **Anteprima: Baseline della sicurezza MDM per ottobre 2018**  
  [Visualizzare le impostazioni](security-baseline-settings-windows.md)

- **ANTEPRIMA: Baseline di Windows Defender ATP**  
  [Visualizzare le impostazioni](security-baseline-settings-defender-atp.md)  
  *Questa baseline è disponibile quando l'ambiente soddisfa i prerequisiti per l'uso di [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites)* .


## <a name="prerequisites"></a>Prerequisiti
Per gestire le baseline in Intune, l'account deve avere il ruolo predefinito [Gestione profili e criteri](role-based-access-control.md#built-in-roles).


## <a name="co-managed-devices"></a>Dispositivi con co-gestione

Le baseline di sicurezza nei dispositivi gestiti da Intune sono paragonabili ai dispositivi con co-gestione con Configuration Manager. I dispositivi con co-gestione usano System Center Configuration Manager e Microsoft Intune per gestire contemporaneamente i dispositivi Windows 10. Questa funzionalità consente di collegare gli investimenti esistenti per Configuration Manager ai vantaggi di Intune tramite il cloud. La [panoramica della co-gestione](https://docs.microsoft.com/sccm/comanage/overview) è un'ottima risorsa se si usa Configuration Manager e si vogliono sfruttare anche i vantaggi del cloud.

Quando si usano dispositivi con co-gestione, è necessario trasferire il carico di lavoro **Configurazione del dispositivo** (le relative impostazioni) in Intune. In [Co-management workloads](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) (Carichi di lavoro di co-gestione) sono disponibili altre informazioni.

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e quindi selezionare **Sicurezza dei dispositivi** > **Baseline di sicurezza (anteprima)** . È disponibile un elenco delle baseline disponibili. 

    ![Selezionare una baseline di sicurezza da configurare](./media/security-baselines/available-baselines.png)

   >[!TIP]  
   > Questa baseline è disponibile quando l'ambiente soddisfa i prerequisiti per l'uso di [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites).
2. Selezionare la baseline che si vuole usare e quindi selezionare **Crea profilo**.  

3. Nella scheda **Informazioni di base** specificare le proprietà seguenti:

    - **Nome**: immettere un nome per il profilo della baseline di sicurezza. Ad esempio, immettere *Profilo standard per Defender ATP*
    - **Description**: immettere un testo che descriva gli scopi di questa baseline. Nella descrizione è possibile immettere il testo preferito. È facoltativa, ma decisamente consigliata.

4. Selezionare la scheda **Configurazione** per visualizzare i gruppi di **Impostazioni** disponibili in questa baseline. Selezionare un gruppo per espanderlo e visualizzare le singole impostazioni che contiene. Le impostazioni hanno configurazioni predefinite per la baseline di sicurezza. Riconfigurare le impostazioni predefinite in base alle specifiche esigenze aziendali.  

    ![Espandere un gruppo per visualizzare le impostazioni per tale gruppo](./media/security-baselines/sample-list-of-settings.png)

5. Selezionare la scheda **Assegnazioni** per assegnare la baseline ai gruppi. Assegnare la baseline a un gruppo esistente oppure creare un nuovo gruppo usando la procedura standard nella console di Intune per completare la configurazione.  

   ![Assegnare un profilo](./media/security-baselines/assignments.png)
  
6. Quando si è pronti per distribuire la baseline, selezionare la scheda **Rivedi e crea** per esaminare i dettagli per la baseline. Selezionare quindi **Salva profilo** per salvare e distribuire il profilo. 

   ![Rivedere la baseline](./media/security-baselines/review.png) 

   Dopo il salvataggio viene eseguito il push del profilo nei dispositivi quando vengono rilevati da Intune. Il push può quindi avvenire anche immediatamente.

   > [!TIP]  
   > È possibile salvare un profilo senza prima assegnarlo a gruppi specifici. È possibile modificare il profilo in un secondo momento per aggiungere gruppi. 

7. Dopo aver creato il profilo, è possibile modificarlo passando a **Sicurezza dei dispositivi** > **Baseline di sicurezza**, selezionare la baseline configurata e quindi selezionare **Profili**.  Selezionare il profilo e quindi selezionare **Proprietà** per modificare le impostazioni e selezionare **Assegnazioni** per modificare i gruppi che ricevono questa baseline. 

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
- Vedere le [impostazioni delle baseline di sicurezza di Windows](security-baseline-settings-windows.md) supportate da Intune.  
- Controllare lo stato e monitorare la [baseline e il profilo](security-baselines-monitor.md).
