---
title: Bloccare le app non provviste di autenticazione moderna | Documentazione Microsoft
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
ms.sourcegitcommit: e55cf608c2e5157feeb40ba20d3988b5b35064db
ms.openlocfilehash: b2d708e35a7993ff7c5e3db170b1025794b33baf
ms.lasthandoff: 02/25/2017


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloccare le app che non usano l'autenticazione moderna (ADAL)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

L'accesso condizionale basato sulle app e i criteri di protezione delle app si basano su applicazioni che usano l'[autenticazione moderna](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) che è un'implementazione di OAuth2. La maggior parte delle applicazioni Office mobili e desktop utilizza l'autenticazione moderna, ma esistono applicazioni di terze parti e applicazioni Office meno recenti che usano altri metodi di autenticazione, quali l'autenticazione di base e l'autenticazione basata su form.

Per bloccare l'accesso a queste applicazioni si consiglia quanto segue:

* Configurare le regole delle attestazioni ADFS per bloccare i protocolli di autenticazione non moderni. Istruzioni dettagliate sono disponibili nello Scenario 3: [block all access to O365 except browser-based applications](https://technet.microsoft.com/library/dn592182.aspx) (Bloccare l'accesso a O365 salvo per le applicazioni basate su browser).

>[!IMPORTANT]
>L'accesso condizionale basato sulle app non deve essere usato con l'autenticazione basata su certificato di Azure Active Directory (Azure AD). È possibile configurare una sola di queste impostazioni alla volta.

### <a name="see-also"></a>Vedere anche
[Consentire l'accesso ai servizi O365 solo alle app supportate da Intune](allow-policy-managed-apps-access-to-o365.md)

