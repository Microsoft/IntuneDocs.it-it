---
title: Convalidare i criteri di protezione delle app
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: questo argomento descrive com&quot;è possibile verificare e convalidare se i criteri di protezione delle app sono configurati correttamente e funzionano come previsto."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 26e191965eff482cf97b920e028cdf60d1881d32
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-validate-your-app-protection-policy-setup"></a>Come convalidare la configurazione dei criteri di protezione delle app

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


Questo argomento fornisce informazioni sulla verifica di eventuali problemi dopo la configurazione dei criteri di protezione delle app. Queste indicazioni si applicano ai criteri di protezione delle app nell'**anteprima** del portale di Azure.

### <a name="checking-for-symptoms"></a>Verifica dei sintomi
Difficilmente gli utenti segnalano problemi poiché la protezione delle app è uno strumento di protezione dei dati. Se si verificasse un problema con la configurazione della protezione delle app l'utente avrebbe accesso senza restrizioni, come avverrebbe se la protezione delle app non fosse installata e non si renderebbe conto della presenza di un problema. Per questo motivo è consigliabile convalidare la configurazione della protezione delle app provando i criteri di protezione delle app con un piccolo gruppo di utenti che possono testare deliberatamente le restrizioni della protezione delle app.


### <a name="what-to-check"></a>Elementi da controllare

Se la verifica mostra che il comportamento dei criteri di protezione delle app non è come previsto, è consigliabile verificare quanto segue:

- Disponibilità della licenza per la protezione delle app
- Disponibilità della licenza per Office 365
- Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**.

#### <a name="user-app-protection-status"></a>Stato di protezione dell'app dell'utente
1. Nel portale di Azure scegliere **Gestisci le app** > **Monitoraggio** >  **App Protection User Status** (Stato utente per la protezione dell'app) > **Utenti**.

2. Scegliere un utente dall'elenco oppure cercare e selezionare un utente, quindi scegliere **Seleziona utente**. Nella parte superiore della colonna **Segnalazione app** verrà visualizzato se l'utente ha la licenza per la protezione delle app. Di seguito, verrà visualizzato se l'utente ha la licenza per Office 365 e lo stato dell'app per tutti i dispositivi dell'utente.



### <a name="what-to-do"></a>Operazioni da eseguire
Di seguito sono descritte le azioni da eseguire in base allo stato dell'utente:

- Se l'utente non dispone di licenza per la protezione delle app, assegnare una licenza Intune all'utente.
- Se l'utente non ha la licenza per Office 365, ottenerne una per l'utente.
- Se un'app dell'utente è elencata come **Non archiviato**, controllare se i criteri di protezione delle app per tale app sono stati configurati correttamente.
- Assicurarsi che queste condizioni vengano applicate a tutti gli utenti a cui si vuole applicare i criteri di protezione delle app.

### <a name="see-also"></a>Vedere anche

[Che cos'è un criterio di protezione delle app di Intune?](app-protection-policies.md)

