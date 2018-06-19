---
title: Impostare i termini e le condizioni in Microsoft Intune
titlesuffix: ''
description: Impostare i termini e le condizioni visualizzati dagli utenti nel portale aziendale per Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 550d9c457335f212f0b60c16249e45f22f5baaf5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31033301"
---
# <a name="manage-your-companys-terms-and-conditions-for-user-access"></a>Gestire termini e condizioni aziendali per l'accesso degli utenti

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Come amministratore di Intune, è possibile richiedere agli utenti di accettare i termini e le condizioni dell'azienda prima di poter usare il portale aziendale per registrare i propri dispositivi e accedere a risorse, come app e posta elettronica aziendali. La configurazione dei termini e delle condizioni è facoltativa.

È possibile creare più set di termini e condizioni e assegnarli a gruppi diversi, ad esempio per supportare lingue diverse.

## <a name="create-terms-and-conditions"></a>Creare termini e condizioni
Completare i passaggi seguenti per creare i termini e le condizioni. Il nome visualizzato e la descrizione sono destinati all'uso amministrativo, mentre le proprietà dei termini e delle condizioni vengono visualizzate agli utenti nel portale aziendale.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.
2. Selezionare **Crea**.
![Screenshot del portale di Azure che mostra il pulsante Crea per i termini e le condizioni](media/terms-create-terms.png)
3. Nel riquadro espanso specificare le informazioni seguenti:

   - **Nome visualizzato**: nome per i termini e le condizioni nel portale di Azure. Questo nome non viene visualizzato agli utenti.

   - **Descrizione**: dettagli facoltativi che permettono di identificare questo set di condizioni nel portale di Azure.

4. Selezionare la freccia accanto a **Define terms of use** (Definisci le condizioni per l'uso) per aprire il riquadro Termini e condizioni e immettere le informazioni seguenti:

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
2. Nell'elenco dei termini e delle condizioni selezionare quelli da assegnare e quindi fare clic su **Gestisci** > **Assegnazioni**.
![Screenshot del riquadro Assegna gruppi del portale di Azure in cui vengono visualizzati i pulsanti Selezione gruppo e Seleziona per l'assegnazione di termini e condizioni](media/terms-assign-groups.png)
3. Fare clic su **Seleziona gruppo**, selezionare i gruppi a cui assegnare i termini e le condizioni e fare clic su **Seleziona**. Non è possibile assegnare termini e condizioni ai gruppi dinamici.
4. Nel riquadro **Gruppi assegnati** fare clic su **Salva**.  I termini e le condizioni sono ora assegnati a utenti in gruppi selezionati. Agli utenti verrà chiesto di accettare i termini e le condizioni al successivo accesso al portale aziendale. I termini e le condizioni devono essere accettati una sola volta. Gli utenti con più dispositivi non dovranno accettarli in ogni dispositivo.


## <a name="monitor-terms-and-conditions"></a>Monitorare termini e condizioni

1. Nel portale di Azure scegliere **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**. 
1. Nel riquadro Intune scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.
2. Nell'elenco dei termini e delle condizioni selezionare quelli per i quali si vuole visualizzare l'accettazione e quindi scegliere **Acceptance Reporting** (Creazione di report sull'accettazione).

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Gestire più versioni di termini e condizioni
È possibile modificare i termini e le condizioni e gestirne le versioni. È consigliabile incrementare il numero di versione e richiedere l'accettazione ogni volta che si apportano modifiche significative ai termini e alle condizioni. Non modificare il numero di versione corrente se, ad esempio, si correggono errori di digitazione o si modifica la formattazione.

1. Nel portale di Azure scegliere **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel riquadro di Intune scegliere **Registrazione del dispositivo**, **Termini e condizioni**, selezionare i termini e le condizioni che si vuole modificare e quindi scegliere **Proprietà**.

4. Nel pannello **Proprietà** selezionare **Termini e condizioni** e quindi modificare **Titolo**, **Riepilogo delle condizioni** e **Termini e condizioni** in base alle esigenze. Se dopo le modifiche apportate è necessario che gli utenti riaccettino i nuovi termini e condizioni, fare clic su **Richiedi agli utenti di accettare di nuovo e incrementa il numero di versione a**.

4.  Selezionare **OK** e quindi **Salva**.

Gli utenti devono accettare i termini e le condizioni aggiornati una sola volta. Gli utenti con più dispositivi non dovranno accettarli in ogni dispositivo.
