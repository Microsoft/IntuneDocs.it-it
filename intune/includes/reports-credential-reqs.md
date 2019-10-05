---
ms.openlocfilehash: 8483ed3d4198e228bdaaf4723b2c9c0dca9cecfc
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830501"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisiti delle credenziali di Azure AD e Intune

L'autenticazione e l'autorizzazione si basano sulle credenziali di Azure AD e sul controllo degli accessi in base al ruolo di Intune (RBAC). Tutti gli amministratori globali e gli amministratori del servizio Intune per il tenant hanno accesso al data warehouse per impostazione predefinita. Usare i ruoli di Intune per offrire l'accesso a più utenti assegnando loro l'accesso alla risorsa **data warehouse di Intune**.

I requisiti per l'accesso al data warehouse di Intune (inclusa l'API) sono i seguenti:

- L'utente deve essere uno dei seguenti:
  - Amministratore globale di Azure AD
  - Amministratore del servizio Intune
  - Utente con accesso basato sul ruolo alla risorsa **data warehouse di Intune**
  - Autenticazione senza utente usando l'[autenticazione OAuth](../developer/data-warehouse-app-only-auth.md) 
