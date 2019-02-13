---
title: Aggiungere app Win32 a Microsoft Intune
titlesuffix: ''
description: Informazioni su come aggiungere, distribuire e gestire app Win32 con Microsoft Intune. Questo argomento offre una panoramica delle funzionalità di distribuzione e gestione delle app Win32 di Intune, nonché informazioni sulla risoluzione dei problemi delle app Win32.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ba77c14e470ed75a87f44adcaf0ba9b98cd06438
ms.sourcegitcommit: e0d55bdda1a818ffe4cfc0ef0592833e22f65a89
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290758"
---
# <a name="intune-standalone---win32-app-management"></a>Intune autonomo - Gestione di app Win32

Intune autonomo consentirà maggiori funzionalità di gestione delle app Win32. Anche se per i clienti connessi al cloud è possibile usare Configuration Manager per la gestione delle app Win32, i clienti solo di Intune avranno maggiori funzionalità di gestione per le app line-of-business Win32. Questo argomento offre una panoramica della funzionalità di gestione delle app Win32 di Intune e informazioni sulla risoluzione dei problemi.

## <a name="prerequisites"></a>Prerequisiti

- Windows 10 versione 1607 o successive (edizioni Enterprise, Pro ed Education)
- Il client di Windows 10 deve essere: 
    - aggiunto ad Azure Active Directory (AAD) o ad Azure Active Directory ibrido e
    - registrato in Intune (gestito da MDM)
- Le dimensioni delle applicazioni Windows prevedono un limite di 8 GB per ogni app

## <a name="prepare-the-win32-app-content-for-upload"></a>Preparare il contenuto delle app Win32 per il caricamento

Usare lo [strumento Microsoft di preparazione dei contenuti Win32](https://go.microsoft.com/fwlink/?linkid=2065730) per eseguire l'analisi preliminare delle app Win32. Lo strumento converte i file di installazione delle applicazioni nel formato *intunewin*. Lo strumento rileva anche alcuni attributi richiesti da Intune per determinare lo stato di installazione delle applicazioni. Dopo aver usato questo strumento nella cartella di installazione delle app, sarà possibile creare un'app Win32 nella console di Intune.

È possibile scaricare lo [strumento Microsoft di preparazione dei contenuti Win32](https://go.microsoft.com/fwlink/?linkid=2065730) da GitHub.

### <a name="available-command-line-parameters"></a>Parametri della riga di comando disponibili 

|    **Parametro della riga di comando**    |    **Descrizione**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Help    |
|    `-c <setup_folder>`     |    Cartella di installazione per tutti i file di installazione.    |
|   ` -s <setup_file>`     |    File di installazione (ad esempio, *setup.exe* o *setup.msi*).    |
|    `-o <output_folder>`     |    Cartella di output per il file con estensione *intunewin* generato.    |
|    `-q`       |    Modalità non interattiva    |

### <a name="example-commands"></a>Comandi di esempio

|    **Comando di esempio**    |    **Descrizione**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Questo comando mostrerà le informazioni di utilizzo per lo strumento.    |
|    `IntuneWinAppUtil -c <setup_folder> -s <source_setup_file> -o <output_folder> <-q>`    |    Questo comando genererà il file `.intunewin` dalla cartella di origine e dal file di installazione specificati. Per il file di installazione MSI, questo strumento recupererà le informazioni necessarie per Intune. Se è specificato `-q`, il comando verrà eseguito in modalità non interattiva e se il file di output esiste già, verrà sovrascritto. Inoltre, se la cartella di output non esiste, verrà creata automaticamente.    |

Durante la generazione di un file con estensione *intunewin*, inserire gli eventuali file a cui è necessario fare riferimento in una sottocartella della cartella di installazione. Usare quindi un percorso relativo per fare riferimento al file specifico necessario. Ad esempio:

**Cartella di origine dell'installazione:** *c:\testapp\v1.0*<br>
**File di licenza:** *c:\testapp\v1.0\licenses\license.txt*

Fare riferimento al file *license.txt* usando il percorso relativo *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Creare, assegnare e monitorare un'app Win32

In modo analogo a un'app line-of-business, è possibile aggiungere un'app Win32 a Microsoft Intune. Questo tipo di app viene in genere scritto internamente o da terze parti. I passaggi seguenti forniscono istruzioni per l'aggiunta di un'app di Windows a Intune.

### <a name="step-1-specify-the-software-setup-file"></a>Passaggio 1: Specificare il file di installazione del software

1.  Accedere al [portale di Azure](https://portal.azure.com/).
2.  Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3.  Nel riquadro **Intune** selezionare **App client** > **App** > **Aggiungi**.
4.  Nel riquadro dell'app **Aggiungi** selezionare **App Windows (Win32)** nell'elenco a discesa.

    ![Screenshot del pannello Aggiungi app - elenco a discesa Tipo di app](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>Passaggio 2: Caricare il file del pacchetto dell'app

1.  Nel riquadro **Aggiungi app** selezionare **File del pacchetto dell'app** per selezionare un file. Verrà visualizzato il riquadro File del pacchetto dell'app.

    ![Screenshot del pannello File del pacchetto dell'app](./media/apps-win32-app-02.png)

2.  Nel riquadro **File del pacchetto dell'app** selezionare il pulsante Sfoglia. Selezionare quindi un file di installazione di Windows con l'estensione *intunewin*.

    > [!IMPORTANT]
    > Assicurarsi di usare la versione più recente dello strumento Microsoft di preparazione di contenuti Win32. Se non si usa la versione più recente, verrà visualizzato un avviso che indica che il pacchetto dell'app è stato compilato con una versione precedente dello strumento. 

3.  Al termine, fare clic su **OK**.

### <a name="step-3-configure-app-information"></a>Passaggio 3: Configurare le informazioni sull'app

1.  Nel riquadro **Aggiungi app** selezionare **Informazioni sull'app** per configurare l'app.
2.  Nel riquadro **Informazioni sull'app** configurare le informazioni seguenti. Alcuni dei valori in questo riquadro potrebbero venire inseriti automaticamente.
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Se il nome di un'app è usato due volte, ogni app verrà visualizzata nel portale aziendale.
    - **Description**: Immettere una descrizione per l'app. La descrizione viene visualizzata nel portale aziendale.
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Le categorie consentono agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: Visualizzare chiaramente l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario dell'app (facoltativo). Un esempio è **Reparto risorse umane**.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. L'icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
3.  Al termine, fare clic su **OK**.

### <a name="step-4-configure-app-installation-details"></a>Passaggio 4: Configurare i dettagli di installazione dell'app
1.  Nel riquadro **Aggiungi app** selezionare **Programma** per configurare i comandi di installazione e rimozione per l'app.
2.  Aggiungere la riga di comando di installazione completa per installare l'app. 

    Se ad esempio il nome file dell'app è **MyApp123**, aggiungere quanto segue: `msiexec /i “MyApp123.msi”`

3.  Aggiungere la riga di comando di disinstallazione completa per disinstallare l'app in base al GUID dell'app. 

    ad esempio `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > È possibile configurare un'app Win32 in modo che venga installata nel contesto **utente** o **di sistema**. Il contesto **utente** si riferisce solo a un determinato utente. Il contesto **di sistema** si riferisce a tutti gli utenti di un dispositivo Windows 10.
    >
    > Gli utenti finali non devono eseguire l'accesso al dispositivo per installare le app Win32.

4.  Al termine, fare clic su **OK**.

### <a name="step-5-configure-app-requirements"></a>Passaggio 5: Configurare i requisiti dell'app

1.  Nel riquadro **Aggiungi app** selezionare **Requisiti** per configurare i requisiti che i dispositivi devono soddisfare prima che l'app venga installata.
2.  Nel riquadro **Requisiti** configurare le informazioni seguenti. Alcuni dei valori in questo riquadro potrebbero venire inseriti automaticamente.
    - **Architettura del sistema operativo**: scegliere l'architettura necessaria per installare l'app.
    - **Sistema operativo minimo**: selezionare il sistema operativo minimo in cui è necessario installare l'app.
    - **Spazio su disco necessario (MB)**: aggiungere facoltativamente lo spazio libero su disco necessario nell'unità di sistema per installare l'app.
    - **Memoria fisica necessaria (MB)**: aggiungere facoltativamente la memoria fisica (RAM) necessaria per installare l'app.
    - **Numero minimo di processori logici necessari**: aggiungere facoltativamente il numero minimo di processori logici necessari per installare l'app.
    - **Velocità di CPU minima necessaria (MHz)**: aggiungere facoltativamente la velocità di CPU minima necessaria per installare l'app.
3.  Al termine, fare clic su **OK**.

### <a name="step-6-configure-app-detection-rules"></a>Passaggio 6: Configurare le regole di rilevamento dell'app

1.  Nel riquadro **Aggiungi app** selezionare **Regole di rilevamento** per configurare le regole per rilevare la presenza dell'app.
2.  Nel campo **Formato delle regole** selezionare come verrà rilevata la presenza dell'app. È possibile scegliere di configurare manualmente le regole di rilevamento oppure usare uno script personalizzato per rilevare la presenza dell'app. È necessario scegliere almeno una regola di rilevamento. 

    > [!NOTE]
    > Nel riquadro **Regole di rilevamento** è possibile scegliere di aggiungere più regole. Per rilevare l'app, devono essere soddisfatte le condizioni per **tutte** le regole.

    - **Configura manualmente le regole di rilevamento** - È possibile selezionare uno dei tipi di regole seguenti:
        1.  **MSI**: eseguire una verifica in base al controllo della versione MSI. Questa opzione può essere aggiunta una sola volta. Quando si sceglie questo tipo di regola, sono disponibili due impostazioni:
            - **Codice prodotto MSI**: aggiungere un codice prodotto MSI valido per l'app.
            - **Verifica della versione del prodotto MSI**: selezionare **Sì** per verificare la versione del prodotto MSI oltre al codice del prodotto MSI.
        2.  **File**: eseguire una verifica in base a rilevamento, data, versione o dimensioni del file o della cartella.
            - **Percorso**: percorso completo della cartella contenente il file o la cartella da rilevare.
            - **File o cartella**: file o cartella da rilevare.
            - **Metodo di rilevamento**: selezionare il tipo di metodo di rilevamento usato per convalidare la presenza dell'app.
            - **Associata a un'app a 32 bit nei client a 64 bit**: selezionare **Sì** per espandere eventuali variabili di ambiente PATH nel contesto a 32 bit nei client a 64 bit. Selezionare **No** (impostazione predefinita) per espandere eventuali variabili di ambiente nel contesto a 64 bit nei client a 64 bit. I client a 32 bit useranno sempre il contesto a 32 bit.
            
            **Esempi di rilevamento basato su file**
            1.  Verificare la presenza del file.
         
                ![Screenshot del riquadro Regola di rilevamento - esistenza del file](./media/apps-win32-app-03.png)
        
            2.  Verificare l'esistenza della cartella.
         
                ![Screenshot del riquadro Regola di rilevamento - esistenza della cartella](./media/apps-win32-app-04.png)
        
        3. **Registro**: eseguire una verifica in base a valore, stringa, Integer o versione.
            - **Percorso della chiave**: percorso completo della voce del Registro di sistema contenente il valore da rilevare.
            - **Nome valore**: nome del valore del Registro di sistema da rilevare. Se questo valore è vuoto, verrà eseguito il rilevamento della chiave. Il valore (predefinito) di una chiave verrà usato come valore di rilevamento se il metodo di rilevamento è diverso dall'esistenza del file o della cartella.
            - **Metodo di rilevamento**: selezionare il tipo di metodo di rilevamento usato per convalidare la presenza dell'app.
            - **Associata a un'app a 32 bit nei client a 64 bit**: selezionare **Sì** per eseguire ricerche nel Registro di sistema a 32 bit nei client a 64 bit. Selezionare **No** (impostazione predefinita) per eseguire ricerche nel Registro di sistema a 64 bit nei client a 64 bit. I client a 32 bit eseguiranno sempre ricerche nel registro di sistema a 32 bit.
            
            **Esempi di rilevamento basato sul Registro di sistema**
            1.  Cercare la chiave del Registro di sistema esistente.
            
                ![Screenshot del riquadro Regola di rilevamento - chiave del Registro di sistema esistente](./media/apps-win32-app-05.png)    
            
            2.  Verificare che il valore del Registro di sistema esista.
        
                ![Screenshot del riquadro Regola di rilevamento - valore del Registro di sistema esistente](./media/apps-win32-app-06.png)    
        
            3.  Cercare la stringa del valore del Registro di sistema Equals.
        
                ![Screenshot del riquadro Regola di rilevamento - stringa del valore del Registro di sistema Equals](./media/apps-win32-app-07.png)    
     
    - **Usa uno script di rilevamento personalizzato**: specificare lo script di PowerShell che verrà usato per rilevare questa app. 
    
        1.  **File di script**: selezionare uno script di PowerShell che rileverà la presenza dell'app nel client. L'app verrà rilevata quando lo script restituirà un codice di uscita con valore 0 e scriverà un valore stringa in STDOUT.

        2.  **Esegui lo script come processo a 32 bit nei client a 64 bit**: selezionare **Sì** per eseguire lo script in un processo a 32 bit su client a 64 bit. Selezionare **No** (impostazione predefinita) per eseguire lo script in un processo a 64 bit su client a 64 bit. I client a 32 bit eseguono lo script in un processo a 32 bit.

        3.  **Imponi il controllo della firma degli script**: selezionare **Sì** per verificare che lo script sia firmato da un'entità di pubblicazione attendibile, in modo da consentire l'esecuzione dello script senza la visualizzazione di avvisi o richieste. Lo script verrà eseguito senza essere bloccato. Selezionare **No** (impostazione predefinita) per eseguire lo script con la conferma dell'utente finale senza la verifica della firma.
    
            L'agente di Intune controlla i risultati dello script. Legge i valori scritti dallo script nel flusso di output standard (STDOUT) e nel flusso degli errori standard (STDERR), nonché il codice di uscita. Se il codice di uscita dello script è un valore diverso da zero, lo script non è riuscito e lo stato del rilevamento dell'applicazione è non installato. Se il codice di uscita è pari a zero e STDOUT contiene dati, lo stato di rilevamento dell'applicazione è installato. 

            > [!NOTE]
            > Quando lo script viene chiuso con il valore 0, l'esecuzione dello script ha avuto esito positivo. Il secondo canale di output indica che l'app è stata rilevata e i dati di STDOUT indicano che l'app è stata trovata nel client. Non è necessario cercare una determinata stringa di STDOUT.

        4.  Dopo aver aggiunto una o più regole, selezionare **Aggiungi** > **OK**.

### <a name="step-7-configure-app-return-codes"></a>Passaggio 7: Configurare i codici restituiti dell'app

1.  Nel riquadro **Aggiungi app** selezionare **Codici restituiti** per aggiungere i codici restituiti usati per specificare il comportamento in caso di nuovo tentativo di installazione dell'app o il comportamento successivo all'installazione. Le voci dei codici restituiti vengono aggiunte durante la creazione dell'app per impostazione predefinita. È tuttavia possibile aggiungere altri codici restituiti o modificare i codici restituiti esistenti. 
2.  Nel riquadro **Codici restituiti** aggiungere altri codici restituiti o modificare i codici restituiti esistenti.
    - **Errore**: valore restituito indicante un errore di installazione dell'app.
    - **Avvio a freddo**: Il codice restituito di avvio a freddo non consente di installare le app Win32 successive nel client senza riavvio. 
    - **Avvio a caldo**: il codice restituito di avvio a caldo consente di installare le app Win32 successive senza richiedere un riavvio del client. Il riavvio è necessario per completare l'installazione dell'applicazione corrente.
    - **Riprova**: l'agente del codice restituito di nuovo tentativo proverà a installare l'app tre volte. Attenderà 5 minuti tra un tentativo e l'altro. 
    - **Riuscita**: valore restituito indicante che l'app è stata installata correttamente.
3.  Selezionare **OK** dopo aver aggiunto o modificato l'elenco di codici restituiti.

### <a name="step-8-add-the-app"></a>Passaggio 8: Aggiungere l'app

1.  Nel riquadro **Aggiungi app** verificare di aver configurato correttamente le informazioni sull'app.
2.  Selezionare **Aggiungi** per caricare l'app in Intune.

### <a name="step-9-assign-the-app"></a>Passaggio 9: Assegnare l'app

1.  Nel riquadro dell'app selezionare **Assegnazioni**.
2.  Selezionare **Aggiungi gruppo** per aprire il riquadro **Aggiungi gruppo** relativo all'app.
3.  Per l'app specifica, selezionare un **tipo di assegnazione**:
    - **Disponibile per i dispositivi registrati**: gli utenti installano l'app dall'app Portale aziendale o dal relativo sito Web.
    - **Obbligatoria**: l'app viene installata nei dispositivi nei gruppi selezionati.
    - **Disinstalla**: l'app viene disinstallata dai dispositivi nei gruppi selezionati.
4.  Selezionare **Gruppi inclusi** e assegnare i gruppi che useranno questa app.
5.  Nel riquadro **Assegna** fare clic su **OK** per completare la selezione dei gruppi inclusi.
6.  Per escludere gruppi di utenti da questa assegnazione di app, selezionare **Escludi gruppi**.
7.  Nel riquadro **Aggiungi gruppo** selezionare **OK**.
8.  Nel riquadro **Assegnazioni** dell'app selezionare **Salva**.

A questo punto è stata completata la procedura per aggiungere un'app Win32 a Intune. Per informazioni sull'assegnazione e il monitoraggio di app, vedere [Assegnare app ai gruppi con Microsoft Intune](https://docs.microsoft.com/intune/apps-deploy) e [Monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune](https://docs.microsoft.com/intune/apps-monitor).

## <a name="delivery-optimization"></a>Ottimizzazione recapito

I client Windows 10 RS3 e versioni successive scaricheranno contenuto dell'app Win32 Intune mediante un componente Ottimizzazione recapito nel client Windows 10. Ottimizzazione recapito offre funzionalità peer-to-peer attivate per impostazione predefinita. È possibile configurare Ottimizzazione recapito tramite Criteri di gruppo e in futuro tramite Intune MDM. Per altre informazioni, vedere [Ottimizzazione recapito per Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Installare le app obbligatorie e disponibili nei dispositivi

L'utente finale riceverà le notifiche di tipo avviso popup di Windows per le installazioni delle app obbligatorie e disponibili. L'immagine seguente mostra un esempio di notifica di tipo avviso popup in cui l'installazione dell'app non risulta completa fino al riavvio del dispositivo. 

![Screenshot delle notifiche di tipo avviso popup di Windows per l'installazione di un'app](./media/apps-win32-app-08.png)    

Nell'immagine seguente l'utente finale riceve una notifica indicante che sono in corso modifiche all'app nel dispositivo.

![Screenshot di invio della notifica relativa alle modifiche in corso per l'app](./media/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Notifiche di tipo avviso popup per app Win32 
Se necessario, è possibile eliminare la visualizzazione delle notifiche di tipo avviso popup degli utenti finali per ogni assegnazione di app. Da Intune, selezionare **App Client** > **App** > selezionare l'app > **Assegnazioni** > **Include Groups** (Includi gruppi). 

## <a name="troubleshoot-win32-app-issues"></a>Risolvere i problemi delle app Win32
I log dell'agente nel computer client si trovano in genere in `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. È possibile usare `CMTrace.exe` per visualizzare questi file di log. *CMTrace.exe* può essere scaricato da [Strumenti client SCCM](https://docs.microsoft.com/sccm/core/support/tools). 

![Screenshot dei log dell'agente nel computer client](./media/apps-win32-app-10.png)    

### <a name="troubleshooting-areas-to-consider"></a>Aree della risoluzione dei problemi da tenere in considerazione
- Controllare la destinazione per verificare che l'agente sia installato nel dispositivo: l'app Win32 destinata a un gruppo o lo script di PowerShell destinato a un gruppo creerà criteri di installazione dell'agente per il gruppo di sicurezza.
- Controllare la versione del sistema operativo: Windows 10 1607 e versioni successive.  
- Controllare lo SKU di Windows 10: Windows 10 S o le versioni di Windows in esecuzione con la modalità S abilitata non supportano l'installazione MSI.

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sull'aggiunta di app a Intune, vedere [Aggiungere app in Microsoft Intune](apps-add.md).
