---
title: Come ottenere supporto per Microsoft Intune
titleSuffix: Microsoft Intune
description: Ottenere supporto online e per telefono per Microsoft Intune a pagamento e per le sottoscrizioni di prova.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91627a47f9dccfb436e64aaadeeb392648dff821
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585289"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Come ottenere supporto per Microsoft Intune  

[!INCLUDE [azure_portal](../../intune-classic/includes/note-for-both-portals.md)]  
  
Microsoft offre supporto globale tecnico e per la prevendita, la fatturazione e le sottoscrizioni di Microsoft Intune. Il supporto è disponibile sia online che telefonicamente per le sottoscrizioni a pagamento e di valutazione. Il supporto tecnico online è disponibile in inglese e giapponese. Il supporto telefonico e il supporto online per la fatturazione online sono disponibili anche in altre lingue.

L'amministratore di Intune può usare l'opzione **Guida e supporto tecnico** per inviare un ticket di supporto online per Intune dal portale di Azure. Per creare e gestire una richiesta di assistenza, l'account deve avere un ruolo Azure Active Directory (Azure AD) che includa l'*azione* **microsoft.office365.supportTickets/tickets/manage**. Per informazioni sui ruoli e le autorizzazioni di Azure AD necessari per creare un ticket di supporto, vedere [Autorizzazioni del ruolo di amministratore in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).  

>[!IMPORTANT]  
> Per il supporto tecnico dei prodotti di terze parti usati con Intune, come ad esempio Saaswedo, Cisco o Lookout, contattare prima il fornitore del prodotto. Prima di aprire una richiesta di supporto per Intune, verificare che l'altro prodotto sia stato configurato correttamente.
>
> Per informazioni sulla risoluzione dei problemi relativi a Microsoft Intune, vedere la [sezione Risoluzione dei problemi](help-desk-operators.md) della documentazione di Intune.

## <a name="known-issues-for-creating-support-incidents"></a>Problemi noti relativi alla creazione di richieste di assistenza  

Se il proprio account ha le autorizzazioni necessarie ma non riesce ad accedere a Guida e supporto tecnico oppure a creare o gestire una richiesta di assistenza, esaminare i problemi noti seguenti e le relative soluzioni:  
- Token utente non aggiornato per l'account. Per risolvere il problema, disconnettersi da tutte le sessioni di console attive, connettersi di nuovo e quindi provare a creare o a gestire una richiesta di assistenza. 
- Più sessioni attive. Se si è eseguito l'accesso con più di un account utente o si è connessi a più sessioni, disconnettersi da tutte le console tranne una. Quindi, con una sola sessione attiva, provare a creare o a gestire una richiesta di assistenza.

Altre azioni che potrebbero essere necessarie per risolvere problemi di accesso:
- Cancellare tutti i cookie della sessione del browser attiva e quindi riprovare a creare o a gestire una richiesta di assistenza.
- Usare una sessione InPrivate Browsing per accedere a Intune e provare a creare o a gestire una richiesta di assistenza.  

Se queste soluzioni alternative non risolvono il problema, passare all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) e creare lì un ticket di supporto. Una soluzione a questo problema sarà disponibile a fine estate.  

## <a name="help-and-support-experience"></a>Esperienza di Guida e supporto tecnico  

L’esperienza di Guida e supporto tecnico per Intune è disponibile nel [portale Gestione dispositivi di Microsoft 365](https://devicemanagement.microsoft.com) e in tutti i pannelli o tutte le pagine di Intune nel portale di Azure. 

![Pannelli di Intune](./media/get-support/intune-blades.png)


L'esperienza *Guida e supporto tecnico* è simile a quella offerta dall'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/) e sostituisce l'opzione *Guida e supporto* precedente che rimane disponibile per altri servizi in Azure. 

Per accedere a Guida e supporto tecnico, usare le opzioni seguenti:  
- **Dashboard Gestione dispositivi:**
  - Dopo aver selezionato un'area funzionale per Intune, selezionare l'opzione **Guida e supporto tecnico**.
  - Da qualsiasi nodo nel portale Gestione dispositivi selezionare l'icona **?** nell'angolo superiore destro del portale e quindi usare l'elenco a discesa per selezionare il servizio per il quale si vuole ottenere assistenza. L'icona **?** nel portale Gestione dispositivi supporta più servizi ed è necessario selezionare il servizio specifico per il quale si vuole ottenere assistenza.  

    ![Selezionare il servizio](./media/get-support/select-a-service.png)

    Dopo aver selezionato un servizio, verrà visualizzata la relativa pagina *Guida e supporto tecnico* in cui sarà possibile [specificare i dettagli](#specify-details-about-an-issue) del problema specifico per il quale si vuole assistenza.  

    Se i risultati della ricerca non sembrano soddisfare le aspettative per il servizio, verificare di aver selezionato il servizio corretto. Il servizio selezionato è visualizzato sotto *Guida e supporto tecnico*.  Se non è stato selezionato il servizio corretto, fare clic su *Seleziona un servizio* per tornare all'elenco a discesa di selezione dei servizi.   

    ![Confermare il servizio](./media/get-support/confirm-your-service-selection.png) 


- **Nel portale di Azure:**
  - Selezionare **Guida e supporto tecnico** in qualsiasi pannello o pagina di Intune

  Nel portale di Azure se si seleziona l'icona **?** nell'angolo superiore destro oppure **Guida e supporto** nel riquadro di spostamento a sinistra, viene aperto *Guida e supporto* per Azure. Da *Guida e supporto* di Azure non è possibile aprire direttamente una richiesta di assistenza per Intune, ma è possibile raggiungere la pagina *Guida e supporto tecnico* di Intune seguendo questa procedura: 
  1. Selezionare Nuova richiesta di supporto.
  2. Per Tipo di problema, specificare Tecnico.
  3. Per Servizio, specificare Microsoft Intune.
  4. Selezionare il collegamento alla pagina Guida e supporto tecnico di Intune.

> [!NOTE]  
> Se l'istanza di Intune è ospitata nel cloud privato per entità pubbliche, noto anche come cloud sovrano quale ad esempio Azure per enti pubblici, vedere [Supporto di Intune per il cloud privato per enti pubblici](#intune-support-for-private-cloud-for-government) più avanti in questo articolo. L'esperienza *Guida e supporto tecnico* di Intune sarà disponibile in nel cloud privato per enti pubblici più avanti nel corso di quest'anno. 


Quando si apre *Guida e supporto tecnico*, la vista offerta dal portale dipende dalla presenza o meno di richieste di assistenza attive e, se si ha il supporto tecnico Premier, essa includerà opzioni ed elementi aggiuntivi:
- **Nessuna richiesta di assistenza attiva**: viene visualizzata la pagina **Serve aiuto?** come illustrato nell'immagine seguente relativa alla dashboard Gestione dispositivi.  
- **Richieste di assistenza attive**: viene visualizzata la pagina [Ticket di supporto](#view-support-cases) con l'elenco delle richieste di assistenza attive.  
- **Contratto di supporto tecnico Premier**: l'esperienza è identica a quella delle prime due opzioni, ma nella pagina Serve aiuto? verranno visualizzati gli elementi aggiuntivi seguenti: 
  - Dopo il titolo della pagina **Serve aiuto?** viene visualizzato il banner del supporto tecnico Premier:  
    ![Banner del supporto tecnico Premier](./media/get-support/premier-banner.png)
  - Nella sezione **Ottieni supporto** della pagina è possibile impostare il livello di **gravità** iniziale quando si crea una richiesta di assistenza tramite telefono.


![Dashboard Gestione dispositivi e pagina Serve aiuto?](./media/get-support/help-support-dashboard.png)

In questa visualizzazione è possibile eseguire le operazioni seguenti:

1. [Specificare i dettagli](#specify-details-about-an-issue) relativi al problema specifico per cui si ha bisogno di assistenza  
2. [Visualizzare la Guida sensibile al contesto](#view-context-sensitive-help) e le relative soluzioni basate sui dettagli specificati  
3. [Ricevere assistenza](#get-support) usando la posta elettronica o il telefono  
4. [Visualizzare le richieste di supporto](#view-support-cases) aperte in precedenza usando questo nuovo flusso di lavoro  

### <a name="specify-details-about-an-issue"></a>Specificare i dettagli riguardo a un problema 

Se si accede a Guida e supporto tecnico da una posizione supportata dalla nuova esperienza, si apre la pagina **Serve assistenza?** che consente di specificare i dettagli relativi a un problema. Quando si immettono i dettagli, la console offre alcune query comuni basate sulle parole chiave usate dall'utente. Selezionare un'opzione tra quelle offerte o completare la propria descrizione del problema. Se si immette una descrizione, selezionare **Richiesta supporto** per inviarla. Dopo l'invio di una query, la console restituisce informazioni sensibili al contesto che possono essere utili per risolvere il problema.

Di seguito sono riportati esempi di query che si potrebbero inviare:
  
- *Non è possibile ripristinare il dispositivo iOS*  
- *Impossibile creare criteri di accesso condizionale*  

![Specificare il problema nella pagina Serve assistenza?](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Visualizzare la guida sensibile al contesto 

Dopo aver selezionato una delle opzioni offerte o inviato una query, i risultati sensibili al contesto appaiono in **Visualizza soluzioni**. Questi risultati includono sia materiale sussidiario self-help specifico di Intune, sia altri risultati restituiti da una ricerca sul Web eseguita in base ai criteri di query.  
![Visualizzazione risultati](./media/get-support/view-results.png)

### <a name="get-support"></a>Ottenere supporto 

Se il supporto Self-help o le indicazioni basate sul Web non consentono di risolvere il problema, usare la console per aprire una richiesta di assistenza via posta elettronica o telefono.  
Selezionare l'opzione che si vuole usare nella pagina **Serve assistenza?** .  

  > [!NOTE] 
  > Le richieste di supporto via posta elettronica non sono disponibili per tutti i tenant.  

- Nel caso di una richiesta via posta elettronica, indicare il proprio indirizzo di posta elettronica e, se necessario, aggiungere allegati alle informazioni inviate. Selezionare **Invia** per aprire la richiesta. 

  ![Richiesta via posta elettronica](./media/get-support/email-support.png)
  
- Per una richiesta telefonica, specificare il proprio numero di telefono. Facoltativamente, è possibile includere il proprio indirizzo di posta elettronica e aggiungere allegati per l'invio. Selezionare Chiama per inviare la richiesta.  



   ![Richiesta via telefono](./media/get-support/phone-support.png)

**Supporto tecnico Premier**:  
Con un contratto di supporto tecnico Premier sono disponibili le stesse opzioni per creare una richiesta di assistenza telefonica. È anche possibile specificare il livello di **gravità** per la richiamata del supporto e scegliere di creare il ticket di supporto in base al proprio contratto Mission Critical.  

![Opzioni di supporto tecnico Premier](./media/get-support/premier-phone-support-options.png)


### <a name="view-support-cases"></a>Visualizzare le richieste di supporto  

Selezionare il pulsante della cronologia per visualizzare le richieste di supporto create.  

![Visualizzare le richieste di supporto](./media/get-support/view-support-tickets.png)

- Solo le richieste di supporto aperte usando il nuovo flusso di lavoro sono visibili dall'interno di questo flusso di lavoro. Per visualizzarle, usare una visualizzazione di Guida e supporto tecnico dalla console di gestione dei dispositivi o da un pannello di Intune nel portale di Azure. Le richieste hanno numeri di otto cifre. È possibile visualizzarle anche dall'interfaccia di amministrazione di Microsoft 365.  

- I casi aperti non utilizzando l’esperienza Guida e supporto tecnico di Intune rimangono invariati. Per visualizzarli, è necessario usare una visualizzazione di Guida e supporto tecnico che non fa parte dell'esperienza di Intune oppure usare il dashboard Gestione dispositivi. Queste richieste hanno numeri di 15 cifre che iniziano con **117** o **118**. A tale scopo:

    1. Accedere a Azure (<https://portal.azure.com>) con le credenziali di amministratore di Intune, scegliere l'icona *?* nell'angolo superiore destro del portale e scegliere *Guida e supporto* per visualizzare la pagina [Guida e supporto](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) di Azure.

    2. Nella pagina **Guida e supporto** è possibile visualizzare l'elenco delle **Richieste di supporto recenti** e selezionarle per visualizzare altri dettagli.
 

## <a name="azure-help--support-experience"></a>Esperienza di Guida e supporto tecnico di Azure 

Quando si usa **Guida e supporto** nel riquadro di spostamento a sinistra oppure l'opzione **?** nell'angolo superiore destro del portale di Azure, viene aperta l'esperienza Guida e supporto di Azure, ovvero un'esperienza diversa da quella offerta da Guida e supporto tecnico di Intune.  

Dal mese di aprile 2019 non è possibile accedere all'esperienza *Guida e supporto* di Azure per ottenere assistenza per Intune, a meno che la sottoscrizione non faccia parte di un cloud privato per enti pubblici.  

Se l'istanza di Intune non è eseguita in un cloud privato per enti pubblici, l'esplorazione di *Guida e supporto* di Azure determina il reindirizzamento dell'utente all'esperienza *Guida e supporto tecnico* di Intune per creare e gestire le richieste di assistenza.  


## <a name="intune-support-for-private-cloud-for-government"></a>Supporto di Intune per il cloud privato per enti pubblici  

Per le sottoscrizioni di Intune ospitate nel cloud privato per entità pubbliche, noto anche come cloud sovrano quale ad esempio Azure per enti pubblici, la nuova esperienza Guida e supporto tecnico di Intune non è ancora disponibile.  Per ottenere supporto per Intune usare le informazioni indicate di seguito. 


### <a name="create-an-online-support-ticket"></a>Creare un ticket di supporto online 

>[!IMPORTANT]    
> Durante la transizione di *Guida e supporto tecnico* a un nuovo sistema che non è ancora disponibile per il cloud privato per enti pubblici, quando viene creata una richiesta di assistenza, il portale identifica un caso di supporto che usa un codice identificativo di 15 cifre. Alla creazione del caso a 15 cifre, viene creato un caso speculare che sarà usato dal supporto tecnico Microsoft. Questo caso speculare viene creato in un nuovo sistema di supporto, usa un ID a 8 cifre e viene usato dai servizi di supporto tecnico per tenere traccia di tutte le attività e le comunicazioni relative alla richiesta di assistenza. Subito dopo la creazione del caso a 15 cifre, si riceverà un messaggio di posta elettronica che identifica il codice a 8 cifre del caso di supporto speculare usato dai servizi di supporto tecnico.  
> 
> Il personale del supporto lavora e comunica dal caso di supporto a 8 cifre e usa esclusivamente questo caso di supporto per registrare le comunicazioni e monitorare lo stato della richiesta di assistenza. Gli aggiornamenti tramite posta elettronica verranno pertanto inviati all'utente dal caso di supporto a 8 cifre che funge da riepilogo delle attività svolte. Nessun dettaglio viene registrato nella richiesta di assistenza a 15 cifre. Al termine dell'intervento di supporto, quando il caso a 8 cifre viene chiuso, lo stato viene riportato nel caso di supporto a 15 cifre che è possibile visualizzare dall'interno del portale di Azure.  Per il caso di supporto a 15 cifre non ci saranno altri aggiornamenti o modifiche di stato.  
> 
> Al termine della transizione degli strumenti di supporto, più avanti nel corso dell'anno, l'esperienza di supporto che Intune ospitava nel cloud per enti pubblici sarà simile all'esperienza *Guida e supporto tecnico* predefinita attualmente disponibile per le sottoscrizioni di Intune ospitate nel cloud pubblico.  


1. Accedere al portale di Azure (<https://portal.azure.com>) con le credenziali di amministratore di Intune, scegliere l'icona **?** nell'angolo superiore destro del portale e scegliere **Guida e supporto** per visualizzare la pagina [Guida e supporto](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) di Azure.

   ![Immagine del collegamento a forma di punto interrogativo con il collegamento Guida e supporto evidenziato](./media/get-support/azure-get-support.png)

2. Nella pagina **Guida e supporto** di Azure selezionare **Nuova richiesta di supporto**.

   ![Immagine del collegamento Nuova richiesta di supporto evidenziato nella pagina Guida e supporto](./media/get-support/azure-support-ticket-link.png)

3. Nella scheda **Informazioni di base**, per la maggior parte dei problemi di supporto tecnico di Intune, scegliere le opzioni seguenti:
   - **Tipo di problema**: **Tecnico**
   - **Sottoscrizione**: <*nome della sottoscrizione*>
   - **Servizio**: **Microsoft Intune**
   - **Tipo di problema**: scegliere il tipo di problema dal menu a discesa.
   - **Sottotipo del problema**: scegliere il sottotipo del problema dal menu a discesa.
   - **Oggetto**: descrivere brevemente il problema per il quale serve assistenza.

   ![Immagine della scheda relativa alle informazioni di base nella pagina Guida e supporto - Nuova richiesta di supporto](./media/get-support/help-new-support-case-basics.png)

   Scegliere **Avanti: Soluzioni** per continuare.
4. Nella scheda **Soluzioni** esaminare le procedure consigliate che possono essere utili per risolvere il problema senza inviare un ticket. Se dopo aver esaminato le procedure si vuole comunque creare una richiesta di supporto, fare clic su **Avanti: Dettagli**.

   ![Immagine della scheda relativa alle soluzioni nella pagina Guida e supporto - Nuova richiesta di supporto](./media/get-support/help-new-support-case-solutions.png)
5. Nella scheda **Dettagli** immettere i dettagli per il problema, il metodo di supporto, le informazioni di contatto e quindi fare clic su **Avanti: Rivedi e crea**.

   ![Immagine della scheda relativa ai dettagli nella pagina Guida e supporto - Nuova richiesta di supporto](./media/get-support/help-new-support-case-details.png)
6. Rivedere le informazioni, verificare che siano corrette e quindi scegliere **Crea** per inviare la richiesta di supporto.

   ![Immagine della scheda Rivedi e crea nella pagina Guida e supporto - Nuova richiesta di supporto](./media/get-support/help-new-support-case-create.png)

>[!IMPORTANT]
>Per domande su fatturazione o abbonamento, è possibile aprire un caso per ottenere assistenza tramite l'[Interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Visualizzare le richieste di supporto  

È possibile visualizzare le richieste di supporto dal portale di Azure. Sono tuttavia disponibili informazioni limitate.  Per visualizzare le richieste di assistenza: 

1. Accedere a Azure (<https://portal.azure.com>) con le credenziali di amministratore di Intune, scegliere l'icona **?** nell'angolo superiore destro del portale e scegliere **Guida e supporto** per visualizzare la pagina [Guida e supporto](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) di Azure.

2. Nella pagina **Guida e supporto** è possibile visualizzare l'elenco **Richieste di supporto recenti**.

   > [!IMPORTANT]  
   > I clienti del cloud privato per enti pubblici possono visualizzare solo il codice a 15 cifre del caso di supporto e lo stato della richiesta di assistenza. Tutte le comunicazioni e le registrazioni di attività o avvisi relative al caso vengono inviate tramite posta elettronica e hanno come riferimento il codice a 8 cifre del caso di supporto creato come caso di supporto speculare di quello aperto dalla console di Intune.   

## <a name="additional-resources"></a>Risorse aggiuntive  

- [Supporto per la fatturazione e la sottoscrizione](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Volume licensing](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Risoluzione dei problemi relativi a Intune](help-desk-operators.md)
