---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows 10 Team
titleSuffix: Intune on Azure
description: Informazioni sulle restrizioni del dispositivo disponibili per dispositivi Windows 10 Team."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7a5c3eaf3d2b1fc4383282473352124c793b666f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

- **Attiva lo schermo quando qualcuno è presente nella stanza** - Consente di riattivare automaticamente il dispositivo quando il sensore rileva la presenza di qualcuno nella stanza.
- **PIN per proiezione wireless** - Specifica se è necessario immettere un PIN prima di usare le funzionalità di proiezione wireless del dispositivo.
- **Proiezione wireless Miracast** - Abilitare questa opzione se si vuole consentire al dispositivo Windows 10 Team di usare i dispositivi abilitati per Miracast per la proiezione.
- **Informazioni sulla riunione visualizzate nella schermata iniziale** - Se si abilita questa opzione, è possibile scegliere le informazioni che verranno visualizzate nel riquadro Riunioni della schermata iniziale. È possibile scegliere le opzioni seguenti:
    - **Mostra solo organizzatore e ora**
    - **Mostra organizzatore, ora e oggetto (l'oggetto è nascosto per le riunioni private)**
- **URL dell'immagine di sfondo della schermata iniziale** - Abilitare questa impostazione per visualizzare uno sfondo personalizzato nella **schermata iniziale** dei dispositivi Windows 10 Team dall'URL specificato.<br>L'immagine deve essere nel formato PNG e l'URL deve iniziare con **https://**.
- **Finestra di manutenzione per gli aggiornamenti** - Configura la finestra durante la quale è possibile eseguire gli aggiornamenti del dispositivo. È possibile configurare l'ora di inizio della finestra e la durata (tra 1 e 5 ore).
- **Azure Operational Insights** - Azure Operational Insights, parte di Microsoft Operations Management Suite, raccoglie, archivia e analizza i dati dei file di log dai dispositivi Windows 10 Team.<br>Per connettersi ad Azure Operational Insights, è necessario specificare un valore per **ID area di lavoro** e **Chiave dell'area di lavoro**.
