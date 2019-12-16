---
title: Esercitazione - Procedura dettagliata per Intune in Microsoft Endpoint Manager
titleSuffix: Microsoft Intune
description: In questa esercitazione verrà presentato Microsoft Intune nell'interfaccia di amministrazione di Microsoft Endpoint Manager per comprendere meglio come eseguire le attività.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 267f09c3dc16aab10fbe64f0e8662ee6f7c7ffa0
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907992"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>Esercitazione: Procedura dettagliata per Intune in Microsoft Endpoint Manager

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contiene più di 100 servizi utili in una vasta gamma di scenari e opportunità di cloud computing. Microsoft Intune è uno dei numerosi servizi disponibili in Azure. Intune consente di assicurarsi che i dispositivi, le app e i dati aziendali soddisfino i requisiti di sicurezza dell'azienda. È possibile specificare i requisiti da controllare e ciò che accade se i requisiti non sono soddisfatti. L'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) è la posizione in cui è possibile trovare il servizio Microsoft Intune, oltre ad altre impostazioni correlate alla gestione dei dispositivi. La conoscenza delle funzionalità disponibili in Intune consentirà di eseguire diverse attività di gestione di dispositivi mobili (MDM) e di gestione di applicazioni mobili (MAM).

> [!NOTE]
> Microsoft Endpoint Manager è una singola piattaforma integrata per la gestione di tutti gli endpoint. L'interfaccia di amministrazione di Microsoft Endpoint Manager si integra con System Center Configuration Manager e Microsoft Intune.

In questa esercitazione:
> [!div class="checklist"]
> * Presentazione dell'interfaccia di amministrazione di Microsoft Endpoint Manager
> * Personalizzare la visualizzazione dell'interfaccia di amministrazione di Microsoft Endpoint Manager

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti
Prima di configurare Microsoft Intune, esaminare i requisiti seguenti:

- [Sistemi operativi e browser supportati](../supported-devices-browsers.md) 
- [Requisiti di configurazione di rete e larghezza di banda](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Iscriversi per una versione di valutazione gratuita di Microsoft Intune

È possibile provare Intune gratuitamente per 30 giorni. Se si ha già un account aziendale o dell'istituto di istruzione, **eseguire l'accesso** con tale account e aggiungere Intune alla sottoscrizione. In alternativa, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md) per usare Intune per l'organizzazione.

> [!IMPORTANT]
> Non è possibile combinare un account aziendale o dell'istituto di istruzione dopo essersi iscritti per ottenere un nuovo account.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Presentazione di Microsoft Intune nell'interfaccia di amministrazione di Microsoft Endpoint Manager

Per comprendere meglio Intune nell'interfaccia di amministrazione di Microsoft Endpoint Manager, seguire questa procedura. Dopo aver completato l'esercitazione, si avrà una migliore comprensione di alcune delle principali aree di Intune.

1. Aprire un browser e accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Se non si ha familiarità con Intune, usare una sottoscrizione di prova gratuita.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Home page](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Quando si apre Microsoft Endpoint Manager o qualsiasi altro servizio in Azure, il servizio viene visualizzato in un riquadro. Alcuni dei primi carichi di lavoro che verranno probabilmente usati in Intune includono **Dispositivi**, **App**, **Utenti** e **Gruppi**. Un carico di lavoro è semplicemente un'area secondaria di un servizio. Quando si seleziona il carico di lavoro, il riquadro viene aperto a pagina intera. Gli altri riquadri scorrono dal lato destro del riquadro quando vengono aperti e si chiudono per visualizzare il riquadro precedente. 

    Per impostazione predefinita, quando si apre Microsoft Endpoint Manager, verrà visualizzato il riquadro **Home page**. Questo riquadro offre una vista generale dello stato del tenant e dello stato di conformità, nonché altri utili collegamenti correlati.

2. Dal riquadro di spostamento selezionare **Dashboard** per visualizzare i dettagli generali sui dispositivi e sulle app client nel tenant di Intune. Se si inizia con un nuovo tenant di Intune, non saranno ancora disponibili dispositivi registrati. 

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Dashboard](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune consente di gestire i dispositivi e le app del personale, nonché la modalità di accesso ai dati aziendali. Per usare il servizio di gestione di dispositivi mobili (MDM), i dispositivi devono prima essere registrati in Intune. Quando un dispositivo viene registrato, viene rilasciato un certificato MDM, che viene usato per la comunicazione con il servizio Intune. 

    Sono disponibili diversi metodi per registrare i dispositivi del personale in Intune. La scelta del metodo dipende dalla proprietà del dispositivo (personale o aziendale), dal tipo di dispositivo (iOS, Windows, Android) e dai requisiti di gestione (reimpostazioni, affinità, blocco). Tuttavia, prima di abilitare la registrazione dei dispositivi, è necessario impostare l'infrastruttura di Intune. In particolare, per la registrazione del dispositivo è necessario [impostare l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md). Per altre informazioni su come preparare l'ambiente di Intune (tenant), vedere [Configurare Intune](setup-steps.md). Dopo aver preparato il tenant di Intune, è possibile registrare i dispositivi. Per altre informazioni sulla registrazione dei dispositivi, vedere [Che cos'è la registrazione dei dispositivi?](../enrollment/device-enrollment.md)

3. Dal riquadro di spostamento selezionare **Dispositivi** per visualizzare i dettagli sui dispositivi registrati nel tenant di Intune. 

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Dispositivi**.

    Il riquadro **Dispositivi - Panoramica** include diverse schede che consentono di visualizzare un riepilogo degli stati e degli avvisi seguenti:
    - **Stato della registrazione** - Informazioni dettagliate sui dispositivi registrati in Intune in base alla piattaforma e sugli errori di registrazione.
    - **Avvisi per la registrazione** - Altri dettagli sui dispositivi non assegnati in base alla piattaforma. 
    - **Stato di conformità** - Verificare lo stato di conformità in base a dispositivo, criterio, impostazione, minacce e protezione. Questo riquadro offre anche un elenco dei dispositivi senza criteri di conformità.
    - **Stato configurazione** - Verificare lo stato di configurazione dei profili di dispositivo, nonché la distribuzione dei profili. 
    - **Stato dell'aggiornamento software** - Rappresentazione visiva dello stato di distribuzione per tutti i dispositivi e per tutti gli utenti.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Dispositivi](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. Dal riquadro **Dispositivi - Panoramica** selezionare **Criteri di conformità** per visualizzare i dettagli sulla conformità per i dispositivi gestiti da Intune. Verranno visualizzati i dettagli come nell'immagine seguente.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Criteri di conformità](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Conformità del dispositivo**.

    I requisiti di conformità sono essenzialmente delle regole, ad esempio la richiesta del PIN di un dispositivo o la richiesta della crittografia del dispositivo. I criteri di conformità dei dispositivi definiscono le regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme. Per usare la conformità dei dispositivi, è necessario avere:
    - Una sottoscrizione di Intune e di Azure Active Directory (Azure AD) Premium
    - Dispositivi che eseguono una piattaforma supportata
    - Dispositivi registrati in Intune
    - Dispositivi registrati per un singolo utente o senza utente primario.
    
    Per altre informazioni, vedere [Introduzione ai criteri di conformità dei dispositivi in Intune](../protect/device-compliance-get-started.md).

5. Dal riquadro **Dispositivi - Panoramica** selezionare **Accesso condizionale** per visualizzare i dettagli sui criteri di accesso.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Accesso condizionale](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Accesso condizionale**.

    L'accesso condizionale si riferisce ai modi in cui è possibile controllare i dispositivi e le app che sono autorizzati a connettersi alle risorse aziendali e di posta elettronica. Per informazioni sull'accesso condizionale basato su dispositivi e app e per scenari comuni d'uso dell'accesso condizionale con Intune, vedere [Che cos'è l'accesso condizionale?](../protect/conditional-access.md)

6. Dal riquadro di spostamento selezionare **Dispositivi** > **Profili di configurazione** per visualizzare i dettagli sui profili di dispositivo in Intune.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Profili di configurazione](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Configurazione del dispositivo**.

    Intune include impostazioni e funzionalità che è possibile abilitare o disabilitare in dispositivi diversi all'interno dell'organizzazione. Queste impostazioni e funzionalità vengono aggiunte ai "profili di configurazione". È possibile creare i profili per diversi dispositivi e diverse piattaforme, tra cui iOS, Android, macOS e Windows. Quindi, è possibile usare Intune per applicare il profilo ai dispositivi nell'organizzazione.   

    Per altre informazioni sulla configurazione dei dispositivi, vedere [Applicare le impostazioni delle funzionalità nei dispositivi usando i profili dei dispositivi in Microsoft Intune](../configuration/device-profiles.md).

7. Dal riquadro di spostamento selezionare **Dispositivi** > **Tutti i dispositivi** per visualizzare i dettagli relativi ai dispositivi registrati del tenant di Intune. Se si inizia con una nuova integrazione di Intune, non saranno ancora disponibili dispositivi registrati.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Tutti i dispositivi](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    Questo elenco di dispositivi mostra i dettagli chiave sulla conformità, sulla versione del sistema operativo e sulla data dell'ultima sincronizzazione.

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Dispositivi** > **Tutti i dispositivi**.
 
8. Dal riquadro di spostamento selezionare **App** per visualizzare una panoramica dello stato dell'app. Questo riquadro fornisce lo stato di installazione dell'app in base alle schede seguenti:

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **App client**.

    Il riquadro **App - Panoramica** include due schede che consentono di visualizzare un riepilogo degli stati seguenti:
    - **Stato dell'installazione** - Visualizzare i principali errori di installazione per dispositivo oltre alle app con errori di installazione.  
    - **Stato dei criteri di protezione delle app** - Informazioni dettagliate sugli utenti assegnati ai criteri di protezione delle app, oltre che sugli utenti contrassegnati.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - App](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    Gli amministratori IT possono usare Microsoft Intune per gestire le app client usate dai dipendenti dell'azienda. Questa funzionalità si aggiunge alla gestione dei dispositivi e alla protezione dei dati. Una delle priorità di un amministratore è fare in modo che gli utenti finali abbiano accesso alle app necessarie per lavorare. In aggiunta, potrebbe essere necessario assegnare e gestire le app su dispositivi non registrati in Intune. Intune offre un'ampia gamma di funzionalità che consente di usare le app necessarie nei dispositivi desiderati. 

    > [!NOTE]
    > Nel riquadro **App - Panoramica** sono disponibili anche informazioni dettagliate sullo stato del tenant e gli account.

    Per altre informazioni sull'aggiunta e l'assegnazione di app, vedere [Aggiungere app in Microsoft Intune](../apps/apps-add.md) e [Assegnare app ai gruppi con Microsoft Intune](../apps/apps-deploy.md).

9. Dal riquadro **App - Panoramica** selezionare **Tutte le app** per visualizzare un elenco delle app aggiunte a Intune.

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **App client** > **App**.

    È possibile aggiungere un'ampia gamma di tipi di app diversi in base alla piattaforma in Intune. Dopo aver aggiunto un'app è possibile assegnarla a gruppi di utenti. 

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Tutte le app](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    Per altre informazioni, vedere [Aggiungere app a Microsoft Intune](~/apps/apps-add.md). 

10. Dal riquadro di spostamento selezionare **Utenti** per visualizzare i dettagli sugli utenti che sono stati inclusi in Intune. Questi utenti sono il personale dell'azienda.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Utenti](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Utenti**.

    È possibile aggiungere direttamente gli utenti in Intune o sincronizzare gli utenti da Active Directory locale. Una volta aggiunti, gli utenti possono registrare i dispositivi e accedere alle risorse aziendali. È anche possibile concedere agli utenti autorizzazioni aggiuntive per accedere a Intune. Per altre informazioni, vedere [Aggiungere utenti e concedere autorizzazioni amministrative a Intune](users-add.md).

11. Dal riquadro di spostamento selezionare **Gruppi** per visualizzare i dettagli sui gruppi di Azure Active Directory (Azure AD) inclusi in Intune. L'amministratore di Intune usa i gruppi per gestire i dispositivi e gli utenti.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Gruppi](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Gruppi**.

    È possibile configurare i gruppi in base alle esigenze dell'organizzazione. Creare gruppi per organizzare utenti o dispositivi in base alla posizione geografica, reparto o caratteristiche hardware. Usare i gruppi per gestire operazioni su larga scala. Ad esempio, è possibile impostare i criteri per più utenti o distribuire le app a un set di dispositivi. Per altre informazioni sui gruppi, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](../groups-add.md).

12. Dal riquadro di spostamento selezionare **Amministrazione del tenant** per visualizzare i dettagli sul tenant di Intune.

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Stato del tenant**.

    Il riquadro **Amministrazione del tenant - Stato del tenant** include le schede **Dettagli del tenant**, **Stato connettore** e **Dashboard di integrità dei servizi**. Se si verificano problemi con il tenant o con Intune, i dettagli saranno disponibili in questo riquadro. 

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Stato del tenant](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    Per altre informazioni, vedere [Pagina Stato del tenant di Intune](../tenant-status.md).

13. Dal riquadro di spostamento selezionare **Risoluzione dei problemi e supporto tecnico** > **Risoluzione dei problemi** per verificare i dettagli sullo stato di un utente specifico. 

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Risoluzione dei problemi**.

    Nell'elenco a discesa **Assegnazioni** è possibile scegliere di visualizzare le assegnazioni delle app client, dei criteri, degli anelli di aggiornamento e delle restrizioni di registrazione. In questo riquadro sono inoltre disponibili informazioni dettagliate sui dispositivi, sullo stato di protezione delle app e sugli errori di registrazione per un utente specifico.

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Risoluzione dei problemi](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Per altre informazioni sulla risoluzione dei problemi in Intune, vedere [Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti aziendali](../help-desk-operators.md).

14. Dal riquadro di spostamento selezionare **Risoluzione dei problemi e supporto tecnico** > **Guida e supporto tecnico** per richiedere assistenza. 

    > [!TIP]
    > Se Intune è stato usato in precedenza nel portale di Azure, i dettagli precedenti sono disponibili nel portale di Azure accedendo a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionando **Guida e supporto tecnico**.

    L'amministratore IT può usare l'opzione **Guida e supporto tecnico** per cercare e visualizzare soluzioni e inviare un ticket di supporto online per Intune. 

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Guida e supporto tecnico](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    Per creare un ticket di supporto, è necessario che l'account sia assegnato come ruolo di amministratore in Azure Active Directory. I ruoli di amministratore includono **Amministratore di Intune**, **Amministratore globale** e **Amministratore del servizio**. 

    Per altre informazioni, vedere [Come ottenere supporto per Microsoft Intune](../get-support.md).

15. Dal riquadro di spostamento selezionare **Risoluzione dei problemi e supporto tecnico** > **Scenari guidati** per visualizzare gli scenari guidati di Intune disponibili. 

    Uno scenario guidato è costituito da una serie personalizzata di passaggi incentrati su un caso d'uso end-to-end. Gli scenari comuni sono basati sul ruolo svolto da un amministratore, un utente o un dispositivo nell'organizzazione. Questi ruoli richiedono in genere una raccolta di profili, impostazioni, applicazioni e controlli di sicurezza orchestrati con attenzione per offrire livelli ottimali di esperienza utente e sicurezza.

    Se non si ha familiarità con tutti i passaggi e le risorse necessari per implementare uno scenario specifico di Intune, è possibile usare gli scenari guidati come punto di partenza. 

    ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Scenari guidati](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    Per altre informazioni sugli scenari guidati, vedere [Panoramica degli scenari guidati](~/fundamentals/guided-scenarios-overview.md).

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Configurare l'interfaccia di amministrazione di Microsoft Endpoint Manager

Azure consente di personalizzare e configurare la visualizzazione del portale.

### <a name="change-the-dashboard"></a>Modificare il dashboard

Il **dashboard** consente di visualizzare i dettagli generali sui dispositivi e sulle app client nel tenant di Intune. I dashboard offrono un modo per creare una visualizzazione specifica e organizzata nell'interfaccia di amministrazione di Microsoft Endpoint Manager. Usare i dashboard come area di lavoro in cui è possibile avviare rapidamente le attività per le operazioni quotidiane e monitorare le risorse. Creare dashboard personalizzati basati su progetti, attività o ruoli utente, ad esempio. Il centro di amministrazione di Microsoft Endpoint Manager include un dashboard predefinito come punto di partenza. È possibile modificare il dashboard predefinito, creare e personalizzare dashboard aggiuntivi e pubblicare e condividere i dashboard per renderli disponibili per altri utenti. 

   ![Screenshot dell'interfaccia di amministrazione di Microsoft Endpoint Manager - Dashboard](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

Per modificare il dashboard corrente, selezionare **Modifica**. Se non si vuole modificare il dashboard predefinito, è possibile creare anche un **nuovo dashboard**. Quando si crea un nuovo dashboard, si ottiene un dashboard privato vuoto con la **Raccolta riquadri**, che consente di aggiungere o ridisporre i riquadri. È possibile trovare i riquadri in base alla categoria o al tipo di risorsa. È anche possibile cercare riquadri particolari. Selezionare **Dashboard** per selezionare uno degli eventuali dashboard personalizzati esistenti.

### <a name="change-the-portal-settings"></a>Modificare le impostazioni del portale

È possibile personalizzare l'interfaccia di amministrazione di Microsoft Endpoint Manager scegliendo la visualizzazione predefinita, il tema, il periodo di timeout delle credenziali, nonché le impostazioni relative alla lingua e all'area.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a usare rapidamente Microsoft Intune, eseguire i passaggi dei modelli di avvio rapido di Intune configurando innanzitutto un account di Intune gratuito.

> [!div class="nextstepaction"]
> [Avvio rapido: Provare Microsoft Intune gratuitamente](free-trial-sign-up.md)
