---
# required metadata

title: Gestione del servizio DEP di Apple per i dispositivi iOS con Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrare i dispositivi IOS di proprietà dell'azienda usando il programma di registrazione dispositivi (DEP)
Microsoft Intune può distribuire un profilo di registrazione che registra in modalità wireless i dispositivi iOS acquistati tramite il programma di registrazione dispositivi (DEP). Il pacchetto di registrazione può includere opzioni di Assistente configurazione per il dispositivo. La registrazione dei dispositivi registrati tramite DEP non può essere annullata dagli utenti.

## Gestione del servizio DEP di Apple per i dispositivi iOS con Microsoft Intune
Per gestire i dispositivi iOS di proprietà dell'azienda con il programma di registrazione dispositivi (DEP) di Apple, le organizzazioni devono partecipare al programma DEP di Apple e acquisire i dispositivi attraverso il programma. I dettagli del processo sono disponibili in:  [https://deploy.apple.com](https://deploy.apple.com) I vantaggi del programma includono la configurazione dei dispositivi senza intervento dell'utente e senza dover connettere tramite USB ogni dispositivo a un computer.

Per registrare i dispositivi iOS di proprietà dell'azienda con DEP, è necessario un token DEP di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi di proprietà dell'azienda che partecipano a DEP. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

1.  **Iniziare a gestire dispositivi iOS con Microsoft Intune**
    Per poter registrare i dispositivi del programma di registrazione dispositivi (DEP) per iOS è necessario abilitare la gestione di iOS per Intune.

2.  **Ottenere una chiave di crittografia**
    Gli utenti amministratori possono aprire la [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **iOS** &gt; **Programma di registrazione dispositivi**, quindi fare clic su **Scarica chiave di crittografia**. Salvare il file della chiave di crittografia (con estensione pem) localmente. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.

      ![Aggiornare un token del programma di registrazione dispositivi](../media/dev-sa-ios-dep.png)

3.  **Ottenere un token del programma di registrazione dispositivi**
    Accedere al [portale del programma di registrazione dispositivi](https://deploy.apple.com) (https://deploy.apple.com) e accedere con l'ID Apple aziendale. Questo ID Apple dovrà essere usato in futuro per rinnovare il token DEP.

    1.  Nel [portale del programma di registrazione dispositivi](https://deploy.apple.com), fare clic su **Programma di registrazione dispositivi** &gt; **Gestisci server**, quindi fare clic su **Aggiungi server MDM**..

    2.  Immettere il **nome del server MDM** e scegliere **Avanti**. Il nome del server viene fornito come riferimento per identificare il server MDM. Non è il nome o l'URL del server Microsoft Intune.

    3.  Si apre la finestra di dialogo **Aggiungi &lt;NomeServer&gt;**. Fare clic su **Scegli file…** per caricare il file PEM, quindi scegliere **Avanti**..

    4.  Si apre la finestra di dialogo **Aggiungi &lt;NomeServer&gt;** con un collegamento **Token del server**. Scaricare il file token del server (.p7m) nel computer, quindi fare clic su **Fine**..

    Questo file del certificato (.p7m) viene usato per stabilire una relazione di trust tra i server di Intune e del programma di registrazione dispositivi di Apple.

4.  **Aggiungere il token DEP a Intune**
    Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), selezionare **AMMINISTRAZIONE** &gt; **Gestione dei dispositivi mobili** &gt; **iOS** &gt; ** 	Programma di registrazione dispositivi** e fare clic su **Carica un token DEP**.. Fare clic su **Sfoglia**, individuare il file del certificato (.p7m), immettere l'**ID Apple** e fare clic su **Carica**..

5.  **Aggiungere il criterio Registrazione di dispositivi aziendali**
    Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), fare clic su **Criteri** &gt; **Registrazione di dispositivi aziendali** e scegliere **Aggiungi**. Fornire le informazioni **generali** , inclusi **Nome** e **Descrizione**, specificare se i dispositivi assegnati al profilo presentano l'affinità utente o appartengono a un gruppo, quindi abilitare **Configura le impostazioni del programma di registrazione dispositivi per questo criterio** per supportare DEP. I **riquadri dell'Assistente configurazione** definiscono le impostazioni del dispositivo iOS configurate durante l'installazione.

      ![Riquadro di Assistente configurazione](../media/pol-sa-corp-enroll.png)

6.  **Assegnare dispositivi DEP per la gestione**
    Accedere al [portale del programma di registrazione dispositivi](https://deploy.apple.com) (https://deploy.apple.com) e accedere con l'ID Apple aziendale. Accedere a **Programma di distribuzione** &gt; **Programma di registrazione dispositivi** &gt; **Gestione dei dispositivi**. Specificare come **scegliere i dispositivi**, fornire le informazioni sul dispositivo e specificare i dettagli in base al **Numero di serie**del dispositivo, al **Numero dell'ordine**o **caricando un file CSV**. Quindi selezionare **Assegna al server**, selezionare il &lt;NomeServer&gt; specificato per Microsoft Intune e fare clic su **OK**.

7.  **Sincronizzare i dispositivi gestiti da DEP**
    Gli utenti amministratori possono aprire la [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **iOS** &gt; **Programma di registrazione dispositivi**, quindi fare clic su **Sincronizza**. Viene inviata una richiesta di sincronizzazione ad Apple. Per visualizzare i dispositivi gestiti da DEP dopo la sincronizzazione, nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) selezionare **Gruppi** &gt; **Dispositivi di proprietà dell'azienda**. Nell'area di lavoro **Dispositivi di proprietà dell'azienda**, lo **Stato** per i dispositivi gestiti rimane "Non contattato" finché il dispositivo non viene acceso e non viene eseguito l'Assistente configurazione per la registrazione del dispositivo.

    Per soddisfare i requisiti Apple per volumi di traffico DEP accettabili, Intune impone le seguenti limitazioni:
     -  Una sincronizzazione DEP completa può essere eseguita non più di una volta ogni 7 giorni. Durante una sincronizzazione completa, Intune aggiorna tutti i numeri di serie che Apple ha assegnato a Intune, anche se sono già stati sincronizzati in precedenza. Se si tenta una sincronizzazione completa entro 7 giorni della precedente, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
     -  Il tempo disponibile per il completamento di una richiesta di sincronizzazione è pari a 10 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante Sincronizza è disabilitato.

8.  **Distribuire i dispositivi agli utenti**
    Ora è possibile distribuire i dispositivi di proprietà dell'azienda agli utenti. Quando un dispositivo iOS viene attivato, viene registrato per la gestione con Intune.



### Vedere anche
[Prepararsi alla registrazione dei dispositivi](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


