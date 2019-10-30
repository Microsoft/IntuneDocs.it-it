---
title: Creare e distribuire i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Questo argomento illustra come creare e assegnare criteri di protezione delle app di Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8e105dae43c4e7139c8e44a8c6535baebe31cc4
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585450"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Come creare e assegnare criteri di protezione delle app

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Informazioni su come creare e assegnare criteri di protezione delle app di Microsoft Intune per gli utenti dell'organizzazione. In questo argomento viene anche descritto come apportare modifiche a criteri esistenti.

## <a name="before-you-begin"></a>Prima di iniziare

I criteri di protezione delle app possono essere applicati in app eseguite su dispositivi gestiti o non gestiti da Intune. Per una descrizione più dettagliata del funzionamento dei criteri di protezione delle app e degli scenari supportati dai criteri di protezione delle app di Intune, vedere [Che cosa sono i criteri di protezione delle app di Microsoft Intune?](app-protection-policy.md)

Per un elenco delle app supportate da MAM, vedere [Elenco di app MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Per informazioni sull'aggiunta di app line-of-business (LOB) dell'organizzazione in Microsoft Intune per preparare i criteri di protezione delle app, vedere [Aggiungere app in Microsoft Intune](apps-add.md).

Attualmente, il flusso del processo per creare i criteri di protezione delle app è diverso a seconda della piattaforma:
- Criteri di protezione delle app per app iOS/iPadOS e Android
- Criteri di protezione delle app per app Windows 10

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>Criteri di protezione delle app per app iOS/iPadOS e Android

Quando si crea un criterio di protezione delle app per app iOS/iPadOS e Android, si segue un flusso di processo di Intune moderno che comporta la creazione di un nuovo criterio di protezione delle app.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>Creare un criterio di protezione delle app iOS/iPadOS o Android
1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Nel portale di Intune scegliere **App client** > **Criteri di protezione delle app**. Questa selezione determina la visualizzazione dei dettagli dei **Criteri di protezione delle app**, in cui è possibile creare nuovi criteri e modificare i criteri esistenti.
3. Selezionare **Crea criteri** e selezionare **iOS/iPadOS** o **Android**. Viene visualizzato il pannello **Crea criteri**.
4. Nella pagina **Informazioni di base** aggiungere i valori seguenti:

    | Valore | Descrizione |
    |--------------|------------------------------------------------|
    | Name | Nome dei criteri di protezione delle app. |
    | Descrizione | [Facoltativo] Descrizione dei criteri di protezione delle app. |


    Il valore **Piattaforma** viene impostato in base alla scelta effettuata in precedenza.

    ![Screenshot della pagina Informazioni di base del pannello Crea criteri](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Fare clic su **Avanti** per visualizzare la pagina **App**.<br>
    La pagina **App** consente di scegliere come applicare questo criterio alle app su dispositivi diversi. È necessario aggiungere almeno un'app.<p>
    
    | Valore/opzione | Descrizione |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Specifica come destinatari le app in tutti i tipi di dispositivo | Usare questa opzione per destinare i criteri alle app nei dispositivi con qualsiasi stato di gestione. Scegliere **No** per destinare i criteri ad app su tipi di dispositivi specifici. |
    |     Tipi di dispositivi | Usare questa opzione per specificare se i criteri di applicano ai dispositivi gestiti MDM o ai dispositivi non gestiti. Per i criteri di protezione delle app iOS selezionare **Non gestito** o **Gestito** per i dispositivi. Per i criteri di protezione delle app Android selezionare **Non gestito**, **Amministratore di dispositivi Android** e **Android Enterprise**.  |
    | App pubbliche | Fare clic su **Select public apps** (Selezionare le app pubbliche) per scegliere le app di destinazione. |
    | App personalizzate | Fare clic su **Select custom apps** (Selezionare le app personalizzate) per selezionare le app personalizzate di destinazione in base a un ID di bundle. |
    
    Le app selezionate verranno visualizzate nell'elenco delle app pubbliche e personalizzate. 
6. Fare clic su **Avanti** per visualizzare la pagina **Protezione dei dati**.<br>
    Questa pagina fornisce le impostazioni per i controlli di prevenzione della perdita dei dati (DLP), incluse le limitazioni per le operazioni Taglia, Copia, Incolla e Salva con nome. Queste impostazioni determinano il modo in cui gli utenti interagiscono con i dati nelle app a cui vengono applicati questi criteri di protezione delle app.

    **Impostazioni di protezione dati**:<br>
    - **Protezione dati iOS/iPadOS** - Per informazioni, vedere [Impostazioni dei criteri di protezione delle app per iOS - Protezione dati](~/apps/app-protection-policy-settings-ios.md#data-protection).
    - **Protezione dati Android** - Per informazioni, vedere [Impostazioni dei criteri di protezione delle app per Android - Protezione dati](~/apps/app-protection-policy-settings-android.md#data-protection).

7. Fare clic su **Avanti** per visualizzare la pagina **Requisiti di accesso**.<br>
    Questa pagina fornisce le impostazioni che consentono di configurare i requisiti di PIN e credenziali che gli utenti devono soddisfare per accedere alle app in un contesto aziendale. 
 
    **Impostazioni dei requisiti di accesso**:<br>
    - **Requisiti di accesso per iOS/iPadOS** - Per informazioni, vedere [Impostazioni dei criteri di protezione delle app per iOS - Requisiti di accesso](~/apps/app-protection-policy-settings-ios.md#access-requirements).
    - **Requisiti di accesso per Android** - Per informazioni, vedere [Impostazioni dei criteri di protezione delle app per Android - Requisiti di accesso](~/apps/app-protection-policy-settings-android.md#access-requirements).

8. Fare clic su **Avanti** per visualizzare la pagina **Avvio condizionale**.<br>
    Questa pagina fornisce le impostazioni per impostare i requisiti di sicurezza per l'accesso per i criteri di protezione delle app. Selezionare una **impostazione** e immettere il **valore** che gli utenti devono soddisfare per accedere all'app aziendale. Selezionare l'**azione** da intraprendere se gli utenti non soddisfano i requisiti. In alcuni casi è possibile configurare più azioni per una singola impostazione.

    **Impostazioni di avvio condizionale**:<br>
    - **Avvio condizionale per iOS/iPadOS** - Per informazioni, vedere [Impostazioni dei criteri di protezione delle app per iOS - Avvio condizionale](~/apps/app-protection-policy-settings-ios.md#conditional-launch).
    - **Avvio condizionale per Android** - Per informazioni, vedere [Impostazioni dei criteri di protezione delle app per Android - Avvio condizionale](~/apps/app-protection-policy-settings-android.md#conditional-launch).

7. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.<br>
   La pagina **Assegnazioni** consente di assegnare i criteri di protezione delle app a gruppi di utenti. 
8. Fare clic su **Avanti: Rivedi e crea** per esaminare i valori e le impostazioni immessi per i criteri di protezione delle app.
9. Al termine, fare clic su **Crea** per creare i criteri di protezione delle app in Intune. 

## <a name="app-protection-policies-for-windows-10-apps"></a>Criteri di protezione delle app per app Windows 10

Per la creazione dei criteri di protezione delle app per le app Windows 10 si seguirà un flusso di processo di Intune classico.

### <a name="create-a-windows-10-app-protection-policy"></a>Creare criteri di protezione delle app per Windows 10
1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Nel portale di Intune scegliere **App client** > **Criteri di protezione delle app**. Questa selezione determina la visualizzazione dei dettagli dei **Criteri di protezione delle app**, in cui è possibile creare nuovi criteri e modificare i criteri esistenti.
3. Selezionare **Crea criterio**.

    <img alt="Screenshot of the 'Create policy' blade for Windows 10" src="~/apps/media/app-protection-policies/app-protection-add-policy.png" width="350">

4. Specificare un nome per il criterio, aggiungere una breve descrizione e selezionare il tipo di piattaforma per i criteri. È possibile creare più criteri per ogni piattaforma.

4. È possibile scegliere **Includi tutti i tipi di app**. Questa opzione consente di destinare i criteri alle app nei dispositivi con qualsiasi stato di gestione. Durante la risoluzione dei conflitti tra criteri, questa impostazione verrà sostituita se un utente dispone di criteri destinati a uno stato di gestione specifico. Per altre informazioni, vedere [Target app protection policies based on device management state](~/apps/app-protection-policies.md#target-app-protection-policies-based-on-device-management-state) (Assegnare i criteri di protezione delle app in base allo stato di gestione del dispositivo).

5. Selezionare **App** per aprire il pannello **App**, che contiene l'elenco delle app disponibili. Selezionare una o più app dall'elenco che si vuole associare al criterio che si sta creando. Selezionare almeno un'app per creare un criterio.  

6. Dopo aver selezionato le app, scegliere **Seleziona** per salvare la selezione.

7. Nel pannello **Aggiungi criteri** selezionare **Configura le impostazioni obbligatorie** per aprire **Impostazioni**.

   Sono tre le categorie di impostazioni dei criteri:
   - **Protezione dei dati**: questo gruppo include i controlli di prevenzione della perdita dei dati, ad esempio le restrizioni relative alle operazioni Taglia, Copia, Incolla e Salva con nome. Queste impostazioni determinano la modalità con cui gli utenti interagiscono con i dati nelle app.
   - **Requisiti di accesso**: questo gruppo contiene le opzioni PIN per ogni app che determinano in che modo l'utente finale accede alle app in un contesto aziendale.  
   - **Avvio condizionale**: questo gruppo contiene impostazioni come le impostazioni minime del sistema operativo, il rilevamento di jailbreak e dispositivi rooted e i periodi di prova offline.

   In questa introduzione le impostazioni dei criteri hanno valori predefiniti. Non è necessario apportare modifiche se i valori predefiniti soddisfano i requisiti.

   > [!TIP]
   > Queste impostazioni dei criteri vengono applicate solo quando si usano le app nel contesto aziendale. Quando gli utenti finali usano l'app per eseguire un'attività personale, questi criteri non hanno effetto. Si noti che ogni nuovo file creato viene considerato un file personale. 

8. Selezionare **OK** per salvare la configurazione. A questo punto ci si trova di nuovo nel riquadro **Aggiungi criteri**.
9. Selezionare **Crea** per creare i criteri e salvare le impostazioni.

I nuovi criteri per Windows 10 creati non vengono assegnati ad alcun utente fino a quando non si procede in modo esplicito all'assegnazione. Per assegnare criteri di Windows 10, vedere [Assegnare criteri di Windows 10 agli utenti](~/apps/app-protection-policies.md#assign-a-windows-10-policy-to-users)

### <a name="assign-a-windows-10-policy-to-users"></a>Assegnare criteri di Windows 10 agli utenti 

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

### <a name="change-existing-windows-10-policies"></a>Modificare criteri esistenti di Windows 10
È possibile modificare criteri esistenti e applicarli agli utenti di destinazione. Quando tuttavia si modificano criteri esistenti, gli utenti che hanno già effettuato l'accesso alle app non vedranno le modifiche per un intervallo di tempo di otto ore.

Per visualizzare immediatamente l'effetto delle modifiche, l'utente finale deve disconnettersi dall'app e quindi eseguire nuovamente l'accesso.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Per modificare l'elenco delle app associate al criterio

1. Nel riquadro **Criteri di protezione delle app** selezionare i criteri che si vuole modificare.

2. Nel riquadro *Protezione app di Intune* selezionare **App di destinazione** per aprire l'elenco di app.

3. Rimuovere o aggiungere app dall'elenco e quindi selezionare l'icona **Salva** per salvare le modifiche.

#### <a name="to-change-the-list-of-user-groups"></a>Per modificare l'elenco dei gruppi di utenti

1. Nel riquadro **Criteri di protezione delle app** selezionare i criteri che si vuole modificare.

2. Nel riquadro *Protezione app di Intune* selezionare **Assegnazioni** per aprire il riquadro **Protezione app di Intune - Assegnazioni** che visualizza l'elenco corrente dei gruppi di utenti che hanno questi criteri.

3. Per aggiungere un nuovo gruppo di utenti ai criteri, nella scheda *Includi* scegliere **Selezionare i gruppi da includere** e selezionare il gruppo di utenti. Scegliere **Seleziona** per aggiungere il gruppo. 

4. Per escludere un gruppo di utenti, nella scheda *Escludi* scegliere **Selezionare i gruppi da escludere** e selezionare il gruppo di utenti. Scegliere **Seleziona** per rimuovere il gruppo di utenti.  

5. Per eliminare gruppi aggiunti in precedenza, nella scheda *Includi* o *Escludi* selezionare i puntini di sospensione (...) e selezionare **Elimina**. 

5. Quando le modifiche delle assegnazioni sono pronte, selezionare **Salva** per salvare la configurazione e distribuire i criteri al nuovo set di utenti. Se si seleziona **Annulla** prima di salvare la configurazione, verranno eliminate tutte le modifiche apportate nelle schede *Includi* ed *Escludi*.

### <a name="to-change-windows-10-policy-settings"></a>Per modificare le impostazioni dei criteri di Windows 10

1. Nel riquadro **Criteri di protezione delle app** scegliere i criteri che si vuole modificare.

2. Nel riquadro *Protezione app di Intune* selezionare **Proprietà** per aprire l'elenco di aree di impostazioni che è possibile modificare. 

3. Selezionare l'area con le impostazioni che si vuole modificare, ad esempio **Rilocazione dei dati** o **Requisiti di accesso**, quindi configurare i nuovi valori per le impostazioni.

4. Selezionare l'icona **Salva** per salvare le modifiche. Ripetere il processo per selezionare un'area di impostazioni e apportare e quindi salvare le modifiche, fino al completamento di tutte le modifiche. È quindi possibile chiudere il riquadro *Protezione app di Intune - Proprietà*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Assegnare i criteri di protezione delle app in base allo stato di gestione del dispositivo
In molte organizzazioni è consuetudine consentire agli utenti finali di usare sia i dispositivi gestiti Intune Mobile Device Management (MDM), ad esempio i dispositivi di proprietà aziendale, sia i dispositivi non gestiti protetti solo con criteri di protezione delle app di Intune. I dispositivi non gestiti sono spesso noti come dispositivi Bring Your Own Device (BYOD).

Poiché i criteri di protezione delle app di Intune usano come destinazione l'identità di un utente, le impostazioni di protezione per un utente possono essere applicate sia ai dispositivi registrati (dispositivi MDM gestiti) che ai dispositivi non registrati (non MDM). È quindi possibile assegnare un criterio di protezione delle app di Intune sia a dispositivi Intune registrati che a dispositivi non registrati iOS e Android. È possibile avere criteri di protezione per dispositivi non gestiti, in cui vengono applicati severi controlli di prevenzione dalla perdita dei dati, e criteri di protezione dati separati per la gestione di dispositivi MDM gestiti, in cui i controlli DLP possono essere meno severi. Per altre informazioni sul funzionamento in dispositivi Android Enterprise personali, vedere [Criteri di protezione delle app e profili di lavoro](android-deployment-scenarios-app-protection-work-profiles.md).

Per creare questi criteri, passare a **App client** > **Criteri di protezione delle app** nella console di Intune e fare clic su **Crea criterio**. È anche possibile modificare un criterio di protezione delle app esistente. Per fare in modo che i criteri di protezione delle app vengano applicati sia ai dispositivi gestiti che non gestiti, passare alla pagina **App** e verificare che l'opzione **Specifica come destinatari le app in tutti i tipi di dispositivo** sia impostata su **Sì**, ovvero il valore predefinito. Per assegnare i criteri in modo granulare sulla base dello stato di gestione, impostare **Specifica come destinatari le app in tutti i tipi di dispositivo** su **No**. 

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
