---
title: Accesso condizionale con Microsoft Intune
titlesuffix: ''
description: Informazioni su come definire le condizioni che utenti, dispositivi e app devono soddisfare per accedere alle risorse aziendali in Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 1e9e8db76978f9547d10fd4709d74ea809f2c281
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184846"
---
# <a name="whats-conditional-access"></a>Che cos'è l'accesso condizionale?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'accesso condizionale fa riferimento ai modi con i quali è possibile controllare i dispositivi e le app che sono autorizzati a connettersi alle risorse aziendali e di posta elettronica. In questo argomento viene illustrato l'accesso condizionale basato su dispositivi e app e gli scenari comuni per l'uso dell'accesso condizionale con Intune.

L'accesso condizionale di Enterprise Mobility + Security (EMS) non è un prodotto autonomo, bensì una soluzione usata in tutti i servizi e i prodotti che fanno parte di EMS. Questa soluzione consente un controllo di accesso granulare per la sicurezza dei dati aziendali, oltre a offrire agli utenti un'esperienza che consente loro di operare in modo ottimale da qualsiasi dispositivo e luogo.

È possibile definire condizioni che limitano l'accesso ai dati aziendali in base alla posizione, al dispositivo, allo stato dell'utente e alla sensibilità dell'applicazione.

> [!NOTE] 
> Le funzionalità di accesso condizionale sono estese anche ai [servizi Office 365](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/).

![Diagramma dell'architettura dell'accesso condizionale](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Accesso condizionale con Intune

L'accesso condizionale è una funzionalità di Azure Active Directory inclusa con una licenza di Azure Active Directory Premium. Intune contribuisce a migliorare questa funzionalità aggiungendo la conformità dei dispositivi mobili e la gestione delle app per dispositivi mobili alla soluzione. 

![Intune e accesso condizionale quando si usa EMS](./media/intune-with-ca-1.png)

Modi per usare l'accesso condizionale con Intune:

-   **Accesso condizionale basato sul dispositivo**

    -   Accesso condizionale per Exchange locale

    -   Accesso condizionale basato sul controllo di accesso alla rete

    -   Accesso condizionale basato sul rischio di dispositivo

    -   Accesso condizionale per i PC Windows

        -   Dispositivi di proprietà dell'azienda

        -   Bring your own device (BYOD)

-   **Accesso condizionale basato sull'app**

## <a name="next-steps"></a>Passaggi successivi

[Modi comuni per usare l'accesso condizionale con Intune](conditional-access-intune-common-ways-use.md)
