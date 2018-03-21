---
title: Come assegnare app ai gruppi con Microsoft Intune
titlesuffix: 
description: "Dopo aver aggiunto un'app a Microsoft Intune, è opportuno assegnarla ai gruppi di utenti o dispositivi."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eba329be463fbf0593638bd4cf41c404a17f9cc0
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Come assegnare app ai gruppi con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Dopo aver aggiunto un'app a Microsoft Intune, è possibile assegnarla a utenti e dispositivi.

Le app possono essere assegnate ai dispositivi gestiti o non gestiti da Intune. Usare la tabella seguente per comprendere le varie opzioni per l'assegnazione di applicazioni a utenti e dispositivi:

||||
|-|-|-|-|
|&nbsp;|Dispositivi registrati con Intune|Dispositivi non registrati con Intune|
|Assegnazione a utenti|Sì|Sì|
|Assegnazione a dispositivi|Sì|No|
|Assegnazione di app sottoposte a wrapping o app che includano l'SDK Intune (per i criteri di protezione delle app)|Sì|Sì|
|Assegnazione di app come Disponibili|Sì|Sì|
|Assegnazione di app come Obbligatorio|Sì|No|
|Disinstallazione di app|Sì|No|
|Ricezione degli aggiornamenti delle app da Intune|Sì|No|
|Installazione di app disponibili sull'app Portale aziendale da parte degli utenti finali|Sì|No|
|Installazione di app disponibili sul portale aziendale basato su Web da parte degli utenti finali|Sì|Sì|

> [!NOTE]
> Attualmente, è possibile assegnare app iOS e Android (sia linea di business che acquistate nello store) a dispositivi non registrati con Intune.<br></br><br></br>
> Per ricevere gli aggiornamenti delle app nei dispositivi che non sono registrati con Intune, gli utenti devono accedere al portale aziendale e installare manualmente gli aggiornamenti delle app.

## <a name="how-to-assign-an-app"></a>Come assegnare un'applicazione

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
1. Nel carico di lavoro **App per dispositivi mobili** scegliere **App** nella sezione **Gestisci**.
2. Nel pannello dell'elenco delle app fare clic sull'app da assegnare.
3. Nel pannello **Panoramica** specifico dell'app scegliere **Assegnazioni** nella sezione **Gestisci**.
4. Scegliere **Aggiungi gruppo** per visualizzare il pannello **Aggiungi gruppo** correlato all'app.
5. Per l'app specifica scegliere un **tipo di assegnazione** per l'app:
    - **Available for enrolled devices** (Disponibile per i dispositivi registrati): gli utenti installano l'app dall'app Portale aziendale o dal relativo sito Web.
    - **Available with or without enrollment** (Disponibile con o senza registrazione): assegnare questa app a gruppi di utenti i cui dispositivi non sono registrati con Intune. Si noti che il tipo **Android for Work App** (App Android for Work) non supporta questa opzione. 
    - **Obbligatoria**: l'applicazione è installata sui dispositivi nei gruppi selezionati.
    - **Disinstalla**: l'applicazione è disinstallata sui dispositivi nei gruppi selezionati.

    > [!NOTE]
    > **Solo per App iOS**: se è stato creato un profilo VPN iOS contenente le impostazioni VPN per app, è possibile selezionarlo in **VPN**. Quando l'app viene eseguita, viene aperta la connessione VPN. Per altre informazioni, vedere [Impostazioni VPN per dispositivi iOS in Microsoft Intune](vpn-settings-ios.md).

6. Selezionare **Gruppi inclusi** per scegliere i gruppi di utenti che saranno interessati da questa assegnazione di app.
7. Fare clic su **Seleziona** dopo aver selezionato uno o più gruppi da includere.
8. Fare clic su **OK** nel pannello **Assegna** per completare la selezione dei gruppi inclusi.
9. Fare clic su **Escludi gruppi** se si sceglie di escludere gruppi di utenti da questa assegnazione di app.
10. Se si è scelto di escludere alcuni gruppi fare clic su **Seleziona** nel pannello **Selezione gruppi**.
11. Fare clic su **OK** nel pannello **Aggiungi gruppo**.
12. Fare clic su **Salva** nel pannello **Assegnazioni** delle app per salvare le assegnazioni.

L'app è ora assegnata ai gruppi selezionati. Per altre informazioni sull'inclusione ed esclusione di assegnazioni di app, vedere [Includere ed escludere assegnazioni di app](apps-inc-exl-assignments.md).

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
>Solo per le app dello Store iOS gestite, quando si aggiungono queste app in Microsoft Intune assegnandole come obbligatorie**,** vengono create automaticamente con entrambe le finalità **Obbligatoria** e **Disponibile**.

## <a name="next-steps"></a>Passaggi successivi

Vedere [How to monitor apps](apps-monitor.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni di app.
