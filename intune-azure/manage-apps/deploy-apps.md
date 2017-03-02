---
title: Come assegnare app ai gruppi | Anteprima di Intune in Azure | Documentazione Microsoft
description: "Anteprima di Intune in Azure: dopo aver aggiunto un&quot;app a Intune, è opportuno assegnarla ai gruppi di utenti o dispositivi."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 638ad0d87c19c9e40e96b42d18e5c4342f40a156
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Come assegnare app ai gruppi con Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Dopo aver aggiunto un'app a Intune, è necessario distribuirla a utenti e dispositivi, assegnandola a essi.

Le app possono essere assegnate ai dispositivi gestiti o non gestiti da Intune. Usare la tabella seguente per comprendere le varie opzioni per l'assegnazione di applicazioni a utenti e dispositivi:

||||
|-|-|-|-|
|&nbsp;|Dispositivi registrati con Intune|Dispositivi non registrati con Intune|
|Assegnazione a utenti|sì|sì|
|Assegnazione a dispositivi|sì|No|
|Assegnazione di app sottoposte a wrapping o app che includa l'SDK Intune (per i criteri di protezione delle app)|sì|sì|
|Assegnazione di app come Disponibili|sì|sì|
|Assegnazione di app come Obbligatorio|sì|No|
|Disinstallazione di app|sì|sì|
|Installazione di app disponibili sull'app Portale aziendale da parte degli utenti finali|sì|No|
|Installazione di app disponibili sul portale aziendale basato su Web da parte degli utenti finali|sì|sì|

> [!NOTE]
> Attualmente, è possibile assegnare app iOS e Android (sia linea di business che acquistate nello store) a dispositivi non registrati con Intune.

## <a name="how-to-assign-an-app"></a>Come assegnare un'applicazione

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
1. Nel carico di lavoro **Gestisci le app** scegliere **Gestisci** > **App**.
2. Nel pannello dell'elenco delle app fare clic sull'app da assegnare.
3. Nel pannello <*nome app*> - **Panoramica** scegliere **Gestisci** > **Assegnazioni**.
4. Scegliere **Seleziona gruppi** e quindi nel pannello **Selezionare i gruppi** scegliere i gruppi Azure AD a cui assegnare l'app.
5. Per ogni app scelta, scegliere un **Tipo di assegnazione** per l'applicazione tra:
    - **Disponibile**: gli utenti installano l'app dall'app Portale aziendale o dal relativo sito Web.
    - **Non applicabile**: l'app non è installata o visualizzata nel portale aziendale.
    - **Obbligatoria**: l'applicazione è installata sui dispositivi nei gruppi selezionati.
    - **Disinstalla**: l'applicazione è disinstallata sui dispositivi nei gruppi selezionati.
    - **Available with or without enrollment** (Disponibile con o senza registrazione): assegnare questa app a gruppi di utenti i cui dispositivi non sono registrati con Intune. Per un aiuto, vedere la tabella in alto.
6. Al termine, scegliere **Salva**.

L'app è ora assegnata al gruppo scelto.

Vedere [How to monitor apps](monitor-apps.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni di app.

