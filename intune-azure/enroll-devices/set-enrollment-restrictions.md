---
title: Impostare le restrizioni di registrazione in Intune | Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: limitare la registrazione dalla piattaforma e impostare un limite di registrazione dei dispositivi in Intune. '
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 1bdefce35c20ce24b94ee701a2d13b5408f435ce

---

# <a name="set-enrollment-restrictions"></a>Impostare le restrizioni di registrazione 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

È possibile limitare i tipi di dispositivi autorizzati alla registrazione in Intune specificando le piattaforme consentite. È anche possibile impostare il numero massimo di dispositivi che un utente è autorizzato a registrare.

## <a name="set-device-type-restrictions"></a>Impostare le restrizioni sul tipo di dispositivi

1. Nel portale di Azure scegliere **Altri servizi**, immettere **Intune** nella casella di testo e quindi scegliere **Altro** > **Intune**

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Restrizioni registrazione**.

3. In **Restrizioni sul tipo di dispositivi** selezionare **Predefinito**.

4. Nel pannello **Tutti gli utenti** selezionare **Piattaforme**.

5. Per le piattaforme autorizzate alla registrazione in Intune, selezionare **Consenti**. Per le piattaforme di cui si desidera impedire la registrazione, selezionare **Blocca**.

6. Selezionare **Salva**.

7. Selezionare **Configurazioni della piattaforma**.

8. Scegliere se consentire o bloccare la registrazione per i dispositivi iOS di proprietà personale.

9. Selezionare **Salva**.

## <a name="set-device-limit-restrictions"></a>Impostare le restrizioni sul limite dei dispositivi

1. Nel pannello Intune del portale di Azure scegliere **Registra i dispositivi** e quindi scegliere **Restrizioni registrazione**.

2. In **Restrizione sul limite di dispositivi** selezionare **Predefinito**.

3. Nel pannello **Tutti gli utenti** selezionare **Limite di dispositivi**.

4. Selezionare il numero massimo di dispositivi che un utente può registrare e quindi selezionare **Salva**.



<!--HONumber=Feb17_HO1-->


