---
title: Accesso condizionale con Microsoft Intune
titleSuffix: Microsoft Intune
description: Informazioni su come definire le condizioni che utenti, dispositivi e app devono soddisfare per accedere alle risorse aziendali in Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: cef8bcf74509d83b076b30a1ee7f2406e622b129
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722644"
---
# <a name="learn-about-conditional-access-and-intune"></a>Informazioni sull'accesso condizionale e su Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'accesso condizionale si riferisce ai modi in cui è possibile controllare i dispositivi e le app che sono autorizzati a connettersi alle risorse aziendali e di posta elettronica. Questo argomento illustra l'accesso condizionale basato su dispositivi e app e gli scenari comuni per l'uso dell'accesso condizionale con Intune.

L'accesso condizionale di Enterprise Mobility + Security (EMS) non è un prodotto autonomo, bensì una soluzione usata in tutti i servizi e i prodotti che fanno parte di EMS. Questa soluzione consente un controllo di accesso granulare per la sicurezza dei dati aziendali, oltre a offrire agli utenti un'esperienza che consente loro di operare in modo ottimale da qualsiasi dispositivo e luogo.

È possibile definire condizioni che limitano l'accesso ai dati aziendali in base alla posizione, al dispositivo, allo stato dell'utente e alla sensibilità dell'applicazione.

> [!NOTE] 
> Le funzionalità di accesso condizionale sono estese anche ai [servizi Office 365](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access).

![Diagramma dell'architettura dell'accesso condizionale](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>Usare l'accesso condizionale con Intune

L'accesso condizionale è una funzionalità di Azure Active Directory inclusa con una licenza di Azure Active Directory Premium. Intune contribuisce a migliorare questa funzionalità aggiungendo la conformità dei dispositivi mobili e la gestione delle app per dispositivi mobili alla soluzione. 

![Intune e accesso condizionale quando si usa EMS](./media/conditional-access/intune-with-ca-1.png)

Modi per usare l'accesso condizionale con Intune:

- **Accesso condizionale basato sul dispositivo**

  - Accesso condizionale per Exchange locale

  - Accesso condizionale basato sul controllo di accesso alla rete

  - Accesso condizionale basato sul rischio di dispositivo

  - Accesso condizionale per i PC Windows

    - Dispositivi di proprietà dell'azienda

    - Bring Your Own Device (BYOD)

- **Accesso condizionale basato sulle app**

## <a name="next-steps"></a>Passaggi successivi

[Modi comuni per usare l'accesso condizionale con Intune](conditional-access-intune-common-ways-use.md)
