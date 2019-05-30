---
title: Creare un ruolo personalizzato in Intune
description: Informazioni su come creare un ruolo personalizzato in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d053b0b37931443a343c91b5122b7a097d248c51
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048681"
---
# <a name="create-a-custom-role-in-intune"></a>Creare un ruolo personalizzato in Intune

È possibile creare un ruolo di Intune personalizzato che include le autorizzazioni necessarie per un ruolo professionale specifico. Ad esempio, se un gruppo del reparto IT gestisce le applicazioni, i criteri e i profili di configurazione, è possibile aggiungere tutte queste autorizzazioni insieme in un ruolo personalizzato. Dopo aver creato un ruolo personalizzato, è possibile [assegnare](assign-role.md) il ruolo a tutti gli utenti che necessitano di tali autorizzazioni.

Per creare, modificare o assegnare ruoli, l'account deve disporre di una delle seguenti autorizzazioni in Azure AD:
- **Amministratore globale**
- **Amministratore del servizio Intune**

## <a name="to-create-a-custom-role"></a>Per creare un ruolo personalizzato

1. Accedere al [portale di Azure](https://portal.azure.com) con le credenziali di Intune.

2. Scegliere **Tutti i servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune** > **Ruoli** > **Tutti i ruoli** > **Aggiungi**.

4. Nel pannello **Aggiungi un ruolo personalizzato** immettere un nome e una descrizione per il nuovo ruolo e quindi fare clic su **Autorizzazioni**.

5. Nel pannello **Autorizzazioni** scegliere le autorizzazioni da usare con questo ruolo. Usare la [tabella del controllo RBAC di Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) per decidere le autorizzazioni da applicare.

6. Nel pannello **Ambito (tag)** scegliere i tag per il ruolo. Questo ruolo può accedere alle risorse che hanno questi tag.

7. Al termine, scegliere **OK**.

8. Nel pannello **Aggiungi ruolo personalizzato** fare clic su **Crea**. Il nuovo ruolo viene visualizzato nell'elenco del pannello **Ruoli di Intune- Tutti i ruoli**.

## <a name="next-steps"></a>Passaggi successivi
- [Assegnare un ruolo a un utente](assign-role.md)
- [Informazioni sul controllo degli accessi in base al ruolo in Intune](role-based-access-control.md)
