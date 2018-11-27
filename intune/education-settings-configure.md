---
title: Configurare le impostazioni di Windows 10 relative alla formazione con Intune
titleSuffix: Microsoft Intune
description: Informazioni su come usare Intune per configurare le impostazioni di Windows 10 relative alla formazione nei dispositivi gestiti.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 120aca8dae457748fea322ce164aa663ffa7e748
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187379"
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Come configurare le impostazioni di Windows 10 relative alla formazione in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I profili di formazione consentono di specificare i dettagli per configurare l'app Test ed esami di Windows, inclusi i dettagli dell'account e l'URL di test. Quando si configurano queste opzioni, l'app Test ed esami viene aperta con il test specificato e nessun'altra app può essere eseguita sul dispositivo finché il test non è completato.

Per informazioni dettagliate su 	Test ed esami, vedere [Test ed esami in Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Creare un profilo di dispositivo contenente le impostazioni del profilo di formazione

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
3. Nel riquadro dei profili scegliere **Crea profilo**.
4. Nella pagina **Crea profilo** immettere **Nome** e **Descrizione** per il profilo di restrizione del dispositivo.
5. Dall'elenco a discesa **Piattaforma** selezionare **Windows 10 e versioni successive**.
6. Dall'elenco a discesa **Tipo di profilo** selezionare **Profilo di formazione**. 
7. Scegliere **Impostazioni > Configura** e nel riquadro **Test ed esami** configurare quanto segue:
    - **Tipo di account**: selezionare un tipo di account dal campo a discesa.
    - **Nome dell'account utente**: immettere il nome utente dell'account usato con Test ed esami. Può trattarsi di un account di dominio, un account Azure Active Directory (AAD) o un account computer locale.
    - **URL della valutazione**: specificare l'URL del test che dovrà essere eseguito dagli utenti. Per altre informazioni, vedere la documentazione relativa a Test ed esami.
    - **Monitoraggio dello schermo**: specificare se si vuole essere in grado di monitorare l'attività dello schermo mentre gli utenti eseguono un test.
    - **Suggerimento di testo**: consentire o bloccare i suggerimenti di testo mentre gli utenti eseguono un test.
8. Al termine tornare al riquadro **Crea profilo** e scegliere **Crea**.

Il profilo verrà creato e visualizzato nel riquadro dell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).



