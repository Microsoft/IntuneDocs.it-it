---
title: Come assegnare app ai gruppi | Microsoft Docs
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: dopo aver aggiunto un&quot;app a Intune, è opportuno assegnarla ai gruppi di utenti o dispositivi."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 1246ef539c044b894b4e4a93f449e60e6462600a
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Come assegnare app ai gruppi con Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Dopo aver aggiunto un'app a Intune, è necessario distribuirla a utenti e dispositivi, assegnandola a essi.

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

## <a name="changes-to-how-you-assign-apps-to-groups-in-the-intune-preview"></a>Modifiche della modalità di assegnazione delle app ai gruppi nell'anteprima di Intune

Nell'anteprima di Intune di Azure per assegnare le app non vengono più usati i gruppi di Intune ma i gruppi di sicurezza di Azure Active Directory (Azure AD). Per questa ragione è necessario conoscere le modifiche apportate alla modalità di assegnazione delle app, in particolare in presenza di app assegnate a gruppi figlio di Intune.
L'aspetto più importante da notare è l'assenza del concetto di gruppi figlio in Azure AD. È possibile tuttavia che alcuni gruppi contengano gli stessi membri. In questo caso, il comportamento di Intune classico è diverso da quello dell'anteprima di Intune di Azure. La tabella seguente descrive le differenze:

||||||
|-|-|-|-|-|
|**Intune classico (prima della migrazione del tenant)**|-|**Intune di Azure (dopo il completamento della migrazione del tenant)**|-|**Altre informazioni**|
|**Intento dell'assegnazione del gruppo padre**|**Intento dell'assegnazione del gruppo figlio**|**Intento dell'assegnazione risultante per i membri comuni del gruppo padre e figlio precedente**|**Intento dell'assegnazione risultante per i membri del gruppo padre**|-|
|Disponibile|Richiesto|Richiesto e disponibile|Disponibile|Richiesto e disponibile indica che le app assegnate come richieste possono essere visualizzate anche nell'app Portale aziendale.
|Non applicabile|Disponibile|Non applicabile|Non applicabile|Soluzione alternativa: rimuovere l'intento dell'assegnazione 'Non applicabile' dal gruppo padre di Intune.
|Richiesto|Disponibile|Richiesto e disponibile|Richiesto|-|
|Richiesto e disponibile<sup>1</sup>|Disponibile|Richiesto e disponibile|Richiesto e disponibile|-|
|Richiesto|Non applicabile|Richiesto|Richiesto|-|
|Richiesto e disponibile|Non applicabile|Richiesto e disponibile|Richiesto e disponibile|-|
|Richiesto|Uninstall|Richiesto|Richiesto|-|
|Richiesto e disponibile|Uninstall|Richiesto e disponibile|Richiesto e disponibile|-|
<sup>1</sup> Solo per le app dello Store iOS gestite, quando si aggiungono le app in Intune e si assegnano le app con l'intento Richiesto, le app vengono create automaticamente con entrambi gli intenti Richiesto e Disponibile.

Per evitare conflitti di assegnazione, è possibile eseguire le azioni seguenti:

1.    Se in precedenza sono state assegnate app a gruppi padre e figlio di Intune correlati, è consigliabile rimuovere queste assegnazioni prima che inizi la migrazione del tenant.
2.    Rimuovere i gruppi figlio dai gruppi padre e creare un nuovo gruppo contenente i membri del gruppo figlio precedente. Sarà quindi possibile creare una nuova assegnazione di app al gruppo.
Note: se il gruppo padre precedente era "Tutti gli utenti", sarà necessario creare un nuovo gruppo dinamico che non includa i membri del gruppo figlio.
È necessario apportare le modifiche ai gruppi nel [portale di Azure](https://portal.azure.com/) per gruppi di utenti e dispositivi. Il [portale di Azure classico](https://manage.windowsazure.com/) consentirà di apportare modifiche soltanto ai gruppi di utenti.


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
    - **Available with or without enrollment** (Disponibile con o senza registrazione): assegnare questa app a gruppi di utenti i cui dispositivi non sono registrati con Intune. Per un aiuto, vedere la tabella in alto.
6. Al termine, scegliere **Salva**.

L'app è ora assegnata al gruppo scelto.

Vedere [How to monitor apps](apps-monitor.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni di app.

