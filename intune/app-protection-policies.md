---
title: Creare e distribuire i criteri di protezione delle app
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni sul modo in cui i criteri di protezione delle app di Intune consentono di proteggere i dati aziendali usati dalle app gestite.'
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d63e99561766268941b2c6d8b3bb6a1dd028f72c
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-create-and-assign-app-protection-policies"></a>Come creare e assegnare criteri di protezione delle app

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

**Se non ci si trova nel servizio Intune nel programma di anteprima del portale di Azure**, questo argomento spiega [come creare i criteri di protezione delle app](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) nella console di Intune classica.

I criteri di protezione delle app possono essere applicati in app eseguite su dispositivi gestiti o non gestiti da Intune. Per una descrizione più dettagliata del funzionamento dei criteri di protezione delle app e degli scenari supportati dai criteri di protezione delle app di Intune, vedere [What is Microsoft Intune app protection policies](app-protection-policy.md)(Cosa sono i criteri di protezione delle app di Microsoft Intune).

##  <a name="create-an-app-protection-policy"></a>Creare un criterio di protezione delle app
1.  Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **Criteri di protezione delle app**.

2.  Verrà visualizzato il pannello **Criteri di protezione delle app**, in cui sarà possibile creare nuovi criteri e modificare i criteri esistenti. Scegliere **Aggiungi criteri**.

  ![Schermata del pannello Aggiungi criteri](./media/app-protection-add-policy.png)

3.  Digitare un nome per il criterio, aggiungere una breve descrizione e selezionare il tipo di piattaforma per creare un criterio per iOS e Android. È possibile creare più criteri per ogni piattaforma.

4.  Scegliere **App** per aprire il **pannello App**, che contiene l'elenco delle app disponibili. Selezionare una o più app dall'elenco che si vuole associare al criterio che si sta creando. Dopo avere selezionato le app, scegliere **Seleziona** nella parte inferiore del pannello **App** per salvare la selezione.

    > [!IMPORTANT]
    > È necessario selezionare almeno un'app per creare un criterio.

5.  Nel pannello **Aggiungi criteri** scegliere **Configurare le impostazioni necessarie** per aprire il pannello delle impostazioni dei criteri.

    Esistono due categorie di impostazioni dei criteri: **Rilocazione dati** e **Accesso**.  I criteri di rilocazione dati sono applicabili allo spostamento dei dati da e verso le app, mentre i criteri di accesso determinano il modo in cui l'utente finale accede alle applicazioni in un contesto aziendale.
    In questa introduzione le impostazioni dei criteri hanno valori predefiniti. Non è necessario apportare modifiche se i valori predefiniti soddisfano i requisiti.

    > [!TIP]
    > Queste impostazioni dei criteri vengono applicate solo quando si usano le app nel contesto aziendale.  Quando l'utente finale usa l'app per eseguire un'attività personale, questi criteri non hanno effetto.



6.  Scegliere **OK** per salvare la configurazione. Viene di nuovo visualizzato il pannello **Aggiungi un criterio** . Scegliere **Crea** per creare i criteri e salvare le impostazioni.


Dopo aver creato un criterio come descritto nella procedura precedente, non verrà distribuito a tutti gli utenti. Per distribuire un criterio, vedere la sezione seguente, "Distribuire un criterio agli utenti".

## <a name="deploy-a-policy-to-users"></a>Distribuire un criterio agli utenti

1.  Nel pannello **Criteri** scegliere **Gruppi di utenti** per aprire il pannello **Gruppi di utenti**. Fare clic su **Aggiungi un gruppo di utenti** nel pannello **Gruppi di utenti** per aprire il pannello **Aggiungi un gruppo di utenti**.

  ![Schermata del pannello Gruppi di utenti con l'opzione Aggiungi un gruppo di utenti evidenziata](./media/app-protection-policy-add-users.png)

2.  Viene visualizzato un elenco dei gruppi di utenti nel pannello **Aggiungi un gruppo di utenti** . Si tratta di un elenco di tutti i gruppi di sicurezza in **Azure Active Directory**. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e quindi scegliere **Seleziona**. Se si sceglie **Seleziona** il criterio verrà distribuito agli utenti.
  ![Schermata del pannello Aggiungi gruppo di utenti che visualizza l'elenco di utenti di Azure Active Directory](./media/azure-ad-user-group-list.png)

A questo punto, l'utente ha creato un criterio e lo ha distribuito agli utenti.

Solo gli utenti a cui sono state assegnate licenze di Microsoft Intune sono interessati dai criteri. Gli utenti che appartengono al gruppo di sicurezza selezionato e ai quali non è stata assegnata una licenza di Microsoft Intune non saranno interessati dai criteri.

>[!IMPORTANT]
> Se si usa Intune con Configuration Manager per gestire i dispositivi Android e iOS, il criterio viene applicato solo agli utenti inclusi direttamente nel gruppo selezionato. I membri dei gruppi figlio annidati all'interno del gruppo selezionato non sono interessati.

Gli utenti finali possono scaricare le app dall'Apple Store o da Google Play. Per altre informazioni, vedere:
* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>Modificare i criteri esistenti
È possibile modificare criteri esistenti e applicarli agli utenti di destinazione. Tuttavia, quando si modificano criteri esistenti, gli utenti che hanno già effettuato l'accesso alle app non vedranno le modifiche per un intervallo di tempo di 8 ore.

Per visualizzare immediatamente l'effetto delle modifiche, l'utente finale dovrà disconnettersi dall'app ed eseguire nuovamente l'accesso.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Per modificare l'elenco delle app associate al criterio

1.  Nel pannello **Criteri per le app** scegliere il criterio che si vuole modificare. Verrà aperto un pannello specifico per il criterio appena selezionato.

2.  Nel pannello dei criteri, scegliere **App di destinazione** per aprire l'elenco delle app.

3.  Rimuovere o aggiungere app dall'elenco e scegliere l'icona **Salva** per salvare le modifiche.

### <a name="to-change-the-list-of-user-groups"></a>Per modificare l'elenco dei gruppi di utenti

1.  Nel pannello **Criteri per le app** scegliere il criterio che si vuole modificare. Verrà aperto il pannello specifico per il criterio selezionato.

2.  Nel pannello dei criteri, scegliere **Gruppi di utenti** per aprire il pannello **Gruppo di utenti**, che visualizza l'elenco dei gruppi di utenti che hanno questo criterio.

3.  Per aggiungere un nuovo gruppo di utenti al criterio, scegliere **Aggiungi un gruppo di utenti** e selezionare il gruppo di utenti. Scegliere **Seleziona** per distribuire il criterio al gruppo selezionato.

4.  Per eliminare un gruppo di utenti, evidenziare il gruppo di utenti che si vuole rimuovere. Scegliere i puntini di sospensione (...) e quindi scegliere **Elimina** per rimuovere il gruppo di utenti.
  ![Schermata con l'opzione Elimina visualizzata](./media/app-protection-policy-delete-user.png)

### <a name="to-change-policy-settings"></a>Per modificare le impostazioni dei criteri

1.  Nel pannello **Criteri per le app** scegliere il criterio che si vuole modificare. Verrà aperto un pannello specifico per il criterio appena selezionato.


2.  Scegliere **Impostazioni criteri** per aprire il pannello **Impostazioni criteri**.

3.  Modificare le impostazioni e quindi scegliere l'icona **Salva** per salvare le modifiche.

## <a name="policy-settings"></a>Impostazioni criteri
Per visualizzare l'elenco completo delle impostazioni dei criteri per iOS e Android, selezionare una delle seguenti voci:

> [!div class="op_single_selector"]
- [Criteri iOS](app-protection-policy-settings-ios.md)
- [Criteri Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Passaggi successivi
[Monitorare la conformità e lo stato utente](app-protection-policies-monitor.md)

### <a name="see-also"></a>Vedere anche
* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)

