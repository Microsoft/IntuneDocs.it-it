---
title: Come assegnare app ai gruppi
titleSuffix: Intune on Azure
description: "Dopo aver aggiunto un'app a Intune, è opportuno assegnarla ai gruppi di utenti o dispositivi.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0bb3ca2f63ee963dae61ee6622d41fe4aef7adfd
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Come assegnare app ai gruppi con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Dopo aver aggiunto un'app a Intune, è possibile assegnarla a utenti e dispositivi.

Le app possono essere assegnate ai dispositivi gestiti o non gestiti da Intune. Usare la tabella seguente per comprendere le varie opzioni per l'assegnazione di applicazioni a utenti e dispositivi:

||||
|-|-|-|-|
|&nbsp;|Dispositivi registrati con Intune|Dispositivi non registrati con Intune|
|Assegnazione a utenti|sì|sì|
|Assegnazione a dispositivi|sì|No|
|Assegnazione di app sottoposte a wrapping o app che includa l'SDK Intune (per i criteri di protezione delle app)|sì|sì|
|Assegnazione di app come Disponibili|sì|sì|
|Assegnazione di app come Obbligatorio|sì|No|
|Disinstallazione di app|sì|No|
|Installazione di app disponibili sull'app Portale aziendale da parte degli utenti finali|sì|No|
|Installazione di app disponibili sul portale aziendale basato su Web da parte degli utenti finali|sì|sì|

> [!NOTE]
> Attualmente, è possibile assegnare app iOS e Android (sia linea di business che acquistate nello store) a dispositivi non registrati con Intune.

## <a name="how-to-assign-an-app"></a>Come assegnare un'applicazione

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
1. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
2. Nel pannello dell'elenco delle app fare clic sull'app da assegnare.
3. Nel pannello <*nome app*> - **Panoramica** scegliere **Gestisci** > **Assegnazioni**.
4. Scegliere **Seleziona gruppi** e quindi nel pannello **Selezionare i gruppi** scegliere i gruppi Azure AD a cui assegnare l'app.
5. Per ogni app scelta, scegliere un **Tipo di assegnazione** per l'applicazione tra:
    - **Disponibile**: gli utenti installano l'app dall'app Portale aziendale o dal relativo sito Web.
    - **Non applicabile**: l'app non è installata o visualizzata nel portale aziendale.
    - **Obbligatoria**: l'applicazione è installata sui dispositivi nei gruppi selezionati.
    - **Disinstalla**: l'applicazione è disinstallata sui dispositivi nei gruppi selezionati.
    - **Available with or without enrollment** (Disponibile con o senza registrazione): assegnare questa app a gruppi di utenti i cui dispositivi non sono registrati con Intune.
6. **Solo per App iOS**: se è stato creato un profilo VPN iOS contenente le impostazioni VPN per app, è possibile selezionarlo in **VPN**. Quando si esegue l'app, viene aperta la connessione VPN. Per altre informazioni, vedere [Impostazioni VPN per dispositivi iOS](vpn-settings-ios.md).
6. Al termine, scegliere **Salva**.

L'app è ora assegnata ai gruppi selezionati.

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Modalità di risoluzione dei conflitti tra finalità di app

In alcuni casi, la stessa app viene assegnata a più gruppi, ma con finalità diverse. In questi casi, usare questa tabella per comprendere la finalità risultante.

||||
|-|-|-|
|Finalità gruppo 1|Finalità gruppo 2|Finalità risultante|
|Obbligatoria per l'utente|Disponibile per l'utente|Richiesto e disponibile|
|Obbligatoria per l'utente|Non disponibile per l'utente|Richiesto|
|Obbligatoria per l'utente|Disinstallazione utente|Richiesto|
|Disponibile per l'utente|Non disponibile per l'utente|Non disponibile|
|Disponibile per l'utente|Disinstallazione utente|Uninstall|
|Non disponibile per l'utente|Disinstallazione utente|Uninstall
|Obbligatoria per l'utente|Obbligatoria per il dispositivo|Entrambe presenti. Il gateway la considera obbligatoria 
|Obbligatoria per l'utente|Disinstallazione dal dispositivo|Entrambe presenti. Risoluzione gateway: obbligatoria 
|Disponibile per l'utente|Obbligatoria per il dispositivo|Entrambe presenti. Risoluzione gateway: obbligatoria (obbligatoria e disponibile)
|Disponibile per l'utente|Disinstallazione dal dispositivo|Entrambe presenti. Risoluzione gateway: disponibile.<br>L'app viene visualizzata nel portale aziendale.<br>Se l'app è già installata perché la sua finalità precedente era "app obbligatoria", viene disinstallata.<br>Ma se l'utente fa clic su Installa dal portale aziendale, l'app viene installata e la finalità di disinstallazione non viene rispettata.|
|Non disponibile per l'utente|Obbligatoria per il dispositivo|Richiesto|
|Non disponibile per l'utente|Disinstallazione dal dispositivo|Uninstall|
|Disinstallazione utente|Obbligatoria per il dispositivo|Entrambe presenti. Risoluzione gateway: obbligatoria|
|Disinstallazione utente|Disinstallazione dal dispositivo|Entrambe presenti. Risoluzione gateway: disinstallazione|
|Obbligatoria per il dispositivo|Disinstallazione dal dispositivo|Richiesto|
|Obbligatoria e disponibile per l'utente|Disponibile per l'utente|Richiesto e disponibile|
|Obbligatoria e disponibile per l'utente|Disinstallazione utente|Richiesto e disponibile|
|Obbligatoria e disponibile per l'utente|Non disponibile per l'utente|Richiesto e disponibile|
|Obbligatoria e disponibile per l'utente|Obbligatoria per il dispositivo|Entrambe presenti, obbligatoria e disponibile
|Obbligatoria e disponibile per l'utente|Non disponibile per il dispositivo|Richiesto e disponibile|
|Obbligatoria e disponibile per l'utente|Disinstallazione dal dispositivo|Entrambe presenti. Risoluzione gateway: obbligatoria. Obbligatoria + disponibile
|Non disponibile per l'utente|Non disponibile per il dispositivo|Non disponibile|
|Disponibile per l'utente|Non disponibile per il dispositivo|Disponibile|
|Obbligatoria per l'utente|Non disponibile per il dispositivo|Richiesto|
|Disponibile per l'utente senza registrazione|Obbligatoria e disponibile per l'utente|Richiesto e disponibile
|Disponibile per l'utente senza registrazione|Obbligatoria per l'utente|Richiesto
|Disponibile per l'utente senza registrazione|Non disponibile per l'utente|Non disponibile
|Disponibile per l'utente senza registrazione|Disponibile per l'utente|Disponibile|
|Disponibile per l'utente senza registrazione|Obbligatoria per il dispositivo|Obbligatoria e disponibile senza registrazione|
|Disponibile per l'utente senza registrazione|Non disponibile per il dispositivo|Disponibile senza registrazione|
|Disponibile per l'utente senza registrazione|Disinstallazione dal dispositivo|Disinstallazione e disponibile senza registrazione.<br>Se l'utente non ha installato l'app dal portale aziendale, la finalità di disinstallazione viene rispettata.<br>Se l'utente installa l'app dal portale aziendale, l'installazione ha priorità più alta rispetto alla disinstallazione.|

>[!NOTE]
>Solo per le app dello Store iOS gestite: quando si aggiungono queste app in Intune assegnandole come obbligatorie, vengono create automaticamente con entrambe le finalità Obbligatoria e Disponibile.

## <a name="next-steps"></a>Passaggi successivi

Vedere [How to monitor apps](apps-monitor.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni di app.
