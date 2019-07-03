---
title: Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune
titleSuffix: ''
description: Informazioni su come usare Microsoft Intune per installare le app di Office 365 nei dispositivi Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 095c2ee0aba0680de0c5fc55c1406dba41111b92
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67527435"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. Tra i [tipi di app](apps-add.md#app-types-in-microsoft-intune) disponibili ci sono le app di Office 365 per i dispositivi Windows 10. Selezionando questo tipo di app in Intune, è possibile assegnare e installare le app di Office 365 nei dispositivi gestiti che eseguono Windows 10. È anche possibile assegnare e installare app per il client desktop Microsoft Project Online e Microsoft Visio Online piano 2, se si hanno le licenze di questi prodotti. Le app di Office 365 disponibili sono visualizzate come un'unica voce nell'elenco delle app nella console di Intune in Azure.

> [!NOTE]
> È necessario usare le licenze di Office 365 ProPlus per attivare le app di Office 365 ProPlus distribuite tramite Microsoft Intune. Attualmente, Intune non supporta Office 365 Business Edition.

## <a name="before-you-start"></a>Prima di iniziare

> [!IMPORTANT]
> Se sono presenti app di Office con estensione msi nel dispositivo dell'utente finale, è necessario usare la funzionalità di **rimozione dei file MSI** per disinstallare correttamente queste app. In caso contrario, le app di Office 365 distribuite da Intune non verranno installate.

- È necessario che i dispositivi in cui vengono distribuite le app eseguano Windows 10 Creators Update o versioni successive.
- Intune supporta l'aggiunta di app di Office solo dalla suite Office 365.
- Se sono aperte app di Office quando Intune installa la suite di app, è possibile che l'installazione non riesca e che gli utenti perdano i dati dei file non salvati.
- Questo metodo di installazione non è supportato nei dispositivi Windows 10S, Windows Home, Windows Team, Windows Holographic o Windows Holographic for Business.
- Intune non consente di installare le app desktop di Office 365 da Microsoft Store (note come app Office Centennial) in un dispositivo a cui sono già state distribuite app di Office 365 con Intune. Se si installa questa configurazione, si potrebbero verificare perdite o danneggiamenti dei dati.
- Più assegnazioni di app necessarie o disponibili non sono cumulative. Un'assegnazione di app successiva sovrascriverà le assegnazioni di app installate preesistenti. Ad esempio, se il primo set di app di Office contiene Word mentre il successivo set non lo contiene, Word verrà disinstallato. Questa condizione non si applica alle applicazioni di Visio o Project.
- **Versione di Office** - Scegliere se assegnare la versione a 32 bit o a 64 bit di Office. La versione a 32 bit può essere installata in dispositivi a 32 bit e a 64 bit, mentre la versione a 64 bit può essere installata solo in dispositivi a 64 bit.
- **Remove MSI from end-user devices** (Rimuovi MSI dai dispositivi degli utenti finali) - Scegliere se si vogliono rimuovere le app MSI di Office preesistenti dai dispositivi degli utenti finali. L'installazione non riesce se sono già presenti app MSI nei dispositivi degli utenti finali. Le app da disinstallare non sono limitate alle app selezionate per l'installazione in **Configura la suite di app**, in quanto verranno rimosse tutte le app di Office (MSI) dal dispositivo dell'utente finale. Per altre informazioni, vedere [Rimuovere le versioni MSI esistenti di Office durante l'aggiornamento a Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando Intune reinstalla Office nei computer dell'utente finale, i Language Pack saranno gli stessi usati nelle precedenti installazioni di Office MSI.

## <a name="get-started"></a>Operazioni preliminari

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro del carico di lavoro **App client** in **Gestisci** selezionare **App**.
5. Selezionare **Aggiungi**.
6. Nel riquadro **Aggiungi app**, nell'elenco **Tipo di app**, in **Office 365 Suite** selezionare **Windows 10**.

## <a name="select-settings-format"></a>Selezionare il formato delle impostazioni

È possibile scegliere un metodo per la configurazione dell'impostazione delle app selezionando un'opzione per **Formato delle impostazioni**. Le opzioni per il formato delle impostazioni includono:
- Progettazione configurazione
- Immettere i dati XML

Quando si sceglie **Progettazione configurazione**, il pannello **Aggiungi app** cambia per includere due opzioni per le impostazioni aggiuntive:
- Configura la suite di app
- Impostazioni della suite di app

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Quando si sceglie **Immettere i dati XML**, nel pannello **Aggiungi app** viene visualizzata l'opzione **Immettere i dati XML**. Selezionare questa opzione per visualizzare il pannello **File di configurazione**. 

![Aggiungere la finestra di progettazione della configurazione di Office 365](./media/apps-add-office365/apps-add-office365-01.png)
    
Per altre informazioni sull'opzione **Immettere i dati XML**, vedere [Immettere i dati XML](apps-add-office365.md#enter-xml-format) di seguito.

## <a name="configure-app-suite-information"></a>Configurare le informazioni sulla suite di app

In questo passaggio si specificano le informazioni sulla suite di app. Queste informazioni consentono di identificare la suite di app in Intune e semplificano la ricerca della suite di app da parte degli utenti nel portale aziendale.

1. Nel riquadro **Aggiungi app** selezionare **Informazioni sulla suite di app**.
2. Nel riquadro **Informazioni sulla suite di app** seguire questa procedura:
    - **Nome della suite**: immettere il nome della suite di app visualizzato nel portale aziendale. Verificare che tutti i nomi di suite usati siano univoci. Se il nome di una suite viene usato due volte, solo una delle due suite viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione della suite** : immettere una descrizione per la suite di app. Ad esempio, è possibile elencare le app selezionate da includere.
    - **Editore**: come editore viene visualizzato Microsoft.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa impostazione consente agli utenti di trovare più facilmente il gruppo di app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: come sviluppatore viene visualizzato Microsoft.
    - **Proprietario**: come proprietario viene visualizzato Microsoft.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: quando gli utenti visitano il portale aziendale, il logo Office 365 viene visualizzato insieme all'app.
3. Selezionare **OK**.

## <a name="configure-app-suite"></a>Configurare la suite di app

Se è stata selezionata l'opzione **Progettazione configurazione** nella casella di riepilogo a discesa **Formato delle impostazioni**, nel pannello **Aggiungi app** verrà visualizzata l'opzione **Configura la suite di app**. Selezionare le app di Office che si vuole assegnare ai dispositivi.

1. Nel riquadro **Aggiungi app** selezionare **Configura la suite di app**.
2. Nel riquadro **Configura la suite di app** selezionare le app di Office standard da assegnare ai dispositivi.  
    È anche possibile installare app per il client desktop Microsoft Project Online e Microsoft Visio Online piano 2, se si hanno le licenze di questi prodotti.
3. Selezionare **OK**.

## <a name="configure-app-suite-settings"></a>Configurare le impostazioni della suite di app

Se è stata selezionata l'opzione **Progettazione configurazione** nella casella di riepilogo a discesa **Formato delle impostazioni**, nel pannello **Aggiungi app** verrà visualizzata l'opzione **Impostazioni della suite di app**. In questo passaggio configurare le opzioni di installazione per la suite di app. Le impostazioni si applicano a tutte le app aggiunte alla suite.

1. Nel riquadro **Aggiungi app** selezionare **Impostazioni della suite di app**.
2. Nel riquadro **Impostazioni della suite di app** seguire questa procedura:
    - **Versione di Office**: scegliere se assegnare la versione a 32 bit o a 64 bit di Office. La versione a 32 bit può essere installata in dispositivi a 32 bit e a 64 bit, mentre la versione a 64 bit può essere installata solo in dispositivi a 64 bit.
    - **Canale di aggiornamento**: scegliere la modalità di aggiornamento di Office nei dispositivi. Per informazioni sui diversi canali di aggiornamento, vedere [Panoramica dei canali di aggiornamento per Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Scegliere tra:
        - **Monthly** (Mensile)
        - **Monthly (Targeted)** (Mensile - mirato)
        - **Semi-Annual** (Semestrale)
        - **Semi-Annual (Targeted)** (Semestrale - mirato)

        Dopo aver scelto un canale, è possibile selezionare facoltativamente **Specifica** per installare una versione specifica di Office per il canale selezionato nei dispositivi degli utenti finali. Selezionare quindi la **versione specifica** di Office da usare.
        
        Le versioni disponibili cambieranno nel corso del tempo. Quando si crea una nuova distribuzione, le versioni disponibili potrebbero quindi essere più recenti e alcune versioni precedenti potrebbero non essere disponibili. Le distribuzioni correnti continueranno a distribuire la versione precedente, ma l'elenco delle versioni verrà continuamente aggiornato per ogni canale.
        
        I dispositivi che aggiornano la versione aggiunta (o aggiornano qualsiasi altra proprietà) e vengono distribuiti come disponibili, verranno indicati come installati nello stato di report se era installata una versione precedente fino alla connessione del dispositivo. Alla connessione del dispositivo, lo stato cambierà temporaneamente in Sconosciuto, ma non verrà visualizzato all'utente. Quando l'utente avvia l'installazione per la versione più recente disponibile, all'utente verrà visualizzato lo stato modificato Installato.
        
        Per altre informazioni, vedere [Panoramica dei canali di aggiornamento per Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

    - **Remove MSI from end-user devices** (Rimuovi MSI dai dispositivi degli utenti finali) - Scegliere se si vogliono rimuovere le app MSI di Office preesistenti dai dispositivi degli utenti finali. L'installazione non riesce se sono già presenti app MSI nei dispositivi degli utenti finali. Le app da disinstallare non sono limitate alle app selezionate per l'installazione in **Configura la suite di app**, in quanto verranno rimosse tutte le app di Office (MSI) dal dispositivo dell'utente finale. Per altre informazioni, vedere [Rimuovere le versioni MSI esistenti di Office durante l'aggiornamento a Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando Intune reinstalla Office nei computer dell'utente finale, i Language Pack saranno gli stessi usati nelle precedenti installazioni di Office MSI. 
    - **Accetta automaticamente il contratto di licenza con l'utente finale** : selezionare questa opzione se non si richiede agli utenti finali di accettare il contratto di licenza. Intune accetterà automaticamente il contratto.
    - **Usa l'attivazione di computer condivisi**: selezionare questa opzione quando più utenti condividono un computer. Per altre informazioni, vedere [Panoramica dell'attivazione di computer condivisi per Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Lingue**: Office viene installato automaticamente in una delle lingue supportate installate con Windows nel dispositivo dell'utente finale. Selezionare questa opzione se si vuole installare lingue aggiuntive con la suite di app. <p></p>
    È possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**. Per altre informazioni, vedere [Panoramica della distribuzione delle lingue in Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Selezionare i tag di ambito (facoltativo)
È possibile usare i tag di ambito per determinare chi può visualizzare le informazioni sull'app client in Intune. Per informazioni dettagliate complete sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

1. Selezionare **Ambito (tag)**  > **Aggiungi**.
2. Usare la casella **Seleziona** per cercare i tag di ambito.
3. Selezionare la casella di controllo accanto ai tag di ambito da assegnare a questa app.
4. Scegliere **Seleziona** > **OK**.

## <a name="enter-xml-format"></a>Immettere il formato XML

Se è stata selezionata l'opzione **Immettere i dati XML** nella casella di riepilogo a discesa **Formato delle impostazioni**, nel pannello **Aggiungi app** verrà visualizzata l'opzione **Enter XML format** (Immettere il formato XML). Per altre informazioni, vedere [Opzioni di configurazione per lo Strumento di distribuzione di Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Terminare

Al termine, selezionare **Aggiungi** nel riquadro **Aggiungi app**. L'app creata viene visualizzata nell'elenco di app.

## <a name="errors-during-installation-of-the-app-suite"></a>Errori durante l'installazione della suite di app

Le tabelle seguenti elencano i codici di errore comuni che possono essere visualizzati e il relativo significato.

### <a name="status-for-office-csp"></a>Stato di Office CSP

| Stato | Fase | Descrizione |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Download | Non è stato possibile scaricare lo strumento di distribuzione di Office |
| 13 (ERROR_INVALID_DATA) | - | Impossibile verificare la firma dello strumento di distribuzione di Office scaricato |
| Codice di errore da CertVerifyCertificateChainPolicy | - | Controllo del certificato non riuscito per lo strumento di distribuzione di Office scaricato |
| 997 | WIP | Installazione |
| 0 | Dopo l'installazione | Installazione completata |
| 1603 (ERROR_INSTALL_FAILURE) | - | I controlli dei prerequisiti hanno avuto esito negativo, ad esempio: SxS (È stata tentata l'installazione con la versione MSI 2016 installata), Versione non corrispondente, Altri |
| 0x8000ffff (E_UNEXPECTED) | - | È stata tentata la disinstallazione senza Office a portata di clic disponibile nel computer |
| 17002 | - | Non è stato possibile completare lo scenario (installazione). Motivi possibili: Installazione annullata dall'utente, Installazione annullata da un'altra installazione, Spazio su disco non sufficiente durante l'installazione, ID lingua sconosciuto |
| 17004 | - | SKU sconosciuti |


### <a name="office-deployment-tool-error-codes"></a>Codici di errore dello strumento di distribuzione di Office

| Scenario | Codice restituito | Interfaccia utente | Nota |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Disinstallazione senza installazione A portata di clic attiva | -2147418113, 0x8000ffff o 2147549183 | Codice errore: 30088-1008 Codice di errore: 30125-1011 (404) | Strumento di distribuzione di Office |
| Installazione con la versione MSI installata | 1603 | - | Strumento di distribuzione di Office |
| Installazione annullata dall'utente o da un'altra installazione | 17002 | - | A portata di clic |
| Tentativo di installazione della versione a 64 bit in un dispositivo in cui è installata la versione a 32 bit. | 1603 | - | Codice restituito dello strumento di distribuzione di Office |
| Tentativo di installazione di un codice SKU sconosciuto (caso d'uso non legittimo per Office CSP poiché devono essere passati solo i codici SKU validi) | 17004 | - | A portata di clic |
| Mancanza di spazio | 17002 | - | A portata di clic |
| Il client A portata di clic non è stato avviato (imprevisto) | 17000 | - | A portata di clic |
| Il client A portata di clic non è stato inserito in coda (imprevisto) | 17001 | - | A portata di clic |

## <a name="next-steps"></a>Passaggi successivi

- Per assegnare le app ai gruppi scelti, vedere [Assegnare app ai gruppi](/intune-azure/manage-apps/deploy-apps).
