---
title: Configurare criteri di accesso condizionale basato su app con Intune
titleSuffix: Microsoft Intune
description: Informazioni su come configurare criteri di accesso condizionale basato su app con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9cbe57d0cf69f036cd36d2c1b95c48b198645e7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723086"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurare criteri di accesso condizionale basato su app con Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Configurare criteri di accesso condizionale basato su app per le app incluse nell'elenco di app approvate. L'elenco di app approvate include le applicazioni testate da Microsoft.

> [!IMPORTANT]
> Questo articolo illustra in dettaglio i passaggi per aggiungere un criterio di accesso condizionale basato su app. Si possono usare gli stessi passaggi per aggiungere app come SharePoint Online, Microsoft Teams e Microsoft Exchange Online dall'elenco delle app approvate.

## <a name="create-app-based-conditional-access-policies"></a>Creare criteri di accesso condizionale basato su app
L'accesso condizionale è una tecnologia di Azure Active Directory (Azure AD). Il nodo di accesso condizionale accessibile da *Intune* è lo stesso nodo accessibile da *Azure AD*. Questo significa che non è necessario spostarsi fra Intune e Azure AD per configurare i criteri.

> [!IMPORTANT]
> Per creare criteri di accesso condizionale dal portale di Intune è necessario avere una licenza di Azure AD Premium.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Per creare criteri di accesso condizionale basato su app

> [!IMPORTANT]
> Per poter usare i criteri di accesso condizionale basato su app, è necessario che i [criteri di protezione delle app di Intune](../apps/app-protection-policies.md) siano applicati alle app in uso.

1. Nel **dashboard di Intune** selezionare **Accesso condizionale**.

2. Nel riquadro **Criteri** scegliere **Nuovi criteri** per creare i nuovi criteri di accesso condizionale basato su app.

4. Dopo avere immesso un nome di criterio e dopo avere configurato le impostazioni disponibili nella sezione **Assegnazioni**, scegliere **Concedi** nella sezione **Controlli di accesso**.

5. Scegliere **Richiedi app client approvata**, quindi **Seleziona** e infine **OK** per salvare il nuovo criterio.

## <a name="next-steps"></a>Passaggi successivi
[Bloccare le app che non usano l'autenticazione moderna](app-modern-authentication-block.md)

## <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](../apps/app-protection-policies.md)
[Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
