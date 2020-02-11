---
title: Come aggiungere app line-of-business per macOS in Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere app line-of-business (LOB) per macOS in Microsoft Intune.
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
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755171"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Come aggiungere app line-of-business (LOB) per macOS in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Usare le informazioni di questo articolo per aggiungere le app line-of-business per macOS in Microsoft Intune. È necessario scaricare uno strumento esterno per eseguire l'analisi preliminare dei file con estensione *pkg* prima di poter caricare il file line-of-business in Microsoft Intune. L'analisi preliminare dei file con estensione *pkg* deve essere eseguita in un dispositivo macOS.

> [!NOTE]
> A partire dalla versione di macOS Catalina 10.15, prima di aggiungere le app a Intune, verificare che le app LOB macOS siano autenticate. Se gli sviluppatori delle app LOB non hanno autenticato le app, non sarà possibile eseguirle nei dispositivi macOS degli utenti. Per altre informazioni su come verificare se un'app è autenticata, visitare [Autenticare le app macOS per poter usare macOS Catalina](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579).

> [!NOTE]
> Anche se gli utenti dei dispositivi macOS possono rimuovere alcune delle app macOS predefinite, ad esempio Borsa e Mappe, non è possibile usare Intune per ridistribuire tali app. Se gli utenti finali eliminano queste app, devono accedere all'App Store e reinstallarle manualmente.

## <a name="before-your-start"></a>Prima di iniziare

Prima di caricare il file line-of-business in Microsoft Intune, è necessario scaricare uno strumento esterno, contrassegnare lo strumento scaricato come eseguibile ed eseguire l'analisi preliminare dei file con estensione *pkg* con tale strumento. L'analisi preliminare dei file con estensione *pkg* deve essere eseguita in un dispositivo macOS. Usare lo strumento di wrapping delle app di Intune per Mac per abilitare la gestione delle app Mac con Microsoft Intune.

> [!IMPORTANT]
> Il file con estensione *pkg* deve essere firmato con il certificato "Programma di installazione ID sviluppatore", ottenuto da un account sviluppatore Apple. Per caricare le app LOB per macOS in Microsoft Intune, si possono usare solo file con estensione *pkg*. La conversione di altri formati, ad esempio da *dmg* a *pkg*, non è supportata.
>

1. Scaricare lo [strumento di wrapping delle app di Intune per Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > Lo **strumento di wrapping delle app di Intune per Mac** deve essere eseguito in un computer macOS. 

2. Contrassegnare lo strumento scaricato come eseguibile:
   - Avviare l'app Terminale.
   - Cambiare la directory sostituendola con il percorso in cui si trova `IntuneAppUtil`.
   - Eseguire il comando seguente per rendere eseguibile lo strumento:<br> 
       `chmod +x IntuneAppUtil`

3. Usare il comando `IntuneAppUtil` nello **strumento di wrapping delle app di Intune per Mac** per eseguire il wrapping del file dell'app LOB con estensione *pkg* da un file con estensione *intunemac*.<br>

    Comandi di esempio da usare per lo strumento di wrapping delle app di Microsoft Intune per macOS:
    > [!IMPORTANT]
    > Verificare che l'argomento `<source_file>` non contenga spazi prima di eseguire i comandi `IntuneAppUtil`.

    - `IntuneAppUtil -h`<br>
    Questo comando mostrerà le informazioni di utilizzo per lo strumento.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Questo comando esegue il wrapping del file dell'app LOB con estensione *pkg* in un file con estensione *intunemac*.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Questo comando estrarrà i parametri rilevati e la versione per il file con estensione *intunemac* creato.

## <a name="select-the-app-type"></a>Selezionare il tipo di app

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Tra i tipi di app in **Altro** nel riquadro **Seleziona il tipo di app** selezionare **App line-of-business**.
4. Fare clic su **Seleziona**. Verrà visualizzata la procedura **Aggiungi app**.

## <a name="step-1---app-information"></a>Passaggio 1: informazioni sull'app

### <a name="select-the-app-package-file"></a>Selezionare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** fare clic su **Selezionare il file del pacchetto di app**. 
2. Nel riquadro **File del pacchetto dell'app** selezionare il pulsante Sfoglia. Selezionare quindi un file di installazione macOS con estensione *intunemac*.
   Verranno visualizzati i dettagli dell'app.
3. Al termine, selezionare **OK** nel riquadro **File del pacchetto dell'app** per aggiungere l'app.

### <a name="set-app-information"></a>Impostare le informazioni sull'app

1. Nella pagina **Informazioni sull'app** aggiungere i dettagli relativi all'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente.
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata nel portale aziendale.
    - **Descrizione**: immettere la descrizione dell'app. La descrizione viene visualizzata nel portale aziendale.
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **Sistema operativo minimo**: selezionare dall'elenco la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Le categorie consentono agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: Visualizzare chiaramente l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario dell'app (facoltativo). Un esempio è **Reparto risorse umane**.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
2. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.

## <a name="step-2---select-scope-tags-optional"></a>Passaggio 2: selezionare i tag di ambito (facoltativo)
È possibile usare i tag di ambito per determinare chi può visualizzare le informazioni sull'app client in Intune. Per informazioni dettagliate complete sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

1. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per l'app. 
2. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.

## <a name="step-3---assignments"></a>Passaggio 3: assegnazioni

1. Per l'assegnazione dell'app a gruppi, selezionare **Obbligatoria**, **Disponibile per i dispositivi registrati** o **Disinstalla**. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md) e [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).
2. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. 

## <a name="step-4---review--create"></a>Passaggio 4 - Verifica e creazione

1. Verificare i valori e le impostazioni immesse per l'app.
2. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

    Verrà visualizzato il pannello **Panoramica** per l'app line-of-business.

L'app creata compare nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

> [!NOTE]
> Se il file con estensione *pkg* contiene più app o programmi di installazione di app, Microsoft Intune segnalerà solo che l'*app* è installata correttamente quando tutte le app installate verranno rilevate nel dispositivo.

## <a name="update-a-line-of-business-app"></a>Aggiornare un'app line-of-business

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Per consentire al servizio Intune di distribuire correttamente un nuovo file con estensione *pkg* nel dispositivo, è necessario incrementare la stringa `version` e `CFBundleVersion` del pacchetto nel file *packageinfo* del pacchetto con estensione *pkg*.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Per altre informazioni, vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Per altre informazioni, vedere [Panoramica dei cicli di vita del dispositivo e dell'app](../fundamentals/device-lifecycle.md)
