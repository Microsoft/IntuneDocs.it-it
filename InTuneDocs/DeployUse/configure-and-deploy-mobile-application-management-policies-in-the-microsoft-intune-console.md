---
# required metadata

title: Configurare e distribuire i criteri di gestione delle applicazioni mobili nella console di Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configure and deploy mobile application management policies in the Microsoft Intune console
I criteri di gestione delle applicazioni mobili in Microsoft Intune consentono di modificare la funzionalità delle app distribuite per adeguarle ai criteri aziendali di conformità e sicurezza. Ad esempio, è possibile limitare le operazioni Taglia, Copia e Incolla in un'app gestita oppure configurare un'app per aprire tutti i collegamenti Web in Managed Browser.

I criteri di gestione delle applicazioni mobili supportano:

-   Dispositivi che eseguono Android 4 e versioni successive

-   Dispositivi che eseguono iOS 7 e versioni successive

> [!TIP]
> I criteri di gestione delle applicazioni mobili supportano i dispositivi registrati con Intune.
> 
> Per informazioni su come creare i criteri di gestione delle app per i dispositivi non gestiti da Intune, vedere [Proteggere i dati delle app usando i criteri di gestione delle app mobili con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

A differenza degli altri criteri di Intune, i criteri di gestione delle applicazioni mobili non vengono distribuiti direttamente ma, al contrario, è possibile associare i criteri all'app che si vuole limitare. Le impostazioni specificate diventeranno effettive quando l'app viene distribuita e installata nei dispositivi.

Per applicare restrizioni a un'app, questa deve includere Microsoft App Software Development Kit (SDK). Esistono due metodi per ottenere questo tipo di app:

-   **Usare un'app gestita da criteri**: include App SDK. Per aggiungere questo tipo di applicazione, è possibile specificare un collegamento all'app da un archivio di app, ad esempio l'iTunes store o Google Play. Non sono richieste ulteriori elaborazioni per questo tipo di app. Vedere un elenco delle [app che si possono usare con i criteri di gestione delle applicazioni di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

-   **Usare un'app di cui è stato eseguito il wrapping**: app che sono state riassemblate per includere App SDK usando lo **strumento di wrapping delle app di Microsoft Intune**. Questo strumento viene in genere usato per elaborare le app aziendali create internamente. Non può essere usato per elaborare le app state scaricate dall'App Store. Vedere [Preparare le app iOS per la gestione delle applicazioni mobili con lo strumento per la disposizione testo delle app di Microsoft Intune](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [Preparare le app Android per la gestione delle applicazioni mobili con lo strumento per la disposizione testo delle app di Microsoft Intune](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

Alcune app gestite, ad esempio l'app Outlook per iOS e Android supportano **più identità**. Ciò significa che Intune si applica solo le impostazioni di gestione di account aziendali o dati nell'applicazione.

Ad esempio, utilizzando Outlook app:

-   Se l'utente configura un account di posta elettronica aziendale e uno personale, Intune applica le impostazioni di gestione solo all'account aziendale e non gestisce l'account personale.

-   Se il dispositivo viene ritirato o unenrolled, solo i dati aziendali di Outlook viene rimosso dal dispositivo.

-   L'account aziendale usato deve essere lo stesso account specificato durante la registrazione del dispositivo con Intune.

> [!TIP]
> Se si usa Intune con Configuration Manager, vedere [Come controllare le app usando i criteri di gestione delle applicazioni mobili in Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx).

## Creare e distribuire un'app con criterio di gestione delle applicazioni mobili

-   **Passaggio 1:** Ottenere il collegamento a un'app gestita da criteri o creare un'app di cui è stato eseguito il wrapping.

-   **Passaggio 2:** Pubblicare l'app nello spazio di archiviazione cloud.

-   **Passaggio 3:** Creare criteri di gestione delle applicazioni mobili.

-   **Passaggio 4:** Distribuire l'app, selezionando l'opzione per associarla con i criteri di gestione delle applicazioni mobili.

-   **Passaggio 5:** Monitorare la distribuzione dell'app.

## **Passaggio 1:** Ottenere il collegamento a un'app gestita da criteri o creare un'app di cui è stata eseguita la disposizione testo.

-   **Per ottenere un collegamento a un'app gestita da criteri**: nell'App Store trovare e prendere nota dell'URL dell'app gestita da criteri che si vuole distribuire.

    Ad esempio, l'URL dell'app Microsoft Word per iPad è **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**

-   **Per creare un'app di cui è stata eseguita la disposizione testo:** usare le informazioni negli argomenti [Preparare le app iOS per la gestione delle applicazioni mobili con lo strumento per la disposizione testo delle app di Microsoft Intune](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [Preparare le app Android per la gestione delle applicazioni mobili con lo strumento per la disposizione testo delle app di Microsoft Intune](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

    Lo strumento crea un'app elaborata che verrà usata quando si pubblica l'app nello spazio di archiviazione cloud.

## **Passaggio 2:** Pubblicare l'app nello spazio di archiviazione cloud
Quando si pubblica un'app gestita, le procedure possono essere diverse a seconda che l'app sia gestita tramite criteri o elaborata con lo strumento di wrapping delle app di Microsoft Intune per iOS.

#### Per pubblicare un'app gestita da criteri

1.  Quando si è pronti per caricare l'app nello spazio di archiviazione cloud, seguire le istruzioni in [Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Per le app iOS, selezionare **App iOS gestita dall'App Store**in **Selezionare il modo in cui questo software viene fornito ai dispositivi**.

    Per le app Android, selezionare **Collegamento esterno**.

3.  In **Specificare l'URL**immettere l'URL dell'app gestita da criteri di cui si è preso nota in precedenza.

Dopo aver completato il caricamento, verrà visualizzato **Sì** per **criteri di gestione delle app** nella pagina **Proprietà software** dell'app caricata.

Dopo avere verificato il corretto caricamento dell'app, continuare con il passaggio 3.

#### Per pubblicare un'app elaborata con lo strumento di wrapping delle app di Microsoft Intune

1.  Quando si è pronti per caricare l'app nello spazio di archiviazione cloud, seguire le istruzioni in [Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Selezionare **Programma di installazione software** in **Selezionare il modo in cui questo software viene fornito ai dispositivi**.

3.  Selezionare **Pacchetto app iOS (file &#42;.ipa)** in **Selezionare il tipo di file del programma di installazione software**.

Dopo aver completato il caricamento, verrà visualizzato **Sì** per **criteri di gestione delle app** nella pagina **Proprietà software** dell'app caricata.

Dopo avere verificato il corretto caricamento dell'app, continuare con il passaggio 3.

## **Passaggio 3:** Creare criteri di gestione delle applicazioni mobili

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** &gt; **Panoramica** &gt; **Aggiungi criterio**.

2.  Configurare e distribuire uno dei seguenti criteri **Software** in base al tipo di dispositivo per cui si desidera configurare le app:

    -   **Criteri di gestione per applicazioni mobili (Android 4 e versioni successive)**

    -   **Criteri di gestione per applicazioni mobili (iOS 7 e versioni successive)**

    È possibile usare le impostazioni consigliate o personalizzare le impostazioni. For altri dettagli, vedere [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Configurare le seguenti impostazioni come necessario: Le opzioni possono variare a seconda del tipo di dispositivo per il quale si sta configurando il criterio.

|Nome impostazione|Dettagli|
    |---------|--------------------|
    |**Nome**|Specificare un nome per i criteri.|
    |**Descrizione**|Specificare una descrizione per i criteri (facoltativo).|
    |**Limitare il contenuto Web per la visualizzazione in Managed Browser dell'azienda**|Quando questa impostazione è abilitata, tutti i collegamenti nell'app verranno aperti in Managed Browser. Per usare questa opzione, è necessario avere distribuito l'app nei dispositivi.|
    |**Impedisci backup in Android** o **Impedisci backup in iTunes e iCloud**|Disabilita il backup delle informazioni presenti nell'app.|
    |**Consenti all'app di trasferire i dati ad altre app**|Specifica le app a cui questa app può inviare dati. È possibile scegliere di non consentire il trasferimento dei dati alle app, di trasferire i dati solo alle altre app gestite oppure di consentire il trasferimento a qualsiasi app. Questa impostazione non controlla l'uso della funzionalità **Apri in** nei dispositivi mobili.<br /><br />Ad esempio, se non si consente il trasferimento dei dati, questo viene limitato in servizi come la messaggistica SMS, l'assegnazione di immagini ai contatti e la pubblicazione di post su Facebook o Twitter.<br /><br />Nei dispositivi iOS, per impedire il trasferimento di documenti tra app gestite e non gestite, è necessario anche configurare e distribuire un criterio di sicurezza dei dispositivi mobili che disabilita l'impostazione **Consenti documenti gestiti in altre app non gestite**. Se si sceglie il trasferimento dei dati solo ad altre app gestite, i visualizzatori di file PDF e di immagini di Intune (se distribuiti) verranno usati per aprire il contenuto dei tipi associati.<br /><br />Inoltre, se si imposta l'opzione su **App gestite da criteri** o **Nessuna**, la funzionalità di iOS 9 che consente a Ricerca Spotlight di cercare i dati nelle app verrà bloccata.|
    |**Consenti all'app di ricevere i dati da altre app**|Specifica le app da cui questa app può ricevere dati. È possibile scegliere di non consentire il trasferimento dei dati dalle app, di trasferire i dati solo da altre app gestite oppure di consentire il trasferimento da qualsiasi app.<br /><br />I dati verranno considerati come dati aziendali e protetti dai criteri per le app iOS che supportano più identità dove Intune applica solo le impostazioni di gestione agli account aziendali o ai dati nell'app, per un dispositivo registrato a cui sono applicati criteri di gestione delle applicazioni mobili, quando un utente accede ai dati da un'app che non è gestita da criteri di gestione delle applicazioni mobili.|
    |**Impedisci "Salva con nome"**|Disabilita l'uso dell'opzione **Salva con nome** per salvare i dati in posizioni di archiviazione cloud personali (ad esempio OneDrive Personal o Dropbox) in tutte le app che usano questi criteri.|
    |**Limita le operazioni taglia, copia e incolla con le altre app**|Specifica come è possibile usare le operazioni taglia, copia e incolla con l'app. È possibile scegliere tra:<br /><br />**Bloccato**: non consente le operazioni taglia, copia e incolla tra questa app e altre app.<br /><br />**App gestite da criteri**: consente le operazioni taglia, copia e incolla solo tra questa app e altre app gestite.<br /><br />**App gestite da criteri con Incolla in**: consente di incollare i dati tagliati o copiati da questa app solo in altre app gestite. I dati tagliati o copiati da qualsiasi app possono essere incollati in questa app.<br /><br />**Qualsiasi app**: nessuna restrizione per le operazioni taglia, copia e incolla in o da questa app.<br /><br />Per copiare o incollare i dati tra app gestite, in entrambe le app deve essere configurata l'impostazione **App gestite da criteri** o **App gestite da criteri con Incolla in**.|
    |**Richiedi PIN semplice per l'accesso**|Richiede all'utente di immettere un numero PIN scelto per usare questa app. All'utente verrà richiesto di impostare questo numero alla prima esecuzione dell'app.|
    |**Numero di tentativi prima della reimpostazione del PIN**|Specificare il numero di tentativi di immissione del PIN che è possibile effettuare prima che all'utente venga richiesto di reimpostare il PIN.|
    |**Richiedi credenziali aziendali per l'accesso**|Richiede all'utente di immettere le informazioni di accesso aziendali per poter accedere all'app.|
    |**Richiedi la conformità del dispositivo ai criteri aziendali per l'accesso**|Consente l'uso dell'app solo se il dispositivo non è jailbroken o rooted.|
    |**Controlla di nuovo i requisiti di accesso dopo (minuti)**|Nel campo **Timeout** specificare il periodo di tempo che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app dopo l'avvio.|
    |**Periodo di prova offline**|Se il dispositivo è offline specificare il periodo di tempo che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.|
    |**Crittografa dati app**|Specifica che tutti i dati associati a questa app verranno crittografati, compresi i dati archiviati esternamente come, ad esempio, i dati delle schede SD.<br /><br />**Crittografia per iOS**<br /><br />Per le app associate ai criteri di gestione delle applicazioni mobili di Intune, i dati vengono crittografati a riposo usando la crittografia a livello di dispositivo fornita dal sistema operativo. Ciò viene abilitato tramite i criteri PIN del dispositivo che devono essere impostati dall'amministratore IT. Quando viene richiesto un PIN, i dati verranno crittografati in base alle impostazioni nei criteri di gestione delle applicazioni mobili. Come indicato nella documentazione di Apple [i moduli usati da iOS 7 sono conformi agli standard FIPS 140-2](http://support.apple.com/en-us/HT202739).<br /><br />**Crittografia per Android**<br /><br />Per le app associate ai criteri di gestione delle applicazioni mobili di Intune, la crittografia viene fornita da Microsoft. I dati vengono crittografati in modo sincrono durante le operazioni di I/O dei file in base all'impostazione nei criteri di gestione delle applicazioni mobili. Le app gestite su Android usano la crittografia AES-128 in modalità CBC con le librerie di crittografia della piattaforma. Il metodo di crittografia non è conforme agli standard FIPS 140-2. Il contenuto nell'archivio del dispositivo verrà sempre crittografato.|
    |**Blocca acquisizione schermo** (solo per dispositivi Android)|Specifica che le funzionalità di acquisizione schermo del dispositivo vengono bloccate quando si usa questa app.|

4.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri** .

## **Passaggio 4:** Associare l'app con i criteri di gestione delle applicazioni mobili e quindi distribuirla
Distribuire l'app assicurandosi di selezionare i criteri di gestione delle applicazioni mobili nella pagina **Gestione delle app mobili** per associare i criteri all'app.

Per informazioni dettagliate, vedere [Distribuire le app in Microsoft Intune](deploy-apps.md).

> [!IMPORTANT]
> Per i dispositivi che eseguono sistemi operativi precedenti a iOS 7.1, i criteri associati non verranno rimossi quando si disinstalla l'app.
> 
> Se viene annullata la registrazione del dispositivo da Intune, i criteri non verranno rimossi dalle app. Tutte le app a cui erano stati applicati i criteri conserveranno le impostazioni dei criteri anche dopo la disinstallazione e reinstallazione dell'app.

### Cosa fare quando un'app è già stata distribuita nei dispositivi
Potrebbero esserci situazioni in cui si distribuisce un'app e un utente o un dispositivo ha già una versione non gestita di quell'app, ad esempio se un utente ha installato Microsoft Word dall'app store.

In questo caso, è necessario chiedere all'utente di disinstallare manualmente la versione non gestita in modo da poter installare la versione gestita che è stata configurata.

Tuttavia, per i dispositivi che eseguono iOS 9 e versioni successive, Intune chiederà automaticamente all'utente l'autorizzazione ad assumere la gestione dell'app esistente. Se l'utente accetta, l'app verrà gestita da Intune e verranno inoltre applicati tutti i criteri di gestione delle applicazione mobili associati all'app.

> [!TIP]
> Se il dispositivo è in modalità di supervisione, Intune assumerà la gestione dell'app esistente senza chiedere agli utenti l'autorizzazione.

## **Passaggio 5:** Monitorare la distribuzione dell'app.
Dopo aver creato e distribuito un'app associata ai criterio di gestione delle applicazioni mobili, usare le procedure seguenti per monitorare l'app e risolvere eventuali conflitti di criteri.

#### Per visualizzare lo stato della distribuzione

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Gruppi** &gt; **Panoramica**.

2.  Eseguire uno dei passaggi seguenti:

    -   Fare clic su **Tutti gli utenti**, quindi fare doppio clic sull'utente di cui si vuole esaminare i dispositivi. Nella pagina **Proprietà utente** fare clic su **Dispositivi**, quindi fare doppio clic sul dispositivo da esaminare.

    -   Fare clic su **Tutti i dispositivi** &gt; **Tutti i dispositivi mobili**. Nella pagina **Proprietà gruppo dispositivi** fare clic su **Dispositivi**, quindi fare doppio clic sul dispositivo da esaminare.

3.  Nella pagina **Proprietà del dispositivo mobile** fare clic su **Criteri** per visualizzare un elenco dei criteri di gestione delle applicazioni mobili che sono stati distribuiti nel dispositivo.

4.  Selezionare i criteri di gestione delle applicazioni mobili di cui si vuole visualizzare lo stato. È possibile visualizzare i dettagli dei criteri nel riquadro inferiore ed espandere il relativo nodo per visualizzarne le impostazioni.

5.  Nella colonna **Stato** dei criteri di gestione delle applicazioni mobili verranno visualizzati **Conforme**, **È conforme (in sospeso)**o **Errore** . Se una o più impostazioni dei criteri selezionati sono in conflitto, in questo campo verrà visualizzato **Errore** .

6.  Dopo aver identificato un conflitto, è possibile modificare le impostazioni dei criteri in conflitto per usare la stessa impostazione o distribuire un solo criterio per l'app e l'utente.

### Come vengono risolti i conflitti di criteri
Quando si verifica un conflitto dei criteri di gestione delle applicazione mobili nella prima distribuzione all'utente o al dispositivo, il valore di impostazione specifico in conflitto verrà rimosso dal criterio distribuito all'app e l'app userà il valore predefinito.

Quando si verifica un conflitto dei criteri di gestione delle applicazione mobili nelle successive distribuzioni all'utente o al dispositivo, il valore di impostazione specifico in conflitto non verrà aggiornato nei criteri distribuiti all'app e l'app userà il valore esistente per tale impostazione.

Nei casi in cui il dispositivo o l'utente riceva due criteri in conflitto, si applica il comportamento seguente:

-   Se un criterio è già stato distribuito al dispositivo, le impostazioni di criteri esistenti non vengono sovrascritte.

-   Se al dispositivo non è stato ancora distribuito alcun criterio e vengono distribuite due impostazioni in conflitto, viene usata l'impostazione predefinita del dispositivo.





<!--HONumber=May16_HO1-->


