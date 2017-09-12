---
title: Impostazioni di configurazione dei dispositivi di Intune condivisi per iOS
titlesuffix: Azure portal
description: Informazioni sulle impostazioni di Intune che consentono di visualizzare informazioni nella schermata di blocco del dispositivo iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bf1547115a1c5d15890504c26a9d1086df489718
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Impostazioni di configurazione del dispositivo condiviso per la visualizzazione di messaggi nella schermata di blocco del dispositivo iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le impostazioni di configurazione del dispositivo condiviso consentono di specificare testo facoltativo visualizzabile nella finestra di accesso e nella schermata di blocco. Ad esempio, è possibile immettere il messaggio "In caso di ritrovamento, restituire a" e informazioni sui tag asset. 

>[!IMPORTANT]
> Questa funzionalità è supportata sui dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

## <a name="create-shared-device-settings"></a>Creare impostazioni per il dispositivo condiviso

1. Nel pannello **Funzionalità de dispositivo** scegliere **Configurazione del dispositivo condiviso (solo con supervisione)**.
2. Nel pannello **Configurazione del dispositivo condiviso (solo con supervisione)** configurare le seguenti impostazioni:
    - **Informazioni sui tag asset**: immettere informazioni sul tag asset del dispositivo. Ad esempio: **Proprietà di Contoso Corp**. Le informazioni immesse vengono applicate a tutti i dispositivi ai quali viene assegnato questo profilo.
    - **Nota a piè di pagina della schermata di blocco**: immettere una nota che può contribuire alla restituzione del dispositivo in caso di furto o smarrimento. Ad esempio: **In caso di ritrovamento, chiamare "numero"**.
3. Al termine, fare clic su **OK** fino a tornare al pannello **Crea profilo**, quindi scegliere **Crea**. 


## <a name="next-steps"></a>Passaggi successivi

È ora possibile assegnare il profilo del dispositivo ai gruppi selezionati. Per informazioni dettagliate, vedere [How to assign device profiles](device-profile-assign.md) (Come assegnare profili di dispositivo).
