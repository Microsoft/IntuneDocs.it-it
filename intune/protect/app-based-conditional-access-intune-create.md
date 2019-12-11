---
title: Configurare criteri di accesso condizionale basato su app con Intune
titleSuffix: Microsoft Intune
description: Informazioni su come configurare criteri di accesso condizionale basato su app con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712835"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurare criteri di accesso condizionale basato su app con Intune

Configurare criteri di accesso condizionale basato su app per le app incluse nell'elenco di app approvate. L'elenco di app approvate include le applicazioni testate da Microsoft.

Per poter usare i criteri di accesso condizionale basato su app è necessario che i [criteri di protezione delle app di Intune](../apps/app-protection-policies.md) siano applicati alle app in uso.

> [!IMPORTANT]
> Questo articolo illustra in dettaglio i passaggi per aggiungere un criterio di accesso condizionale basato su app. Si possono usare gli stessi passaggi per aggiungere app come SharePoint Online, Microsoft Teams e Microsoft Exchange Online dall'elenco delle app approvate.

## <a name="create-app-based-conditional-access-policies"></a>Creare criteri di accesso condizionale basato su app

L'accesso condizionale è una tecnologia di Azure Active Directory (Azure AD). Il nodo di accesso condizionale accessibile da *Intune* è lo stesso nodo a cui si accede da *Azure AD*. Poiché il nodo è lo stesso, non è necessario spostarsi fra Intune e Azure AD per configurare i criteri.

Per poter creare criteri di accesso condizionale dall'interfaccia di amministrazione di Microsoft Endpoint Manager è necessario avere una licenza Azure AD Premium.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Per creare criteri di accesso condizionale basato su app

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Endpoint Security** > **Accesso condizionale** > **Nuovi criteri**.

3. Immettere un **Nome** per i criteri e quindi in *Assegnazioni* selezionare **Utenti e gruppi**. Usare l'opzione Includi o Escludi per aggiungere i gruppi per il criterio e selezionare **Fatto**.

4. Selezionare **Applicazioni cloud o azioni** e scegliere le app da proteggere. Ad esempio, scegliere **Seleziona le app** e quindi selezionare **Office 365 SharePoint Online**e **Office 365 Exchange Online**.

   Selezionare **Fatto** per salvare le modifiche.

5. Selezionare **Condizioni** > **App client** per applicare il criterio alle app e ai browser. Ad esempio, selezionare **Sì** e quindi abilitare **Browser** e **App per dispositivi mobili e client desktop**.

   Selezionare **Fatto** per salvare le modifiche.

6. In *Controlli di accesso* selezionare **Concedi** per applicare l'accesso condizionale basato sulla conformità del dispositivo. Ad esempio, selezionare **Concedi accesso** > **Richiedi che i dispositivi siano contrassegnati come conformi**.

   Scegliere **OK** per salvare le modifiche.

7. In **Attiva criterio** selezionare **Attivato**, e quindi selezionare **Crea** per salvare le modifiche.





## <a name="next-steps"></a>Passaggi successivi
[Bloccare le app che non usano l'autenticazione moderna](app-modern-authentication-block.md)

## <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](../apps/app-protection-policies.md)
[Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
