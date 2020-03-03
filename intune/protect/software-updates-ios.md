---
title: Configurare i criteri di aggiornamento software per iOS/iPadOS in Microsoft Intune - Azure | Microsoft Docs
description: In Microsoft Intune è possibile creare o aggiungere criteri di configurazione per limitare l'installazione automatica di aggiornamenti software nei dispositivi iOS/iPadOS. È possibile scegliere la data e ora in cui l'installazione degli aggiornamenti non verrà effettuata. È anche possibile assegnare questi criteri a gruppi, utenti o dispositivi e verificare la presenza di eventuali errori di installazione.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77d4a90bb2eaa8434ff9c05362dcb0d7cb270651
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576161"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>Aggiungere criteri di aggiornamento software per iOS/iPadOS in Intune

I criteri di aggiornamento software consentono di forzare l'installazione automatica degli aggiornamenti del sistema operativo nei dispositivi iOS/iPadOS con supervisione. I dispositivi con supervisione sono quelli registrati tramite Apple Business Manager o Apple School Manager. Quando si configurano i criteri per la distribuzione degli aggiornamenti, è possibile:

- Scegliere di distribuire l'*aggiornamento più recente* disponibile oppure scegliere di distribuire un aggiornamento precedente in base al numero di versione dell'aggiornamento se non si vuole distribuire l'aggiornamento più recente. Se si sceglie di distribuire un aggiornamento precedente, è necessario impostare anche un criterio di configurazione del dispositivo per limitare la visibilità degli aggiornamenti software.
- Specificare una pianificazione che determini quando installare l'aggiornamento. Una pianificazione prevede semplicemente l'installazione degli aggiornamenti alla sincronizzazione successiva del dispositivo o la creazione di intervalli di data e ora durante i quali è possibile installare gli aggiornamenti o impedirne l'installazione.

Questa funzionalità si applica a:

- iOS 10.3 e versioni successive (con supervisione)

Per impostazione predefinita, i dispositivi si collegano a Intune ogni 8 ore. Se è disponibile un aggiornamento tramite un criterio di aggiornamento, il dispositivo lo scarica. Il dispositivo installa quindi l'aggiornamento alla sincronizzazione successiva nell'ambito della configurazione della pianificazione. Anche se in genere il processo di aggiornamento non richiede alcuna interazione con l'utente, se il dispositivo ha un passcode l'utente deve immetterlo per poter avviare un aggiornamento software. I profili non impediscono agli utenti di aggiornare manualmente il sistema operativo. È possibile impedire agli utenti di aggiornare manualmente il sistema operativo con un criterio di configurazione del dispositivo per limitare la visibilità degli aggiornamenti software.

## <a name="configure-the-policy"></a>Configurare i criteri

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Criteri di aggiornamento per iOS/iPadOS** > **Crea profilo**.
3. Nella scheda **Informazioni di base** specificare un nome per il criterio, specificare una descrizione (facoltativa) e quindi selezionare **Avanti**.

   ![Scheda Informazioni di base](./media/software-updates-ios/basics-tab.png)

4. Nella scheda **Aggiorna le impostazioni del criterio** configurare quanto segue:

   1. **Selezionare la versione da installare**. È possibile scegliere tra:

      - *Aggiornamento più recente*: questa opzione consente di distribuire l'aggiornamento rilasciato più recentemente per iOS/iPadOS.
      - Qualsiasi versione precedente disponibile nella casella a discesa. Se si seleziona una versione precedente, è anche necessario distribuire un criterio di configurazione del dispositivo per posticipare la visibilità degli aggiornamenti software.

   2. **Tipo di pianificazione**: configurare la pianificazione per questo criterio:

      - *Aggiorna alla sincronizzazione successiva*: l'aggiornamento viene installato nel dispositivo alla sincronizzazione successiva con Intune. Questa è l'opzione più semplice e non ha configurazioni aggiuntive.
      - *Aggiorna durante l'orario pianificato*: è possibile configurare uno o più intervalli temporali durante i quali l'aggiornamento verrà installato in seguito alla sincronizzazione.
      - *Aggiorna in orari diversi da quello pianificato*: è possibile configurare uno o più intervalli temporali durante i quali gli aggiornamenti non verranno installati in seguito alla sincronizzazione.

   3. **Pianificazione settimanale**: se si sceglie un tipo di pianificazione diverso da *Aggiorna alla sincronizzazione successiva*, configurare le opzioni seguenti:

      ![Esempio di selezione per l'aggiornamento durante l'orario pianificato](./media/software-updates-ios/scheduled-time.png)

      - **Fuso orario**: scegliere un fuso orario.
      - **Intervallo di tempo**: definire uno o più blocchi temporali che limitano il periodo di installazione degli aggiornamenti. L'effetto delle opzioni seguenti dipende dal tipo di pianificazione selezionato. Se si usano un giorno di inizio e un giorno di fine, sono supportati i blocchi nelle ore notturne. Le opzioni includono:

        - **Giorno di inizio**: scegliere il giorno in cui parte la finestra di pianificazione.
        - **Ora di inizio**: scegliere l'ora del giorno in cui inizia la finestra di pianificazione. Se ad esempio si seleziona 5:00 e il tipo di pianificazione è *Aggiorna durante l'orario pianificato*, sarà possibile iniziare l'installazione degli aggiornamenti alle 5:00. Se si sceglie il tipo di pianificazione *Aggiorna in orari diversi da quello pianificato*, il periodo di tempo in cui non è possibile installare gli aggiornamenti avrà inizio alle 5:00.
        - **Giorno di fine**: scegliere il giorno in cui termina la finestra di pianificazione.
        - **Ora di fine**: scegliere l'ora del giorno in cui si arresta la finestra di pianificazione. Se ad esempio si seleziona 1:00 e il tipo di pianificazione è *Aggiorna durante l'orario pianificato*, alla 1:00 non sarà più sarà possibile installare gli aggiornamenti. Se si sceglie il tipo di pianificazione *Aggiorna in orari diversi da quello pianificato*, il periodo di tempo in cui è possibile installare gli aggiornamenti avrà inizio alla 1:00.

       Se non si configura l'ora di inizio o di fine, la configurazione non comporta alcuna restrizione e gli aggiornamenti possono essere installati in qualsiasi momento.  

       > [!NOTE]
       > Per ritardare la visibilità degli aggiornamenti software per un periodo di tempo specifico nei dispositivi iOS/iPadOS con supervisione, configurare queste impostazioni in [Limitazioni del dispositivo](../configuration/device-restrictions-ios.md#general). I criteri di aggiornamento software sostituiscono tutte le restrizioni dei dispositivi. Quando si impostano criteri di aggiornamento software e limitazioni per ritardare la visibilità degli aggiornamenti software, il dispositivo forza un aggiornamento software in base ai criteri. La limitazione si applica in modo che gli utenti non vedano l'opzione per aggiornare il dispositivo autonomamente e viene eseguito il push dell'aggiornamento in base a quanto definito dai criteri di aggiornamento di iOS.

   Dopo aver configurato *Aggiorna le impostazioni del criterio*, selezionare **Avanti**.

5. Nella scheda **Tag di ambito** selezionare **+ Selezionare i tag di ambito** per aprire il riquadro *Selezionare i tag* per applicarli ai criteri di aggiornamento.

   - Nel riquadro **Selezionare i tag** scegliere uno o più tag, quindi fare clic su **Seleziona** per aggiungerli ai criteri e tornare al riquadro *Tag di ambito*.

   Quando si è pronti, selezionare **Avanti** per procedere ad *Assegnazioni*.

6. Nella scheda **Assegnazioni** scegliere **+ Selezionare i gruppi da includere** e quindi assegnare i criteri di aggiornamento a uno o più gruppi. Usare **+ Selezionare i gruppi da escludere** per mettere a punto l'assegnazione. Quando si è pronti selezionare **Avanti** per continuare.

   I dispositivi usati dagli utenti a cui sono destinati i criteri vengono valutati per la conformità degli aggiornamenti. Questo criterio supporta anche i dispositivi senza utente.

7. Nella scheda **Rivedi e crea** esaminare le impostazioni e quindi selezionare **Crea** quando si è pronti per salvare i criteri di aggiornamento per iOS/iPadOS. I nuovi criteri vengono visualizzati nell'elenco dei criteri di aggiornamento per iOS/iPadOS.

Per indicazioni a cura del team di supporto di Intune, vedere [Ritardare la visibilità degli aggiornamenti software in Intune per i dispositivi con supervisione](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Il software MDM di Apple non consente di imporre a un dispositivo di installare gli aggiornamenti entro un'ora o data determinata. Non è possibile usare i criteri di aggiornamento software di Intune per effettuare il downgrade della versione del sistema operativo in un dispositivo.

## <a name="edit-a-policy"></a>Modificare un criterio

È possibile modificare un criterio esistente, inclusa la modifica delle limitazione di orario:

1. Selezionare **Dispositivi** > **Criteri di aggiornamento per iOS**. Selezionare il criterio da modificare.

2. Nella visualizzazione delle **Proprietà** dei criteri selezionare **Modifica** per la pagina dei criteri che si vuole modificare.

   ![Modificare un criterio](./media/software-updates-ios/edit-policy.png)

3. Dopo aver introdotto una modifica, selezionare **Verifica e salva** > **Salva** per salvare le modifiche e tornare alle *Proprietà* dei criteri.

> [!NOTE]
> Se i valori per **Ora di inizio** e **Ora di fine** sono entrambi impostati sulle 00.00, Intune non controlla le limitazioni riguardo a quando installare gli aggiornamenti. Questo significa che tutte le configurazioni per **Selezionare gli orari per impedire le installazioni di aggiornamenti** vengono ignorate e gli aggiornamenti possono essere installati in qualunque momento.

## <a name="monitor-device-installation-failures"></a>Monitorare gli errori di installazione nei dispositivi

<!-- 1352223 -->
**Aggiornamenti software** > **Errori di installazione per dispositivi iOS** mostra un elenco di dispositivi iOS/iPadOS con supervisione per cui è stato impostato un criterio di aggiornamento, è stato tentato un aggiornamento e non è stato possibile eseguirlo. Per ogni dispositivo, è possibile visualizzare il motivo per cui l'aggiornamento automatico non è riuscito. I dispositivi integri e aggiornati non vengono visualizzati nell'elenco. Un dispositivo è aggiornato se include l'ultimo aggiornamento supportato dal dispositivo stesso.

## <a name="next-steps"></a>Passaggi successivi

[Monitorare lo stato](../configuration/device-profile-monitor.md).
