---
# required metadata

title: Ricevere notifiche tramite gli avvisi | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 396ea714-0433-4bd5-a934-8d0b477f28e4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ricevere notifiche tramite gli avvisi di Microsoft Intune
Gli avvisi informano l'utente delle attività in esecuzione in Microsoft Intune.

Ad esempio, gli avvisi possono comunicare all'utente gli eventi seguenti:

-   Un problema con Exchange Connector che interessa la gestione dei dispositivi mobili

-   Malware rilevato in un computer

-   Un conflitto rilevato tra due criteri di Intune


## Come funzionano gli avvisi
Gli avvisi vengono generati in base ai **tipi di avviso**, un set di regole preconfigurato e predefinito in Intune. Ad esempio, il tipo di avviso **La memoria cloud dispone di un massimo di 10% di spazio libero** informa l'utente che lo spazio disponibile per l'archiviazione delle app nel cloud è in esaurimento. È possibile abilitare o disabilitare e configurare le proprietà per ogni tipo di avviso. Ad esempio, usando il tipo di avviso precedente, è possibile configurare:

-   **Stato:** se il tipo di avviso è abilitato o disabilitato

-   **Gravità:** la gravità dell'avviso.


|Gravità|Dettagli|
|--------|-------|
    |![Avviso critico](../media/Critical-Alert.jpg)|Segnala un problema serio che richiede un'indagine tempestiva, ad esempio se in un computer viene rilevato un malware.|
    |![Avvertenza](../media/Warning-Alert.jpg)|Segnala un problema non grave, ma che potrebbe diventarlo se non viene risolto, ad esempio aggiornamenti della sicurezza in attesa di installazione.|
    |![Avviso informativo](../media/Informational-Alert.jpg)|Fornisce informazioni non essenziali per il funzionamento, ad esempio la disponibilità di una nuova versione di Exchange Connector.|

Altri tipi di avviso possono contenere elementi diversi che è possibile configurare, ad esempio la percentuale di dispositivi che deve essere interessata da un problema prima che venga generato un avviso.

**Quando vengono soddisfatti i criteri per un tipo di avviso, viene generato un avviso visualizzato nella console di amministrazione di Intune.**

È anche possibile configurare Intune in modo che invii notifiche tramite posta elettronica quando viene generato un avviso.

## Configurazione degli avvisi
Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione** &gt; **Avvisi e notifiche**, quindi scegliere una delle attività di configurazione seguenti:

|Attività|Descrizione|
|--------|---------------|
|**Tipi di avviso**|Scegliere il tipo di avviso da configurare, quindi eseguire una delle due procedure seguenti:<br /><br />Scegliere **Configura**. Nella finestra di dialogo **Configura tipo avviso** configurare le impostazioni e scegliere **OK**.<br /><br />**Abilitare** o **disabilitare** l'avviso.<br /><br />Espandere il nodo **Tipi di avviso** e scegliere una categoria per visualizzare solo i tipi di avviso della categoria selezionata.|
|**Destinatari**|Scegliere **Aggiungi** per aggiungere un nuovo indirizzo di posta elettronica che riceverà le notifiche tramite posta elettronica configurate.<br /><br />È anche possibile **modificare** o **eliminare** i destinatari esistenti.<br /><br />Per ricevere le notifiche, l'indirizzo di posta elettronica deve essere aggiunto anche come destinatario in **Regole di notifica**.|
|**Regole di notifica**|Configura le regole che definiscono gli utenti ai quali verrà inviato un avviso tramite posta elettronica. È possibile:<br /><br />**Scegliere una regole esistente**: scegliere una regola, quindi scegliere **Seleziona destinatari**. È quindi possibile selezionare tutti i destinatari che riceveranno un messaggio di posta elettronica quando viene generato un avviso che soddisfa questa regola.<br /><br />**Creare una nuova regola**: immettere un nome per la regola, selezionare le categorie di avviso e la gravità dell'avviso da applicare alle regole, selezionare i gruppi di dispositivi a cui viene applicata la regola e selezionare gli utenti che riceveranno un messaggio di posta elettronica quando viene generato un avviso.<br /><br />È anche possibile **abilitare**, **disabilitare**, **modificare**o **eliminare** una regola esistente.|

## Utilizzo degli avvisi
Usare le opzioni seguenti per gestire gli avvisi dalla console di amministrazione di Intune.

|Opzione|Descrizione|
|----------|---------------|
|**Visualizzare gli avvisi attivi**|Scegliere una delle opzioni seguenti:<br /><br />**Visualizzare un riepilogo degli avvisi**: nell'area di lavoro **Dashboard** gli errori principali vengono visualizzati nel riquadro Avvisi. Scegliere il riquadro per visualizzare altre informazioni.<br /><br />Inoltre, il riepilogo degli avvisi può essere visualizzato nella pagina **Panoramica** dell'area di lavoro **Avvisi** .<br /><br />**Visualizzare tutti gli avvisi**: nell'area di lavoro **Avvisi** fare clic su **Tutti gli avvisi**.|
|**Visualizzare le notifiche**|Scegliere una delle opzioni seguenti:<br /><br />Nell'area di lavoro **Dashboard** scegliere **Notifiche**.<br /><br />Nell'area di lavoro **Avvisi** scegliere**Tutti gli avvisi** &gt; **Notifiche**.|
|**Chiudere un avviso**|Nell'elenco degli avvisi scegliere l'avviso da chiudere, quindi scegliere **Chiudi avviso**.<br /><br />Gli avvisi chiusi vengono eliminati definitivamente dopo 90 giorni.|
|**Riattivare un avviso chiuso**|Nell'elenco degli avvisi impostare l'elenco a discesa **Filtri** su **Chiuso**.<br /><br />Nell'elenco degli avvisi chiusi selezionare l'avviso da riattivare, quindi scegliere **Riattiva avviso**.|
Gli avvisi di Intune restano attivi finché:

-   Il problema per il quale è stato generato l'avviso non viene risolto

-   L'avviso non viene chiuso manualmente

-   Non trascorrono 45 giorni dalla generazione dell'avviso

> [!TIP] Se lo stesso avviso viene generato da dispositivi che eseguono sistemi operativi diversi, potrebbero essere visualizzate più versioni dello stesso avviso nell'elenco degli avvisi.

### Vedere anche
[Monitoraggio e report con Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)


<!--HONumber=May16_HO5-->


