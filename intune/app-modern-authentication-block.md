---
title: Bloccare le app che non usano l'autenticazione moderna in Intune
titleSuffix: Microsoft Intune
description: Informazioni su come bloccare le app che non usano l'autenticazione moderna (ADAL) in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: dc9318d46892eab21e81c7eb2992f3476720abd1
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642456"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloccare le app che non usano l'autenticazione moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'accesso condizionale basato sulle app con i criteri di protezione delle app si basa su applicazioni che usano l'[autenticazione moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) che è un'implementazione di OAuth2. L'autenticazione moderna è usata dalle applicazioni desktop e per dispositivi mobili di Office più recenti. Tuttavia, esistono app di terze parti e app di Office meno recenti che usano altri metodi di autenticazione, ad esempio l'autenticazione di base e l'autenticazione basata su moduli.

## <a name="block-apps"></a>Bloccare le app

Per bloccare l'accesso alle app che non usano l'autenticazione moderna, è consigliabile adottare i metodi seguenti:

- Configurare le regole delle attestazioni AD FS per bloccare i protocolli di autenticazione non moderni. Istruzioni dettagliate sono disponibili nello Scenario 3: [block all access to O365 except browser-based applications](https://technet.microsoft.com/library/dn592182.aspx) (Bloccare l'accesso a O365 salvo per le applicazioni basate su browser).
- Per **Exchange e SharePoint Online** usare l'accesso condizionale di Azure Active Directory e usare il cmdlet PowerShell Set-SPOTenant per SharePoint online. Per istruzioni dettagliate, vedere [Configurare SharePoint Online ed Exchange Online per l'accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>L'accesso condizionale basato sulle app non deve essere usato con l'autenticazione basata su certificato di Azure Active Directory (Azure AD). È possibile configurare una sola di queste impostazioni alla volta.

## <a name="next-steps"></a>Passaggi successivi

- [Accesso condizionale basato su app con Intune](app-based-conditional-access-intune.md)
