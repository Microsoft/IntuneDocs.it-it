---
title: Bloccare le app non provviste di autenticazione moderna | Microsoft Intune
description: 
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5083cb49e7a98f19ff21c1972149b00aee4ec93e
ms.openlocfilehash: 8c2718da6f90f18ffbaa6a977dfca7fbc9a1bb09


---

# Bloccare le app che non usano l'autenticazione moderna (ADAL)
L'accesso condizionale per le app con criteri MAM (MAM CA) si basa su applicazioni che usano l'[autenticazione moderna](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), un'implementazione di OAuth2. La maggior parte delle applicazioni Office mobili e desktop utilizza l'autenticazione moderna, ma esistono applicazioni di terze parti e applicazioni Office meno recenti che usano altri metodi di autenticazione, quali l'autenticazione di base e l'autenticazione basata su form.

Per bloccare l'accesso a queste applicazioni si consiglia quanto segue:

* Configurare le regole delle attestazioni ADFS per bloccare i protocolli di autenticazione non moderni. Istruzioni dettagliate sono disponibili nello Scenario 3: [block all access to O365 except browser-based applications](https://technet.microsoft.com/library/dn592182.aspx) (Bloccare l'accesso a O365 salvo per le applicazioni basate su browser).

>[!IMPORTANT]
>L'accesso condizionale per la gestione delle app per dispositivi mobili non deve essere usato con l'autenticazione basata su certificato di Azure Active Directory (Azure AD). È possibile configurare una sola di queste impostazioni alla volta.



### Vedere anche
[Allow only apps supported by Intune to access O365 services (Consentire l'accesso ai servizi O365 solo alle app supportate da Intune)](allow-policy-managed-apps-access-to-o365.md)



<!--HONumber=Oct16_HO4-->


