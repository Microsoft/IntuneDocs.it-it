---
ms.openlocfilehash: 76706fb39c3c5a69cba4fbf3f57c0b58d92e4a27
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2019
ms.locfileid: "67560000"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisiti delle credenziali di Azure AD e Intune

L'autenticazione e l'autorizzazione si basano sulle credenziali di Azure AD e sul controllo degli accessi in base al ruolo di Intune (RBAC). Tutti gli amministratori globali e gli amministratori del servizio Intune per il tenant hanno accesso al data warehouse per impostazione predefinita. Usare i ruoli di Intune per offrire l'accesso a più utenti assegnando loro l'accesso alla risorsa **data warehouse di Intune**.

I requisiti per l'accesso al data warehouse di Intune (inclusa l'API) sono i seguenti:

  - L'utente deve essere uno dei seguenti:
      - Amministratore globale di Azure AD
      - Amministratore del servizio Intune
      - Utente con accesso basato sul ruolo alla risorsa **data warehouse di Intune**
      - Autenticazione senza utente usando l'[autenticazione OAuth](../data-warehouse-app-only-auth.md) 
