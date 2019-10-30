---
title: Configurare i criteri di aggiornamento software per iOS in Microsoft Intune - Azure | Microsoft Docs
description: In Microsoft Intune è possibile creare o aggiungere criteri di configurazione per limitare l'installazione automatica di aggiornamenti software nei dispositivi iOS. È possibile scegliere la data e ora in cui l'installazione degli aggiornamenti non verrà effettuata. È anche possibile assegnare questi criteri a gruppi, utenti o dispositivi e verificare la presenza di eventuali errori di installazione.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ada1f6e5292684803fbea40430cdd43d61796746
ms.sourcegitcommit: 1a5b185acd27954b10b6d59409d82eb80fd71284
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72681349"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Aggiungere criteri di aggiornamento software per iOS in Intune

I criteri di aggiornamento software consentono di forzare l'installazione automatica dell'aggiornamento del sistema operativo più recente disponibile nei dispositivi iOS con supervisione. Quando si configurano criteri, è possibile aggiungere i giorni e gli orari in cui si vuole che i dispositivi non installino aggiornamenti.

Questa funzionalità si applica a:

- iOS 10.3 e versioni successive (con supervisione)

Il dispositivo si collega a Intune ogni 8 ore. Se è disponibile un aggiornamento, il dispositivo lo scarica e lo installa, eccetto durante i periodi limitati. Non è necessario alcun intervento dell'utente per aggiornare il dispositivo. I criteri non impediscono a un utente di aggiornare manualmente il sistema operativo.

## <a name="configure-the-policy"></a>Configurare i criteri

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Aggiornamenti software** > **Criteri di aggiornamento per iOS** > **Crea**.
3. Nella scheda **Informazioni di base** specificare un nome per il criterio, specificare una descrizione (facoltativa) e quindi selezionare **Avanti**.

   ![Scheda Informazioni di base](./media/software-updates-ios/basics-tab.png) 

4. Nella scheda **Aggiorna le impostazioni del criterio** specificare un intervallo di tempo limitato durante il quale non deve essere forzata l'installazione degli aggiornamenti.  
   - I blocchi nelle ore notturne non sono supportati e potrebbero non funzionare. Ad esempio, non configurare un criterio con *Ora di inizio* alle 20.00 e *Ora di fine* alle 6.00.
   - Un criterio che inizia a alle 00.00 e termina alle 00.00 viene valutato come 0 ore e non 24 ore. Questa configurazione non comporta alcuna restrizione.

   Nell'impostare l'intervallo di tempo limitato, immettere i dettagli seguenti:

   - **Giorni**: scegliere il giorno o i giorni della settimana in cui gli aggiornamenti non vengono installati. Ad esempio, selezionare Lunedì, Mercoledì e Venerdì per impedire l'installazione degli aggiornamenti in questi giorni.
   - **Fuso orario**: scegliere un fuso orario.
   - **Ora di inizio**: scegliere l'ora di inizio dell'intervallo di tempo limitato. Ad esempio, immettere 5.00 in modo che gli aggiornamenti non vengano installati a partire dalle 5.00.
   - **Ora di fine**: scegliere l'ora di fine dell'intervallo di tempo limitato. Ad esempio, immettere 1.00 in modo che gli aggiornamenti possano essere installati a partire dall'1.00.
  
   > [!IMPORTANT]  
   > Un criterio i cui valori per *Ora di inizio* e *Ora di fine* sono impostati sulle 00.00 viene valutato come 0 ore e non 24 ore. Questo significa nessuna limitazione.  
    
   Per ritardare la visibilità degli aggiornamenti software per un periodo di tempo specifico nei dispositivi iOS con supervisione, configurare queste impostazioni in [Limitazioni del dispositivo](../configuration/device-restrictions-ios.md#general). I criteri di aggiornamento software sostituiscono tutte le restrizioni dei dispositivi. Quando si impostano criteri di aggiornamento software e limitazioni per ritardare la visibilità degli aggiornamenti software, il dispositivo forza un aggiornamento software in base ai criteri. La limitazione si applica in modo che gli utenti non vedano l'opzione per aggiornare il dispositivo autonomamente e viene eseguito il push dell'aggiornamento in occasione del primo intervallo utile in base a quanto definito dai criteri di aggiornamento di iOS.

   Dopo aver configurato *Aggiorna le impostazioni del criterio*, selezionare **Avanti**. 

5. Nella scheda **Tag di ambito** selezionare **+ Selezionare i tag di ambito** per aprire il riquadro *Selezionare i tag* per applicarli ai criteri di aggiornamento.
   
   - Nel riquadro **Selezionare i tag** scegliere uno o più tag, quindi fare clic su **Seleziona** per aggiungerli ai criteri e tornare al riquadro *Tag di ambito*.  

   Quando si è pronti, selezionare **Avanti** per procedere ad *Assegnazioni*.

6. Nella scheda **Assegnazioni** scegliere **+ Selezionare i gruppi da includere** e quindi assegnare i criteri di aggiornamento a uno o più gruppi. Usare **+ Selezionare i gruppi da escludere** per mettere a punto l'assegnazione. Quando si è pronti selezionare **Avanti** per continuare. 

   I dispositivi usati dagli utenti a cui sono destinati i criteri vengono valutati per la conformità degli aggiornamenti. Questo criterio supporta anche i dispositivi senza utente.

7. Nella scheda **Rivedi e crea** esaminare le impostazioni e quindi selezionare **Crea** quando si è pronti per salvare i criteri di aggiornamento per iOS. I nuovi criteri vengono visualizzati nell'elenco dei criteri di aggiornamento per iOS.


Per indicazioni a cura del team di supporto di Intune, vedere [Ritardare la visibilità degli aggiornamenti software in Intune per i dispositivi con supervisione](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Il software MDM di Apple non consente di imporre a un dispositivo di installare gli aggiornamenti entro un'ora o data determinata.

## <a name="edit-a-policy"></a>Modificare un criterio
È possibile modificare un criterio esistente, inclusa la modifica delle limitazione di orario:

1. In **Aggiornamenti software** selezionare **Criteri di aggiornamento per iOS** e quindi selezionare i criteri da modificare.

2. Nella visualizzazione delle **Proprietà** dei criteri selezionare **Modifica** per la pagina dei criteri che si vuole modificare.  
   ![Modificare criteri](./media/software-updates-ios/edit-policy.png)   

3. Dopo aver introdotto una modifica, selezionare **Verifica e salva** > **Salva** per salvare le modifiche e tornare alle *Proprietà* dei criteri.  
 
> [!NOTE]
> Se i valori per **Ora di inizio** e **Ora di fine** sono entrambi impostati sulle 00.00, Intune non controlla le limitazioni riguardo a quando installare gli aggiornamenti. Questo significa che tutte le configurazioni per **Selezionare gli orari per impedire le installazioni di aggiornamenti** vengono ignorate e gli aggiornamenti possono essere installati in qualunque momento.  


## <a name="monitor-device-installation-failures"></a>Monitorare gli errori di installazione nei dispositivi
<!-- 1352223 -->
**Aggiornamenti software** > **Errori di installazione per dispositivi iOS** mostra un elenco di dispositivi con supervisione per cui è stato impostato un criterio di aggiornamento, è stato tentato un aggiornamento e non è stato possibile eseguirlo. Per ogni dispositivo, è possibile visualizzare il motivo per cui l'aggiornamento automatico non è riuscito. I dispositivi integri e aggiornati non vengono visualizzati nell'elenco. Un dispositivo è aggiornato se include l'ultimo aggiornamento supportato dal dispositivo stesso.

## <a name="next-steps"></a>Passaggi successivi

[Monitorare lo stato](../configuration/device-profile-monitor.md).
