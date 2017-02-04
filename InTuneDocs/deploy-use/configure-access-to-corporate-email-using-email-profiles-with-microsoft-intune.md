---
title: Accedere alla posta elettronica aziendale con i profili di posta elettronica | Documentazione Microsoft
description: "È possibile usare le impostazioni del profilo di posta elettronica per configurare le impostazioni di accesso alla posta elettronica per client di posta elettronica specifici sui dispositivi mobili."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 519d3f475e158391b08ab4e51f9410b7bdefcd4c


---

# <a name="configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune"></a>Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Nel sistema operativo di molte piattaforme per dispositivi mobili è incluso un client di posta elettronica nativo. Questo argomento descrive come impostare alcuni di questi client usando profili di posta elettronica.

È possibile usare le impostazioni del profilo di posta elettronica per configurare le impostazioni di accesso alla posta elettronica per client di posta specifici sui dispositivi mobili. Nelle piattaforme supportate è possibile impostare i client di posta elettronica nativi con Microsoft Intune per consentire agli utenti di accedere alla posta elettronica aziendale da dispositivi personali senza alcuna configurazione aggiuntiva.

Per una maggiore prevenzione della perdita dei dati, scegliere [Accesso condizionale](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), opzione che controlla l'accesso alla posta elettronica degli utenti di qualsiasi client di posta elettronica, inclusi i client nativi di posta elettronica.

Gli amministratori IT o gli utenti possono anche scegliere di installare client di posta elettronica alternativi, ad esempio Microsoft Outlook per Android o iOS. È possibile che questi client di posta elettronica non supportino i profili di posta elettronica e non possano essere configurati mediante profili di posta elettronica di Intune.  

È possibile usare i profili di posta elettronica per configurare il client di posta elettronica nativo nei tipi di dispositivi seguenti:
-   Windows Phone 8.1 e versioni successive
-   Windows 10 (desktop), Windows 10 Mobile e versioni successive
-   iOS 8.0 e versioni successive
-   Samsung KNOX Standard 4.0 e versioni successive
-   Android for Work

>[!NOTE]
>Intune offre due profili di posta elettronica Android for Work, uno per Gmail e uno per Nine Work. Queste app sono disponibili in Google Play Store e possono connettersi a Exchange. Per abilitare la connettività della posta elettronica, distribuire una di queste app nei dispositivi dell'utente. In seguito creare e distribuire il profilo corrispondente.

Oltre a configurare un account di posta elettronica sul dispositivo, è possibile impostare il numero di messaggi di posta elettronica da sincronizzare. A seconda del tipo di dispositivo, è possibile impostare anche i tipi di contenuto da sincronizzare.

>[!NOTE]
>
>Se l'utente ha installato un profilo di posta elettronica prima di configurare un profilo con Intune, il risultato della distribuzione del profilo di posta elettronica di Intune dipende dalla piattaforma del dispositivo:

>**iOS**: un profilo di posta elettronica esistente duplicato viene individuato in base al nome host e all'indirizzo di posta elettronica. Il profilo di posta elettronica duplicato creato dall'utente blocca la distribuzione di un profilo creato dall'amministratore di Intune. Si tratta di un problema comune poiché gli utenti di iOS in genere creano un profilo di posta elettronica e poi eseguono la registrazione. Il portale aziendale comunica all'utente che esiste un problema di conformità perché il profilo di posta elettronica è stato configurato manualmente. All'utente viene quindi richiesto di rimuovere il profilo. L'utente deve rimuovere il proprio profilo di posta elettronica per consentire l'impostazione del profilo di Intune. Per evitare il problema, indicare agli utenti di eseguire la registrazione prima di installare un profilo di posta elettronica e di consentire a Intune di impostarlo.

>**Windows**: un profilo di posta elettronica esistente duplicato viene individuato in base al nome host e all'indirizzo di posta elettronica. Intune sovrascrive il profilo di posta elettronica esistente creato dall'utente.

>**Samsung KNOX**: un profilo di posta elettronica esistente duplicato viene individuato sulla base dell'indirizzo di posta elettronica e viene sovrascritto con il profilo di Intune. Se l'utente imposta tale account, questo verrà sovrascritto nuovamente dal profilo di Intune. Questo comportamento può confondere l'utente.

>Poiché Samsung KNOX non usa il nome host per identificare il profilo, si consiglia di non creare diversi profili di posta elettronica da usare con lo stesso indirizzo di posta elettronica su host diversi perché tali profili si sovrascrivono a vicenda.

>**Android for Work**: il profilo di Intune è applicabile solo ad app di posta elettronica specifiche nel profilo di lavoro del dispositivo. Non ha effetti sulla configurazione della posta elettronica nel profilo utente del dispositivo.


## <a name="secure-email-profiles"></a>Proteggere i profili di posta elettronica
È possibile proteggere i profili di posta elettronica mediante un certificato o una password.

### <a name="certificates"></a>Certificati
Quando si crea il profilo di posta elettronica, si sceglie un profilo di certificato creato in precedenza in Intune. Questo profilo, noto come certificato di identità, viene usato per eseguire l'autenticazione in base a un profilo di certificato attendibile (o certificato radice) per stabilire se il dispositivo dell'utente è autorizzato alla connessione. Il certificato attendibile viene distribuito al computer che autentica la connessione alla posta elettronica che è in genere il server di posta elettronica nativo.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteggere l'accesso alle risorse con i profili certificato).

### <a name="user-name-and-password"></a>Nome utente e password
L'utente esegue l'autenticazione al server di posta elettronica nativo specificando nome utente e password.

Poiché la password non è contenuta nel profilo di posta elettronica, l'utente deve specificarla quando si connette alla posta elettronica.

### <a name="create-an-email-profile"></a>Creare un profilo di posta elettronica

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Aggiungi criterio**.

2.  Impostare uno dei tipi di criteri seguenti:

    -   **Profilo di posta elettronica per Samsung KNOX Standard (4.0 e versioni successive)**

    -   **Profilo di posta elettronica (iOS 8.0 e versioni successive)**

    -   **Profilo di posta elettronica (Windows Phone 8.1 e versioni successive)**

    -   **Profilo di posta elettronica (Windows 10 Desktop e Mobile e versioni successive)**

    -   **Profilo di posta elettronica (Android for Work - Gmail)**

    -   **Profilo di posta elettronica (Android for Work - Nine Work)**

    È possibile solo creare e distribuire criteri personalizzati dei profili di posta elettronica. Le impostazioni consigliate non sono disponibili.

3.  Usare la tabella seguente per configurare le impostazioni del profilo di posta elettronica:

|Nome impostazione | Altre informazioni|
| ----------- | --------------- |
    |**Nome**|Nome univoco per il profilo di posta elettronica.|
    |**Descrizione**|Descrizione che consente di identificare il profilo.|
    |**Host**|Nome host del server aziendale che ospita il servizio di posta elettronica nativo.|
    |**Nome account**|Nome dell'account di posta elettronica visualizzato nei dispositivi degli utenti.|
    |**Nome utente**|Si tratta dell'attributo in Active Directory (AD) o AD Azure che verrà usato per generare il nome utente per questo profilo di posta elettronica. Selezionare Indirizzo SMTP primario, ad esempio *user1@contoso.com* o Nome entità utente, ad esempio *utente1* o *user1@contoso.com*.|
    |**Indirizzo di posta elettronica**|Modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Indirizzo SMTP primario** per accedere a Exchange con l'indirizzo SMTP primario o **Nome entità utente** per usare il nome completo dell'entità come indirizzo di posta elettronica.|
    |**Metodo di autenticazione** (Android for Work, Samsung KNOX e iOS)|Selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione usato dal profilo di posta elettronica.|
    |**Selezionare un certificato client per l'autenticazione client (certificato di identità)** (Android for Work, Samsung KNOX e iOS)|Selezionare il certificato SCEP client creato in precedenza che verrà usato per autenticare la connessione di Exchange. Per altre informazioni su come usare i profili di certificato in Intune, vedere [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteggere l'accesso alle risorse con profili certificato). Questa opzione viene visualizzata solo quando il metodo di autenticazione è **Certificati**.|
    |**Usa S/MIME** (Samsung KNOX e iOS)|Consente di usare la crittografia S/MIME per inviare posta elettronica in uscita.|
    |**Certificato di firma** (Samsung KNOX e iOS)|Selezionare il certificato di firma che verrà usato per firmare il messaggio di posta elettronica in uscita. Questa opzione viene visualizzata solo quando si seleziona **Usa S/MIME**.|
    |**Numero di giorni di messaggi di posta elettronica da sincronizzare**|Il numero di giorni di posta elettronica che si vogliono sincronizzare. In alternativa, selezionare **Illimitata** per sincronizzare tutta la posta elettronica disponibile.|
    |**Pianificazione sincronizzazione** (Android for Work, Samsung KNOX, Windows Phone 8 e versioni successive, Windows 10)|Selezionare la pianificazione in base a cui i dispositivi sincronizzeranno i dati dal server Exchange. È anche possibile selezionare **Quando arrivano i messaggi**, per sincronizzare i dati non appena arrivano, oppure **Manuale**, per consentire all'utente del dispositivo di avviare la sincronizzazione.|
    |**Usa SSL**|Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange. Per i dispositivi che eseguono Samsung KNOX 4.0 o versioni successive, è necessario esportare il certificato SSL di Exchange Server e distribuirlo come profilo di certificato attendibile Android in Intune. Intune non supporta l'accesso a questo certificato se è stato installato in Exchange Server con altre procedure.|
    |**Tipo di contenuti da sincronizzare** (tutte le piattaforme tranne Android for Work, Gmail)|Selezionare i tipi di contenuto da sincronizzare nei dispositivi.|
    |**Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti** (solo iOS)|Consente all'utente di selezionare questo profilo come account predefinito per l'invio di posta elettronica e consente ad applicazioni di terze parti di aprire la posta elettronica nella relativa app nativa, ad esempio per allegare file ai messaggi.|

> [!IMPORTANT]
>
> Se è stato distribuito un profilo di posta elettronica e quindi si vogliono modificare i valori di **Host** o **Indirizzo di posta elettronica** è necessario eliminare il profilo di posta elettronica e crearne uno nuovo con i valori necessari.

4.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri** .

## <a name="deploy-the-policy"></a>Distribuire i criteri

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire e quindi scegliere **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   **Per distribuire il criterio**, selezionare uno o più gruppi a cui lo si vuole distribuire e quindi scegliere **Aggiungi** &gt; **OK**.

    -   **Per chiudere la finestra di dialogo senza distribuirlo**, scegliere **Annulla**.

Un riepilogo dello stato e gli avvisi visualizzati nella pagina **Panoramica** dell'area di lavoro **Criteri** consentono di identificare i problemi relativi ai criteri che richiedono attenzione. Un riepilogo dello stato viene visualizzato anche nell'area di lavoro Dashboard.

> [!NOTE]
> - Per Android for Work, assicurarsi di distribuire anche le app di Gmail o Nine Work, oltre al profilo di posta elettronica appropriato.
> - Per rimuovere un profilo di posta elettronica da un dispositivo, modificare la distribuzione e rimuovere tutti i gruppi di cui il dispositivo è membro.



<!--HONumber=Dec16_HO2-->


