---
title: Configurare i criteri MAM nella console di Intune | Microsoft Docs
description: "I criteri di gestione delle applicazioni mobili in Microsoft Intune consentono di modificare la funzionalità delle app distribuite per allinearle ai criteri aziendali di conformità e sicurezza."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 65b2eb20aea4bbadba9d470590b6c344ac37b9f5
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console"></a>Configurare e distribuire criteri di gestione delle applicazioni mobili nella console di Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I criteri di gestione delle applicazioni mobili (MAM, Mobile Application Management) in Microsoft Intune consentono di modificare la funzionalità delle app distribuite per allinearle ai criteri aziendali di conformità e sicurezza. Ad esempio, è possibile limitare le operazioni Taglia, Copia e Incolla in un'app gestita oppure configurare un'app per aprire tutti i collegamenti Web in Managed Browser.

I criteri di gestione delle applicazioni mobili supportano:

-   Dispositivi che eseguono Android 4 e versioni successive

-   Dispositivi che eseguono iOS 8.0 e versioni successive.

> [!TIP]
> I criteri di gestione delle applicazioni mobili supportano i dispositivi registrati con Intune.
>
> Per informazioni su come creare criteri di gestione delle app per i dispositivi non gestiti da Intune, vedere [Proteggere i dati delle app usando i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

A differenza degli altri criteri di Intune, i criteri di gestione delle applicazioni mobili non vengono distribuiti direttamente ma, al contrario, è possibile associare i criteri all'app che si vuole limitare. Le impostazioni specificate saranno effettive dopo la distribuzione e l'installazione dell'app nei dispositivi.

Per applicare restrizioni a un'app, questa deve includere Microsoft Intune App SDK. Esistono tre metodi per ottenere questo tipo di app:

-   **Usare un'app gestita da criteri**. Un'app gestita da criteri include App SDK. Per aggiungere questo tipo di applicazione, è possibile specificare un collegamento all'app da un archivio di app, ad esempio l'iTunes store o Google Play. Non sono richieste ulteriori elaborazioni per questo tipo di app. Per altre informazioni, vedere l'elenco delle [app che è possibile usare con i criteri di gestione delle applicazioni mobili di Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

-   **Usare un'app di cui è stato eseguito il wrapping**. Un'app di cui è stato eseguito il wrapping è un'app che è stata riassemblata in modo da includere App SDK usando lo strumento di wrapping delle app di Microsoft Intune. Questo strumento viene in genere usato per elaborare le app aziendali create internamente. Non può essere usato per elaborare app scaricate dall'App Store. Per altre informazioni, vedere [Preparare le app per iOS per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [Preparare le app per Android per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

- **Sviluppare una propria app che includa Intune App SDK**. Intune App SDK consente di integrare in un'app funzionalità di gestione specifiche durante la fase di sviluppo. Per altre informazioni, vedere [Panoramica di Intune App SDK](/intune-classic/develop/intune-app-sdk).

Per informazioni sulla scelta tra lo strumento di wrapping delle app e Intune App SDK, vedere [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

Alcune app gestite, ad esempio l'app Outlook per iOS e Android, supportano *più identità*. Questo significa che Intune si applica solo alle impostazioni di gestione di account aziendali o dati all'interno dell'applicazione.

Ad esempio, utilizzando Outlook app:

-   Se l'utente configura un account di posta elettronica aziendale e uno personale, Intune applica le impostazioni di gestione soltanto all'account aziendale e non gestisce l'account personale.

-   Se il dispositivo viene ritirato o ne viene annullata la registrazione, dal dispositivo vengono rimossi solo i dati aziendali di Outlook.

-   L'account aziendale deve essere lo stesso account specificato durante la registrazione del dispositivo con Intune.

> [!TIP]
> Se si usa Intune con Configuration Manager, vedere [Come controllare le app usando i criteri di gestione delle applicazioni mobili in Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx).

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>Creare e distribuire un'app con criterio di gestione delle applicazioni mobili

-   **Passaggio 1:** Ottenere il collegamento a un'app gestita da criteri, creare un'app sottoposta a wrapping o usare Intune App SDK per sviluppare un'app abilitata per MAM.

-   **Passaggio 2:** Pubblicare l'app nello spazio di archiviazione cloud.

-   **Passaggio 3:** Creare criteri di gestione delle applicazioni mobili.

-   **Passaggio 4:** Associare l'app con i criteri di gestione delle applicazioni mobili e quindi distribuirla.

-   **Passaggio 5:** Monitorare la distribuzione dell'app.

## <a name="step-1-get-the-link-to-a-policy-managed-app-create-a-wrapped-app-or-use-the-intune-app-sdk-to-write-a-mam-enabled-app"></a>Passaggio 1: Ottenere il collegamento a un'app gestita da criteri, creare un'app sottoposta a wrapping o usare Intune App SDK per sviluppare un'app abilitata per MAM

Nell'App Store trovare e prendere nota dell'URL dell'app gestita da criteri che si vuole distribuire. Ad esempio, l'URL dell'app Microsoft Word per iPad è **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.


## <a name="step-2-publish-the-app-to-your-cloud-storage-space"></a>Passaggio 2: Pubblicare l'app nello spazio di archiviazione cloud
Quando si pubblica un'app gestita, le procedure possono essere diverse a seconda che l'app sia gestita tramite criteri o elaborata con lo strumento di wrapping delle app di Microsoft Intune per iOS.

#### <a name="to-publish-a-policy-managed-app"></a>Per pubblicare un'app gestita da criteri

1.  Quando si è pronti per caricare l'app nello spazio di archiviazione cloud, seguire le istruzioni in [Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)

2.  Per le app iOS, selezionare **App iOS gestita dall'App Store** in **Selezionare il modo in cui questo software viene fornito ai dispositivi**.

    Per le app Android, selezionare **Collegamento esterno**.

3.  In **Specificare l'URL**immettere l'URL dell'app gestita da criteri di cui si è preso nota in precedenza.

Dopo aver completato il caricamento, verrà visualizzato **Sì** per **Criteri di gestione delle app** nella pagina **Proprietà software** dell'app caricata.

Dopo avere verificato il corretto caricamento dell'app, continuare con il passaggio 3.

#### <a name="to-publish-an-app-that-was-processed-through-the-microsoft-intune-app-wrapping-tool"></a>Per pubblicare un'app elaborata con lo strumento di wrapping delle app di Microsoft Intune

1.  Quando si è pronti per caricare l'app nello spazio di archiviazione cloud, seguire le istruzioni in [Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)

2.  Selezionare **Programma di installazione software** in **Selezionare il modo in cui questo software viene fornito ai dispositivi**.

3.  Selezionare **Pacchetto app iOS (file &#42;.ipa)** in **Selezionare il tipo di file del programma di installazione software**.

Dopo aver completato il caricamento, verrà visualizzato **Sì** per **Criteri di gestione delle app** nella pagina **Proprietà software** dell'app caricata.

Dopo avere verificato il corretto caricamento dell'app, continuare con il passaggio 3.

## <a name="step-3-create-a-mobile-application-management-policy"></a>Passaggio 3: Creare criteri di gestione delle applicazioni mobili

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Panoramica** &gt; **Aggiungi criterio**.

2.  Configurare e distribuire uno dei seguenti criteri **Software** in base al tipo di dispositivo per cui si vuole configurare le app:

    -   **Criteri di gestione per applicazioni mobili (Android 4 e versioni successive)**

    -   **Criteri di gestione di applicazioni mobili (iOS 8.0 e versioni successive)**

    È possibile usare le impostazioni consigliate o personalizzare le impostazioni. Per i dettagli vedere [Manage settings and features on your devices with Microsoft Intune policies](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) (Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune).

3.  Configurare le seguenti impostazioni come necessario: Le opzioni possono variare a seconda del tipo di dispositivo per il quale si sta configurando il criterio.

|Nome impostazione|Dettagli|
    |---------|--------------------|
    |**Nome**|Specificare un nome per i criteri.|
    |**Descrizione**|Specificare una descrizione per i criteri (facoltativo).|
    |**Limitare il contenuto Web per la visualizzazione in Managed Browser dell'azienda**|Quando questa impostazione è abilitata, tutti i collegamenti presenti nell'app verranno aperti in Managed Browser. Per usare questa opzione, è necessario avere distribuito l'app nei dispositivi.|
    |**Impedisci backup in Android** o **Impedisci backup in iTunes e iCloud**|Questa impostazione disabilita il backup delle informazioni presenti nell'app.|
    |**Consenti all'app di trasferire i dati ad altre app**|Questa impostazione specifica le app a cui l'app in questione può inviare dati. È possibile scegliere di non consentire il trasferimento dei dati alle app, di trasferire i dati solo alle altre app gestite oppure di consentire il trasferimento a qualsiasi app. <br /><br />Ad esempio, se non si consente il trasferimento dei dati, questo viene limitato in servizi come la messaggistica SMS, l'assegnazione di immagini ai contatti e la pubblicazione di post su Facebook o Twitter.<br /><br />Nei dispositivi iOS, per impedire il trasferimento di documenti tra app gestite e non gestite, è necessario anche configurare e distribuire un criterio di sicurezza dei dispositivi mobili che disabilita l'impostazione **Consenti documenti gestiti in altre app non gestite**. Se si sceglie di consentire il trasferimento dei dati solo ad altre app gestite, i visualizzatori di file PDF e di immagini di Intune (se distribuiti) verranno usati per aprire il contenuto dei rispettivi tipi.<br /><br />Inoltre, se si imposta l'opzione su **App gestite da criteri** o **Nessuna**, la funzionalità di iOS 9 che consente a Ricerca Spotlight di cercare i dati nelle app verrà bloccata.<br><br>Questa impostazione non controlla l'uso della funzionalità Apri in nei dispositivi mobili. Per gestire la funzionalità Apri in, vedere [Gestire il trasferimento di dati tra app iOS con Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).|
    |**Consenti all'app di ricevere i dati da altre app**|Questa impostazione specifica le app da cui questa app può ricevere dati. È possibile scegliere di non consentire il trasferimento dei dati dalle app, di trasferire i dati solo da altre app gestite oppure di consentire il trasferimento da qualsiasi app.<br /><br />Quando un utente accede ai dati da un'app non gestita da criteri di gestione delle applicazioni mobili, i dati verranno considerati come dati aziendali e saranno protetti dai criteri. Questo si applica ad app iOS che supportano più identità (dove Intune applica le impostazioni di gestione solo ai dati o agli account aziendali presenti nell'app). In alternativa, si applica a un dispositivo registrato con criteri di gestione delle applicazioni mobili.|
    |**Impedisci "Salva con nome"**|Questa impostazione disabilita l'uso dell'opzione **Salva con nome** per salvare i dati in posizioni di archiviazione cloud personali (ad esempio OneDrive o Dropbox) nelle app che usano questi criteri.|
    |**Limita le operazioni taglia, copia e incolla con le altre app**|Questa impostazione specifica come è possibile usare le operazioni Taglia, Copia e Incolla con l'app. È possibile scegliere tra:<br /><br />**Bloccato**. Non consente le operazioni Taglia, Copia e Incolla tra questa app e altre app.<br /><br />**App gestite da criteri**. Consente le operazioni Taglia, Copia e Incolla solo tra questa app e altre app gestite.<br /><br />**App gestite da criteri con Incolla in**. I dati tagliati o copiati da questa app possono essere incollati solo in altre app gestite. I dati tagliati o copiati da qualsiasi app possono essere incollati in questa app.<br /><br />**Qualsiasi app**. Nessuna restrizione per le operazioni Taglia, Copia e Incolla in o da questa app.<br /><br />Per copiare o incollare i dati tra app gestite, in entrambe le app deve essere configurata l'impostazione **App gestite da criteri** o **App gestite da criteri con Incolla in**.|
    |**Richiedi PIN semplice per l'accesso**|Questa impostazione richiede all'utente di immettere un PIN specificato per l'uso dell'app. All'utente verrà richiesto di impostare questo numero alla prima esecuzione dell'app.|
    |**Numero di tentativi prima della reimpostazione del PIN**|Specificare il numero di tentativi di immissione del PIN che è possibile effettuare prima che all'utente venga richiesto di reimpostare il PIN.|
    |**Richiedi credenziali aziendali per l'accesso**|Questa impostazione richiede all'utente di immettere le informazioni di accesso aziendali per poter accedere all'app.|
    |**Richiedi la conformità del dispositivo ai criteri aziendali per l'accesso**|Questa impostazione consente l'uso dell'app solo se il dispositivo non è jailbroken o rooted.|
    |**Controlla di nuovo i requisiti di accesso dopo (minuti)**|Nel campo **Timeout** specificare il periodo di tempo che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app dopo l'apertura.|
    |**Periodo di prova offline**|Se il dispositivo è offline specificare il periodo di tempo che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.|
    |**Crittografa dati app**|Questa impostazione specifica che tutti i dati associati all'app verranno crittografati. Sono inclusi i dati archiviati esternamente, ad esempio i dati delle schede SD.<br /><br />**Crittografia per iOS**<br /><br />Per le app associate ai criteri di gestione delle applicazioni mobili di Intune, i dati vengono crittografati a riposo mediante la crittografia a livello di dispositivo fornita dal sistema operativo. Questo viene abilitato tramite i criteri PIN del dispositivo impostati dall'amministratore IT. Quando viene richiesto un PIN, i dati verranno crittografati in base alle impostazioni nei criteri di gestione delle applicazioni mobili. Come indicato nella documentazione di Apple, [i moduli usati da iOS sono dotati di certificazione FIPS 140-2](http://support.apple.com/HT202739).<br /><br />**Crittografia per Android**<br /><br />Per le app associate ai criteri di gestione delle applicazioni mobili di Intune, la crittografia viene fornita da Microsoft. I dati vengono crittografati in modo sincrono durante le operazioni di I/O file.  Il contenuto nell'archivio del dispositivo verrà sempre crittografato. Il metodo di crittografia è compatibile con FIPS 140-2 solo per i dispositivi Samsung KNOX.|
    |**Blocca acquisizione schermo** (solo per dispositivi Android)|Questa impostazione specifica che le funzionalità di acquisizione schermo del dispositivo vengono bloccate quando un utente usa l'app.|

4. Al termine, scegliere **Salva criterio**.

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri**.

## <a name="step-4-associate-the-app-with-a-mobile-application-management-policy-and-then-deploy-the-app"></a>Passaggio 4: Associare l'app ai criteri di gestione delle applicazioni mobili e quindi distribuirla
Verificare di selezionare i criteri di gestione delle applicazioni mobili nella pagina **Gestione delle app mobili** della finestra di dialogo **Gestisci distribuzione** per associare i criteri all'app.

Per i dettagli vedere [Distribuire app in Microsoft Intune](deploy-apps.md).

> [!IMPORTANT]
> Se viene annullata la registrazione del dispositivo da Intune, i criteri non vengono rimossi dalle app. Nelle app con i criteri applicati verranno mantenute le impostazioni di questi ultimi anche dopo che l'app è stata disinstallata e reinstallata.

### <a name="what-to-do-when-an-app-is-already-deployed-on-devices"></a>Cosa fare quando un'app è già stata distribuita nei dispositivi
Possono verificarsi situazioni in cui si distribuisce un'app e un utente o un dispositivo ha già una versione non gestita dell'app installata. Ad esempio, è possibile che un utente abbia installato Microsoft Word dall'App Store.

In questo caso, è necessario chiedere all'utente di disinstallare manualmente la versione non gestita in modo da poter installare la versione gestita che è stata configurata.

Tuttavia, per i dispositivi che eseguono iOS 9 e versioni successive, Intune chiederà automaticamente all'utente l'autorizzazione ad assumere la gestione dell'app esistente. Se l'utente accetta, l'app verrà gestita da Intune e verranno inoltre applicati tutti i criteri di gestione delle applicazioni mobili associati a tale app.

> [!TIP]
> Se il dispositivo è in modalità di supervisione, Intune assumerà la gestione dell'app esistente senza chiedere l'autorizzazione dell'utente.

## <a name="step-5-monitor-the-app-deployment"></a>Passaggio 5: Monitorare la distribuzione dell'app
Dopo aver creato e distribuito un'app associata ai criteri di gestione delle applicazioni mobili, usare la procedura seguente per monitorare l'app e risolvere eventuali conflitti di criteri.

#### <a name="to-view-the-status-of-the-deployment"></a>Per visualizzare lo stato della distribuzione

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Gruppi** &gt; **Panoramica**.

2.  Eseguire uno dei passaggi seguenti:

    -   Scegliere **Tutti gli utenti** e fare doppio clic sull'utente di cui si vuole esaminare il dispositivo. Nella pagina **Proprietà utente** scegliere **Dispositivi** e quindi fare doppio clic sul dispositivo da esaminare.

    -   Scegliere **Tutti i dispositivi** &gt; **Tutti i dispositivi mobili**. Nella pagina **Proprietà gruppo dispositivi** scegliere **Dispositivi** e quindi fare doppio clic sul dispositivo che si vuole esaminare.

3.  Nella pagina **Proprietà del dispositivo mobile** scegliere **Criteri** per visualizzare un elenco dei criteri di gestione delle applicazioni mobili che sono stati distribuiti nel dispositivo.

4.  Selezionare i criteri di gestione delle applicazioni mobili di cui si vuole visualizzare lo stato. È possibile visualizzare i dettagli dei criteri nel riquadro inferiore ed espandere il relativo nodo per visualizzarne le impostazioni.

5.  Nella colonna **Stato** dei criteri di gestione delle applicazioni mobili verrà visualizzato **Conforme**, **È conforme (in sospeso)** o **Errore**. Se una o più impostazioni dei criteri selezionati sono in conflitto, in questo campo verrà visualizzato **Errore**.

6.  Dopo aver identificato un conflitto, è possibile modificare le impostazioni dei criteri in conflitto per usare la stessa impostazione o distribuire un solo criterio per l'app e l'utente.

### <a name="how-policy-conflicts-are-resolved"></a>Come vengono risolti i conflitti di criteri
Quando si verifica un conflitto dei criteri di gestione delle applicazioni mobili nella prima distribuzione all'utente o al dispositivo, il valore di impostazione specifico in conflitto verrà rimosso dai criteri distribuiti all'app. L'app userà un valore in conflitto incorporato.

Se nelle successive distribuzioni all'utente o al dispositivo si verifica un conflitto dei criteri di gestione delle applicazioni mobili, il valore di impostazione specifico in conflitto non verrà aggiornato nei criteri distribuiti all'app. L'app userà il valore esistente per tale impostazione.

Nei casi in cui il dispositivo o l'utente riceva due criteri in conflitto, si applica il comportamento seguente:

-   Se un criterio è già stato distribuito al dispositivo, le impostazioni di criteri esistenti non vengono sovrascritte.

-   Se al dispositivo non è stato ancora distribuito alcun criterio e vengono distribuite due impostazioni in conflitto, viene usata l'impostazione predefinita del dispositivo.

