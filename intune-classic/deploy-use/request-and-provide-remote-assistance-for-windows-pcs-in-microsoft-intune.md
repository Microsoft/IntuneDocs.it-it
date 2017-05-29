---
title: Richiedere e fornire assistenza remota per i PC Windows | Documentazione Microsoft
description: Descrive i passaggi che l&quot;utente finale e l&quot;amministratore IT devono eseguire per fornire assistenza remota per i desktop Windows gestiti come PC e per l&quot;avvio remoto di un PC.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 416fb7a4f4be0450dcfbd02b1fdb51097553df0a
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>Richiedere e fornire assistenza remota per i PC Windows

Le informazioni fornite in questo argomento sono valide solo per i desktop Windows gestiti come PC usando il client software di Intune.

Intune può usare il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per consentire agli amministratori di fornire assistenza remota agli utenti che eseguono il client software di Intune. Quando un utente richiede assistenza a Microsoft Intune Center, si riceve un avviso, si può accettare la richiesta e quindi fornire assistenza. Questa funzionalità sostituisce la funzionalità Assistenza remota Windows presente in Intune.


## <a name="before-you-start"></a>Prima di iniziare

Prima di stabilire la connessione e rispondere alle richieste di assistenza remota, verificare che siano soddisfatti i prerequisiti seguenti:

- È necessario [aver ottenuto un account TeamViewer](https://login.teamviewer.com/LogOn#register) per accedere al sito Web TeamViewer.
- I PC Windows da amministrare devono essere [gestiti dal client del software Windows](manage-windows-pcs-with-microsoft-intune.md)
- È possibile amministrare tutti i sistemi operativi per PC Windows supportati da Intune.

## <a name="configure-the-teamviewer-connector"></a>Configurare TeamViewer Connector

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione**.
2. Nell'area di lavoro **Amministrazione** scegliere **TeamViewer**.
3. Nella pagina **TeamViewer**, in **TeamViewer Connector**, scegliere **Abilita**.
4. Nella finestra di dialogo **Abilita TeamViewer** visualizzare le condizioni di licenza, quindi scegliere **Accetta**. Se non si ha ancora una licenza di TeamViewer, scegliere **Acquista una licenza di TeamViewer**.
5. Dopo l'apertura della finestra di TeamViewer nel browser, accedere al sito con le credenziali di TeamViewer.
6. Nel sito di TeamViewer leggere e accettare le opzioni che consentono a Intune di connettersi a TeamViewer.
7. Nella console di Intune verificare che **TeamViewer Connector** sia visualizzato come **Abilitato**.


## <a name="open-a-remote-assistance-request-end-user"></a>Aprire una richiesta di assistenza remota (utente finale)

1. In un PC Windows client aprire **Microsoft Intune Center**.
2. In **Assistenza remota** scegliere **Richiedi assistenza remota**.
3. Dopo l'approvazione della richiesta (vedere più avanti) TeamViewer si apre all'interno del client. L'utente deve accettare tutti i messaggi che indicano che il Web browser sta tentando di aprire l'applicazione TeamViewer.
4. Viene visualizzato un messaggio che chiede l'autorizzazione a controllare il PC. Per continuare è necessario accettare questo messaggio.
5. Durante la sessione di assistenza remota l'utente vede una finestra che mostra la connessione in corso. Se si chiude questa finestra, la sessione remota termina.

## <a name="respond-to-a-remote-assistance-request"></a>Rispondere a una richiesta di assistenza remota

1. Quando un utente invia una richiesta di assistenza remota, è possibile visualizzare quest'ultima nell'area di lavoro **Avvisi**, in **Monitoraggio** > **Assistenza remota**. Ad esempio:
> ![Screenshot di una richiesta di assistenza remota](./media/team-viewer.png)

<br>Se una richiesta non riceve una risposta per più di 4 ore, viene rimossa.
2. Per accettare la richiesta, scegliere **Approva la richiesta e apri Assistenza remota**.
3. Nella finestra di dialogo **Nuova richiesta di Assistenza remota in sospeso** scegliere **Accettare la richiesta di Assistenza remota**. Se non è già installato, TeamViewer installerà tutte le app necessarie nel PC in uso.
4. TeamViewer quindi avvisa l'utente finale che si vuole assumere il controllo del PC. Dopo che l'utente ha accettato la richiesta, la finestra di TeamViewer viene aperta ed è possibile controllare il PC.

Durante una sessione di assistenza remota è possibile usare tutti i comandi di TeamViewer disponibili per controllare il computer remoto. Per informazioni su questi comandi, scaricare la [Guida sul controllo remoto](http://www.teamviewer.com/en/support/documents/) dal sito Web TeamViewer.

## <a name="close-the-remote-assistance-session"></a>Chiudere la sessione di Assistenza remota

Dal menu**Azioni** della finestra di **TeamViewer**, scegliere **Termina sessione**.

## <a name="remotely-restart-a-windows-pc"></a>Riavviare in remoto un PC Windows
Quando si fornisce supporto agli utenti riguardo a questi problemi, in alcune occasioni può essere necessario riavviarne i PC in remoto. Seguire questa procedura per riavviare in remoto un PC Windows.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il PC da riavviare.

2.  Selezionare uno o più PC e quindi scegliere **Attività remote** &gt; **Riavvia il computer**.

3.  Per visualizzare lo stato dell'attività, scegliere il collegamento **Attività remote** nell'angolo inferiore destro della pagina.

4.  Nella finestra di dialogo **Stato attività** , rivedere le attività remote correnti, il relativo stato, il nome del dispositivo e gli eventuali errori segnalati.

### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
