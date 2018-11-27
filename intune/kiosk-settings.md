---
title: Impostazioni relative alla modalità tutto schermo per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare i dispositivi Windows 10 e versioni successive per l'esecuzione di una o più app in modalità tutto schermo. Include la personalizzazione del menu Start, l'aggiunta di app, la barra della applicazioni e la configurazione di un Web browser. Configurare anche i dispositivi Windows Holographic for Business per l'esecuzione di più app in modalità tutto schermo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 7552c9c1fa8e94560505a8971143886160cff6ce
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185954"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Impostazioni relative alla modalità tutto schermo per Windows 10 e versioni successive in Intune

Nei dispositivi Windows 10 è possibile usare Intune per l'esecuzione di questi dispositivi in modalità tutto schermo. Nella modalità tutto schermo (nota anche come chiosco multimediale) è possibile eseguire un'app o molte app. È anche possibile visualizzare e personalizzare un menu Start, aggiungere app diverse, incluse app Win32, aggiungere una specifica home page per un Web browser e molto altro. 

Usare le procedure descritte in questo articolo per creare un chiosco multimediale con una singola app o con più app in Intune.

Intune supporta un profilo in modalità a tutto schermo per ogni dispositivo. Se servono più profili per la modalità tutto schermo in un singolo dispositivo, è possibile usare un [OMA-URI personalizzato](custom-settings-windows-10.md).

## <a name="kiosk-settings"></a>Impostazioni della modalità tutto schermo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le seguenti proprietà:

   - **Nome**: immettere un nome descrittivo per il nuovo profilo.
   - **Descrizione:** immettere una descrizione per il profilo. Questa impostazione è facoltativa ma consigliata.
   - **Piattaforma**: selezionare **Windows 10 e versioni successive**
   - **Tipo di profilo**: selezionare **Modalità tutto schermo (anteprima)**

4. Selezionare una **modalità tutto schermo**. La **modalità tutto schermo** identifica il tipo di modalità tutto schermo supportata dal criterio. Le opzioni includono:

    - **Non configurata** (impostazione predefinita): il criterio non abilita la modalità tutto schermo.
    - **App singola per chiosco multimediale a schermo intero**: il dispositivo viene eseguito con un singolo account utente e bloccato su una singola app dello Store. Pertanto, quando l'utente accede, viene avviata un'app specifica. Questa modalità impedisce anche all'utente di aprire nuove app o modificare l'app in esecuzione.
    - **App multiple per chiosco multimediale**: il dispositivo esegue più app dello Store, app Win32 o app predefinite di Windows tramite ID modello utente applicazione (AUMID). Solo le app aggiunte sono disponibili nel dispositivo.

        Il vantaggio di avere più app in modalità tutto schermo, o un dispositivo predefinito per uno scopo, consiste nel garantire un'esperienza semplice, consentendo di accedere solo alle app necessarie e rimuovendo dalla visualizzazione le app non necessarie.

## <a name="single-full-screen-app-kiosks"></a>App singola per chioschi multimediali a schermo intero
Quando si sceglie la modalità App singola per chiosco multimediale a schermo intero, immettere le impostazioni seguenti:

- **Tipo di accesso utente**: le app aggiunte vengono eseguite con l'account utente immesso. Le opzioni disponibili sono:

  - **Accesso automatico (Windows 10, versione 1803+)**: per i dispositivi in modalità tutto schermo in ambienti pubblici che non richiedono all'utente di eseguire l'accesso, in modo simile a un account guest. Questa impostazione usa il [provider di servizi di configurazione AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Account utente locale**: immettere l'account utente locale (per il dispositivo). L'account specificato viene usato per accedere al chiosco multimediale.

- **Tipo di applicazione**: selezionare **App Store**.

- **App da eseguire in modalità tutto schermo**: scegliere **Aggiungi un'app dello Store** e selezionare un'app nell'elenco.

    Se l'elenco non include app, aggiungerne qualcuna seguendo la procedura in [App client](apps-add.md).

    Selezionare **OK** per salvare le modifiche.

- **Impostazioni del browser in modalità tutto schermo**: queste impostazioni consentono di controllare un'app Web browser nel dispositivo in modalità tutto schermo. Assicurarsi di ottenere l'[app browser in modalità tutto schermo](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) dallo Store, aggiungerla a Intune come [app client](apps-add.md) e quindi assegnare l'app ai dispositivi in modalità tutto schermo.

  Immettere le impostazioni seguenti:

  - **URL della home page predefinita**: immettere l'URL predefinito visualizzato all'apertura o al riavvio del browser in modalità tutto schermo. Ad esempio, immettere `http://bing.com` o `http://www.contoso.com`.

  - **Pulsante Pagina iniziale**: scegliere **Mostra** o **Nascondi** per il pulsante Pagina iniziale del browser in modalità tutto schermo. Per impostazione predefinita, il pulsante non viene visualizzato.

  - **Pulsanti di spostamento**: scegliere **Mostra** o **Nascondi** per i pulsanti Avanti e Indietro. Per impostazione predefinita, i pulsanti di spostamento non sono visualizzati.

  - **Pulsante Termina sessione**: scegliere **Mostra** o **Nascondi** per il pulsante Termina sessione. Quando visualizzato, l'utente seleziona il pulsante e l'app chiede conferma della chiusura della sessione. Se confermata, il browser cancella tutti i dati di esplorazione (cookie, cache e così via) e quindi apre l'URL predefinito. Per impostazione predefinita, il pulsante non viene visualizzato.

  - **Aggiorna il browser dopo il tempo di inattività**: immettere la quantità di tempo di inattività (da 1 a 1440 minuti) trascorso il quale il browser in modalità tutto schermo viene riavviato. Il tempo di inattività è il numero di minuti dopo l'ultima interazione dell'utente. Per impostazione predefinita, il valore è vuoto, ovvero non è configurato alcun timeout di inattività.

  - **Siti Web consentiti**: usare questa impostazione per consentire l'apertura di siti Web specifici. In altre parole, usare questa funzionalità per limitare o bloccare siti Web nel dispositivo. Ad esempio, è possibile consentire l'apertura di tutti i siti Web in `http://contoso.com*`. Per impostazione predefinita, sono consentiti tutti i siti Web.
 
      Per consentire siti Web specifici, caricare un file che include un elenco dei siti Web consentiti in righe distinte. Se non si aggiunge un file, sono consentiti tutti i siti Web. Intune supporta * (asterisco) come carattere jolly.

      Il file di esempio sarà simile all'elenco seguente:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

  Selezionare **OK** per salvare le modifiche.

## <a name="multi-app-kiosks"></a>Più app in modalità tutto schermo

Le app in questa modalità sono disponibili nel menu Start. Sono le uniche app che l'utente può aprire.

Quando si sceglie la modalità tutto schermo per più app, immettere le impostazioni seguenti:

- **Specifica Windows 10 come destinazione nei dispositivi in modalità S**: scegliere **Sì** per consentire le app dello Store e le app AUMID (sono escluse le app Win32) nel profilo in modalità tutto schermo. Scegli **No** per consentire le app dello Store, le app Win32 e le app AUMID nel profilo in modalità tutto schermo. Quando si sceglie **No**, questo profilo in modalità tutto schermo non viene distribuito nei dispositivi in modalità S.

- **Tipo di accesso utente**: le app aggiunte vengono eseguite con l'account utente immesso. Le opzioni disponibili sono:

  - **Accesso automatico (Windows 10, versione 1803+)**: per i dispositivi in modalità tutto schermo in ambienti pubblici che non richiedono all'utente di eseguire l'accesso, in modo simile a un account guest. Questa impostazione usa il [provider di servizi di configurazione AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Account utente locale**: **aggiungere** l'account utente locale (per il dispositivo). L'account specificato viene usato per accedere al chiosco multimediale.
  - **Utente o gruppo di Azure AD (Windows 10, versione 1803+)**: selezionare **Aggiungi** per scegliere gli utenti o i gruppi di Azure nell'elenco. È possibile selezionare più utenti e gruppi. Scegliere **OK** per salvare le modifiche.
  - **Visitatore di HoloLens**: l'account del visitatore è un account Guest che non richiede credenziali utente o autenticazione, come descritto in [Concetti della modalità PC condiviso](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Applicazioni**: aggiungere le app da eseguire nel dispositivo in modalità tutto schermo. Ricordarsi che è possibile aggiungere più app.

  - **Aggiungi l'app dello Store**: aggiungere un'app da Microsoft Store per le aziende. Se l'elenco non include alcuna app, è possibile ottenerle e [aggiungerle a Intune](store-apps-windows.md). Ad esempio, è possibile aggiungere un browser in modalità tutto schermo, Excel, OneNote e altro ancora.

  - **Aggiungi un'app di Win32**: un'app Win32 è un'app desktop tradizionale, ad esempio Visual Studio Code o Google Chrome. Immettere le seguenti proprietà:

    - **Nome applicazione**: obbligatorio. Immettere un nome per l'applicazione.
    - **Percorso locale**: obbligatorio. Immettere il percorso del file eseguibile, ad esempio `C:\Program Files (x86)\Microsoft VS Code\Code.exe` o `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **ID modello utente applicazione (AUMID)**: immettere l'ID modello utente applicazione dell'app Win32. Questa impostazione determina il layout iniziale del riquadro sul desktop. Per ottenere questo ID, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps) (Trovare l'ID modello utente dell'applicazione di un'app installata) per ottenere l'ID.
    - **Dimensioni del riquadro**: obbligatorio. Scegliere Piccolo, Medio o Grande per le dimensioni del riquadro.
  
  - **Aggiungi in base all'ID modello utente applicazione**: usare questa opzione per aggiungere app predefinite di Windows come il Blocco note o la Calcolatrice. Immettere le seguenti proprietà: 

    - **Nome applicazione**: obbligatorio. Immettere un nome per l'applicazione.
    - **ID modello utente applicazione (AUMID)**: obbligatorio. Immettere l'ID modello utente applicazione (AUMID) dell'app Windows. Per ottenere questo ID, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata) per ottenere l'ID.
    - **Dimensioni del riquadro**: obbligatorio. Scegliere Piccolo, Medio o Grande per le dimensioni del riquadro.

  > [!TIP]
  > Dopo aver aggiunto tutte le app, è possibile modificarne l'ordine di visualizzazione facendo clic e trascinando le app nell'elenco.  

  Selezionare **OK** per salvare le modifiche.

- **Impostazioni del browser in modalità tutto schermo**: queste impostazioni consentono di controllare un'app Web browser nel dispositivo in modalità tutto schermo. Assicurarsi di distribuire un'app Web browser ai dispositivi in modalità tutto schermo usando [App client](apps-add.md).

  Immettere le impostazioni seguenti:

  - **URL della home page predefinita**: immettere l'URL predefinito visualizzato all'apertura o al riavvio del browser in modalità tutto schermo. Ad esempio, immettere `http://bing.com` o `http://www.contoso.com`.

  - **Pulsante Pagina iniziale**: scegliere **Mostra** o **Nascondi** per il pulsante Pagina iniziale del browser in modalità tutto schermo. Per impostazione predefinita, il pulsante non viene visualizzato.

  - **Pulsanti di spostamento**: scegliere **Mostra** o **Nascondi** per i pulsanti Avanti e Indietro. Per impostazione predefinita, i pulsanti di spostamento non sono visualizzati.

  - **Pulsante Termina sessione**: scegliere **Mostra** o **Nascondi** per il pulsante Termina sessione. Quando visualizzato, l'utente seleziona il pulsante e l'app chiede conferma della chiusura della sessione. Se confermata, il browser cancella tutti i dati di esplorazione (cookie, cache e così via) e quindi apre l'URL predefinito. Per impostazione predefinita, il pulsante non viene visualizzato.

  - **Aggiorna il browser dopo il tempo di inattività**: immettere la quantità di tempo di inattività (da 1 a 1440 minuti) trascorso il quale il browser in modalità tutto schermo viene riavviato. Il tempo di inattività è il numero di minuti dopo l'ultima interazione dell'utente. Per impostazione predefinita, il valore è vuoto, ovvero non è configurato alcun timeout di inattività.

  - **Siti Web consentiti**: usare questa impostazione per consentire l'apertura di siti Web specifici. In altre parole, usare questa funzionalità per limitare o bloccare siti Web nel dispositivo. Ad esempio, è possibile consentire l'apertura di tutti i siti Web in `contoso.com*`. Per impostazione predefinita, sono consentiti tutti i siti Web.

    Per consentire siti Web specifici, caricare un file CSV che include un elenco dei siti Web consentiti. Se non si aggiunge un file CSV, sono consentiti tutti i siti Web.

  Selezionare **OK** per salvare le modifiche.

- **Usa un layout Start alternativo**: scegliere **Sì** per immettere un file XML che descrive come le app vengono visualizzate nel menu Start, incluso il relativo ordine. Usare questa opzione se è necessaria una maggiore personalizzazione nel menu Start. Leggere [Personalizzare ed esportare il layout della schermata Start](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) per conoscere alcune linee guida e XML di esempio.

- **Barra delle applicazioni di Windows**: scegliere **Mostra** o **Nascondi** per la barra delle applicazioni. Per impostazione predefinita, la barra delle applicazioni non viene visualizzata.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

È possibile configurare i dispositivi Windows Holographic for Business per l'esecuzione di una o più app in modalità tutto schermo. Alcune funzionalità non sono supportate in Windows Holographic for Business.

#### <a name="single-full-screen-app-kiosks"></a>App singola per chioschi multimediali a schermo intero
Quando si sceglie la modalità App singola per chiosco multimediale a schermo intero, immettere le impostazioni seguenti:

- **Tipo di accesso utente**: selezionare **Account utente locale** per immettere l'account utente locale (per il dispositivo) oppure un account Microsoft associato all'app in modalità tutto schermo. I tipi di account utente con **accesso automatico** non sono supportati in Windows Holographic for Business.

- **Tipo di applicazione**: selezionare **App Store**.

- **App da eseguire in modalità tutto schermo**: scegliere **Aggiungi un'app dello Store** e selezionare un'app nell'elenco.

    Se l'elenco non include app, aggiungerne qualcuna seguendo la procedura in [App client](apps-add.md).

    Selezionare **OK** per salvare le modifiche.

#### <a name="multi-app-kiosks"></a>Più app in modalità tutto schermo
Le app in questa modalità sono disponibili nel menu Start. Sono le uniche app che l'utente può aprire. Quando si sceglie la modalità tutto schermo per più app, immettere le impostazioni seguenti:

- **Specifica Windows 10 come destinazione nei dispositivi in modalità S**: scegliere **No**. La modalità S non è supportata in Windows Holographic for Business.

- **Tipo di accesso utente**: aggiungere uno o più account utente autorizzati a usare le app aggiunte. Le opzioni disponibili sono: 

  - **Accesso automatico**: opzione non supportata in Windows Holographic for Business.
  - **Account utente locale**: scegliere **Aggiungi** per aggiungere l'account utente locale (per il dispositivo). L'account specificato viene usato per accedere al chiosco multimediale.
  - **Utente o gruppo di Azure AD (Windows 10, versione 1803+)**: richiede le credenziali utente per accedere al dispositivo. Selezionare **Aggiungi** per scegliere utenti o gruppi di Azure AD nell'elenco. È possibile selezionare più utenti e gruppi. Scegliere **OK** per salvare le modifiche.
  - **Visitatore di HoloLens**: l'account del visitatore è un account Guest che non richiede credenziali utente o autenticazione, come descritto in [Concetti della modalità PC condiviso](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Applicazioni**: aggiungere le app da eseguire nel dispositivo in modalità tutto schermo. Ricordarsi che è possibile aggiungere più app.

  - **Aggiungi l'app dello Store**: selezionare un'app esistente aggiunta tramite [App client](apps-add.md). Se l'elenco non include alcuna app, è possibile ottenerle e [aggiungerle a Intune](store-apps-windows.md).
  - **Aggiungi app di Win32**: opzione non supportata in Windows Holographic for Business.
  - **Aggiungi in base all'ID modello utente applicazione**: usare questa opzione per aggiungere app predefinite di Windows. Immettere le seguenti proprietà: 

    - **Nome applicazione**: obbligatorio. Immettere un nome per l'applicazione.
    - **ID modello utente applicazione (AUMID)**: obbligatorio. Immettere l'ID modello utente applicazione (AUMID) dell'app Windows. Per ottenere questo ID, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata) per ottenere l'ID.
    - **Dimensioni del riquadro**: obbligatorio. Scegliere Piccolo, Medio o Grande per le dimensioni del riquadro.

- **Impostazioni del browser in modalità tutto schermo**: opzione non supportata in Windows Holographic for Business.

- **Usa un layout Start alternativo**: scegliere **Sì** per immettere un file XML che descrive come le app vengono visualizzate nel menu Start, incluso il relativo ordine. Usare questa opzione se è necessaria una maggiore personalizzazione nel menu Start. [Personalizzare ed esportare il layout della schermata Start](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) offre alcune indicazioni e include un file XML specifico per i dispositivi Windows Holographic for Business.

- **Barra delle applicazioni di Windows**: opzione non supportata in Windows Holographic for Business.



## <a name="next-steps"></a>Passaggi successivi
[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
