---
title: Impostare i termini e le condizioni in Microsoft Intune
titlesuffix: Azure portal
description: 'Impostare i termini e le condizioni visualizzati dagli utenti nel portale aziendale per Intune. '
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 63434cbbc9edc668d59fb99968727551e0c4cc40
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2017
---
# <a name="ensure-users-accept-company-terms-for-access"></a>Verificare che gli utenti accettino le condizioni aziendali per l'accesso

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Come amministratore di Intune, è possibile richiedere agli utenti di accettare i termini e le condizioni dell'azienda prima di poter usare il portale aziendale per registrare i propri dispositivi e accedere a risorse, come app e posta elettronica aziendali. La configurazione dei termini e delle condizioni è facoltativa.

È possibile creare più set di termini e condizioni e assegnarli a gruppi diversi, ad esempio per supportare lingue diverse.

## <a name="create-terms-and-conditions"></a>Creare termini e condizioni
Completare i passaggi seguenti per creare i termini e le condizioni. Il nome visualizzato e la descrizione sono destinati all'uso amministrativo, mentre le proprietà dei termini e delle condizioni vengono visualizzate agli utenti nel portale aziendale.

1. Nel portale di Azure scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.
2. Selezionare **Crea**.
![Screenshot del portale di Azure che mostra il pulsante Crea per i termini e le condizioni](media/terms-create-terms.png)
3. Nel pannello espanso specificare le informazioni seguenti:

   - **Nome visualizzato**: nome per i termini e le condizioni nel portale di Azure. Questo nome non viene visualizzato agli utenti.

   - **Descrizione**: dettagli facoltativi che permettono di identificare questo set di condizioni nel portale di Azure.

4. Selezionare la freccia accanto a Define terms of use (Definisci le condizioni per l'utilizzo) per aprire il pannello Termini e condizioni, quindi immettere le informazioni seguenti:

   ![Schermata della schermata di accettazione dei termini e condizioni dell'utente finale con riepilogo dei termini](./media/terms-summary-create.png)

   - **Titolo**: il nome per le condizioni che verrà visualizzato agli utenti nel portale aziendale sopra **Riepilogo**.
   - **Riepilogo delle condizioni:** testo che spiega il significato dell'accettazione da parte degli utenti. Ad esempio, "Registrando il dispositivo, si accettano le condizioni di utilizzo definite da Contoso. Leggere attentamente le condizioni prima di continuare."
   - **Termini e condizioni**: termini e condizioni visualizzati dagli utenti, che devono accettarli o rifiutarli.

5. Selezionare **OK** e quindi **Crea**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Modalità di visualizzazione delle condizioni agli utenti
L'esempio seguente mostra **Titolo** e **Riepilogo delle condizioni** nella console di amministrazione e nel portale aziendale.

![Screenshot di Titolo e Riepilogo delle condizioni nella console di amministrazione e nel portale aziendale.](./media/terms-summary-terms.png)

L'esempio seguente mostra i termini e le condizioni nella console di amministrazione e nel portale aziendale.

![Screenshot dei termini e delle condizioni nella console di amministrazione e nel portale aziendale.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Assegnare termini e condizioni

È possibile assegnare termini e condizioni a gruppi di utenti, che devono accettarli prima di usare il portale aziendale.

1. Nel portale di Azure scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.
2. Nell'elenco dei termini e delle condizioni selezionare quelli da assegnare e quindi fare clic su **Gruppi assegnati**.
![Screenshot del pannello Assegna gruppi del portale di Azure che mostra i pulsanti Seleziona gruppo e Seleziona per l'assegnazione dei termini e delle condizioni](media/terms-assign-groups.png)
3. Fare clic sul pulsante **Seleziona gruppo**, selezionare i gruppi a cui assegnare i termini e le condizioni nel pannello **Seleziona gruppi** e quindi fare clic su **Seleziona**. Non è possibile assegnare termini e condizioni ai gruppi dinamici.
4. Nel pannello **Gruppi assegnati** fare clic su **Salva**.  I termini e le condizioni sono ora assegnati a utenti in gruppi selezionati. Agli utenti verrà chiesto di accettare i termini e le condizioni al successivo accesso al portale aziendale. I termini e le condizioni devono essere accettati una sola volta. Gli utenti con più dispositivi non dovranno accettarli in ogni dispositivo.


## <a name="monitor-terms-and-conditions"></a>Monitorare termini e condizioni

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**. Nel pannello Intune scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.
2. Nell'elenco dei termini e delle condizioni selezionare quelli per i quali si vuole visualizzare l'accettazione e quindi fare clic su **Stati di accettazione**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Gestire più versioni di termini e condizioni
È possibile modificare i termini e le condizioni e gestirne le versioni. È consigliabile incrementare il numero di versione e richiedere l'accettazione ogni volta che si apportano modifiche significative ai termini e alle condizioni. Non modificare il numero di versione corrente se, ad esempio, si correggono errori di digitazione o si modifica la formattazione.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registrazione del dispositivo**, scegliere **Termini e condizioni**, selezionare i termini e le condizioni da modificare e quindi selezionare **Proprietà**.

4. Nel pannello **Proprietà** selezionare **Termini e condizioni** e quindi modificare **Titolo**, **Riepilogo delle condizioni** e **Termini e condizioni** in base alle esigenze. Se dopo le modifiche apportate è necessario che gli utenti riaccettino i nuovi termini e condizioni, fare clic su **Richiedi agli utenti di accettare di nuovo e incrementa il numero di versione a**.

4.  Selezionare **OK** e quindi **Salva**.

Gli utenti devono accettare i termini e le condizioni aggiornati una sola volta. Gli utenti con più dispositivi non dovranno accettarli in ogni dispositivo.
