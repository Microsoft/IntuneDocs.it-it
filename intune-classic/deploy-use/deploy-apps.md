---
title: Distribuire le app | Documentazione Microsoft
description: "Questo argomento illustra i concetti che è necessario comprendere prima di iniziare a distribuire le app con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: b2f0709beb6c64da1b70c20be6b3bb82bd06d5e8
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="deploy-apps-with-microsoft-intune"></a>Distribuire le app con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento illustra alcuni dei concetti che è necessario comprendere prima di iniziare a distribuire le app con Microsoft Intune.


## <a name="app-deployment-actions"></a>Azioni di distribuzione dell'app
Quando si distribuiscono le app, è possibile scegliere una delle seguenti azioni di distribuzione:

-   **Installazione richiesta**: l'app viene installata nel dispositivo senza alcun intervento da parte dell'utente.

    > [!TIP]
    > Per i dispositivi iOS non in modalità di supervisione e per tutti i dispositivi Android, l'utente deve accettare l'offerta per l'app prima di installarla.
    >
    >  Se un utente disinstalla un'app distribuita come richiesta, Intune reinstalla automaticamente l'app dopo il ciclo di inventario successivo. In genere l'inventario viene eseguito ogni sette giorni.

-   **Installazione disponibile**: l'app viene visualizzata nel portale aziendale e gli utenti possono installarla su richiesta.

-   **Disinstalla** : l'app viene disinstallata dal dispositivo.

-   **Non applicabile**: l'app non viene visualizzata nel portale aziendale e non viene installata in alcun dispositivo.

#### <a name="understand-which-deployment-actions-are-available-for-each-installer-type"></a>Comprendere quali sono le azioni di distribuzione disponibili per ogni tipo di programma di installazione

|Tipo di programma di installazione|Installazione richiesta|Installazione disponibile|Disinstalla|Non applicabile|
|------------------|--------------------|---------------------|-------------|------------------|
|Pacchetto app Windows (distribuito in un gruppo di utenti)|sì|Sì|Sì|sì|
|Pacchetto app Windows (distribuito in un gruppo di dispositivi)|sì|No|Sì|sì|
|Pacchetto app per dispositivi mobili (distribuito in un gruppo di utenti)|sì|Sì|Sì|sì|
|Pacchetto app per dispositivi mobili (distribuito in un gruppo di dispositivi)|sì|No|Sì|sì|
|Windows Installer (distribuito in un gruppo di utenti)|No|Sì|No|sì|
|Windows Installer (distribuito in un gruppo di dispositivi)|sì|No|Sì|sì|
|Collegamento esterno (distribuito in un gruppo di utenti)|No|Sì|No|sì|
|Collegamento esterno (distribuito in un gruppo di dispositivi)|No|No|No|No|
|App iOS gestita dall'App Store (distribuita in un gruppo di utenti)|sì|Sì|Sì|sì|
|App iOS gestita dall'App Store (distribuita in un gruppo di dispositivi)|sì|No|Sì|sì|
> [!TIP]
> Quando si distribuiscono le app, se si selezionano gruppi sia di utenti che di dispositivi, è possibile distribuire l'app soltanto come **Installazione disponibile**.

## <a name="deployment-conflicts"></a>Conflitti di distribuzione
Quando un dispositivo riceve due distribuzioni con la stessa azione di distribuzione, si applicano le regole seguenti:

-   Le distribuzioni eseguite in un gruppo di dispositivi hanno la precedenza rispetto a quelle eseguite in un gruppo di utenti. Tuttavia, se un'app viene distribuita a un gruppo di utenti con un'azione di tipo **Disponibile** e la stessa app viene distribuita in un gruppo di dispositivi con un'azione di tipo **Non applicabile**, l'app risulterà installabile dagli utenti nel portale aziendale.

-   Un'azione di installazione ha la precedenza rispetto a un'azione di disinstallazione.

-   Se un dispositivo riceve sia un'installazione richiesta sia un'installazione disponibile, le azioni vengono combinate. In altre parole, l'utente può installare l'app disponibile dal portale aziendale prima che inizi l'installazione richiesta.


## <a name="next-steps"></a>Passaggi successivi

Informazioni su come [distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).

