---
title: Bloccare le app che non usano l'autenticazione moderna in Intune
titleSuffix: Microsoft Intune
description: Informazioni su come bloccare le app che non usano l'autenticazione moderna.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a4e4fbc4239941c662166f625de73858f1ef948a
ms.sourcegitcommit: d047a692c798e1fb61ee43a487d6332bce344610
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44058779"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloccare le app che non usano l'autenticazione moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'accesso condizionale basato sulle app e i criteri di protezione delle app si basano su applicazioni che usano l'[autenticazione moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) che è un'implementazione di OAuth2. La maggior parte delle applicazioni Office mobili e desktop usa l'autenticazione moderna, ma esistono applicazioni di terze parti e applicazioni Office meno recenti che usano altri metodi di autenticazione, quali l'autenticazione di base e l'autenticazione basata su moduli.

Per bloccare l'accesso a queste app è consigliabile:

* Configurare le regole delle attestazioni AD FS per bloccare i protocolli di autenticazione non moderni. Istruzioni dettagliate sono disponibili nello Scenario 3: [block all access to O365 except browser-based applications](https://technet.microsoft.com/library/dn592182.aspx) (Bloccare l'accesso a O365 salvo per le applicazioni basate su browser).
* Per **Exchange e SharePoint Online** usare l'accesso condizionale di Azure Active Directory e usare il cmdlet PowerShell Set-SPOTenant per SharePoint online. Per istruzioni dettagliate, vedere [Configurare SharePoint Online ed Exchange Online per l'accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>L'accesso condizionale basato sulle app non deve essere usato con l'autenticazione basata su certificato di Azure Active Directory (Azure AD). È possibile configurare una sola di queste impostazioni alla volta.

### <a name="see-also"></a>Vedere anche
[Accesso condizionale basato su app con Intune](app-based-conditional-access-intune.md)
