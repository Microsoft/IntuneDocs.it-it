---
title: Convalidare la configurazione dei criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Questo articolo illustra come verificare che i criteri di protezione delle app siano configurati e funzionino correttamente.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2018
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 3158d0531de4809bf654c030b8c1e0ef90185362
ms.sourcegitcommit: 8019bdd8117806c6a3a73a8c6d40af1a3def6d90
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53247068"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Come convalidare la configurazione dei criteri di protezione delle app

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verificare che i criteri di protezione delle app siano configurati e funzionino correttamente. Queste indicazioni si applicano ai criteri di protezione delle app nel portale di Azure.

### <a name="checking-for-symptoms"></a>Verifica dei sintomi
Difficilmente gli utenti segnalano problemi poiché la protezione delle app è uno strumento di protezione dei dati. Se si verificasse un problema con la configurazione della protezione delle app, l'utente avrebbe accesso senza restrizioni, come avverrebbe se la protezione delle app non fosse installata, e non si renderebbe conto della presenza di un problema. Per questo motivo è consigliabile convalidare la configurazione della protezione delle app provando i criteri di protezione delle app con un piccolo gruppo di utenti che possono testare deliberatamente le restrizioni della protezione delle app.


### <a name="what-to-check"></a>Elementi da controllare

Se dai test risulta che il comportamento dei criteri di protezione delle app è diverso dal previsto, verificare questi elementi:

- Disponibilità della licenza per la protezione delle app
- Disponibilità della licenza per Office 365
- Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**.

#### <a name="user-app-protection-status"></a>Stato di protezione dell'app dell'utente
1. Accedere al [portale Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Selezionare **App client** > **Monitor** >  **Stato protezione app**e quindi selezionare il riquadro **Utenti assegnati**. 
4. Nella pagina **Segnalazione app** selezionare **Selezionare l'utente** per visualizzare un elenco di utenti e gruppi. 
5. Cercare e selezionare un utente nell'elenco e quindi scegliere **Selezionare l'utente**. Nella parte superiore del riquadro **Segnalazione app** è possibile verificare se l'utente ha la licenza per la protezione delle app. È anche possibile visualizzare se l'utente ha una licenza per Office 365 e lo stato dell'app per tutti i dispositivi dell'utente.



### <a name="what-to-do"></a>Operazioni da eseguire
Di seguito sono descritte le azioni da eseguire in base allo stato dell'utente:

- Se l'utente non ha la licenza per la protezione delle app, assegnare una licenza di Intune all'utente.
- Se l'utente non ha una licenza per Office 365, ottenerne una per l'utente.
- Se un'app dell'utente è elencata come **Archiviazione non eseguita**, controllare se i criteri di protezione delle app per tale app sono stati configurati correttamente.
- Assicurarsi che queste condizioni vengano applicate a tutti gli utenti a cui si vogliono applicare i criteri di protezione delle app.

### <a name="see-also"></a>Vedere anche

[Che cos'è un criterio di protezione delle app di Intune?](app-protection-policies.md)
