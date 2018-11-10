---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bacaf8ff4119d4cd40483b65ea45e283d98a51f1
ms.sourcegitcommit: 814d1d473de2de2e735efab826b1091de2b093f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025203"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Edizione anticipata per Microsoft Intune - Novembre 2018

> [!Note]
> Notifica accordo di riservatezza: le seguenti modifiche di Intune sono in fase di sviluppo. Queste informazioni sono condivise con accordo di riservatezza su base estremamente limitata. Non pubblicare queste informazioni nei social network o in siti Web pubblici, come Twitter, UserVoice, Reddit e così via. 

L'**edizione anticipata** fornisce un elenco di funzionalità, condivise con accordo di riservatezza, che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non inviare tweet, pubblicare in UserVoice o condividere in altro modo queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Disinstallazione di app in dispositivi iOS con supervisione di proprietà dell'azienda <!-- 1281677 -->
Sarà possibile rimuovere qualsiasi app nei dispositivi iOS con supervisione di proprietà dell'azienda. È possibile rimuovere qualsiasi app specificando come destinazione gruppi di utenti o dispositivi con un tipo di assegnazione **Disinstalla**. Per i dispositivi iOS personali o senza supervisione, sarà ancora possibile rimuovere solo le app installate usando Intune.

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Supporto per iOS 12 OAuth nei profili di posta elettronica iOS <!--2155106 -->
I profili di posta elettronica iOS di Intune supporteranno iOS 12 OAuth. Per visualizzare questa funzionalità, scegliere **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**. Nel pannello Crea profilo è possibile abilitare o disabilitare **OAuth**. Se questa impostazione viene attivata, verranno eseguite due operazioni:
1. Verrà rilasciato un nuovo profilo ai dispositivi già specificati come destinazione.
2. Agli utenti verrà chiesto di fornire nuovamente le credenziali.

### <a name="track-installation-of-office-proplus---2620217--"></a>Tenere traccia dell'installazione di Office ProPlus <!--2620217-->
Sarà possibile tenere traccia dell'avanzamento dell'installazione di [Office ProPlus](apps-add-office365.md) usando la [pagina relativa allo stato della registrazione](windows-enrollment-status.md).

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>Supporto di Device Enrollment Program di macOS per gli account Apple School Manager <!--3006133-->
Intune supporterà l'uso di Device Enrollment Program nei dispositivi macOS per gli account Apple School Manager.

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Sospendere temporaneamente la modalità tutto schermo sui dispositivi Android per apportare modifiche <!-- 3041935 -->
Quando si usano dispositivi Android in modalità tutto schermo per più app, un amministratore IT potrebbe aver bisogno di apportare modifiche al dispositivo. Una nuova impostazione della modalità tutto schermo per più app consentirà a un amministratore IT di sospendere temporaneamente la modalità tutto schermo tramite un PIN e di ottenere l'accesso all'intero dispositivo.
Per visualizzare le impostazioni della modalità tutto schermo correnti, vedere [Impostazioni della modalità tutto schermo per Android](android-kiosk-settings.md).

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Impostare lo sfondo personalizzato nell'app di schermata iniziale gestita <!-- 3041945 -->
Verrà aggiunta un'impostazione che consente di personalizzare l'aspetto dello sfondo dell'app di schermata iniziale gestita nei dispositivi in modalità tutto schermo per più app di Android Enterprise.  Per configurare lo **sfondo personalizzato per l'URL**, passare a Intune nel portale di Azure > Configurazione del dispositivo. Selezionare un profilo di configurazione del dispositivo corrente o crearne uno nuovo per modificarne le impostazioni della modalità tutto schermo.

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Abilitare il pulsante Pagina iniziale virtuale nei dispositivi in modalità tutto schermo di Android Enterprise <!-- 3042021 -->
Una nuova impostazione consentirà agli utenti di toccare un pulsante softkey nel dispositivo per passare dall'app di schermata iniziale gestita alle altre app assegnate nel dispositivo in modalità tutto schermo per più app. Questa impostazione è particolarmente utile negli scenari in cui l'app in modalità tutto schermo di un utente non risponde in modo corretto al pulsante "Indietro". Sarà possibile configurare questa impostazione per i dispositivi Android monouso di proprietà dell'azienda. Per abilitare o disabilitare il **pulsante Pagina iniziale virtuale**, passare a Intune nel portale di Azure > Configurazione del dispositivo. Selezionare un profilo di configurazione del dispositivo corrente o crearne uno nuovo per modificarne le impostazioni della modalità tutto schermo.

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Salvataggio e applicazione dell'assegnazione dei criteri di protezione dell'app <!-- 3104570 -->
Si avrà maggiore controllo sulle assegnazioni dei criteri di protezione dell'app. Salvando e applicando le assegnazioni dei criteri di protezione dell'app, solo gli utenti desiderati sono direttamente interessati da un criterio di assegnazione di protezione dell'app.

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nuove impostazioni del browser Microsoft Edge per Windows 10 e versioni successive <!-- 3174639 -->
Verrà aggiunta una nuova impostazione per controllare e gestire il browser Microsoft Edge nei dispositivi. Per un elenco delle impostazioni correnti, vedere [Device restriction for Windows 10 (and newer)](device-restrictions-windows-10.md#edge-browser) (Restrizione dei dispositivi per Windows 10 e versioni successive).

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Selezionare le app registrate nella pagina Stato di registrazione<!-- 2531007 -->
Sarà possibile scegliere le app di cui tenere traccia nella pagina Stato di registrazione.

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Aggiornamento dell'interfaccia utente dei criteri di protezione delle app di Intune <!-- 3251427 -->

I criteri di protezione delle app di Intune consentono di configurare varie impostazioni di protezione dei dati per le app protette da Intune, ad esempio Microsoft Outlook e Word. Verranno modificate le etichette delle impostazioni e dei pulsanti per facilitarne la comprensione. I controlli di tipo **sì**/**no** verranno sostituiti principalmente da controlli di tipo **blocca**/**consenti** e **disabilita**/**abilita** e anche le etichette verranno aggiornate per maggiore chiarezza. Le impostazioni verranno anche riformattate, in modo che l'impostazione e la relativa etichetta siano affiancate nel controllo, consentendo una migliore navigazione. Le impostazioni predefinite e il numero di impostazioni non subiranno modifiche, ma questa modifica permetterà all'utente di comprendere, esplorare e utilizzare le impostazioni più facilmente per applicare i criteri di protezione delle app selezionati.



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Usare le impostazioni consigliate da Microsoft con le baseline di sicurezza <!-- 2055484 -->
Intune si integra con altri servizi specifici per la sicurezza, inclusi Windows Defender ATP e Office 365 ATP. I clienti manifestano l'esigenza di una strategia comune e di un set integrato di flussi di lavoro di sicurezza end-to-end nei servizi di Microsoft 365. L'obiettivo è l'allineamento delle strategie per creare soluzioni in grado di conciliare le operazioni di sicurezza e le comuni attività degli amministratori. Per realizzare questo obiettivo in Intune, è stato pubblicato un set di "baseline di sicurezza" consigliate da Microsoft (**Intune** > **Baseline di sicurezza**).  Un amministratore potrà creare criteri di sicurezza direttamente da queste baseline e quindi distribuirle agli utenti. Può anche personalizzare le indicazioni sulle procedure consigliate per soddisfare le esigenze dell'organizzazione. Intune verifica che i dispositivi rimangano conformi a queste baseline e invia agli amministratori una notifica sugli utenti e i dispositivi non conformi.

### <a name="scope-tags-for-apps---1081941---"></a>Tag di ambito per le app <!--1081941 -->
Sarà possibile creare tag di ambito per limitare l'accesso alle risorse di Intune. Aggiungere un tag di ambito a un'assegnazione di ruolo e quindi aggiungere il tag di ambito a un profilo di configurazione. Il ruolo potrà accedere solo alle risorse con profili di configurazione con tag di ambito corrispondenti (o nessun tag di ambito).
Per creare un tag di ambito, scegliere **Ruoli di Intune** > **Ambito (tag)** > **Crea**.
Per aggiungere un tag di ambito a un'assegnazione di ruolo, scegliere **Ruoli di Intune** > **Tutti i ruoli** > **Policy and Profile Manager (Gestione criteri e profili)** > **Assegnazioni** > **Ambito (tag)**.
Per aggiungere un tag di ambito a un profilo di configurazione, scegliere **Configurazione del dispositivo** > **Profili** > scegliere un profilo > **Proprietà** > **Ambito (tag)**.

### <a name="tenant-health-dashboard----1124854---"></a>Dashboard sull'integrità del tenant <!-- 1124854 -->
La pagina Stato del tenant in Intune fornirà in un'unica posizione le informazioni sullo stato del tenant. La pagina è suddivisa in 4 sezioni:  
- **Dettagli del tenant**: contiene informazioni, ad esempio l'autorità MDM, il totale dei dispositivi registrati nel tenant e i conteggi delle licenze. Questa sezione indica anche la versione corrente del servizio per il tenant.
- **Stato del connettore**: contiene informazioni sui connettori configurati, ad esempio Apple VPP, Windows Store for Business e connettori di certificati. In base allo stato corrente, i connettori vengono contrassegnati come *Integro*, *Avviso* o *Non integro*.
- **Integrità del servizio Intune**: contiene gli eventi imprevisti attivi o le interruzioni del tenant. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office ([https://portal.office.com](https://portal.office.com)).
- **Novità su Intune**: contiene i messaggi attivi sul tenant, ad esempio le notifiche che informano che il tenant ha ricevuto le funzionalità di Intune più recenti. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Criteri WIP distribuiti senza registrazione dell'utente <!-- 1434452 -->
I criteri di Windows Information Protection (WIP) potranno essere distribuiti senza richiedere agli utenti MDM di registrare il dispositivo Windows 10. Questa configurazione non solo consente alle società di proteggere i documenti aziendali in base alla configurazione WIP, ma permette anche agli utenti di continuare a gestire i dispositivi Windows. Quando i documenti sono protetti da un criterio WIP, i dati protetti possono essere cancellati in modo selettivo da un amministratore di Intune. Selezionando l'utente e il dispositivo e inviando una richiesta di cancellazione, tutti i dati protetti tramite i criteri WIP non saranno più utilizzabili. Da Intune nel portale di Azure selezionare **App per dispositivi mobili** > **Cancellazione selettiva di app**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Impostazioni dei criteri di protezione dell'app per i dati Web <!-- 2662995 -->
Le impostazioni dei criteri di protezione dell'app per il contenuto Web nei dispositivi iOS e Android verranno aggiornate per gestire meglio i collegamenti Web sia http che https, nonché il trasferimento dei dati tramite i collegamenti universali iOS e i collegamenti delle app Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP Apple usato da un altro software MDM <!-- 1488946 -->
Intune rileverà e visualizzerà i dettagli se un token VPP (Volume Purchase Program) Apple viene usato sia da Intune che da un altro software MDM.

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Vengono visualizzati i numeri di versione e di build di iOS e macOS <!-- 1892471 -->
In **Conformità del dispositivo** > **Conformità del dispositivo** viene visualizzata la versione del sistema operativo iOS e macOS. In un aggiornamento futuro verrà anche visualizzato il numero di build per entrambe le piattaforme.

Quando vengono rilasciati aggiornamenti della sicurezza, Apple lascia in genere il numero di versione invariato, ma aggiorna il numero di build. Visualizzando il numero di build, è possibile verificare facilmente se è installato un aggiornamento di una vulnerabilità.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivi ritirati nel dashboard della conformità dei dispositivi <!-- 1981119 -->
In un aggiornamento futuro i dispositivi ritirati verranno rimossi dal dashboard della conformità dei dispositivi. Questa operazione modificherà i numeri di conformità.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Modifica nel processo di aggiornamento per i connettori locali <!-- 2277554 -->
In base al feedback dei clienti, cambierà il modo in cui gli aggiornamenti vengono eseguiti nei connettori locali. Dopo aver installato un connettore locale, gli aggiornamenti verranno eseguiti automaticamente. Questa modifica inizierà con il nuovo connettore di certificati PFX per Microsoft Intune e successivamente verrà applicata ad altri tipi di connettori locali. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Verificare la conformità di Configuration Manager <!-- 2192052 -->
Un aggiornamento futuro includerà una nuova impostazione di conformità System Center Configuration Manager (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10**). Configuration Manager invia segnali per la conformità di Intune. Usando l'impostazione di Intune è possibile richiedere che tutti i segnali Configuration Manager restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Si applica a Windows 10 e versioni successive

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Avvisi per i token VPP in scadenza o un numero insufficiente di licenze del portale aziendale <!-- 2237572 -->
Se si usa Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante la registrazione DEP, Intune invia un avviso in prossimità della scadenza del token VPP e in caso di un numero insufficiente di licenze per il portale aziendale.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).



