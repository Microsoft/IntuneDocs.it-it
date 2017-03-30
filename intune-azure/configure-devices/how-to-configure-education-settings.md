---
title: Configurare le impostazioni di Intune relative alla formazione
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come usare Intune per configurare le impostazioni relative alla formazione nei dispositivi gestiti.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: 5c73719c4fd2805f91c6af3ba48c39f5d798aaeb
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-configure-education-settings-in-microsoft-intune"></a>Come configurare le impostazioni relative alla formazione in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

I profili di formazione consentono di specificare i dettagli per configurare l'app Test ed esami di Windows, inclusi i dettagli dell'account e l'URL di test. Quando si configurano queste opzioni, l'app Test ed esami viene aperta con il test specificato e nessun'altra app può essere eseguita sul dispositivo finché il test non è completato.

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione di un profilo di restrizione del dispositivo e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Creare un profilo di dispositivo contenente le impostazioni del profilo di formazione

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di restrizione del dispositivo.
5. Dall'elenco a discesa **Piattaforma** selezionare **Windows 10 e versioni successive**.
6. Dall'elenco a discesa **Tipo di profilo** selezionare **Profilo di formazione**. 
7. Scegliere Impostazioni > Configura e quindi nel pannello **Test ed esami** configurare quanto segue:
    - **Nome dell'account utente**: immettere il nome utente dell'account usato con Test ed esami. Può trattarsi di un account di dominio, un account Azure Active Directory (AAD) o un account computer locale.
    - **URL della valutazione**: specificare l'URL del test che dovrà essere eseguito dagli utenti. Per altre informazioni, vedere la documentazione relativa a Test ed esami.
    - **Monitoraggio dello schermo**: specificare se si vuole essere in grado di monitorare l'attività dello schermo mentre gli utenti eseguono un test.
    - **Suggerimento di testo**: consentire o bloccare i suggerimenti di testo mentre gli utenti eseguono un test.
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md).




