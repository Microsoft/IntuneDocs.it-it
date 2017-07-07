---
title: Registrazione diretta per i dispositivi iOS
description: "Usare lo strumento Apple Configurator per registrare direttamente i dispositivi iOS di proprietà dell'azienda con un criterio predefinito mediante connessione USB a un computer Mac."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9909e1dd4f9891a2efb47383242ed7765d3f0291
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="directly-enroll-ios-devices-by-using-apple-configurator"></a>Registrare direttamente i dispositivi iOS con Apple Configurator

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda con lo strumento [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) in esecuzione in un computer Mac. Questo processo non ripristina le impostazioni predefinite del dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi con **nessuna affinità utente** e richiede la connessione USB del dispositivo iOS a un computer Mac per configurare la registrazione aziendale.

Durante la registrazione diretta dei dispositivi iOS, è possibile registrare un dispositivo senza acquisire il numero di serie del dispositivo. È anche possibile denominare il dispositivo per scopi di identificazione prima che Intune acquisisca il nome del dispositivo durante la registrazione. L'app Portale aziendale non è supportata per i dispositivi con registrazione diretta. In queste istruzioni si presuppone l'uso di Apple Configurator 2.0 in un computer Mac.

>[!NOTE]
>Questo metodo di registrazione non può essere usato con il metodo del [manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

1.  Se non è disponibile, creare un profilo di registrazione dispositivi per i dispositivi iOS registrati tramite Apple Configurator. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate ai dispositivi.

    1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** &gt; **Registrazione di dispositivi aziendali** e scegliere **Aggiungi**.

        ![Pagina Crea profilo di registrazione dispositivi](../media/pol-sa-corp-enroll.png)

    2.  Immettere i dettagli per i profili di dispositivo:

        -   **Nome** : nome del profilo di registrazione dispositivi. Non è visibile agli utenti.

        -   **Descrizione**: descrizione del profilo di registrazione dispositivi. Non è visibile agli utenti.

        -   **Associazione utente**: specifica la modalità di registrazione dei dispositivi. Per la registrazione diretta selezionare **Nessuna affinità utente**.

        -   **Pre-assegnazione del gruppo di dispositivi**: tutti i dispositivi distribuiti con questo profilo appartengono inizialmente a questo gruppo. È possibile riassegnare i dispositivi dopo la registrazione.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    3.  Scegliere **Salva profilo** per aggiungere il profilo.

5.  Esportare un profilo come file con estensione mobileconfig per distribuire i dispositivi iOS:

    1.   Selezionare il profilo del dispositivo creato.

    2.   Scegliere **Esporta** sulla barra delle applicazioni.

    3.   Scegliere **Scarica il profilo** e salvare il file con estensione mobileconfig scaricato.

6.  Copiare il file con estensione mobileconfig scaricato in un computer Mac.
    > [!NOTE]
    > L'URL del profilo di registrazione è valido per due settimane quando viene esportato. Dopo due settimane è necessario esportare un nuovo URL del profilo di registrazione per registrare i dispositivi iOS con Assistente configurazione.

7.  Preparare il dispositivo con Apple Configurator. I dispositivi iOS vengono connessi al computer Mac e registrati per la gestione dei dispositivi mobili.

    1.  Aprire **Apple Configurator 2.0** in un computer Mac.

    2.  Connettere il dispositivo iOS al computer Mac con un cavo USB. Chiudere **Photos**, **iTunes** e altre app che vengono aperte quando viene rilevato il dispositivo.

    3.  In Apple Configurator selezionare il dispositivo iOS connesso e scegliere **Aggiungi**. Nell'elenco a discesa vengono visualizzate le opzioni che possono essere aggiunte al dispositivo. Scegliere **Profili**.

    4.  Usare il selettore file per selezionare il file con estensione mobileconfig esportato da Intune e scegliere **Aggiungi**. Il profilo viene aggiunto al dispositivo.  Se per il dispositivo è indicato **Supervisione non eseguita**, l'installazione richiederà accettazione sul dispositivo.

8.  È ora possibile installare il profilo nel dispositivo iOS. Il dispositivo deve aver già completato l'Assistente configurazione ed essere pronto per l'uso. Se la registrazione comporta distribuzioni dell'app, il dispositivo deve avere un ID Apple configurato perché le distribuzioni di app richiederanno l'accesso all'App Store con un ID Apple.

    1.  Sbloccare il dispositivo iOS.

    2.  Nella finestra di dialogo **Installa profilo** del **profilo di gestione** scegliere **Installa**.

    3.  Indicare **Device Passcode** o **Apple ID**, se necessario.

    4.  Accettare l'**avviso** e scegliere **Installa**.

    5.  Accettare l'**avviso remoto** e scegliere **Attendibile**.

    6.  Quando la casella **Profilo installato** conferma che il profilo è **Installato**, scegliere **Fine**.

9.  Nel dispositivo iOS aprire la finestra **Impostazioni** e passare a **Generale** &gt; **Gestione dei dispositivi** &gt; **Profilo di gestione**. Verificare che l'installazione del profilo è inclusa nell'elenco e controllare le restrizioni dei criteri iOS e le app installate. La visualizzazione delle restrizioni dei criteri e delle app nel dispositivo può impiegare fino a 10 minuti.

10.  Distribuire i dispositivi. Il dispositivo iOS viene ora registrato con Intune e gestito.