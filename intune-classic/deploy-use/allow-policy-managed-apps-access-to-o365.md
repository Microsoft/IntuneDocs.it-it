---
title: Accesso condizionale basato su app a Office 365
description: "Informazioni su come l'accesso condizionale per la gestione delle app per dispositivi mobili può essere usato per controllare le app che hanno accesso ai servizi di Office 365."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 78b5d58df44252d1f3916c1d2a2ea02fcb1a10e2
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>Consentire l'accesso ai servizi di Office 365 solo alle app per dispositivi mobili che supportano i criteri di protezione delle app di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I [criteri di protezione delle app di Intune](protect-apps-and-data-with-microsoft-intune.md) consentono di proteggere i dati aziendali sui dispositivi registrati per la gestione in Intune. I criteri di protezione delle app possono essere usati anche nei **dispositivi di proprietà dei dipendenti non registrati per la gestione in Intune**.  In questo caso, anche se il dispositivo non viene gestito, è comunque necessario assicurarsi che i dati e le risorse aziendali siano protetti. Se si usa l'accesso condizionale basato sulle app con il software MAM, è possibile creare criteri che consentano solo alle app per dispositivi mobili che supportano i criteri di protezione delle app di Intune di accedere ai servizi di Office 365 come Exchange Online.

Ad esempio, consentendo solo all'**app di Microsoft Outlook** di accedere a Exchange Online è possibile **bloccare le app di posta elettronica predefinite in iOS e Android** che non hanno la protezione dei dati dei criteri di gestione delle app per dispositivi mobili di Intune per ricevere la posta elettronica da **Exchange Online**. Oppure è possibile impedire alle app per dispositivi mobili che non supportano la gestione di applicazioni mobili di Intune di accedere a **SharePoint Online**.

La figura seguente illustra il flusso usato dai criteri di accesso condizionale basato sulle app per determinare se consentire o bloccare l'accesso: ![Figura che illustra i diversi criteri inclusi per determinare se consentire o bloccare l'accesso](../media/mam-ca-decision-flow_simple.png).

Descrizione delle abbreviazioni usate nei diagrammi:
* **CP**: app Portale aziendale
* **AA**: app Azure Authenticator
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>Prerequisiti
**Prima** di creare criteri di accesso condizionale basati sulle app è necessario avere una **sottoscrizione Enterprise Mobility + Security o Azure Active Directory Premium** e gli utenti devono avere la licenza per EMS o Azure AD. Per altre informazioni dettagliate, vedere la [pagina dei prezzi di Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) o la [pagina dei prezzi di Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).


## <a name="supported-apps"></a>App supportate
**Exchange Online**:
* **Microsoft Outlook** per Android e iOS.

**SharePoint Online**
* Microsoft Word per iOS e Android
* Microsoft Excel per iOS e Android
* Microsoft PowerPoint per iOS e Android
* Microsoft OneDrive for Business per iOS e Android
* Microsoft OneNote per iOS

>[!IMPORTANT]
>Per i dispositivi Android, è necessario accedere a OneDrive o a Outlook per eseguire la registrazione iniziale del dispositivo. OneNote per Android non supporta la gestione di applicazioni mobili se non è stata eseguita la registrazione.

Per informazioni sull'esperienza utente con un'app che usa criteri di accesso condizionale basato sulle app, vedere [Cosa accade quando viene usata un'app con accesso condizionale basato sulle app](use-apps-with-mam-ca.md).


## <a name="next-steps"></a>Passaggi successivi
[Creare criteri di Exchange Online per le app di gestione delle app per dispositivi mobili](mam-ca-for-exchange-online.md)

[Creare criteri di SharePoint Online per le app di gestione delle app per dispositivi mobili](mam-ca-for-sharepoint-online.md)

[Bloccare le app che non usano l'autenticazione moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
