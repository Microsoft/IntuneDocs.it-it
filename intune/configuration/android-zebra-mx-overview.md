---
title: Utilizzare Mobility Extensions di Zebra sui dispositivi Android in Microsoft Intune - Azure | Microsoft Docs
description: Utilizzare Microsoft Intune per gestire e usare i dispositivi Zebra che eseguono Android con Mobility Extensions (MX) di Zebra. Vedere tutti i passaggi, tra cui l’installazione dell’app Portale aziendale, effettuare il sideload dell’app, assegnare il ruolo di amministratore del dispositivo, creare un profilo StageNow e altro ancora.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: jieyan
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f343ace48c917e65d9d59cd7c42c53e9b892968
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73756723"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Utilizzare e gestire i dispositivi Zebra con Mobility Extensions di Zebra in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune include un'ampia gamma di funzionalità, tra cui la gestione delle app e la configurazione delle impostazioni del dispositivo. Queste funzionalità e impostazioni predefinite gestiscono i dispositivi Android prodotti da Zebra Technologies, noti anche come "dispositivi Zebra".

Nei dispositivi Android, usare i profili **Mobility Extensions (MX)** di Zebra per personalizzare o aggiungere altre impostazioni specifiche di Zebra.

Questo articolo illustra come utilizzare Mobility Extensions (MX) di Zebra sui dispositivi Zebra in Microsoft Intune.

Questa funzionalità si applica a:

- Android

La società può usare dispositivi Zebra per la vendita al dettaglio, nell’ambiente di produzione e altro ancora. Ad esempio, nel caso in cui l’ambiente di un rivenditore al dettaglio includa migliaia di dispositivi mobili Zebra utilizzati dagli assistenti alle vendite. Intune consente di gestire questi dispositivi come parte della soluzione MDM.

Con Intune, è possibile registrare i dispositivi Zebra per distribuire le app line-of-business sui dispositivi. I profili "Configurazione del dispositivo" consentono di creare profili MX per gestire le impostazioni specifiche di Zebra.

> [!NOTE]
> Per impostazione predefinita, le API di zebra MX non sono bloccate nei dispositivi. Prima di registrare un dispositivo in Intune, è possibile che il dispositivo possa essere compromesso in modo dannoso. Quando il dispositivo è in uno stato pulito, è consigliabile bloccare le API MX usando Access Manager (AccessMgr). Ad esempio, è possibile scegliere di chiamare le API MX solo per le app Portale aziendale e le app attendibili.
>
> Per ulteriori informazioni, vedere [blocco del dispositivo](https://developer.zebra.com/community/home/blog/2017/04/11/locking-down-your-device) nel sito Web di zebra.

## <a name="before-you-begin"></a>Prima di iniziare

- Assicurarsi di disporre della versione più recente dell'app desktop StageNow di Zebra Technologies.
- Assicurarsi di controllare la [matrice completa delle funzionalità MX di Zebra](http://techdocs.zebra.com/mx/compatibility) (apre il sito Web di Zebra) per verificare che i profili creati siano compatibili con la versione di MX, la versione del sistema operativo e il modello del dispositivo.
- Alcuni dispositivi, ad esempio i dispositivi TC20/25, non supportano tutte le funzionalità MX disponibili in StageNow. Assicurarsi di controllare la [matrice delle funzionalità di Zebra](http://techdocs.zebra.com/mx/tc2x/) (apre il sito Web di Zebra) per informazioni aggiornate sul supporto.

## <a name="step-1-install-the-latest-company-portal-app"></a>Passaggio 1: installare l'app Portale aziendale più recente

Nel dispositivo aprire l'archivio Google Play. Scaricare e installare l'app Portale aziendale Intune da Microsoft. Una volta installata da Google Play, l'app Portale aziendale scarica automaticamente gli aggiornamenti e le correzioni.

Se Google Play non è disponibile, scaricare [Portale aziendale di Microsoft Intune per Android](https://www.microsoft.com/download/details.aspx?id=49140) (si apre un altro sito Web Microsoft) ed [effettuarne il sideload ](#sideload-the-company-portal-app) (in questo articolo). Se viene installata in questo modo, l'app non può ricevere automaticamente gli aggiornamenti o le correzioni. Assicurarsi che gli aggiornamenti e le patch siano regolarmente installati nell'app manualmente.

### <a name="sideload-the-company-portal-app"></a>Trasferire localmente l'app Portale aziendale

"Sideload" indica quando non viene utilizzato Google Play per installare un'app. Per effettuare il sideload dell'app Portale aziendale, utilizzare StageNow. 

I passaggi seguenti offrono una panoramica. Per informazioni dettagliate specifiche, vedere la documentazione di Zebra. [La registrazione a un sistema MDM tramite StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (si apre il sito Web di Zebra) può essere un'ottima risorsa.

1. In StageNow, creare un profilo per **Enroll in an MDM (Registra in un MDM)** .
2. In **Deployment (distribuzione)** , scegliere di scaricare il file dell'agente MDM.
3. Impostare i passaggi **Support App (App di supporto)** e **Download Configuration (Scarica configurazione)** su **No**.
4. In **Download MDM (Scarica MDM)** , selezionare **Transfer/Copy File (Trasferisci/copia file)** . Aggiungere l'origine e la destinazione del pacchetto Android (APK) Portale aziendale.
5. In **Launch MDM (Avvia MDM)** , lasciare i valori predefiniti come sono. Aggiungere i dettagli seguenti:

    - **Nome pacchetto**: `com.microsoft.windowsintune.companyportal`
    - **Nome classe**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Continuare a pubblicare il profilo e utilizzarlo con l'app StageNow nel dispositivo. L’app Portale aziendale viene installata e aperta nel dispositivo.

> [!TIP]
> Per altre informazioni su StageNow e il suo funzionamento, vedere [Staging dei dispositivi Android con StageNow](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (si apre il sito Web di Zebra).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Passaggio 2: verificare che l’app Portale aziendale disponga del ruolo di amministratore del dispositivo

L'app Portale aziendale richiede il ruolo Amministratore dispositivo per gestire i dispositivi Android. Per attivare il ruolo Amministratore dispositivo, alcuni dispositivi Zebra includono un'interfaccia utente nel dispositivo. Se il dispositivo include un'interfaccia utente, l'app Portale aziendale chiede all'utente finale di concedere il ruolo Amministratore dispositivo durante la [registrazione](#step-3-enroll-the-device-in-to-intune) (in questo articolo).

Se non è disponibile un'interfaccia utente, utilizzare **DevAdmin Manager** in StageNow per creare un profilo che conceda manualmente il ruolo Amministratore dispositivo all'app Portale aziendale.

I passaggi seguenti offrono una panoramica. Per informazioni dettagliate specifiche, vedere la documentazione di Zebra. 
[L’impostazione della modalità di scambio della batteria come amministratore del dispositivo](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (si apre il sito Web di Zebra) può essere un'ottima risorsa.

1. In StageNow, creare un profilo e selezionare **Xpert Mode (Modalità esperto)** .
2. Aggiungere **DevAdmin Manager** al profilo.
3. Impostare **Device Administration Action (Azione amministrazione dispositivo)** su **Turn On as Device Administrator (Attiva come Amministratore dispositivo)** .
4. Impostare **Device Admin Package Name (Nome pacchetto amministratore dispositivo)** su `com.microsoft.windowsintune.companyportal`.
5. Impostare **Device Admin Class Name (Nome classe amministratore dispositivo)** su `com.microsoft.omadm.client.PolicyManagerReceiver`.

Continuare a pubblicare il profilo e utilizzarlo con l'app StageNow nel dispositivo. All’app Portale aziendale viene concesso il ruolo Amministratore dispositivo.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Passaggio 3: registrare il dispositivo in Intune

Dopo aver completato i primi due passaggi, l'app Portale aziendale viene installata nel dispositivo. Il dispositivo è pronto per essere registrato in Intune.

[Registrare dispositivi Android](../enrollment/android-enroll.md) elenca i passaggi. Se si dispone di più dispositivi Zebra, è consigliabile utilizzare un [account manager di registrazione dispositivi (DEM)](../enrollment/device-enrollment-manager-enroll.md). L’utilizzo dell’account DEM consente anche di eliminare la possibilità di annullare la registrazione dall'app Portale aziendale, in modo che gli utenti non possano annullare la registrazione con estrema facilità.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Passaggio 4: creare un profilo di gestione dei dispositivi in StageNow

Utilizzare StageNow per creare un profilo che consente di configurare le impostazioni desiderate per la gestione del dispositivo. Per informazioni dettagliate specifiche, vedere la documentazione di Zebra. I [profili](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (si apre il sito Web di Zebra) possono rappresentare un'ottima risorsa.

Quando si crea il profilo in StageNow, nell'ultimo passaggio, selezionare **Export to MDM (Esporta in MSM)** . Questo passaggio genera un file XML. Salvare questo file. Sarà necessario in un passaggio successivo.

- È consigliabile testare il profilo prima di distribuirlo ai dispositivi nell'organizzazione. Per effettuare il test, durante l’ultimo passaggio per la creazione dei profili con StageNow nel computer, utilizzare le opzioni **Test**. Quindi, utilizzare il file generato da StageNow con l'app StageNow nel dispositivo.

  L'app StageNow nel dispositivo mostra i log generati quando si testa il profilo. [Utilizzare i log StageNow sui dispositivi Zebra che eseguono Android in Intune](android-zebra-mx-logs-troubleshoot.md) contiene informazioni sull'utilizzo del log di StageNow per ottenere informazioni sugli errori.

- Se si fa riferimento ad app, pacchetti di aggiornamento o si aggiornano altri file nel profilo di StageNow, in genere si desidera che tali aggiornamenti vegano scaricati sul dispositivo. Per scaricare gli aggiornamenti, il dispositivo deve connettersi al server di distribuzione StageNow quando viene applicato il profilo. 

  In alternativa, è possibile usare le funzionalità incorporate in Intune per ottenere queste modifiche, tra cui:

  - Funzionalità di gestione delle app per [aggiungere](../apps/apps-add.md), [distribuire](../apps/apps-deploy.md), aggiornare e [monitorare](../apps/apps-monitor.md) le app.
  - Gestione di [aggiornamenti di sistema e app](device-restrictions-android-for-work.md#device-owner-only) nei dispositivi che eseguono Android Enterprise

Dopo avere testato il file, il passaggio successivo consiste nel distribuire il profilo ai dispositivi con Intune.

- È possibile distribuire uno o più profili MX in un dispositivo.
- È anche possibile esportare più profili StageNow e combinare le impostazioni in un unico file XML. Caricare quindi il file XML in Intune per la distribuzione nei dispositivi.

  > [!WARNING]
  > Se più profili MX sono assegnati allo stesso gruppo e si configura la stessa proprietà, si verificano conflitti nel dispositivo.
  >
  > Se la stessa proprietà viene configurata più volte in un singolo profilo MX, l'ultima configurazione prevale.

## <a name="step-5-create-a-profile-in-intune"></a>Passaggio 5: creare un profilo iOS in Intune

Creare un profilo di configurazione del dispositivo in Intune:

1. Accedere al centro di [amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **dispositivi** > **profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Descrizione:** immettere una descrizione per il profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Android**.
    - **Tipo di profilo**: selezionare il **profilo MX (solo Zebra)** .

4. In **MX profile in .xml format (Profilo MX in formato .xml)** , aggiungere il file del profilo XML [esportato da StageNow](#step-4-create-a-device-management-profile-in-stagenow) (in questo articolo).
5. Selezionare **OK** > **Crea** per salvare le modifiche. Il criterio viene creato e visualizzato nell'elenco.

    > [!TIP]
    > Per motivi di sicurezza, non sarà possibile vedere il testo XML del profilo dopo averlo salvato. Il testo è crittografato e viene sostituito da asterischi (`****`). Per riferimento, è consigliabile salvare le copie dei profili MX prima di aggiungerli a Intune.

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

La volta successiva che il dispositivo verifica la disponibilità di aggiornamenti di configurazione, il profilo MX viene distribuito sul dispositivo. I dispositivi vengono sincronizzati con Intune quando vengono registrati e quindi ogni 8 ore circa. È anche possibile [forzare una sincronizzazione in Intune](../remote-actions/device-sync.md). In alternativa, sul dispositivo, aprire l’**app Portale aziendale** > **Impostazioni** > **Sincronizzazione**. 

## <a name="update-a-zebra-mx-configuration-after-its-assigned"></a>Aggiornare una configurazione di zebra MX dopo che è stata assegnata

Per aggiornare la configurazione specifica di MX di un dispositivo Zebra, è possibile: 

- Creare un file XML StageNow aggiornato, modificare il profilo MX di Intune esistente e caricare il nuovo file XML StageNow. Questo nuovo file sovrascrive i criteri precedenti nel profilo e sostituisce la configurazione precedente.
- Creare un nuovo file XML StageNow per configurare impostazioni diverse, creare un nuovo profilo MX di Intune, caricare il nuovo file XML StageNow e assegnarlo allo stesso gruppo. Vengono distribuiti più profili. Se il nuovo profilo configura le impostazioni già presenti nei profili esistenti, si verificheranno dei conflitti.

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
- [Usare i log StageNow per risolvere i problemi relativi ai dispositivi Zebra](android-zebra-mx-logs-troubleshoot.md).
