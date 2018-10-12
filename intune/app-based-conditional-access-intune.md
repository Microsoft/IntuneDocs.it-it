---
title: Accesso condizionale basato su app con Intune
description: Informazioni su come funziona l'accesso condizionale basato su app con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 95458642f60dfb8c7ba18078ef4bd238c53502aa
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231305"
---
# <a name="app-based-conditional-access-with-intune"></a>Accesso condizionale basato su app con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I [criteri di protezione delle app di Intune](app-protection-policy.md) consentono di proteggere i dati aziendali sui dispositivi registrati in Intune. I criteri di protezione delle app possono essere usati anche nei dispositivi di proprietà dei dipendenti non registrati per la gestione in Intune. In questo caso, anche se il dispositivo non viene gestito dall'azienda, è comunque necessario assicurarsi che i dati e le risorse aziendali siano protetti.

L'accesso condizionale basato su app e la gestione delle app client consentono di aggiungere un livello di sicurezza, garantendo che solo le app client che supportano i criteri di protezione delle app di Intune possano accedere a Exchange Online e agli altri servizi di Office 365.

> [!NOTE]
> Un'app gestita è un'app a cui sono applicati criteri di protezione delle app e che può essere gestita da Intune.

Consentendo solo all'app Microsoft Outlook di accedere a Exchange Online, è possibile bloccare le app di posta elettronica predefinite in iOS e Android. È inoltre possibile impedire di accedere a SharePoint Online alle app a cui non sono applicati criteri di protezione delle app di Intune.

## <a name="prerequisites"></a>Prerequisiti
Prima di creare un criterio di accesso condizionale basato su app, sono necessari:

- **Enterprise Mobility + Security (EMS)** o una **sottoscrizione Azure Active Directory (AD) Premium**
- Gli utenti devono avere la licenza per EMS o Azure AD

Per altre informazioni, vedere i [prezzi di Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) o i [prezzi di Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>App supportate

Un elenco di app che supportano l'accesso condizionale basato su app è disponibile nella [documentazione di riferimento tecnico per l'accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

L'accesso condizionale basato su app [supporta anche le app line-of-business (LOB)](app-modern-authentication-block.md), ma queste app devono usare l'[autenticazione moderna di Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a). 

## <a name="how-app-based-conditional-access-works"></a>Funzionamento dell'accesso condizionale basato su app

In questo esempio, l'amministratore ha applicato criteri di protezione delle app all'app Outlook, seguiti da una regola di accesso condizionale che aggiunge l'app Outlook a un elenco approvato di app che possono essere usate per l'accesso alla posta elettronica aziendale.

> [!NOTE]
> Per le altre app gestite è possibile usare la struttura del diagramma di flusso riportata di seguito.

![Processo di accesso condizionale basato su app illustrato in un diagramma di flusso](./media/ca-intune-common-ways-3.png)

1. L'utente tenta di eseguire l'autenticazione in Azure AD dall'app Outlook.

2. L'utente viene reindirizzato all'App Store per installare un'app broker quando tenta di eseguire l'autenticazione per la prima volta. L'app broker può essere Microsoft Authenticator per iOS o il Portale aziendale Microsoft per i dispositivi Android.

   Se gli utenti tentano di usare un'app di posta elettronica nativa, vengono reindirizzati all'App Store per installare l'app Outlook.

3. L'app broker viene installata nel dispositivo.

4. L'app broker avvia il processo di registrazione di Azure AD, che crea un record di dispositivo in Azure AD. Si tratta di un processo diverso dalla registrazione per la gestione di dispositivi mobili (MDM), ma questo record è necessario per applicare i criteri di accesso condizionale nel dispositivo.

5. L'app broker verifica l'identità dell'app. È presente un livello di sicurezza, in modo che l'app broker possa verificare se l'app è autorizzata per l'uso da parte dell'utente.

6. L'app broker invia l'ID client dell'app ad Azure AD nell'ambito del processo di autenticazione utente per verificare se è incluso nell'elenco dei criteri approvati.

7. Azure AD consente all'utente di eseguire l'autenticazione e di usare l'app in base all'elenco dei criteri approvati. Se l'app non è presente nell'elenco, Azure AD nega l'accesso all'app.

8. L'app Outlook comunica con il servizio cloud di Outlook per avviare la comunicazione con Exchange Online.

9. Il servizio cloud di Outlook comunica con Azure AD per recuperare i token di accesso del servizio Exchange Online per l'utente.

10. L'app Outlook comunica con Exchange Online per recuperare la posta elettronica aziendale dell'utente.

11. La posta elettronica aziendale viene recapitata nella cassetta postale dell'utente.

## <a name="next-steps"></a>Passaggi successivi
[Creare criteri di accesso condizionale basato su app](app-based-conditional-access-intune-create.md)

[Bloccare le app che non usano l'autenticazione moderna](app-modern-authentication-block.md)
