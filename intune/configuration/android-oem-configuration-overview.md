---
title: Usare OEMConfig in dispositivi Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Usare Microsoft Intune per gestire e usare i dispositivi che eseguono Android Enterprise con OEMConfig. Leggere tutti i passaggi, inclusa una panoramica, verificare i prerequisiti, creare il profilo di configurazione in Intune e visualizzare un elenco delle app OEMConfig supportate.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cc568cbadb683f632ffd2365ab7023cd796f231
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886698"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Usare e gestire i dispositivi Android Enterprise con OEMConfig in Microsoft Intune

In Microsoft Intune è possibile usare OEMConfig per aggiungere, creare e personalizzare le impostazioni specifiche dell'OEM per i dispositivi Android Enterprise. OEMConfig viene in genere usato per configurare le impostazioni che non sono integrate in Intune. Le impostazioni variano a seconda dell'OEM (Original Equipment Manufacturer). Quelle disponibili dipendono dai dati inclusi dall'OEM nell'app OEMConfig.

Questa funzionalità si applica a:  

- Android Enterprise

Questo articolo descrive OEMConfig, elenca i prerequisiti, mostra come creare un profilo di configurazione e include l'elenco delle app OEMConfig supportate in Intune.

## <a name="overview"></a>Panoramica

I criteri di OEMConfig sono un tipo particolare di criteri di configurazione dei dispositivi simili ai [criteri di configurazione delle app](../apps/app-configuration-policies-overview.md). OEMConfig è uno standard definito da Google che usa la configurazione delle app in Android per inviare le impostazioni dei dispositivi alle app create dagli OEM. Questo standard consente agli OEM e ai provider EMM (Enterprise Mobility Management) di creare e supportare le funzionalità specifiche degli OEM in modo standardizzato. [Altre informazioni su OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Storicamente, i provider EMM, ad esempio Intune, creano manualmente il supporto per le funzionalità specifiche dell'OEM dopo che sono state introdotte dall'OEM. Questo approccio richiede un duplice sforzo e rallenta il processo di adozione.

Con OEMConfig, un OEM crea uno schema che definisce le sue specifiche funzionalità di gestione. L'OEM incorpora lo schema in un'app e quindi pubblica l'app su Google Play. Il provider EMM legge lo schema dall'app ed espone lo schema nella console di amministrazione EMM, che gli amministratori di Intune possono usare per configurare le impostazioni nello schema.

Quando viene installata in un dispositivo, l'app OEMConfig usa le impostazioni configurate nella console di amministrazione EMM per gestire il dispositivo. Le impostazioni del dispositivo vengono eseguite dall'app OEMConfig, anziché da un agente MDM creato dal provider EMM.

Quando l'OEM introduce miglioramenti o nuove funzionalità di gestione, aggiorna anche l'app su Google Play. In qualità di amministratore, si possono scaricare le nuove funzionalità e gli aggiornamenti (incluse le correzioni) senza attendere che vengano inclusi dai provider EMM.

> [!TIP]
> È possibile usare OEMConfig solo con i dispositivi che supportano questa funzionalità e hanno un'app OEMConfig corrispondente. Per dettagli specifici, consultare l'OEM.

## <a name="before-you-begin"></a>Prima di iniziare

Quando si usa OEMConfig, tenere presenti le informazioni seguenti:

- Intune espone lo schema dell'app OEMConfig per consentire di configurarlo. Intune non convalida né modifica lo schema fornito dall'app. Se lo schema non è corretto o contiene dati poco precisi, i dati vengono comunque inviati ai dispositivi. Se si riscontra un problema che ha origine dallo schema, contattare l'OEM per indicazioni.
- Intune non ha alcun controllo o influenza sul contenuto dello schema dell'app, ad esempio sulle stringhe, la lingua, le azioni consentite e così via. Per altre informazioni sulla gestione dei dispositivi con OEMConfig, è consigliabile contattare l'OEM.
- In qualsiasi momento, gli OEM possono aggiornare le funzionalità e gli schemi supportati e caricare una nuova app su Google Play. Intune esegue sempre la sincronizzazione con la versione più recente dell'app OEMConfig da Google Play. Intune non gestisce le versioni precedenti dello schema o dell'app. Se si verificano conflitti di versione, è consigliabile contattare l'OEM per altre informazioni.
- A un dispositivo deve essere assegnato un unico profilo OEMConfig. Se allo stesso dispositivo sono assegnati più profili, può verificarsi un comportamento incoerente. Il modello OEMConfig supporta un singolo criterio per dispositivo.

## <a name="prerequisites"></a>Prerequisiti

Per usare OEMConfig nei dispositivi, assicurarsi che siano soddisfatti i requisiti seguenti:

- Un dispositivo Android Enterprise registrato in Intune.
- Un'app OEMConfig creata dall'OEM e caricata su Google Play. Se non è disponibile su Google Play, contattare l'OEM per altre informazioni.
- L'amministratore di Intune dispone di autorizzazioni di controllo degli accessi in base al ruolo (RBAC) per le **app per dispositivi mobili**, le **configurazioni dei dispositivi** e l'autorizzazione di lettura in **Android for Work**. Queste autorizzazioni sono necessarie perché i profili OEMConfig usano configurazioni di app gestite per gestire le configurazioni dei dispositivi.

## <a name="prepare-the-oemconfig-app"></a>Preparare l'app OEMConfig

Assicurarsi che il dispositivo supporti OEMConfig, che l'app OEMConfig corretta sia stata aggiunta a Intune e che l'app sia installata nel dispositivo. Per queste informazioni, contattare l'OEM.

> [!TIP] 
> Le app OEMConfig sono specifiche dell'OEM. Ad esempio, un'app OEMConfig di Sony installata in un dispositivo Zebra Technologies non esegue alcuna operazione.

1. Scaricare l'app OEMConfig da Google Play Store gestito. In [Aggiungere app di Google Play gestito a dispositivi Android Enterprise](../apps/apps-add-android-for-work.md) sono elencati i passaggi.
2. Alcuni OEM possono distribuire i dispositivi con l'app OEMConfig preinstallata. Se l'app non è preinstallata, usare Intune per [aggiungere e distribuire l'app nei dispositivi](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Creare un profilo OEMConfig

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Piattaforma**: selezionare **Android Enterprise**.
    - **Tipo di profilo**: selezionare **OEMConfig**.

4. Selezionare **Crea**.
5. In **Informazioni di base** immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **App OEMConfig**: scegliere **Selezionare un'app OEMConfig**.

6. In **App associata** selezionare un'app OEMConfig esistente aggiunta in precedenza > **Seleziona**. Assicurarsi di scegliere l'app OEMConfig corretta per i dispositivi a cui si sta assegnando il criterio.

    Se nell'elenco non sono presenti app, configurare Google Play gestito e scaricare le app da Google Play Store gestito. In [Aggiungere app di Google Play gestito a dispositivi Android Enterprise](../apps/apps-add-android-for-work.md) è illustrata la procedura.

    > [!IMPORTANT]
    > Se un'app OEMConfig è stata aggiunta e sincronizzata con Google Play, ma non è inclusa nell'elenco come **App associata**, potrebbe essere necessario contattare Intune per eseguire l'onboarding dell'app. Vedere le istruzioni per l'[aggiunta di una nuova app](#supported-oemconfig-apps) (in questo articolo).

7. Selezionare **Avanti**.
8. In **Configura impostazioni** selezionare **Progettazione configurazione** o **Editor JSON**:

    > [!TIP]
    > Leggere la documentazione dell'OEM per assicurarsi di configurare le proprietà in modo corretto. Queste proprietà dell'app vengono incluse dall'OEM, non da Intune. Intune esegue una convalida minima delle proprietà o dei dati immessi dall'utente. Se ad esempio si immette `abcd` per un numero di porta, il profilo viene salvato così com'è e distribuito ai dispositivi con i valori configurati. Assicurarsi di immettere le informazioni corrette.

    - **Progettazione configurazione**: quando si seleziona questa opzione, vengono visualizzate le proprietà disponibili nello schema dell'app per consentirne la configurazione.

      - I menu di scelta rapida nella finestra di progettazione di configurazione indicano che sono disponibili più opzioni. Ad esempio, il menu di scelta rapida potrebbe consentire di aggiungere, eliminare e riordinare le impostazioni. Queste opzioni vengono incluse dall'OEM. Assicurarsi di leggere la documentazione dell'app OEM per informazioni su come usare queste opzioni per creare i profili.

      - Molte impostazioni hanno valori predefiniti forniti dall'OEM. Per verificare se è presente un valore predefinito, passare il puntatore del mouse sull'icona informazioni accanto all'impostazione. Una descrizione comando mostra i valori predefiniti per l'impostazione (se applicabili) e altri dettagli forniti dall'OEM.

      - Facendo clic su **Cancella** viene eliminata un'impostazione dal profilo. Se un'impostazione non è presente nel profilo, il suo valore sul dispositivo rimane invariato quando il profilo viene applicato.

      - Se si crea un bundle vuoto (non configurato) nella finestra di progettazione di configurazione, questo viene eliminato quando si passa all'editor JSON.

    - **Editor JSON**: quando si seleziona questa opzione, viene aperto un editor JSON con un modello per lo schema di configurazione completo incorporato nell'app. Nell'editor personalizzare il modello con i valori per le diverse impostazioni. Se si usa **Progettazione configurazione** per modificare i valori, l'editor JSON sovrascrive il modello con i valori della finestra di progettazione di configurazione.

      - Se si aggiorna un profilo esistente, l'editor JSON mostra le impostazioni salvate per ultime con il profilo.

      - Gli schemi OEMConfig possono essere complessi e di grandi dimensioni. Se si preferisce aggiornare queste impostazioni usando un editor diverso, selezionare il pulsante **Download del modello JSON** . Usare un editor di propria scelta per aggiungere i valori di configurazione al modello. Quindi, copiare e incollare il codice JSON aggiornato nella proprietà **Editor JSON**.

      - Per creare una copia di backup della configurazione, è possibile usare l'editor JSON. Dopo aver configurato le impostazioni, usare questa funzionalità per ottenere le impostazioni JSON con i valori. Copiare e incollare il codice JSON in un file e salvarlo. A questo punto si ha un file di backup.

    Tutte le modifiche apportate nella finestra di progettazione di configurazione vengono applicate automaticamente anche nell'editor JSON. Analogamente, tutte le modifiche apportate nell'editor JSON vengono eseguite automaticamente nella finestra di progettazione di configurazione. Se l'input contiene valori non validi, non è possibile spostarsi tra la finestra di progettazione di configurazione e l'editor JSON finché non sono stati risolti i problemi.

9. Selezionare **Avanti**.
10. In **Tag ambito** (facoltativo) assegnare un tag per filtrare il profilo a gruppi IT specifici, ad esempio `US-NC IT Team` o `JohnGlenn_ITDepartment`. Per altre informazioni sui tag di ambito, vedere [Usare il controllo degli accessi in base al ruolo (RBAC) e i tag di ambito per l'infrastruttura IT distribuita](../fundamentals/scope-tags.md).

    Selezionare **Avanti**.

11. In **Assegnazioni** selezionare gli utenti o i gruppi che riceveranno il profilo. Assegnare un profilo a ogni dispositivo. Il modello OEMConfig supporta un solo criterio per dispositivo.

    Per altre informazioni sull'assegnazione di profili, vedere [Assegnare profili utente e dispositivo](device-profile-assign.md).

    Selezionare **Avanti**.

12. In **Rivedi e crea** rivedere le impostazioni. Quando si seleziona **Crea**, le modifiche vengono salvate e il profilo viene assegnato. Il criterio viene visualizzato anche nell'elenco dei profili.

Alla successiva verifica degli aggiornamenti della configurazione da parte del dispositivo, le impostazioni specifiche dell'OEM configurate vengono applicate all'app OEMConfig.

> [!NOTE]
> Lo standard OEMConfig non include attualmente la creazione di rapporti di stato. Pertanto, i profili mostrano lo stato **In sospeso** per impostazione predefinita.

## <a name="supported-oemconfig-apps"></a>App OEMConfig supportate

Rispetto alle app standard, le app OEMConfig espandono i privilegi delle configurazioni gestite concessi da Google per supportare schemi più complessi. Intune supporta attualmente le app OEMConfig seguenti:

-----------------

| OEM | ID bundle | Documentazione dell'OEM (se disponibile) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Guida dell'amministratore di Knox Service Plugin](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra Technologies | com.zebra.oemconfig.common | [Panoramica di Zebra OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [Documentazione dell'utente per Datalogic OEMConfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| SpectraLink - Codici a barre | com.spectralink.barcode.service |  |
| SpectraLink - Pulsanti | com.spectralink.buttons |  |
| SpectraLink - Dispositivo | com.spectralink.slnkdevicesettings  |  |
| SpectraLink - Registrazione | com.spectralink.slnklogger |  |
| SpectraLink - VQO | com.spectralink.slnkvqo |  |
| HMD Global | com.hmdglobal.app.oemconfig.ironman |  |

-----------------

Se per il dispositivo esiste un'applicazione OEMConfig, ma non è presente nella tabella precedente, o non viene visualizzata nella console di Intune, inviare un messaggio di posta elettronica all'indirizzo `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Le app OEMConfig devono essere caricate da Intune prima di poter essere configurate con i profili OEMConfig. Quando un'app è supportata, non è necessario contattare Microsoft per la relativa configurazione nel tenant. È sufficiente seguire le istruzioni riportate in questa pagina.

## <a name="next-steps"></a>Passaggi successivi

[Monitorare lo stato del profilo](device-profile-monitor.md).
