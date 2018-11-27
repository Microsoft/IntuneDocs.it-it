---
title: Configurare criteri di accesso condizionale basato su app con Intune
description: Informazioni su come configurare criteri di accesso condizionale basato su app con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 32044422943282d9cf813192405a335ee756e44e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52177932"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurare criteri di accesso condizionale basato su app con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configurare criteri di accesso condizionale basato su app per le app che fanno parte dell'elenco di app approvate. L'elenco di app approvate include le applicazioni testate da Microsoft.

> [!IMPORTANT]
> Questo articolo illustra in dettaglio i passaggi per aggiungere un criterio di accesso condizionale basato su app. Si possono usare gli stessi passaggi per aggiungere app come SharePoint Online, Microsoft Teams e Microsoft Exchange Online dall'elenco delle app approvate.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Creare criteri di accesso condizionale basato su app in un carico di lavoro di Azure AD

Gli amministratori IT possono creare criteri di accesso condizionale basato su app dal carico di lavoro di Azure AD. Con questo accesso non è necessario spostarsi tra i carichi di lavoro di Azure e Intune.

> [!IMPORTANT]
> È necessario avere una licenza di Azure AD Premium per creare criteri di accesso condizionale di Azure AD dal portale di Intune di Azure.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Per creare criteri di accesso condizionale basato su app

> [!IMPORTANT]
> Per potere usare i criteri di accesso condizionale basato su app, è prima di tutto necessario che i [criteri di protezione delle app di Intune](app-protection-policies.md) siano applicati alle app.

1. Nel **dashboard di Intune** scegliere **Accesso condizionale**.

2. Nel pannello **Criteri** scegliere **Nuovi criteri** per creare i nuovi criteri di accesso condizionale basato su app.

4. Dopo avere immesso un nome di criterio e dopo avere configurato le impostazioni disponibili nella sezione **Assegnazioni**, scegliere **Concedi** nella sezione **Controlli di accesso**.

5. Scegliere **Richiedi app client approvata**, quindi **Seleziona** e infine **OK** per salvare il nuovo criterio.

## <a name="next-steps"></a>Passaggi successivi
[Bloccare le app che non usano l'autenticazione moderna](app-modern-authentication-block.md)

### <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](app-protection-policies.md)
[Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
