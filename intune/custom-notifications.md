---
title: Inviare notifiche personalizzate agli utenti con Microsoft Intune
titleSuffix: Microsoft Intune
description: Usare Intune per creare e inviare notifiche push personalizzate agli utenti di dispositivi iOS e Android
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bffbc96e945d522453c299717a6eb413354a4af4
ms.sourcegitcommit: 98f2597eec28c6096985d5a1acae72430c2afb1a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70878048"
---
# <a name="send-custom-notifications-in-intune"></a>Inviare notifiche personalizzate in Intune  

Usare Microsoft Intune per inviare notifiche personalizzate agli utenti di dispositivi iOS e Android gestiti. Questi messaggi vengono visualizzati come notifiche push standard dall'app Portale aziendale e dall'app Microsoft Intune sul dispositivo di un utente nello stesso modo in cui vengono visualizzate sul dispositivo le notifiche provenienti da altre applicazioni. Le notifiche personalizzate di Intune non sono supportate dai dispositivi Windows.   

I messaggi di notifica personalizzati includono un titolo breve e un corpo del messaggio di massimo 500 caratteri. Questi messaggi possono essere personalizzati per qualsiasi scopo di comunicazione generale.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Scenari comuni per l'invio di notifiche personalizzate  

- Usare le notifiche personalizzate per avvisare utenti specifici della disponibilità di una nuova app nel Portale aziendale.  
- Informare tutti i dipendenti di un cambiamento della pianificazione, ad esempio della chiusura degli edifici a causa del maltempo.  

## <a name="considerations-for-using-custom-notifications"></a>Considerazioni sull'uso delle notifiche personalizzate  

**Configurazione del dispositivo**:  
- Prima che gli utenti possano ricevere notifiche personalizzate, è necessario che nei dispositivi sia installata l'app Portale aziendale o l'app Microsoft Intune. È anche necessario che siano configurate le autorizzazioni per consentire all'app Portale aziendale o all'app Microsoft Intune di inviare notifiche push. Se necessario, l'app Portale aziendale e l'app Microsoft Intune possono richiedere agli utenti di consentire le notifiche.  
- In Android Google Play Services è una dipendenza obbligatoria.  
- Il dispositivo deve disporre della registrazione a MDM.

**Creazione delle notifiche**:  
- Per creare un messaggio, usare un account a cui è assegnato un ruolo di Intune che include l'autorizzazione **Aggiorna** per l'**organizzazione**. Per assegnare autorizzazioni a un utente, vedere [Assegnazioni di ruolo](role-based-access-control.md#role-assignments)  
- Le notifiche personalizzate sono limitate a titoli di 50 caratteri e messaggi di 500 caratteri.  
- Intune non salva i messaggi inviati. Per inviare nuovamente un messaggio, è necessario crearlo di nuovo.  
- È possibile inviare al massimo 25 messaggi all'ora. Questa restrizione è a livello di tenant.  
- Ogni notifica può essere destinata direttamente a un massimo di 25 gruppi. I gruppi annidati non vengono conteggiati in questo totale.  
- I gruppi possono includere utenti o dispositivi, ma i messaggi vengono inviati solo agli utenti e vengono inviati a ogni dispositivo iOS o Android registrato dall'utente.  

**Recapito**:  
- Intune invia i messaggi all'app Portale aziendale degli utenti o all'app Microsoft Intune, che quindi crea la notifica push. Non è necessario che gli utenti siano connessi all'app affinché la notifica venga inviata tramite push al dispositivo.  
- Intune, l'app Portale aziendale e l'app Microsoft Intune non possono garantire il recapito di una notifica personalizzata. Le notifiche personalizzate potrebbero essere visualizzate con alcune ore di ritardo, pertanto non è consigliabile usarle per i messaggi urgenti.  
- I messaggi di notifica personalizzati di Intune vengono visualizzati nei dispositivi come notifiche push standard. Se l'app Portale aziendale è aperta in un dispositivo iOS quando riceve la notifica, la notifica viene visualizzata nell'app invece che in una notifica push.  
- Le notifiche personalizzate possono essere visibili nelle schermate di blocco nei dispositivi iOS e Android a seconda delle impostazioni del dispositivo.  
- Nei dispositivi Android altre app potrebbero avere accesso ai dati nelle notifiche personalizzate. Non usarle per le comunicazioni riservate.  
- Gli utenti di un dispositivo di cui è stata recentemente annullata la registrazione o gli utenti che sono stati rimossi da un gruppo potrebbero comunque ricevere una notifica personalizzata inviata successivamente a tale gruppo.  Analogamente, se si aggiunge un utente a un gruppo dopo l'invio di una notifica personalizzata al gruppo, è possibile che l'utente appena aggiunto riceva il messaggio di notifica inviato in precedenza.  

## <a name="send-a-custom-notification"></a>Inviare una notifica personalizzata  

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) con un account che ha le autorizzazioni per creare e inviare notifiche e passare a **Dispositivi** > **Invia notifiche personalizzate**.  

2. Nella scheda Informazioni di base specificare gli elementi seguenti e quindi selezionare **Avanti** per continuare.  
   - **Titolo**: specificare un titolo per la notifica. Il testo dei titoli può avere una lunghezza massima di 50 caratteri.  
   - **Corpo**: specificare il messaggio. Il testo dei messaggi può avere una lunghezza massima di 500 caratteri

   ![Creare una notifica personalizzata](./media/custom-notifications/custom-notifications.png)  

3. Nella scheda **Assegnazioni** selezionare i gruppi a cui si vuole inviare la notifica personalizzata e fare clic su Avanti per continuare.  

4. Nella scheda **Rivedi e crea** esaminare le informazioni e, quando si è pronti per inviare la notifica, selezionare **Crea**.  

Intune elabora immediatamente i messaggi creati dall'utente. L'unica conferma che il messaggio è stato inviato è la notifica di Intune che conferma l'invio della notifica personalizzata.  

![Conferma di una notifica inviata](./media/custom-notifications/notification-sent.png)  

Intune non tiene traccia delle notifiche personalizzate inviate e i dispositivi non registrano la ricezione all'esterno del centro notifiche del dispositivo.  

## <a name="receive-a-custom-notification"></a>Ricevere una notifica personalizzata  

In un dispositivo gli utenti visualizzano i messaggi di notifica personalizzati inviati da Intune come notifica push standard dall'app Portale aziendale o dall'app Microsoft Intune. Queste notifiche sono simili alle notifiche push che gli utenti ricevono da altre app del dispositivo.  

Nei dispositivi iOS, se l'app Portale aziendale è aperta quando si riceve la notifica essa viene visualizzata nell'app invece che in una notifica push.  

La notifica rimane fino a quando non viene ignorata dall'utente.  

## <a name="next-steps"></a>Passaggi successivi  
[Gestire i dispositivi](device-management.md)
