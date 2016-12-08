---
title: Distribuire le app | Microsoft Intune
description: "Questo argomento illustra i concetti che è necessario comprendere prima di iniziare a distribuire le app con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: eedf7db0a974f9a0aa0a21b27b64ed8b4a91b378


---

# Distribuire le app con Microsoft Intune

Questo argomento illustra alcuni dei concetti che è necessario comprendere prima di iniziare a distribuire le app con Microsoft Intune.


## Azioni di distribuzione dell'app
Quando si distribuiscono le app, è possibile scegliere una delle seguenti azioni di distribuzione:

-   **Installazione richiesta**: l'app viene installata nel dispositivo senza alcun intervento da parte dell'utente.

    > [!TIP]
    > Per i dispositivi iOS non in modalità di supervisione e per tutti i dispositivi Android, l'utente deve accettare l'offerta per l'app prima di installarla.
    >
    >  Se un utente disinstalla un'app distribuita come richiesta, Intune reinstalla automaticamente l'app dopo il ciclo di inventario successivo. In genere l'inventario viene eseguito ogni sette giorni.

-   **Installazione disponibile**: l'app viene visualizzata nel portale aziendale e gli utenti possono installarla su richiesta.

-   **Disinstalla** : l'app viene disinstallata dal dispositivo.

-   **Non applicabile**: l'app non viene visualizzata nel portale aziendale e non viene installata in alcun dispositivo.

#### Comprendere quali sono le azioni di distribuzione disponibili per ogni tipo di programma di installazione

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

## Conflitti di distribuzione
Quando un dispositivo riceve due distribuzioni con la stessa azione di distribuzione, si applicano le regole seguenti:

-   Le distribuzioni eseguite in un gruppo di dispositivi hanno la precedenza rispetto a quelle eseguite in un gruppo di utenti. Tuttavia, se un'app viene distribuita a un gruppo di utenti con un'azione di tipo **Disponibile** e la stessa app viene distribuita in un gruppo di dispositivi con un'azione di tipo **Non applicabile**, l'app risulterà installabile dagli utenti nel portale aziendale.

-   Un'azione di installazione ha la precedenza rispetto a un'azione di disinstallazione.

-   Se un dispositivo riceve sia un'installazione richiesta sia un'installazione disponibile, le azioni vengono combinate. In altre parole, l'utente può installare l'app disponibile dal portale aziendale prima che inizi l'installazione richiesta.


## Passaggi successivi

Informazioni su come [distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Oct16_HO4-->


