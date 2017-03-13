---
title: Impostare i termini e le condizioni in Microsoft Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: impostare i termini e le condizioni che gli utenti visualizzano nel portale aziendale di Intune. '
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 07a42cf8fa10d3223129fbb2932217ff90ac365b
ms.lasthandoff: 02/18/2017

---

# <a name="set-terms-and-conditions"></a>Impostare termini e condizioni 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

È possibile distribuire termini e condizioni di Intune a gruppi di utenti per spiegare in che modo la registrazione, l'accesso alle risorse di lavoro e l'uso dell'app Portale aziendale influiscono su dispositivi e utenti. Gli utenti dovranno quindi accettare i termini e le condizioni prima di poter usare il portale aziendale per registrare le app e accedere al lavoro.

È possibile creare e distribuire più criteri contenenti termini e condizioni diversi. È anche possibile creare versioni degli stessi termini e condizioni in lingue diverse e distribuirle ai gruppi appropriati.

**Per creare termini e condizioni**:

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi scegliere **Termini e condizioni**.

3. Selezionare **Crea**.

4. Nel pannello **Crea termini e condizioni** specificare le informazioni seguenti:

   - **Nome visualizzato**: nome da usare per i termini. Nome visualizzato dagli utenti nell'app del Portale aziendale.

   - **Descrizione**: dettagli facoltativi che consentono di identificare il criterio nel portale di Azure.

5. Selezionare la freccia accanto a Define terms of use (Definisci le condizioni per l'utilizzo) per aprire il pannello Termini e condizioni, quindi immettere le informazioni seguenti:

   - **Titolo**: il titolo visualizzato dagli utenti nel Portale aziendale.

   - **Riepilogo delle condizioni:** testo che spiega il significato dell'accettazione da parte degli utenti.

   - **Termini e condizioni**: etichetta legale che gli utenti visualizzano e devono accettare o rifiutare, ad esempio "Accetto i termini e condizioni".

6. Selezionare **Ok**.

