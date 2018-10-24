---
title: Installare le app di Office 365 nei dispositivi usando Microsoft Intune
titlesuffix: ''
description: Informazioni su come usare Microsoft Intune per rendere più semplice l'installazione delle app di Office 365 nei dispositivi Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1fb8e4f309e7ab80282dd0e94a10473442238db
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2018
ms.locfileid: "49424969"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune

Questo tipo di app semplifica l'assegnazione delle app Office 365 ai dispositivi gestiti che eseguono Windows 10. È anche possibile installare app per il client per desktop di Microsoft Project Online e Microsoft Visio Pro for Office 365 se si è proprietari delle relative licenze. Le app desiderate vengono visualizzate come un'unica voce nell'elenco delle app nella console di Intune.

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
- **Remove MSI from end-user devices** (Rimuovi MSI dai dispositivi degli utenti finali) - Scegliere se si vogliono rimuovere le app MSI di Office preesistenti dai dispositivi degli utenti finali. L'installazione non riesce se sono già presenti app MSI nei dispositivi degli utenti finali. Le app da disinstallare non sono limitate alle app selezionate per l'installazione in **Configura la suite di app**, in quanto verranno rimosse tutte le app di Office (MSI) dal dispositivo dell'utente finale. Per altre informazioni, vedere [Rimuovere le versioni MSI esistenti di Office durante l'aggiornamento a Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). 

## <a name="get-started"></a>Operazioni preliminari

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro del carico di lavoro **App client** in **Gestisci** selezionare **App**.
5. Selezionare **Aggiungi**.
6. Nel riquadro **Aggiungi app**, nell'elenco **Tipo di app**, in **Office 365 Suite** selezionare **Windows 10**.

A questo punto è possibile configurare la suite di app.

## <a name="configure-the-app-suite"></a>Configurare la suite di app

Selezionare le app di Office che si vuole assegnare ai dispositivi.

1. Nel riquadro **Aggiungi app** selezionare **Configura la suite di app**.
2. Nel riquadro **Configura la suite di app** selezionare le app di Office standard da assegnare ai dispositivi.  
    È anche possibile installare app per il client per desktop di Microsoft Project Online e Microsoft Visio Pro for Office 365 se si è proprietari delle relative licenze.
3. Selezionare **OK**.

## <a name="configure-app-information"></a>Configurare le informazioni sull'app

In questo passaggio si specificano le informazioni sulla suite di app. Queste informazioni consentono di identificare la suite di app in Intune e semplificano la ricerca della suite di app da parte degli utenti nel portale aziendale.

1. Nel riquadro **Aggiungi app** selezionare **Informazioni sulla suite di app**.
2. Nel riquadro **Informazioni sulla suite di app** seguire questa procedura:
    - **Nome della suite**: immettere il nome della suite di app visualizzato nel portale aziendale. Verificare che tutti i nomi di suite usati siano univoci. Se il nome di una suite viene usato due volte, solo una delle due suite viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione della suite**: immettere una descrizione per la suite di app. Ad esempio, è possibile elencare le app selezionate da includere.
    - **Editore**: Microsoft viene visualizzato come editore.
    - **Categoria**: facoltativamente, selezionare una o più categorie di app predefinite oppure una categoria creata. Questa impostazione consente agli utenti di trovare più facilmente il gruppo di app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: Microsoft viene visualizzato come sviluppatore.
    - **Proprietario**: Microsoft viene visualizzato come proprietario.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: il logo Office 365 è visualizzato insieme all'app quando gli utenti visitano il portale aziendale.
3. Selezionare **OK**.

## <a name="configure-app-settings"></a>Configurare le impostazioni dell'app

In questo passaggio configurare le opzioni di installazione per la suite di app. Le impostazioni si applicano a tutte le app aggiunte alla suite.

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

    - **Remove MSI from end-user devices** (Rimuovi MSI dai dispositivi degli utenti finali) - Scegliere se si vogliono rimuovere le app MSI di Office preesistenti dai dispositivi degli utenti finali. L'installazione non riesce se sono già presenti app MSI nei dispositivi degli utenti finali. Le app da disinstallare non sono limitate alle app selezionate per l'installazione in **Configura la suite di app**, in quanto verranno rimosse tutte le app di Office (MSI) dal dispositivo dell'utente finale. Per altre informazioni, vedere [Rimuovere le versioni MSI esistenti di Office durante l'aggiornamento a Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). 
    - **Accetta automaticamente il contratto di licenza con l'utente finale**: selezionare questa opzione se non si richiede agli utenti finali di accettare il contratto di licenza. Intune accetterà automaticamente il contratto.
    - **Usa l'attivazione di computer condivisi**: selezionare questa opzione quando più utenti condividono un computer. Per altre informazioni, vedere [Panoramica dell'attivazione di computer condivisi per Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Lingue**: Office viene installato automaticamente in una delle lingue supportate installate con Windows nel dispositivo dell'utente finale. Selezionare questa opzione se si vuole installare lingue aggiuntive con la suite di app. <p></p>
    È possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**. Per altre informazioni, vedere [Panoramica della distribuzione delle lingue in Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="finish-up"></a>Terminare

Al termine, selezionare **Aggiungi** nel riquadro **Aggiungi app**. L'app creata viene visualizzata nell'elenco di app.

## <a name="errors-during-installation-of-the-app-suite"></a>Errori durante l'installazione della suite di app

Le tabelle seguenti elencano i codici di errore comuni che possono essere visualizzati e il relativo significato.

### <a name="status-for-office-csp"></a>Stato di Office CSP

||||
|-|-|-|
|Stato|Fase|Descrizione|
|1460 (ERROR_TIMEOUT)|Download|Non è stato possibile scaricare lo strumento di distribuzione di Office|    
|13 (ERROR_INVALID_DATA)|-|Impossibile verificare la firma dello strumento di distribuzione di Office scaricato|
|Codice di errore da CertVerifyCertificateChainPolicy|-|Controllo del certificato non riuscito per lo strumento di distribuzione di Office scaricato|    
|997|WIP|Installazione|
|0|Dopo l'installazione|Installazione completata|    
|1603 (ERROR_INSTALL_FAILURE)|-|Non sono stati eseguiti tutti i controlli dei prerequisiti, ad esempio:<ul><li>SxS (È stata tentata l'installazione con la versione MSI 2016 installata)</li><li>Versione non corrispondente</li><li>Altri</li></ul>|  
|0x8000ffff (E_UNEXPECTED)|-|È stata tentata la disinstallazione senza Office a portata di clic disponibile nel computer|     
|17002|-|Non è stato possibile completare lo scenario (installazione). Motivi possibili:<ul><li>Installazione annullata dall'utente</li><li>Installazione annullata da un'altra installazione</li><li>Spazio su disco non sufficiente durante l'installazione</li><li>ID lingua sconosciuto</li></ul>|
|17004|-|SKU sconosciuti|   


### <a name="office-deployment-tool-error-codes"></a>Codici di errore dello strumento di distribuzione di Office

|||||
|-|-|-|-|
|Scenario|Codice restituito|Interfaccia utente|Nota|
|Disinstallazione senza installazione A portata di clic attiva|-2147418113, 0x8000ffff o 2147549183|Codice di errore: 30088-1008<br>Codice di errore: 30125-1011 (404)|Strumento di distribuzione di Office|
|Installazione con la versione MSI installata|1603|-|Strumento di distribuzione di Office|
|Installazione annullata dall'utente o da un'altra installazione|17002|-|A portata di clic|
|Tentativo di installazione della versione a 64 bit in un dispositivo in cui è installata la versione a 32 bit.|1603|-|Codice restituito dello strumento di distribuzione di Office|
|Tentativo di installazione di un codice SKU sconosciuto (caso d'uso non legittimo per Office CSP poiché devono essere passati solo i codici SKU validi)|17004|-|A portata di clic|
|Mancanza di spazio|17002|-|A portata di clic|
|Il client A portata di clic non è stato avviato (imprevisto)|17000|-|A portata di clic|
|Il client A portata di clic non è stato inserito in coda (imprevisto)|17001|-|A portata di clic|

## <a name="next-steps"></a>Passaggi successivi

- Per assegnare le app ai gruppi scelti, vedere [Assegnare app ai gruppi](/intune-azure/manage-apps/deploy-apps).
