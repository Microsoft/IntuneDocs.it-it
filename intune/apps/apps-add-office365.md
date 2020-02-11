---
title: Installare app di Office 365 in dispositivi Windows 10 con Microsoft Intune
titleSuffix: ''
description: Informazioni su come usare Microsoft Intune per installare le app di Office 365 nei dispositivi Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86d02ae1277ff2fd6dfce9bf206628f5dc1c2a84
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755325"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Installare app di Office 365 in dispositivi Windows 10 con Microsoft Intune

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. Tra i [tipi di app](apps-add.md#app-types-in-microsoft-intune) disponibili ci sono le app di Office 365 per i dispositivi Windows 10. Selezionando questo tipo di app in Intune, è possibile assegnare e installare le app di Office 365 nei dispositivi gestiti che eseguono Windows 10. È anche possibile assegnare e installare app per il client desktop Microsoft Project Online e Microsoft Visio Online piano 2, se si hanno le licenze di questi prodotti. Le app di Office 365 disponibili sono visualizzate come un'unica voce nell'elenco delle app nella console di Intune in Azure.

> [!NOTE]
> È necessario usare le licenze di Office 365 ProPlus per attivare le app di Office 365 ProPlus distribuite tramite Microsoft Intune. Attualmente, Intune non supporta Office 365 Business Edition.

## <a name="before-you-start"></a>Prima di iniziare

> [!IMPORTANT]
> Se sono presenti app di Office con estensione msi nel dispositivo dell'utente finale, è necessario usare la funzionalità di **rimozione dei file MSI** per disinstallare correttamente queste app. In caso contrario, le app di Office 365 distribuite da Intune non verranno installate.

- È necessario che i dispositivi in cui vengono distribuite le app eseguano Windows 10 Creators Update o versioni successive.
- Intune supporta l'aggiunta di app di Office solo dalla suite Office 365.
- Se sono aperte app di Office quando Intune installa la suite di app, è possibile che l'installazione non riesca e che gli utenti perdano i dati dei file non salvati.
- Questo metodo di installazione non è supportato nei dispositivi Windows Home, Windows Team, Windows Holographic o Windows Holographic for Business.
- Intune non consente di installare le app desktop di Office 365 da Microsoft Store (note come app Office Centennial) in un dispositivo a cui sono già state distribuite app di Office 365 con Intune. Se si installa questa configurazione, si potrebbero verificare perdite o danneggiamenti dei dati.
- Più assegnazioni di app necessarie o disponibili non sono cumulative. Un'assegnazione di app successiva sovrascriverà le assegnazioni di app installate preesistenti. Ad esempio, se il primo set di app di Office contiene Word mentre il successivo set non lo contiene, Word verrà disinstallato. Questa condizione non si applica alle applicazioni di Visio o Project.
- Non sono attualmente supportate più distribuzioni di Office 365. Solo una distribuzione verrà recapitata al dispositivo.
- **Versione di Office** - Scegliere se assegnare la versione a 32 bit o a 64 bit di Office. La versione a 32 bit può essere installata in dispositivi a 32 bit e a 64 bit, mentre la versione a 64 bit può essere installata solo in dispositivi a 64 bit.
- **Remove MSI from end-user devices** (Rimuovi MSI dai dispositivi degli utenti finali) - Scegliere se si vogliono rimuovere le app MSI di Office preesistenti dai dispositivi degli utenti finali. L'installazione non riesce se sono già presenti app MSI nei dispositivi degli utenti finali. Le app da disinstallare non sono limitate alle app selezionate per l'installazione in **Configura la suite di app**, in quanto verranno rimosse tutte le app di Office (MSI) dal dispositivo dell'utente finale. Per altre informazioni, vedere [Rimuovere le versioni MSI esistenti di Office durante l'aggiornamento a Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando Intune reinstalla Office nei computer dell'utente finale, i Language Pack saranno gli stessi usati nelle precedenti installazioni di Office MSI.

## <a name="select-the-office-365-suite-app-type"></a>Selezionare il tipo di app Famiglia di prodotti Office 365

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Selezionare **Windows 10** nella sezione **Famiglia di prodotti Office 365** del riquadro **Seleziona il tipo di app**.
4. Fare clic su **Seleziona**. Verrà visualizzata la procedura **Aggiungi la famiglia di prodotti Office 365**.


## <a name="step-1---app-suite-information"></a>Passaggio 1: informazioni sulla famiglia di prodotti dell'app

In questo passaggio si specificano le informazioni sulla suite di app. Queste informazioni consentono di identificare la suite di app in Intune e semplificano la ricerca della suite di app da parte degli utenti nel portale aziendale.

1. Nella pagina **Informazioni sulla famiglia di prodotti dell'app** è possibile confermare o modificare i valori predefiniti:
    - **Nome della suite**: immettere il nome della suite di app visualizzato nel portale aziendale. Verificare che tutti i nomi di suite usati siano univoci. Se il nome di una suite viene usato due volte, solo una delle due suite viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione della suite** : immettere una descrizione per la suite di app. Ad esempio, è possibile elencare le app selezionate da includere.
    - **Autore**: come editore viene visualizzato Microsoft.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa impostazione consente agli utenti di trovare più facilmente il gruppo di app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: come sviluppatore viene visualizzato Microsoft.
    - **Proprietario**: come proprietario viene visualizzato Microsoft.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: quando gli utenti visitano il portale aziendale, il logo Office 365 viene visualizzato insieme all'app.
2. Fare clic su **Avanti** per visualizzare la pagina **Configura la famiglia di prodotti dell'app**.

## <a name="step-2---option-1-configure-app-suite-using-the-configuration-designer"></a>Passaggio 2: (**opzione 1**) configurare la famiglia di prodotti dell'app usando la progettazione di configurazione 

È possibile scegliere un metodo per la configurazione dell'impostazione delle app selezionando un'opzione per **Formato delle impostazioni di configurazione**. Le opzioni per il formato delle impostazioni includono:
- Progettazione configurazione
- Immettere i dati XML

Quando si sceglie **Progettazione configurazione**, il riquadro **Aggiungi app** cambia per includere tre aree per le impostazioni aggiuntive:
- Configurare la suite di app
- Informazioni sulla famiglia di prodotti dell'app
- Proprietà

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

1. Nella pagina **Configurazione della suite di app** scegliere **Progettazione configurazione**.
   - **Selezionare le app di Office**: selezionare le app di Office standard da assegnare ai dispositivi scegliendo le app dall'elenco a discesa.
   - **Selezionare altre app di Office (licenza obbligatoria)** : selezionare le app di Office aggiuntive da assegnare ai dispositivi e delle quali di dispone di licenze scegliendo le app dall'elenco a discesa. Sono incluse app con licenza, ad esempio il client desktop di Microsoft Project Online e Microsoft Visio Online piano 2.
   - **Architettura**: scegliere se assegnare la versione a **32 bit** o a  **64 bit** di Office ProPlus. La versione a 32 bit può essere installata in dispositivi a 32 bit e a 64 bit, mentre la versione a 64 bit può essere installata solo in dispositivi a 64 bit.
    - **Canale di aggiornamento**: scegliere la modalità di aggiornamento di Office nei dispositivi. Per informazioni sui diversi canali di aggiornamento, vedere [Panoramica dei canali di aggiornamento per Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Scegliere tra:
        - **Monthly** (Mensile)
        - **Monthly (Targeted)** (Mensile - mirato)
        - **Semi-Annual** (Semestrale)
        - **Semi-Annual (Targeted)** (Semestrale - mirato)

        Dopo aver scelto un canale, è possibile scegliere quanto riportato di seguito:
        - **Rimuovi altre versioni**: selezionare **Sì** per rimuovere altre versioni di Office (MSI) dai dispositivi utente. Scegliere questa opzione per rimuovere le app MSI di Office preesistenti dai dispositivi degli utenti finali. L'installazione non riesce se sono già presenti app MSI nei dispositivi degli utenti finali. Le app da disinstallare non sono limitate alle app selezionate per l'installazione in **Configura la suite di app**, in quanto verranno rimosse tutte le app di Office (MSI) dal dispositivo dell'utente finale. Per altre informazioni, vedere [Rimuovere le versioni MSI esistenti di Office durante l'aggiornamento a Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando Intune reinstalla Office nei computer dell'utente finale, i Language Pack saranno gli stessi usati nelle precedenti installazioni di Office MSI. 
        - **Versione da installare**: scegliere la versione di Office da installare.
        - **Versione specifica**: se è stata scelta l'opzione precedente **Specifico** come **Versione da installare**, è possibile scegliere di installare una versione specifica di Office per il canale selezionato nei dispositivi degli utenti finali. 
            
            Le versioni disponibili cambieranno nel corso del tempo. Quando si crea una nuova distribuzione, le versioni disponibili potrebbero quindi essere più recenti e alcune versioni precedenti potrebbero non essere disponibili. Le distribuzioni correnti continueranno a distribuire la versione precedente, ma l'elenco delle versioni verrà continuamente aggiornato per ogni canale.
            
            I dispositivi che aggiornano la versione aggiunta (o aggiornano qualsiasi altra proprietà) e vengono distribuiti come disponibili, verranno indicati come installati nello stato di report se era installata una versione precedente fino alla connessione del dispositivo. Alla connessione del dispositivo, lo stato cambierà temporaneamente in Sconosciuto, ma non verrà visualizzato all'utente. Quando l'utente avvia l'installazione per la versione più recente disponibile, all'utente verrà visualizzato lo stato modificato Installato.
            
            Per altre informazioni, vedere [Panoramica dei canali di aggiornamento per Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).
    - **Usa l'attivazione di computer condivisi**: selezionare questa opzione quando più utenti condividono un computer. Per altre informazioni, vedere [Panoramica dell'attivazione di computer condivisi per Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Accetta automaticamente il contratto di licenza con l'utente finale** : selezionare questa opzione se non si richiede agli utenti finali di accettare il contratto di licenza. Intune accetterà automaticamente il contratto.
    - **Lingue**: Office viene installato automaticamente in una delle lingue supportate installate con Windows nel dispositivo dell'utente finale. Selezionare questa opzione se si vuole installare lingue aggiuntive con la suite di app. <p></p>
        È possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App** > **Tutte le app** > **Aggiungi**. Nell'elenco **Tipo di app** del riquadro **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel riquadro **Impostazioni della suite di app**. Per altre informazioni, vedere [Panoramica della distribuzione delle lingue in Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).
2. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.

## <a name="step-2---option-2-configure-app-suite-using-xml-data"></a>Passaggio 2: (**opzione 2**) configurare la famiglia di prodotti dell'app usando i dati XML 

Se è stata selezionata l'opzione **Immettere i dati XML** nella casella a discesa **Formato delle impostazioni** della pagina **Configura la famiglia di prodotti dell'app**, è possibile configurare la famiglia di prodotti dell'app Office usando un file di configurazione personalizzato.

![Aggiungere la finestra di progettazione della configurazione di Office 365](./media/apps-add-office365/apps-add-office365-01.png)

1. Aggiungere il file XML di configurazione.
2. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.

Per altre informazioni sull'immissione di dati XML, vedere [Opzioni di configurazione per lo Strumento di distribuzione di Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="step-3---select-scope-tags-optional"></a>Passaggio 3: selezionare i tag di ambito (facoltativo)
È possibile usare i tag di ambito per determinare chi può visualizzare le informazioni sull'app client in Intune. Per informazioni dettagliate complete sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

1. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per la famiglia di prodotti dell'app. 
2. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.

## <a name="step-4---assignments"></a>Passaggio 4 - Assegnazioni

1. Per l'assegnazione della famiglia di prodotti dell'app a gruppi, selezionare **Obbligatoria**, **Disponibile per i dispositivi registrati** o **Disinstalla**. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md) e [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).
2. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. 

## <a name="step-5---review--create"></a>Passaggio 5 - Verifica e creazione

1. Verificare i valori e le impostazioni immessi per la famiglia di prodotti dell'app.
2. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

    Verrà visualizzato il pannello **Panoramica** della famiglia di prodotti dell'app Office 365 per Window 10 creata.

## <a name="deployment-details"></a>Dettagli di distribuzione

Dopo aver assegnato i criteri di distribuzione di Intune ai computer di destinazione tramite il [provider di servizi di configurazione di Office](https://docs.microsoft.com/windows/client-management/mdm/office-csp), il dispositivo finale scarica automaticamente il pacchetto di installazione dal percorso *officecdn.microsoft.com*. Verranno visualizzate due directory nella directory *Programmi*:

![Pacchetti di installazione di Office nella directory Programmi](./media/apps-add-office365/office-folder.png)

Nella directory *Microsoft Office* viene creata una nuova cartella in cui vengono archiviati i file di installazione:

![Nuova cartella creata nella directory Microsoft Office](./media/apps-add-office365/created-folder.png)

Nella directory *Microsoft Office 15* vengono archiviati i file dell'utilità di avvio dell'installazione A portata di clic di Office. L'installazione verrà avviata automaticamente se è necessario il tipo di assegnazione:

![File di avvio dell'installazione A portata di clic](./media/apps-add-office365/clicktorun-files.png)

L'installazione sarà in modalità invisibile all'utente se la famiglia di prodotti Office 365 è configurata come richiesta. I file di installazione scaricati verranno eliminati una volta completata l'installazione. Se l'assegnazione è configurata come **Disponibile**, le applicazioni Office verranno visualizzate nell'applicazione Portale aziendale in modo che gli utenti finali possano attivare l'installazione manualmente.

## <a name="troubleshooting"></a>Risoluzione dei problemi
Intune usa lo [strumento di distribuzione di Office](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) per scaricare e distribuire Office 365 ProPlus ai computer client usando la [rete CDN di Office 365](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Fare riferimento alle procedure consigliate descritte in [Gestione degli endpoint di Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) per garantire che la configurazione di rete consenta ai client di accedere alla rete CDN direttamente anziché indirizzare il traffico della rete CDN tramite proxy centrali per evitare di introdurre latenza inutile.

Eseguire [Assistente supporto e ripristino per Office 365](https://diagnostics.office.com) su un dispositivo di destinazione se si verificano problemi in fase di esecuzione o installazione.

### <a name="additional-troubleshooting-details"></a>Altri dettagli per la risoluzione dei problemi

Quando non è possibile installare le app di Office 365 in un dispositivo, è necessario stabilire se il problema è correlato a Intune o al sistema operativo oppure a Office. Se è possibile visualizzare le due cartelle *Microsoft Office* e *Microsoft Office 15* nella directory *Programmi* del dispositivo, si può supporre che Intune abbia avviato correttamente la distribuzione. Se non è possibile visualizzare le due cartelle in *Programmi*, è necessario verificare quanto segue:

- Il dispositivo è registrato correttamente in Microsoft Intune. 
- È presente una connessione di rete attiva nel dispositivo. Se il dispositivo è in modalità aereo, è disattivato o si trova in una posizione in cui il servizio non funziona, il criterio non verrà applicato finché non verrà stabilita la connettività di rete.
- Sono soddisfatti i requisiti di rete di Intune e Office 365 e gli intervalli di indirizzi IP correlati sono accessibili in base agli articoli seguenti:

  - [Requisiti di configurazione di rete di Intune e larghezza di banda](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [URL e intervalli di indirizzi IP per Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- La famiglia di app di Office 365 è stata assegnata ai gruppi corretti. 

Monitorare anche le dimensioni della directory *C:\Programmi\Microsoft Office\Updates\Download*. Il pacchetto di installazione scaricato dal cloud di Intune verrà archiviato in questo percorso. Se le dimensioni non aumentano o aumentano molto lentamente, è consigliabile verificare la connettività di rete e la larghezza di banda.

Quando è possibile concludere che sia Intune che l'infrastruttura di rete funzionano come previsto, è necessario analizzare il problema dalla prospettiva del sistema operativo. Prendere in considerazione le condizioni seguenti:

- Il dispositivo di destinazione deve essere eseguito in Windows 10 Creators Update o versioni successive.
- Mentre Intune distribuisce le applicazioni non vengono aperte app di Office esistenti.
- Le versioni di MSI di Office esistenti sono state rimosse correttamente dal dispositivo. Intune usa A portata di clic di Office, che non è compatibile con MSI di Office. Questo comportamento è indicato più avanti nel documento:<br>
  [Le edizioni di Office installate con A portata di clic e basate su Windows Installer non possono convivere nello stesso computer](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- L'utente di accesso deve avere l'autorizzazione per installare le applicazioni nel dispositivo.
- Verificare che non siano presenti problemi basati sul registro di Windows Visualizzatore eventi **Registri di Windows** -> **Applicazioni**.
- Acquisire i log dettagliati dell'installazione di Office durante l'installazione. A tale scopo, attenersi alla seguente procedura:<br>
    1. Attivare la registrazione dettagliata per l'installazione di Office nei computer di destinazione. A tale scopo, eseguire il comando seguente per modificare il Registro di sistema:<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. Distribuire di nuovo la famiglia di prodotti Office 365 nei dispositivi di destinazione.<br>
    3. Attendere circa 15-20 minuti e passare alla cartella **%temp%** e alla cartella **%windir%\temp**, ordinare per **Data modifica**, selezionare i file *{nome computer}-{timestamp}.log* modificati in base al tempo di riproduzione.<br>
    4. Per disabilitare il log dettagliato, eseguire il comando seguente:<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        I log dettagliati possono offrire maggiori informazioni sul processo di installazione.

## <a name="errors-during-installation-of-the-app-suite"></a>Errori durante l'installazione della suite di app

Vedere [How to enable Office 365 ProPlus ULS logging](/office/troubleshoot/diagnostic-logs/how-to-enable-office-365-proplus-uls-logging) (Come abilitare la registrazione del Servizio di registrazione unificato di Office 365 ProPlus) per informazioni su come visualizzare i log di installazione dettagliati.

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

- Per assegnare la famiglia di prodotti dell'app a gruppi aggiuntivi, vedere [Assegnare app ai gruppi](/intune-azure/manage-apps/deploy-apps).
