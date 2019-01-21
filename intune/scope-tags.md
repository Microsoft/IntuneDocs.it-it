---
title: Filtrare i criteri con tag di ambito in Microsoft Intune - Azure | Microsoft Docs
description: Usare i tag di ambito per filtrare i profili di configurazione in base a ruoli specifici.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0da6861b6c49fc37691b8c6e464a506670643fa3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203332"
---
# <a name="use-scope-tags-to-filter-policies"></a>Usare i tag di ambito per filtrare i criteri

I tag di ambito consentono di filtrare i criteri con tag personalizzati creati dall'utente. È possibile applicare i tag di ambito a ruoli e app.

Ad esempio, creare un tag di ambito denominato "Reparto tecnico" e assegnarlo ai profili di configurazione correlati al reparto tecnico. Assegnare lo stesso tag a un ruolo "Amministratori reparto tecnico". Vedranno solo i criteri con il tag "Reparto tecnico".

## <a name="to-create-a-scope-tag"></a>Per creare un tag di ambito

Scegliere **Ruoli** > **Ambito (tag)** > **Crea**.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Per aggiungere un tag di ambito a un profilo di configurazione

Scegliere **Configurazione del dispositivo** > **Profili** > scegliere un profilo > **Proprietà** > **Ambito (tag)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Per assegnare un tag di ambito a un ruolo

Scegliere **Ruoli** > **Tutti i ruoli** > **Policy and Profile Manager (Gestione criteri e profili)** > **Assegnazioni**  >  **Ambito (tag)**.

## <a name="to-assign-a-scope-tag-to-an-app"></a>Per assegnare un tag di ambito a un'app

Scegliere **App client** > **App** > scegliere un'app > **Proprietà** > **Ambito (tag)** > **Aggiungi** > scegliere i tag > **Selezionare** > **OK** > **Salva**.


## <a name="next-steps"></a>Passaggi successivi

Gestire i propri [ruoli](role-based-access-control.md) e [profili](device-profile-assign.md).

