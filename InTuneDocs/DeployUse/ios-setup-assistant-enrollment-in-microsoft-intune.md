---
title: Registrazione di Assistente configurazione per i dispositivi iOS con Microsoft Intune | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f3637e79e7b6f93820e775932653c41879f369fe
ms.openlocfilehash: b9cb10ccb26d4f61d63fb2dc6c18be48cc0a3182


---

# Registrare i dispositivi iOS con Apple Configurator mediante Assistente configurazione
Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda con lo strumento [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) in esecuzione in un computer Mac. Questo processo ripristina le impostazioni predefinite del dispositivo e lo prepara per l'esecuzione di Assistente configurazione con i criteri della società preinstallati da parte del nuovo utente.


## Registrazione di Assistente configurazione per i dispositivi iOS con Microsoft Intune
Con Apple Configurator è possibile ripristinare le impostazioni predefinite dei dispositivi iOS in modo da prepararli per poter essere configurati dal nuovo utente del dispositivo.  Per questo metodo è necessario connettere tramite USB il dispositivo iOS a un computer Mac per configurare la registrazione aziendale e si presuppone l'uso di Apple Configurator 2.0. La maggior parte degli scenari richiede che i criteri applicati al dispositivo iOS includano *Affinità utente* per abilitare l'app Portale aziendale di Microsoft Intune.

**Prerequisiti**
* Accesso fisico ai dispositivi iOS - La configurazione dei dispositivi deve essere annullata (ripristino impostazioni predefinite) senza password di protezione
* Numeri di serie del dispositivo - [Come ottenere un numero di serie iOS](https://support.apple.com/en-us/HT204308)
* Cavi di connessione USB
* Computer Mac con [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


1.  **Creare il gruppo di dispositivi mobili** (facoltativo). Se l'azienda richiede l'uso di gruppi di dispositivi mobili per gestire i dispositivi, creare tali gruppi. [Usare i gruppi per gestire utenti e dispositivi con Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

2.  **Creare un profilo per dispositivi**. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi. Se non lo si è ancora fatto, creare un profilo di registrazione dispositivi per i dispositivi iOS registrati tramite Apple Configurator.

    ###### Per creare un profilo

    1.  Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) passare a **Criteri** &gt; **Dispositivi di proprietà dell'azienda** e quindi scegliere **Aggiungi**.

    ![Crea profilo di registrazione dispositivi](../media/pol-sa-corp-enroll.png)

    2.  Immettere i dettagli per i profili di dispositivo:

        -   **Nome** : nome del profilo di registrazione dispositivi. (Non visibile agli utenti)

        -   **Descrizione**: descrizione del profilo di registrazione dispositivi. (Non visibile agli utenti)

        -   **Dettagli della registrazione**: consente di specificare la modalità di registrazione dei dispositivi.

            -   **Richiedi affinità utente**: il dispositivo iOS può essere associato a un utente durante la configurazione iniziale e potrebbe quindi accedere ai dati aziendali e alla posta elettronica con questo nome utente. Per la maggior parte degli scenari di Assistente configurazione, usare **Richiedi affinità utente**.
            Questa modalità supporta numerosi scenari:

                -   **Dispositivo personale di proprietà dell'azienda**: è simile alla strategia CYOD (Choose Your Own Device) secondo la quale i dispositivi sono personali o privati, ma l'amministratore gode di determinati privilegi, tra cui l'autorizzazione per cancellare dati, reimpostare, amministrare e annullare la registrazione del dispositivo. L'utente del dispositivo può installare app e dispone della maggior parte delle altre autorizzazioni previste per l'uso del dispositivo nei casi in cui non siano bloccate dai criteri di gestione.

                -   **Account del manager di registrazione dispositivi** : per registrare il dispositivo viene usato uno speciale account amministratore di Intune. Può essere gestito come account privato, ma solo un utente che conosce le credenziali del manager di registrazione può installare app, cancellare dati, reimpostare, amministrare e annullare la registrazione del dispositivo. Per informazioni sulla registrazione di un dispositivo condiviso da molti utenti con un account comune, vedere [Enroll corporate-owned devices with the Device Enrollment Manager in Microsoft Intune](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) (Registrare i dispositivi di proprietà dell'azienda con Manager di registrazione dispositivi in Microsoft Intune).

            -   **Nessuna affinità utente**: il dispositivo non ha utenti. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente sono disabilitate o non funzioneranno.

        -   **Pre-assegnazione al gruppo di dispositivi**: tutti i dispositivi distribuiti con questo profilo apparterranno inizialmente a questo gruppo. È possibile riassegnare i dispositivi dopo la registrazione.

        >[!Important]
        >Le assegnazioni di gruppo passeranno da Intune ad Azure Active Directory. [Altre informazioni](http://go.microsoft.com/fwlink/?LinkID=787064)

          -  **Programma di registrazione del dispositivo**: il programma di registrazione dispositivo di Apple (DEP) non può essere usato con la registrazione di Assistente configurazione. Verificare che sia impostato su **Disattivato**.

    3.  Scegliere **Salva profilo** per aggiungere il profilo.

3.  **Aggiungere i dispositivi iOS per la registrazione con Assistente configurazione**. Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) passare a **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i dispositivi di proprietà dell'azienda** &gt; **Tutti i dispositivi**, quindi fare clic su **Aggiungi dispositivi**. È possibile aggiungere dispositivi in due modi:

    ![Finestra di dialogo Aggiungi dispositivi](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **Caricare un file CSV contenente i numeri di serie**: creare un elenco delimitato da virgole (CSV) composto da due colonne senza intestazione e limitato a 5 MB o 5000 dispositivi per ogni file CSV.

        |||
        |-|-|
        |&lt;Numero di serie 1&gt;|&lt;Dettagli sul dispositivo 1&gt;|
        |&lt;Numero di serie 2&gt;|&lt;Dettagli sul dispositivo 2&gt;|
        Il file con estensione CSV quando viene visualizzato in un editor di testo viene visualizzato come:

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **Aggiungere manualmente i dettagli dispositivo**: immettere il numero di serie e i dettagli per un massimo di cinque dispositivi.

    > [!NOTE]
    > Se in un secondo tempo occorre rimuovere i dispositivi di proprietà dell'azienda dalla gestione di Intune, può essere necessario rimuoverne il numero di serie da Intune nel gruppo **Dispositivi di proprietà dell'azienda** in **Dispositivi aziendali preregistrati** per disabilitarne la registrazione.  Se Intune esegue una procedura di ripristino di emergenza nell’ora in cui sono stati rimossi i numeri di serie, sarà necessario verificare che solo i numeri di serie dei dispositivi attivi siano presenti in tale gruppo.

    Scegliere **Avanti**.

4.  **Selezionare i dispositivi da registrare**. Confermare i dispositivi da registrare. I numeri di serie già registrati o registrati in altro modo non possono essere importati. Scegliere **Avanti** per continuare.

5.  **Assegnare il profilo**. Specificare il profilo da assegnare ai dispositivi aggiunti dall'elenco dei profili disponibili, esaminare i **Dettagli del profilo di registrazione** e quindi fare clic su **Fine**. I dispositivi aggiunti manualmente possono essere assegnati a qualsiasi profilo di registrazione.

6.  **Esportare un profilo per la distribuzione nei dispositivi iOS**. Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) passare a **Criteri** &gt; **Registrazione di dispositivi aziendali** e quindi selezionare il profilo di dispositivo da distribuire ai dispositivi mobili. Scegliere **Esporta** nella barra delle attività. Copiare e salvare l' **URL del profilo**. Verrà caricato in Apple Configurator in un secondo momento per definire il profilo di Intune usato dai dispositivi iOS.
    Per supportare Apple Configurator 2 è necessario modificare l'URL del profilo 2.0. Replace
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    con

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   L'URL del profilo verrà caricato nel servizio Apple DEP con Apple Configurator nella procedura seguente, per definire il profilo di Intune usato dai dispositivi iOS.



7.  **Preparare il dispositivo con Apple Configurator**. I dispositivi iOS vengono connessi al computer Mac e registrati per la gestione dei dispositivi mobili.

    1.  In un computer Mac aprire **Apple Configurator 2**. Nella barra dei menu scegliere **Apple Configurator 2** e quindi scegliere **Preferences** (Preferenze).

         > [!WARNING]
         > Le impostazioni predefinite dei dispositivi verranno ripristinate durante il processo di registrazione. Come procedura consigliata, reimpostare il dispositivo e accenderlo. Come procedura consigliata, i dispositivi dovrebbero trovarsi in corrispondenza della schermata **Hello** quando si connette il dispositivo.

    2. Nel riquadro delle preferenze selezionare **Server** e quindi fare clic sul simbolo "+" sotto il riquadro sinistro per avviare la procedura guidata per il server MDM. Scegliere **Avanti**.

    3. Immettere **Name** (Nome) e **Enrollment URL** (URL di registrazione) per il server MDM dal passaggio 6 precedente. Per l'URL di registrazione immettere l'URL del profilo di registrazione esportato da Intune. Scegliere **Avanti**.  

       Se si riceve un messaggio di avviso sui requisiti del profilo di attendibilità per Apple TV, è possibile disattivare in modo sicuro l'opzione **Convalida profilo** scegliendo la "X" grigia. È possibile anche ignorare qualsiasi avviso relativo a certificati trust anchor. Per continuare, fare clic su **Next** (Avanti) fino a completare la procedura guidata.

    4.  Nel riquadro **Server** fare clic su "Edit" (Modifica) accanto al profilo del nuovo server. Verificare che URL di registrazione corrisponda esattamente all'URL esportato da Intune. In caso contrario immettere nuovamente l'URL originale, quindi fare clic su **Save** (Salva) per salvare il profilo di registrazione esportato da Intune.

    5.  Connettere i dispositivi mobili iOS al computer Apple con un adattatore USB.

        > [!WARNING]
        > Le impostazioni predefinite dei dispositivi verranno ripristinate durante il processo di registrazione. Come procedura consigliata, reimpostare il dispositivo e accenderlo. Come procedura consigliata, i dispositivi dovrebbero trovarsi nella schermata **Hello** quando si avvia Assistente di configurazione.

    6.  Fare clic su **Prepare** (Prepara). Nel riquadro **Prepare iOS Device** (Prepara dispositivo iOS) selezionare **Manual** (Manuale) e quindi scegliere **Next** (Avanti).

    7. Nel riquadro **Enroll in MDM Server** (Registra su server MDM) selezionare il nome creato e quindi scegliere **Next** (Avanti).

    8. Nel riquadro **Supervise Devices** (Supervisione dispositivi) selezionare il livello di supervisione e quindi scegliere **Next** (Avanti).

    9. Nel riquadro **Create an Organization** (Crea un'organizzazione) scegliere un'organizzazione in **Organization** (Organizzazione) oppure crearne una nuova e scegliere **Next** (Avanti).

    10. Nel riquadro **Configure iOS Setup Assistant** (Configura Assistente configurazione di iOS) scegliere i passaggi presentati all'utente e quindi fare clic su **Prepare** (Prepara). Se richiesto, eseguire l'autenticazione per aggiornare le impostazioni di attendibilità.  

    11. Al termine della preparazione del dispositivo iOS, sarà possibile disconnettere il cavo USB.  

8.  **Distribuire i dispositivi**. I dispositivi sono ora pronti per la registrazione aziendale. Spegnere i dispositivi e distribuirli agli utenti. All'accensione dei dispositivi, verrà avviato l'Assistente configurazione.



### Vedere anche
[Prepararsi alla registrazione dei dispositivi](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jul16_HO1-->


