---
title: Controllare l'esito positivo o negativo delle baseline di sicurezza in Microsoft Intune - Azure | Microsoft Docs
description: Controllare lo stato di errore, conflitto ed esito positivo quando si distribuiscono baseline di sicurezza a utenti e dispositivi in Microsoft Intune MDM. Informazioni su come risolvere i problemi mediante i log del client e le funzionalità di report in Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a87b54dde9afe9803d71f7cbef62f7c55375f51b
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040648"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Monitorare la baseline di sicurezza e i profili in Microsoft Intune  

Intune offre diverse opzioni per monitorare le baseline di sicurezza. È possibile monitorare il profilo delle baseline di sicurezza che si applica a utenti e dispositivi. È anche possibile monitorare la baseline effettiva e tutti i dispositivi corrispondenti (o non corrispondenti) ai valori consigliati.

Questo articolo illustra entrambe le opzioni di monitoraggio.

In [Baseline di sicurezza in Intune](security-baselines.md) sono disponibili maggiori dettagli sulla funzionalità delle baseline di sicurezza in Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Monitorare la baseline e i dispositivi  

Quando si monitora una baseline, si ottengono informazioni dettagliate sullo stato di sicurezza dei dispositivi in base ai consigli di Microsoft. È possibile visualizzare queste informazioni dettagliate nel riquadro Panoramica della baseline di sicurezza nella console di Intune.  Sono necessarie fino a 24 ore prima che i dati vengano visualizzati dopo che si assegna per la prima volta una baseline. La visualizzazione delle modifiche apportate successivamente può richiedere fino a sei ore.  

Per visualizzare i dati di monitoraggio per la baseline e i dispositivi, accedere al [portale di Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Selezionare quindi **Sicurezza dei dispositivi** > **Baseline di sicurezza (anteprima)**, selezionare una baseline e visualizzare il riquadro **Panoramica**.

Il riquadro **Panoramica** offre due metodi per monitorare lo stato:
- **Visualizzazione dispositivo**: riepilogo del numero di dispositivi inclusi in ogni categoria di stato per la baseline.  
- **Per categoria**: visualizzazione che mostra ogni categoria nella baseline e include la percentuale di dispositivi per ogni gruppo di stati per ciascuna categoria di baseline. 

Ogni dispositivo è rappresentato da uno degli stati seguenti, usati nelle visualizzazioni *dispositivo* e *per categoria*:  
- **Matches baseline** (Corrisponde alla baseline): tutte le impostazioni nella baseline corrispondono a quelle consigliate.
- **Does not match baseline** (Non corrisponde alla baseline): almeno un'impostazione nella baseline non corrisponde a quelle consigliate.
- **Configurazione non valida**: almeno un'impostazione non è configurata correttamente. Questo stato indica che l'impostazione si trova in uno stato di conflitto, errore o in sospeso.
- **Non applicabile**: almeno un'impostazione non è applicabile e non viene applicata.


### <a name="device-view"></a>Visualizzazione dispositivi
Il riquadro Panoramica mostra un riepilogo basato su grafico del numero di dispositivi che hanno uno stato specifico per la baseline: **Security baseline posture for assigned Windows 10 devices** (Comportamento delle baseline di sicurezza per dispositivi Windows 10 assegnati).  

![Controllare lo stato dei dispositivi](./media/security-baselines-monitor/overview.png)

Quando un dispositivo ha uno stato diverso in base a diverse categorie nella baseline, il dispositivo è rappresentato da un unico stato. Lo stato che rappresenta il dispositivo viene ottenuto dall'ordine di precedenza seguente: **Configurazione non valida**, **Does not match baseline** (Non corrisponde alla baseline), **Non applicabile**, **Matches baseline** (Corrisponde alla baseline).  

Ad esempio, se un dispositivo ha un'impostazione classificata come *Configurazione non valida* e una o più impostazioni classificate come *Does not match baseline* (Non corrisponde alla baseline), il dispositivo è classificato come *Configurazione non valida*.  

È possibile fare clic sul grafico per eseguire il drill-through e visualizzare un elenco di dispositivi con stati diversi. È quindi possibile selezionare singoli dispositivi dall'elenco per visualizzare i dettagli su ogni dispositivo. Ad esempio:
- Selezionare **Configurazione dispositivo** > selezionare il profilo con uno stato di errore:

  ![Controllare lo stato dei dispositivi](./media/security-baselines-monitor/device-configuration-profile-list.png)

- Selezionare il profilo di errore. Viene visualizzato un elenco di tutte le impostazioni nel profilo e il relativo stato. A questo punto è possibile scorrere per individuare l'impostazione che causa l'errore:

  ![Visualizzare l'impostazione che causa l'errore](./media/security-baselines-monitor/profile-with-error-status.png)

Usare queste informazioni di report per individuare le eventuali impostazioni in un profilo che causano un problema. È anche possibile ottenere altri dettagli sui criteri e i profili distribuiti nei dispositivi.

> [!NOTE]
> Quando una proprietà è impostata su **Non configurato** nella baseline, l'impostazione viene ignorata e non vengono applicate restrizioni. La proprietà non viene visualizzata in alcun report.

### <a name="per-category-view"></a>Visualizzazione per categorie
Il riquadro Panoramica mostra un grafico per categorie per la baseline, **Security baseline posture by category** (Comportamento baseline di sicurezza per categoria).  La visualizzazione mostra ogni categoria della baseline e identifica la percentuale di dispositivi che rientrano in una classificazione di stato per ognuna delle categorie. 
 
![Visualizzazione per categoria di stato](./media/security-baselines-monitor/monitor-baseline-per-category.png)

Lo stato per **Matches baseline** (Corrisponde alla baseline) non viene visualizzato finché il 100% dei dispositivi non indica lo stato per la categoria.   

È possibile ordinare la visualizzazione per categoria in base a ogni colonna, facendo clic sull'icona di freccia verso l'alto o verso il basso nella parte superiore della colonna.  


## <a name="monitor-the-profile"></a>Monitorare il profilo

Il monitoraggio del profilo offre informazioni dettagliate sullo stato di distribuzione dei dispositivi, ma non sullo stato di sicurezza basato sulle raccomandazioni della baseline.

1. In Intune selezionare **Baseline di sicurezza** > selezionare una baseline > **Profiles created** (Profili creati).

2. Selezionare un profilo. In **Panoramica** l'immagine mostra il numero di dispositivi e utenti con questo profilo assegnato:

    ![Vedere a quanti dispositivi e utenti è assegnato il profilo delle baseline di sicurezza](./media/security-baselines-monitor/existing-profile-overview.png)

3. In **Gestisci** > **Proprietà** viene visualizzato un elenco di tutte le impostazioni nella baseline. È anche possibile modificare queste impostazioni:

    ![Visualizzare e aggiornare le impostazioni nel profilo delle baseline di sicurezza](./media/security-baselines-monitor/manage-settings.png)

4. In **Monitoraggio** è possibile visualizzare lo stato di distribuzione del profilo in singoli dispositivi, lo stato per ogni utente e lo stato per ogni impostazione nella baseline:

    ![Visualizzare le diverse opzioni di monitoraggio per un profilo di baseline di sicurezza](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>Risolvere i problemi con lo stato per singola impostazione

Si supponga di aver distribuito una baseline di sicurezza, ma che lo stato di distribuzione indichi un errore. La procedura seguente offre alcune indicazioni per la risoluzione dell'errore.

1. In Intune selezionare **Baseline di sicurezza** > selezionare una baseline > **Profiles created** (Profili creati).
2. Selezionare un profilo > in **Monitoraggio** > **Stato per singola impostazione**.
3. La tabella mostra tutte le impostazioni e lo stato di ognuna. Selezionare la colonna **Errore** o la colonna **Conflitto** per visualizzare l'impostazione che causa l'errore.

### <a name="mdm-diagnostic-information"></a>Informazioni di diagnostica MDM

A questo punto è stata individuata l'impostazione problematica. Il passaggio successivo consiste nello scoprire il motivo per cui questa impostazione sta causando un errore o un conflitto. 

Nei dispositivi Windows 10 è disponibile un report di informazioni diagnostiche MDM predefinito. Questo report include i valori predefiniti, i valori correnti, elenca i criteri, mostra se sono distribuiti per il dispositivo o per l'utente e altro ancora. Usare questo report per determinare il motivo per cui l'impostazione sta causando un conflitto o un errore.

1. Nel dispositivo passare a **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**.
2. Selezionare l'account > **Informazioni** > **Advanced Diagnostic Report** > **Create report** (Report di diagnostica avanzato, Crea report).
3. Scegliere **Esporta** e aprire il file generato.
4. Nel report cercare l'impostazione con errore o conflitto nelle diverse sezioni del report.

  Ad esempio, cercare nella sezione **Enrolled configuration sources and target resources** (Origini di configurazione registrate e risorse di destinazione) o nella sezione **Unmanaged policies** (Criteri non gestiti). È possibile farsi un'idea del motivo per cui l'impostazione causa un errore o un conflitto.

In [Diagnose MDM failures in Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) (Diagnosticare gli errori MDM in Windows 10) sono disponibili altre informazioni su questo report predefinito.

> [!TIP]
> - Per alcune impostazioni viene elencato anche il GUID. È possibile cercare questo GUID nel Registro di sistema locale (regedit) per verificare gli eventuali valori impostati.
> - Anche i log di Visualizzatore eventi potrebbero includere alcune informazioni sull'errore dell'impostazione problematica (**Visualizzatore eventi** > **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Amministratore**).

## <a name="next-steps"></a>Passaggi successivi

[Monitorare i profili di dispositivo](device-profile-monitor.md) e [vedere alcuni problemi comuni e relative soluzioni](device-profile-troubleshoot.md).
