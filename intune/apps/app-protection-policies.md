---
title: Creare e distribuire i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Questo argomento illustra come creare e assegnare criteri di protezione delle app di Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4958a35f3a83fecffacf26421e4c1d797f45ddaa
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940383"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Come creare e assegnare criteri di protezione delle app

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Informazioni su come creare e assegnare criteri di protezione delle app di Microsoft Intune agli utenti. In questo argomento viene anche descritto come apportare modifiche a criteri esistenti.

## <a name="before-you-begin"></a>Prima di iniziare

I criteri di protezione delle app possono essere applicati in app eseguite su dispositivi gestiti o non gestiti da Intune. Per una descrizione più dettagliata del funzionamento dei criteri di protezione delle app e degli scenari supportati dai criteri di protezione delle app di Intune, vedere [Che cosa sono i criteri di protezione delle app di Microsoft Intune?](app-protection-policy.md)

Per un elenco delle app supportate da MAM, vedere [Elenco di app MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Per informazioni sull'aggiunta di app line-of-business (LOB) dell'organizzazione in Microsoft Intune per preparare i criteri di protezione delle app, vedere [Aggiungere app in Microsoft Intune](apps-add.md).

## <a name="create-an-app-protection-policy"></a>Creare un criterio di protezione delle app
1. Nel portale di Intune passare ad **App client** > **Criteri di protezione delle app**. Questa selezione determina la visualizzazione dei dettagli dei **Criteri di protezione delle app**, in cui è possibile creare nuovi criteri e modificare i criteri esistenti.
2. Selezionare **Crea criterio**.

   ![Schermata del pannello "Aggiungi criteri"](./media/app-protection-policies/app-protection-add-policy.png)

3. Specificare un nome per il criterio, aggiungere una breve descrizione e selezionare il tipo di piattaforma per i criteri. È possibile creare più criteri per ogni piattaforma.

4. Selezionare **App** per aprire il pannello **App**, che contiene l'elenco delle app disponibili. Selezionare una o più app dall'elenco che si vuole associare al criterio che si sta creando. Selezionare almeno un'app per creare un criterio.  

5. Dopo aver selezionato le app, scegliere **Seleziona** per salvare la selezione.

6. Nel pannello **Aggiungi criteri** selezionare **Configura le impostazioni obbligatorie** per aprire **Impostazioni**.

   Sono tre le categorie di impostazioni dei criteri:
   - **Protezione dei dati**: questo gruppo include i controlli di prevenzione della perdita dei dati, ad esempio le restrizioni relative alle operazioni Taglia, Copia, Incolla e Salva con nome. Queste impostazioni determinano la modalità con cui gli utenti interagiscono con i dati nelle app.
   - **Requisiti di accesso**: questo gruppo contiene le opzioni PIN per ogni app che determinano in che modo l'utente finale accede alle app in un contesto aziendale.  
   - **Avvio condizionale**: questo gruppo contiene impostazioni come le impostazioni minime del sistema operativo, il rilevamento di jailbreak e dispositivi rooted e i periodi di prova offline.

   In questa introduzione le impostazioni dei criteri hanno valori predefiniti. Non è necessario apportare modifiche se i valori predefiniti soddisfano i requisiti.

   > [!TIP]
   > Queste impostazioni dei criteri vengono applicate solo quando si usano le app nel contesto aziendale. Quando gli utenti finali usano l'app per eseguire un'attività personale, questi criteri non hanno effetto. Si noti che ogni nuovo file creato viene considerato un file personale. 

7. Selezionare **OK** per salvare la configurazione. A questo punto ci si trova di nuovo nel riquadro **Aggiungi criteri**.
8. Selezionare **Crea** per creare i criteri e salvare le impostazioni.

I nuovi criteri creati non vengono distribuiti agli utenti finché non si esegue questa operazione in modo esplicito. Per distribuire un criterio, vedere [Distribuire un criterio agli utenti](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Distribuire un criterio agli utenti

1. Selezionare un criterio nel riquadro **Criteri di protezione delle app**.

2. Nel riquadro ***Protezione app di Intune** selezionare **Assegnazioni** per aprire il riquadro **Protezione app di Intune - Assegnazioni**. Nella scheda *Includi* selezionare **Selezionare i gruppi da includere**. 

   ![Schermata del riquadro Assegnazioni con il menu Selezionare i gruppi da includere](./media/app-protection-policies/app-protection-policy-add-users.png)

3. Viene visualizzato un elenco di tutti i gruppi di sicurezza in **Azure Active Directory**. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e quindi scegliere **Seleziona**. 

    ![Screenshot del riquadro Selezionare i gruppi da includere con un elenco di utenti Azure AD](./media/app-protection-policies/azure-ad-user-group-list.png)

4. Dopo aver incluso ed escluso gruppi, selezionare **Salva** per salvare la configurazione e distribuire i criteri agli utenti. Se si seleziona **Annulla** prima di salvare la configurazione, verranno eliminate tutte le modifiche apportate nelle schede *Includi* ed *Escludi*.   
 
     ![Screenshot che mostra le opzioni Salva e Annulla](./media/app-protection-policies/save-assignment.png)
  
A questo punto, l'utente ha creato un criterio e lo ha distribuito agli utenti.

Solo gli utenti a cui sono state assegnate licenze di Microsoft Intune sono interessati dai criteri. Gli utenti del gruppo di sicurezza selezionato a cui non è stata assegnata una licenza di Intune non sono interessati.

>[!IMPORTANT]
> Se si usa Intune con Configuration Manager per gestire i propri dispositivi, il criterio viene applicato solo agli utenti inclusi direttamente nel gruppo selezionato. I membri dei gruppi figlio annidati all'interno del gruppo selezionato non sono interessati.

Gli utenti finali possono scaricare le app dall'Apple Store o da Google Play. Per altre informazioni, vedere:
* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](../fundamentals/end-user-mam-apps-android.md)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>Modificare i criteri esistenti
È possibile modificare criteri esistenti e applicarli agli utenti di destinazione. Quando tuttavia si modificano criteri esistenti, gli utenti che hanno già effettuato l'accesso alle app non vedranno le modifiche per un intervallo di tempo di otto ore.

Per visualizzare immediatamente l'effetto delle modifiche, l'utente finale deve disconnettersi dall'app e quindi eseguire nuovamente l'accesso.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Per modificare l'elenco delle app associate al criterio

1. Nel riquadro **Criteri di protezione delle app** selezionare i criteri che si vuole modificare.

2. Nel riquadro *Protezione app di Intune* selezionare **App di destinazione** per aprire l'elenco di app.

3. Rimuovere o aggiungere app dall'elenco e quindi selezionare l'icona **Salva** per salvare le modifiche.

### <a name="to-change-the-list-of-user-groups"></a>Per modificare l'elenco dei gruppi di utenti


1. Nel riquadro **Criteri di protezione delle app** selezionare i criteri che si vuole modificare.

2. Nel riquadro *Protezione app di Intune* selezionare **Assegnazioni** per aprire il riquadro **Protezione app di Intune - Assegnazioni** che visualizza l'elenco corrente dei gruppi di utenti che hanno questi criteri.

3. Per aggiungere un nuovo gruppo di utenti ai criteri, nella scheda *Includi* scegliere **Selezionare i gruppi da includere** e selezionare il gruppo di utenti. Scegliere **Seleziona** per aggiungere il gruppo. 

4. Per escludere un gruppo di utenti, nella scheda *Escludi* scegliere **Selezionare i gruppi da escludere** e selezionare il gruppo di utenti. Scegliere **Seleziona** per rimuovere il gruppo di utenti.  

5. Per eliminare gruppi aggiunti in precedenza, nella scheda *Includi* o *Escludi* selezionare i puntini di sospensione (...) e selezionare **Elimina**. 

5. Quando le modifiche delle assegnazioni sono pronte, selezionare **Salva** per salvare la configurazione e distribuire i criteri al nuovo set di utenti. Se si seleziona **Annulla** prima di salvare la configurazione, verranno eliminate tutte le modifiche apportate nelle schede *Includi* ed *Escludi*.

### <a name="to-change-policy-settings"></a>Per modificare le impostazioni dei criteri

1. Nel riquadro **Criteri di protezione delle app** scegliere i criteri che si vuole modificare.

2. Nel riquadro *Protezione app di Intune* selezionare **Proprietà** per aprire l'elenco di aree di impostazioni che è possibile modificare. 

3. Selezionare l'area con le impostazioni che si vuole modificare, ad esempio **Rilocazione dei dati** o **Requisiti di accesso**, quindi configurare i nuovi valori per le impostazioni.

4. Selezionare l'icona **Salva** per salvare le modifiche. Ripetere il processo per selezionare un'area di impostazioni e apportare e quindi salvare le modifiche, fino al completamento di tutte le modifiche. È quindi possibile chiudere il riquadro *Protezione app di Intune - Proprietà*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Assegnare i criteri di protezione delle app in base allo stato di gestione del dispositivo
In molte organizzazioni è consuetudine consentire agli utenti finali di usare sia i dispositivi gestiti Intune Mobile Device Management (MDM), ad esempio i dispositivi di proprietà aziendale, sia i dispositivi non gestiti protetti solo con criteri di protezione delle app di Intune. I dispositivi non gestiti sono spesso noti come dispositivi Bring Your Own Device (BYOD).

Poiché i criteri di protezione delle app di Intune usano come destinazione l'identità di un utente, le impostazioni di protezione per un utente possono essere applicate sia ai dispositivi registrati (dispositivi MDM gestiti) che ai dispositivi non registrati (non MDM). È quindi possibile assegnare un criterio di protezione delle app di Intune sia a dispositivi Intune registrati che a dispositivi non registrati iOS e Android. È possibile avere criteri di protezione per dispositivi non gestiti, in cui vengono applicati severi controlli di prevenzione dalla perdita dei dati, e criteri di protezione dati separati per la gestione di dispositivi MDM gestiti, in cui i controlli DLP possono essere meno severi. Per altre informazioni sul funzionamento in dispositivi Android Enterprise personali, vedere [Criteri di protezione delle app e profili di lavoro](android-deployment-scenarios-app-protection-work-profiles.md).

Per creare questi criteri, passare a **App client** > **Criteri di protezione delle app** nella console di Intune e fare clic su **Crea criterio**. È anche possibile modificare un criterio di protezione delle app esistente. Per fare in modo che il criterio di protezione delle app venga applicato sia ai dispositivi gestiti che non gestiti, verificare che l'opzione **Includi tutti i tipi di app** sia impostata su **Sì**, il valore predefinito. Per assegnare i criteri in modo granulare sulla base dello stato di gestione, impostare **Includi tutti i tipi di app** su **No**. 

![Screenshot del pannello Aggiungi criteri con Includi tutti i tipi di app](./media/app-protection-policies/app-protection-policies-target-all.png)

### <a name="app-types"></a>Tipi di app

- **App nei dispositivi non gestiti**: i dispositivi non gestiti sono dispositivi in cui non è stata rilevata la gestione MDM di Intune. Sono inclusi i fornitori di MDM di terze parti.
- **App nei dispositivi gestiti da Intune**: i dispositivi gestiti sono gestiti dalla gestione di dispositivi mobili di Intune.
- **App nel profilo di lavoro di Android**: i dispositivi gestiti che sono stati registrati come dispositivi con il profilo di lavoro di Android Enterprise.

> Nota: i dispositivi Android richiederanno di installare l'app Portale aziendale Intune indipendentemente dal tipo di app scelta. Ad esempio, se si seleziona "App nei dispositivi gestiti di Intune", verranno comunque richiesti gli utenti con dispositivi Android non gestiti.

Per iOS, sono necessarie impostazioni di configurazione delle app aggiuntive per assegnare le impostazioni dei criteri di protezione delle app alle app nei dispositivi registrati in Intune:

- È necessario configurare **IntuneMAMUPN** per tutte le applicazioni gestite da MDM. Per altre informazioni, vedere [Come gestire il trasferimento di dati tra app iOS in Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- È necessario configurare **IntuneMAMDeviceID** per tutte le applicazioni gestite di terze parti e line-of-business. È necessario impostare **IntuneMAMDeviceID** sul token dell'ID del dispositivo. Ad esempio, `key=IntuneMAMDeviceID, value={{deviceID}}` Per altre informazioni, vedere [Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti](app-configuration-policies-use-ios.md).
- Se si configura solo **IntuneMAMDeviceID**, l'app di Intune considererà il dispositivo come non gestito.

> [!NOTE]
> Per informazioni sul supporto iOS in merito ai criteri di protezione delle app sulla base dello stato di gestione del dispositivo, vedere [Criteri di protezione MAM mirati sulla base dello stato di gestione](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-).

## <a name="policy-settings"></a>Impostazioni criteri
Per visualizzare l'elenco completo delle impostazioni dei criteri per iOS e Android, selezionare uno dei collegamenti seguenti:

- [Criteri iOS](app-protection-policy-settings-ios.md)
- [Criteri Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Passaggi successivi
[Monitorare la conformità e lo stato utente](app-protection-policies-monitor.md)

## <a name="see-also"></a>Vedere anche
* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](../fundamentals/end-user-mam-apps-android.md)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](../fundamentals/end-user-mam-apps-ios.md)