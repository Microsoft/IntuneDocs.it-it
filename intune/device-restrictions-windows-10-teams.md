---
title: Restrizioni dei dispositivi di Microsoft Intune per Windows 10 Team
titleSuffix: ''
description: Informazioni sulle restrizioni disponibili per i dispositivi che eseguono Windows 10 Team.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 20621246f76810ba7efaac3cadbdde1a0229c923
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "71302351"
---
# <a name="microsoft-intune-windows-10-team-device-restriction-settings"></a>Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni relative alle restrizioni dei dispositivi di Microsoft Intune configurabili per i dispositivi che eseguono Windows 10 Team.


## <a name="apps-and-experience"></a>App ed esperienza

- **Attiva lo schermo quando qualcuno è presente nella stanza** - Consente di riattivare automaticamente il dispositivo quando il sensore rileva la presenza di qualcuno nella stanza.
- **Informazioni sulla riunione visualizzate nella schermata iniziale**: se si abilita questa opzione, è possibile scegliere le informazioni che vengono visualizzate nel riquadro Riunioni della schermata iniziale. È possibile scegliere le opzioni seguenti:
  - **Mostra solo organizzatore e ora**
  - **Mostra organizzatore, ora e oggetto (l'oggetto è nascosto per le riunioni private)**
- **URL dell'immagine di sfondo della schermata iniziale** - Abilitare questa impostazione per visualizzare uno sfondo personalizzato nella **schermata iniziale** dei dispositivi Windows 10 Team dall'URL specificato.<br>L'immagine deve essere nel formato PNG e l'URL deve iniziare con **https://** .

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights**: Azure Operational Insights, parte di Microsoft Operations Management Suite, raccoglie, archivia e analizza i dati dei file di log dai dispositivi Windows 10 Team.
Per connettersi ad Azure Operational Insights, è necessario specificare un valore per **ID area di lavoro** e **Chiave dell'area di lavoro**.

## <a name="maintenance"></a>Manutenzione

- **Finestra di manutenzione per gli aggiornamenti** - Configura la finestra durante la quale è possibile eseguire gli aggiornamenti del dispositivo. È possibile configurare l'**ora di inizio** della finestra e la **durata in ore** (tra 1 e 5 ore).

## <a name="wireless-projection"></a>Proiezione wireless

- **PIN per proiezione wireless** - Specifica se è necessario immettere un PIN prima di usare le funzionalità di proiezione wireless del dispositivo.
- **Proiezione wireless Miracast**: per consentire al dispositivo Windows 10 Team di usare i dispositivi abilitati per Miracast per la proiezione, selezionare questa opzione.
- **Canale di proiezione wireless Miracast**: scegliere il canale Miracast che viene usato per stabilire la connessione.


## <a name="next-steps"></a>Passaggi successivi

Usare le informazioni contenute in [Come configurare le impostazioni delle restrizioni dei dispositivi](device-restrictions-configure.md) per salvare e assegnare il profilo a utenti e dispositivi.
