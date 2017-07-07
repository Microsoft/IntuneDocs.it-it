---
title: Convalidare la configurazione di MAM
description: "Questo argomento descrive com'è possibile verificare e convalidare se i criteri di gestione delle applicazioni mobili (MAM) sono configurati correttamente e funzionano come previsto."
keywords: 
author: andredm7
ms.author: andredm
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ms.reviewer: joglocke
ms.custom: intune-classic
ms.openlocfilehash: 1e22be7b238cce195ee88c938b1cca009c0b21d3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="validating-your-mobile-application-management-setup"></a>Convalidare la configurazione dei criteri di gestione delle applicazioni mobili

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento fornisce informazioni sulla verifica di eventuali problemi dopo la configurazione dei criteri di gestione delle applicazioni mobili (MAM). Queste indicazioni si applicano ai criteri MAM nel portale di Azure.

### <a name="checking-for-symptoms"></a>Verifica dei sintomi
Difficilmente gli utenti segnalano problemi poiché MAM è uno strumento di protezione dei dati. Se si verificasse un problema con la configurazione di MAM l'utente avrebbe accesso senza restrizioni, come avverrebbe se MAM non fosse installato, e non si renderebbe conto della presenza di un problema. Per questo motivo che è consigliabile convalidare la configurazione di MAM provando i criteri di gestione delle applicazioni mobili con un piccolo gruppo di utenti che possono testare deliberatamente le restrizioni MAM.


### <a name="what-to-check"></a>Elementi da controllare

Se la verifica mostra che il comportamento dei criteri di gestione delle applicazioni mobili non è come previsto, è consigliabile verificare quanto segue:

- Disponibilità della licenza per MAM
- Disponibilità della licenza per Office 365
- Stato di ogni app MAM degli utenti. I possibili stati per le app sono **Archiviato** e **Non archiviato**.

#### <a name="user-mam-status"></a>Stato MAM utente
1. Nel portale di Azure scegliere **Gestione di applicazioni mobili di Intune** > **Impostazioni** > **Gestione app** > **Tutte le impostazioni** > **Segnalazione app per utente** > **Utenti**.

2. Scegliere un utente dall'elenco oppure cercare e selezionare un utente, quindi scegliere **Seleziona utente**. Nella parte superiore della colonna **Segnalazione app** verrà visualizzato se l'utente ha la licenza per MAM. Di seguito, verrà visualizzato se l'utente ha la licenza per Office 365 e lo stato dell'app per tutti i dispositivi dell'utente.

![Stato dell'app per MAM](..\media\ts-mam-user-apps.png)

### <a name="what-to-do"></a>Operazioni da eseguire
Di seguito sono descritte le azioni da eseguire in base allo stato dell'utente:

- Se l'utente non ha la licenza per MAM, assegnare una licenza Intune all'utente come descritto in [Gestire le licenze di Intune](/intune/setup-steps).
- Se l'utente non ha la licenza per Office 365, ottenerne una per l'utente.
- Se un'app dell'utente è elencata come **Non archiviato**, controllare se i criteri MAM per tale app sono stati configurati correttamente.
- Assicurarsi che queste condizioni vengano applicate a tutti gli utenti a cui si vuole applicare i criteri di gestione delle applicazioni mobili.

### <a name="see-also"></a>Vedere anche
[Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili con Microsoft Intune](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Proteggere i dati delle app usando i criteri di gestione delle app mobili con Microsoft Intune](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
