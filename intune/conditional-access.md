---
title: Accesso condizionale con Intune
titleSuffix: Intune on Azure
description: Informazioni su come definire le condizioni che utenti e dispositivi devono soddisfare per accedere alle risorse aziendali in Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f6f7443224b9ec114f0323d1715f343b0adfec4
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2017
---
# <a name="whats-conditional-access"></a>Che cos'è l'accesso condizionale?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo argomento descrive l'accesso condizionale applicato a Enterprise Mobility + Security (EMS) e, a seguire, gli scenari comuni di accesso condizionale quando si usa Intune.

L'accesso condizionale di Enterprise Mobility + Security (EMS) non è un prodotto autonomo, bensì una soluzione usata in tutti i servizi e i prodotti che fanno parte di EMS. Questa soluzione consente un controllo di accesso granulare per la sicurezza dei dati aziendali, oltre a offrire agli utenti un'esperienza che consente loro di operare in modo ottimale da qualsiasi dispositivo e luogo.

È possibile definire condizioni che limitano l'accesso ai dati aziendali in base alla posizione, al dispositivo, allo stato dell'utente e alla sensibilità dell'applicazione.

> [!NOTE] 
> Le funzionalità di accesso condizionale sono estese anche ai [servizi Office 365](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/).

![Diagramma dell'architettura dell'accesso condizionale](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Accesso condizionale con Intune

Intune aggiunge criteri per la conformità dei dispositivi mobili e per la gestione delle app a supporto della soluzione di accesso condizionale di EMS.

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