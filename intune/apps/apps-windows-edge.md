---
title: Aggiungere Microsoft Edge per Windows 10 a Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere Microsoft Edge per Windows a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa0156d059513a2586eb7d8866d23508be0af10c
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886674"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>Aggiungere Microsoft Edge per Windows 10 a Microsoft Intune

Prima di poter distribuire, configurare, monitorare o proteggere le app è necessario aggiungerle a Intune. Uno dei tipi di [app disponibili](~/apps/apps-add.md#app-types-in-microsoft-intune) è Microsoft Edge *versione 77 e successive*. Selezionando questo tipo di app in Intune, è possibile assegnare e installare Microsoft Edge *versione 77 e successive* nei dispositivi gestiti che eseguono Windows 10.

> [!IMPORTANT]
> Questo tipo di app è disponibile in **anteprima pubblica** e viene offerta nei canali stabile, beta e per sviluppatori per Windows 10. La distribuzione è solo in lingua inglese (EN), ma gli utenti finali possono modificare la lingua di visualizzazione nel browser in **Impostazioni** > **Lingue**. Microsoft Edge è un'app Win32 installata nel contesto di sistema e in architetture corrispondenti (app x86 in un sistema operativo x86 e app x64 in un sistema operativo x64). Intune rileverà tutte le installazioni di Microsoft Edge preesistenti. Se il browser è installato nel contesto utente, un'installazione del sistema lo sovrascriverà. Se è installato nel contesto di sistema, viene segnalato l'esito positivo dell'installazione. Inoltre gli aggiornamenti automatici di Microsoft Edge sono **attivati** per impostazione predefinita e non è possibile disinstallare Microsoft Edge.

> [!NOTE]
> Microsoft Edge *versione 77 e successive* è disponibile anche per macOS.
> 
> Non è possibile usare la distribuzione dell'applicazione predefinita di Microsoft Edge per i computer aggiunti all'area di lavoro. Per la distribuzione dell'applicazione predefinita è richiesta l'estensione di gestione di Intune, disponibile solo per i dispositivi aggiunti ad AAD. È comunque possibile distribuire Microsoft Edge *versione 77 e successive* usando un file *MSI* caricato in **App**. Vedere [Aggiungere un'app line-of-business per Windows a Microsoft Intune](~/apps/lob-apps-windows.md).

## <a name="prerequisites"></a>Prerequisiti
- È necessario Windows 10 RS2 o versione successiva.
- Tutte le versioni preinstallate di Microsoft Edge *versione 77 e successive* per tutti i canali del contesto utente verranno sovrascritte con Edge installato nel contesto di sistema.

## <a name="configure-the-app-in-intune"></a>Configurare l'app in Intune
È possibile aggiungere Microsoft Edge versione 77 e successive a Intune seguendo questa procedura:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Nell'elenco **Tipo di app** in **Microsoft Edge versione 77 e successive** selezionare **Windows 10**.

## <a name="configure-app-information"></a>Configurare le informazioni sull'app
In questo passaggio verranno specificate le informazioni su questa distribuzione di app. Queste informazioni consentono di identificare l'app in Intune e permettono agli utenti di trovarla nel portale aziendale.

1. Fare clic su **Informazioni sull'app** per visualizzare il riquadro **Informazioni sull'app**.
2. Nel riquadro **Informazioni sull'app** specificare le informazioni su questa distribuzione di app. Queste informazioni consentono di identificare l'app in Intune e permettono agli utenti di trovarla nel portale aziendale.
    - **Nome**: Immettere il nome dell'app che verrà visualizzato nel portale aziendale. Assicurarsi che tutti i nomi siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione**: Immettere una descrizione per l'app. Ad esempio, è possibile elencare gli utenti di destinazione nella descrizione.
    - **Autore**: come editore viene visualizzato Microsoft.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa impostazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: come sviluppatore viene visualizzato Microsoft.
    - **Proprietario**: come proprietario viene visualizzato Microsoft.
    - **Note**: immettere eventuali note da associare a questa app (facoltativo).
3. Selezionare **OK**.

## <a name="configure-app-settings"></a>Configurare le impostazioni dell'app
In questo passaggio configurare le opzioni di installazione per l'app.

1. Nel riquadro **Aggiungi app** selezionare **Impostazioni dell'app**.
2. Nel riquadro **Impostazioni dell'app** selezionare **Stabile**, **Beta** o **Sviluppo** nell'elenco **Canale** per determinare il canale di Microsoft Edge da cui si vuole distribuire l'app.
    - Il canale **Stabile** è il canale consigliato per la distribuzione su larga scala negli ambienti aziendali. Viene aggiornato ogni sei settimane e ogni versione include miglioramenti derivanti dal canale beta.
    - Il canale **Beta** corrisponde all'esperienza di anteprima di Microsoft Edge più stabile ed è la scelta migliore per un progetto pilota completo all'interno dell'organizzazione. Con gli aggiornamenti principali pubblicati ogni sei settimane, ogni versione include le esperienze e i miglioramenti dal canale Sviluppo.
    - Il canale **Sviluppo** è pensato per raccogliere commenti e suggerimenti dai clienti aziendali su Windows, Windows Server e macOS. Prevede aggiornamenti settimanali e contiene i miglioramenti e le correzioni più recenti.

    > [!NOTE]
    > Il logo del browser Microsoft Edge viene visualizzato insieme all'app quando gli utenti visitano il portale aziendale.

3.  Selezionare **OK**.

## <a name="select-scope-tags-optional"></a>Selezionare i tag di ambito (facoltativo)
È possibile usare i tag di ambito per determinare chi può visualizzare le informazioni sull'app client in Intune. Per informazioni dettagliate complete sui tag di ambito, vedere Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti.
1.  Selezionare **Ambito (tag)**  > **Aggiungi**.
2.  Usare la casella **Seleziona** per cercare i tag di ambito.
3.  Selezionare la casella di controllo accanto ai tag di ambito da assegnare a questa app.
4.  Fare clic su **Seleziona** > **OK**.

## <a name="add-the-app"></a>Aggiungere l'app
Al termine della configurazione dell'app, selezionare **Aggiungi** nel riquadro **Aggiungi app**. 

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. 

> [!NOTE]
> Attualmente, se si annulla l'assegnazione della distribuzione di Microsoft Edge, il programma rimarrà nel dispositivo.

## <a name="troubleshooting"></a>Risoluzione dei problemi
**Microsoft Edge versione 77 e successive per Windows 10:**<br>
Intune usa l'estensione di gestione di Intune per scaricare e distribuire il programma di installazione di Microsoft Edge in dispositivi Windows 10 assegnati, quindi comunica le impostazioni di distribuzione al programma di installazione di Microsoft Edge, che scarica e installa il browser Microsoft Edge direttamente dalla rete CDN. Fare riferimento ai [prerequisiti per l'estensione di gestione di Intune](~/apps/intune-management-extension.md#prerequisites) e alle procedure consigliate descritte nell'articolo sull'accesso al servizio di aggiornamento di Azure e alla rete CDN per assicurarsi che la configurazione della rete consenta ai dispositivi Windows 10 di accedere a tali posizioni. Per consentire l'accesso ai file di installazione da una rete CDN per installare il browser, è anche necessario consentire l'accesso agli endpoint Windows Update. Per altre informazioni, vedere [Gestire gli endpoint di connessione per Windows 10, versione 1809 - Windows Update](https://docs.microsoft.com/windows/privacy/manage-windows-1809-endpoints#windows-update) ed [Endpoint di rete per Microsoft Intune](~/fundamentals/intune-endpoints.md).

## <a name="next-steps"></a>Passaggi successivi
- [Assegnare app ai gruppi](~/apps/apps-deploy.md)
