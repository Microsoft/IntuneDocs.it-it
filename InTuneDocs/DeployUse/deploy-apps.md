---
title: Distribuire le app | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: e6b995118e66fd146a68b49ce4decdcbd1fe3572
ms.openlocfilehash: a68cb85602bd585539147c7d7d38c0d906f2b1f7


---

# Distribuire le app con Microsoft Intune

Questo argomento illustra alcuni dei concetti che è necessario comprendere prima di iniziare a distribuire le app con Microsoft Intune.


## Azioni di distribuzione dell'app
Quando si distribuiscono le app, è possibile scegliere una delle seguenti azioni di distribuzione:

-   **Installazione richiesta**: l'app viene installata nel dispositivo senza alcun intervento da parte dell'utente finale.

    > [!TIP]
    > [!TIP] Per i dispositivi iOS non in modalità di supervisione e per tutti i dispositivi Android l'utente deve accettare l'offerta per l'app prima di installare l'app.
    > 
    >  Se un utente finale disinstalla un'app distribuita come obbligatoria, Intune reinstallerà automaticamente l'app dopo il ciclo di inventario successivo. In genere l'inventario viene eseguito ogni 7 giorni.

-   **Installazione disponibile**: l'app viene visualizzata nel Portale aziendale e gli utenti finali possono eseguirne l'installazione su richiesta.

-   **Disinstalla** : l'app viene disinstallata dal dispositivo.

-   **Non applicabile** : l'app non viene visualizzata nel Portale aziendale e non viene installata in nessun dispositivo.

#### Comprendere quali sono le azioni di distribuzione disponibili per ogni tipo di programma di installazione

|Tipo di programma di installazione|Installazione richiesta|Installazione disponibile|Disinstalla|Non applicabile|
|------------------|--------------------|---------------------|-------------|------------------|
|Pacchetto app Windows (distribuito in un gruppo di utenti)|Sì|Sì|Sì|sì|
|Pacchetto app Windows (distribuito in un gruppo di dispositivi)|sì|No|Sì|Sì|
|Pacchetto app per dispositivi mobili (distribuito in un gruppo di utenti)|Sì|Sì|Sì|Sì|
|Pacchetto app per dispositivi mobili (distribuito in un gruppo di dispositivi)|Sì|No|Sì|Sì|
|Windows Installer (distribuito in un gruppo di utenti)|No|Sì|No|Sì|
|Windows Installer (distribuito in un gruppo di dispositivi)|Sì|No|Sì|Sì|
|Collegamento esterno (distribuito in un gruppo di utenti)|No|Sì|No|Sì|
|Collegamento esterno (distribuito in un gruppo di dispositivi)|No|No|No|No|
|App iOS gestita dall'App Store (distribuita in un gruppo di utenti)|Sì|Sì|Sì|Sì|
|App iOS gestita dall'App Store (distribuita in un gruppo di dispositivi)|Sì|No|Sì|sì|
> [!TIP]
> [!TIP] Quando si distribuiscono le app, se si selezionano gruppi sia di utenti che di dispositivi, è possibile distribuire l'app soltanto come **Installazione disponibile**.

## Conflitti di distribuzione
Quando un dispositivo riceve due distribuzioni con la stessa azione di distribuzione, si applicano le regole seguenti:

-   Le distribuzioni eseguite in un gruppo di dispositivi hanno la precedenza rispetto a quelle eseguite in un gruppo di utenti. Tuttavia, se un'applicazione viene distribuita in un gruppo di utenti con un'azione di distribuzione di **disponibile** e la stessa applicazione viene distribuita in un gruppo di dispositivi con un'azione di distribuzione di **non applicabile**, l'applicazione verrà reso disponibile nel portale aziendale agli utenti di installare.

-   Un'azione di installazione ha la precedenza rispetto a un'azione di disinstallazione.

-   Se un dispositivo riceve sia un'installazione obbligatoria che una disponibile, le azioni vengono combinate e l'app è sia obbligatoria che disponibile. In altre parole, l'utente finale può installarla dal portale aziendale prima che inizi l'installazione obbligatoria.


## Passaggi successivi

Informazioni su come [distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Jul16_HO2-->


