---
title: "Attivare la modalità di dispositivo perso iOS con Intune"
titleSuffix: Intune on Azure
description: "Informazioni su come usare Intune per attivare la modalità di dispositivo perso nei dispositivi iOS smarriti o rubati.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a34d008ae76355578c6f24a932c9e1e501d5b46b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="activate-lost-mode-on-ios-devices"></a>Attivare la modalità di dispositivo perso nei dispositivi iOS


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Modalità di dispositivo perso** consente di abilitare la modalità di dispositivo perso nei dispositivi iOS smarriti o rubati. Questa modalità consente di specificare un messaggio e un numero di telefono che verranno visualizzati nella schermata di blocco del dispositivo.

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS e quindi scegliere l'azione remota **Modalità di dispositivo perso**.
6. Nel pannello **Modalità di dispositivo perso** abilitare questa modalità, immettere il messaggio che verrà visualizzato e, facoltativamente, indicare un numero di telefono di contatto.
7. Fare clic su **OK**.

Quando si abilita la modalità di dispositivo perso, si blocca qualsiasi uso del dispositivo. L'utente finale non può accedere al dispositivo finché l'amministratore non disabilita questa modalità. Quando la modalità di dispositivo perso è abilitata, è possibile usare l'azione **Individua il dispositivo** per scoprire dove si trova il dispositivo.
Per usare la modalità di dispositivo perso è necessario un dispositivo iOS di proprietà dell'azienda, registrato con DEP, in cui sia attiva la modalità con supervisione.

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informazioni su privacy e sicurezza per le azioni Modalità di dispositivo perso e Individua il dispositivo
- Non vengono inviate informazioni sulla posizione del dispositivo a Intune finché non si attiva questa azione.
- Quando si usa l'azione Individua il dispositivo, le coordinate di latitudine e longitudine del dispositivo vengono inviate a Intune e visualizzate nel portale di Azure.
- I dati vengono archiviati per 24 ore e quindi rimossi. Non è possibile rimuoverli manualmente.
- I dati relativi alla posizione sono crittografati, sia durante il periodo di archiviazione sia quando vengono trasmessi.
- Quando si configura la modalità di dispositivo perso, nel messaggio da visualizzare nella schermata di blocco è opportuno fornire informazioni che possano consentire a qualcuno che trova il dispositivo di renderlo al proprietario.

