---
title: 'Esercitazione: Usare Apple Business Manager o Device Enrollment Program per registrare i dispositivi iOS/iPadOS in Intune'
titleSuffix: Microsoft Intune
description: Questa esercitazione descrive come configurare le funzionalità di registrazione dei dispositivi aziendali di Apple da ABM per registrare i dispositivi iOS/iPadOS in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9aab0233c05416fc50413a7889435cb221179730
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415149"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-iosipados-devices-in-intune"></a>Esercitazione: Usare le funzionalità Corporate Device Enrollment di Apple in Apple Business Manager (ABM) per registrare i dispositivi iOS/iPadOS in Intune
Le funzionalità Device Enrollment di Apple Business Manager semplificano la registrazione di dispositivi. Intune supporta anche il portale Device Enrollment Program precedente di Apple, ma è consigliabile iniziare da zero con Apple Business Manager. Con Microsoft Intune e Apple Corporate Device Enrollment, i dispositivi vengono registrati automaticamente in modo sicuro la prima volta che vengono accesi. È pertanto possibile spedire i dispositivi a più utenti senza dover configurare ogni singolo dispositivo. 

In questa esercitazione si apprenderà come:
> [!div class="checklist"]
> * Ottenere un token di Apple Device Enrollment Program
> * Sincronizzare i dispositivi gestiti con Intune
> * Creare un profilo di registrazione
> * Assegnare il profilo di registrazione ai dispositivi

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti
- Dispositivi acquistati in [Apple Business Manager](https://business.apple.com) o [Device Enrollment Program di Apple](http://deploy.apple.com)
- Impostare l'[autorità di gestione di dispositivi mobili](../fundamentals/mdm-authority-set.md)
- Ottenere un [certificato push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>Ottenere un token di Apple Device Enrollment Program
Prima di registrare i dispositivi iOS/iPadOS con le funzionalità di registrazione aziendale di Apple, è necessario un file di token di Apple Device Enrollment token (PEM). Questo token consente a Intune di sincronizzare le informazioni sui dispositivi Apple di proprietà dell'azienda. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

Per creare un token di Device Enrollment, usare il portale ABM o DEP. Usare questi portali anche per assegnare i dispositivi a Intune per la gestione.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione** > **Aggiungi**.

2. Concedere a Microsoft l'autorizzazione per l'invio di informazioni su utenti e dispositivi ad Apple selezionando **Accetto**.

   ![Schermata del pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica.](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Scegliere **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file con estensione pem viene usato per richiedere un certificato di relazione di trust al portale ABM o DEP.

4. Scegliere **Creare un token tramite Apple Device Enrollment Program** per aprire il portale del programma di distribuzione Apple e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token DEP.

5. Nel [portale dei programmi di distribuzione](https://deploy.apple.com) di Apple scegliere **Inizia** per **Device Enrollment Program**. La procedura potrebbe essere leggermente diversa dai passaggi seguenti in [Apple Business Manager](https://business.apple.com).

4. Nella pagina **Gestisci server** scegliere **Aggiungi server MDM**.

5. Come **nome del server MDM** immettere *TestMDMServer* e quindi scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non corrisponde al nome o all'URL del server di Microsoft Intune.

6. Viene visualizzata la finestra di dialogo **Aggiungi &lt;NomeServer&gt;** che richiede di **caricare la chiave pubblica**. Selezionare **Scegli file**. per caricare il file PEM e scegliere **Avanti**.

6. Passare a **Programma di distribuzione** > **Programma di registrazione dispositivi** > **Gestione dei dispositivi**.
7. In **Scegli dispositivi per** scegliere **Numero di serie**. <!--ask Tiffany about this-->

8. In **Scegliere un'azione** scegliere **Assegna al server,** scegliere il &lt;nome del serve&gt;r specificato per Microsoft Intune e quindi scegliere **OK**. Il portale Apple assegna i dispositivi specificati al server di Intune per la gestione e quindi visualizza il messaggio **Assegnazione completata**.

   Nel portale Apple passare a **Deployment Programs** (Programmi di distribuzione) &gt; **Device Enrollment Program** &gt; **View Assignment History** (Visualizza cronologia di assegnazione) per visualizzare un elenco di dispositivi con la rispettiva assegnazione di server MDM.

9. Per riferimenti futuri, in Intune nel portale di Azure specificare l'ID Apple usato per creare il token.

    ![Screenshot della specifica dell'ID Apple usato per creare il token DEP e passare al token DEP.](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. Nella casella **Token Apple** passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi scegliere **Crea**. 

11. Se si vogliono applicare tag di ambito per limitare gli amministratori che hanno accesso a questo token, selezionare gli ambiti.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple
Ora che è stato installato il token, è possibile creare un profilo di registrazione per i dispositivi iOS/iPadOS di proprietà dell'azienda. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione**.

2. Selezionare il token installato, scegliere **Profili** > **Crea profilo**.

3. In **Crea profilo** immettere *TestDEPProfile* per **Nome** e *Test DEP per dispositivi iOS/iPadOS* per **Descrizione**. Questi dettagli non vengono visualizzati agli utenti.

4. Scegliere **iOS** in **Piattaforma**.

5. Stabilire se i dispositivi dovranno essere registrati con o senza **Affinità utente**. La funzionalità Affinità utente è destinata ai dispositivi che verranno usati da specifici utenti. Se gli utenti vogliono usare il portale aziendale per servizi come l'installazione di app, scegliere **Registra con affinità utente**. Se gli utenti non hanno bisogno del portale aziendale o si vuole eseguire il provisioning del dispositivo per molti utenti, scegliere **Registra senza affinità utente**.

6. Se si sceglie la registrazione con Affinità utente, stabilire se si vuole eseguire l'autenticazione con il portale aziendale o con Apple Setup Assistant. Se si vuole usare Multi-Factor Authentication, consentire agli utenti di cambiare le password dopo il primo accesso o richiedere agli utenti di reimpostare le loro password durante la registrazione, scegliere **Sì** per **Autenticazione con il Portale aziendale invece di Apple Setup Assistant**. Se si vuole usare l'autenticazione HTTP di base fornita da Apple tramite Apple Setup Assistant, scegliere **No**. Se si sceglie **Sì** e si vuole che l'applicazione Portale aziendale venga aggiornata automaticamente nei dispositivi degli utenti finali, distribuire separatamente il Portale aziendale come app richiesta a questi utenti usando il programma Volume Purchase Program (VPP) di Apple.

7. Se si sceglie la registrazione con Affinità utente e Autenticazione con il portale aziendale, stabilire se si vuole installare il portale aziendale con Apple Volume Purchase Program (VPP). Se si installa il portale aziendale con un token di VPP, l'utente non dovrà immettere un ID e una password Apple per scaricare il portale aziendale dallo store durante la registrazione. Scegliere **Usa il token** in **Installa il Portale aziendale con VPP** per selezionare un token di VPP con licenze gratuite del portale aziendale disponibili. Se non si vuole usare VPP per distribuire il portale aziendale, scegliere **Non usare VPP** in **Installa il Portale aziendale con VPP**. 

8. Se si sceglie la registrazione con Affinità utente, Autenticazione con il portale aziendale e Installa il Portale aziendale con VPP, decidere se si vuole eseguire il portale aziendale in modalità applicazione singola fino all'autenticazione. Questa impostazione consente di assicurarsi che l'utente non abbia accesso ad altre app finché non completa la registrazione aziendale. Se si vuole limitare l'utente a questo flusso fino al completamento della registrazione, scegliere **Sì** in **Esegui il Portale aziendale in modalità applicazione singola fino all'autenticazione**. 

9. Scegliere **Impostazioni di gestione dei dispositivi** e scegliere **Sì** in **Supervisione eseguita**. I dispositivi supervisionati offrono la maggior parte delle opzioni di gestione per i dispositivi iOS/iOS/iPadOS aziendali.

10. Scegliere **Sì** in **Registrazione bloccata** per assicurarsi che gli utenti non possano rimuovere la gestione dal dispositivo aziendale. 

11. Scegliere un'opzione di **Sincronizza con computer** per determinare se sarà possibile sincronizzare i dispositivi iOS/iPadOS con i computer.

12. Per impostazione predefinita, Apple assegna il nome al dispositivo con il tipo di dispositivo, ad esempio iPad. Se si vuole fornire un modello di nome diverso, scegliere **Sì** in **Applica il modello di nome di dispositivo**. Immettere il nome da applicare ai dispositivi, dove le stringhe *{{SERIAL}}* e *{{DEVICETYPE}}* sostituiranno il numero di serie e il tipo di ogni dispositivo. In caso contrario, scegliere **No** in **Applica il modello di nome di dispositivo**.

13. Scegliere **OK**.

14. Scegliere **Personalizzazione dell'Assistente configurazione** e immettere *Reparto esercitazione* per **Nome del reparto**. Questa stringa viene visualizzata agli utenti quando toccano **Informazioni sulla configurazione** durante l'attivazione del dispositivo.

15. In **Telefono del reparto** immettere un numero di telefono. Il numero viene visualizzato quando gli utenti toccano il pulsante **Richiesta di assistenza** durante l'attivazione.

16. È possibile scegliere **Mostra** o **Nascondi** per diverse schermate durante l'attivazione del dispositivo. Per un'esperienza di registrazione più semplice possibile, impostare tutte le schermate su **Nascondi**.

17. Scegliere **OK** > **Crea**.

## <a name="sync-managed-devices-to-intune"></a>Sincronizzare i dispositivi gestiti con Intune

Dopo aver configurato un token del programma di registrazione con il portale ABM, ASM o DEP e aver assegnato i dispositivi al server MDM, è possibile aspettare che questi dispositivi vengano sincronizzati con il servizio Intune oppure eseguire il push manuale di una sincronizzazione. Senza sincronizzazione manuale, possono essere necessarie fino a 24 ore prima che i dispositivi vengano visualizzati nel portale di Azure.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione** > scegliere un token dall'elenco > **Dispositivi** > **Sincronizza**.

## <a name="assign-an-enrollment-profile-to-iosipados-devices"></a>Assegnare un profilo di registrazione ai dispositivi iOS/iPadOS

Prima della registrazione è necessario assegnare ai dispositivi un profilo DEP. Questi dispositivi sono sincronizzati con Intune da Apple e devono essere assegnati al token del server MDM appropriato nel portale ABM, ASM o DEP.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione** > scegliere un token dall'elenco.
2. Scegliere **Dispositivi** > scegliere i dispositivi nell'elenco > **Assegna profilo**.
3. In **Assegna profilo** scegliere un profilo per i dispositivi > **Assegna**.

## <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

È stata configurata la gestione e la sincronizzazione tra Apple e Intune ed è stato assegnato un profilo per consentire la registrazione dei dispositivi DEP. È ora possibile distribuire i dispositivi agli utenti. I dispositivi con affinità utente richiedono che a ogni utente sia assegnata una licenza di Intune.

## <a name="next-steps"></a>Passaggi successivi

È possibile consultare altre informazioni sulle opzioni disponibili per la registrazione dei dispositivi iOS/iPadOS.

> [!div class="nextstepaction"]
> [Articolo con dettagli sulla registrazione DEP per iOS/iPadOS](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS/iPadOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
