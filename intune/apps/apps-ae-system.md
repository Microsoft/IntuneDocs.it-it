---
title: Aggiungere app di sistema Android Enterprise a Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere app di sistema Enterprise a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755256"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Aggiungere app di sistema Android Enterprise a Microsoft Intune

Prima di assegnare un'app a un dispositivo o a un gruppo di utenti, è necessario aggiungere l'app a Microsoft Intune. Le app di sistema sono supportate nei dispositivi Android Enterprise. È possibile abilitare un'app di sistema per [dispositivi completamente gestiti](../enrollment/android-kiosk-enroll.md) o [dispositivi dedicati Android Enterprise](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Aggiungere l'app

Seguire questa procedura per aggiungere un'app di sistema Android Enterprise a Intune dal portale di Azure:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Nel riquadro **Seleziona il tipo di app** selezionare **App di sistema Android Enterprise** tra i tipi disponibili in **Altro**.
4. Fare clic su **Seleziona**. Verrà visualizzata la procedura **Aggiungi app**.
Nella pagina **Informazioni sull'app** aggiungere i dettagli relativi all'app:
    - **Nome app**: Immettere il nome dell'app.
    - **Autore**: Immettere il nome dell'autore dell'app.  
    - **Nome pacchetto**: Immettere un nome di pacchetto. Intune convaliderà la validità del nome del pacchetto.
5. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.
8. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per l'app. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti](~/fundamentals/scope-tags.md).
9. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.
10. Selezionare le assegnazioni a gruppi per l'app. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md). 
11. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. Verificare i valori e le impostazioni immessi per l'app.
12. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

Verrà visualizzato il pannello **Panoramica** dell'app creata.

> [!NOTE]
> Sarà necessario collaborare con l'OEM del dispositivo per trovare il nome del pacchetto dell'app che si vuole abilitare o disabilitare.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. 

Le app di sistema Android Enterprise abilitano o disabilitano le app che fanno già parte della piattaforma. Per abilitare un'app, assegnare l'app di sistema come **obbligatoria**. Per disabilitare un'app, assegnare l'app di sistema come **disinstallazione**. Non è possibile assegnare le app di sistema come disponibili per un utente.


## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md)
