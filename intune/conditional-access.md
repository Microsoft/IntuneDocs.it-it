---
title: Accesso condizionale con Microsoft Intune
titlesuffix: ''
description: Informazioni su come definire le condizioni che utenti, dispositivi e app devono soddisfare per accedere alle risorse aziendali in Microsoft Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/06/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a62166792570c5bb81391d05d1cbc3f8486543a4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
