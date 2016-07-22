---
title: Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 05/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8a3df01e9c02af7c43cdadc6d202bc6d74a000da
ms.openlocfilehash: d0fa235b7b25fe71a4e3b4b0bf68cd2db31b1f18


---

# Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune
Nel sistema operativo di molte piattaforme per dispositivi mobili è incluso un client di posta elettronica *nativo*.  Questo argomento descrive come configurare alcuni di questi client usando profili di posta elettronica.

Per una maggiore prevenzione sulla perdita dei dati (DLP, Data Loss Prevention), scegliere [Accesso condizionale](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) che controlla l'accesso alla posta elettronica degli utenti di qualsiasi client di posta elettronica, incluso client nativi di posta elettronica.

È possibile usare le impostazioni del profilo di posta elettronica per configurare le impostazioni di accesso alla posta elettronica per client di posta elettronica specifici sui dispositivi mobili.   Nel sistema operativo della maggior parte delle piattaforme per dispositivi mobili è incluso un client di posta elettronica *nativo*.  Nelle piattaforme supportate è possibile configurare i client di posta elettronica nativi con Microsoft Intune per consentire agli utenti di accedere alla loro posta elettronica aziendale da dispositivi personali senza alcuna installazione.  

Gli amministratori IT o gli utenti possono anche scegliere di installare client di posta elettronica alternativi, ad esempio Microsoft Outlook per Android o iOS.  Questi client di posta elettronica potrebbero non supportare i profili di posta elettronica e non possono essere configurati usando profili di posta elettronica di Microsoft Intune.  

È possibile usare i profili di posta elettronica per configurare il client di posta elettronica nativo nei tipi di dispositivi seguenti:
-   Windows Phone 8 e versioni successive
-   Windows 10 Desktop, Windows 10 Mobile e versioni successive
-   iOS 7.1 e versioni successive
-   Samsung KNOX Standard 4.0 e versioni successive


Oltre a configurare un account di posta elettronica sul dispositivo, è possibile configurare le impostazioni di sincronizzazione, ad esempio la quantità di posta elettronica da sincronizzare e, a seconda del tipo di dispositivo, i tipi di contenuto per la sincronizzazione.

## Proteggere i profili di posta elettronica
È possibile proteggere i profili di posta elettronica usando uno dei due metodi seguenti:

### Certificati
Quando si crea il profilo di posta elettronica, si sceglie un profilo di certificato creato in precedenza in Intune. Questo profilo, noto come certificato di identità, viene usato per eseguire l'autenticazione in base a un profilo di certificato attendibile (o certificato radice) per stabilire che il dispositivo dell'utente è autorizzato a connettersi. Il certificato attendibile viene distribuito al computer che autentica la connessione alla posta elettronica che è in genere il server di posta elettronica nativo.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteggere l'accesso alle risorse con i profili certificato).

### Nome utente e password
L'utente esegue l'autenticazione al server di posta elettronica nativo specificando nome utente e password.

La password non è contenuta nel profilo di posta elettronica, quindi l'utente dovrà specificarla quando si connette alla posta elettronica.

### Creare un profilo di posta elettronica

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** &gt; **Aggiungi criterio**.

2.  Configurare uno dei tipi di criteri seguenti:

    -   **Profilo di posta elettronica per Samsung KNOX Standard (4.0 e versioni successive)**

    -   **Profilo di posta elettronica (iOS 7.1 e versioni successive)**

    -   **Profilo di posta elettronica (Windows Phone 8 e versioni successive)**

    -   **Profilo di posta elettronica (Windows 10 Desktop e Mobile e versioni successive)**

    È possibile solo creare e distribuire criteri personalizzati dei profili di posta elettronica. Le impostazioni consigliate non sono disponibili.

3.  Usare la tabella seguente per configurare le impostazioni del profilo di posta elettronica:
    |Nome impostazione|Altre informazioni|
    |----------------|-----------------------------------------------------------------------------|
    |**Nome**|Nome univoco per il profilo di posta elettronica.|
    |**Descrizione**|Descrizione che consente di identificare il profilo.|
    |**Host**|Nome host del server aziendale che ospita il servizio di posta elettronica nativo.|
    |**Nome account**|Nome dell'account di posta elettronica visualizzato nei dispositivi degli utenti.|
    |**Nome utente**|Modalità con cui viene ottenuto il nome utente per l'account di posta elettronica. Selezionare **Nome utente** per un server Exchange locale o **Nome entità utente** per Office 365.|
    |**Indirizzo di posta elettronica**|Modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Indirizzo SMTP primario** per accedere a Exchange con l'indirizzo SMTP primario o **Nome entità utente** per usare il nome completo dell'entità come indirizzo di posta elettronica.|
    |**Metodo di autenticazione** (Samsung KNOX e iOS)|Selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione usato dal profilo di posta elettronica.|
    |**Selezionare un certificato client per l'autenticazione del client (certificato di identità)** (Samsung KNOX e iOS)|Selezionare il certificato SCEP client creato in precedenza che verrà usato per autenticare la connessione di Exchange. Per altre informazioni su come usare i profili di certificato in Intune, vedere [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteggere l'accesso alle risorse con profili certificato).<br /><br />Questa opzione viene visualizzata solo quando il metodo di autenticazione è **Certificati**.|
    |**Usa S/MIME** (Samsung KNOX e iOS)|Consente di usare la crittografia S/MIME per inviare posta elettronica in uscita.|
    |**Certificato di firma** (Samsung KNOX e iOS)|Selezionare il certificato di firma che verrà usato per firmare il messaggio di posta elettronica in uscita.<br /><br />Questa opzione viene visualizzata solo quando si seleziona **Usa S/MIME**.|
    |**Numero di giorni di messaggi di posta elettronica da sincronizzare**|Il numero di giorni di posta elettronica che si vuole sincronizzare o selezionare **Illimitata** per sincronizzare tutta la posta elettronica disponibile.|
    |**Pianificazione sincronizzazione** (Samsung KNOX, Windows Phone 8 e versioni successive, Windows 10)|Selezionare la pianificazione in base a cui i dispositivi sincronizzeranno i dati dal server di Exchange. È anche possibile selezionare **Quando arrivano i messaggi**, per sincronizzare i dati non appena arrivano, oppure **Manuale**, per consentire all'utente del dispositivo di avviare la sincronizzazione.|
    |**Usa SSL**|Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio di messaggi di posta elettronica, la ricezione di messaggi di posta elettronica e la comunicazione con il server Exchange.<br /><br />Per i dispositivi che eseguono Samsung KNOX 4.0 o versioni successive, è necessario esportare il certificato SSL di Exchange Server e distribuirlo come profilo di certificato attendibile Android in Intune. Intune non supporta l'accesso a questo certificato se è stato installato in Exchange Server con altre procedure.|
    |**Tipo di contenuti da sincronizzare**|Selezionare i tipi di contenuto da sincronizzare nei dispositivi.| 
    |**Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti** (solo iOS)|Consente all'utente di selezionare questo profilo come account predefinito per l'invio di posta elettronica e consente ad applicazioni di terze parti di aprire posta elettronica nella relativa app nativa, ad esempio per allegare file ai messaggi.|

    > [!IMPORTANT]
    > Se è stato distribuito un profilo di posta elettronica e quindi si vogliono modificare i valori di **Host** o **Indirizzo di posta elettronica** è necessario eliminare il profilo di posta elettronica e crearne uno nuovo con i valori necessari.

4.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri** .

## Distribuire i criteri

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire, quindi fare clic su **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   **Per distribuire il criterio**: selezionare uno o più gruppi in cui si vuole distribuire il criterio, quindi fare clic su **Aggiungi** &gt; **OK**.

    -   **Per chiudere la finestra di dialogo senza distribuire il criterio**, fare clic su **Annulla**.

Un riepilogo dello stato e gli avvisi visualizzati nella pagina **Panoramica** dell'area di lavoro **Criteri** consentono di identificare i problemi relativi ai criteri che richiedono attenzione. Un riepilogo dello stato viene visualizzato anche nell'area di lavoro Dashboard.

> [!NOTE]
> Per rimuovere un profilo di posta elettronica da un dispositivo, modificare la distribuzione e rimuovere tutti i gruppi di cui il dispositivo è membro.





<!--HONumber=Jun16_HO4-->


