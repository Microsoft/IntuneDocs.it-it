---
title: Configurare criteri di accesso condizionale basato su app con Intune
titleSuffix: Microsoft Intune
description: Informazioni su come configurare criteri di accesso condizionale basato su app con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1514fe9dfcd09e2b77967b0fed8c36fb7a06634f
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567491"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurare criteri di accesso condizionale basato su app con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configurare criteri di accesso condizionale basato su app per le app che fanno parte dell'elenco di app approvate. L'elenco di app approvate include le applicazioni testate da Microsoft.

> [!IMPORTANT]
> Questo articolo illustra in dettaglio i passaggi per aggiungere un criterio di accesso condizionale basato su app. Si possono usare gli stessi passaggi per aggiungere app come SharePoint Online, Microsoft Teams e Microsoft Exchange Online dall'elenco delle app approvate.

## <a name="create-app-based-conditional-access-policies"></a>Creare criteri di accesso condizionale basato su app
L'accesso condizionale è una tecnologia di Azure Active Directory (Azure AD). Il nodo di accesso condizionale accessibile da *Intune* è lo stesso nodo accessibile da *Azure AD*. Questo significa che non è necessario spostarsi fra Intune e Azure AD per configurare i criteri.

> [!IMPORTANT]
> È necessario avere una licenza di Azure AD Premium per creare criteri di accesso condizionale dal portale di Intune.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Per creare criteri di accesso condizionale basato su app

> [!IMPORTANT]
> Per potere usare i criteri di accesso condizionale basato su app, è prima di tutto necessario che i [criteri di protezione delle app di Intune](app-protection-policies.md) siano applicati alle app.

1. Nel **dashboard di Intune** selezionare **Accesso condizionale**.

2. Nel pannello **Criteri** scegliere **Nuovi criteri** per creare i nuovi criteri di accesso condizionale basato su app.

4. Dopo avere immesso un nome di criterio e dopo avere configurato le impostazioni disponibili nella sezione **Assegnazioni**, scegliere **Concedi** nella sezione **Controlli di accesso**.

5. Scegliere **Richiedi app client approvata**, quindi **Seleziona** e infine **OK** per salvare il nuovo criterio.

## <a name="next-steps"></a>Passaggi successivi
[Bloccare le app che non usano l'autenticazione moderna](app-modern-authentication-block.md)

### <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](app-protection-policies.md)
[Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
