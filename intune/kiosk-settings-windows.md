---
title: Impostazioni relative alla modalità tutto schermo per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare i dispositivi Windows 10 e versioni successive per l'esecuzione di una o più app in modalità tutto schermo, personalizzare il menu Start, aggiungere app, visualizzare la barra della applicazioni e configurare un Web browser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a80e4cf4e68235ef9e88943a8b62121e0cfb6623
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046964"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Impostazioni dei dispositivi Windows 10 e versioni successive per l'esecuzione in modalità tutto schermo in Intune

È possibile configurare i dispositivi Windows 10 e versioni successive per l'esecuzione di una o più app in modalità tutto schermo.

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi Windows 10 e versioni successive. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per configurare i dispositivi Windows 10 e versioni successive da eseguire in modalità tutto schermo.

Come amministratore di Intune, è possibile creare e assegnare queste impostazioni ai dispositivi.

Per altre informazioni sulla funzionalità Modalità tutto schermo di Windows in Intune, vedere [Configurare le impostazioni a tutto schermo](kiosk-settings.md).

## <a name="before-you-begin"></a>Prima di iniziare

- [Creare il profilo](kiosk-settings.md#create-the-profile).

- Questo profilo per la modalità tutto schermo è direttamente correlato al profilo di restrizioni per i dispositivi creato usando le [impostazioni della modalità tutto schermo di Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser). Per concludere:

  1. Creare questo profilo per la modalità tutto schermo per l'esecuzione del dispositivo in modalità tutto schermo.
  2. Creare il [profilo di restrizioni per i dispositivi](device-restrictions-windows-10.md#microsoft-edge-browser) e configurare le funzionalità e le impostazioni specifiche consentite in Microsoft Edge.

> [!IMPORTANT] 
> Assicurarsi di assegnare questo profilo per la modalità tutto schermo agli stessi dispositivi del [profilo di Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>App singola per chioschi multimediali a schermo intero

Eseguire una sola app nel dispositivo.

- **Selezionare una modalità tutto schermo**: scegliere **App singola per chiosco multimediale a schermo intero**.

- **Tipo di accesso utente**: le app aggiunte vengono eseguite con l'account utente immesso. Le opzioni disponibili sono:

  - **Accesso automatico (Windows 10, versione 1803+)** : usare sui dispositivi in modalità tutto schermo in ambienti pubblici che non richiedono all'utente di eseguire l'accesso, in modo simile a un account Guest. Questa impostazione usa il [provider di servizi di configurazione AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Account utente locale**: immettere l'account utente locale (per il dispositivo). L'account immesso accede al chiosco multimediale.

- **Tipo di applicazione**: selezionare il tipo di applicazione. Le opzioni disponibili sono:

  - **Aggiungi il browser Microsoft Edge**: selezionare **Browser Microsoft Edge** e scegliere il **Tipo di modalità tutto schermo di Microsoft Edge**:

    - **Insegna digitale o schermo interattivo**: consente di aprire un URL a schermo intero e visualizza solo il contenuto di tale sito Web. [Set up digital signs](https://docs.microsoft.com/windows/configuration/setup-digital-signage) (Configurare insegne digitali) offre altre informazioni su questa funzionalità.
    - **Esplorazione pubblica (InPrivate)** : esegue una versione multi-scheda limitata di Microsoft Edge. Gli utenti possono esplorare pubblicamente o terminare la sessione di esplorazione.

    Per altre informazioni su queste opzioni, vedere [Distribuire la modalità tutto schermo di Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Questa impostazione abilita il browser Microsoft Edge nel dispositivo. Per configurare le impostazioni specifiche di Microsoft Edge, creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo**  >  **Windows 10** per la piattaforma > **Restrizioni del dispositivo** >  **Browser Microsoft Edge**). In [Browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) sono elencate e descritte le impostazioni disponibili.

    Selezionare **OK** per salvare le modifiche.

  - **Aggiungi un browser in modalità tutto schermo**: selezionare **Impostazioni del browser in modalità tutto schermo**. Queste impostazioni controllano un'app Web browser in modalità tutto schermo. Assicurarsi di ottenere l'[app browser in modalità tutto schermo](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) dallo Store, aggiungerla a Intune come [app client](apps-add.md) e quindi assegnare l'app ai dispositivi in modalità tutto schermo.

    Immettere le impostazioni seguenti:

    - **URL della home page predefinita**: immettere l'URL predefinito visualizzato all'apertura o al riavvio del browser in modalità tutto schermo. Ad esempio, immettere `http://bing.com` o `http://www.contoso.com`.

    - **Pulsante Pagina iniziale**: scegliere **Mostra** o **Nascondi** per il pulsante Pagina iniziale del browser in modalità tutto schermo. Per impostazione predefinita, il pulsante non viene visualizzato.

    - **Pulsanti di spostamento**: scegliere **Mostra** o **Nascondi** per i pulsanti Avanti e Indietro. Per impostazione predefinita, i pulsanti di spostamento non sono visualizzati.

    - **Pulsante Termina sessione**: scegliere **Mostra** o **Nascondi** per il pulsante Termina sessione. Quando visualizzato, l'utente seleziona il pulsante e l'app chiede conferma della chiusura della sessione. Se confermata, il browser cancella tutti i dati di esplorazione (cookie, cache e così via) e quindi apre l'URL predefinito. Per impostazione predefinita, il pulsante non viene visualizzato.

    - **Aggiorna il browser dopo il tempo di inattività**: immettere la quantità di tempo di inattività (da 1 a 1440 minuti) trascorso il quale il browser in modalità tutto schermo viene riavviato. Il tempo di inattività è il numero di minuti dopo l'ultima interazione dell'utente. Per impostazione predefinita, il valore è vuoto, ovvero non è configurato alcun timeout di inattività.

    - **Siti Web consentiti**: usare questa impostazione per consentire l'apertura di siti Web specifici. In altre parole, usare questa funzionalità per limitare o bloccare siti Web nel dispositivo. Ad esempio, è possibile consentire l'apertura di tutti i siti Web in `http://contoso.com*`. Per impostazione predefinita, sono consentiti tutti i siti Web.

      Per consentire siti Web specifici, caricare un file che include un elenco dei siti Web consentiti in righe distinte. Se non si aggiunge un file, sono consentiti tutti i siti Web. Intune supporta `*` (asterisco) come carattere jolly.

      Il file di esempio sarà simile all'elenco seguente:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

    Selezionare **OK** per salvare le modifiche.

  - **Aggiungi l'app dello Store**: scegliere **Aggiungi un'app dello Store** e scegliere un'app nell'elenco.

    Se l'elenco non include app, aggiungerne qualcuna seguendo la procedura in [App client](apps-add.md).

  Selezionare **OK** per salvare le modifiche.

## <a name="multi-app-kiosks"></a>Più app in modalità tutto schermo

Le app in questa modalità sono disponibili nel menu Start. Sono le uniche app che l'utente può aprire. Se un'app presenta una dipendenza da un'altra app, entrambe devono essere incluse nell'elenco delle app consentite. Ad esempio, Internet Explorer a 64 bit ha una dipendenza da Internet Explorer a 32 bit, pertanto è necessario consentire sia "C:\Programmi\internet explorer\iexplore.exe" che “C:\Programmi (x86)\Internet Explorer\iexplore.exe”. 

- **Selezionare una modalità tutto schermo**: scegliere **Più app in modalità tutto schermo**.

- **Specifica Windows 10 come destinazione nei dispositivi in modalità S**:
  - **Sì**: consente le app dello Store e le app AUMID (escluse le app Win32) nel profilo in modalità tutto schermo.
  - **No**: consente le app dello Store, le app Win32 e le app AUMID nel profilo in modalità tutto schermo. Questo profilo per la modalità tutto schermo non viene distribuito nei dispositivi in modalità S.

- **Tipo di accesso utente**: le app aggiunte vengono eseguite con l'account utente immesso. Le opzioni disponibili sono:

  - **Accesso automatico (Windows 10, versione 1803+)** : usare sui dispositivi in modalità tutto schermo in ambienti pubblici che non richiedono all'utente di eseguire l'accesso, in modo simile a un account Guest. Questa impostazione usa il [provider di servizi di configurazione AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Account utente locale**: **aggiungere** l'account utente locale (per il dispositivo). L'account immesso accede al chiosco multimediale.
  - **Utente o gruppo di Azure AD (Windows 10, versione 1803+)** : selezionare **Aggiungi** e scegliere gli utenti o i gruppi di Azure nell'elenco. È possibile selezionare più utenti e gruppi. Scegliere **OK** per salvare le modifiche.
  - **Visitatore di HoloLens**: l'account del visitatore è un account Guest che non richiede credenziali utente o autenticazione, come descritto in [Concetti della modalità PC condiviso](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Browser e applicazioni**: aggiungere le app da eseguire nel dispositivo in modalità tutto schermo. Ricordarsi che è possibile aggiungere più app.

  - **Browser**

    - **Aggiungi Microsoft Edge**: Microsoft Edge viene aggiunto alla griglia delle app e tutte le applicazioni possono essere eseguite in questo chiosco multimediale. Scegliere il **Tipo di modalità tutto schermo di Microsoft Edge**:

      - **Modalità normale (versione completa di Microsoft Edge)** : esegue una versione completa di Microsoft Edge con tutte le funzionalità di esplorazione. I dati dell'utente e lo stato vengono salvati tra le sessioni.
      - **Esplorazione pubblica (InPrivate)** : esegue una versione con più schede di Microsoft Edge InPrivate con un'esperienza personalizzata per i chioschi multimediali eseguiti in modalità schermo intero.

      Per altre informazioni su queste opzioni, vedere [Distribuire la modalità tutto schermo di Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Questa impostazione abilita il browser Microsoft Edge nel dispositivo. Per configurare le impostazioni specifiche di Microsoft Edge, creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo**  >  **Windows 10** per la piattaforma > **Restrizioni del dispositivo** >  **Browser Microsoft Edge**). In [Browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) sono elencate e descritte le impostazioni disponibili.

      Selezionare **OK** per salvare le modifiche.

    - **Aggiungi un browser in modalità tutto schermo**: queste impostazioni consentono di controllare un'app Web browser nel dispositivo in modalità tutto schermo. Assicurarsi di distribuire un'app Web browser ai dispositivi in modalità tutto schermo usando [App client](apps-add.md).

      Immettere le impostazioni seguenti:

      - **URL della home page predefinita**: immettere l'URL predefinito visualizzato all'apertura o al riavvio del browser in modalità tutto schermo. Ad esempio, immettere `http://bing.com` o `http://www.contoso.com`.

      - **Pulsante Pagina iniziale**: scegliere **Mostra** o **Nascondi** per il pulsante Pagina iniziale del browser in modalità tutto schermo. Per impostazione predefinita, il pulsante non viene visualizzato.

      - **Pulsanti di spostamento**: scegliere **Mostra** o **Nascondi** per i pulsanti Avanti e Indietro. Per impostazione predefinita, i pulsanti di spostamento non sono visualizzati.

      - **Pulsante Termina sessione**: scegliere **Mostra** o **Nascondi** per il pulsante Termina sessione. Quando visualizzato, l'utente seleziona il pulsante e l'app chiede conferma della chiusura della sessione. Se confermata, il browser cancella tutti i dati di esplorazione (cookie, cache e così via) e quindi apre l'URL predefinito. Per impostazione predefinita, il pulsante non viene visualizzato.

      - **Aggiorna il browser dopo il tempo di inattività**: immettere la quantità di tempo di inattività (da 1 a 1440 minuti) trascorso il quale il browser in modalità tutto schermo viene riavviato. Il tempo di inattività è il numero di minuti dopo l'ultima interazione dell'utente. Per impostazione predefinita, il valore è vuoto, ovvero non è configurato alcun timeout di inattività.

      - **Siti Web consentiti**: usare questa impostazione per consentire l'apertura di siti Web specifici. In altre parole, usare questa funzionalità per limitare o bloccare siti Web nel dispositivo. Ad esempio, è possibile consentire l'apertura di tutti i siti Web in `contoso.com*`. Per impostazione predefinita, sono consentiti tutti i siti Web.

        Per consentire siti Web specifici, caricare un file CSV che include un elenco dei siti Web consentiti. Se non si aggiunge un file CSV, sono consentiti tutti i siti Web.

      Selezionare **OK** per salvare le modifiche.

  - **Applicazioni**

    - **Aggiungi l'app dello Store**: aggiungere un'app da Microsoft Store per le aziende. Se l'elenco non include alcuna app, è possibile ottenerle e [aggiungerle a Intune](store-apps-windows.md). Ad esempio, è possibile aggiungere un browser in modalità tutto schermo, Excel, OneNote e altro ancora.

      Selezionare **OK** per salvare le modifiche.

    - **Aggiungi un'app di Win32**: un'app Win32 è un'app desktop tradizionale, ad esempio Visual Studio Code o Google Chrome. Immettere le proprietà seguenti:

      - **Nome applicazione**: obbligatorio. Immettere un nome per l'applicazione.
      - **Percorso locale**: obbligatorio. Immettere il percorso del file eseguibile, ad esempio `C:\Program Files (x86)\Microsoft VS Code\Code.exe` o `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **ID modello utente applicazione (AUMID)** : immettere l'ID modello utente applicazione dell'app Win32. Questa impostazione determina il layout iniziale del riquadro sul desktop. Per ottenere questo ID, vedere [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

      Selezionare **OK** per salvare le modifiche.

    - **Aggiungi in base all'ID modello utente applicazione**: usare questa opzione per aggiungere app predefinite di Windows come il Blocco note o la Calcolatrice. Immettere le proprietà seguenti:

      - **Nome applicazione**: obbligatorio. Immettere un nome per l'applicazione.
      - **ID modello utente applicazione (AUMID)** : obbligatorio. Immettere l'ID modello utente applicazione (AUMID) dell'app Windows. Per ottenere questo ID, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata) per ottenere l'ID.

      Selezionare **OK** per salvare le modifiche.

    - **AutoLaunch**: facoltativo. Scegliere un'applicazione da avviare automaticamente quando l'utente esegue l'accesso. È possibile configurare una sola app per l'avvio automatico.
    - **Dimensioni del riquadro**: obbligatorio. Scegliere Piccolo, Medio o Grande per le dimensioni del riquadro.

  > [!TIP]
  > Dopo aver aggiunto tutte le app, è possibile modificarne l'ordine di visualizzazione facendo clic e trascinando le app nell'elenco.  

- **Usa un layout Start alternativo**: scegliere **Sì** per immettere un file XML che descrive come le app vengono visualizzate nel menu Start, incluso il relativo ordine. Usare questa opzione se è necessaria una maggiore personalizzazione nel menu Start. Leggere [Personalizzare ed esportare il layout della schermata Start](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) per conoscere alcune linee guida e XML di esempio.

- **Barra delle applicazioni di Windows**: scegliere **Mostra** o **Nascondi** per la barra delle applicazioni. Per impostazione predefinita, la barra delle applicazioni non viene visualizzata. Vengono visualizzate delle icone, ad esempio l'icona del Wi-Fi, ma le impostazioni non possono essere modificate dagli utenti finali.

- **Consenti l'accesso alla cartella Download**: scegliere **Sì** per consentire agli utenti di accedere alla cartella Download in Esplora risorse. Per impostazione predefinita, l'accesso alla cartella Download è disabilitato. Questa funzionalità viene usata comunemente per consentire agli utenti finali di accedere agli elementi scaricati da un browser.

Selezionare **OK** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili in modalità tutto schermo per dispositivi [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) e [Windows Holographic for Business](kiosk-settings-holographic.md).
