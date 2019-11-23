---
title: Usare OEMConfig in dispositivi Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Usare Microsoft Intune per gestire e usare i dispositivi che eseguono Android Enterprise con OEMConfig. Vedere tutti i passaggi, inclusa una panoramica, vedere i prerequisiti, creare il profilo di configurazione in Intune e visualizzare un elenco delle app OEMConfig supportate.
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
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 075e7a99f72de30e83447a2869154859e33356b9
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390847"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Usare e gestire i dispositivi Android Enterprise con OEMConfig in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In Microsoft Intune, è possibile usare OEMConfig per aggiungere, creare e personalizzare le impostazioni specifiche dell'OEM per i dispositivi Android Enterprise. OEMConfig viene in genere usato per configurare le impostazioni non integrate in Intune. Diversi OEM (Original Equipment Manufacturer) includono impostazioni diverse. Le impostazioni disponibili dipendono dall'OEM incluso nell'app OEMConfig.

Questa funzionalità si applica a:  

- Android Enterprise

Questo articolo descrive OEMConfig, elenca i prerequisiti, Mostra come creare un profilo di configurazione ed elenca le app OEMConfig supportate in Intune.

## <a name="overview"></a>Panoramica

I criteri di OEMConfig sono un tipo speciale di criteri di configurazione dei dispositivi simili ai [criteri di configurazione delle app](../apps/app-configuration-policies-overview.md). OEMConfig è uno standard definito da Google che sfrutta la configurazione delle app in Android per inviare le impostazioni del dispositivo alle app scritte da OEM (Original Equipment Manufacturer). Questo standard consente agli OEM e a EMMs (Enterprise Mobility Management) di compilare e supportare le funzionalità specifiche degli OEM in modo standardizzato. [Altre informazioni su OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Storicamente, EMMs, ad esempio Intune, compilano manualmente il supporto per le funzionalità specifiche dell'OEM dopo che sono state introdotte dall'OEM. Questo approccio comporta sforzi duplicati e un'adozione lenta.

Con OEMConfig, un OEM crea uno schema che definisce le funzionalità di gestione specifiche dell'OEM. L'OEM incorpora lo schema in un'app e quindi inserisce questa app in Google Play. EMM legge lo schema dall'app ed espone lo schema nella console di amministrazione EMM. La console consente agli amministratori di Intune di configurare le impostazioni nello schema.

Quando l'app OEMConfig viene installata in un dispositivo, USA le impostazioni configurate nella console di amministrazione EMM per gestire il dispositivo. Le impostazioni nel dispositivo vengono eseguite dall'app OEMConfig, anziché da un agente MDM compilato da EMM.

Quando l'OEM aggiunge e migliora le funzionalità di gestione, l'OEM aggiorna anche l'app in Google Play. In qualità di amministratore, si ottengono queste nuove funzionalità e aggiornamenti (incluse le correzioni) senza attendere che EMMs includa tali aggiornamenti.

> [!TIP]
> È possibile usare OEMConfig solo con i dispositivi che supportano questa funzionalità e hanno un'app OEMConfig corrispondente. Per dettagli specifici, vedere l'OEM.

## <a name="before-you-begin"></a>Prima di iniziare

Quando si usa OEMConfig, tenere presente le informazioni seguenti:

- Intune espone lo schema dell'app OEMConfig in modo che sia possibile configurarlo. Intune non convalida o modifica lo schema fornito dall'app. Se lo schema non è corretto o contiene dati non accurati, questi dati vengono comunque inviati ai dispositivi. Se si riscontra un problema che ha origine nello schema, contattare l'OEM per informazioni aggiuntive.
- Intune non influenza o controlla il contenuto dello schema dell'app. Intune, ad esempio, non dispone di alcun controllo sulle stringhe, sulla lingua, sulle azioni consentite e così via. È consigliabile contattare l'OEM per informazioni dettagliate e procedure consigliate per la gestione dei dispositivi con OEMConfig.
- In qualsiasi momento, gli OEM possono aggiornare le funzionalità e gli schemi supportati e caricare una nuova app per Google Play. Intune Sincronizza sempre la versione più recente dell'app OEMConfig da Google Play. Intune non mantiene le versioni precedenti dello schema o dell'app. Se si verificano conflitti di versione, è consigliabile contattare l'OEM per ottenere ulteriori informazioni.
- Assegnare un profilo OEMConfig a un dispositivo. Se allo stesso dispositivo sono assegnati più profili, è possibile che venga visualizzato un comportamento incoerente. Il modello OEMConfig supporta solo un singolo criterio per dispositivo.

## <a name="prerequisites"></a>Prerequisiti

Per usare OEMConfig nei dispositivi, assicurarsi di avere i requisiti seguenti:

- Un dispositivo Android Enterprise registrato in Intune.
- App OEMConfig compilata dall'OEM e caricata in Google Play. Se non è Google Play, contattare l'OEM per ottenere ulteriori informazioni.
- L'amministratore di Intune dispone di autorizzazioni di controllo degli accessi in base al ruolo (RBAC) per le **app per dispositivi mobili**, le **configurazioni dei dispositivi**e l'autorizzazione "lettura" in **Android for Work**. Queste autorizzazioni sono necessarie perché i profili OEMConfig usano configurazioni di app gestite per gestire le configurazioni dei dispositivi.

## <a name="prepare-the-oemconfig-app"></a>Preparare l'app OEMConfig

Assicurarsi che il dispositivo supporti OEMConfig, che l'app OEMConfig corretta venga aggiunta a Intune e che l'app sia installata nel dispositivo. Per informazioni, contattare l'OEM.

> [!TIP] 
> Le app OEMConfig sono specifiche dell'OEM. Ad esempio, un'app Sony OEMConfig installata in un dispositivo di tecnologie Zebra non esegue alcuna operazione.

1. Ottenere l'app OEMConfig dal Google Play Store gestito. In [Aggiungere app di Google Play gestito a dispositivi Android Enterprise](../apps/apps-add-android-for-work.md) sono elencati i passaggi.
2. Alcuni OEM possono spedire i dispositivi con l'app OEMConfig preinstallata. Se l'app non è preinstallata, usare Intune per [aggiungere e distribuire l'app nei dispositivi](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Creare un profilo OEMConfig

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Descrizione:** immettere una descrizione per il profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Android Enterprise**.
    - **Tipo di profilo**: selezionare **OEMConfig**.

4. Selezionare **app associata**e selezionare un'app OEMConfig esistente aggiunta in precedenza > **OK**. Assicurarsi di scegliere l'app OEMConfig corretta per i dispositivi a cui si sta assegnando il criterio.

    Se non è presente alcuna app elencata, configurare Google Play gestiti e ottenere le app dall'archivio Google Play gestito. In [Aggiungere app di Google Play gestito a dispositivi Android Enterprise](../apps/apps-add-android-for-work.md) sono elencati i passaggi.

    > [!IMPORTANT]
    > Se è stata aggiunta un'app OEMConfig e la si sincronizza con Google Play, ma non è elencata come **app associata**, potrebbe essere necessario contattare Intune per caricare l'app. Vedere [aggiunta di una nuova app](#supported-oemconfig-apps) (in questo articolo).

5. In **Configura impostazioni con**scegliere di usare la **finestra di progettazione di configurazione** o l' **Editor JSON**:

    > [!TIP]
    > Leggere la documentazione OEM per assicurarsi che le proprietà siano configurate correttamente. Queste proprietà dell'app sono incluse nell'OEM, non in Intune. Intune esegue una convalida minima delle proprietà o di ciò che si immette. Ad esempio, se si immette `abcd` per un numero di porta, il profilo viene salvato così com'è e viene distribuito ai dispositivi con i valori configurati. Assicurarsi di immettere le informazioni corrette.

    - **Progettazione configurazione**: quando si seleziona questa opzione, vengono visualizzate le proprietà disponibili nello schema dell'app per la configurazione.

      - I menu di scelta rapida nella finestra di progettazione di configurazione indicano che sono disponibili più opzioni. Ad esempio, il menu di scelta rapida potrebbe consentire di aggiungere, eliminare e riordinare le impostazioni. Queste opzioni sono incluse nell'OEM. Assicurarsi di leggere la documentazione dell'app OEM per informazioni su come usare queste opzioni per creare i profili.

      - Molte impostazioni hanno valori predefiniti forniti dall'OEM. Per verificare se è presente un valore predefinito, passare il mouse sull'icona info accanto all'impostazione. Una descrizione comando Mostra i valori predefiniti per l'impostazione (se applicabile) e altri dettagli forniti dall'OEM.

      - Se si fa clic su **Cancella** , viene eliminata un'impostazione dal profilo. Se un'impostazione non è presente nel profilo, il suo valore sul dispositivo non cambierà quando viene applicato il profilo.

      - Se si crea un bundle vuoto (non configurato) nella finestra di progettazione di configurazione, questo viene eliminato quando si passa all'editor JSON.

    - **Editor JSON**: quando si seleziona questa opzione, viene aperto un editor JSON con un modello per lo schema di configurazione completo incorporato nell'app. Nell'editor personalizzare il modello con i valori per le diverse impostazioni. Se si usa la **finestra di progettazione di configurazione** per modificare i valori, l'editor JSON sovrascrive il modello con i valori della finestra di progettazione di configurazione.

      - Se si sta aggiornando un profilo esistente, l'editor JSON Mostra le impostazioni salvate per l'ultima volta con il profilo.

      - Gli schemi OEMConfig possono essere di grandi dimensioni e complessi. Se si preferisce aggiornare queste impostazioni usando un editor diverso, selezionare il pulsante **Scarica modello JSON** . Usare un editor di propria scelta per aggiungere i valori di configurazione al modello. Quindi, copiare e incollare il codice JSON aggiornato nella proprietà **Editor JSON** .

      - Per creare un backup della configurazione, è possibile usare l'editor JSON. Dopo aver configurato le impostazioni, usare questa funzionalità per ottenere le impostazioni JSON con i valori. Copiare e incollare il codice JSON in un file e salvarlo. A questo punto si dispone di un file di backup.

    Tutte le modifiche apportate nella finestra di progettazione di configurazione vengono eseguite automaticamente anche nell'editor JSON. Analogamente, tutte le modifiche apportate nell'editor JSON vengono eseguite automaticamente nella finestra di progettazione di configurazione. Se l'input contiene valori non validi, non è possibile spostarsi tra la finestra di progettazione di configurazione e l'editor JSON finché non vengono risolti i problemi.

6. Selezionare **OK** > **Aggiungi** per salvare le modifiche. Il criterio viene creato e visualizzato nell'elenco.

Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

 > [!NOTE]
 > Assegnare un profilo a ogni dispositivo. Il modello OEMConfig supporta solo un criterio per dispositivo.

Alla successiva verifica degli aggiornamenti della configurazione da parte del dispositivo, le impostazioni specifiche dell'OEM configurate vengono applicate all'app OEMConfig.

> [!NOTE]
> Lo standard OEMConfig attualmente non include la creazione di rapporti di stato. Quindi, per impostazione predefinita, i profili mostrano uno stato **in sospeso** .

## <a name="supported-oemconfig-apps"></a>App OEMConfig supportate

Rispetto alle app standard, le app OEMConfig espandono i privilegi di configurazione gestiti concessi da Google per supportare schemi più complessi. Intune supporta attualmente le app OEMConfig seguenti:

-----------------

| OEM | ID bundle | Documentazione OEM (se disponibile) |
| --- | --- | ---|
| Samsung | com. Samsung. Android. Knox. KPU | [Guida dell'amministratore del plug-in del servizio Knox](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Tecnologie Zebra | com. Zebra. oemconfig. Common | [Panoramica di zebra OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com. Datalogic. oemconfig | [Documentazione dell'utente per Datalogic OEMConfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com. Honeywell. oemconfig |  |
| Kyocera | JP. Kyocera. enterprisedeviceconfig |  |
| SpectraLink-codici a barre | com. SpectraLink. Barcode. Service |  |
| SpectraLink-pulsanti | com. SpectraLink. Buttons |  |
| SpectraLink-dispositivo | com. SpectraLink. slnkdevicesettings  |  |
| SpectraLink-registrazione | com. SpectraLink. slnklogger |  |
| SpectraLink-VQO | com. SpectraLink. slnkvqo |  |

-----------------

Se esiste un'applicazione OEMConfig per il dispositivo, ma non è presente nella tabella precedente, o non viene visualizzata nella console di Intune, inviare un messaggio di posta elettronica `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Le app OEMConfig devono essere caricate da Intune prima di poter essere configurate con i profili OEMConfig. Quando un'app è supportata, non è necessario contattare Microsoft per la relativa configurazione nel tenant. È sufficiente seguire le istruzioni disponibili in questa pagina.

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
