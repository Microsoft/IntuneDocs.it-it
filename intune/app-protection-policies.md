---
title: Creare e distribuire i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Informazioni su come creare e assegnare criteri di protezione delle app di Microsoft Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a66ed41442e89ed40850f5b9cd56cbc004a43d0
ms.sourcegitcommit: 8b4f5685dc7f41f5e967a8f9d0627707a36dbe93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2018
ms.locfileid: "40251610"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Come creare e assegnare criteri di protezione delle app

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Informazioni su come creare e assegnare criteri di protezione delle app di Microsoft Intune agli utenti. In questo argomento viene anche descritto come apportare modifiche a criteri esistenti.

## <a name="before-you-begin"></a>Prima di iniziare

I criteri di protezione delle app possono essere applicati in app eseguite su dispositivi gestiti o non gestiti da Intune. Per una descrizione più dettagliata del funzionamento dei criteri di protezione delle app e degli scenari supportati dai criteri di protezione delle app di Intune, vedere [Che cosa sono i criteri di protezione delle app di Microsoft Intune?](app-protection-policy.md).

Per un elenco delle app supportate da MAM, vedere [Elenco di app MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Per informazioni sull'aggiunta di app line-of-business (LOB) dell'organizzazione in Microsoft Intune per preparare i criteri di protezione delle app, vedere [Aggiungere app in Microsoft Intune](apps-add.md).

##  <a name="create-an-app-protection-policy"></a>Creare un criterio di protezione delle app
1. Nel carico di lavoro **App per dispositivi mobili** selezionare **Criteri di protezione delle app** dalla sezione **Gestisci**. Questa selezione determina la visualizzazione dei dettagli dei **Criteri di protezione delle app**, in cui è possibile creare nuovi criteri e modificare i criteri esistenti.
2. Scegliere **Aggiungi criteri**.

   ![Schermata del pannello "Aggiungi criteri"](./media/app-protection-add-policy.png)

3. Digitare un nome per il criterio, aggiungere una breve descrizione e selezionare il tipo di piattaforma per i criteri. È possibile creare più criteri per ogni piattaforma, se necessario.

4. Scegliere **App** per aprire il pannello **App**, che contiene l'elenco delle app disponibili. Selezionare una o più app dall'elenco che si vuole associare al criterio che si sta creando.
5. Dopo aver selezionato le app, scegliere **Seleziona** per salvare la selezione.

    > [!IMPORTANT]
    > È necessario selezionare almeno un'app per creare un criterio.

6. Scegliere **Configura le impostazioni obbligatorie** nel pannello **Aggiungi criteri** per aprire le **Impostazioni**.

   Esistono due categorie di impostazioni dei criteri: **Rilocazione dati** e **Accesso**.  I criteri di rilocazione dei dati sono applicabili allo spostamento dei dati da e verso le app. I criteri di accesso determinano come l'utente finale accede alle applicazioni in un contesto aziendale.
   In questa introduzione le impostazioni dei criteri hanno valori predefiniti. Non è necessario apportare modifiche se i valori predefiniti soddisfano i requisiti.

   > [!TIP]
   > Queste impostazioni dei criteri vengono applicate solo quando si usano le app nel contesto aziendale. Quando gli utenti finali usano l'app per eseguire un'attività personale, questi criteri non hanno effetto.

7. Scegliere **OK** per salvare la configurazione. Viene di nuovo visualizzato il riquadro **Aggiungi criteri**. Scegliere **Crea** per creare i criteri e salvare le impostazioni.
8. Scegliere **OK** per salvare la configurazione. A questo punto ci si trova di nuovo nel riquadro **Aggiungi criteri**.
9. Scegliere **Crea** per creare i criteri e salvare le impostazioni.

Dopo aver creato un criterio come descritto nella procedura precedente, non verrà distribuito a tutti gli utenti. Per distribuire un criterio, vedere [Distribuire un criterio agli utenti](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Distribuire un criterio agli utenti


1. Selezionare un criterio nel riquadro **Criteri di protezione delle app**.

1. Nel riquadro **Criteri** scegliere **Assegnazioni**, che consente di visualizzare il riquadro **Protezione app di Intune - Assegnazioni**. Scegliere **Selezionare i gruppi da includere** nel riquadro **Assegnazioni** per aprire il riquadro **Selezionare i gruppi da includere**.

   ![Schermata del riquadro Assegnazioni con l'opzione di menu Selezionare i gruppi da includere evidenziata](./media/app-protection-policy-add-users.png)

2.  Viene visualizzato un elenco dei gruppi di utenti nel riquadro **Aggiungi un gruppo di utenti**. Si tratta di un elenco di tutti i gruppi di sicurezza in **Azure Active Directory**. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e quindi scegliere **Seleziona**. Se si sceglie **Seleziona** il criterio verrà distribuito agli utenti.

    ![Schermata del riquadro Aggiungi un gruppo di utenti che visualizza l'elenco di utenti di Azure Active Directory](./media/azure-ad-user-group-list.png)

A questo punto, l'utente ha creato un criterio e lo ha distribuito agli utenti.

Solo gli utenti a cui sono state assegnate licenze di Microsoft Intune sono interessati dai criteri. Gli utenti del gruppo di sicurezza selezionato a cui non è stata assegnata una licenza di Intune non sono interessati.

>[!IMPORTANT]
> Se si usa Intune con Configuration Manager per gestire i propri dispositivi, il criterio viene applicato solo agli utenti inclusi direttamente nel gruppo selezionato. I membri dei gruppi figlio annidati all'interno del gruppo selezionato non sono interessati.

Gli utenti finali possono scaricare le app dall'Apple Store o da Google Play. Per altre informazioni, vedere:
* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>Modificare i criteri esistenti
È possibile modificare criteri esistenti e applicarli agli utenti di destinazione. Quando tuttavia si modificano criteri esistenti, gli utenti che hanno già effettuato l'accesso alle app non vedranno le modifiche per un intervallo di tempo di 8 ore.

Per visualizzare immediatamente l'effetto delle modifiche, l'utente finale deve disconnettersi dall'app ed eseguire nuovamente l'accesso.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Per modificare l'elenco delle app associate al criterio

1.  Nel riquadro **Criteri di protezione delle app** scegliere i criteri da modificare per aprire un riquadro specifico per i criteri appena selezionati.

2.  Nel riquadro dei criteri scegliere **App di destinazione** per aprire l'elenco delle app.

3.  Rimuovere o aggiungere app dall'elenco e scegliere l'icona **Salva** per salvare le modifiche.

### <a name="to-change-the-list-of-user-groups"></a>Per modificare l'elenco dei gruppi di utenti


1.  Nel riquadro **Criteri di protezione delle app** scegliere i criteri da modificare per aprire il riquadro specifico per i criteri selezionati.

2.  Nel riquadro Criteri scegliere **Assegnazioni** per aprire il riquadro **Protezione app di Intune - Assegnazioni** che visualizza l'elenco corrente dei gruppi di utenti che hanno questi criteri.

3.  Per aggiungere un nuovo gruppo di utenti ai criteri, nella scheda **Includi** scegliere **Selezionare i gruppi da includere** e selezionare il gruppo di utenti. Scegliere **Seleziona** per distribuire il criterio al gruppo selezionato.

4.  Per eliminare un gruppo di utenti, nella scheda **Escludi** scegliere **Selezionare i gruppi da escludere** e selezionare il gruppo di utenti. Scegliere **Seleziona** per rimuovere il gruppo di utenti.

### <a name="to-change-policy-settings"></a>Per modificare le impostazioni dei criteri

1.  Nel riquadro **Criteri di protezione delle app** scegliere i criteri da modificare per aprire un riquadro specifico per i criteri appena selezionati.

2.  Scegliere **Impostazioni criteri** per aprire il riquadro **Impostazioni criteri**.

3.  Modificare le impostazioni e quindi scegliere l'icona **Salva** per salvare le modifiche.

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Assegnare i criteri di protezione delle app in base allo stato di gestione del dispositivo
In molte organizzazioni è consuetudine consentire agli utenti finali di usare sia i dispositivi gestiti Intune Mobile Device Management (MDM), ad esempio i dispositivi di proprietà aziendale, sia i dispositivi non gestiti protetti solo con criteri di protezione delle app di Intune, ad esempio i dispositivi BYO.

Poiché i criteri di protezione delle app di Intune sono mirati all'identità di un utente, in genere le impostazioni di protezione per un utente vengono applicate sia ai dispositivi registrati (dispositivi MDM gestiti) sia ai dispositivi non registrati (non MDM). Pertanto, è possibile assegnare un criterio di protezione delle app di Intune sia a dispositivi Intune registrati sia a dispositivi non registrati iOS e Android. È possibile avere criteri di protezione per i dispositivi non gestiti, in cui vengono applicati severi controlli di prevenzione dalla perdita dei dati, e criteri di protezione dati separati per la gestione dei dispositivi MDM gestiti, in cui i controlli DLP possono essere leggermente più morbidi. 

Per creare questi criteri, passare a **App per dispositivi mobili** > **Criteri di protezione delle app** nella console di Intune e fare clic su **Aggiungi criteri**. È anche possibile modificare un criterio di protezione delle app esistente. Se si desidera che il criterio di protezione delle app venga applicato sia ai dispositivi gestiti che non gestiti, verificare che l'opzione **Includi tutti i tipi di app** sia impostata su **Sì**, il valore predefinito. Se si desidera assegnare i criteri in modo granulare sulla base dello stato di gestione, impostare l'opzione **Includi tutti i tipi di app** su **No**. 

Affinché le app iOS possano essere considerate "gestite", l'impostazione dei criteri di configurazione **IntuneMAMUPN** deve essere distribuita per ogni app. Per altre informazioni, vedere [Come gestire il trasferimento di dati tra app iOS in Microsoft Intune](https://docs.microsoft.com/en-us/intune/data-transfer-between-apps-manage-ios#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).

> [!NOTE]
> Per informazioni sul supporto iOS in merito ai criteri di protezione delle app sulla base dello stato di gestione del dispositivo, vedere [Criteri di protezione MAM mirati sulla base dello stato di gestione](whats-new.md#mam-protection-policies-targeted-based-on-management-state-).

## <a name="policy-settings"></a>Impostazioni criteri
Per visualizzare l'elenco completo delle impostazioni dei criteri per iOS e Android, selezionare uno dei collegamenti seguenti:

- [Criteri iOS](app-protection-policy-settings-ios.md)
- [Criteri Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Passaggi successivi
[Monitorare la conformità e lo stato utente](app-protection-policies-monitor.md)

### <a name="see-also"></a>Vedere anche
* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)
