---
title: Impostare restrizioni di registrazione in Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: limitare la registrazione dalla piattaforma e impostare un limite di registrazione dei dispositivi in Intune. '
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 56996592febf0be5ab74b158a70404728fe17a4d
ms.lasthandoff: 02/18/2017

---

# <a name="set-enrollment-restrictions"></a>Impostare le restrizioni di registrazione 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

È possibile impostare i tipi e il numero massimo di dispositivi che un utente è autorizzato a registrare. Nel pannello Restrizioni registrazione è possibile impostare:

- Le piattaforme per cui è consentita la registrazione e se bloccare la registrazione dei dispositivi personali per Android e iOS.

- Il numero massimo di dispositivi che un utente è autorizzato a registrare.

## <a name="set-device-type-restrictions"></a>Impostare le restrizioni sul tipo di dispositivi

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi scegliere **Restrizioni registrazione**.

3. In **Restrizioni sul tipo di dispositivi** selezionare **Predefinito**.

4. Nel pannello **Tutti gli utenti** selezionare **Piattaforme**.

5. Per le piattaforme autorizzate alla registrazione in Intune, selezionare **Consenti**. Per le piattaforme di cui si vuole impedire la registrazione, selezionare **Blocca**. Le piattaforme sono impostate su **Consenti** per impostazione predefinita. 

    >[!NOTE]
    >Queste impostazioni non riguardano o bloccano le registrazioni di Windows che usano il client software di Intune. Queste impostazioni riguardano solo la registrazione mediante gestione dei dispositivi mobili. 

6. Selezionare **Salva**.

7. Selezionare **Configurazioni della piattaforma**.

8. Scegliere **Consenti** o **Blocca** per la registrazione dei dispositivi iOS e Android di proprietà personale.

9. Selezionare **Salva**.

## <a name="set-device-limit-restrictions"></a>Impostare le restrizioni sul limite dei dispositivi

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi scegliere **Restrizioni registrazione**.

3. In **Restrizione sul limite di dispositivi** selezionare **Predefinito**.

4. Nel pannello **Tutti gli utenti** selezionare **Limite di dispositivi**.

5. Selezionare il numero massimo di dispositivi che un utente può registrare e quindi selezionare **Salva**.

