---
title: Inviare notifiche personalizzate agli utenti con Microsoft Intune
titleSuffix: Microsoft Intune
description: Usare Intune per creare e inviare notifiche push agli utenti dei dispositivi iOS/iPadOS e Android
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5195ee83efb68cea061e69f5cad49e9d43458450
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609364"
---
# <a name="send-custom-notifications-in-intune"></a>Inviare notifiche personalizzate in Intune  

Usare Microsoft Intune per inviare notifiche personalizzate agli utenti dei dispositivi iOS/iPadOS e Android gestiti. Questi messaggi vengono visualizzati come notifiche push standard dall'app Portale aziendale e dall'app Microsoft Intune sul dispositivo di un utente nello stesso modo in cui vengono visualizzate sul dispositivo le notifiche provenienti da altre applicazioni. Le notifiche personalizzate di Intune non sono supportate dai dispositivi macOS e Windows.   

I messaggi di notifica personalizzati includono un titolo breve e un corpo del messaggio al massimo di 500 caratteri. Questi messaggi possono essere personalizzati per qualsiasi scopo di comunicazione generale.

### <a name="what-the-notification-looks-like-on-an-iosipados-device"></a>Visualizzazione della notifica in un dispositivo iOS/iPadOS

Se l'app Portale aziendale è aperta in un dispositivo iOS/iPadOS, la notifica sarà simile allo screenshot seguente:

> [!div class="mx-imgBorder"]
> ![Notifica di prova di Portale aziendale in iOS/iPadOS](./media/custom-notifications/105046-1.png)

Se il dispositivo è bloccato, la notifica ha il seguente aspetto:

> [!div class="mx-imgBorder"]
> ![Notifica di prova per dispositivo bloccato in iOS/iPadOS](./media/custom-notifications/105046-2.png)

### <a name="what-the-notification-looks-like-on-an-android-device"></a>Come appare la notifica in un dispositivo Android

Se l'app Portale aziendale è aperta in un dispositivo Android, la notifica sarà simile alla schermata seguente:

> [!div class="mx-imgBorder"]
> ![Notifica di prova in Android](./media/custom-notifications/105046-3.png)

## <a name="common-scenarios-for-sending-custom-notifications"></a>Scenari comuni per l'invio di notifiche personalizzate  

- Informare tutti i dipendenti di un cambiamento della programmazione, ad esempio di una chiusura degli edifici a causa del maltempo.
- Inviare una notifica all'utente di un singolo dispositivo per comunicare una richiesta urgente, ad esempio il riavvio del dispositivo per completare l'installazione di un aggiornamento.

## <a name="considerations-for-using-custom-notifications"></a>Considerazioni sull'uso delle notifiche personalizzate

**Configurazione del dispositivo**

- Prima che gli utenti possano ricevere notifiche personalizzate, è necessario che nei dispositivi sia installata l'app Portale aziendale o l'app Microsoft Intune. È anche necessario che siano configurate le autorizzazioni per consentire all'app Portale aziendale o all'app Microsoft Intune di inviare notifiche push. Se necessario, l'app Portale aziendale e l'app Microsoft Intune possono richiedere agli utenti di consentire le notifiche.
- In Android Google Play Services è una dipendenza obbligatoria.
- Il dispositivo deve disporre della registrazione a MDM.

**Autorizzazioni**:

- Per inviare le notifiche ai gruppi, l'account deve avere l'autorizzazione RBAC seguente in Intune: *Organizzazione* > **Aggiorna**.
- Per inviare le notifiche a un dispositivo, l'account deve avere l'autorizzazione RBAC seguente in Intune: *Attività remote* > **Invia notifiche personalizzate**.

**Creazione delle notifiche**:
 
- Per creare un messaggio, usare un account a cui è assegnato un ruolo di Intune che include l'autorizzazione corretta, come descritto nella sezione *Autorizzazioni* precedente. Per assegnare autorizzazioni a un utente, vedere [Assegnazioni di ruolo](../fundamentals/role-based-access-control.md#role-assignments).
- Le notifiche personalizzate sono limitate a titoli di 50 caratteri e messaggi di 500 caratteri.  
- Intune non salva il testo delle notifiche personalizzate inviate in precedenza. Per inviare nuovamente un messaggio, è necessario crearlo di nuovo.  
- È possibile inviare ai gruppi al massimo 25 messaggi all'ora. Questa restrizione è a livello di tenant. Questa limitazione non viene applicata quando si inviano notifiche a singoli dispositivi.
- È possibile inviare ai gruppi al massimo 25 messaggi all'ora. Questa restrizione è a livello di tenant. Questa limitazione non viene applicata quando si inviano notifiche a singoli utenti.
- Quando si inviano messaggi a singoli dispositivi, è possibile inviare fino a un massimo di 10 messaggi all'ora allo stesso dispositivo.
- È possibile inviare notifiche agli utenti in gruppi. Quando si inviano notifiche ai gruppi, ogni notifica può essere destinata direttamente a un massimo di 25 gruppi. I gruppi annidati non vengono conteggiati in questo totale. Quando si invia una notifica a un gruppo, i messaggi sono destinati solo agli utenti del gruppo e vengono inviati a ogni dispositivo iOS o Android registrato dall'utente. I dispositivi del gruppo verranno ignorati quando si invia la notifica.
- È possibile inviare notifiche a un singolo dispositivo. Anziché usare i gruppi, selezionare un dispositivo e usare un'[azione del dispositivo](device-management.md#available-device-actions) remota per inviare la notifica personalizzata.  

**Recapito**:

- Intune invia i messaggi all'app Portale aziendale degli utenti o all'app Microsoft Intune, che quindi crea la notifica push. Non è necessario che gli utenti siano connessi all'app affinché la notifica venga inviata tramite push al dispositivo, ma il dispositivo deve essere stato registrato dall'utente interessato.
- Intune, l'app Portale aziendale e l'app Microsoft Intune non possono garantire il recapito di una notifica personalizzata. Le notifiche personalizzate potrebbero essere visualizzate con alcune ore di ritardo, pertanto non è consigliabile usarle per i messaggi urgenti.  
- I messaggi di notifica personalizzati di Intune vengono visualizzati nei dispositivi come notifiche push standard. Se l'app Portale aziendale è aperta in un dispositivo iOS quando riceve la notifica, la notifica viene visualizzata nell'app invece che sotto forma di una notifica push di sistema.  
- Le notifiche personalizzate possono essere visibili nelle schermate di blocco nei dispositivi iOS/iPadOS e Android a seconda delle impostazioni del dispositivo.  
- Nei dispositivi Android altre app potrebbero avere accesso ai dati nelle notifiche personalizzate. Non usarle per le comunicazioni riservate.  
- Gli utenti di un dispositivo di cui è stata recentemente annullata la registrazione o gli utenti che sono stati rimossi da un gruppo potrebbero comunque ricevere una notifica personalizzata inviata successivamente a tale gruppo.  Analogamente, se si aggiunge un utente a un gruppo dopo l'invio di una notifica personalizzata al gruppo, è possibile che l'utente appena aggiunto riceva il messaggio di notifica inviato in precedenza.  

## <a name="send-a-custom-notification-to-groups"></a>Inviare una notifica personalizzata ai gruppi

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) con un account che ha autorizzazioni per creare e inviare notifiche e passare ad **Amministrazione del tenant** > **Notifiche personalizzate**.  

2. Nella scheda Informazioni di base specificare gli elementi seguenti e quindi selezionare **Avanti** per continuare.  
   - **Titolo**: specificare un titolo per la notifica. Il testo dei titoli può avere una lunghezza massima di 50 caratteri.  
   - **Corpo**: specificare il messaggio. Il testo dei messaggi può avere una lunghezza massima di 500 caratteri.

   ![Creare una notifica personalizzata](./media/custom-notifications/custom-notifications.png)  

3. Nella scheda **Assegnazioni** selezionare i gruppi a cui si vuole inviare la notifica personalizzata e fare clic su Avanti per continuare. L'invio di una notifica a un gruppo interessa solo gli utenti di quel gruppo; la notifica arriverà a tutti i dispositivi iOS e Android registrati da tale utente.

4. Nella scheda **Rivedi e crea** esaminare le informazioni e, quando si è pronti per inviare la notifica, selezionare **Crea**.  

Intune elabora immediatamente i messaggi creati dall'utente. L'unica conferma che il messaggio è stato inviato è la notifica di Intune che conferma l'invio della notifica personalizzata.  

![Conferma di una notifica inviata](./media/custom-notifications/notification-sent.png)  

Intune non tiene traccia delle notifiche personalizzate inviate e i dispositivi non registrano la ricezione all'esterno del centro notifiche del dispositivo. La notifica può essere contenuta in un log di diagnostica temporaneo se un utente richiede supporto nell'app Portale aziendale o nell'app Intune.

## <a name="send-a-custom-notification-to-a-single-device"></a>Inviare una notifica personalizzata a un singolo dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) con un account che ha autorizzazioni per creare e inviare notifiche e passare a **Dispositivi** > **Tutti i dispositivi**.

2. Fare doppio clic sul nome del dispositivo gestito a cui si vuole inviare una notifica per aprire la pagina *Panoramica* del dispositivo.

3. Nella pagina **Panoramica** selezionare l'azione **Invia una notifica personalizzata** per aprire il riquadro *Invia una notifica personalizzata*. Se questa opzione non è disponibile, selezionare l'opzione **...** (puntini di sospensione) nell'angolo superiore destro della pagina, quindi selezionare **Invia una notifica personalizzata**.

4. Nel riquadro **Invia una notifica personalizzata** specificare i dettagli del messaggio seguenti:  

   - **Titolo**: specificare un titolo per la notifica. Il testo dei titoli può avere una lunghezza massima di 50 caratteri.  
   - **Corpo**: specificare il messaggio. Il testo dei messaggi può avere una lunghezza massima di 500 caratteri.  

5. Selezionare **Invia** per inviare la notifica personalizzata al dispositivo. Diversamente dalle notifiche inviate ai gruppi, non è possibile configurare un'assegnazione o rivedere il messaggio prima di inviarlo.  

Intune elabora immediatamente il messaggio. L'unica conferma che il messaggio è stato inviato è la notifica di Intune che verrà ricevuta nella console, in cui viene visualizzo il testo del messaggio inviato.  

## <a name="receive-a-custom-notification"></a>Ricevere una notifica personalizzata

In un dispositivo gli utenti visualizzano i messaggi di notifica personalizzati inviati da Intune come notifica push standard dall'app Portale aziendale o dall'app Microsoft Intune. Queste notifiche sono simili alle notifiche push che gli utenti ricevono da altre app del dispositivo.  

Nei dispositivi iOS/iPadOS, se l'app Portale aziendale è aperta quando si riceve la notifica, la notifica viene visualizzata nell'app invece che in una notifica push.  

La notifica rimane fino a quando non viene ignorata dall'utente.  

## <a name="next-steps"></a>Passaggi successivi

[Gestire i dispositivi](device-management.md)
