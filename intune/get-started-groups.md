---
title: Creare un gruppo in Microsoft Intune
titleSuffix: 
description: Organizzare gli utenti in gruppi per semplificare la gestione dei criteri e delle app a cui possono accedere.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4fc4ee80b1cf5a8422d135d13a9fb498980500b5
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>Creare un gruppo per gestire gli utenti e l'accesso ai dati

I gruppi vengono usati per gestire gli utenti e controllare l'accesso dei dipendenti alle risorse aziendali. Queste risorse possono essere parte della directory o essere risorse esterne, ad esempio app SaaS o siti SharePoint.

Microsoft Intune usa Azure Active Directory (Azure AD) per gestire l'accesso alle risorse aziendali. L'accesso viene controllato tramite ruoli nella directory. Intune gestisce quindi l'accesso per i dispositivi mobili, per consentire ai membri del gruppo di accedere alle risorse.

## <a name="how-do-i-create-a-group"></a>Come si crea un gruppo?

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Dopo aver aperto il riquadro **Microsoft Intune** selezionare **Gruppi**.
4. Nel riquadro **Utenti e gruppi - Tutti i gruppi** scegliere il comando **Nuovo gruppo**.
5. Nel riquadro **Gruppo** scegliere **Tipo di gruppo**.
5. Immettere un **nome** e una **descrizione** per il gruppo.
6. Impostare **Tipo di appartenenza** su **Assegnato**. Non **abilitare le funzionalità di Office** per il gruppo di test.
7. Selezionare i **membri** per il gruppo.
7. Scegliere **Crea**.

Se un gruppo è stato creato correttamente, verrà visualizzato nell'elenco di **tutti i gruppi**. Se non è incluso nell'elenco, provare a creare un altro gruppo.

## <a name="next-steps"></a>Passaggi successivi

[Introduzione ai criteri](get-started-policies.md): illustra come creare criteri per impedire agli utenti di eseguire operazioni non autorizzate con i propri dispositivi.

## <a name="learn-more"></a>Altre informazioni

* [Impostare restrizioni di registrazione tramite i gruppi in Intune](groups-add.md)
* [Gestire l'accesso alle risorse aziendali tramite i gruppi in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
