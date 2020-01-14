---
title: Come monitorare i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Questo argomento illustra come monitorare i criteri di protezione delle app in Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36a84296aabd2d78cbc3cdc14ffb8f696afa5c22
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75205259"
---
# <a name="how-to-monitor-app-protection-policies"></a>Come monitorare i criteri di protezione delle app
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

È possibile monitorare lo stato dei criteri di protezione delle app applicati agli utenti nel riquadro di protezione delle app di Intune nel [portale di Azure](https://portal.azure.com). Sono anche disponibili informazioni sugli utenti interessati dai criteri di protezione delle app, lo stato di conformità di questi criteri ed eventuali problemi che gli utenti potrebbero riscontrare.

I criteri di protezione delle app possono essere monitorati in tre posizioni diverse:
- Visualizzazione di riepilogo
- Visualizzazione dettagliata
- Visualizzazione Rapporti

Il periodo di conservazione per i dati di protezione delle app è di 90 giorni. Tutte le istanze dell'app che hanno eseguito la sincronizzazione nel servizio Intune negli ultimi 90 giorni sono incluse nel report sullo stato di protezione dell'app. Un'*istanza dell'app* è un insieme univoco di utente + app + dispositivo. 

> [!NOTE]
> Per altre informazioni, vedere [Come creare e assegnare criteri di protezione delle app](app-protection-policies.md).

## <a name="summary-view"></a>Visualizzazione di riepilogo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selezionare **App** > **Monitoraggio** > **Stato protezione app**.

   ![Screenshot del riquadro di riepilogo del riquadro di gestione di applicazioni per dispositivi mobili di Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Utenti assegnati**: numero totale di utenti assegnati dell'azienda che usano un'app associata a un criterio in un contesto aziendale. Comprende sia gli utenti protetti e con licenza, sia gli utenti non protetti e senza licenza.
- **Utenti contrassegnati**: Numero di utenti che riscontrano problemi con il proprio dispositivo. Gli utenti con dispositivi jailbroken (iOS) e rooted (Android) vengono indicati in **Utenti contrassegnati**. Vengono segnalati qui anche gli utenti con dispositivi contrassegnati dal controllo dell'attestazione del dispositivo SafetyNet di Google, se attivato dall'amministratore IT. 
- **Utenti con app potenzialmente dannose**: numero di utenti che possono avere un'app dannosa nel dispositivo Android rilevato da Google Play Protect. 
- **Stato utente per iOS** e **Stato utente per Android**: numero di utenti che hanno usato un'app e ai quali è associato un criterio in un contesto aziendale per la relativa piattaforma. Questa informazione mostra il numero di utenti gestiti dal criterio e il numero di utenti che usano un'app non associata ad alcun criterio in un contesto aziendale. È consigliabile aggiungere questi utenti ai criteri.
- **Principali app protette di iOS** e **Principali app protette di Android**: in base alle app iOS e Android più usate, questa informazione indica il numero di app protette e non protette dalla piattaforma.
- **Prime app iOS configurate senza registrazione** e **Prime app Android configurate senza registrazione**: in base alle app iOS e Android più usate per i dispositivi non registrati, questa informazione indica il numero di app configurate dalla piattaforma (come se si usassero i criteri di configurazione dell'app).

    > [!NOTE]
    > Se esistono più criteri per ogni piattaforma, un utente viene considerato gestito da criteri quando ha almeno un criterio assegnato.

## <a name="detailed-view"></a>Visualizzazione dettagliata
Per accedere alla visualizzazione dettagliata del riepilogo, scegliere il riquadro **Utenti contrassegnati** e il riquadro **Utenti con app potenzialmente dannose**.

### <a name="flagged-users"></a>Utenti contrassegnati
Nella visualizzazione dettagliata sono indicati il messaggio di errore, l'app a cui si è eseguito l'accesso quando si è verificato l'errore, la piattaforma del sistema operativo del dispositivo interessato e un timestamp. L'errore si verifica in genere per dispositivi jailbroken (iOS) o rooted (Android). In più, gli utenti con dispositivi contrassegnati dal controllo di avvio condizionale 'Attestazione del dispositivo SafetyNet' vengono indicati qui con il motivo segnalato da Google. Perché un utente possa essere rimosso dal report, è necessario che lo stato del dispositivo stesso sia cambiato. Questo si verifica dopo che il controllo di rilevamento radice (o controllo jailbreak/SafetyNet) successivo ha indicato un risultato positivo. Se il dispositivo è stato effettivamente corretto, l'aggiornamento del report Utenti contrassegnati avviene quando il riquadro viene ricaricato.

### <a name="users-with-potentially-harmful-apps"></a>Utenti con app potenzialmente dannose
Gli utenti con dispositivi contrassegnati dal controllo di avvio condizionale **Rendi obbligatoria l'analisi delle minacce nelle app** vengono indicati qui con la categoria di minaccia segnalata da Google. Se nel report sono elencate app in corso di distribuzione tramite Intune, contattare lo sviluppatore dell'app o rimuovere l'app dall'assegnazione agli utenti. La visualizzazione dettagliata indica:

- **Utente**: Nome dell'utente.
- **ID pacchetto dell'app**: il modo con cui il sistema operativo Android definisce in modo univoco un'app.
- **Se l'app è abilitata per MAM**: indica se l'app viene distribuita o meno tramite Microsoft Intune. 
- **Categoria di minaccia**: categoria di minaccia determinata da Google in cui rientra l'app. 
- **Posta elettronica**: indirizzo di posta elettronica dell'utente.
- **Nome dispositivo**: nomi dei dispositivi associati all'account dell'utente.
- **Timestamp**: la data dell'ultima sincronizzazione eseguita Google con Microsoft Intune relativamente alle app potenzialmente dannose.

## <a name="reporting-view"></a>Visualizzazione Rapporti

Sono visualizzati gli stessi report disponibili nella parte superiore del riquadro **Stato protezione app**. Per visualizzare questi report, selezionare **App** > **Stato protezione app** > **Report**. Nel riquadro **Report** sono disponibili diversi report in base all'utente e all'app, tra cui:

### <a name="user-report"></a>Report utente
È possibile eseguire la ricerca di un singolo utente e controllare il relativo stato di conformità. Il riquadro **Segnalazione app** visualizza le informazioni seguenti per un utente selezionato:
- **Icona**: indica se lo stato dell'app è aggiornato.
- **Nome app**: nome dell'app.
- **Nome dispositivo**: dispositivi associati all'account dell'utente.
- **Tipo di dispositivo**: tipo di dispositivo o sistema operativo in cui è in esecuzione il dispositivo.
- **Criteri**: i criteri associati all'app.
- **Status** (Stato):
  - **Archiviazione eseguita**: i criteri sono stati distribuiti all'utente e l'app è stata usata almeno una volta nel contesto aziendale.
  - **Archiviazione non eseguita**: i criteri sono stati distribuiti all'utente, ma in seguito l'app non è stata usata nel contesto aziendale.
- **Ultima sincronizzazione**: data dell'ultima sincronizzazione dell'app con Intune. 

>[!NOTE]
> La colonna **Ultima sincronizzazione** contiene lo stesso valore sia nel report Stato dell'utente nella console sia nel [report esportabile con estensione csv](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities) Criteri di protezione dell'app. La differenza è un leggero ritardo nella sincronizzazione tra i valori nei due report. 
>
> L'ora a cui fa riferimento Ultima sincronizzazione è l'ultima volta in cui Intune ha rilevato l'istanza dell'app. Quando un utente avvia un'app, può informare il servizio Protezione app di Intune al momento dell'avvio, a seconda dell'ultima archiviazione eseguita. Vedere [i tempi degli intervalli tra tentativi per l'archiviazione di Criteri di protezione dell'app](~/apps/app-protection-policy-delivery.md). Se un utente non ha usato l'app nell'ultimo intervallo di archiviazione, in genere 30 minuti per l'utilizzo attivo, e avvia l'app, si verifica quanto segue:
>
> - Il report esportabile con estensione csv Criteri di protezione dell'app indica l'ora più recente, con un ritardo compreso tra 1 minuto (minimo) e 30 minuti (massimo).
> - Il report Stato dell'utente ha immediatamente l'ora più recente.
>
> Si consideri ad esempio un utente specifico con licenza che avvia un'app protetta alle 12:00:
> - Se si tratta del primo accesso, significa che l'utente prima era disconnesso e non ha registrato un'istanza dell'app con Intune. Dopo l'accesso, l'utente ottiene una nuova registrazione dell'istanza dell'app, che può essere archiviata immediatamente, con gli stessi ritardi elencati in precedenza per le archiviazioni future. L'ora dell'ultima sincronizzazione corrisponde quindi a 12:00 nel report Stato dell'utente e a 12:01 (o a 12:30 al più tardi) nel report Criteri di protezione dell'app. 
> - Se l'utente avvia semplicemente l'app, l'ora dell'ultima sincronizzazione indicata dipende dall'ultima archiviazione eseguita.

Per visualizzare i report generati per un utente, seguire questa procedura:

1. Per selezionare un utente, scegliere il riquadro di riepilogo **Stato utente**.

    ![Schermata del riquadro Riepilogo della funzionalità di gestione di applicazioni mobili di Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. Nel riquadro **Segnalazione app** scegliere **Selezionare l'utente** per cercare un utente di Azure Active Directory.

    ![Schermata dell'opzione Selezionare l'utente nel riquadro Segnalazione app](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Selezionare un utente nell'elenco. È possibile visualizzare i dettagli dello stato di conformità per l'utente.

>[!NOTE]
> Se per l'utente cercato non è stato distribuito il criterio MAM, verrà visualizzato un messaggio che informa che all'utente non è applicato alcun criterio MAM.

### <a name="app-report"></a>Report app
È possibile eseguire la ricerca per piattaforma e app. Questo report offre due diversi stati di protezione dell'app tra cui è possibile scegliere prima di generare il report. Questi stati sono **Protetta** e **Non protetta**.

  - Stato utente per attività MAM gestita (**Protetta**): questo report descrive, per utente, l'attività di ogni app MAM gestita. Visualizza, per utente, tutte le app a cui sono destinati criteri MAM e lo stato di ogni app archiviato con i criteri MAM. Il report include anche lo stato delle app a cui sono destinati criteri MAM ma che non sono mai state archiviate.
  - Stato utente per attività MAM non gestita (**Non protetta**): questo report descrive, per utente, l'attività delle app abilitate per MAM attualmente non gestite. Ciò può verificarsi perché:
    - Le app sono usate da un utente o da un'app a cui attualmente non sono destinati criteri MAM.
    - Tutte le app sono archiviate, ma non ricevono alcun criterio MAM.

    ![Screenshot del riquadro Segnalazione app di un utente con i dettagli di tre app](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**Report configurazione utente**
in base all'utente selezionato, questo report fornisce informazioni dettagliate sulle configurazioni di app ricevute dall'utente.

### <a name="app-configuration-report"></a>**Report configurazione app**
In base alla piattaforma e all'app selezionate, questo report offre informazioni dettagliate sugli utenti che hanno ricevuto configurazioni per l'app selezionata.

### <a name="app-learning-report-for-windows-information-protection"></a>Report di apprendimento app per Windows Information Protection
questo report mostra le app che stanno tentando di oltrepassare i limiti dei criteri.

### <a name="website-learning-for-windows-information-protection"></a>Apprendimento siti Web per Windows Information Protection
questo report mostra i siti Web che stanno tentando di oltrepassare i limiti dei criteri.

## <a name="export-app-protection-activities"></a>Esportare le attività di protezione delle app
È possibile esportare tutte le attività relative ai criteri di protezione delle app in un singolo file con estensione csv. Questa opzione può rivelarsi utile per analizzare tutti gli stati di protezione delle app segnalati dagli utenti. Il **file di protezione dei dati con estensione csv** contiene i dati seguenti:
- **Utente**: Nome dell'utente.
- **Posta elettronica**: indirizzo di posta elettronica dell'utente.
- **App**: nome dell'app.
- **Versione app**: versione dell'app.
- **Nome dispositivo**: nomi dei dispositivi associati all'account dell'utente.
- **Produttore dispositivo**: specifica il produttore del dispositivo (solo Android). 
- **Modello dispositivo**: specifica il produttore del dispositivo (solo Android). 
- **Versione della patch Android**: data dell'ultima patch di sicurezza per Android.
- **ID dispositivo AAD**: questa colonna viene popolata se il dispositivo viene aggiunto ad AAD.
- **ID dispositivo MDM**: questa colonna viene popolata se il dispositivo è registrato nella gestione di dispositivi mobili di Microsoft Intune.
- **Piattaforma**: sistema operativo.
- **Versione piattaforma**: versione del sistema operativo.
- **Tipo di gestione**: tipo di gestione nel dispositivo, ad esempio Android Enterprise, non gestito o MDM.  
- **Stato di protezione dell'app**: non protetto o protetto.
- **Policy** (Criteri): criteri di protezione associati all'app.
- **Ultima sincronizzazione**: data dell'ultima sincronizzazione dell'app con Microsoft Intune. 
- **Stato di conformità**: indica se l'app nel dispositivo dell'utente è conforme ai criteri di accesso condizionale basato su app.  

Seguire questa procedura per generare un file con estensione csv di Protezione app o un file con estensione csv di Configurazione app:

1. Nel pannello Gestione di applicazioni mobili di Intune scegliere **Report protezione app**.

    ![Screenshot del collegamento per il download di Protezione app](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Scegliere **Sì** per salvare il report e quindi scegliere **Salva con nome**. Selezionare la cartella in cui si vuole salvare il report.

    ![Schermata della finestra di conferma Salva report](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> Intune offre campi aggiuntivi per i report relativi ai dispositivi, tra cui ID di registrazione app, produttore Android, modello e versione della patch di sicurezza, oltre al modello iOS. È possibile accedere a questi campi in Intune selezionando **App** > **Stato protezione app** > **Report sulla protezione dell'app: iOS, Android**. Questi parametri consentono anche di configurare l'elenco **Consenti** per il produttore del dispositivo (Android), l'elenco **Consenti** per il modello di dispositivo (Android e iOS) e l'impostazione della **versione minima della patch di sicurezza per Android**.   
 
## <a name="see-also"></a>Vedere anche
- [Gestire il trasferimento di dati tra app iOS](data-transfer-between-apps-manage-ios.md)
- [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](../fundamentals/end-user-mam-apps-android.md)
- [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](../fundamentals/end-user-mam-apps-ios.md)
