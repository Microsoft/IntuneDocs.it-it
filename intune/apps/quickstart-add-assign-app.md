---
title: Guida introduttiva - Aggiungere e assegnare un'app client
titleSuffix: Microsoft Intune
description: In questa guida introduttiva si userà Microsoft Intune per aggiungere e assegnare un'app client.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40337b3c45885dacf486173814044a27b7f3f6cc
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755069"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Guida introduttiva: Aggiungere e assegnare un'app client

In questa guida introduttiva si userà Intune per aggiungere e assegnare un'app client alla forza lavoro della società. Una delle priorità di un amministratore è fare in modo che gli utenti finali abbiano accesso alle app necessarie per lavorare. 

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti

- Per completare questa guida introduttiva è necessario [creare un utente](../fundamentals/quickstart-create-user.md), [creare un gruppo](../fundamentals/quickstart-create-group.md) e [registrare un dispositivo](../quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come [amministratore globale o come amministratore del servizio Intune](../fundamentals/users-add.md#types-of-administrators). Se è stata creata una sottoscrizione della versione di valutazione di Intune, l'account creato con tale sottoscrizione sarà un amministratore globale.

## <a name="add-the-client-app-to-intune"></a>Aggiungere l'app client in Intune

È possibile inserire un'app per poter gestire aspetti dell'app tramite Intune. 

Usare la procedura seguente per aggiungere un'app in Intune:
1. In [Intune](https://aka.ms/intuneportal) selezionare **App** > **Tutte le app** > **Aggiungi**. 
2. Selezionare **Windows 10** nella sezione **Famiglia di prodotti Office 365** del riquadro **Seleziona il tipo di app**.
3. Fare clic su **Seleziona**. Verrà visualizzata la procedura **Aggiungi app**.
4. Confermare i dettagli predefiniti nella pagina **Informazioni sulla famiglia di prodotti dell'app**.
5. Fare clic su **Avanti** per visualizzare la pagina **Configura la famiglia di prodotti dell'app**.
6. Accanto a **Canale di aggiornamento** selezionare **Ogni mese** dalla casella a discesa.
7. Confermare i dettagli predefiniti rimanenti nella pagina ***Configura la famiglia di prodotti dell'app**.
8. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.
9. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per l'app. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti](~/fundamentals/scope-tags.md).
10. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.
11. Selezionare le assegnazioni a gruppi per l'app. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md). 
12. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. Verificare i valori e le impostazioni immesse per l'app.
13. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

## <a name="assign-the-app-to-a-group"></a>Assegnare l'app a un gruppo

Dopo aver aggiunto un'app in Microsoft Intune, è possibile assegnarla a gruppi di utenti o dispositivi.

> [!NOTE]
> Questo argomento di avvio rapido è basato sui precedenti della stessa serie. Per informazioni dettagliate, vedere i [prerequisiti](quickstart-add-assign-app.md#prerequisites) in questa guida introduttiva.

Usare la procedura seguente per assegnare un'app a un gruppo:
1. In [Intune](https://aka.ms/intuneportal) selezionare **App** > **Tutte le app**. 
2. Selezionare l'app che si vuole assegnare a un gruppo.
3. Fare clic su **Assegnazioni** > **Aggiungi gruppo** per visualizzare il riquadro **Aggiungi gruppo**.
4. Selezionare **Disponibile per i dispositivi registrati** nella casella a discesa **Tipo di assegnazione**. 
5. Fare clic su **Gruppi inclusi** > **Selezionare i gruppi da includere** > **Contoso Testers** (Tester Contoso).
6. Fare clic su **Seleziona** > **OK** > **OK** > **Salva** per assegnare il gruppo.

L'app è stata assegnata al gruppo **Contoso Testers** (Tester Contoso).

## <a name="install-the-app-on-the-enrolled-device"></a>Installare l'app nel dispositivo registrato

È necessario installare e usare l'app Portale aziendale per installare l'app **To-Do di Contoso** resa disponibile tramite Intune. Usare la procedura seguente per verificare che l'app sia disponibile per l'utente del dispositivo registrato.

1. Accedere al dispositivo Windows 10 Desktop registrato.

    > [!IMPORTANT]
    > È necessario che il dispositivo sia [registrato in Intune](../quickstart-enroll-windows-device.md). Inoltre, è necessario accedere al dispositivo usando un account contenuto nel gruppo assegnato all'app.

2. Dal menu **Start** aprire **Microsoft Store**. Quindi, trovare l'app **Portale aziendale** e installarla.
3. Avviare l'app **Portale aziendale**.
4. Fare clic sull'app aggiunta usando Intune. In questa guida introduttiva è stata aggiunta l'app **Suite di app Microsoft Office 365**.

    > [!NOTE]
    > Se non sono state assegnate app all'utente di Intune, viene visualizzato il messaggio seguente: *L'amministratore IT non ha reso disponibile alcuna app.*

5. Fare clic su **Installa**.

Se per le specifiche esigenze aziendali è richiesta l'assegnazione dell'app Portale aziendale alla forza lavoro, è possibile assegnare manualmente l'app Portale aziendale di Windows 10 direttamente da Intune. Per altre informazioni, vedere [Aggiungere manualmente l'app Portale aziendale di Windows 10 usando Microsoft Intune](../company-portal-app.md).

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva le app sono state aggiunte in Intune, assegnate a un gruppo e installate nel dispositivo Windows 10 Desktop registrato. Per altre informazioni sulla gestione delle app in Intune, vedere [Informazioni sulla gestione delle app in Microsoft Intune](app-management.md).

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: Creare e assegnare un criterio di protezione delle app](quickstart-create-assign-app-policy.md)
