---
title: Bloccare le app che non usano l'autenticazione moderna in Intune
titleSuffix: Microsoft Intune
description: Informazioni sulle app e l'autenticazione moderna (ADAL) in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ca96f36f8813d80c7ebb07bfb3bd65f8aa0b392
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/05/2019
ms.locfileid: "59569103"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>Bloccare le app che non usano l'autenticazione moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'accesso condizionale basato sulle app con i criteri di protezione delle app si basa su applicazioni che usano l'[autenticazione moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) che è un'implementazione di OAuth2. L'autenticazione moderna è usata dalle applicazioni desktop e per dispositivi mobili di Office più recenti. Tuttavia, esistono app di terze parti e app di Office meno recenti che usano altri metodi di autenticazione, ad esempio l'autenticazione di base e l'autenticazione basata su moduli.

## <a name="block-access-to-apps"></a>Bloccare l'accesso alle app

Per bloccare l'accesso alle app che non usano l'autenticazione moderna, usare i criteri di protezione delle app di Intune per implementare l'accesso condizionale. Per altre informazioni, vedere [Accesso condizionale basato su app con Intune](app-based-conditional-access-intune.md).

## <a name="additional-information"></a>Informazioni aggiuntive

Per altre informazioni sull'accesso condizionale di Azure AD, vedere gli argomenti seguenti:
- [Che cos'è l'accesso condizionale in Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Funzionamento dell'accesso condizionale basato su app](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [Configurare SharePoint Online ed Exchange Online per l'accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>Passaggi successivi

- [Accesso condizionale basato su app con Intune](app-based-conditional-access-intune.md)
