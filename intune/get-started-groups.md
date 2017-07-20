---
title: Introduzione ai gruppi
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04843a918a3c661ab69dfa711f4d22a8feedf5f3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-groups"></a>Introduzione ai gruppi

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[](./media/generic-users-groups.png)

Microsoft Intune usa Azure Active Directory (Azure AD) per [gestire l'accesso alle risorse aziendali](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups). L'accesso viene controllato tramite ruoli nella directory. Intune gestisce quindi l'accesso per i dispositivi mobili, per consentire ai membri del gruppo di accedere alle risorse.

__Creare un gruppo__

1. Accedere al [portale di Azure](https://portal.azure.com).
2. In **Cerca risorse** cercare **Utenti e gruppi**.
3. Dopo aver aperto il pannello **Utenti e gruppi**, selezionare **Tutti i gruppi**.
4. Nel pannello **Utenti e gruppi - Tutti i gruppi** scegliere il comando **Nuovo gruppo**.
5. Nel pannello **Gruppo** aggiungere un **nome** e una **descrizione** al gruppo.
6. Impostare **Tipo di appartenenza** su **Assegnato**. Non **abilitare le funzionalità di Office** per il gruppo di test.
7. Scegliere **Crea**.

Se un gruppo è stato creato correttamente, verrà visualizzato nell'elenco di **tutti i gruppi**. Se non è incluso nell'elenco, provare a creare un altro gruppo.
