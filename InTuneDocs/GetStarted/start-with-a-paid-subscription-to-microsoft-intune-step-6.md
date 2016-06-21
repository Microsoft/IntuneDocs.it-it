---
# required metadata

title: Creare i criteri e pubblicare un'app | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Creare i criteri e pubblicare un'app
I criteri di Intune specificano impostazioni che consentono di controllare le impostazioni di sicurezza dei dispositivi mobili, di eseguire la manutenzione delle impostazioni di Windows Firewall ed Endpoint Protection per i computer, nonché di distribuire applicazioni. Per altre informazioni, vedere [Manage settings and features on your devices with Microsoft Intune policies](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) (Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune) e [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) (Proteggere i PC Windows con Endpoint Protection per Microsoft Intune).

Con Intune è possibile eseguire due tipi di installazioni delle app. La prima è un' **installazione richiesta**, con cui l'app viene distribuita automaticamente nei computer gestiti. L'altra è un'**installazione disponibile** che distribuisce l'app, o un link all'app, al portale aziendale di Intune in modo che gli utenti possano scegliere se installarla sul computer o su dispositivi mobili.

<!-- this section really isn't necessary and confuses a lot of people because most mobile device apps aren't licensed this way (and our licensing/reporting features aren't super helpful). I think it's best to avoid this during a quick start guide.

Before using Intune to deploy apps, make sure that you have the appropriate licenses to publish, distribute, and use the app. The Licenses workspace lets you add and manage license agreement information for apps or software purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.
-->

La procedura seguente consente di impostare un criterio di configurazione per dispositivi mobili e un criterio firewall per PC Windows. Verrà anche configurato Skype come installazione disponibile per i dispositivi mobili dopo che sono stati registrati.

> [!TIP]
> Dopo aver aggiunto e distribuito un nuovo criterio, tutti gli utenti o i dispositivi in cui viene distribuito il criterio ereditano le impostazioni come criteri di base. È sempre possibile esaminare e modificare i dettagli dei criteri in un secondo momento dall'area di lavoro Criteri.


## Creare e distribuire un criterio di configurazione per dispositivi mobili

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com/).

2.  Nel riquadro a sinistra scegliere l'icona **Criteri**.

    ![admin-console-policy-workspace](./media/policy.png)

3.  Nell'elenco **Attività** della pagina **Panoramica criteri** scegliere **Aggiungi criterio**.

4.  Nell'elenco dei criteri espandere la piattaforma per cui creare un criterio, quindi scegliere **Configurazione generale** > **Creare e distribuire criteri con le impostazioni consigliate** > **Crea criterio**.

5.  Quando viene visualizzata la richiesta **Selezionare i gruppi a cui si desidera distribuire questo criterio**, scegliere un gruppo dall'elenco dei gruppi disponibili e selezionare **Aggiungi** > **OK**.

I criteri vengono visualizzati nell'elenco dei criteri di configurazione e risultano distribuiti al gruppo **Intune Users** (Utenti Intune). Fare doppio clic sul criterio per visualizzare le relative impostazioni.

## Pubblicare l'app Skype per dispositivi mobili

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere l'icona **App** e quindi selezionare **App** > **Aggiungi app**. Se richiesto, immettere le proprie credenziali [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![admin-console-apps-workspace](./media/apps.png)

    > [!NOTE] Quando si avvia **Autore del software Microsoft Intune** per la prima volta, si verifica un breve ritardo dovuto all'installazione dell'applicazione.

2.  Leggere l'avviso di sicurezza e scegliere **Esegui**.

3.  Nella pagina **Prima di iniziare** fare clic su **Avanti**.

4.  Nella pagina **Installazione software** selezionare **Collegamento esterno** in **Selezionare il modo in cui questo software viene fornito ai dispositivi**.

5.  Accedere al collegamento esterno per il software in **Specificare l'URL** e quindi scegliere **Avanti**. Assicurarsi di fare precedere l'URL da **http://**. Per l'app Skype usare il collegamento seguente corrispondente alla piattaforma per dispositivi mobili usata:

    -   **iOS:**   [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:**  [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 o Windows Phone 8.1:**  [http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Nella pagina **Descrizione software** specificare le informazioni sul software che si vuole vengano visualizzate dagli utenti nel portale aziendale e quindi scegliere **Avanti**. Sono disponibili le impostazioni seguenti (l'esempio si riferisce a Skype):

    -   **Autore:** immettere il nome dell'autore, ovvero "Microsoft"

    -   **Nome:** immettere **Skype**

    -   **Descrizione:** immettere una descrizione per il software, ad esempio **app di comunicazione Skype**

    -   **Categoria:** selezionare la categoria che meglio si adatta a questo software, ad esempio **Collaborazione**

    -   **Visualizzare questo elemento come app in evidenza ed evidenziarlo nel Portale aziendale:** selezionare questa opzione per visualizzare chiaramente l'app nel portale aziendale nei dispositivi mobili.

    -   **Icona:** scegliere se associare un'icona al software. La dimensione massima per l'icona facoltativa è 250 x 250 pixel e la dimensione consigliata è di 32 x 32 pixel.

7.  Nella pagina **Riepilogo** verificare le informazioni sul software e quindi scegliere **Carica**. Scegliere **Chiudi** per uscire dalla procedura guidata.

8.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **App** > **App** > **Skype** > **Gestisci distribuzione**.

9. Nella pagina **Seleziona gruppi** scegliere **Intune Users** (Utenti Intune) per distribuire il software al gruppo di utenti specifico e quindi scegliere **Aggiungi** > **Avanti**.

10. Nella pagina **Azione di distribuzione** selezionare **Installazione disponibile** dalla colonna **Approvazione** per il proprio gruppo.

11. Scegliere **Fine**.

L'applicazione Skype è ora disponibile per l'installazione sui dispositivi mobili dal Portale aziendale, ma prima è necessario installare il software [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] su computer e dispositivi mobili.


### Passaggi successivi
A questo punto, Passaggio 6 della *Guida introduttiva di Intune* completato.

>[!div class="step-by-step"]

>[&larr; **Organizzare utenti e dispositivi**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)[**Personalizzare il Portale aziendale** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  


<!--HONumber=Jun16_HO3-->


