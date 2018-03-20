---
title: Impostazioni di configurazione dei dispositivi di Microsoft Intune condivisi per iOS
titlesuffix: 
description: Informazioni sulle impostazioni di Microsoft Intune che consentono di visualizzare informazioni nella schermata di blocco del dispositivo iOS.
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9147eaff2bd366dbfd86c6422e0f7a29f685db62
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Impostazioni di configurazione del dispositivo condiviso per la visualizzazione di messaggi nella schermata di blocco del dispositivo iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'articolo illustra le impostazioni di Microsoft Intune che consentono di visualizzare informazioni nella schermata di blocco del dispositivo iOS.

Le impostazioni di configurazione del dispositivo condiviso consentono di specificare testo facoltativo visualizzabile nella finestra di accesso e nella schermata di blocco. Ad esempio, è possibile immettere il messaggio "In caso di ritrovamento, restituire a" e informazioni sui tag asset. 

>[!IMPORTANT]
> Questa funzionalità è supportata sui dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

## <a name="create-shared-device-settings"></a>Creare impostazioni per il dispositivo condiviso

1. Da [Intune nel portale di Azure](https://portal.azure.com) passare a [**Funzionalità del dispositivo** nell'area di configurazione del dispositivo](device-features-configure.md). 
1. Nel riquadro **Funzionalità del dispositivo** scegliere **Configurazione del dispositivo condiviso (solo con supervisione)**.
2. Nel riquadro **Configurazione del dispositivo condiviso (solo con supervisione)** configurare le impostazioni seguenti:
    - **Informazioni sui tag asset**: immettere informazioni sul tag asset del dispositivo. Ad esempio: **Proprietà di Contoso Corp**. Le informazioni immesse vengono applicate a tutti i dispositivi ai quali viene assegnato questo profilo.
    - **Nota a piè di pagina della schermata di blocco**: immettere una nota che può contribuire alla restituzione del dispositivo in caso di furto o smarrimento. Ad esempio: **In caso di ritrovamento, chiamare "numero"**.
3. Al termine, scegliere **OK** fino a tornare al riquadro **Crea profilo** e scegliere **Crea**. 


## <a name="next-steps"></a>Passaggi successivi

È ora possibile assegnare il profilo del dispositivo ai gruppi selezionati. Per informazioni dettagliate, vedere [How to assign device profiles](device-profile-assign.md) (Come assegnare profili di dispositivo).
