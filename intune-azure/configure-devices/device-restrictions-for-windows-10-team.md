---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows 10 Team
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune Azure: informazioni sulle restrizioni del dispositivo disponibili con Windows 10 Team.'
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
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 4df8afe50912912e42e03b6b9bc1c397fff2d6db
ms.lasthandoff: 02/18/2017


---

# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

- **Attiva lo schermo quando qualcuno è presente nella stanza** - Consente di riattivare automaticamente il dispositivo quando il sensore rileva la presenza di qualcuno nella stanza.
- **PIN per proiezione wireless** - Specifica se è necessario immettere un PIN prima di usare le funzionalità di proiezione wireless del dispositivo.
- **Proiezione wireless Miracast** - Abilitare questa opzione se si vuole consentire al dispositivo Windows 10 Team di usare i dispositivi abilitati per Miracast per la proiezione.
- **Informazioni sulla riunione visualizzate nella schermata iniziale** - Se si abilita questa opzione, è possibile scegliere le informazioni che verranno visualizzate nel riquadro Riunioni della schermata iniziale. È possibile scegliere le opzioni seguenti:
    - **Mostra solo organizzatore e ora**
    - **Mostra organizzatore, ora e oggetto (l'oggetto è nascosto per le riunioni private)**
- **URL dell'immagine di sfondo della schermata iniziale** - Abilitare questa impostazione per visualizzare uno sfondo personalizzato nella **schermata iniziale** dei dispositivi Windows 10 Team dall'URL specificato.<br>L'immagine deve essere nel formato PNG e l'URL deve iniziare con **https://**.
- **Finestra di manutenzione per gli aggiornamenti** - Configura la finestra durante la quale è possibile eseguire gli aggiornamenti del dispositivo. È possibile configurare l'ora di inizio della finestra e la durata (tra 1 e 5 ore).
- **Azure Operational Insights** - Azure Operational Insights, parte di Microsoft Operations Management Suite, raccoglie, archivia e analizza i dati dei file di log dai dispositivi Windows 10 Team.<br>Per connettersi ad Azure Operational Insights, è necessario specificare un valore per **ID area di lavoro** e **Chiave dell'area di lavoro**.

