---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows 10 Team
titlesuffix: Azure portal
description: Informazioni sulle restrizioni del dispositivo disponibili per dispositivi Windows 10 Team."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 33142a4e7b95d8b689ab85ef6a25e56fd365aa82
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="apps-and-experience"></a>App ed esperienza

- **Attiva lo schermo quando qualcuno è presente nella stanza** - Consente di riattivare automaticamente il dispositivo quando il sensore rileva la presenza di qualcuno nella stanza.
- **Informazioni sulla riunione visualizzate nella schermata iniziale**: se si abilita questa opzione, è possibile scegliere le informazioni che vengono visualizzate nel riquadro Riunioni della schermata iniziale. È possibile scegliere le opzioni seguenti:
    - **Mostra solo organizzatore e ora**
    - **Mostra organizzatore, ora e oggetto (l'oggetto è nascosto per le riunioni private)**
- **URL dell'immagine di sfondo della schermata iniziale** - Abilitare questa impostazione per visualizzare uno sfondo personalizzato nella **schermata iniziale** dei dispositivi Windows 10 Team dall'URL specificato.<br>L'immagine deve essere nel formato PNG e l'URL deve iniziare con **https://**.

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights**: Azure Operational Insights, parte di Microsoft Operations Management Suite, raccoglie, archivia e analizza i dati dei file di log dai dispositivi Windows 10 Team.
Per connettersi ad Azure Operational Insights, è necessario specificare un valore per **ID area di lavoro** e **Chiave dell'area di lavoro**.

## <a name="maintenance"></a>Manutenzione

- **Finestra di manutenzione per gli aggiornamenti** - Configura la finestra durante la quale è possibile eseguire gli aggiornamenti del dispositivo. È possibile configurare l'**ora di inizio** della finestra e la **durata in ore** (tra 1 e 5 ore).

## <a name="wireless-projection"></a>Proiezione wireless

- **PIN per proiezione wireless** - Specifica se è necessario immettere un PIN prima di usare le funzionalità di proiezione wireless del dispositivo.
- **Proiezione wireless Miracast**: per consentire al dispositivo Windows 10 Team di usare i dispositivi abilitati per Miracast per la proiezione, selezionare questa opzione.
- **Canale di proiezione wireless Miracast**: scegliere il canale Miracast che verrà usato per stabilire la connessione.


## <a name="next-steps"></a>Passaggi successivi

Usare le informazioni contenute in [Come configurare le impostazioni delle restrizioni dei dispositivi](device-restrictions-configure.md) per salvare e assegnare il profilo a utenti e dispositivi.
