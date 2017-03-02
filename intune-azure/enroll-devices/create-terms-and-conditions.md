---
title: Impostare termini e condizioni in Microsoft Intune | Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: impostare i termini e le condizioni che gli utenti visualizzano nel portale aziendale di Intune. '
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: f7d6ebc9d71a077492ab615a3bc5397e092b1deb
ms.lasthandoff: 02/15/2017

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

