---
title: 'Guida introduttiva: creare un utente in Intune'
description: 'Guida introduttiva: creare un utente in Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581675"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Guida introduttiva: creare un utente e assegnargli una licenza

In questa guida introduttiva verrà creato un utente a cui verrà assegnata una licenza. In Intune, ogni persona che si desidera possa accedere ai dati aziendali deve disporre di un account utente. Gli amministratori di Intune potranno quindi configurare tali utenti per gestire il controllo dell'accesso.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune.

## <a name="create-a-user"></a>Creazione di un utente

Gli utenti devono disporre di un account utente per registrarsi alla gestione dei dispositivi in Intune.

1. In Intune, scegliere **Utenti** > **Tutti gli utenti** > **Nuovo utente**.
![Browser](media/quickstart-create-user/create-user.png)
2. Nella casella **Nome** immettere *Dewey Kellum*.
3. Nella casella **Nome utente** immettere *Dewey@contoso.onmicrosoft.com*.
4. Scegliere **Gruppi** > **Tutti** > **Seleziona**.
5. Scegliere **Mostra password** e prendere nota della password generata automaticamente in modo che sia possibile accedere a un dispositivo di test.
6. Scegliere **Crea**.

## <a name="assign-a-license-to-the-user"></a>Assegnare una licenza a un utente

Dopo aver creato un utente è necessario usare il [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) per assegnare una licenza di Intune a tale utente. Senza una licenza, l'utente non può registrare il dispositivo in Intune. 

1. Accedere al [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con le stesse credenziali usate per accedere a Intune.
2. Scegliere **Utenti** > **Utenti attivi** > scegliere l'utente appena creato.
3. In **Percorso** scegliere un percorso per l'utente.
3. Scegliere **Licenze di prodotto** e impostare **Enterprise Mobility + Security E3** (o un'altra licenza di cui si dispone che includa Intune) su **Attivato**.
   > [!NOTE]
   > Questa operazione usa una delle licenze per l'utente. Se si usa l'ambiente in tempo reale è possibile disattivare l'uso di licenza in un secondo momento per riassegnarla a un utente reale.
5. Scegliere **Salva**.

## <a name="clean-up-resources"></a>Pulizia delle risorse

Se l'utente non è più necessario, è possibile eliminarlo scegliendo **Utenti** > **Tutti gli utenti** > scegliere l'utente nell'elenco > **Elimina utente** > **Sì**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato creato un utente a cui è stata assegnata una licenza. È ora possibile assegnare tale utente a un gruppo.

> [!div class="nextstepaction"]
> [Creare un gruppo](quickstart-create-group.md)
