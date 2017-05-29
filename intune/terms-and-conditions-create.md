---
title: Impostare i termini e le condizioni in Microsoft Intune
titleSuffix: Intune Azure preview
description: 'Impostare i termini e le condizioni visualizzati dagli utenti nel portale aziendale per Intune. '
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d53e91e24988d1bc71ff8df425f0d82e0fc43b58
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017

---

# <a name="ensure-users-accept-company-terms-for-access"></a>Verificare che gli utenti accettino le condizioni aziendali per l'accesso

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Come amministratore di Intune, è possibile scegliere di richiedere agli utenti di accettare i termini e le condizioni dell'azienda prima di poter usare il portale aziendale per registrare i propri dispositivi e accedere alle risorse aziendali, come app e posta elettronica. La configurazione dei termini e delle condizioni è facoltativa.

È possibile creare più set di termini e condizioni e assegnarli a gruppi diversi, ad esempio per supportare lingue diverse.

## <a name="create-terms-and-conditions"></a>Creare termini e condizioni
Completare i passaggi seguenti per creare i termini e le condizioni. Il nome visualizzato e la descrizione sono destinati all'uso amministrativo, mentre le proprietà dei termini e delle condizioni vengono visualizzate agli utenti nel portale aziendale.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.

3. Selezionare **Crea**.
![Screenshot del portale di Intune che mostra il pulsante Crea per i termini e le condizioni](media/terms-create-terms.png)

4. Nel pannello espanso specificare le informazioni seguenti:

   - **Nome visualizzato**: nome per i termini e le condizioni nel portale di Intune. Questo nome non viene visualizzato agli utenti.

   - **Descrizione**: dettagli facoltativi che permettono di identificare questo set di condizioni nel portale di Intune.

5. Selezionare la freccia accanto a Define terms of use (Definisci le condizioni per l'utilizzo) per aprire il pannello Termini e condizioni, quindi immettere le informazioni seguenti:

   ![Schermata della schermata di accettazione dei termini e condizioni dell'utente finale con riepilogo dei termini](./media/terms-summary-create.png)

   - **Titolo**: titolo visualizzato dagli utenti nel portale aziendale.

   - **Riepilogo delle condizioni:** testo che spiega il significato dell'accettazione da parte degli utenti. Ad esempio, "Registrando il dispositivo, si accettano le condizioni di utilizzo definite da Contoso. Leggere attentamente le condizioni prima di continuare."

   - **Termini e condizioni**: termini e condizioni visualizzati dagli utenti, che devono accettarli o rifiutarli.

6. Selezionare **OK** e quindi **Crea**.

## <a name="assign-terms-and-conditions"></a>Assegnare termini e condizioni

È possibile assegnare termini e condizioni a gruppi di utenti, che devono accettarli prima di usare il portale aziendale.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.

3. Nell'elenco dei termini e delle condizioni selezionare quelli da assegnare e quindi fare clic su **Gruppi assegnati**.
![Screenshot del pannello Assegna gruppi del portale di Intune che mostra i pulsanti Seleziona gruppo e Seleziona per l'assegnazione dei termini e delle condizioni](media/terms-assign-groups.png)

4. Fare clic sul pulsante **Seleziona gruppo**, selezionare i gruppi a cui assegnare i termini e le condizioni nel pannello **Seleziona gruppi** e quindi fare clic su **Seleziona**.

5. Nel pannello **Gruppi assegnati** fare clic su **Salva**.  I termini e le condizioni sono ora assegnati a utenti in gruppi selezionati. Agli utenti verrà chiesto di accettare i termini e le condizioni al successivo accesso al portale aziendale.

   ![Schermata della schermata di accettazione dei termini e condizioni dell'utente finale con riepilogo dei termini](./media/terms-summary-accept.png)

## <a name="monitor-a-terms-and-conditions"></a>Monitorare i termini e le condizioni

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**. Nel pannello Intune scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.
2. Nell'elenco dei termini e delle condizioni selezionare quelli per i quali si vuole visualizzare l'accettazione e quindi fare clic su **Stati di accettazione**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Gestire più versioni di termini e condizioni
È possibile modificare i termini e le condizioni e gestirne le versioni. È consigliabile incrementare il numero di versione e richiedere l'accettazione ogni volta che si apportano modifiche significative ai termini e alle condizioni. Non modificare il numero di versione corrente se, ad esempio, si correggono errori di digitazione o si modifica la formattazione.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registrazione del dispositivo**, scegliere **Termini e condizioni**, selezionare i termini e le condizioni da modificare e quindi selezionare **Proprietà**.

4. Nel pannello **Proprietà** selezionare **Termini e condizioni** e quindi modificare **Titolo**, **Riepilogo delle condizioni** e **Termini e condizioni** in base alle esigenze. Se dopo le modifiche apportate è necessario che gli utenti riaccettino i nuovi termini e condizioni, fare clic su **Richiedi agli utenti di accettare di nuovo e incrementa il numero di versione a**.

4.  Selezionare **OK** e quindi **Salva**.

