---
title: Impostazioni dei criteri di Mac OS X | Documentazione Microsoft
description: "Intune offre una gamma di impostazioni generali predefinite che è possibile configurare nei dispositivi Mac OS X. È anche possibile usare lo strumento Apple Configurator per creare impostazioni personalizzate non disponibili in Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: 58dc1d872e7e12978652542d80061dd7ed86aeb2


---

# <a name="mac-os-x-configuration-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di configurazione di Mac OS X in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune offre una gamma di impostazioni generali predefinite che è possibile configurare nei dispositivi Mac OS X. È anche possibile usare lo strumento Apple Configurator per creare impostazioni personalizzate non disponibili in Intune.

## <a name="general-configuration-policy-settings"></a>Impostazioni dei criteri di configurazione generali

Usare i **criteri di configurazione generali Mac OS X** di Microsoft Intune per configurare:

-   **Impostazioni di sicurezza del dispositivo**. Scegliere da un elenco di impostazioni predefinite che consentono di controllare una gamma di funzionalità e caratteristiche nel dispositivo.

-   **App conformi e non conformi**. Specificare un elenco di app conformi o non conformi rispetto ai requisiti aziendali. È possibile usare il Report app non conformi per visualizzare la conformità delle app specificate nell'elenco rispetto a quelle installate dagli utenti, ma senza impedire l'effettiva installazione dell'app.

Se l'impostazione che si sta cercando non è visualizzata nell'elenco, è possibile crearla usando i criteri personalizzati di Mac OS X che consentono di importare le impostazioni create con lo strumento Apple Configurator. Per altre informazioni, vedere "Impostazioni di criteri personalizzati" più avanti in questo argomento.

### <a name="password-settings"></a>Impostazioni della password

|Nome impostazione|Dettagli|
|----------------|---------------|
|**Richiedi una password per sbloccare i dispositivi**|Specificare se l'utente deve usare una password per accedere al computer Mac. **Importante:** a differenza dei dispositivi iOS, sui dispositivi Mac OS X all'utente non viene immediatamente richiesto di aggiornare la password per la conformità con questa impostazione.|
|**Tipo di password richiesto**|Specificare se la password usata può essere solo **numerica** o se deve essere di tipo **alfanumerico**, ovvero contenere lettere e numeri. **Importante:** questa impostazione è supportata solo su Mac OS X 10.10.3 e versioni successive.|
|**Numero di caratteri complessi richiesti nella password**|Specificare il numero di caratteri complessi richiesti per la password, da **0** a **4**.<br /><br />Un carattere complesso è un simbolo, ad esempio **?**.|
|**Lunghezza minima password**|Specificare la lunghezza minima della password, da **4** a **14** caratteri.|
|**Consenti password semplici**|Consentire l'uso di password semplici come **0000** o **1234**.|
|**Minuti di inattività prima che venga richiesta la password**|Specificare per quanto tempo il computer deve essere inattivo prima che sia richiesta una password per sbloccarlo.|
|**Scadenza password (giorni)**|Specificare quanti giorni devono trascorrere prima che l'utente sia obbligato a cambiare la password, da **1** a **255** giorni.|
|**Ricorda cronologia password**|Impedire all'utente di specificare una password usata in precedenza. Quando si imposta questa opzione, è anche possibile impostare **Impedisci riutilizzo delle password precedenti** per specificare il numero di password usate in precedenza che non possono essere riutilizzate, da **1** a **24**.|
|**Minuti di inattività prima dell'attivazione dello screen saver**|Specificare per quanto tempo il computer deve rimanere inattivo prima che venga attivato lo screen saver.|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Impostazioni per le app conformi e non conformi
Nell'**Elenco app conformi &amp; non conformi per Mac OS X** abilitare **Impostazioni gestite per i dispositivi** e specificare un elenco di app conformi o non conformi usando le informazioni seguenti.

> [!NOTE]
> Un singolo criterio può contenere solo un elenco di app conformi o non conformi. Non è possibile specificare entrambi nello stesso criterio.
>
> Intune consente di visualizzare un report dei dispositivi con app non conformi. Le app non conformi non vengono rimosse e non ne viene bloccata l'installazione.

|Nome impostazione|Dettagli|
|----------------|---------------|
|**Segnala la mancata conformità quando gli utenti installano le app elencate**|Visualizza le app Mac OS X che gli utenti non sono autorizzati a installare. Se gli utenti installano una qualsiasi di queste app, sarà registrata nel **Report app non conformi**.|
|**Segnala la mancata conformità quando gli utenti installano app non elencate**|Elenca le app Mac OS X che gli utenti sono autorizzati a installare. Se gli utenti installano una qualsiasi altra app, sarà registrata nel **Report app non conformi**.|
|**Aggiungi**|Aggiungere un'app all'elenco selezionato. Specificare il nome scelto, l'autore dell'app (facoltativo) e l'ID bundle dell'app. **Suggerimento:** per trovare l'ID bundle di un'app, usare i passaggi seguenti in un computer Mac in cui è installata l'app:<ol><li>Aprire la cartella in cui è installata l'app, ad esempio **/Applications**.</li><li>Selezionare il bundle *&lt;Nome app&gt;***.app** e scegliere **Show Package Contents** (Visualizza contenuto pacchetto).</li><li>Aprire il file **Info.plist**.</li><li>Controllare il valore associato alla chiave **CFBundleIdentifier**.</li></ol>Il formato per ID bundle è **com.contoso.nomeapp**.|
|**Importa app**|Importare un elenco di app specificate in un file con valori separati da virgola. Nel file usare il formato: nome dell'app, autore, ID bundle dell'app.|
|**Modifica**|Modificare il nome, l'autore e l'ID bundle dell'app selezionata.|
|**Eliminazione**|Eliminare l'app selezionata dall'elenco.|
> [!TIP]
> Per altre informazioni sui report di Intune, vedere [Comprendere le operazioni di Microsoft Intune con l'uso dei report](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> Quando un dispositivo Mac OS X è in modalità di sospensione, criteri e profili non possono essere recapitati né può esserne effettuato l'inventario. Di conseguenza, la console di Intune potrebbe visualizzare temporaneamente lo stato **Impostazioni criteri errate** fino alla successiva riattivazione del dispositivo dalla modalità sospensione.

### <a name="monitor-compliant-and-noncompliant-apps"></a>Monitorare le app conformi e non conformi
Usare il **Report app non conformi** per visualizzare la conformità delle app specificate.

#### <a name="to-run-a-report"></a>Per eseguire un report

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Report** &gt; **Report app non conformi**.

2.  Selezionare i gruppi di dispositivi da controllare, scegliere se verificare la presenza di app conformi, di app non conformi o di entrambi i tipi di app, quindi scegliere **Visualizza report**.

## <a name="mac-os-x-custom-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri personalizzati di Mac OS X in Microsoft Intune
Usare i **criteri di configurazione personalizzati di Mac OS X** di Microsoft Intune per distribuire le impostazioni create con lo [strumento Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) nei dispositivi Mac OS X. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione nei criteri personalizzati di Intune per Mac OS X e distribuire le impostazioni a utenti e dispositivi nell'organizzazione.

Questa funzionalità consente di distribuire le impostazioni di Mac OS X che non possono essere configurate con i criteri di configurazione generale per Mac OS X di Intune.

### <a name="prerequisites"></a>Prerequisiti
Prima di iniziare, è necessario aver installato lo strumento Apple Configurator e creato un file di configurazione contenente le impostazioni da distribuire a utenti o dispositivi. È possibile scaricare e acquisire informazioni su Apple Configurator da [Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

> [!NOTE]
> Intune non segnala la conformità delle singole impostazioni nei criteri personalizzati di Mac OS X. Tuttavia, viene segnalata la conformità generale del criterio.

### <a name="general-settings"></a>Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per i criteri personalizzati di Mac OS X che consenta di identificarli nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sui criteri personalizzati di Mac OS X e altre informazioni rilevanti per consentirne l'individuazione.|


### <a name="custom-settings"></a>Impostazioni personalizzate

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome del profilo di configurazione personalizzato (visualizzato agli utenti)**|Specificare il nome con cui il criterio verrà visualizzato nel dispositivo e nei report dei criteri di Intune.|
    |**File del profilo di configurazione**|Scegliere **Importa**, quindi selezionare il profilo di configurazione creato usando lo strumento Apple Configurator. **Suggerimento**: vedere "Come creare un file del profilo di configurazione" in questo argomento per informazioni sulla creazione del profilo di configurazione.|
    |**Dettagli del profilo di configurazione**|Visualizzare il codice XML per il profilo di configurazione importato.|



### <a name="how-to-create-a-configuration-profile-file"></a>Come creare un file del profilo di configurazione
Il file del profilo di configurazione usato dai criteri personalizzati può essere creato in due modi:

-   Esportare il file, con estensione **mobileconfig**, dallo strumento Apple Configurator.

-   Creare il file manualmente usando lo schema appropriato dalla pagina di [riferimento alle chiavi del profilo di configurazione Apple](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Dec16_HO5-->


