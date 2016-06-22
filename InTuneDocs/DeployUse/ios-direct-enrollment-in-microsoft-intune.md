---
# required metadata

title: Registrazione diretta per i dispositivi iOS | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: dagerrit
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrare direttamente i dispositivi iOS con Apple Configurator
Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda con lo strumento [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) in esecuzione in un computer Mac. Questo processo non ripristina le impostazioni predefinite del dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi con **Nessuna affinità utente** e richiede la connessione con USB del dispositivo iOS a un computer Mac per configurare la registrazione aziendale. L'app Portale aziendale non è supportata per i dispositivi con registrazione diretta. In queste istruzioni si presuppone l'uso di Apple Configurator 2.0 in un computer Mac.

1.  **Creare un profilo per i dispositivi**. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate ai dispositivi. Se non lo si è ancora fatto, creare un profilo di registrazione dispositivi per i dispositivi iOS registrati tramite Apple Configurator.

    #### Per creare un profilo

    1.  Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) fare clic su **Criteri** &gt; **Registrazione di dispositivi aziendali** e quindi scegliere **Aggiungi**.

        ![Pagina Crea profilo di registrazione dispositivi](../media/pol-sa-corp-enroll.png)

    2.  Immettere i dettagli per i profili di dispositivo:

        -   **Nome** : nome del profilo di registrazione dispositivi. Non è visibile agli utenti.

        -   **Descrizione**: descrizione del profilo di registrazione dispositivi. Non è visibile agli utenti.

        -   **Associazione utente** : consente di specificare la modalità di registrazione dei dispositivi. Per la registrazione diretta selezionare **Nessuna affinità utente**.

        -   **Pre-assegnazione al gruppo di dispositivi**: tutti i dispositivi distribuiti con questo profilo apparterranno inizialmente a questo gruppo. È possibile riassegnare i dispositivi dopo la registrazione.

    3.  Scegliere **Salva profilo** per aggiungere il profilo.

5.  **Esportare un profilo come file con estensione mobileconfig per la distribuzione nei dispositivi iOS**. Selezionare il profilo di dispositivo creato. Scegliere **Esporta** nella barra delle attività. Scegliere **Scarica il profilo** e salvare il file con estensione mobileconfig scaricato.

6.  **Trasferire il file**. Copiare il file con estensione mobileconfig scaricato in un computer Mac.
    > [!NOTE]
    > L'URL del profilo di registrazione è valido per due settimane quando viene esportato. Dopo due settimane è necessario esportare un nuovo URL del profilo di registrazione per registrare i dispositivi iOS con Assistente configurazione.
7.  **Preparare il dispositivo con Apple Configurator**. I dispositivi iOS vengono connessi al computer Mac e registrati per la gestione dei dispositivi mobili.

    1.  In un computer Mac avviare **Apple Configurator 2.0**.

    2.  Connettere il dispositivo iOS al computer Mac con un cavo USB. Chiudere **Photos**, **iTunes** e altre app che vengono aperte quando viene rilevato il dispositivo.

    3.  In Apple Configurator fare clic sul dispositivo iOS connesso e quindi scegliere **Add** (Aggiungi). Nell'elenco a discesa vengono visualizzate le opzioni che possono essere aggiunte al dispositivo. Scegliere **Profiles** (Profili).

    4.  Usare il selettore file per selezionare il file con estensione mobileconfig esportato da Intune e quindi scegliere **Add** (Aggiungi). Il profilo viene aggiunto al dispositivo.  Se per il dispositivo è indicato **Supervisione non eseguita**, l'installazione richiederà accettazione sul dispositivo.

8.  **Installare il profilo**. È ora possibile installare il profilo nel dispositivo iOS. Il dispositivo deve aver già completato l'Assistente configurazione ed essere pronto per l'uso.  Se la registrazione comporta distribuzioni dell'app, il dispositivo deve avere un ID Apple configurato perché le distribuzioni di app richiederanno l'accesso all'App Store con un ID Apple.

    ###### Completamento dell'accettazione del profilo per i dispositivi iOS non supervisionati

    1.  Sbloccare il dispositivo iOS.

    2.  Nella finestra di dialogo **Install profile** per **Management profile** toccare **Install**.

    3.  Indicare **Device Passcode** o **Apple ID**, se necessario.

    4.  Accettare l'**avviso** e toccare **Install**.

    5.  Accettare l'**avviso remoto** e toccare **Trust**.

    6.  Quando la casella **Profilo installato** conferma che il profilo è **Installato**, scegliere **Fine**.

9. **Verificare il profilo**
    Nel dispositivo iOS avviare **Impostazioni**, passare a **Generale** &gt; **Gestione dispositivo** &gt; **Management Profile** (Profilo di gestione)&gt;, confermare che l'installazione del profilo sia elencata, quindi verificare le restrizioni del criterio iOS e le app installate. La visualizzazione delle restrizioni dei criteri e delle app sul dispositivo può richiedere fino a 10 minuti.

10. **Distribuire i dispositivi** Il dispositivo iOS viene ora registrato con Intune e gestito.


### Vedere anche
[Prepararsi alla registrazione dei dispositivi](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=Jun16_HO3-->


