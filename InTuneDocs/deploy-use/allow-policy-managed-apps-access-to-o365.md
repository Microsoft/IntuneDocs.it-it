---
title: Accesso condizionale basato su app a Office 365 | Documentazione Microsoft
description: "Informazioni su come l&quot;accesso condizionale per la gestione delle app per dispositivi mobili può essere usato per controllare le app che hanno accesso ai servizi di Office&365;."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e55cf608c2e5157feeb40ba20d3988b5b35064db
ms.openlocfilehash: d53cded6670069f10bf645d23ff9a9102bd97539
ms.lasthandoff: 02/25/2017


---

# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>Consentire l'accesso ai servizi di Office 365 solo alle app per dispositivi mobili che supportano i criteri di protezione delle app di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I [criteri di protezione delle app di Intune](protect-apps-and-data-with-microsoft-intune.md) consentono di proteggere i dati aziendali sui dispositivi registrati per la gestione in Intune. I criteri di protezione delle app possono essere usati anche nei **dispositivi di proprietà dei dipendenti non registrati per la gestione in Intune**.  In questo caso, anche se il dispositivo non viene gestito, è comunque necessario assicurarsi che i dati e le risorse aziendali siano protetti. Se si usa l'accesso condizionale basato sulle app con il software MAM, è possibile creare un criterio che consenta solo alle app per dispositivi mobili che supportano i criteri di protezione delle app di Intune di accedere ai servizi di Office&365; come Exchange Online.

Ad esempio, consentendo solo all'**app di Microsoft Outlook** di accedere a Exchange Online è possibile **bloccare le app di posta elettronica predefinite in iOS e Android** che non hanno la protezione dei dati dei criteri di gestione delle app per dispositivi mobili di Intune per ricevere la posta elettronica da **Exchange Online**.

La figura seguente illustra il flusso usato dai criteri di accesso condizionale basato sulle app per determinare se consentire o bloccare l'accesso: ![Figura che illustra i diversi criteri inclusi per determinare se consentire o bloccare l'accesso](../media/mam-ca-decision-flow_simple.png).

Descrizione delle abbreviazioni usate nei diagrammi:
* **CP**: app Portale aziendale
* **AA**: app Azure Authenticator
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>Prerequisiti
**Prima** di creare un criterio di accesso condizionale basato sulle app è necessario avere una **sottoscrizione Enterprise Mobility + Security o Azure Active Directory Premium** e gli utenti devono avere la licenza per EMS o Azure AD. Per altre informazioni dettagliate, vedere la [pagina dei prezzi di Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) o la [pagina dei prezzi di Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).


## <a name="supported-apps"></a>App supportate
**Exchange Online**: **Microsoft Outlook** per Android e iOS.

Per informazioni sull'esperienza utente con un'app che usa criteri di accesso condizionale basato sulle app, vedere [Cosa accade quando viene usata un'app con accesso condizionale basato sulle app](use-apps-with-mam-ca.md).


## <a name="next-steps"></a>Passaggi successivi
[Creare criteri di Exchange Online per le app di gestione delle app per dispositivi mobili](mam-ca-for-exchange-online.md)

[Bloccare le app che non usano l'autenticazione moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

