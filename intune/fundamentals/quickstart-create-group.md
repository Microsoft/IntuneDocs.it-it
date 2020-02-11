---
title: 'Guida introduttiva: creare un gruppo per gestire gli utenti'
titleSuffix: Microsoft Intune
description: In questa guida introduttiva si utilizzerà Microsoft Intune per creare un gruppo basato su utenti esistenti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9b06043dd10f92b6176d4b2e9f90f1b7c87aac9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540954"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Guida introduttiva: Creare un gruppo per gestire gli utenti

In questa guida introduttiva si utilizzerà Intune per creare un gruppo basato su un utente esistente. I gruppi vengono usati per gestire gli utenti e controllare l'accesso dei dipendenti alle risorse aziendali. Queste risorse possono essere parte dell'intranet aziendale o essere risorse esterne, ad esempio siti SharePoint, app SaaS o app Web.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

>[!NOTE]
>Intune fornisce per praticità i gruppi **Tutti gli utenti** e **Tutti i dispositivi** creati in precedenza nella console con le ottimizzazioni predefinite.

## <a name="prerequisites"></a>Prerequisiti

- Sottoscrizione di Microsoft Intune - [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).
- Per completare questa guida introduttiva, è necessario [creare un utente](quickstart-create-user.md).

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Accedere a Intune in Microsoft Endpoint Manager

Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) come [amministratore globale o amministratore del servizio Intune](users-add.md#types-of-administrators). Se è stata creata una sottoscrizione della versione di valutazione di Intune, l'account creato con tale sottoscrizione sarà un amministratore globale.

## <a name="create-a-group"></a>Creare un gruppo

Verrà creato un gruppo che sarà usato poi in questa serie di guide introduttive. Per creare un gruppo:

1. Dopo aver aperto **Microsoft Endpoint Manager** selezionare **Gruppi** > **Nuovo gruppo**.
2. Nella casella a discesa **Tipo gruppo** selezionare **Sicurezza**.
3. Nel campo **Nome gruppo** immettere il nome del nuovo gruppo (ad esempio, **Tester Contoso**).
4. Aggiungere una **Descrizione** per il gruppo.
5. Impostare **Tipo di appartenenza** su **Assegnato**. 
6. In **Membri** selezionare il collegamento e aggiungere uno o più membri al gruppo dall'elenco.

    ![Screenshot della creazione di un gruppo in Microsoft Intune](./media/quickstart-create-group/quickstart-use-groups-01.png)

7. Fare clic su **Seleziona** > **Crea**.

Se il gruppo è stato creato correttamente, verrà visualizzato nell'elenco **Tutti i gruppi**. 

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato utilizzato Intune per creare un gruppo basato su un utente esistente. Per altre informazioni sull'aggiunta di gruppi in Intune, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](../groups-add.md).

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: configurare la registrazione automatica per i dispositivi Windows 10](../enrollment/quickstart-setup-auto-enrollment.md)
