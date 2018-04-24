---
title: Impostazioni dei criteri di configurazione di Windows Team
description: Usare i **criteri di configurazione generale di Windows 10 Team** di Microsoft Intune per configurare le impostazioni per i dispositivi Windows 10 Team registrati, ad esempio Microsoft Surface Hub.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 70b1091cd58439b7d42eab1a612b0b63ca39103d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di configurazione di Windows Team in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Usare i **criteri di configurazione generale di Windows 10 Team** di Microsoft Intune per configurare le impostazioni per i dispositivi Windows 10 Team registrati, ad esempio Microsoft Surface Hub.


|                                  Nome impostazione                                   |                                                                                                                                                                Dettagli                                                                                                                                                                |
|---------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <strong>Consenti riattivazione automatica dello schermo se qualcuno è presente nella stanza</strong>   |                                                                                                                         Consente di riattivare automaticamente il dispositivo quando il sensore rileva la presenza di qualcuno nella stanza.                                                                                                                          |
|              <strong>Richiedi PIN per proiezione wireless</strong>               |                                                                                                             Specifica se immettere un PIN prima di usare le funzionalità di proiezione wireless del dispositivo.                                                                                                             |
|          <strong>Configura la finestra di manutenzione per il dispositivo</strong>           |                                                                                          Configura la finestra durante la quale cui è possibile eseguire gli aggiornamenti del dispositivo. È possibile configurare l'ora di inizio della finestra e la durata (tra 1 e 5 ore).                                                                                           |
|               <strong>Abilita Azure Operational Insights</strong>                |                  Azure Operational Insights, parte di Microsoft Operations Management Suite, raccoglie, archivia e analizza i dati dei file di log dai dispositivi Windows 10 Team.<br /><br />Per connettersi ad Azure Operational Insights, è necessario specificare un valore per <strong>ID area di lavoro</strong> e <strong>Chiave dell'area di lavoro</strong>.                   |
|              <strong>Abilita proiezione wireless Miracast</strong>               |                                          Abilitare questa opzione se si vuole consentire al dispositivo Windows 10 Team di usare i dispositivi abilitati per Miracast per la proiezione.<br /><br />Se si abilita questa opzione, selezionare in <strong>Scegli un canale Miracast</strong> il canale Miracast usato per la proiezione del contenuto.                                           |
| <strong>Scegli le informazioni sulla riunione visualizzate nella schermata iniziale</strong> | Se si abilita questa opzione, è possibile scegliere le informazioni che verranno visualizzate nel riquadro <strong>Riunioni</strong> riquadro della schermata <strong>iniziale</strong>. È possibile scegliere le opzioni seguenti:<br /><br />-   <strong>Mostra solo organizzatore e ora</strong><br />-   <strong>Mostra organizzatore, ora e oggetto (l'oggetto è nascosto per le riunioni private)</strong> |
|                <strong>URL dell'immagine di sfondo per la schermata di blocco</strong>                 |                                           Abilitare questa impostazione per visualizzare uno sfondo personalizzato nella <strong>schermata iniziale</strong> dei dispositivi Windows 10 Team dall'URL specificato.<br /><br />L'immagine deve essere nel formato PNG e l'URL deve iniziare con <strong>https://</strong>.                                            |

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

