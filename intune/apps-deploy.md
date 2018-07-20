---
title: Assegnare app ai gruppi con Microsoft Intune
titlesuffix: ''
description: Informazioni su come assegnare un'app di Intune ai gruppi di utenti o dispositivi.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1e6ffd31e35637cf722fc2af486be4bd9101c1db
ms.sourcegitcommit: 413d271b42a6d4396adc2f749e31eed782aaa9da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38993752"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Assegnare app ai gruppi con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dopo avere [aggiunto un'app](apps-add.md) a Microsoft Intune, è possibile assegnarla a utenti e dispositivi. Si noti che è possibile assegnare un'app a un dispositivo indipendentemente dal fatto che il dispositivo sia gestito da Intune o meno. 

La tabella seguente elenca le varie opzioni per l'assegnazione di applicazioni a utenti e dispositivi:

||||
|-|-|-|-|
|&nbsp;|**Dispositivi registrati con Intune**|**Dispositivi non registrati con Intune**|
|Assegnazione a utenti|Sì|Sì|
|Assegnazione a dispositivi|Sì|No|
|Assegnazione di app sottoposte a wrapping o di app che includono Intune SDK (per i criteri di protezione delle app)|Sì|Sì|
|Assegnazione di app come Disponibili|Sì|Sì|
|Assegnazione di app come Obbligatorio|Sì|No|
|Disinstallazione di app|Sì|No|
|Ricezione degli aggiornamenti delle app da Intune|Sì|No|
|Installazione di app disponibili sull'app Portale aziendale da parte degli utenti finali|Sì|No|
|Installazione di app disponibili sul portale aziendale basato sul Web da parte degli utenti finali|Sì|Sì|

> [!NOTE]
> Attualmente, è possibile assegnare app iOS e Android (app line-of-business e acquistate nello store) a dispositivi non registrati con Intune.
>
> Per ricevere gli aggiornamenti delle app nei dispositivi che non sono registrati con Intune, gli utenti devono accedere al portale aziendale dell'organizzazione e installare manualmente gli aggiornamenti delle app.

## <a name="to-assign-an-app"></a>Per assegnare un'applicazione

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Dal menu **Intune** scegliere **App per dispositivi mobili**.
4. Nella sezione **Gestisci** del menu selezionare **App**.
5. Nel riquadro **App** selezionare l'app che si vuole assegnare.
6. Nella sezione **Gestisci** del menu selezionare **Assegnazioni**.
7. Selezionare **Aggiungi gruppo** per aprire il riquadro **Aggiungi gruppo** relativo all'app.
8. Per l'app specifica, selezionare un **tipo di assegnazione**:
   - **Disponibile per i dispositivi registrati**: gli utenti installano l'app dall'app Portale aziendale o dal relativo sito Web.
   - **Disponibile con o senza registrazione**: assegnare questa app a gruppi di utenti i cui dispositivi non sono registrati con Intune. Le app della versione gestita di Google Play non supportano questa opzione. 
   - **Obbligatoria**: l'applicazione è installata nei dispositivi nei gruppi selezionati.
   - **Disinstalla**: l'applicazione è disinstallata dai dispositivi nei gruppi selezionati.

     > [!NOTE]
     > **Solo per App iOS**: se è stato creato un profilo VPN iOS contenente le impostazioni VPN per app, è possibile selezionare il profilo VPN in **VPN**. Quando l'app viene eseguita, viene aperta la connessione VPN. Per altre informazioni, vedere [Impostazioni VPN per dispositivi iOS in Microsoft Intune](vpn-settings-ios.md).

9. Per selezionare i gruppi di utenti che sono interessati da questa assegnazione di app, selezionare **Gruppi inclusi**.
10. Dopo avere selezionato uno o più gruppi da includere, selezionare **Seleziona**.
11. Nel riquadro **Assegna** fare clic su **OK** per completare la selezione dei gruppi inclusi.
12. Per escludere gruppi di utenti da questa assegnazione di app, selezionare **Escludi gruppi**.
13. Se si è scelto di escludere alcuni gruppi in **Selezione gruppi** selezionare **Seleziona**.
14. Nel riquadro **Aggiungi gruppo** selezionare **OK**.
15. Nel riquadro **Assegnazioni** dell'app selezionare **Salva**.

L'app è ora assegnata ai gruppi selezionati. Per altre informazioni sull'inclusione ed esclusione di assegnazioni di app, vedere [Includere ed escludere assegnazioni di app](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Modalità di risoluzione dei conflitti tra finalità di app

In alcuni casi, la stessa app viene assegnata a più gruppi, ma con finalità diverse. Le informazioni nella tabella seguente consentono di conoscere la finalità risultante in casi come questo:

||||
|-|-|-|
|**Finalità gruppo 1**|**Finalità gruppo 2**|**Finalità risultante**|
|Obbligatoria per l'utente|Disponibile per l'utente|Richiesto e disponibile|
|Obbligatoria per l'utente|Non disponibile per l'utente|Richiesto|
|Obbligatoria per l'utente|Disinstallazione utente|Richiesto|
|Disponibile per l'utente|Non disponibile per l'utente|Non disponibile|
|Disponibile per l'utente|Disinstallazione utente|Uninstall|
|Non disponibile per l'utente|Disinstallazione utente|Uninstall
|Obbligatoria per l'utente|Obbligatoria per il dispositivo|Entrambe presenti. Il gateway la considera obbligatoria
|Obbligatoria per l'utente|Disinstallazione dal dispositivo|Entrambe presenti. Risoluzione gateway: obbligatoria
|Disponibile per l'utente|Obbligatoria per il dispositivo|Entrambe presenti. Risoluzione gateway: obbligatoria (obbligatoria e disponibile)
|Disponibile per l'utente|Disinstallazione dal dispositivo|Entrambe presenti. Risoluzione gateway: disponibile.<br><br>L'app viene visualizzata nel portale aziendale.<br><br>Se l'app è già installata perché la sua finalità precedente era "app obbligatoria", viene disinstallata.<br><br>Se l'utente seleziona **Installa dal portale aziendale**, l'app viene installata e la finalità di disinstallazione non viene rispettata.|
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
|Obbligatoria e disponibile per l'utente|Disinstallazione dal dispositivo|Entrambe presenti. Risoluzione gateway: obbligatoria (obbligatoria e disponibile)
|Non disponibile per l'utente|Non disponibile per il dispositivo|Non disponibile|
|Disponibile per l'utente|Non disponibile per il dispositivo|Disponibile|
|Obbligatoria per l'utente|Non disponibile per il dispositivo|Richiesto|
|Disponibile per l'utente senza registrazione|Obbligatoria e disponibile per l'utente|Richiesto e disponibile
|Disponibile per l'utente senza registrazione|Obbligatoria per l'utente|Richiesto
|Disponibile per l'utente senza registrazione|Non disponibile per l'utente|Non disponibile
|Disponibile per l'utente senza registrazione|Disponibile per l'utente|Disponibile|
|Disponibile per l'utente senza registrazione|Obbligatoria per il dispositivo|Obbligatoria e disponibile senza registrazione|
|Disponibile per l'utente senza registrazione|Non disponibile per il dispositivo|Disponibile senza registrazione|
|Disponibile per l'utente senza registrazione|Disinstallazione dal dispositivo|Disinstallazione e disponibile senza registrazione.<br><br>Se l'utente non ha installato l'app dal portale aziendale, la finalità di disinstallazione viene rispettata.<br><br>Se l'utente installa l'app dal portale aziendale, l'installazione ha priorità più alta rispetto alla disinstallazione.|

> [!NOTE]
> Solo per le app dello Store iOS gestite, quando si aggiungono queste app in Microsoft Intune assegnandole come **obbligatorie**, le app vengono create automaticamente con entrambe le finalità **Obbligatoria** e **Disponibile**.<br><br>
> Le app dello Store iOS (non le app VPP per iOS) di destinazione con scopo obbligatorio verranno applicate sul dispositivo al momento della connessione di quest'ultimo e verranno visualizzate anche nell'app Portale aziendale.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sul monitoraggio delle assegnazioni di app, vedere [Come monitorare le app](apps-monitor.md).
