---
title: Bloccare le app che non usano l&quot;autenticazione moderna
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: abfb3912ba6dfa6802e1321782afd155a96fbefc
ms.lasthandoff: 04/19/2017


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloccare le app che non usano l'autenticazione moderna (ADAL)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

L'accesso condizionale basato sulle app e i criteri di protezione delle app si basano su applicazioni che usano l'[autenticazione moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) che è un'implementazione di OAuth2. La maggior parte delle applicazioni Office mobili e desktop utilizza l'autenticazione moderna, ma esistono applicazioni di terze parti e applicazioni Office meno recenti che usano altri metodi di autenticazione, quali l'autenticazione di base e l'autenticazione basata su form.

Per bloccare l'accesso a queste applicazioni si consiglia quanto segue:

* Configurare le regole delle attestazioni ADFS per bloccare i protocolli di autenticazione non moderni. Istruzioni dettagliate sono disponibili nello Scenario 3: [block all access to O365 except browser-based applications](https://technet.microsoft.com/library/dn592182.aspx) (Bloccare l'accesso a O365 salvo per le applicazioni basate su browser).
* Per **SharePoint Online**, disabilitare l'autenticazione non moderna nel servizio di SharePoint Online tramite il cmdlet PowerShell [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) per impostare la proprietà dei protocolli di autenticazione precedente su false:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false
 
```


>[!IMPORTANT]
>L'accesso condizionale basato sulle app non deve essere usato con l'autenticazione basata su certificato di Azure Active Directory (Azure AD). È possibile configurare una sola di queste impostazioni alla volta.

### <a name="see-also"></a>Vedere anche
[Consentire l'accesso ai servizi O365 solo alle app supportate da Intune](allow-policy-managed-apps-access-to-o365.md)

