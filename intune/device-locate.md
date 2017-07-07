---
title: Individuare un dispositivo iOS perso con Intune
titleSuffix: Intune on Azure
description: Informazioni su come individuare dispositivi iOS persi o rubati con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 80aa0e5afd1f8862b181d455ff6b545e462f90c9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Individuare dispositivi iOS persi o rubati con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Individua il dispositivo** consente di visualizzare su una mappa la posizione di un dispositivo iOS rubato o smarrito. Deve trattarsi di un dispositivo iOS di proprietà dell'azienda, registrato con DEP, in cui sia attiva la modalità con supervisione. Prima di usare questa azione, è necessario abilitare la [modalità di dispositivo perso](/intune-azure/manage-devices/lost-mode.md).

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS e quindi scegliere l'azione remota **Individua il dispositivo**.
6. Dopo che il dispositivo è stato trovato, la relativa posizione viene visualizzata nel pannello **Individua il dispositivo**.
    ![Pannello Individua il dispositivo](./media/locate-device.png)

>[!NOTE]
>Per motivi di privacy, la distanza di zoom nella mappa è limitata.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informazioni su privacy e sicurezza per le azioni Modalità di dispositivo perso e Individua il dispositivo
- Non vengono inviate informazioni sulla posizione del dispositivo a Intune finché non si attiva questa azione.
- Quando si usa l'azione Individua il dispositivo, le coordinate di latitudine e longitudine del dispositivo vengono inviate a Intune e visualizzate nel portale di Azure.
- I dati vengono archiviati per 24 ore e quindi rimossi. Non è possibile rimuoverli manualmente.
- I dati relativi alla posizione sono crittografati, sia durante il periodo di archiviazione sia quando vengono trasmessi.
- Quando si configura la modalità di dispositivo perso, nel messaggio da visualizzare nella schermata di blocco è opportuno fornire informazioni che possano consentire a qualcuno che trova il dispositivo di renderlo al proprietario.
