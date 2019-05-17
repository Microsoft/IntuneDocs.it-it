---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni e le relative descrizioni per la creazione di limitazioni per i dispositivi in Windows 10 e versioni successive. Usare queste impostazioni in un profilo di configurazione per controllare screenshot, requisiti per le password, impostazioni della modalità tutto schermo, app nello Store, browser Microsoft Edge, Windows Defender, accesso al cloud, menu Start e altro in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8957c8d8aad2eaa1741b1a625afd4b5a41a8bb51
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423697"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Impostazioni dei dispositivi Windows 10 (e versioni successive) per consentire o limitare l'uso delle funzionalità tramite Intune

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi Windows 10 e versioni successive. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per abilitare o disabilitare funzionalità, impostare regole per le password, personalizzare la schermata di blocco, usare Windows Defender e altro ancora.

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo in Intune e quindi assegnate o distribuite ai dispositivi Windows 10.

> [!Note]
> Non tutte le opzioni sono disponibili in tutte le edizioni di Windows. Per informazioni sulle edizioni supportate, vedere [Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Provider di servizi di configurazione dei criteri) (viene aperto un altro sito Web Microsoft).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>App Store

- **App Store (solo dispositivi mobili)**: consente o blocca l'uso dell'App Store nei dispositivi Windows 10 Mobile.
- **Aggiorna automaticamente le app dallo Store**: consente l'aggiornamento automatico delle app installate da Microsoft Store.
- **Installazione di app attendibile**: consente il trasferimento locale delle app con certificato attendibile.
- **Sblocco dallo sviluppatore**: consente all'utente finale di modificare le impostazioni per gli sviluppatori Windows, ad esempio consentire il trasferimento locale delle app.
- **Dati app utente condivisi**: consente alle app di condividere dati tra utenti diversi dello stesso dispositivo.
- **Usa solo lo Store privato**: abilitare questa opzione per consentire agli utenti finali di scaricare app solo da uno Store privato.
- **Avvio di app originate dallo Store**: consente di disabilitare tutte le app preinstallate nel dispositivo o scaricate da Microsoft Store.
- **Installa i dati dell'app nel volume di sistema**: impedisce alle app di archiviare dati nel volume di sistema del dispositivo.
- **Installa le app nell'unità di sistema**: impedisce alle app di archiviare dati nell'unità di sistema del dispositivo.
- **Game DVR (solo desktop)**: configura se la registrazione e la trasmissione dei giochi sono consentite.
- **App solo dallo Store**: specifica se gli utenti possono installare le app da posizioni diverse dall'App Store.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività

- **Canale per rete dati**: impedisce agli utenti di usare dati, ad esempio di esplorare il Web, mentre sono connessi a una rete dati. 
- **Roaming dati**: consente il roaming tra reti quando si accede ai dati.
- **VPN nella rete cellulare**: controlla se il dispositivo può accedere a connessioni VPN quando è collegato a una rete cellulare.
- **Roaming VPN nella rete cellulare**: controlla se il dispositivo può accedere a connessioni VPN quando è in roaming su una rete cellulare.
- **Bluetooth**: controlla se l'utente può abilitare e configurare Bluetooth nel dispositivo.
- **Individuabilità di Bluetooth**: consente l'individuazione del dispositivo da altri dispositivi con la funzione Bluetooth attivata.
- **Pre-associazione Bluetooth**: consente di configurare dispositivi Bluetooth specifici per l'associazione automatica a un dispositivo host.
- **Annunci con Bluetooth**: consente al dispositivo di ricevere annunci tramite Bluetooth.
- **Servizio dispositivi connessi**: consente di scegliere se consentire il servizio dispositivi connessi, che abilita l'individuazione e la connessione ad altri dispositivi Bluetooth.
- **NFC**: consente all'utente di abilitare e configurare le funzionalità NFC (Near Field Communications) nel dispositivo.
- **Wi-Fi**: consente all'utente di attivare e configurare le funzionalità Wi-Fi nel dispositivo (solo Windows 10 Mobile).
- **Connetti automaticamente a hotspot Wi-Fi**: consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente termini e condizioni per la connessione.
- **Configurazione Wi-Fi manuale**: controlla se l'utente può configurare le proprie connessioni Wi-Fi o se può usare solo le connessioni configurate da un profilo Wi-Fi (solo Windows 10 Mobile).
- **Intervallo di analisi Wi-Fi**: immettere la frequenza con cui i dispositivi ricercano le reti Wi-Fi. Immettere un valore compreso tra 1 (ricerca più frequente) e 500 (ricerca meno frequente).
- **Servizi Bluetooth consentiti**: immettere sotto forma di stringhe esadecimali un elenco di profili e servizi Bluetooth consentiti.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione

- **Account Microsoft**: consente all'utente di associare un account Microsoft al dispositivo.
- **Account non Microsoft**: consente all'utente di aggiungere account di posta elettronica al dispositivo che non sono associati a un account Microsoft.
- **Sincronizzazione delle impostazioni per l'account Microsoft**: consente che le impostazioni del dispositivo e delle app associate a un account Microsoft vengano sincronizzate fra i dispositivi.
- **Assistente per l'accesso all'account Microsoft**: scegliere **Disabilita** per impedire agli utenti finali di controllare il servizio dell'assistente per l'accesso Microsoft (wlidsvc), ad esempio arrestando o avviando manualmente il servizio. Se impostato su **Non configurato**, il servizio NT (wlidsvc) usa l'impostazione predefinita del sistema operativo, che può consentire agli utenti finali di avviare e arrestare il servizio. Questo servizio viene usato dal sistema operativo per consentire agli utenti di accedere al proprio account Microsoft.

## <a name="cloud-printer"></a>Stampante cloud

- **URL di individuazione stampanti**: immettere l'URL per l'individuazione delle stampanti nel cloud.
- **URL dell'autorità per l'accesso alle stampanti**: immettere l'URL dell'endpoint di autenticazione per l'acquisizione di token OAuth. Ad esempio, `https://login.microsoftonline.com/your Azure AD Tenant ID`.
- **GUID dell'app client nativa di Azure**: immettere l'identificatore univoco globale dell'applicazione client autorizzata a recuperare token OAuth da OAuthAuthority.
- **URI della risorsa del servizio di stampa**: immettere l'URI della risorsa OAuth per il servizio di stampa configurato nel portale di Azure. Ad esempio, `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Numero massimo di stampanti da sottoporre a query (solo dispositivi mobili)**: immettere il numero massimo di stampanti da sottoporre a query. Immettere ad esempio `10`.
- **URI della risorsa del servizio di individuazione**: immettere l'URI della risorsa OAuth per il servizio di individuazione delle stampanti configurato nel portale di Azure. Ad esempio, `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Dopo aver configurato [Hybrid Cloud Print di Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), è possibile configurare queste impostazioni e quindi eseguire la distribuzione ai dispositivi Windows.

## <a name="control-panel-and-settings"></a>Pannello di controllo e impostazioni

- **App Impostazioni**: blocca l'accesso all'app Impostazioni di Windows.
  - **Sistema**: blocca l'accesso all'area di sistema dell'app Impostazioni.
    - **Modifica delle impostazioni di risparmio energia e sospensione (solo desktop)**: impedisce all'utente finale di modificare le impostazioni di risparmio energia e sospensione del dispositivo.
  - **Dispositivi**: blocca l'accesso all'area dei dispositivi dell'app Impostazioni.
  - **Rete Internet**: blocca l'accesso all'area rete e Internet dell'app Impostazioni.
  - **Personalizzazione**: blocca l'accesso all'area di personalizzazione dell'app Impostazioni.
  - **Account**: blocca l'accesso all'area degli account dell'app Impostazioni.
  - **Ora e lingua**: blocca l'accesso all'area dell'ora e della lingua dell'app Impostazioni.
    - **Modifica dell'ora di sistema**: impedisce all'utente finale di modificare la data e l'ora del dispositivo.
    - **Modifica delle impostazioni dell'area (solo desktop)**: impedisce all'utente finale di modificare le impostazioni dell'area del dispositivo.
    - **Modifiche alle impostazioni della lingua (solo desktop)**: impedisce all'utente finale di modificare le impostazioni della lingua del dispositivo.
  - **Giochi**: blocca l'accesso all'app Giochi in Impostazioni.
  - **Accessibilità**: blocca l'accesso all'area accessibilità dell'app Impostazioni.
  - **Privacy**: blocca l'accesso all'area privacy dell'app Impostazioni.
  - **Aggiornamento e sicurezza** : blocca l'accesso all'area Aggiornamento e sicurezza dell'app Impostazioni.

## <a name="display"></a>Schermo

- **Attiva il ridimensionamento del programma GDI per le app**
- **Disattiva il ridimensionamento del programma GDI per le ap**

  Il ridimensionamento DPI del programma GDI consente alle app non sensibili ai valori DPI di diventare sensibili ai valori DPI per monitor. Immettere le app legacy con ridimensionamento DPI del programma GDI attivato. Quando il ridimensionamento DPI del programma GDI è configurato per l'attivazione e per la disattivazione in un'app, il ridimensionamento è disattivato per l'app.

## <a name="general"></a>Generale

- **Acquisizione di schermata (solo dispositivi mobili)**: consente all'utente di acquisire la schermata del dispositivo come immagine.
- **Copia e incolla (solo dispositivi mobili)**: consente le azioni di copia e incolla tra app sul dispositivo.
- **Annullamento manuale della registrazione**: consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.
  - Questa impostazione dei criteri non è applicabile se il computer è stato aggiunto ad Azure AD e la registrazione automatica è abilitata. 
  - Questa impostazione dei criteri non si applica ai computer con Windows 10 Home.
- **Installazione manuale del certificato radice (solo per dispositivi mobili)**: impedisce all'utente di installare manualmente i certificati radice e i certificati intermedi CAP.

- **Fotocamera**: consente o blocca l'uso della fotocamera nel dispositivo.
- **Sincronizzazione dei file di OneDrive**: impedisce al dispositivo di sincronizzare i file in OneDrive.
- **Archivi rimovibili**: specifica se è possibile usare con il dispositivo supporti di archiviazione esterni come le schede SD.
- **Georilevazione**: specifica se il dispositivo può usare le informazioni dei servizi di posizione.
- **Internet condiviso**: consente l'uso della condivisione della connessione Internet nel dispositivo.
- **Ripristino delle impostazioni predefinite del telefono**: controlla se l'utente può eseguire una cancellazione del dispositivo.
- **Connessione USB (solo per dispositivi mobili)**: controlla se i dispositivi possono accedere a dispositivi di archiviazione esterni tramite una connessione USB.
- **Modalità antifurto (solo per dispositivi mobili)**: configura l'attivazione della modalità antifurto di Windows.
- **Cortana**: abilita o disabilita l'assistente vocale Cortana.
- **Registrazione voce (solo per dispositivi mobili)**: consente o impedisce l'uso del registratore vocale del dispositivo.
- **Modifica del nome del dispositivo**: impedisce all'utente finale di modificare il nome del dispositivo (solo Windows 10 Mobile).
- **Aggiungi pacchetti di provisioning**: blocca l'agente di configurazione di runtime che installa i pacchetti di provisioning.
- **Rimuovi i pacchetti di provisioning**: blocca l'agente di configurazione di runtime che rimuove i pacchetti di provisioning.
- **Individuazione dei dispositivi**: impedisce l'individuazione di un dispositivo da parte di altri dispositivi.
- **Cambio modalità per l'attività (solo dispositivi mobili)**: blocca il cambio modalità per l'attività nel dispositivo.
- **Finestra di dialogo di errore per la scheda SIM (solo dispositivi mobili)**: blocca la visualizzazione di un messaggio di errore nel dispositivo se non viene rilevata alcuna scheda SIM.
- **Area Ink**: impedisce agli utenti l'accesso all'area di lavoro Windows Ink. **Non configurata** attiva l'area Ink e l'utente è autorizzato a usarla sopra la schermata di blocco.
- **Ridistribuzione automatica**: consente agli utenti con diritti amministrativi di eliminare tutti i dati utente e tutte le impostazioni utente tramite **CTRL+tasto WINDOWS+R** nella schermata di blocco del dispositivo. Il dispositivo viene automaticamente riconfigurato e registrato di nuovo nella gestione.
- **Richiedi agli utenti di connettersi alla rete durante la configurazione del dispositivo**: scegliere **Rendi obbligatorio** per fare in modo che il dispositivo si connetta a una rete prima di procedere oltre la pagina Rete durante l'installazione di Windows 10.

  L'impostazione diventa effettiva alla successiva cancellazione o reimpostazione del dispositivo. Come per qualsiasi altra configurazione di Intune, è necessario che il dispositivo sia registrato e gestito da Intune al fine di ricevere le impostazioni di configurazione. Ma dopo che è stato registrato e che riceve i criteri, la reimpostazione del dispositivo determina l'applicazione dell'impostazione durante l'installazione di Windows successiva.

- **Accesso diretto alla memoria (DMA)**: **Blocca** consente di impedire l'accesso diretto alla memoria (DMA) per tutte le porte downstream PCI collegabili a caldo finché un utente non accede a Windows. **Abilitato** (impostazione predefinita) consente l'accesso diretto alla memoria, anche quando un utente non è connesso.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Termina processi da Gestione attività**: questa impostazione determina se gli utenti non amministratori possono usare Gestione attività per terminare le attività. **Blocca** impedisce agli utenti standard (non amministratori) di usare Gestione attività per terminare un processo o un'attività nel dispositivo. **Non configurata** (impostazione predefinita) consente agli utenti standard di terminare un processo o un'attività usando Gestione attività.

## <a name="locked-screen-experience"></a>Esperienza della schermata bloccata

- **Notifiche del centro notifiche (solo per dispositivi mobili)**: consente la visualizzazione delle notifiche del centro notifiche nella schermata di blocco del dispositivo (solo Windows 10 Mobile).
- **URL dell'immagine della schermata bloccata (solo desktop)**: immettere l'URL di un'immagine in formato JPEG da usare come sfondo della schermata bloccata di Windows. Questa impostazione blocca l'immagine. L'immagine non potrà essere modificata in seguito.
- **Timeout dello schermo configurabile dall'utente (solo dispositivi mobili)**: consente agli utenti di configurare il timeout. 
- **Cortana nella schermata di blocco (solo desktop)**: non consente all'utente di interagire con Cortana quando è attiva la schermata di blocco del dispositivo (solo Windows 10 Desktop).
- **Notifiche di tipo avviso popup nella schermata di blocco**: blocca la visualizzazione dei messaggi di avviso nella schermata di blocco del dispositivo.
- **Timeout dello schermo (solo dispositivi mobili)**: specifica il tempo in secondi tra il blocco e lo spegnimento dello schermo.

## <a name="messaging"></a>Messaggistica

- **Sincronizzazione di messaggi (solo dispositivi mobili)**: disabilitare i messaggi su qualsiasi dispositivo e il backup e il ripristino di SMS.
- **MMS (solo dispositivi mobili)**: disabilitare la funzionalità di invio/ricezione di MMS nel dispositivo.
- **RCS (solo dispositivi mobili)**: disabilitare la funzionalità di invio/ricezione di RCS (Rich Communication Services) nel dispositivo.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

### <a name="use-microsoft-edge-kiosk-mode"></a>Usa la modalità tutto schermo di Microsoft Edge

Le impostazioni disponibili variano a seconda delle scelte effettuate. Le opzioni disponibili sono:

- **No** (impostazione predefinita): Microsoft Edge non viene eseguito in modalità tutto schermo. È possibile modificare e configurare tutte le impostazioni di Microsoft Edge.
- **Insegna digitale o schermo interattivo (app singola in modalità tutto schermo)**: filtra le impostazioni di Microsoft Edge applicabili alla modalità tutto schermo di Microsoft Edge Insegna digitale o schermo interattivo per l'uso solo in app singole in modalità tutto schermo Windows 10. Scegliere questa impostazione per aprire un URL a tutto schermo e visualizzare solo il contenuto di quel sito Web. [Set up digital signs](https://docs.microsoft.com/windows/configuration/setup-digital-signage) (Configurare insegne digitali) offre altre informazioni su questa funzionalità.
- **Esplorazione pubblica InPrivate (app singola in modalità tutto schermo)**: filtra le impostazioni di Microsoft Edge applicabili alla modalità tutto schermo di Microsoft Edge Esplorazione pubblica InPrivate per l'uso in app singole in modalità tutto schermo Windows 10. Esegue una versione a schede multiple di Microsoft Edge.
- **Modalità normale (più app in modalità tutto schermo)**: filtra le impostazioni di Microsoft Edge applicabili alla modalità tutto schermo di Microsoft Edge normale. Esegue una versione completa di Microsoft Edge con tutte le funzionalità di esplorazione.
- **Esplorazione pubblica (più app in modalità tutto schermo)**: filtra le impostazioni di Microsoft Edge applicabili all'esplorazione pubblica in più app in modalità tutto schermo Windows 10.  Esegue una versione a schede multiple di Microsoft Edge InPrivate.

> [!TIP]
> Per altre informazioni su queste opzioni, vedere [Microsoft Edge kiosk mode configuration types](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types) (Tipi di configurazione della modalità tutto schermo di Microsoft Edge).

Questo profilo di restrizioni per i dispositivi è direttamente correlato al profilo in modalità tutto schermo creato usando le [impostazioni della modalità tutto schermo di Windows](kiosk-settings-windows.md). Per concludere:

1. Creare il profilo con le [impostazioni della modalità tutto schermo di Windows](kiosk-settings-windows.md) per eseguire il dispositivo in modalità tutto schermo. Selezionare Microsoft Edge come applicazione e impostare la modalità tutto schermo di Microsoft Edge nel profilo in modalità tutto schermo.
2. Creare il profilo di restrizioni per i dispositivi descritto in questo articolo e configurare funzionalità e impostazioni specifiche consentite in Microsoft Edge. Assicurarsi di scegliere lo stesso tipo di modalità tutto schermo di Microsoft Edge di quello selezionato nel profilo in modalità tutto schermo ([impostazioni della modalità tutto schermo di Windows](kiosk-settings-windows.md)). 

    [Supported kiosk mode settings](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) (Impostazioni supportate per la modalità tutto schermo) è un'ottima risorsa.

> [!IMPORTANT] 
> Assicurarsi di assegnare questo profilo di Microsoft Edge agli stessi dispositivi del profilo in modalità tutto schermo ([impostazioni della modalità tutto schermo di Windows](kiosk-settings-windows.md)).

[CSP ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Esperienza di avvio

- **Avvia Microsoft Edge con**: scegliere quali pagine si aprono all'avvio di Microsoft Edge. Le opzioni disponibili sono:
  - **Pagine iniziali**: Microsoft Edge viene avviato con la pagina iniziale predefinita definita dal sistema operativo
  - **Pagina Nuova scheda**: Microsoft Edge carica qualsiasi pagina definita con l'impostazione **URL della pagina Nuova scheda**
  - **Pagina dell'ultima sessione**: Microsoft Edge carica la pagina dell'ultima sessione 
  - **Pagine iniziali personalizzate**: Microsoft Edge caricata la pagina iniziale definita dall'amministratore IT
- **L'utente può modificare le pagine iniziali**: **Consenti** consente agli utenti di modificare le pagine iniziali. Gli amministratori possono usare `EdgeHomepageUrls` per immettere le pagine iniziali che gli utenti visualizzano per impostazione predefinita all'apertura di Microsoft Edge. **Non configurata** impedisce agli utenti di modificare le pagine iniziali.
- **URL della pagina Nuova scheda**: immettere l'URL da aprire nella pagina Nuova scheda. Immettere ad esempio `https://www.bing.com`.
- **Apri contenuti Web nella pagina della nuova scheda**: scegliere **Blocca** per impedire a Microsoft Edge di aprire un sito Web in una nuova scheda. Quando è bloccata, la pagina della nuova scheda è vuota. **Non configurata** usa il comportamento predefinito del sistema operativo nel dispositivo, che può consentire agli utenti di scegliere cosa visualizzare.
- **Pulsante Pagina iniziale**: scegliere cosa accade quando si seleziona il pulsante Pagina iniziale. Le opzioni disponibili sono:
  - **Pagine iniziali**: viene aperta la pagina scelta per l'impostazione **Avvia Microsoft Edge con**
  - **Pagina Nuova scheda**: viene aperta la pagina scelta per l'impostazione **URL della pagina Nuova scheda**
  - **URL personalizzato del pulsante Pagina iniziale**: viene aperta la pagina scelta per l'impostazione **URL del pulsante Pagina iniziale**
  - **Nascondi il pulsante Pagina iniziale**: nasconde il pulsante Pagina iniziale
- **L'utente può modificare il pulsante Pagina iniziale**: **Consenti** consente agli utenti di modificare il pulsante Pagina iniziale. Le modifiche dell'utente sostituiscono eventuali impostazioni dell'amministratore per il pulsante Pagina iniziale. **Non configurata** usa il comportamento predefinito del sistema operativo nel dispositivo, che potrebbe impedire agli utenti di modificare la configurazione dell'amministratore per il pulsante Pagina iniziale.
- **Mostra la pagina del completamento dell'installazione**: **Blocca** impedisce la visualizzazione della pagina introduttiva quando si esegue Microsoft Edge per la prima volta. Questa funzionalità consente alle aziende, ad esempio le organizzazioni registrate in configurazioni a zero emissioni, di bloccare questa pagina. **Non configurata** mostra la pagina introduttiva.
  - **URL di completamento dell'installazione**: immettere l'URL della pagina visualizzata alla prima esecuzione di Microsoft Edge (solo Windows 10 Mobile).
- **Aggiorna il browser dopo il tempo di inattività**: immettere il numero di minuti di inattività trascorsi i quali il browser viene aggiornato, da 0 a 1440 minuti. L'impostazione predefinita è `5` minuti. Se impostata su `0` (zero), il browser non viene aggiornato dopo essere stato inattivo.

  Questa impostazione è disponibile solo in modalità [Esplorazione pubblica InPrivate (app singola in modalità tutto schermo)](#use-microsoft-edge-kiosk-mode).

  CSP: [ConfigureKioskResetAfterIdleTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskresetafteridletimeout)

- **Popup**: scegliere **Blocca** per bloccare le finestre popup nel browser. Si applica solo a Windows 10 Desktop. **Non configurata** consente i popup nel Web browser.
- **Invia traffico Intranet a Internet Explorer**: **Consenti** consente agli utenti di aprire siti Web della Intranet in Internet Explorer invece che in Microsoft Edge (solo per Windows 10 Desktop). **Non configurata** consente agli utenti di usare Microsoft Edge.
- **Posizione dell'elenco di siti con modalità Enterprise**: immettere l'URL che include un elenco di siti Web che si aprono in modalità Enterprise. Gli utenti non possono modificare questo elenco. Si applica solo a Windows 10 Desktop.
- **Messaggio all'apertura di siti in Internet Explorer**: usare questa impostazione per configurare Microsoft Edge per visualizzare una notifica prima dell'apertura di un sito in Internet Explorer 11. Le opzioni disponibili sono:
  - **Non configurata**: viene usato il comportamento predefinito del sistema operativo, che potrebbe non prevedere la visualizzazione di un messaggio.
  - **Mostra il messaggio senza l'opzione per l'apertura di siti in Microsoft Edge**: consente di visualizzare il messaggio all'apertura di siti in Internet Explorer. I siti vengono aperti in Internet Explorer. Non è disponibile un'opzione per aprire i siti in Microsoft Edge.
  - **Mostra un messaggio all'apertura dei siti in Microsoft Edge**: consente di visualizzare il messaggio all'apertura di siti in Internet Explorer. Il messaggio include un collegamento **Continua in Microsoft Edge** in modo che gli utenti possano scegliere Microsoft Edge invece di Internet Explorer.

  > [!IMPORTANT]
  > Questa impostazione richiede l'abilitazione dell'impostazione **Configura elenco siti modalità Enterprise**, dell'impostazione **Invia tutti i siti Intranet a Internet Explorer 11** o di entrambe.

- **Elenco di compatibilità Microsoft**: **Blocca** impedisce l'uso dell'elenco di compatibilità Microsoft in Microsoft Edge. Questo elenco fornito da Microsoft aiuta Microsoft Edge a visualizzare in modo appropriato i siti con problemi di compatibilità noti. **Non configurata** consente l'uso di un elenco di compatibilità Microsoft.
- **Precarica le pagine iniziali e la pagina Nuova scheda**: scegliere **Blocca** per impedire a Microsoft Edge di precaricare le pagine iniziali e la pagina Nuova scheda. Il precaricamento riduce al minimo il tempo necessario per avviare Microsoft Edge e caricare una nuova scheda. **Non configurata** usa il comportamento predefinito del sistema operativo, che potrebbe prevedere il precaricamento di queste pagine.
- **Preavvia le pagine iniziali e la pagina Nuova scheda**: scegliere **Blocca** per impedire a Microsoft Edge di preavviare le pagine iniziali e la pagina Nuova scheda. Il preavvio contribuisce a migliorare le prestazioni di Microsoft Edge e riduce al minimo il tempo necessario per avviare Microsoft Edge. **Non configurata** usa il comportamento predefinito del sistema operativo, che potrebbe prevedere il preavvio di queste pagine.

### <a name="favorites-and-search"></a>Preferiti e ricerca

- **Barra Preferiti**: scegliere cosa accade alla barra Preferiti in qualsiasi pagina di Microsoft Edge. Le opzioni disponibili sono:
  - **Non configurata**: usa il comportamento predefinito del sistema operativo, che potrebbe nascondere la barra Preferiti in tutte le pagine. L'utente può modificare questa impostazione.
  - **Nascondi**: nasconde la barra Preferiti in tutte le pagine. L'utente non può modificare questa impostazione.
  - **Mostra**: mostra la barra Preferiti in tutte le pagine. L'utente non può modificare questa impostazione.
- **Elenco Preferiti**: aggiungere un elenco di URL al file dei Preferiti. Ad esempio: aggiungere `http://contoso.com/favorites.html`.
- **Limita le modifiche ai Preferiti**: **Blocca** per impedire agli utenti di eseguire operazioni di aggiunta, importazione, ordinamento o modifica dell'elenco Preferiti. **Non configurata** usa l'impostazione predefinita del sistema operativo, che potrebbe consentire agli utenti di modificare l'elenco.
- **Sincronizza i Preferiti tra i browser Microsoft (solo desktop)**: **Rendi obbligatorio** impone la sincronizzazione dei Preferiti tra Microsoft Edge e Internet Explorer in Windows. Le aggiunte, le eliminazioni, le modifiche e le variazioni dell'ordine dei Preferiti vengono condivise tra i browser.  **Non configurata** usa l'impostazione predefinita del sistema operativo, che può consentire agli utenti di scegliere di sincronizzare i Preferiti tra i browser.
- **Motore di ricerca predefinito**: scegliere il motore di ricerca predefinito nel dispositivo. Gli utenti finali possono modificare questo valore in qualsiasi momento. Le opzioni disponibili sono:
  - Predefinito
  - Bing
  - Google
  - Yahoo
  - Valore personalizzato
- **Suggerimenti per la ricerca**: **Non configurata** consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca nella barra degli indirizzi. **Blocca** impedisce questa funzionalità.
- **Consenti modifiche al motore di ricerca**: **Sì** (impostazione predefinita) consente agli utenti di aggiungere nuovi motori di ricerca o di cambiare quello predefinito in Microsoft Edge. Scegliere **No** per impedire agli utenti di personalizzare il motore di ricerca.

  Questa impostazione è disponibile solo in [Modalità normale (più app in modalità tutto schermo)](#use-microsoft-edge-kiosk-mode).

  CSP: [AllowSearchEngineCustomization](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsearchenginecustomization)

### <a name="privacy-and-security"></a>Privacy e sicurezza

- **InPrivate Browsing**: **Blocca** impedisce agli utenti finali di aprire sessioni InPrivate Browsing. **Non configurata** consente questa funzionalità.
- **Salva la cronologia esplorazioni**: **Blocca** impedisce a Microsoft Edge di salvare la cronologia esplorazioni. **Non configurata** consentire il salvataggio della cronologia esplorazioni.
- **Cancella i dati di esplorazione all'uscita (solo desktop)** : **Rendi obbligatorio** cancella la cronologia e i dati di esplorazione quando l'utente esce da Microsoft Edge. **Non configurata** usa il valore predefinito del sistema operativo, che potrebbe memorizzare nella cache i dati di esplorazione.
- **Sincronizza le impostazioni del browser tra i dispositivi dell'utente**: scegliere come si vogliono sincronizzare le impostazioni del browser tra i dispositivi. Le opzioni disponibili sono:
  - **Consenti**: consente la sincronizzazione delle impostazioni del browser Microsoft Edge tra i dispositivi dell'utente
  - **Block and enable user override** (Blocca e consenti modifica da parte dell'utente): blocca la sincronizzazione delle impostazioni del browser Microsoft Edge tra i dispositivi dell'utente. Gli utenti possono modificare questa impostazione.
  - **Blocca**: blocca la sincronizzazione delle impostazioni del browser Microsoft Edge tra i dispositivi dell'utente. Gli utenti non possono sostituire questa impostazione.
- **Strumento per la gestione delle password**: **Blocca** disabilita la funzione di gestione password di Microsoft Edge. **Non configurata** consente questa funzionalità.
- **Cookie**: scegliere come vengono gestiti i cookie nel Web browser. Le opzioni disponibili sono:
  - **Consenti**: i cookie vengono archiviati nel dispositivo.
  - **Blocca tutti i cookie**: i cookie non vengono archiviati nel dispositivo.
  - **Blocca solo i cookie di terze parti**: i cookie di partner o terze parti non vengono archiviati nel dispositivo.
- **Riempimento automatico**: **Blocca** disabilita la funzionalità di riempimento automatico nel dispositivo. **Non configurata** consente agli utenti di modificare le impostazioni di completamento automatico nel browser (solo per Windows 10 Desktop).
- **Invia intestazioni DNT (Do Not Track)**: **Non configurata** richiede ai dispositivi di inviare le intestazioni DNT (Do Not Track) ai siti Web che richiedono informazioni di traccia (scelta consigliata). Scegli **Blocca** per impedire al dispositivo di inviare queste intestazioni, che consentono ai siti Web di tracciare l'utente.
- **Indirizzo IP localhost WebRtc**: **Blocca** impedisce la visualizzazione dell'indirizzo IP localhost degli utenti quando eseguono telefonate tramite il protocollo Web RTC. **Non configurata** consente la visualizzazione dell'indirizzo IP localhost degli utenti quando eseguono telefonate con questo protocollo.
- **Raccolta di dati per il riquadro animato**: scegliere **Blocca** per impedire a Windows di raccogliere informazioni dal riquadro animato, ovvero un sito aggiunto al menu Start da Microsoft Edge. **Non configurata** consente la raccolta di queste informazioni.
- **L'utente può eseguire l'override degli errori del certificato**: **Blocca** impedisce agli utenti di accedere ai siti Web che contengono errori SSL o TLS. **Non configurata** consente agli utenti di accedere a questi siti.

### <a name="additional"></a>Ulteriori informazioni

- **Browser Microsoft Edge (solo per dispositivi mobili)**: scegliere **Blocca** per impedire l'uso di Microsoft Edge nel dispositivo. Se si blocca Microsoft Edge, le singole impostazioni si applicano solo al desktop. **Non configurata** consente l'uso del Web browser Microsoft Edge nel dispositivo.
- **Elenco a discesa della barra degli indirizzi (solo desktop)**: **Blocca** impedisce a Microsoft Edge di visualizzare un elenco di suggerimenti in un elenco a discesa durante la digitazione. Questa opzione consente di ridurre al minimo l'uso della larghezza di banda tra Microsoft Edge e i servizi Microsoft. **Non configurata** consente a Microsoft Edge di visualizzare un elenco di suggerimenti.
- **Schermo intero**: scegliere **Blocca** per impedire a Microsoft Edge di visualizzare solo il contenuto Web nascondendo Microsoft Edge (modalità a schermo intero). **Non configurata** usa l'impostazione predefinita del sistema operativo, che consente a Microsoft Edge di usare la modalità a schermo intero.
- **Flag Informazioni su**: **Blocca** impedisce agli utenti finali di accedere alla pagina `about:flags` in Microsoft Edge che include le impostazioni sperimentali e per gli sviluppatori. **Non configurata** usa il valore predefinito del sistema operativo, che potrebbe consentire l'accesso alla pagina `about:flags`.
- **Strumenti di sviluppo**: **Blocca** impedisce agli utenti finali di aprire gli strumenti di sviluppo di Microsoft Edge. **Non configurata** consente agli utenti di aprire gli strumenti di sviluppo.
- **Estensioni**: **Non configurata** consente agli utenti di installare le estensioni di Microsoft Edge nel dispositivo. **Blocca** impedisce l'installazione.
- **Sideload delle estensioni per sviluppatori**: **Blocca** impedisce a Microsoft Edge di eseguire il sideload, quindi installa ed esegue le estensioni non verificate usando la funzionalità **Carica estensioni**. **Non configurata** usa il valore predefinito del sistema operativo, che potrebbe consentire il sideload.
- **Estensioni obbligatorie**: scegliere le estensioni che non possono essere disattivate dagli utenti finali in Microsoft Edge. Immettere i nomi delle famiglie di pacchetti e selezionare **Aggiungi**. In [Trovare un nome di famiglia di pacchetti (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) sono disponibili alcune linee guida.

  È anche possibile **importare** un file CSV che include i nomi delle famiglie di pacchetti.

- **JavaScript**: scegliere **Blocca** per impedire l'esecuzione nel dispositivo degli script Java nel browser. **Non configurata**: consente di eseguire script, ad esempio JavaScript, nel browser Microsoft Edge.

## <a name="network-proxy"></a>Proxy di rete

- **Rileva automaticamente impostazioni proxy**: se questa opzione è abilitata il dispositivo tenta di trovare il percorso per uno script PAC.
- **Usa lo script proxy**: selezionare questa opzione per immettere un percorso per uno script PAC per configurare il server proxy.
  - **URL dell'indirizzo dello script di installazione**: immettere l'URL di uno script PAC che si vuole usare per configurare il server proxy.
- **Usa il server proxy manuale**: selezionare questa opzione per immettere manualmente le informazioni del server proxy.
  - **Indirizzo**: immettere il nome o l'indirizzo IP del server proxy.
  - **Numero porta**: immettere il numero della porta del server proxy.
  - **Eccezione del proxy**: immettere gli URL che non devono usare il server proxy. Per separare ogni elemento, usare un punto e virgola.
  - **Ignora il server proxy per l'indirizzo locale**: abilitare questa opzione se non si vuole usare il server proxy per gli indirizzi locali della rete Intranet.

## <a name="password"></a>Password

- **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
  - **Tipo di password richiesto**: consente di specificare se la password deve essere solo numerica o alfanumerica.
  - **Lunghezza minima password**: si applica solo a Windows 10 Mobile.
  - **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: per i dispositivi che eseguono Windows 10, se nel dispositivo è abilitato BitLocker, viene attivata la modalità di ripristino BitLocker se l'accesso ha esito negativo per il numero di volte specificato. Se nel dispositivo non è abilitato BitLocker, questa impostazione non si applica. Per i dispositivi che eseguono Windows 10 Mobile, se l'accesso ha esito negativo per il numero di volte immesso, il dispositivo viene cancellato.
  - **Numero massimo di minuti di inattività fino al blocco dello schermo**: specifica il periodo di tempo per cui un dispositivo deve rimanere inattivo prima che lo schermo venga bloccato.
  - **Scadenza password (giorni)**: specifica l'intervallo di tempo dopo il quale è necessario modificare la password del dispositivo.
  - **Impedisci riutilizzo delle password precedenti**: specifica il numero di password usate in precedenza che il dispositivo deve ricordare.
  - **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività (solo Mobile)**: specifica che l'utente deve immettere una password per sbloccare il dispositivo (solo Windows 10 Mobile).
  - **Password semplici**: consente di autorizzare l'uso di password semplici come 1111 o 1234. Questa impostazione consente o blocca anche l'uso delle password grafiche di Windows.
- **Crittografia automatica durante l'aggiunta ad AAD**: **Blocca** impedisce la crittografia automatica BitLocker del dispositivo quando quest'ultimo viene preparato per il primo uso, nei casi in cui è aggiunto ad Azure AD. **Non configurata** (impostazione predefinita) usa l'impostazione predefinita del sistema operativo, che può abilitare la crittografia. Altre informazioni sulla [crittografia BitLocker per dispositivi](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [CSP Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Criteri FIPS (Federal Information Processing Standard)**: se si sceglie **Consenti** vengono usati i criteri FIPS (Federal Information Processing Standard), ovvero uno standard del governo degli Stati Uniti per crittografia, hash e firma. **Non configurata** (impostazione predefinita) usa l'impostazione predefinita del sistema operativo, che non usa FIPS.

  [CSP Cryptography/AllowFipsAlgorithmPolicy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Autenticazione del dispositivo Windows Hello**: **Consenti** permette agli utenti di usare un dispositivo complementare Windows Hello, ad esempio un telefono, un bracciale per il fitness o un dispositivo IoT per accedere a un computer Windows 10. **Non configurata** (impostazione predefinita) usa l'impostazione predefinita del sistema operativo che può impedire al dispositivo complementare Windows Hello di eseguire l'autenticazione in Windows.

  [CSP Authentication/AllowSecondaryAuthenticationDevice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Accesso Web**: abilita il supporto di accesso Windows per i provider federati non ADFS (Active Directory Federation Services), ad esempio Security Assertion Markup Language (SAML). SAML usa token di sicurezza che consentono ai Web browser l'esperienza di accesso Single Sign-On (SSO). Le opzioni disponibili sono:

  - **Non configurata** (impostazione predefinita): usa l'impostazione predefinita del sistema operativo nel dispositivo.
  - **Abilitato**: il provider di credenziali Web è abilitato per l'accesso.
  - **Disabilitato**: il provider di credenziali Web è disabilitato per l'accesso.

  [CSP Authentication/EnableWebSignIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Dominio preferito del tenant di Azure AD**: immettere un nome di dominio esistente nell'organizzazione Azure AD. Gli utenti di questo dominio non dovranno digitare il nome di dominio all'accesso. Immettere ad esempio `contoso.com`. Gli utenti inclusi nel dominio `contoso.com` possono accedere usando il proprio nome utente, ad esempio "abby", anziché "abby@contoso.com".

  [CSP Authentication/PreferredAadTenantDomainName](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>Eccezioni alla privacy per app

È possibile aggiungere app che devono avere un comportamento diverso in relazione alla privacy da quello definito in "Privacy predefinita".

- **Nome pacchetto**: nome della famiglia di pacchetti dell'app.
- **Nome dell'app**: nome dell'app.

### <a name="exceptions"></a>Eccezioni

- **Informazioni account**: specificare se l'app può accedere a nome utente, immagine e altre informazioni di contatto.
- **App in background**: specificare se l'app può essere eseguita in background.
- **Calendario**: specificare se l'app può accedere al calendario.
- **Registro chiamate**: specificare se l'app può accedere al registro delle chiamate personale.
- **Fotocamera**: specificare se l'app può accedere alla fotocamera.
- **Contatti**: specificare se l'app può accedere ai contatti.
- **Posta elettronica**: specificare se l'app può accedere alla posta elettronica e inviare messaggi.
- **Posizione**: specificare se l'app può accedere a informazioni sulla posizione.
- **Messaggistica**: specificare se l'app può leggere o inviare SMS o MMS.
- **Microfono**: specificare se l'app può usare il microfono.
- **Movimento**: specificare se l'app può accedere a informazioni sul movimento dei dispositivi.
- **Notifiche**: specificare se l'app può accedere alle notifiche.
- **Telefono**: specificare se l'app può accedere al telefono.
- **Radio**: alcune app usano le radio nel dispositivo, ad esempio Bluetooth, per inviare e ricevere i dati e devono attivare o disattivare queste radio. Specificare se l'app può controllare queste radio.
- **Attività**: specificare se l'app può accedere alle attività personali.
- **Dispositivi attendibili**: specificare se l'app può usare dispositivi attendibili. I dispositivi attendibili sono hardware già connesso o hardware incluso nel dispositivo. Ad esempio, usare TV, proiettori e così via come dispositivi attendibili.
- **Commenti e diagnostica**: specificare se l'app può accedere alle informazioni di diagnostica.
- **Sincronizza con i dispositivi**: specificare se l'app può condividere e sincronizzare automaticamente le informazioni con dispositivi wireless non associati in modo esplicito al dispositivo.

## <a name="personalization"></a>Personalization

- **URL dell'immagine di sfondo del desktop (solo desktop)**: immettere l'URL per un'immagine in formato JPEG che si vuole usare come sfondo del desktop di Windows. Gli utenti non possono modificare l'immagine.

## <a name="printer"></a>Stampante

- **Stampanti**: elenco delle stampanti locali che sono state aggiunte.
- **Stampante predefinita**: impostare la stampante predefinita.
- **User access to add new printers** (Accesso utente per l'aggiunta di nuove stampanti): consentire o bloccare l'uso delle stampanti locali.

## <a name="privacy"></a>Privacy

- **Personalizzazione dell'input**: non consente l'uso di servizi di riconoscimento vocale basati sul cloud per Cortana, app di dettatura o app di Microsoft Store. Se si consentono questi servizi, Microsoft potrebbe raccogliere dati vocali per migliorare il servizio.
- **Accettazione automatica delle richieste di associazione e di consenso utente sulla privacy**: consente a Windows di accettare automaticamente messaggi di associazione e consenso sulla privacy durante l'esecuzione di app.
- **Pubblica le attività utente**: **Blocca** impedisce la condivisione delle esperienze e l'individuazione delle risorse usate di recente nella selezione attività.
- **Solo attività locali**: **Blocca** impedisce la condivisione delle esperienze e l'individuazione delle risorse usate di recente nella selezione attività solo per le attività locali.

È possibile configurare le informazioni accessibili per tutte le app nel dispositivo. Definire anche le eccezioni per le singole app tramite **Eccezioni alla privacy per app**.

### <a name="exceptions"></a>Eccezioni

- **Informazioni account**: specificare se l'app può accedere a nome utente, immagine e altre informazioni di contatto.
- **App in background**: specificare se l'app può essere eseguita in background.
- **Calendario**: specificare se l'app può accedere al calendario.
- **Registro chiamate**: specificare se l'app può accedere al registro delle chiamate personale.
- **Fotocamera**: specificare se l'app può accedere alla fotocamera.
- **Contatti**: specificare se l'app può accedere ai contatti.
- **Posta elettronica**: specificare se l'app può accedere alla posta elettronica e inviare messaggi.
- **Posizione**: specificare se l'app può accedere a informazioni sulla posizione.
- **Messaggistica**: specificare se l'app può leggere o inviare SMS o MMS.
- **Microfono**: specificare se l'app può usare il microfono.
- **Movimento**: specificare se l'app può accedere a informazioni sul movimento dei dispositivi.
- **Notifiche**: specificare se l'app può accedere alle notifiche.
- **Telefono**: specificare se l'app può accedere al telefono.
- **Radio**: alcune app usano le radio nel dispositivo, ad esempio Bluetooth, per inviare e ricevere i dati e devono attivare o disattivare queste radio. Specificare se l'app può controllare queste radio.
- **Attività**: specificare se l'app può accedere alle attività personali.
- **Dispositivi attendibili**: specificare se l'app può usare dispositivi attendibili. I dispositivi attendibili sono hardware già connesso o hardware incluso nel dispositivo. Ad esempio, usare TV, proiettori e così via come dispositivi attendibili.
- **Commenti e diagnostica**: specificare se l'app può accedere alle informazioni di diagnostica.
- **Sincronizza con i dispositivi** - Specificare se l'app può condividere e sincronizzare automaticamente le informazioni con dispositivi wireless non associati in modo esplicito a questo PC, tablet o telefono.

## <a name="projection"></a>Proiezione

- **Input degli utenti da ricevitori di schermo wireless**: blocca l'input degli utenti da ricevitori di schermo wireless.
- **Proiezione per questo computer**: impedisce ad altri dispositivi di trovare il PC per la proiezione.
- **Richiedi il PIN per l'associazione**: richiede un PIN durante la connessione a un dispositivo di proiezione.

## <a name="reporting-and-telemetry"></a>Reporting e telemetria

- **Condividi i dati di utilizzo**: scegliere il livello di dati di diagnostica inviati. Le opzioni disponibili sono:
  - Sicurezza
  - Basic
  - Avanzato
  - Completo
- **Invia i dati di esplorazione di Microsoft Edge a Microsoft 365 Analytics**: per usare questa funzionalità, impostare l'opzione **Condividi i dati di utilizzo** su **Avanzato** o **Completo**. Questa funzionalità consente di controllare quali dati Microsoft Edge invia a Microsoft 365 Analytics per i dispositivi aziendali con un ID commerciale configurato. Le opzioni disponibili sono:
  - **Non configurata**: usa l'impostazione predefinita del sistema operativo, che potrebbe non inviare dati della cronologia esplorazioni
  - **Invia solo dati Intranet**: consente all'amministratore di inviare la cronologia dei dati Intranet
  - **Invia solo dati Internet**: consente all'amministratore di inviare la cronologia dei dati Internet
  - **Invia dati Intranet e Internet**: consente all'amministratore di inviare la cronologia dei dati Intranet e Internet
- **Server proxy di telemetria**: immettere il nome di dominio completo (FQDN) o l'indirizzo IP di un server proxy per l'inoltro delle richieste Esperienze utente connesse e telemetria, tramite una connessione Secure Sockets Layer (SSL). Il formato di questa impostazione è *server*:*porta*. In caso di errore del proxy denominato oppure se viene immesso alcun proxy al momento dell'abilitazione di questo criterio, i dati Esperienze utente connesse e telemetria non vengono inviati e rimangono nel dispositivo locale.

  Formati di esempio:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Cerca

- **Ricerca sicura (solo dispositivi mobili)**: controlla come Cortana filtra il contenuto per adulti nei risultati della ricerca. È possibile selezionare **Strict**, **Moderate** o consentire all'utente finale di scegliere le proprie impostazioni.
- **Visualizza i risultati Web nella ricerca**: blocca o consente la visualizzazione dei risultati Web nelle ricerche eseguite nel dispositivo.

## <a name="start"></a>Avvia

- **Layout del menu Start**: per personalizzare il menu Start nei dispositivi desktop, è possibile caricare un file XML che include le personalizzazioni, tra cui l'ordine in cui sono elencate le app e altro ancora. Gli utenti non possono modificare il layout del menu Start immesso.
- **Aggiungi i siti Web ai riquadri nel menu Start**: consente di importare immagini da Microsoft Edge che vengono visualizzate come collegamenti nel menu Start di Windows per i dispositivi desktop.
- **Rimuovi le app dalla barra delle applicazioni**: scegliere **Blocca** per impedire all'utente di rimuovere app dalla barra delle applicazioni.
- **Cambio rapido utente**: scegliere **Blocca** per impedire il cambio utente tra utenti connessi simultaneamente senza che eseguano la disconnessione.
- **App più usate**: scegliere **Blocca** per nascondere le app più usate nel menu Start. Questa opzione disabilita anche l'alternanza corrispondente nell'app Impostazioni.
- **App aggiunte di recente**: scegliere **Blocca** per nascondere le app aggiunte di recente nel menu Start. Questa opzione disabilita anche l'alternanza corrispondente nell'app Impostazioni.
- **Modalità della schermata Start**: scegliere la modalità di visualizzazione della schermata Start. Le opzioni di visualizzazione disponibili sono **Schermo intero** oppure **Non a schermo intero**.
- **Elementi aperti di recente nelle jump list**: scegliere **Blocca** per nascondere le jump list recenti nel menu Start e nella barra delle applicazioni. Questa opzione disabilita anche l'alternanza corrispondente nell'app Impostazioni.
- **Elenco di app**: scegliere la modalità di visualizzazione dell'app Impostazioni. Le opzioni disponibili sono: 
  - Comprimi
  - Comprimi e disabilita l'app Impostazioni 
  - Rimuovi e disabilita l'app Impostazioni
- **Pulsante di alimentazione**: scegliere **Blocca** per nascondere il pulsante di alimentazione nel menu Start.
- **Riquadro utente**: scegliere **Blocca** per nascondere il riquadro utente nel menu Start.
  - **Blocco**: scegliere **Blocca** per nascondere l'opzione `Lock` nel riquadro utente nel menu Start.
  - **Disconnetti**: scegliere **Blocca** per nascondere l'opzione `Sign out` nel riquadro utente nel menu Start.
- **Arresta**: scegliere **Blocca** per nascondere le opzioni `Update and shut down` e `Shut down` nel pulsante di alimentazione nel menu Start.
- **Sospendi**: scegliere **Blocca** per nascondere l'opzione `Sleep` nel pulsante di alimentazione nel menu Start.
- **Iberna**: scegliere **Blocca** per nascondere l'opzione `Hibernate` nel pulsante di alimentazione nel menu Start.
- **Cambia account**: scegliere **Blocca** per nascondere l'opzione `Switch account` nel riquadro utente nel menu Start.
- **Opzioni per il riavvio**: scegliere **Blocca** per nascondere le opzioni `Update and restart` e `Restart` nel pulsante di alimentazione nel menu Start.
- **Documenti nel menu Start**: nasconde o mostra la cartella Documenti nel menu Start di Windows.
- **Download nel menu Start**: nasconde o mostra la cartella Download nel menu Start di Windows.
- **Esplora file nel menu Start**: nasconde o mostra l'app Esplora file nel menu Start di Windows.
- **Gruppo Home nel menu Start**: nasconde o mostra la cartella Gruppo Home nel menu Start di Windows.
- **Musica nel menu Start**: nasconde o mostra la cartella Musica nel menu Start di Windows.
- **Rete nel menu Start**: nasconde o mostra la cartella Rete nel menu Start di Windows.
- **Cartella Personale nel menu Start**: nasconde o mostra la cartella Personale nel menu Start di Windows.
- **Immagini nel menu Start**: nasconde o mostra la cartella delle immagini nel menu Start di Windows.
- **Impostazioni nel menu Start**: nasconde o mostra l'app Impostazioni nel menu Start di Windows.
- **Video nel menu Start**: nasconde o mostra la cartella dei video nel menu Start di Windows.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen per Microsoft Edge**: abilita SmartScreen di Microsoft Edge per l'accesso a siti e download di file.
- **Accesso a siti dannosi**: impedisce agli utenti di ignorare gli avvisi del filtro SmartScreen di Windows Defender e impedisce loro di passare al sito.
- **Download di file non verificati**: impedisce agli utenti di ignorare gli avvisi del filtro SmartScreen di Windows Defender e impedisce loro di scaricare file non verificati.

## <a name="windows-spotlight"></a>Contenuti in evidenza di Windows

- **Windows Spotlight**: usare questa impostazione per bloccare tutte le funzionalità di Windows Spotlight nei dispositivi Windows 10. Se si blocca questa impostazione, le impostazioni seguenti non sono disponibili:
  - **Windows Spotlight nella schermata di blocco**: impedisce a Windows Spotlight di visualizzare informazioni nella schermata di blocco del dispositivo.
  - **Suggerimenti di terze parti in Windows Spotlight**: impedisce a Windows Spotlight di suggerire contenuto non pubblicato da Microsoft.
  - **Funzionalità consumer**: consente di bloccare le funzionalità consumer, ad esempio i suggerimenti per il menu Start e le notifiche di appartenenza.
  - **Suggerimenti di Windows**: consente di bloccare la visualizzazione dei suggerimenti popup in Windows.
  - **Centro notifiche di Windows Spotlight**: blocca la visualizzazione di suggerimenti di Windows Spotlight (quali nuove app o contenuti sulla sicurezza) nel Centro notifiche di Windows.
  - **Personalizzazione di Windows Spotlight**: impedisce a Windows Spotlight ila personalizzazione dei risultati in base all'utilizzo di un dispositivo.
  - **Esperienza di Configurazione e personalizzazione di Windows**: blocca l'Esperienza di Configurazione e personalizzazione di Windows, che visualizza informazioni su funzionalità nuove o aggiornate.

## <a name="windows-defender-antivirus"></a>Windows Defender Antivirus

- **Monitoraggio in tempo reale**: abilita l'analisi in tempo reale per malware, spyware e altro software indesiderato.
- **Monitoraggio del comportamento**: consente a Defender di controllare la presenza di modelli noti di attività sospette nei dispositivi.
- **Network Inspection System (NIS)**: consente di proteggere i computer dagli exploit basati sulla rete. Usa le firme delle vulnerabilità note da Microsoft Endpoint Protection Center per consentire di rilevare e bloccare il traffico dannoso.
- **Analizza tutti i download**: controlla se Defender deve analizzare tutti i file scaricati da Internet.
- **Analizza gli script caricati nei Web browser Microsoft**: consente a Defender di analizzare gli script usati in Internet Explorer.
- **Accesso dell'utente finale a Defender**: controlla se l'interfaccia utente di Windows Defender è nascosta agli utenti finali. Quando questa impostazione viene modificata, ha effetto dal successivo avvio del PC dell'utente finale.
- **Intervallo di aggiornamento della firma (in ore)**: immettere l'intervallo con il quale Defender controllerà i nuovi file di firma.
- **Monitora l'attività di file e programmi**: consente a Defender di monitorare l'attività di file e programmi nei dispositivi.
- **Giorni di attesa prima dell'eliminazione di malware in quarantena**: continua a monitorare il malware risolto per il numero di giorni immesso, in modo che sia possibile controllare manualmente i dispositivi colpiti in precedenza. Se si imposta il numero di giorni su **0**, il malware rimane nella cartella della quarantena e non viene rimosso automaticamente.
- **Limite di utilizzo della CPU durante un'analisi**: limitare la quantità di CPU di cui è consentito l'uso per le analisi, da **1** a **100**.
- **Analizza file di archivio**: consente a Defender di analizzare i file archiviati come i file con estensione.zip o cab.
- **Analizza i messaggi di posta in arrivo**: consente a Defender di analizzare i messaggi di posta elettronica non appena arrivano sul dispositivo.
- **Analizza le unità rimovibili durante un'analisi completa**: consente a Defender di analizzare le unità rimovibili come le chiavi USB.
- **Analizza le unità di rete mappate durante un'analisi completa**: consente a Defender di analizzare i file nelle unità di rete mappate.
  Se i file nell'unità sono di sola lettura, Defender non può rimuovere il malware rilevato in tali file.
- **Analizza file aperti da cartelle di rete**: consente a Defender di analizzare i file nelle unità di rete condivise, ad esempio i file a cui si accede da un percorso UNC. Se i file nell'unità sono di sola lettura, Defender non può rimuovere il malware rilevato in tali file.
- **Protezione cloud**: consente o blocca la ricezione di informazioni sull'attività del malware da parte di Microsoft Active Protection Service dai dispositivi gestiti. Queste informazioni migliorano il servizio in futuro.
- **Richiedi conferma all'utente prima dell'invio di campioni**: determina se i file potenzialmente dannosi che potrebbero richiedere ulteriore analisi vengono inviati automaticamente a Microsoft.
- **Ora di esecuzione di un'analisi veloce giornaliera**: scegliere l'ora in cui eseguire un'analisi veloce giornaliera. Se **Non configurata**, l'analisi giornaliera non viene eseguita. Per un'ulteriore personalizzazione, configurare l'impostazione **Tipo di analisi di sistema da eseguire**.

  [CSP Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)
- **Tipo di analisi di sistema da eseguire**: consente di pianificare un'analisi di sistema, inclusi il livello di analisi e il giorno e l'ora in cui eseguire l'analisi. Le opzioni disponibili sono:
  - **Non configurata**: l'analisi di sistema non è pianificata nel dispositivo. Gli utenti finali possono eseguire manualmente le analisi nei dispositivi in base alle proprie esigenze.
  - **Disabilita**: disabilita qualsiasi analisi di sistema presente nel dispositivo. Scegliere questa opzione se si usa una soluzione antivirus partner che analizza i dispositivi.
  - **Analisi veloce**: esamina i percorsi comuni in cui potrebbe essere presente malware registrato, ad esempio chiavi del Registro di sistema e cartelle di avvio Windows note.
    - **Giorno pianificato**: scegliere il giorno in cui eseguire l'analisi.
    - **Ora pianificata**: scegliere l'ora in cui eseguire l'analisi.
  - **Analisi completa**: esamina i percorsi comuni in cui potrebbe essere presente malware registrato e analizza anche ogni file e cartella presente nel dispositivo.
    - **Giorno pianificato**: scegliere il giorno in cui eseguire l'analisi.
    - **Ora pianificata**: scegliere l'ora in cui eseguire l'analisi.

  Questa impostazione potrebbe essere in conflitto con l'impostazione **Ora di esecuzione di un'analisi veloce giornaliera**. Alcuni consigli:

  - Per eseguire un'analisi veloce giornaliera, configurare l'impostazione **Ora di esecuzione di un'analisi veloce giornaliera**.
  - Per eseguire un'analisi veloce giornaliera e un'analisi completa ogni settimana, configurare **Ora di esecuzione di un'analisi veloce giornaliera** e impostare **Tipo di analisi di sistema da eseguire** su un'analisi completa con il giorno e l'ora.
  - Non configurare l'impostazione **Ora di esecuzione di un'analisi veloce giornaliera** contemporaneamente a **Tipo di analisi di sistema da eseguire** impostato su **Analisi veloce**. Queste impostazioni possono essere in conflitto e l'analisi potrebbe non essere eseguita.
  - Per eseguire un'analisi veloce ogni martedì alle 6, configurare l'impostazione **Tipo di analisi di sistema da eseguire**.

  [CSP Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [CSP Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [CSP Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Rileva applicazioni potenzialmente indesiderate**: scegliere il livello di protezione quando Windows rileva applicazioni potenzialmente indesiderate:
  - **Bloccato**
  - **Controllo** Per altre informazioni sulle app potenzialmente indesiderate, vedere [Rilevare e bloccare le applicazioni potenzialmente indesiderate](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Azioni per le minacce malware rilevate**: scegliere le azioni che si vuole vengano eseguite da Defender a seconda del livello di minaccia rilevato: basso, moderato, alto o grave. Le opzioni disponibili sono:
  - **Pulisci**
  - **Quarantena**
  - **Rimuovi**
  - **Consentito**
  - **Definito dall'utente**
  - **Bloccato**

### <a name="windows-defender-antivirus-exclusions"></a>Esclusioni di Windows Defender Antivirus

- **File e cartelle da escludere dalle analisi e dalla protezione in tempo reale**: aggiunge uno o più file e cartelle come **C:\Percorso** o **%ProgramFiles%\Percorso\nomefile.exe** all'elenco delle esclusioni. Questi file e cartelle non sono inclusi nelle analisi in tempo reale o pianificate.
- **Estensioni di file da escludere dalle analisi e dalla protezione in tempo reale**: aggiunge una o più estensioni di file come **jpg** o **txt** all'elenco delle esclusioni. I file con queste estensioni non vengono inclusi nelle analisi in tempo reale o pianificate.
- **Processi da escludere dalle analisi e dalla protezione in tempo reale**: aggiunge uno o più processi di tipo **.exe**, **.com** o **.scr** all'elenco delle esclusioni. Questi processi non vengono inclusi nelle analisi in tempo reale o nelle analisi pianificate.

## <a name="next-steps"></a>Passaggi successivi

Per altri dettagli tecnici su ogni impostazione e sulle edizioni di Windows supportate, vedere [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Informazioni di riferimento sul provider di servizi di configurazione Policy di Windows 10)
