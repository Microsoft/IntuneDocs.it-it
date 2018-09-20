---
title: Risolvere i problemi di installazione delle app
titlesuffix: Microsoft Intune
description: Usare il riquadro Risoluzione dei problemi di Microsoft Intune per facilitare la risoluzione dei problemi di installazione delle app.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: 80b6828f4768ff79f86532ef0d39ff2100b0ef25
ms.sourcegitcommit: 11cad61c565c474a8d653181675cc1109d562626
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43241712"
---
# <a name="troubleshoot-app-installation-issues"></a>Risolvere i problemi di installazione delle app

Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. Microsoft Intune offre dettagli sugli errori di installazione delle app che consentono agli operatori di help desk e agli amministratori di Intune di visualizzare informazioni sulle app in per rispondere alle richieste degli utenti. Il riquadro di risoluzione dei problemi all'interno di Intune fornisce dettagli sull'errore, incluse informazioni dettagliate sulle app gestite nel dispositivo dell'utente. Per ogni singolo dispositivo sono disponibili informazioni dettagliate sul ciclo di vita completo di un'app nel riquadro **App gestite**. È possibile visualizzare i problemi di installazione, ad esempio quando l'app è stato creata, modificata, assegnata e recapitata a un dispositivo. 

## <a name="to-review-app-troubleshooting-details"></a>Per esaminare le informazioni dettagliate per la risoluzione dei problemi delle app

Intune offre informazioni dettagliate per la risoluzione dei problemi delle app in base alle app installate nel dispositivo di un utente specifico.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Risoluzione dei problemi**.
4. Fare clic su **Seleziona utente** per selezionare un utente per risolvere i problemi. Verrà visualizzato il riquadro **Seleziona utenti**.
5. Selezionare un utente digitando il nome o l'indirizzo di posta elettronica. Fare clic su **Seleziona** nella parte inferiore del riquadro. Le informazioni di risoluzione dei problemi per l'utente vengono visualizzate nel riquadro **Risoluzione dei problemi**. 
6. Selezionare il dispositivo per cui si vuole eseguire la risoluzione dei problemi nell'elenco **Dispositivi**.
    ![Riquadro Risoluzione dei problemi di Intune.](media/troubleshoot-app-install-01.png)
7. Selezionare **App gestite** nel riquadro del dispositivo selezionato. Verrà visualizzato un elenco delle app gestite.
    ![Dettagli di un dispositivo specifico gestito da Intune.](media/troubleshoot-app-install-02.png)
8. Selezionare un'app nell'elenco per cui **Stato dell'installazione** indica un errore.
    ![App selezionata che mostra informazioni dettagliate sull'errore di installazione.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > La stessa app potrebbe essere assegnata a più gruppi, ma con diverse azioni previste (finalità) per l'app. Ad esempio, la finalità risolta per un'app indicherà **esclusa** se l'app viene esclusa per un utente durante l'assegnazione di app. Per altre informazioni, vedere [Modalità di risoluzione dei conflitti tra finalità di app](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Se si verifica un errore di installazione per un'app obbligatoria, l'utente o il supporto tecnico sarà in grado di sincronizzare il dispositivo e ritentare l'installazione dell'app.

I dettagli dell'errore di installazione dell'app indicheranno il problema. È possibile usare questi dettagli per determinare l'azione migliore da intraprendere per risolvere il problema. Per altre informazioni sulla risoluzione dei problemi di installazione delle app, vedere [Error Codes For Troubleshooting App Installation Issues](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues) (Codici di errore per la risoluzione dei problemi di installazione delle app).

> [!Note]  
> È anche possibile accedere al riquadro **Risoluzione dei problemi** digitando nel browser l'indirizzo seguente: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="app-installation-errors"></a>Errori di installazione delle app

I seguenti messaggi di errore e descrizioni contengono dettagli sugli errori di installazione di Android e iOS. 

### <a name="android-errors"></a>Errori di Android

|    Messaggio di errore/codice    |    Descrizione    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Non è stato possibile installare l'app. (0xC7D14FB5)    |    Questo messaggio di errore viene visualizzato quando Intune non è in grado di determinare la causa radice dell'errore di installazione dell'app per Android. Non si ricevono informazioni da Android quando si verifica l'errore.       Questo errore viene restituito quando il download del pacchetto dell'applicazione Android (APK) viene completato, ma l'installazione dell'app non riesce. Questo errore spesso può verificarsi a causa di un file APK non valido che non può essere installato nel dispositivo. Una causa possibile può essere il fatto che Google Play Protect blocca l'installazione dell'app come misura di sicurezza. L'errore si può verificare anche quando un dispositivo non supporta l'app, ad esempio, se l'app richiede l'API versione 21 o successive e il dispositivo attualmente usa la versione 19 dell'API.         Intune restituisce questo errore per i dispositivi DA e KNOX e benché gli utenti possano ricevere una notifica che indica di fare clic per riprovare, se si verifica un problema con il file APK, l'errore non continuerà a ripetersi. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata.        |
|    L'installazione dell'app è stata annullata perché il file di installazione (APK) è stato eliminato dopo il download, ma prima dell'installazione. (0xC7D14FBA)    |    Il download del file APK è stato completato, ma il file è stato rimosso dal dispositivo prima che l'utente installasse l'app. Questo problema può verificarsi se trascorre molto tempo tra il download e l'installazione. Ad esempio, l'utente ha annullato l'installazione originale, ha atteso e poi ha fatto clic sulla notifica per riprovare.         Questo messaggio di errore viene restituito solo per gli scenari DA. Gli scenari KNOX possono essere eseguiti in modo invisibile all'utente. Viene presentata una notifica che indica di riprovare in modo che l'utente possa accettare anziché annullare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata.    |
|    L'installazione dell'app è stata annullata perché il processo è stato riavviato durante l'installazione. (0xC7D14FBB)    |    Il dispositivo è stato riavviato durante il processo di installazione del pacchetto dell'applicazione Android, quindi l'installazione è stata annullata.        Questo messaggio di errore viene restituito per i dispositivi DA e KNOX. Intune visualizza una notifica per invitare gli utenti a fare clic per riprovare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata.    |
|    Applicazione non rilevata dopo il completamento dell'installazione. (0x87D1041C)    |    L'utente ha disinstallato l'app in modo esplicito. Questo errore non viene restituito dal client. Si tratta di un errore generato quando l'app è già installata ma viene successivamente disinstallata dall'utente. Questo errore dovrebbe verificarsi solo per le applicazioni obbligatorie. Gli utenti possono disinstallare le app non obbligatorie. Questo errore si può verificare solo in DA. KNOX blocca la disinstallazione delle app gestite.       Con la sincronizzazione successiva la notifica verrà ripubblicata nel dispositivo per indicare all'utente di eseguire l'installazione.   L'utente può ignorare la notifica. Questo errore continuerà a essere segnalato finché l'utente non installa l'app.    |
|    Non è stato possibile eseguire il download a causa di un errore sconosciuto. (0xC7D14FB2)    |    Questo errore si verifica quando il download ha esito negativo. In genere, questo errore può verificarsi a causa di problemi di Wi-Fi o connessioni lente.       Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente. Intune visualizza una notifica per invitare gli utenti a fare clic per riprovare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata.    |
|    Non è stato possibile eseguire il download a causa di un errore sconosciuto. Il criterio verrà ritentato alla successiva sincronizzazione del dispositivo. (0xC7D15078)    |    Questo errore si verifica quando il download ha esito negativo. In genere, questo errore può verificarsi a causa di problemi di Wi-Fi o connessioni lente.       Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente.    |
|    L'utente finale ha annullato l'installazione dell'app. (0xC7D14FB1)    |    L'utente ha disinstallato l'app in modo esplicito. Questo errore viene restituito quando l'attività di installazione del sistema operativo Android viene annullata dall'utente. L'utente ha premuto il pulsante Annulla quando era visualizzata la richiesta di installazione del sistema operativo oppure ha fatto clic in un altro punto.        Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente. Intune visualizza una notifica per invitare gli utenti a fare clic per riprovare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata.    |
|    Il processo di download di file è stato arrestato in modo imprevisto. (0xC7D15015)    |    Il sistema operativo ha arrestato il processo di download prima del completamento. Questo errore può verificarsi quando il dispositivo ha la batteria in esaurimento o il download richiede troppo tempo.       Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente. Intune visualizza una notifica per invitare gli utenti a fare clic per riprovare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata.    |
|    Il servizio di download di file è stato arrestato in modo imprevisto. Il criterio verrà ritentato alla successiva sincronizzazione del dispositivo. (0xC7D1507C)    |    Il sistema operativo ha arrestato il processo di download prima del completamento. Questo errore può verificarsi quando il dispositivo ha la batteria in esaurimento o il download richiede troppo tempo.       Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente.    |

### <a name="ios-errors"></a>Errori iOS

|    Messaggio di errore/codice    |    Descrizione    |
|:----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    (0x87D12906)    |    L'agente MDM di Apple ha segnalato che il comando di installazione ha avuto esito negativo.        |
|    (0x87D1313C)    |    Si è persa la connessione di rete mentre l'URL aggiornato del servizio di download veniva inviato al dispositivo. In particolare, non è stato possibile trovare un server con il nome host specificato.    |
|    Il dispositivo iOS è attualmente occupato. (0x87D11388)    |    Il dispositivo iOS era occupato e ciò ha provocato un errore.    |
|    Installazione app non riuscita. (0x87D13B64)    |    Si è verificato un errore di installazione dell'app. Sono necessari i log XCODE per risolvere questo errore.    |
|    L'app è gestita, ma è scaduta o è stata rimossa dall'utente. (0x87D13B66)    |    L'utente ha disinstallato l'app in modo esplicito. Oppure, l'app è scaduta ma non è stato possibile scaricarla o il rilevamento dell'app non corrisponde alla risposta del dispositivo.   Inoltre, questo errore può verificarsi per un bug della piattaforma iOS 9.2.2.    |
|    L'app viene pianificata per l'installazione, ma è necessario un codice di riscatto per completare la transazione.   (0x87D13B60)    |    Questo errore si verifica in genere con le app di iOS Store a pagamento.     |
|    Applicazione non rilevata dopo il completamento dell'installazione. (0x87D1041C)    |    Il processo di rilevamento dell'app non corrisponde alla risposta del dispositivo.    |
|    L'utente ha rifiutato l'offerta di installazione dell'app. (0x87D13B62)    |    Durante l'installazione iniziale dell'app, l'utente ha fatto clic su Annulla.    |
|    L'utente ha rifiutato l'offerta di aggiornamento dell'app. (0x87D13B63)    |    L'utente finale ha fatto clic su Annulla durante il processo di aggiornamento.     |
|    Errore sconosciuto (0x87D103E8)    |    Si è verificato un errore sconosciuto durante l'installazione dell'app. Si tratta dell'errore che si verifica quando l'altro errore non si è verificato.    |


## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sulla risoluzione dei problemi di Intune, vedere [Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti aziendali](help-desk-operators.md). 
- È possibile ottenere informazioni sui problemi noti in Microsoft Intune. Per altre informazioni, vedere [Problemi noti in Microsoft Intune](known-issues.md).
- È possibile ottenere altre informazioni. Vedere [Come ottenere supporto per Microsoft Intune](get-support.md).
