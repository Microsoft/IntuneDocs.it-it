---
title: Come aggiungere app line-of-business per macOS in Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere app line-of-business (LOB) per macOS in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
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
ms.openlocfilehash: aeae231e07ceeee6a54f8f60ec5d53cc96d55be0
ms.sourcegitcommit: 737ad6c675deedfc6009f792023ff95981b06582
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117890"
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
    
    - `IntuneAppUtil -h`<br>
    Questo comando mostrerà le informazioni di utilizzo per lo strumento.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Questo comando esegue il wrapping del file dell'app LOB con estensione *pkg* in un file con estensione *intunemac*.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Questo comando estrarrà i parametri rilevati e la versione per il file con estensione *intunemac* creato.

## <a name="step-1---specify-the-software-setup-file"></a>Passaggio 1: specificare il file di installazione del software

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **App client**.
4. Nel carico di lavoro **App client** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel riquadro **Aggiungi app** scegliere **App line-of-business**.

## <a name="step-2---configure-the-app-package-file"></a>Passaggio 2: configurare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel riquadro **File del pacchetto dell'app** scegliere il pulsante Sfoglia e selezionare un file di installazione macOS con estensione *intunemac*.
3. Al termine, scegliere **OK**.


## <a name="step-3---configure-app-information"></a>Passaggio 3: configurare le informazioni sull'app

1. Nel riquadro **Aggiungi app** scegliere **Informazioni sull'app**.
2. Nel riquadro **Informazioni sull'app** aggiungere i dettagli relativi all'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione**: immettere la descrizione dell'app che gli utenti visualizzeranno nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Sistema operativo minimo**: nell'elenco scegliere la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. L'uso delle categorie consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. Questa è l'icona visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
3. Al termine, scegliere **OK**.

## <a name="step-4---finish-up"></a>Passaggio 4: completare l'operazione

1. Nel riquadro **Aggiungi app** verificare che i dettagli dell'app siano corretti.
2. Scegliere **Aggiungi** per caricare l'app in Intune.

L'app creata compare nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

> [!NOTE]
> Se il file con estensione *pkg* contiene più app o programmi di installazione di app, Microsoft Intune segnalerà solo che l'*app* è installata correttamente quando tutte le app installate verranno rilevate nel dispositivo.

## <a name="step-5---update-a-line-of-business-app"></a>Passaggio 5: aggiornare un'app line-of-business

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Per consentire al servizio Intune di distribuire correttamente un nuovo file con estensione *pkg* nel dispositivo, è necessario incrementare la stringa `version` e `CFBundleVersion` del pacchetto nel file *packageinfo* del pacchetto con estensione *pkg*.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Per altre informazioni, vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Per altre informazioni, vedere [Panoramica dei cicli di vita del dispositivo e dell'app](../fundamentals/device-lifecycle.md)
