---
title: 'Guida introduttiva: creare un gruppo per gestire gli utenti'
titlesuffix: Microsoft Intune
description: In questa guida introduttiva si utilizzerà Microsoft Intune per creare un gruppo basato su utenti esistenti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b52265bb9b3df800c0e13450a2154e46098a933
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410821"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Guida introduttiva: creare un gruppo per gestire gli utenti

In questa guida introduttiva si utilizzerà Intune per creare un gruppo basato su un utente esistente. I gruppi vengono usati per gestire gli utenti e controllare l'accesso dei dipendenti alle risorse aziendali. Queste risorse possono essere parte dell'intranet aziendale o essere risorse esterne, ad esempio siti SharePoint, app SaaS o app Web.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

>[!NOTE]
>Intune fornisce per praticità i gruppi **Tutti gli utenti** e **Tutti i dispositivi** creati in precedenza nella console con le ottimizzazioni predefinite.

## <a name="prerequisites"></a>Prerequisiti

- Per completare questa guida introduttiva, è necessario [creare un utente](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come [amministratore globale o come amministratore del servizio Intune](users-add.md#types-of-administrators). Se è stata creata una sottoscrizione della versione di valutazione di Intune, l'account creato con tale sottoscrizione sarà un amministratore globale.

## <a name="create-a-group"></a>Creare un gruppo

Verrà creato un gruppo che sarà usato poi in questa serie di guide introduttive.

1. Dopo aver aperto il riquadro **Microsoft Intune** selezionare **Gruppi** > **Nuovo gruppo**.
2. Nella casella a discesa **Tipo gruppo** selezionare **Sicurezza**.
3. Impostare il **Nome** su "Contoso Testers" e aggiungere una **Descrizione** per il gruppo.
4. Impostare **Tipo di appartenenza** su **Assegnato**. 
5. Fare clic su **Membri** e selezionare uno o più membri per il gruppo dall'elenco esistente.

    ![Screenshot della creazione di un gruppo in Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Fare clic su **Seleziona** > **Crea**.

Se il gruppo è stato creato correttamente, verrà visualizzato nell'elenco **Tutti i gruppi**. 

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato utilizzato Intune per creare un gruppo basato su un utente esistente.

> [!div class="nextstepaction"]
> [Creare criteri di conformità dei dispositivi](quickstart-create-policy.md)
