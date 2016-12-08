---
title: Creare criteri e pubblicare un&quot;app per gli utenti | Microsoft Intune
description: Come creare criteri e pubblicare un&quot;app quando si esegue l&quot;iscrizione per una valutazione gratuita di 30 giorni di Intune
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 64f857307046ea061e702d0b383968b322b89c33


---


# <a name="create-policies-and-publish-an-app-to-evaluation-users"></a>Creare i criteri e pubblicare un'app per gli utenti della valutazione
I criteri di Intune specificano impostazioni che consentono di controllare le impostazioni di sicurezza dei dispositivi mobili, di eseguire la manutenzione delle impostazioni di Windows Firewall ed Endpoint Protection per i computer, nonché di distribuire applicazioni. Se si intende usare Intune per dispositivi che dopo la valutazione verranno configurati per la produzione, è essenziale seguire le istruzioni in [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) e [Proteggere i PC Windows con Endpoint Protection per Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).

Con Intune è possibile eseguire due tipi di installazioni delle app. La prima è un'**installazione richiesta**, con cui l'app viene distribuita automaticamente nei dispositivi gestiti. L'altra è un'**installazione disponibile** che distribuisce l'app, o un link all'app, al portale aziendale di Intune in modo che gli utenti possano scegliere se installarla sul computer o su dispositivi mobili.

Prima di usare Intune per distribuire app, assicurarsi di disporre delle licenze appropriate per pubblicare, distribuire e usare l'app. L'area di lavoro **Licenze** consente di aggiungere e gestire le informazioni sui contratti di licenza per app o software acquistati tramite Contratti multilicenza Microsoft e per app o software Microsoft o non Microsoft acquistati in altro modo. È quindi possibile creare report licenza che consentono di visualizzare informazioni sull'utilizzo delle licenze gestite nell'azienda e rimanere aggiornati sulle attività correlate all'utilizzo delle licenze.

In questa procedura verrà impostato un criterio di configurazione per dispositivi mobili e un criterio firewall per computer Windows. Verrà inoltre configurato Skype come installazione disponibile per i dispositivi mobili dopo che sono stati registrati. Dopo aver aggiunto e distribuito un nuovo criterio, tutti gli utenti o i dispositivi in cui viene distribuito il criterio ereditano le impostazioni come criteri di base. È sempre possibile esaminare e modificare i dettagli dei criteri in un secondo momento dall'area di lavoro **Criteri** nella console di amministrazione.

## <a name="create-and-deploy-a-mobile-device-configuration-policy"></a>Creare e distribuire un criterio di configurazione per dispositivi mobili

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com/).

2.  Nel riquadro a sinistra scegliere l'icona **Criteri**.

3.  Nell'elenco **Attività** della pagina **Panoramica criteri** scegliere **Aggiungi criterio**.

4.  Nell'elenco dei criteri espandere la piattaforma per cui si vuole creare un criterio, selezionare **Configurazione generale**, scegliere **Creare e distribuire criteri personalizzati** e infine scegliere **Crea criterio**.

5.  Al prompt **Selezionare i gruppi a cui si vuole distribuire questo criterio** selezionare **Utenti di valutazione personali** nell'elenco, quindi fare clic su **Aggiungi**&gt;**OK**.

I criteri vengono visualizzati nell'elenco dei criteri di configurazione e risultano distribuiti al gruppo **Utenti di valutazione personali** . Fare doppio clic sul criterio per visualizzare le relative impostazioni.

## <a name="publish-the-skype-app-for-mobile-devices"></a>Pubblicare l'app Skype per dispositivi mobili

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere l'icona **App** e quindi selezionare **App**&gt;**Aggiungi app**. Se richiesto, immettere le proprie credenziali Intune.

    > [!NOTE]
    > Quando si avvia **Autore del software Intune** per la prima volta, si verifica un breve ritardo dovuto all'installazione dell'applicazione.

2.  Leggere l'avviso di sicurezza e scegliere **Esegui**.

3.  Nella pagina **Prima di iniziare** fare clic su **Avanti**.

4.  Nella pagina **Installazione software** selezionare **Collegamento esterno**in **Selezionare il modo in cui questo software viene fornito ai dispositivi**.

5.  Accedere al collegamento esterno per il software in **Specificare l'URL** e quindi scegliere **Avanti**. Assicurarsi di fare precedere l'URL da **https://**. Per l'app Skype usare il collegamento seguente corrispondente alla piattaforma per dispositivi mobili usata:

    -   **iOS:** [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8.1:** [http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Nella pagina **Descrizione software** specificare le informazioni sul software che si vuole vengano visualizzate dagli utenti nel portale aziendale e quindi scegliere **Avanti**. Sono disponibili le impostazioni seguenti (l'esempio si riferisce a Skype):

    -   **Editore:** immettere il nome dell'editore, ovvero **Microsoft**

    -   **Nome:** immettere **Skype**

    -   **Descrizione:** immettere una descrizione per il software, ad esempio **app di comunicazione Skype**

    -   **Categoria:** selezionare la categoria che meglio si adatta a questo software, ad esempio **Collaborazione**

    -   **Visualizzare questo elemento come app in evidenza ed evidenziarlo nel Portale aziendale:** selezionare questa opzione per visualizzare chiaramente l'app nel portale aziendale nei dispositivi mobili.

    -   **Icona:**  (Facoltativo) Scegliere se associare un'icona al software. Le dimensioni massime per l'icona sono di 250 x 250 pixel, ma le dimensioni consigliate sono di 32 x 32 pixel.

7.  Nella pagina **Riepilogo** verificare le informazioni sul software e quindi scegliere **Carica**. Scegliere **Chiudi** per uscire dalla procedura guidata.

8.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **App** &gt; **App** &gt; **Skype** &gt; **Gestisci distribuzione**.

9. Nella pagina **Seleziona gruppi** selezionare **Utenti di valutazione personali** per distribuire il software a questo gruppo di utenti, quindi fare clic su **Aggiungi**&gt;**Avanti**.

10. Nella pagina **Azione di distribuzione** selezionare **Installazione disponibile** dalla colonna **Approvazione** per il proprio gruppo.

11. Scegliere **Fine**.

## <a name="install-the-skype-app"></a>Installare l'app Skype
Aprire l'app Portale aziendale nel dispositivo mobile, scegliere **App** e quindi installare Microsoft Skype.

Questa è l'operazione conclusiva della guida alla gestione di dispositivi mobili di Intune. Per altre informazioni su Intune, seguire i collegamenti riportati nella sezione Passaggi successivi.
## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle [funzionalità di Intune](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)

Leggere informazioni sui [metodi comuni per l'uso di Intune](common-ways-to-use-intune.md)

Passare a una [sottoscrizione a pagamento](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)



<!--HONumber=Nov16_HO5-->


