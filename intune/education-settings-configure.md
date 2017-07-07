---
title: Configurare le impostazioni di Windows 10 relative alla formazione con Intune
titleSuffix: Intune on Azure
description: Informazioni su come usare Intune per configurare le impostazioni di Windows 10 relative alla formazione nei dispositivi gestiti."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39aa668794280adc612122e9b2c3c4e7737b65e9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Come configurare le impostazioni di Windows 10 relative alla formazione in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I profili di formazione consentono di specificare i dettagli per configurare l'app Test ed esami di Windows, inclusi i dettagli dell'account e l'URL di test. Quando si configurano queste opzioni, l'app Test ed esami viene aperta con il test specificato e nessun'altra app può essere eseguita sul dispositivo finché il test non è completato.

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione di un profilo di restrizione del dispositivo e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Creare un profilo di dispositivo contenente le impostazioni del profilo di formazione

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
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
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).



