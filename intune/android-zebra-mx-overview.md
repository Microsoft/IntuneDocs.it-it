---
title: Usare le estensioni di mobilità nei dispositivi Android in Microsoft Intune - Azure | Microsoft Docs
description: Usare Microsoft Intune per gestire e usare dispositivi Zebra che eseguono Android con le mobilità delle estensioni (MX). Vedere tutti i passaggi, tra cui installare l'app portale aziendale, effettuare il sideload delle app, assegnare il ruolo di amministratore dispositivo, creare un profilo StageNow e altro ancora.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490605"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Usare e gestire i dispositivi Zebra con le estensioni di mobilità in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune include un'ampia gamma di funzionalità, ad esempio la gestione delle App e configurare le impostazioni del dispositivo. Queste funzionalità incorporate e le impostazioni vengono usate per gestire i dispositivi Android realizzati dalle tecnologie, noto anche come "dispositivi zebrato".

Se si desidera personalizzare o aggiungere altre impostazioni Zebra specifiche, è inoltre possibile utilizzare Zebra **mobilità delle estensioni (MX)** su questi dispositivi. 

Questa funzionalità si applica a:

- Android

La società può usare dispositivi zebrato per la vendita al dettaglio, in ambiente di produzione e molto altro. Ad esempio, si ha un rivenditore e l'ambiente include migliaia di dispositivi mobili Zebra usati dagli assistenti alle vendite. Intune consente di gestire questi dispositivi come parte della soluzione mobile device management (MDM).

Con Intune, è possibile registrare i dispositivi Zebra per distribuire le app line-of-business ai dispositivi. I profili "Configurazione del dispositivo" consentono di creare i profili per gestire le impostazioni specifiche Zebra MX.

Questo articolo illustra come usare le mobilità delle estensioni (MX) nei dispositivi Zebra in Microsoft Intune.

## <a name="before-you-begin"></a>Prima di iniziare

- Assicurarsi di avere la versione più recente dell'app desktop StageNow le tecnologie.
- Assicurarsi di controllare [matrice di funzionalità del Zebra completo MX](http://techdocs.zebra.com/mx/compatibility) (si apre in sito web delle) per verificare che i profili creati siano compatibili con versione MX, versione del sistema operativo e il modello del dispositivo.
- Alcuni dispositivi, ad esempio dispositivi TC20/25, non supportano tutte le funzionalità MX disponibili in StageNow. Assicurarsi di controllare [matrice di funzionalità del Zebra](http://techdocs.zebra.com/mx/tc2x/) (si apre in sito web delle) per informazioni sul supporto aggiornato.

## <a name="step-1-install-the-latest-company-portal-app"></a>Passaggio 1: Installare l'app portale aziendale più recente

Nel dispositivo, passare a Google Play store, scaricare e installare l'app portale aziendale di Intune da Microsoft. Durante l'installazione da Google Play, l'app portale aziendale Ottiene gli aggiornamenti e correzioni automaticamente.

Se Google Play non è disponibile, scaricare il [portale aziendale di Microsoft Intune per Android](https://www.microsoft.com/download/details.aspx?id=49140) (si apre un altro sito Web Microsoft), e [effettuare il sideload,](#sideload-the-company-portal-app) (in questo articolo). Quando è installato in questo modo, l'app non può ricevere gli aggiornamenti o corregge automaticamente. Verranno regolarmente aggiornamento e patch manualmente l'app.

### <a name="sideload-the-company-portal-app"></a>Trasferire localmente l'app Portale aziendale

"Sideload" è quando non si usa Google Play per installare un'app. Trasferire localmente l'app portale aziendale, usare StageNow. 

I passaggi seguenti offrono una panoramica. Per informazioni dettagliate, vedere documentazione di zebrato. [Registrare un MDM usando StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (si apre in sito web delle) può essere un'ottima risorsa.

1. In StageNow, creare un profilo per **Enroll in MDM un**.
2. Nelle **distribuzione**, scegliere di scaricare il file dell'agente MDM.
3. Impostare il **App di supporto** e **Scarica Configuration** la procedura per **No**.
4. Nelle **MDM scaricare**, selezionare **trasferimento o copiare File**. Aggiungere l'origine e la destinazione del pacchetto Android di portale aziendale (APK).
5. Nelle **MDM avviare**, lasciare i valori predefiniti come-è. Aggiungere i dettagli seguenti:

    - **Nome pacchetto**: `com.microsoft.windowsintune.companyportal`
    - **Nome classe**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Continuare a pubblicare il profilo e usarla con l'app StageNow nel dispositivo. L'app portale aziendale è installata e aperta sul dispositivo.

> [!TIP]
> Per altre informazioni su StageNow e cosa, vedere [staging dispositivo StageNow Android](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (si apre in sito web delle).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Passaggio 2: Verificare che l'app portale aziendale ha il ruolo di amministratore dispositivo

L'app portale aziendale richiede l'amministratore del dispositivo per gestire i dispositivi Android. Per attivare il ruolo di amministratore del dispositivo, alcuni dispositivi Zebra includono un'interfaccia utente (UI) nel dispositivo. Se il dispositivo include un'interfaccia utente, l'app portale aziendale chiede all'utente finale per concedere l'amministratore del dispositivo durante [registrazione](#step-3-enroll-the-device-in-to-intune) (in questo articolo).

Se un'interfaccia utente non è disponibile, usare il **DevAdmin Manager** in StageNow per creare un profilo che concede l'amministratore del dispositivo manualmente per l'app portale aziendale.

I passaggi seguenti offrono una panoramica. Per informazioni dettagliate, vedere documentazione di zebrato. 
[Impostare la modalità di scambio della batteria come amministratore del dispositivo](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (si apre in sito Web del Zebra) può essere un'ottima risorsa.

1. In StageNow, creare un profilo e selezionare **Xpert modalità**.
2. Aggiungere **DevAdmin Manager** al profilo.
3. Impostare **azione di amministrazione del dispositivo** al **attivare come amministratore del dispositivo**.
4. Impostare **nome del pacchetto di amministratore dispositivo** a `com.microsoft.windowsintune.companyportal`.
5. Impostare **nome della classe di amministratore dispositivo** a `com.microsoft.omadm.client.PolicyManagerReceiver`.

Continuare a pubblicare il profilo e usarla con l'app StageNow nel dispositivo. L'app portale aziendale viene concesso il ruolo di amministratore del dispositivo.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Passaggio 3: Registrare il dispositivo in Intune

Dopo aver completato i primi due passaggi, l'app portale aziendale è installata nel dispositivo. Il dispositivo è pronto per essere iscritti a Intune.

[Registrare i dispositivi Android](android-enroll.md) Elenca i passaggi. Se si dispone di molti dispositivi zebrato, è possibile usare una [account di manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Passaggio 4: Creare un profilo di gestione di dispositivi in StageNow

Usare StageNow per creare un profilo che consente di configurare le impostazioni desiderate per la gestione del dispositivo. Per informazioni dettagliate, vedere documentazione di zebrato. [I profili](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (si apre in sito Web del Zebra) può essere un'ottima risorsa.

Quando si crea il profilo in StageNow, nell'ultimo passaggio, selezionare **esportare in MDM**. Verrà generato un file XML. Salvare questo file. È necessario in un passaggio successivo.

> [!TIP]
> È consigliabile per testare il profilo prima di distribuirla ai dispositivi nell'organizzazione. Per testare, nell'ultimo passaggio quando si creano i profili con StageNow nel computer, usare il **testare** opzioni. Quindi, utilizzare il file generato StageNow con l'app StageNow nel dispositivo. 
> 
> L'app StageNow nel dispositivo vengono visualizzati i log generati quando si testa il profilo. [Usare StageNow accede Zebra dispositivi Android in Intune](android-zebra-mx-logs-troubleshoot.md) contiene informazioni sull'uso dei log StageNow per informazioni sugli errori.

> [!NOTE]
> Se si fa riferimento le app, i pacchetti di aggiornamento o aggiornare altri file nel profilo StageNow, si vuole che il dispositivo per ottenere questi aggiornamenti. Per ottenere gli aggiornamenti, il dispositivo deve connettersi al server di distribuzione StageNow quando viene applicato il profilo. 
> 
> In alternativa, è possibile usare le funzionalità incorporate in Intune per ottenere queste modifiche, tra cui: 
> - Funzionalità di gestione delle app da [aggiungere](apps-add.md), [distribuire](apps-deploy.md), aggiornare, e [monitor](apps-monitor.md) app.
> - Gestire [gli aggiornamenti di sistema e app](device-restrictions-android-for-work.md#device-owner-only) nei dispositivi che eseguono Android Enterprise

Dopo avere testato il file, il passaggio successivo consiste nel distribuire il profilo ai dispositivi con Intune.

> [!NOTE]
> Distribuire un profilo per ogni dispositivo. Se sono presenti più profili StageNow da distribuire nei dispositivi, quindi esportare i profili StageNow e combinare le impostazioni in un unico file XML prima di aggiungerlo a Intune. 
> 
> Per evitare che due impostazioni che consentono di configurare la stessa proprietà nello stesso file XML. L'obiettivo è evitare conflitti tra le impostazioni del dispositivo.

## <a name="step-5-create-a-profile-in-intune"></a>Passaggio 5: Creare un profilo di Intune

Creare un profilo di configurazione del dispositivo in Intune:

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Descrizione:** immettere una descrizione per il profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Android**.
    - **Tipo di profilo**: selezionare **profilo MX (solo Zebra)**.

4. Nelle **profilo MX in formato XML**, aggiungere il file del profilo XML [esportato da StageNow](#step-4-create-a-device-management-profile-in-stagenow) (in questo articolo).
5. Selezionare **OK** > **Crea** per salvare le modifiche. Il criterio viene creato e visualizzato nell'elenco.

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

La volta successiva che il dispositivo verifica la disponibilità di aggiornamenti di configurazione, il profilo MX viene distribuito al dispositivo. Sincronizzare i dispositivi con Intune quando registrano i dispositivi e quindi ogni 8 ore circa. È anche possibile [forzare una sincronizzazione in Intune](device-sync.md). In alternativa, nel dispositivo, aprire il **app portale aziendale** > **impostazioni** > **sincronizzazione**. 

> [!TIP]
> - Per motivi di sicurezza, sarà possibile vedere il testo XML del profilo dopo averlo salvato. Il testo è crittografato e viene visualizzato solo un asterisco (`****`). Per riferimento, è consigliabile salvarne le copie dei profili MX prima di aggiungerli a Intune.
> 
> - Per aggiornare un profilo dopo che è assegnato ai dispositivi zebrato, creare un file XML StageNow aggiornato, modificare il profilo di Intune esistente e aggiungere il nuovo file StageNow XML. Questo nuovo file sovrascrive i precedenti criteri StageNow nel profilo.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

[Usare i log StageNow per risolvere i problemi di dispositivi Zebra](android-zebra-mx-logs-troubleshoot.md).
