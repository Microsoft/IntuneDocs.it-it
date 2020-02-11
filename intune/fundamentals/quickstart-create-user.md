---
title: 'Guida introduttiva: creare un utente in Intune'
description: 'Guida introduttiva: creare un utente in Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754491"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>Guida introduttiva: Creare un utente in Intune e assegnare una licenza all'utente

In questo articolo di avvio rapido verrà creato un utente a cui verrà poi assegnata una licenza di Intune. Quando si usa Intune, ogni persona a cui si vuole consentire l'accesso ai dati aziendali deve avere un proprio account utente. Gli amministratori di Intune possono configurare gli utenti in un secondo momento per gestire il controllo di accesso.

## <a name="prerequisites"></a>Prerequisiti

- Sottoscrizione di Microsoft Intune. [Iscriversi per un account valutazione gratuito](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>Accedere a Intune in Microsoft Endpoint Manager

Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) come [amministratore globale o amministratore del servizio Intune](users-add.md#types-of-administrators). Se è stata creata una sottoscrizione di valutazione di Intune, l'account con cui è stata creata la sottoscrizione è quello dell'amministratore globale.

## <a name="create-a-user"></a>Creare un utente

Gli utenti devono avere un account utente per iscriversi alla gestione dei dispositivi in Intune. Per creare un nuovo utente:

1. In Microsoft Endpoint Manager selezionare **Utenti** > **Tutti gli utenti** > **Nuovo utente**:  ![In Microsoft Endpoint Manager selezionare Nuovo utente](./media/quickstart-create-user/create-user.png)
2. Nella casella **Nome** immettere un nome, ad esempio *Dewey Kellum*:  ![Aggiungere i dettagli dell'utente](./media/quickstart-create-user/create-user-02.png)
3. Nella casella **Nome utente** immettere un ID utente, ad esempio Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Se non è stato configurato il nome di dominio del cliente, usare il nome di dominio verificato usato per creare la sottoscrizione di Intune (o la [versione di valutazione gratuita](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Selezionare **Mostra password** e assicurarsi di ricordare la password generata automaticamente per poter accedere a un dispositivo di test.
5. Selezionare **Crea**.

## <a name="assign-a-license-to-the-user"></a>Assegnare una licenza a un utente

Dopo aver creato un utente, è necessario usare l'[interfaccia di amministrazione di Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) per assegnare una licenza di Intune all'utente. Se non si assegna una licenza all'utente, non sarà in grado di registrare il dispositivo in Intune.

Per assegnare una licenza di Intune a un utente:

1. Accedere all'[interfaccia di amministrazione di Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) con le stesse credenziali usate per accedere a Intune.
2. Selezionare **Utenti** > **Utenti attivi** e quindi selezionare l'utente appena creato.
3. Selezionare la scheda **Licenze e app**.
4. In **Seleziona località** selezionare una località per l'utente, se non è già impostata.
2. Selezionare la casella di controllo **Intune** nella sezione **Licenze**. Se un'altra licenza include Intune, è possibile selezionarla. Il [nome del prodotto](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) visualizzato viene usato come piano di servizio nella gestione di Azure.

    ![Selezionare la località e la licenza di Intune](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > Questa impostazione usa una delle licenze dell'utente. Se si sta usando un ambiente di valutazione, sarà necessario riassegnare in seguito questa licenza a un utente reale in un ambiente live.

6. Selezionare **Salva modifiche**.

Verrà ora indicato che il nuovo utente di Intune attivo usa una licenza di **Intune**.

## <a name="clean-up-resources"></a>Pulizia delle risorse

Se l'utente non è più necessario, è possibile eliminarlo. A tale scopo, passare all'[interfaccia di amministrazione di Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) e selezionare **Utenti** > *utente* > *icona Elimina utente* > **Elimina utente** > **Chiudi**.

   ![Selezionare l'icona di eliminazione](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>Passaggi successivi

In questo articolo di avvio rapido è stato creato un utente a cui è stata assegnata una licenza di Intune. Per altre informazioni sull'aggiunta di utenti a Intune, vedere [Aggiungere utenti e concedere autorizzazioni amministrative a Intune](users-add.md).

Per continuare questa serie di articoli di avvio rapido su Intune, passare al prossimo articolo:

> [!div class="nextstepaction"]
> [Avvio rapido: Creare un gruppo per gestire gli utenti](../quickstart-create-group.md)
