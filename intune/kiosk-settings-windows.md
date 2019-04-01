---
title: Impostazioni relative alla modalità tutto schermo per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare i dispositivi Windows 10 e versioni successive per l'esecuzione di una o più app in modalità tutto schermo, personalizzare il menu Start, aggiungere app, visualizzare la barra della applicazioni e configurare un Web browser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55a0cb45cd3e3a8e367b0bff7bd8e856b02af953
ms.sourcegitcommit: aab39bf86707ccaef45fd6527fff4f1c89336710
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2019
ms.locfileid: "58429692"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Impostazioni dei dispositivi Windows 10 e versioni successive per l'esecuzione in modalità tutto schermo in Intune

È possibile configurare i dispositivi Windows 10 e versioni successive per l'esecuzione di una o più app in modalità tutto schermo.

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi Windows 10 e versioni successive. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per configurare i dispositivi Windows 10 e versioni successive da eseguire in modalità tutto schermo.

Come amministratore di Intune, è possibile creare e assegnare queste impostazioni ai dispositivi.

Per altre informazioni sulla funzionalità Modalità tutto schermo di Windows in Intune, vedere [Configurare le impostazioni a tutto schermo](kiosk-settings.md).

## <a name="before-you-begin"></a>Prima di iniziare

- [Creare il profilo](kiosk-settings.md#create-the-profile).

- Questo profilo per chiosco multimediale è direttamente correlato al profilo di restrizioni del dispositivo creata tramite il [impostazioni modalità tutto schermo di Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser). Per concludere:

  1. È stato creato il profilo per chiosco multimediale per l'esecuzione del dispositivo in modalità tutto schermo.
  2. Creare il [profilo di restrizione](device-restrictions-windows-10.md#microsoft-edge-browser)e configurare le impostazioni consentite in Microsoft Edge e le funzionalità specifiche.

> [!IMPORTANT] 
> Assicurarsi di assegnare il profilo per chiosco multimediale agli stessi dispositivi come le [profilo di Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>App singola per chioschi multimediali a schermo intero

Esegue solo un'app nel dispositivo.

- **Selezionare una modalità per chiosco multimediale**: scegliere **singola app, per chiosco multimediale a schermo intero**.

- **Tipo di accesso utente**: le app aggiunte vengono eseguite con l'account utente immesso. Le opzioni disponibili sono:

  - **Accesso automatico (Windows 10, versione 1803+)**: usare sui dispositivi in modalità tutto schermo in ambienti pubblici che non richiedono all'utente di eseguire l'accesso, in modo simile a un account Guest. Questa impostazione usa il [provider di servizi di configurazione AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Account utente locale**: immettere l'account utente locale (per il dispositivo). L'account che immesso consente l'accesso per la modalità tutto schermo.

- **Tipo di applicazione**: selezionare il tipo di applicazione. Le opzioni disponibili sono:

  - **Aggiungere browser Microsoft Edge**: selezionare **browser Microsoft Edge**, quindi scegliere il **tipo Edge type di modalità per chiosco multimediale**:

    - **/ Interactive digital signage**: consente di aprire un URL completo e Mostra solo il contenuto in tale sito Web. [Impostare i cartelli digitali](https://docs.microsoft.com/windows/configuration/setup-digital-signage) vengono fornite ulteriori informazioni su questa funzionalità.
    - **Pubblica esplorazione (InPrivate)**: esegue una versione multi-scheda limitata di Microsoft Edge. Gli utenti possono esplorare pubblicamente o terminare la sessione di esplorazione.

    Per altre informazioni su queste opzioni, vedere [modalità tutto schermo di distribuire Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Questa impostazione abilita il browser Microsoft Edge sul dispositivo. Per configurare le impostazioni specifiche di Microsoft Edge, creare un profilo di configurazione del dispositivo (**configurazione del dispositivo** > **profili** > **Crea profilo**  >  **Windows 10** per la piattaforma > **restrizioni del dispositivo** >  **Browser Microsoft Edge**). [Browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) Elenca e descrive le impostazioni disponibili.

    Selezionare **OK** per salvare le modifiche.

  - **Aggiungere browser Chiosco**: selezionare **delle impostazioni del browser per chiosco multimediale**. Queste impostazioni controllano un'app Web browser in modalità tutto schermo. Assicurarsi di ottenere l'[app browser in modalità tutto schermo](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) dallo Store, aggiungerla a Intune come [app client](apps-add.md) e quindi assegnare l'app ai dispositivi in modalità tutto schermo.

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

  - **App Store Add**: selezionare **aggiungere un'app dello store**, scegliere un'app dall'elenco.

    Se l'elenco non include app, aggiungerne qualcuna seguendo la procedura in [App client](apps-add.md).

  Selezionare **OK** per salvare le modifiche.

## <a name="multi-app-kiosks"></a>Più app in modalità tutto schermo

Le app in questa modalità sono disponibili nel menu Start. Sono le uniche app che l'utente può aprire. Se un'app presenta una dipendenza da un'altra app, entrambi deve essere incluso nell'elenco App consentite. Ad esempio, Internet Explorer 64 bit presenta una dipendenza su Internet Explorer 32 bit, pertanto è necessario consentire in "C:\Programmi\Microsoft c:\Programmi\Internet explorer\iexplore.exe" sia "C:\Program Files (x86) \Internet". 

- **Selezionare una modalità per chiosco multimediale**: scegliere **tra più app per chiosco multimediale**.

- **Specifica Windows 10 come destinazione nei dispositivi in modalità S**:
  - **Sì**: consente le app dello Store e le app AUMID (escluse le app Win32) nel profilo in modalità tutto schermo.
  - **No**: consente le app dello Store, le app Win32 e le app AUMID nel profilo in modalità tutto schermo. Questo profilo per chiosco multimediale non è stato distribuito ai dispositivi in modalità S.

- **Tipo di accesso utente**: le app aggiunte vengono eseguite con l'account utente immesso. Le opzioni disponibili sono:

  - **Accesso automatico (Windows 10, versione 1803+)**: usare sui dispositivi in modalità tutto schermo in ambienti pubblici che non richiedono all'utente di eseguire l'accesso, in modo simile a un account Guest. Questa impostazione usa il [provider di servizi di configurazione AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Account utente locale**: **aggiungere** l'account utente locale (per il dispositivo). L'account che immesso consente l'accesso per la modalità tutto schermo.
  - **Utente o gruppo di Azure AD (Windows 10, versione 1803+)**: selezionare **Aggiungi** e scegliere gli utenti o i gruppi di Azure nell'elenco. È possibile selezionare più utenti e gruppi. Scegliere **OK** per salvare le modifiche.
  - **Visitatore di HoloLens**: l'account del visitatore è un account Guest che non richiede credenziali utente o autenticazione, come descritto in [Concetti della modalità PC condiviso](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Browser e applicazioni**: aggiungere le app da eseguire nel dispositivo in modalità tutto schermo. Ricordarsi che è possibile aggiungere più app.

  - **Browser**

    - **Aggiungere Microsoft Edge**: Microsoft Edge viene aggiunta alla griglia di app e tutte le applicazioni possono essere eseguite in questa modalità tutto schermo. Scegliere il **tipo di modalità tutto schermo di Microsoft Edge**:

      - **Modalità normale (versione completa di Microsoft Edge)**: esegue una versione completa di Microsoft Edge con tutte le funzionalità di esplorazione. Lo stato e dati utente vengono salvate tra le sessioni.
      - **Pubblica esplorazione (InPrivate)**: esegue una versione multi-scheda di InPrivate di Microsoft Edge con un'esperienza personalizzata per i chioschi multimediali che vengono eseguiti in modalità schermo intero.

      Per altre informazioni su queste opzioni, vedere [modalità tutto schermo di distribuire Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Questa impostazione abilita il browser Microsoft Edge sul dispositivo. Per configurare le impostazioni specifiche di Microsoft Edge, creare un profilo di configurazione del dispositivo (**configurazione del dispositivo** > **profili** > **Crea profilo**  >  **Windows 10** per la piattaforma > **restrizioni del dispositivo** >  **Browser Microsoft Edge**). [Browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) Elenca e descrive le impostazioni disponibili.

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
      - **ID modello utente applicazione (AUMID)**: immettere l'ID modello utente applicazione dell'app Win32. Questa impostazione determina il layout iniziale del riquadro sul desktop. Per ottenere questo ID, vedere [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

      Selezionare **OK** per salvare le modifiche.

    - **Aggiungi in base all'ID modello utente applicazione**: usare questa opzione per aggiungere app predefinite di Windows come il Blocco note o la Calcolatrice. Immettere le proprietà seguenti:

      - **Nome applicazione**: obbligatorio. Immettere un nome per l'applicazione.
      - **ID modello utente applicazione (AUMID)**: obbligatorio. Immettere l'ID modello utente applicazione (AUMID) dell'app Windows. Per ottenere questo ID, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata) per ottenere l'ID.

      Selezionare **OK** per salvare le modifiche.

    - **Avvio automatico di**: facoltativo. Scegliere un'applicazione di avvio automatico quando l'utente esegue l'accesso. È possibile AutoLaunched solo una singola app.
    - **Dimensioni del riquadro**: obbligatorio. Scegliere Piccolo, Medio o Grande per le dimensioni del riquadro.

  > [!TIP]
  > Dopo aver aggiunto tutte le app, è possibile modificarne l'ordine di visualizzazione facendo clic e trascinando le app nell'elenco.  

- **Usa un layout Start alternativo**: scegliere **Sì** per immettere un file XML che descrive come le app vengono visualizzate nel menu Start, incluso il relativo ordine. Usare questa opzione se è necessaria una maggiore personalizzazione nel menu Start. Leggere [Personalizzare ed esportare il layout della schermata Start](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) per conoscere alcune linee guida e XML di esempio.

- **Barra delle applicazioni di Windows**: scegliere **Mostra** o **Nascondi** per la barra delle applicazioni. Per impostazione predefinita, la barra delle applicazioni non viene visualizzata. Vengono visualizzate delle icone, ad esempio l'icona del Wi-Fi, ma le impostazioni non possono essere modificate dagli utenti finali.

- **Consentire l'accesso alla cartella Downloads**: scegliere **Sì** per consentire agli utenti di accedere alla cartella di download in Windows Explorer. Per impostazione predefinita, l'accesso alla cartella di download è disabilitata. Questa funzionalità viene comunemente usata per gli utenti finali per accedere agli elementi scaricati da un browser.

Selezionare **OK** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili in modalità tutto schermo per dispositivi [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) e [Windows Holographic for Business](kiosk-settings-holographic.md).
