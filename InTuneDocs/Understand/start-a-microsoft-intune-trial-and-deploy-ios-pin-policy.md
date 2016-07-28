---
title: Avviare una versione di valutazione di Intune e distribuire criteri PIN di iOS | Microsoft Intune
description: Distribuire i criteri PIN di iOS in Intune
keywords: 
author: Staciebarker
manager: arob98
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 06cb9a73-0f17-44b3-b334-86c98020316e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: b2b24492693b61a544a4adc3e878b8b212d15a21


---

# Avviare una versione di valutazione di Microsoft Intune e distribuire criteri PIN di iOS
Queste istruzioni dettagliate permettono di installare una versione di valutazione di Intune e configurare un criterio PIN per i dispositivi iOS. Per un elenco di altre comuni attività di valutazione di Intune da provare, vedere [Attività comuni di valutazione di Intune](common-microsoft-intune-evaluation-tasks.md).



## Esaminare i prerequisiti per questa attività

-   PC Windows con Internet Explorer - per l'esecuzione di attività amministrative

-   Dispositivo iOS 7.1 o versione successiva per il test di convalida dei criteri utente

-   Numero di telefono per autenticarsi durante l'iscrizione alla versione di valutazione

## Creare un account di valutazione gratuito di Intune
> [!NOTE]
> Se si ha già una sottoscrizione di Intune, ignorare questa sezione e passare a quella successiva.

1.  Usando un PC Windows, fare clic con il pulsante destro del mouse su **Internet Explorer** (IE) e selezionare **InPrivate Browsing**.

    ![Avviare InPrivate Browsing](../media/30-day-trial-walkthrus/30day-start-trial-1-InPrivate.png)

2.  Passare al [portale di iscrizione a Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1), fornire le informazioni richieste e fare clic su **Avanti**.

    ![Registrarsi per un account](../media/30-day-trial-walkthrus/30day-start-trial-2-abt-you.png)

3.  Immettere un ID utente e una password per l'account amministratore e fare clic su **Avanti**. Si userà questo ID per accedere al portale di Intune per eseguire le attività di amministrazione.

    ![Creare un ID](../media/30-day-trial-walkthrus/30day-start-trial-3-createID.png)

4.  Immettere il proprio numero di telefono cellulare e fare clic su **SMS** per convalidare il numero.

    ![Convalidare i dettagli](../media/30-day-trial-walkthrus/30day-start-trial-4-textme.png)

5.  Salvare le informazioni visualizzate sullo schermo e quindi fare clic su **È possibile continuare**.

    ![Continuare](../media/30-day-trial-walkthrus/30day-start-trial-5-ReadyToGo.png)

## Creare un utente test

1.  Usando un PC Windows, fare clic su **Start** per passare alla pagina di gestione degli utenti.

    ![Passare alla pagina di gestione utenti](../media/30-day-trial-walkthrus/30day-crt-user-6-click-start.png)

2.  Fare clic sul pulsante **+** per aggiungere un utente.

    ![Aggiunta di un utente](../media/30-day-trial-walkthrus/30day-crt-user-7-click-plus.png)

3.  Nella pagina di **creazione nuovo account utente**:

    1.  Fornire le informazioni sull'utente test.

    2.  Selezionare l'opzione che richiede di **digitare la password**.

    3.  Deselezionare la casella di controllo **Chiedere all'utente di cambiare la password al primo accesso**.

    4.  Scegliere **Crea**.

    ![Creare un nuovo account utente](../media/30-day-trial-walkthrus/30day-crt-user-8-add-user-info.png)

4.  Nella pagina di conferma della creazione utente, fare clic su **Chiudi**.

    ![Pagina di conferma della creazione utente](../media/30-day-trial-walkthrus/30day-crt-user-9-close-confirm.png)

5.  Fare clic sul pulsante **Aggiorna** per visualizzare l'utente test creato.

    ![Conferma dell'account](../media/30-day-trial-walkthrus/30day-crt-user-10-refresh-user.png)

## Configurare un criterio PIN di iOS per l'utente test

1.  Usando un PC Windows, impostare l'autorità MDM su Intune:

    1.  Passare alla [console di gestione Intune](http://manage.microsoft.com/), accedere con l'account amministratore e fare clic su **Inizia a gestire i dispositivi mobili**. Viene aperta la pagina Autorità di gestione del dispositivo mobile.

        ![Introduzione alla console di Intune](../media/30-day-trial-walkthrus/30day-cfg-pol-11-start-mg-mobl-dev.png)

    2.  Fare clic sul collegamento **Imposta autorità di gestione del dispositivo mobile**.

        ![Impostare l'autorità di gestione dei dispositivi mobili](../media/30-day-trial-walkthrus/30day-cfg-pol-12-link-set-mdm.png)

2.  Abilitare i dispositivi iOS alla registrazione. Questo processo imposta un certificato attendibile tra il servizio di notifica Push di Apple (APNs) e la sottoscrizione di Intune.

    1.  Fare clic su **Abilita la piattaforma iOS e Mac OS X**.

        ![Abilitare la registrazione iOS e Mac OS X](../media/30-day-trial-walkthrus/30day-cfg-pol-13-enbl-ios-plat.png)

    2.  Fare clic su **Scarica richiesta di certificato APNs**.

        ![Scaricare il certificato APN](../media/30-day-trial-walkthrus/30day-cfg-pol-14-dwnld-cert-reqst.png)

    3.  Specificare un nome e un percorso per la richiesta di firma del certificato (CSR, Certificate Signing Request) e quindi fare clic su **Salva**. Questo file contiene la chiave pubblica che corrisponde a una chiave privata usata dalla sottoscrizione a Intune.

        ![Specificare una richiesta di firma del certificato](../media/30-day-trial-walkthrus/30day-cfg-pol-15-cert-name-loc.png)

    4.  Fare clic su **Portale Apple Push Certificates** per aprire una nuova scheda.

        ![Passare alla pagina dei certificati APN](../media/30-day-trial-walkthrus/30day-cfg-pol-16-cert-portl-link.png)

    5.  Immettere l'ID Apple e la password, quindi fare clic su **Accedi**. Questo ID può essere quello usato nel dispositivo iOS per scaricare le app dall'App Store di iOS.

        ![Accedere al portale Apple Push Certificates](../media/30-day-trial-walkthrus/30day-cfg-pol-17-id-passw-signin.png)

    6.  Fare clic su **Create a Certificate**.

        ![Creare un certificato APN](../media/30-day-trial-walkthrus/30day-cfg-pol-18-create-cert.png)

    7.  Leggere le Condizioni per l'utilizzo di Apple, selezionare la casella di controllo e fare clic su **Accept**.

        ![Accettare le condizioni](../media/30-day-trial-walkthrus/30day-cfg-pol-19-TOU.png)

    8.  Fare clic su **Browse**.

        ![Individuare la posizione in cui è stato salvato il certificato](../media/30-day-trial-walkthrus/30day-cfg-pol-20-browse.png)

    9. Selezionare il file CSR salvato in precedenza e fare clic su **Open**.

        ![Aprire il certificato](../media/30-day-trial-walkthrus/30day-cfg-pol-21-CSRfile-open.png)

    10. Fare clic sul pulsante **Upload**.

        ![Caricare il certificato](../media/30-day-trial-walkthrus/30day-cfg-pol-22-upld-reqst.png)

    11. Quando viene richiesto di sovrascrivere un file JSON, fare clic su **Save**.

        ![Salvare il file con estensione json](../media/30-day-trial-walkthrus/30day-cfg-pol-23-json-saveas.png)

    12. Specificare un percorso per il file JSON e fare clic su **Save**.

        ![Specificare dove salvare il file con estensione json](../media/30-day-trial-walkthrus/30day-cfg-pol-24-json-save-loc.png)

        Se la pagina non reindirizza automaticamente dopo alcuni secondi, fare clic su **Cancel**.

        ![Annullare se la pagina non viene reindirizzata](../media/30-day-trial-walkthrus/30day-cfg-pol-25-json-pg-cancel.png)

    13. Per recuperare il file del certificato appena creato, fare clic su **Download**.

        ![Scaricare il certificato](../media/30-day-trial-walkthrus/30day-cfg-pol-26-dwnld-retrv-cert.png)

    14. Quando viene richiesto di scaricare un file PEM, fare clic su **Save**.

        ![Scaricare il file con estensione pem](../media/30-day-trial-walkthrus/30day-cfg-pol-27-pem-saveas.png)

    15. Specificare un percorso per il file PEM e fare clic su **Save**.

        ![Salvare il file con estensione pem](../media/30-day-trial-walkthrus/30day-cfg-pol-28-pem-save-loc.png)

    16. Tornare alla scheda della Console di gestione di Intune e fare clic sui **Carica il certificato APNs**.

        ![Caricare il certificato APN](../media/30-day-trial-walkthrus/30day-cfg-pol-29-upld-cert.png)

    17. Immettere l'ID Apple e fare clic su **Sfoglia**.

        ![Immettere l'ID Apple](../media/30-day-trial-walkthrus/30day-cfg-pol-30-app-id-browse.png)

    18. Selezionare il file PEM appena salvato e fare clic su **Apri**.

        ![Aprire il file con estensione pem](../media/30-day-trial-walkthrus/30day-cfg-pol-31-sel-pem-open.png)

    19. Fare clic su **Carica**.

        ![Caricare il file con estensione pem](../media/30-day-trial-walkthrus/30day-cfg-pol-32-pem-upload.png)

        Il certificato APNs è ora configurato.

        ![Il certificato APN è ora configurato](../media/30-day-trial-walkthrus/30day-cfg-pol-33-apns-confgd.png)

3.  Creare un gruppo di utenti test per la definizione dei criteri:

    1.  Nel riquadro di sinistra fare clic su **Gruppi**.

        ![Aprire Gruppi](../media/30-day-trial-walkthrus/30day-cfg-pol-34-clk-groups.png)

    2.  All'estrema destra, fare clic su **Crea gruppo**.

        ![Creare un gruppo](../media/30-day-trial-walkthrus/30day-cfg-pol-35-crt-group.png)

    3.  Specificare un nome di gruppo, selezionare **Tutti gli utenti** come gruppo padre e fare clic su **Avanti**.

        ![Selezionare Tutti gli utenti come gruppo padre](../media/30-day-trial-walkthrus/30day-cfg-pol-36-name-group.png)

    4.  Nel campo **Iniziare l'appartenenza al gruppo con**, selezionare **Tutti gli utenti del gruppo padre** e fare clic su **Fine**.

        ![Iniziare l'appartenenza al gruppo con il gruppo padre](../media/30-day-trial-walkthrus/30day-cfg-pol-37-all-users-group.png)

4.  Creare un criterio PIN iOS e definire la destinazione per il gruppo di utenti test:

    1.  Nel riquadro di sinistra fare clic su **Criteri**.

        ![Aprire l'area di lavoro Criteri](../media/30-day-trial-walkthrus/30day-cfg-pol-38-clk-policy.png)

    2.  All'estrema destra, fare clic su **Aggiungi criterio**.

        ![Aggiungere un criterio](../media/30-day-trial-walkthrus/30day-cfg-pol-39-add-policy.png)

    3.  Espandere il nodo iOS, selezionare la riga **Configurazione generale** e fare clic su **Crea criterio**.

        ![Creare criteri di configurazione generale iOS](../media/30-day-trial-walkthrus/30day-cfg-pol-40-gen_cfg_pol.png)

    4.  Digitare un nome per il criterio, attivare l'opzione **Richiedi una password per sbloccare i dispositivi mobili** e impostare la **Lunghezza minima password** su **4**.

        ![Configurare le impostazioni della password](../media/30-day-trial-walkthrus/30day-cfg-pol-41-name-policy.png)

    5.  Fare clic su **Sì** per distribuire il criterio.

        ![Distribuire i criteri](../media/30-day-trial-walkthrus/30day-cfg-pol-42-yes-deploy-pol.png)

    6.  Fare clic sul gruppo utente creato in precedenza, fare clic su **Aggiungi** e fare clic su **OK**.

        ![Selezionare il gruppo per i criteri](../media/30-day-trial-walkthrus/30day-cfg-pol-43-add-pol-to-grp.png)

        È ora disponibile un criterio PIN iOS che fa riferimento al gruppo di utenti test.

        ![Installazione dei criteri completata](../media/30-day-trial-walkthrus/30day-cfg-pol-44-policy-applied.png)

## Verificare che i criteri vengano applicati in un dispositivo iOS

1.  In un iPad, avviare l'App Store di iOS, installare l'app **Portale aziendale di Microsoft Intune** gratuita e aprirla.

    ![Installare il portale aziendale](../media/30-day-trial-walkthrus/30day-cfg-pol-45-cportal-installed.png)

2.  Immettere il nome e la password dell'account utente test e toccare **Accedi**.

    ![Immettere le credenziali](../media/30-day-trial-walkthrus/30day-cfg-pol-46-cportal-signin.png)

3.  Toccare **Registra** per iniziare a registrare il dispositivo in Intune.

    ![Avviare la registrazione](../media/30-day-trial-walkthrus/30day-cfg-pol-47-tap-enroll.jpg)

4.  Nella schermata **Installa profilo** toccare **Installa**.

    ![Installare un profilo](../media/30-day-trial-walkthrus/30day-cfg-pol-48-profile-install-1.jpg)

5.  Nella finestra di dialogo **Installa profilo** toccare **Installa**.

    ![Continuare l'installazione del profilo](../media/30-day-trial-walkthrus/30day-cfg-pol-49-profile-install-2.jpg)

6.  Nella schermata **Avviso** toccare **Installa**.

    ![Accettare il messaggio di avviso](../media/30-day-trial-walkthrus/30day-cfg-pol-50-warning-install-3.png)

7.  Nella finestra di dialogo **Gestione remota** toccare **Attendibilità**.

    ![Attendibilità gestione remota](../media/30-day-trial-walkthrus/30day-cfg-pol-51-remt-mgmt-trust.jpg)

8.  Al termine dell'installazione del profilo di gestione, toccare **Fine**. La registrazione è stata completata.

    ![Registrazione completata](../media/30-day-trial-walkthrus/30day-cfg-pol-52-profile-done.jpg)

9. Una volta completata la registrazione, toccare **OK** e quindi chiudere l'app Portale aziendale.

    ![Toccare OK per chiudere l'app Portale aziendale](../media/30-day-trial-walkthrus/30day-cfg-pol-53-devc-enrolled-ok.png)

10. Quando viene richiesto di configurare un passcode, toccare **Continua**.

    ![Accettare il prompt per configurare il passcode](../media/30-day-trial-walkthrus/30day-cfg-pol-54-passcode-req-cont.png)

11. Immettere il passcode, toccare **Continua**, immettere di nuovo il passcode e toccare **Salva**.

    ![Fornire un passcode](../media/30-day-trial-walkthrus/30day-cfg-pol-55-passcode-enter.jpg)

12. Premere il pulsante di alimentazione per bloccare l'iPad, quindi farlo scorrere per sbloccarlo: a questo punto sarà necessario immettere il passcode per sbloccare il dispositivo.

### Vedere anche
[Guida alla valutazione di Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


