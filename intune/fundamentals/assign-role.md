---
title: Assegnare un ruolo a un utente di Intune
description: Informazioni su come assegnare un ruolo predefinito o personalizzato a un utente in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9e337d47757e3c5507c94433f90d5c2863bc1b0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503018"
---
# <a name="assign-a-role-to-an-intune-user"></a>Assegnare un ruolo a un utente di Intune

È possibile assegnare un ruolo [predefinito](role-based-access-control.md#built-in-roles) o [personalizzato](create-custom-role.md) a un utente di Intune.

Per creare, modificare o assegnare ruoli, l'account deve disporre di una delle seguenti autorizzazioni in Azure AD:
- **Amministratore globale**
- **Amministratore del servizio Intune**

1. Accedere al [portale Azure](https://portal.azure.com).

2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.

3. Nel pannello **Intune** scegliere **Ruoli** > **Tutti i ruoli**.

4. Nel pannello **Ruoli di Intune - Tutti i ruoli** scegliere il ruolo predefinito da assegnare.

5. Nel pannello <*nome ruolo*> - **Panoramica** scegliere **Gestisci** > **Assegnazioni**.

6. Nel pannello del ruolo personalizzato scegliere **Assegna**.

7. Nel pannello **Assegnazioni di ruolo** immettere un **Nome dell'assegnazione** e una **Descrizione dell'assegnazione** facoltativa per l'assegnazione.

8. Per **Membri (gruppi)** scegliere un gruppo contenente l'utente a cui si vogliono assegnare le autorizzazioni.

9. Per **Ambito (gruppi)** scegliere un gruppo contenente gli utenti/dispositivi che il membro indicato in precedenza è autorizzato a gestire.

10. Per **Ambito (tag)** scegliere i tag in cui verrà applicata questa assegnazione di ruolo.

11. Al termine, scegliere **OK**. La nuova assegnazione viene visualizzata nell'elenco di assegnazioni.


## <a name="next-steps"></a>Passaggi successivi
- [Informazioni sul controllo degli accessi in base al ruolo in Intune](role-based-access-control.md)
- [Creare un ruolo personalizzato](create-custom-role.md)
