---
title: 'Esercitazione: Procedura dettagliata per Intune nel portale di Azure'
titleSuffix: Microsoft Intune
description: In questa esercitazione verrà presentato Microsoft Intune per comprendere meglio come eseguire le attività.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 03/28/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c601af8c2b73ac68ec88f45d3684fcfd41f1c87f
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2019
ms.locfileid: "58567589"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Esercitazione: Procedura dettagliata per Microsoft Intune nel portale di Azure

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contiene più di 100 servizi utili in una vasta gamma di scenari e opportunità di cloud computing. Microsoft Intune è uno dei numerosi servizi disponibili in Azure. Intune consente di assicurarsi che i dispositivi, le app e i dati aziendali soddisfino i requisiti di sicurezza dell'azienda. È possibile specificare i requisiti da controllare e ciò che accade se i requisiti non sono soddisfatti. Il [portale di Azure](https://portal.azure.com) è l'area in cui è disponibile il servizio Microsoft Intune. La conoscenza delle funzionalità disponibili in Intune consentirà di eseguire diverse attività di gestione di dispositivi mobili (MDM) e di gestione di applicazioni mobili (MAM).

In questa esercitazione:
> [!div class="checklist"]
> * Verrà presentato Microsoft Intune
> * Verrà configurato il portale di Azure

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti
Prima di configurare Microsoft Intune, esaminare i requisiti seguenti:

   - [Sistemi operativi e browser supportati](supported-devices-browsers.md) 
   - [Requisiti di configurazione di rete e larghezza di banda](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Iscriversi per una versione di valutazione gratuita di Microsoft Intune

È possibile provare Intune gratuitamente per 30 giorni. Se si ha già un account aziendale o dell'istituto di istruzione, **eseguire l'accesso** con tale account e aggiungere Intune alla sottoscrizione. In alternativa, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md) per usare Intune per l'organizzazione.

> [!IMPORTANT]
> Non è possibile combinare un account aziendale o dell'istituto di istruzione dopo essersi iscritti per ottenere un nuovo account.

## <a name="tour-microsoft-intune"></a>Verrà presentato Microsoft Intune

Seguire la procedura seguente per conoscere meglio l'uso di Intune nel portale di Azure. Dopo aver completato l'esercitazione, si avrà una migliore comprensione di alcune delle principali aree di Intune.

1. Aprire un browser e accedere al [portale di Intune](https://aka.ms/intuneportal). Se non si ha familiarità con Intune, usare una sottoscrizione di prova gratuita.

    ![Screenshot del portale di Microsoft Intune](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Quando si apre Intune o un altro servizio in Azure, il servizio viene visualizzato in un riquadro. Alcuni dei primi carichi di lavoro che è possibile usare in Intune includono **Dispositivi**, **App client**, **Utenti** e **Gruppi**. Un carico di lavoro è semplicemente un'area secondaria di un servizio. Quando si seleziona il carico di lavoro, il riquadro viene aperto a pagina intera. Gli altri riquadri scorrono dal lato destro del riquadro quando vengono aperti e si chiudono per visualizzare il riquadro precedente. I riquadri vengono chiamati anche pannelli. 

    Per impostazione predefinita, quando si apre Intune viene visualizzato il riquadro **Panoramica**. Questo riquadro offre uno snapshot visivo generale dell'assegnazione dei dispositivi e dello stato di conformità, nonché dello stato di installazione delle app.

2. Da [Intune](https://aka.ms/intuneportal) selezionare **Registrazione dispositivi** per visualizzare i dettagli sui dispositivi registrati nel tenant di Intune. Se si inizia con un nuovo tenant di Intune, non saranno ancora disponibili dispositivi registrati. 

    ![Screenshot del riquadro di registrazione dei dispositivi](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune consente di gestire i dispositivi e le app del personale, nonché la modalità di accesso ai dati aziendali. Per usare il servizio di gestione di dispositivi mobili (MDM), i dispositivi devono prima essere registrati in Intune. Quando un dispositivo viene registrato, viene rilasciato un certificato MDM, che viene usato per la comunicazione con il servizio Intune. 

    Sono disponibili diversi metodi per registrare i dispositivi del personale in Intune. La scelta del metodo dipende dalla proprietà del dispositivo (personale o aziendale), dal tipo di dispositivo (iOS, Windows, Android) e dai requisiti di gestione (reimpostazioni, affinità, blocco). Tuttavia, prima di abilitare la registrazione dei dispositivi, è necessario impostare l'infrastruttura di Intune. In particolare, per la registrazione del dispositivo è necessario [impostare l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md). Per altre informazioni su come preparare l'ambiente di Intune (tenant), vedere [Configurare Intune](setup-steps.md). Dopo aver preparato il tenant di Intune, è possibile registrare i dispositivi. Per altre informazioni sulla registrazione dei dispositivi, vedere [Che cos'è la registrazione dei dispositivi?](device-enrollment.md)

3. Da [Intune](https://aka.ms/intuneportal) selezionare **Conformità del dispositivo** per visualizzare i dettagli sulla conformità per i dispositivi gestiti da Intune. Verranno visualizzati i dettagli come nell'immagine seguente.

    ![Screenshot del riquadro di conformità del dispositivo](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    I requisiti di conformità sono essenzialmente delle regole, ad esempio la richiesta del PIN di un dispositivo o la richiesta della crittografia del dispositivo. I criteri di conformità dei dispositivi definiscono le regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme. Per usare la conformità dei dispositivi, è necessario avere:
    - Una sottoscrizione di Intune e di Azure Active Directory (Azure AD) Premium
    - Dispositivi che eseguono una piattaforma supportata
    - Dispositivi registrati in Intune
    - Dispositivi registrati per un singolo utente o senza utente primario.
    
    Per altre informazioni, vedere [Introduzione ai criteri di conformità dei dispositivi in Intune](device-compliance-get-started.md).

4. Da [Intune](https://aka.ms/intuneportal) selezionare **Configurazione del dispositivo** per visualizzare i dettagli sui profili di dispositivo in Intune. 

    ![Screenshot del riquadro di configurazione del dispositivo](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune include impostazioni e funzionalità che è possibile abilitare o disabilitare in dispositivi diversi all'interno dell'organizzazione. Queste impostazioni e funzionalità vengono aggiunte ai "profili di configurazione". È possibile creare i profili per diversi dispositivi e diverse piattaforme, tra cui iOS, Android e Windows. Quindi, è possibile usare Intune per applicare il profilo ai dispositivi nell'organizzazione.   

    Per altre informazioni sulla configurazione dei dispositivi, vedere [Applicare le impostazioni delle funzionalità nei dispositivi usando i profili dei dispositivi in Microsoft Intune](device-profiles.md).

5. Da [Intune](https://aka.ms/intuneportal) selezionare **Dispositivi** per visualizzare i dettagli sui dispositivi registrati nel tenant di Intune. Se si inizia con una nuova integrazione di Intune, non saranno ancora disponibili dispositivi registrati. 

    ![Screenshot del riquadro di registrazione dei dispositivi](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)
    
    Il riquadro **Dispositivi** visualizza dettagli sui dispositivi registrati del tenant. È possibile fare clic su **Tutti i dispositivi** per visualizzare un elenco dei dispositivi per il tenant di Intune. 

6. Da [Intune](https://aka.ms/intuneportal) selezionare **App client** per visualizzare lo stato di installazione delle app.

    ![Screenshot del riquadro delle app client](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)
    
    Gli amministratori IT possono usare Microsoft Intune per gestire le app client usate dai dipendenti dell'azienda. Questa funzionalità si aggiunge alla gestione dei dispositivi e alla protezione dei dati. Una delle priorità di un amministratore è fare in modo che gli utenti finali abbiano accesso alle app necessarie per lavorare. In aggiunta, potrebbe essere necessario assegnare e gestire le app su dispositivi non registrati in Intune. Intune offre un'ampia gamma di funzionalità che consente di usare le app necessarie nei dispositivi desiderati. Per altre informazioni sull'aggiunta e l'assegnazione di app, vedere [Aggiungere app in Microsoft Intune](apps-add.md) e [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).

7. Da [Intune](https://aka.ms/intuneportal) selezionare **Accesso condizionale** per visualizzare i dettagli sui criteri di accesso.

    ![Screenshot del riquadro di accesso condizionale](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    L'accesso condizionale fa riferimento ai modi con i quali è possibile controllare i dispositivi e le app che sono autorizzati a connettersi alle risorse aziendali e di posta elettronica. Per informazioni sull'accesso condizionale basato su dispositivi e app e per scenari comuni d'uso dell'accesso condizionale con Intune, vedere [Che cos'è l'accesso condizionale?](conditional-access.md)

8. Da [Intune](https://aka.ms/intuneportal) selezionare **Utenti** per visualizzare i dettagli sugli utenti che sono stati inclusi in Intune. Questi utenti sono il personale dell'azienda. 
 
    ![Screenshot del riquadro Utenti](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    È possibile aggiungere direttamente gli utenti in Intune o sincronizzare gli utenti da Active Directory locale. Una volta aggiunti, gli utenti possono registrare i dispositivi e accedere alle risorse aziendali. È anche possibile concedere agli utenti autorizzazioni aggiuntive per accedere a Intune. Per altre informazioni, vedere [Aggiungere utenti e concedere autorizzazioni amministrative a Intune](users-add.md).

9. Da [Intune](https://aka.ms/intuneportal) selezionare **Gruppi** per visualizzare i dettagli sui gruppi di Azure Active Directory (Azure AD) inclusi in Intune. L'amministratore di Intune usa i gruppi per gestire i dispositivi e gli utenti. 

    ![Screenshot del riquadro Gruppi](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    È possibile configurare i gruppi in base alle esigenze dell'organizzazione. Creare gruppi per organizzare utenti o dispositivi in base alla posizione geografica, reparto o caratteristiche hardware. Usare i gruppi per gestire operazioni su larga scala. Ad esempio, è possibile impostare i criteri per più utenti o distribuire le app a un set di dispositivi. Per altre informazioni sui gruppi, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](groups-add.md).

10. Da [Intune](https://aka.ms/intuneportal) selezionare **Guida e supporto tecnico** per chiedere assistenza. L'amministratore IT può usare l'opzione **Guida e supporto tecnico** per cercare e visualizzare soluzioni e inviare un ticket di supporto online per Intune. 

    ![Screenshot del riquadro Guida e supporto tecnico](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Per creare un ticket di supporto, è necessario che l'account sia assegnato come ruolo di amministratore in Azure Active Directory. I ruoli di amministratore includono **Amministratore di Intune**, **Amministratore globale** e **Amministratore del servizio**. Per altre informazioni, vedere [Come ottenere supporto per Microsoft Intune](get-support.md).

11. Da [Intune](https://aka.ms/intuneportal) selezionare **Stato del tenant** per visualizzare i dettagli sul tenant di Intune.

    ![Screenshot del riquadro Stato del tenant](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    I dettagli sullo stato del tenant includono lo stato del connettore, l'integrità del servizio Intune e le notizie di Intune. Se si verificano problemi con il tenant o con Intune, i dettagli vengono visualizzati nel riquadro **Stato del tenant**. Per altre informazioni, vedere [Pagina Stato del tenant di Intune](tenant-status.md).

12. Da [Intune](https://aka.ms/intuneportal) selezionare **Risoluzione dei problemi** per visualizzare un collegamento ai suggerimenti per la risoluzione dei problemi, alla richiesta di supporto o alla verifica dello stato di Intune. Queste informazioni sono specifiche dell'utente di Intune selezionato.

    ![Screenshot del riquadro Risoluzione dei problemi](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Per altre informazioni sulla risoluzione dei problemi in Intune, vedere [Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti aziendali](help-desk-operators.md).

## <a name="configure-the-azure-portal"></a>Verrà configurato il portale di Azure

Azure consente di personalizzare e configurare la visualizzazione del portale.

### <a name="change-the-sidebar"></a>Modificare la barra laterale

La **barra laterale** sul lato sinistro del portale di Azure contiene un elenco di tutti i servizi di Azure disponibili. Questo elenco completo può essere modificato rispetto alla visualizzazione predefinita in modo da avere una visualizzazione permanente dei servizi più importanti. Nelle informazioni che seguono viene usato Intune come esempio di servizio da aggiungere in cima all'elenco.

![Utente che cerca Microsoft Intune nell'elenco "Altri servizi".](./media/azure-add-intune1.png)

1. Selezionare **Tutti i servizi** nella barra laterale sul lato sinistro della pagina.
2. Cercare **Intune** nella casella del filtro.
3. Selezionare la **stella** per aggiungere Intune alla fine dell'elenco dei servizi preferiti.
4. Passare il puntatore del mouse sul servizio Intune. Selezionare e trascinare Intune mediante i **tre punti verticali** a destra del nome del servizio.

### <a name="change-the-dashboard"></a>Modificare il dashboard

La pagina di destinazione predefinita è il **dashboard**. Usare questa pagina per personalizzare i riquadri in cui visualizzare le informazioni più importanti.

![Immagine del nuovo dashboard generico. Mostra la barra laterale con tutti i servizi a sinistra, quindi il dashboard principale al centro. I pulsanti di modifica del dashboard si trovano nella parte superiore, con i riquadri che consentono di accedere a tutte le risorse, le esercitazioni introduttive, all'integrità dei servizi e ad Azure Marketplace.](./media/azure-default-dashboard.png)

Per modificare il dashboard corrente, selezionare il pulsante **Modifica dashboard**. Se non si vuole modificare il dashboard predefinito, è possibile creare anche un **nuovo dashboard**. Quando si crea un nuovo dashboard, si ottiene un dashboard privato vuoto con la **Raccolta riquadri**, che consente di aggiungere o ridisporre i riquadri. È possibile trovare i riquadri in base alla relativa categoria **Generale**, al **Tipo**, mediante **Ricerca** e tramite un **Gruppo di risorse** o **Tag**.

È anche possibile aggiungere i riquadri direttamente al dashboard usando qualsiasi pulsante con **i puntini di sospensione** e selezionando **Aggiungi al dashboard**.

![Primo piano del percorso Utenti e gruppi > Tutti i gruppi in Intune, con l'opzione "Aggiungi al dashboard" visibile all'estrema destra di un gruppo.](./media/azure-pin-to-dashboard.png)

Questa funzionalità sarà più rilevante dopo aver aggiunto altro contenuto a Intune, ad esempio gruppi e utenti.

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a usare rapidamente Microsoft Intune, eseguire i passaggi dei modelli di avvio rapido di Intune configurando innanzitutto un account di Intune gratuito.

> [!div class="nextstepaction"]
> [Avvio rapido: Provare Microsoft Intune gratuitamente](free-trial-sign-up.md)


