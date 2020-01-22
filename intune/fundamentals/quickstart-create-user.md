---
title: 'Guida introduttiva: creare un utente in Intune'
description: 'Guida introduttiva: creare un utente in Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: fdd97e69c97df5a266e147381d94b3d4419bab34
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036577"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>Guida introduttiva: Creare un utente in Intune e assegnare una licenza

In questo articolo di avvio rapido verrà creato un utente a cui verrà poi assegnata una licenza di Intune. In Intune, ogni persona che si vuole possa accedere ai dati aziendali deve avere un proprio account utente. Gli amministratori di Intune possono configurare gli utenti in un secondo momento per gestire il controllo di accesso.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come [amministratore globale o come amministratore del servizio Intune](users-add.md#types-of-administrators). Se è stata creata una sottoscrizione di valutazione di Intune, l'account con cui è stata creata la sottoscrizione sarà l'amministratore globale.

## <a name="create-a-user"></a>Creare un utente

Gli utenti devono avere un account utente per registrarsi nella gestione dei dispositivi in Intune. Per creare un nuovo utente:

1. In Intune, scegliere **Utenti** > **Tutti gli utenti** > **Nuovo utente**.
![Browser](./media/quickstart-create-user/create-user.png)
2. Nella casella **Nome** immettere un nome, ad esempio *Dewey Kellum*.
3. Nella casella **Nome utente** immettere un ID utente, ad esempio Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Se non è stato configurato il nome di dominio del cliente, usare il nome di dominio verificato usato per creare la sottoscrizione di Intune (o la [versione di valutazione gratuita](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Scegliere **Mostra password** e prendere nota della password generata automaticamente in modo che sia possibile accedere a un dispositivo di test.
5. Scegliere **Crea**.

## <a name="assign-a-license-to-the-user"></a>Assegnare una licenza a un utente

Dopo aver creato un utente, è necessario usare l'[interfaccia di amministrazione di Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) per assegnare una licenza di Intune a tale utente. Se non si assegna una licenza all'utente, non sarà in grado di registrare il dispositivo in Intune. 

Per assegnare una licenza di Intune a un utente:

1. Accedere all'[interfaccia di amministrazione di Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) con le stesse credenziali usate per accedere a Intune.
2. Scegliere **Utenti** > **Utenti attivi** e quindi scegliere l'utente appena creato.
3. Accanto a **Licenze di prodotto** selezionare **Modifica**.
4. In **Percorso** scegliere un percorso per l'utente.
5. Fare clic su **Attivata** accanto alla licenza di Intune (o a un'altra licenza che include Intune). Il [nome del prodotto](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** visualizzato viene usato come piano di servizio nella gestione di Azure 

   > [!NOTE]
   > Questa impostazione usa una delle licenze dell'utente. Se si usa un ambiente di valutazione, sarà necessario riassegnare la licenza a un utente reale in un ambiente live.
6. Scegliere **Salva** > **Chiudi**.

Verrà ora indicato che il nuovo utente di Intune attivo usa una licenza di **Intune**.

## <a name="clean-up-resources"></a>Pulizia delle risorse

Se l'utente non è più necessario, è possibile eliminarlo. Passare all'[interfaccia di amministrazione di Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) e scegliere **Utenti** > **Utenti attivi** > *scegliere l'utente nell'elenco* > **Elimina utente** > **Elimina utente** > **Conferma modifiche** > **Chiudi**.

## <a name="next-steps"></a>Passaggi successivi

In questo articolo di avvio rapido è stato creato un utente a cui è stata assegnata una licenza di Intune. Per altre informazioni sull'aggiunta di utenti a Intune, vedere [Aggiungere utenti e concedere autorizzazioni amministrative a Intune](users-add.md).

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: Creare un gruppo per gestire gli utenti](../quickstart-create-group.md)
