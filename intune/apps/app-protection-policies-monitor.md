---
title: Come monitorare i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Questo argomento illustra come monitorare i criteri di protezione delle app in Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b4ab3369f241c9f33d4e0bddfd0dcf98c8ab915
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830591"
---
# <a name="how-to-monitor-app-protection-policies"></a>Come monitorare i criteri di protezione delle app
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

È possibile monitorare lo stato di conformità dei criteri di gestione delle app per dispositivi mobili (MAM) applicati agli utenti nel riquadro di protezione delle app di Intune nel [portale di Azure](https://portal.azure.com). Sono inoltre disponibili informazioni sugli utenti interessati dai criteri MAM, lo stato di conformità di questi criteri ed eventuali problemi riscontrati dagli utenti.

I criteri di protezione delle app possono essere monitorati in tre posizioni diverse:
- Visualizzazione di riepilogo
- Visualizzazione dettagliata
- Visualizzazione Rapporti

> [!NOTE]
> Per informazioni sulla creazione di criteri di protezione delle app, vedere [Come creare e assegnare criteri di protezione delle app](app-protection-policies.md).

Il periodo di conservazione per i dati di protezione delle app è di 90 giorni. Tutte le istanze dell'app che hanno archiviato il servizio MAM negli ultimi 90 giorni verranno incluse nel report Stato protezione app. Un'istanza dell'app è un insieme di utente univoco + app + dispositivo. 

## <a name="summary-view"></a>Visualizzazione di riepilogo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **App client**.
4. Nel carico di lavoro **App client** scegliere **Stato protezione app** nella sezione **Monitoraggio** per esaminare la visualizzazione di riepilogo:

![Riquadro Riepilogo del riquadro Gestione di applicazioni mobili di Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Utenti assegnati**: numero totale di utenti assegnati dell'azienda che usano un'app associata a un criterio in un contesto aziendale. Comprende sia gli utenti protetti e con licenza, sia gli utenti non protetti e senza licenza.
- **Utenti contrassegnati**: numero di utenti che riscontrano problemi. Gli utenti con dispositivi jailbroken (iOS) e rooted (Android) vengono indicati in **Utenti contrassegnati**. Gli utenti con dispositivi contrassegnati dal controllo dell'attestazione del dispositivo SafetyNet di Google (se attivato dall'amministratore IT) vengono indicati qui. 
- **Utenti con app potenzialmente dannose**: numero di utenti che possono avere un'app dannosa nel dispositivo Android rilevato da Google Play Protect. 
- **Stato utente per iOS** e **Stato utente per Android**: numero di utenti che hanno usato un'app e ai quali è associato un criterio in un contesto aziendale per la relativa piattaforma. Questa informazione mostra il numero di utenti gestiti dal criterio e il numero di utenti che usano un'app non associata ad alcun criterio in un contesto aziendale. È consigliabile aggiungere questi utenti ai criteri.
- **Principali app protette di iOS**: in base alle app iOS più usate, questa informazione indica il numero di app iOS protette e non protette.
- **Principali app protette di Android**: in base alle app Android più usate, questa informazione indica il numero di app Android protette e non protette.
- **Prime app iOS configurate senza registrazione**: in base alle app iOS più usate per i dispositivi non registrati, questa informazione indica il numero di app iOS configurate.
- **Prime app Android configurate senza registrazione**: in base alle app Android più usate per i dispositivi non registrati, questa informazione indica il numero di app Android configurate.

    > [!NOTE]
    > Se esistono più criteri per ogni piattaforma, un utente viene considerato gestito da criteri quando ha almeno un criterio assegnato.

## <a name="detailed-view"></a>Visualizzazione dettagliata
Per accedere alla visualizzazione dettagliata del riepilogo, scegliere il riquadro **Stato utente**, a seconda della piattaforma del sistema operativo del dispositivo, e il riquadro **Utenti con app potenzialmente dannose** e **Utenti contrassegnati**.

### <a name="user-status"></a>Stato utente
È possibile eseguire la ricerca di un singolo utente e controllare il relativo stato di conformità. Il riquadro **Segnalazione app** visualizza le informazioni seguenti per un utente selezionato:
- **Icona**: indica se lo stato dell'app è aggiornato.
- **Nome app**: nome dell'app.
- **Nome dispositivo**: dispositivi associati all'account dell'utente.
- **Tipo di dispositivo**: tipo di dispositivo o sistema operativo in cui è in esecuzione il dispositivo.
- **Criteri**: i criteri associati all'app.
- **Status** (Stato):
  - **Archiviazione eseguita**: i criteri sono stati distribuiti all'utente e l'app è stata usata almeno una volta nel contesto aziendale.
  - **Archiviazione non eseguita**: i criteri sono stati distribuiti all'utente, ma l'app non è stata usata nel contesto aziendale da quel momento.
- **Ultima sincronizzazione**: data dell'ultima sincronizzazione dell'app con Intune. 

>[!NOTE]
> La colonna "Ultima sincronizzazione" contiene lo stesso valore sia nel rapporto Stato dell'utente nella console sia nel [report esportabile con estensione csv](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities-to-csv) Criteri di protezione dell'app. La differenza è un leggero ritardo nella sincronizzazione tra i valori nei 2 rapporti. 
>
> L'ora a cui fa riferimento "Ultima sincronizzazione" è l'ultima volta in cui Intune ha rilevato l'istanza dell'app. L'istanza di un'app è una combinazione univoca di app + utente + dispositivo. Quando un utente finale avvia un'app, potrebbe comunicare o meno con il servizio Protezione app di Intune al momento dell'avvio, a seconda dell'ultima archiviazione eseguita. Questa documentazione spiega [i tempi degli intervalli tra tentativi per l'archiviazione dei criteri di protezione delle app](https://docs.microsoft.com/en-us/intune/app-protection-policy-delivery). Quindi, se un utente finale non ha usato l'app specifica nell'ultimo intervallo di archiviazione, in genere 30 minuti per l'utilizzo attivo, e avvia l'app, si verifica quanto segue:
>
> - Nel report esportabile con estensione csv Criteri di protezione dell'app sarà riportata l'ora più recente in un intervallo compreso tra 1 minuto (solitamente il tempo minimo) e 30 minuti (il contratto di servizio massimo disponibile con l'aggregazione SQL usata dai report di Intune).
> - Il report Stato dell'utente riporterà immediatamente l'ora più recente.
>
> Si consideri ad esempio un determinato utente finale con licenza che avvia un'app protetta alle 12:00:
> - Se si tratta di un primo accesso, significa che l'utente finale è stato disconnesso prima (utilizzo non attivo), vale a dire che non esiste una registrazione dell'istanza dell'app con Intune. Dopo aver eseguito l'accesso, verrà inviata una nuova registrazione dell'istanza dell'app e verrà immediatamente eseguita un'archiviazione in assenza di problemi di connettività, con gli stessi ritardi di tempo elencati in precedenza per le archiviazioni future. L'ora dell'ultima sincronizzazione sarà quindi 12:00 nel report Stato dell'utente e 12:01 (o 12:30 al più tardi) nel report Criteri di protezione dell'app. 
> - Se l'app è stata appena avviata, l'ora dell'ultima sincronizzazione segnalata dipenderà dall'ultima archiviazione eseguita.


Per visualizzare i report generati per un utente, seguire questa procedura:

1. Per selezionare un utente, scegliere il riquadro di riepilogo **Stato utente**.

    ![Schermata del riquadro Riepilogo della funzionalità di gestione di applicazioni mobili di Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. Nel riquadro **Segnalazione app** che viene aperto scegliere **Selezionare l'utente** per cercare un utente di Azure Active Directory.

    ![Schermata dell'opzione Selezionare l'utente nel riquadro Segnalazione app](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Selezionare un utente nell'elenco. È possibile visualizzare i dettagli dello stato di conformità per l'utente.

>[!NOTE]
> Se per l'utente cercato non è stato distribuito il criterio MAM, verrà visualizzato un messaggio che informa che all'utente non è applicato alcun criterio MAM.

### <a name="flagged-users"></a>Utenti contrassegnati
Nella visualizzazione dettagliata sono indicati il messaggio di errore, l'app a cui si è eseguito l'accesso quando si è verificato l'errore, la piattaforma del sistema operativo del dispositivo interessato e un timestamp. Gli utenti con dispositivi contrassegnati dal controllo dell'avvio condizionale "dell'attestazione del dispositivo SafetyNet" vengono indicati qui con il motivo segnalato da Google.

### <a name="users-with-potentially-harmful-apps"></a>Utenti con app potenzialmente dannose
La visualizzazione dettagliata contiene l'utente, l'ID del pacchetto dell'app, se l'app è abilitata per MAM, la categoria di minacce, la posta elettronica, il nome del dispositivo e un timestamp. Gli utenti con dispositivi contrassegnati dal controllo dell'avvio condizionale "Rendi obbligatoria l'analisi delle minacce nelle app" vengono indicati qui con la categoria di minaccia segnalata da Google. Se nel report sono elencate app che vengono distribuite tramite Intune, contattare lo sviluppatore dell'app e/o rimuovere l'app perché non sia assegnata agli utenti finali. 

## <a name="reporting-view"></a>Visualizzazione Rapporti

Sono visualizzati gli stessi report disponibili nella parte superiore del pannello **Stato protezione app**.

> [!NOTE]
> Intune offre campi aggiuntivi per i report relativi ai dispositivi, tra cui ID di registrazione app, produttore Android, modello e versione della patch di sicurezza, oltre al modello iOS. In Intune questi campi sono disponibili selezionando **App client** > **Stato protezione app** e scegliendo **Report sulla protezione dell'app: iOS, Android**. Inoltre, questi parametri consentiranno di configurare l'elenco **Consenti** per il produttore del dispositivo (Android), l'elenco **Consenti** per il modello di dispositivo (Android e iOS) e l'impostazione della versione minima della patch di sicurezza Android. 

Sono disponibili altri report relativi allo stato di conformità dei criteri MAM. Per visualizzare questi report, selezionare **App client** > **Stato protezione app** > **Report**. 

Il pannello **Report** fornisce diversi report in base all'utente e all'app, tra cui:


- **Report utenti**: questo report offre le stesse informazioni del report **Stato utente** descritte nella sezione [Visualizzazione dettagliata](app-protection-policies-monitor.md#detailed-view).

- **Report app**: oltre a selezionare la piattaforma e l'app, questo report offre due stati di protezione dell'app diversi tra cui è possibile scegliere prima di generare il report. Questi stati sono **Protetta** e **Non protetta**.

  - Stato utente per attività MAM gestita (**Protetta**): questo report descrive l'attività di ogni app MAM gestita per ogni utente. Visualizza tutte le app di destinazione dei criteri MAM per ogni utente e suddivide lo stato di ogni app archiviata con i criteri MAM o di destinazione di un criterio MAM ma mai archiviata.
  - Stato utente per attività MAM non gestita (**Non protetta**): questo report descrive l'attività delle app abilitate per MAM attualmente non gestite per ogni utente. Questa situazione può verificarsi per i motivi seguenti:
    - Le app sono usate da un utente o un'app che attualmente non è destinazione di un criterio MAM.
    - Tutte le app sono archiviate, ma non ricevono alcun criterio MAM.

    ![Screenshot del pannello Segnalazione app di un utente con i dettagli di tre app](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Report configurazione utente**: in base all'utente selezionato, questo report fornisce informazioni dettagliate sulle configurazioni di app ricevute dall'utente.
- **Report configurazione app**: in base alla piattaforma e all'app selezionate, questo report fornisce informazioni dettagliate sugli utenti che hanno ricevuto configurazioni per l'app selezionata.
- **Report di apprendimento app per Windows Information Protection**: questo report mostra le app che stanno tentando di oltrepassare i limiti dei criteri.
- **Apprendimento siti Web per Windows Information Protection**: questo report mostra i siti Web che stanno tentando di oltrepassare i limiti dei criteri.

## <a name="table-grouping"></a>Raggruppamento tabelle

Dopo la visualizzazione dei dati del **Report protezione app per l'utente**, è possibile aggregare i dati nel modo seguente:

- **Risultato convalida:** i dati visualizzati sono raggruppati in base allo stato di protezione dell'app, che può corrispondere a operazione completata, errore o avviso.
- **Nome app:** i dati visualizzati sono raggruppati in base all'app (identificata dal nome effettivo) con indicazione dello stato, che può corrispondere a operazione completata, errore o avviso.

## <a name="export-app-protection-activities-to-csv"></a>Esportare le attività di protezione delle app in formato CSV

È possibile esportare tutte le attività relative ai criteri di protezione delle app in un singolo file con estensione *csv*. Questa opzione può rivelarsi utile per analizzare tutti gli stati di protezione delle app segnalati dagli utenti.

Seguire questi passaggi per generare il report sulla protezione delle app:

1. Nel pannello Gestione di applicazioni mobili di Intune scegliere **Report protezione app**.

    ![Screenshot del collegamento per il download di Protezione app](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Scegliere **Sì** per salvare il report, quindi scegliere **Salva con nome** e selezionare la cartella in cui eseguire il salvataggio.

    ![Schermata della finestra di conferma Salva report](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Vedere anche
- [Gestire il trasferimento di dati tra app iOS](data-transfer-between-apps-manage-ios.md)
- [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](../fundamentals/end-user-mam-apps-android.md)
- [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](../fundamentals/end-user-mam-apps-ios.md)
