---
title: Cancellare i dati usando le azioni di avvio condizionale per i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Informazioni su come cancellare i dati in modo selettivo usando le azioni di avvio condizionale per i criteri di protezione delle app in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a0440e2d6f5890b20ccf020c40bb1037bcfcae38
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564132"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>Cancellare i dati in modo selettivo usando le azioni di avvio condizionale per i criteri di protezione delle app in Intune

I criteri di protezione delle app di Intune consentono di configurare impostazioni per impedire agli utenti finali di accedere a un'app o un account aziendale. Queste impostazioni riguardano la rilocazione dei dati e i requisiti di accesso definiti dall'organizzazione per aspetti quali dispositivi jail-broken e versioni minime del sistema operativo.
 
Usando queste impostazioni, è possibile scegliere in modo esplicito di cancellare i dati aziendali dell'organizzazione dal dispositivo dell'utente finale come azione da intraprendere in caso di non conformità. Per alcune impostazioni sarà possibile configurare più azioni, ad esempio il blocco dell'accesso e la cancellazione dei dati in base a diversi valori specificati.

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>Creare criteri di protezione delle app usando azioni di avvio condizionale

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Criteri di protezione delle app**.
3. Fare clic su **Crea criterio** e selezionare la piattaforma del dispositivo per il criterio. 
4. Fare clic su **Configura le impostazioni obbligatorie** per visualizzare l'elenco di impostazioni configurabili per il criterio. 
5. Se si scorre verso il basso il riquadro Impostazioni, verrà visualizzata la sezione **Avvio condizionale** con una tabella modificabile.

    ![Screenshot delle azioni di accesso per la protezione delle app di Intune](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions01.png)

6. Selezionare una **impostazione** e immettere il **valore** che gli utenti devono soddisfare per accedere all'app aziendale. 
7. Selezionare l'**azione** da intraprendere se gli utenti non soddisfano i requisiti. In alcuni casi è possibile configurare più azioni per una singola impostazione. Per altre informazioni, vedere [Come creare e assegnare criteri di protezione delle app](app-protection-policies.md).

## <a name="policy-settings"></a>Impostazioni criteri 

La tabella delle impostazioni dei criteri di protezione delle app contiene le colonne **Impostazione**, **Valore** e **Azione**.

### <a name="ios-policy-settings"></a>Impostazioni dei criteri di iOS
Per iOS è possibile configurare azioni per le impostazioni seguenti usando l'elenco a discesa della colonna **Impostazione**:
- Numero massimo di tentativi di PIN
- Periodo di prova offline
- Dispositivi jailbroken/rooted
- Versione minima del sistema operativo
- Versione minima dell'app
- Versione minima dell'SDK
- Modello/i dispositivo
- Livello di minaccia massimo consentito del dispositivo

Per usare l'impostazione **Modello/i dispositivo**, inserire un elenco di identificatori di modello iOS separati da punto e virgola. I valori non fanno distinzione tra maiuscole e minuscole. Oltre a trovare l'input "Modello di dispositivi" nei report di Intune, è possibile individuare un identificatore di modello iOS nella colonna Tipo di dispositivo nella [documentazione di supporto di HockeyApp](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types) o in questo [repository GitHub di terze parti](https://gist.github.com/adamawolf/3048717).<br>
Input di esempio: *iPhone5,2;iPhone5,3*

Nei dispositivi degli utenti finali il client Intune eseguirà un'azione in base a una semplice corrispondenza di stringhe relative a modelli di dispositivo specificate in Intune per i criteri di protezione delle applicazioni. La corrispondenza dipende completamente da quanto segnalato dal dispositivo. È consigliabile che l'amministratore IT si assicuri che si verifichi il comportamento previsto, testando questa impostazione con produttori e modelli di dispositivo diversi e usando come destinazione un piccolo gruppo di utenti. Il valore predefinito è **Non configurato**.<br>
Impostare una delle azioni seguenti: 
- Consenti specificati (blocca non specificati)
- Consenti specificati (cancella non specificati)

**Cosa accade se l'amministratore IT inserisce un elenco diverso di identificatori di modello iOS tra i criteri destinati alla stessa app per lo stesso utente di Intune?**<br>
Quando si verificano conflitti tra due criteri di protezione delle app per i valori configurati, Intune applica in genere l'approccio più restrittivo. Di conseguenza, il criterio risultante inviato all'app di destinazione in corso di apertura da parte dell'utente di Intune corrisponde all'intersezione degli identificatori di modello iOS elencati in *Criterio A* e in *Criterio B* specifica per la combinazione app/utente. Si supponga, ad esempio, che *Criterio A* specifichi "iPhone5,2;iPhone5,3", e *Criterio B* specifichi "iPhone5,3". Il criterio risultante per l'utente di Intune di destinazione di *Criterio A* e di *Criterio B* sarà "iPhone5,3". 

### <a name="android-policy-settings"></a>Impostazione dei criteri di Android

Per Android è possibile configurare azioni per le impostazioni seguenti usando l'elenco a discesa della colonna **Impostazione**:
- Numero massimo di tentativi di PIN
- Periodo di prova offline
- Dispositivi jailbroken/rooted
- Versione minima del sistema operativo
- Versione minima dell'app
- Versione minima della patch
- Produttore/i dispositivo
- Attestazione del dispositivo SafetyNet
- Rendi obbligatoria l'analisi delle minacce nelle app
- Versione minima del Portale aziendale
- Livello di minaccia massimo consentito del dispositivo

Usando la **Versione minima del Portale aziendale** è possibile indicare una versione minima definita specifica del Portale aziendale da applicare a un dispositivo di un utente finale. Questa impostazione di avvio condizionale consente di impostare i valori **Blocca accesso**, **Cancella i dati** e **Avvisa** come azioni possibili quando non tutti i valori sono soddisfatti. I formati possibili per questo valore seguono il criterio *[Major].[Minor]* , *[Major].[Minor].[Build]* o *[Major].[Minor].[Build].[Revision]* . Dato che alcuni utenti finali potrebbero voler evitare un aggiornamento immediato forzato delle app, l'opzione Avvisa potrebbe essere la scelta ideale per la configurazione di questa impostazione. Per gli aggiornamenti delle app, Google Play Store ha avuto la buona idea di inviare solo i byte delta, ma questi possono comunque costituire una grande quantità di dati e l'utente potrebbe non voler usare questa procedura se al momento dell'aggiornamento è connesso alla rete mobile. La forzatura di un aggiornamento e il download immediato di un'app aggiornata possono comportare addebiti imprevisti per i dati al momento dell'aggiornamento. L'impostazione **Versione minima del Portale aziendale**, se configurata, influisce su tutti gli utenti finali che ottengono la versione 5.0.4560.0 e le versioni future del Portale aziendale. Questa impostazione non influisce sugli utenti che usano una versione del Portale aziendale precedente alla versione con la quale questa funzionalità viene rilasciata. Gli utenti finali che usano gli aggiornamenti automatici delle app nel proprio dispositivo probabilmente non visualizzeranno alcuna finestra di dialogo di questa funzionalità, dal momento che probabilmente avranno la versione del Portale aziendale più recente. Questa impostazione è presente solo in Android con la protezione delle app per i dispositivi registrati e non registrati.

Per usare l'impostazione **Produttore/i dispositivo**, inserire un elenco di identificatori di modello separati da punto e virgola. I valori non fanno distinzione tra maiuscole e minuscole. È possibile trovare il produttore di un dispositivo Android tramite le impostazioni del dispositivo e nei report di Intune. <br>
Esempio di input: *Produttore A;Produttore B* 

>[!NOTE]
> Questi sono alcuni dei produttori più comuni segnalati dai dispositivi che usano Intune e possono essere usati come input: Asus; Blackberry; Bq; Gionee; Google; Hmd global; Htc; Huawei; Infinix; Kyocera; Lemobile; Lenovo; Lge; Motorola; Oneplus; Oppo; Samsung; Sharp; Sony; Tecno; Vivo; Vodafone; Xiaomi; Zte; Zuk

Nei dispositivi degli utenti finali il client Intune eseguirà un'azione in base a una semplice corrispondenza di stringhe relative a modelli di dispositivo specificate in Intune per i criteri di protezione delle applicazioni. La corrispondenza dipende completamente da quanto segnalato dal dispositivo. È consigliabile che l'amministratore IT si assicuri che si verifichi il comportamento previsto, testando questa impostazione con produttori e modelli di dispositivo diversi e usando come destinazione un piccolo gruppo di utenti. Il valore predefinito è **Non configurato**.<br>
Impostare una delle azioni seguenti: 
- Consenti specificati (blocca non specificati)
- Consenti specificati (cancella non specificati)

**Cosa accade se l'amministratore IT inserisce un elenco diverso di produttori Android tra i criteri destinati alla stessa app per lo stesso utente di Intune?**<br>
Quando si verificano conflitti tra due criteri di protezione delle app per i valori configurati, Intune applica in genere l'approccio più restrittivo. Di conseguenza, il criterio risultante inviato all'app di destinazione in corso di apertura da parte dell'utente di Intune corrisponde all'intersezione dei produttori Android elencati in *Criterio A* e in *Criterio B* specifica per la combinazione app/utente. Si supponga, ad esempio, che *Criterio A* specifichi "Google;Samsung", e *Criterio B* specifichi "Google". Il criterio risultante per l'utente di Intune di destinazione di *Criterio A* e di *Criterio B* sarà "Google". 

### <a name="additional-settings-and-actions"></a>Impostazioni e azioni aggiuntive 

Per impostazione predefinita, la tabella avrà righe popolate come le impostazioni configurate per **Periodo di prova offline** e **Numero massimo di tentativi di PIN**, se l'impostazione **Richiedi PIN per l'accesso** è impostata su **Sì**.
 
Per configurare un'impostazione, selezionarla dall'elenco a discesa nella colonna **Impostazione**. Dopo aver selezionato un'impostazione, viene abilitata la casella di testo modificabile nella colonna **Valore** sulla stessa riga, se è necessario impostare un valore. L'elenco a discesa viene inoltre abilitato nella colonna **Azione** con il set di azioni di avvio condizionale applicabili all'impostazione. 

L'elenco seguente riporta le azioni comuni:
- **Blocca l'accesso**: blocca l'accesso dell'utente finale all'app aziendale.
- **Cancella i dati**: cancella i dati aziendali dal dispositivo dell'utente finale.
- **Avvisa**: visualizza una finestra di dialogo per l'utente finale come messaggio di avviso.

In alcuni casi, ad esempio per l'impostazione **Versione minima del sistema operativo**, è possibile configurare l'impostazione per l'esecuzione di tutte le azioni applicabili in base ai diversi numeri di versione. 

![Screenshot delle azioni di accesso per la protezione delle app - Versione minima del sistema operativo](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions05.png)

Al termine della configurazione di un'impostazione, la riga sarà posta nella visualizzazione di sola lettura e sarà disponibile per la modifica in qualsiasi momento. La riga avrà anche un elenco a discesa disponibile per la selezione nella colonna **Impostazione**. Le impostazioni già configurate che non consentono azioni multiple non saranno disponibili per la selezione nell'elenco a discesa.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui criteri di protezione delle app di Intune, vedere:
- [Come creare e assegnare criteri di protezione delle app](app-protection-policies.md) (How to create and assign app protection policies)
- [Impostazioni dei criteri di protezione delle app per iOS](app-protection-policy-settings-ios.md)
- [Impostazioni dei criteri di protezione delle app di Android in Microsoft Intune](app-protection-policy-settings-android.md) 
