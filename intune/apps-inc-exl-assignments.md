---
title: Includere ed escludere assegnazioni di app
titlesuffix: Microsoft Intune
description: "Informazioni su come è possibile usare Intune per includere ed escludere le assegnazioni di app."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ca1f45c3203645dc474fcb6411a8ad598ff83714
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Includere ed escludere assegnazioni di app in Microsoft Intune

Con Intune è possibile determinare chi ha accesso a un'app assegnando i gruppi da includere ed escludere. È possibile includere ed escludere le assegnazioni di app a un gruppo di utenti o dispositivi usando una combinazione di assegnazioni di gruppi di inclusione ed esclusione. Dopo aver selezionato un'app, è possibile scegliere come assegnare l'app. Questa funzionalità può essere utile quando si rende disponibile l'app includendo un gruppo numeroso e quindi si limitano gli utenti selezionati escludendo anche un gruppo più piccolo. Il gruppo più piccolo potrebbe essere un gruppo di test o un gruppo amministrativo. 

Quando si escludono i gruppi da un'assegnazione, è necessario escludere solo gruppi di utenti o gruppi di dispositivi, non usare una combinazione di gruppi. Intune non considera l'associazione di utente a un dispositivo quando esclude i gruppi. L'inclusione di gruppi di utenti mentre si escludono i gruppi di dispositivi molto probabilmente non dà i risultati necessari perché l'inclusione ha la precedenza sull'esclusione. Ad esempio, se si seleziona un'app iOS per **Tutti gli utenti** e si escludono **Tutti gli iPad**, il risultato finale sarà che tutti gli utenti che usano un iPad riceveranno comunque l'app. Se, tuttavia, si seleziona l'app iOS per **Tutti i dispositivi** e si escludono **Tutti gli iPad**, la distribuzione sarà corretta.  

>[!NOTE]
>Durante l'impostazione di un'assegnazione di gruppo per un'app, il tipo **Non applicabile** è stato deprecato e sostituito con la funzionalità di esclusione di gruppi. 
>
>Intune fornisce per praticità i gruppi **Tutti gli utenti** e **Tutti i dispositivi** creati in precedenza nella console con le ottimizzazioni predefinite. È consigliabile usare questi gruppi per scegliere tutti gli utenti e tutti i dispositivi invece dei gruppi 'Tutti gli utenti' o 'Tutti i dispositivi' che potrebbero essere stati creati manualmente.  

## <a name="including-and-excluding-groups-when-assigning-apps"></a>Inclusione ed esclusione di gruppi durante l'assegnazione di app 
Per assegnare un'app ai gruppi usando l'assegnazione di inclusione ed esclusione:
1. Selezionare **App per dispositivi mobili** nel pannello di Microsoft Intune.
2. Selezionare **App** nel pannello **App per dispositivi mobili**. Viene visualizzato l'elenco di app aggiunte.
3. Selezionare l'app che si vuole assegnare. Viene visualizzato un dashboard correlato all'app. 
4. Selezionare **Assegnazioni** nella sezione **Gestisci**. 

    ![Assegnazioni di app in Intune](./media/apps-inc-exl-01.png)
5. Selezionare **Aggiungi gruppo** per aggiungere i gruppi di utenti assegnati all'app. 
6. Selezionare un **Tipo di assegnazione** tra i tipi di assegnazione disponibili nel pannello **Aggiungi gruppo**.
7. Selezionare **Disponibile con o senza registrazione** come tipo di assegnazione.

    ![Assegnazioni di app di Intune - Aggiungi gruppo](./media/apps-inc-exl-02.png)
8. Selezionare **Gruppi inclusi** per selezionare il gruppo di utenti per cui si vuole rendere questa app disponibile.

    >[!NOTE]
    >Quando si aggiunge un gruppo, se non sono stati ancora inclusi altri gruppi per un tipo di assegnazione specifico, tale gruppo risulterà preselezionato e non potrà essere modificato per gli altri tipi di assegnazione di inclusione. Di conseguenza, tale gruppo non potrà essere usato come gruppo incluso.

9. Selezionare **Sì** per rendere questa app disponibile a tutti gli utenti.

    ![Assegnazioni di app di Intune - Includere gruppi](./media/apps-inc-exl-03.png)
10. Fare clic su **OK** per impostare il gruppo da includere.
11. Selezionare **Gruppi esclusi** per selezionare il gruppo di utenti per cui si vuole rendere questa app non disponibile. 
12. Selezionare i gruppi da escludere, per i quali questa app non sarà disponibile.

    ![Assegnazioni di app di Intune - Escludere gruppi](./media/apps-inc-exl-04.png)
13. Fare clic su **Seleziona** per completare la selezione dei gruppi.
14. Fare clic su **OK** nel pannello **Aggiungi gruppo**. Verrà visualizzato l'elenco **Assegnazioni** dell'app.
15. Fare clic su **Salva** per attivare le assegnazioni di gruppi per l'app.

Quando si effettuano le assegnazioni di gruppi, i gruppi che sono già stati assegnati o selezionati vengono disabilitati. Se si vuole selezionare un gruppo che è attualmente disabilitato, rimuoverlo dall'elenco assegnato dell'app. È possibile modificare le assegnazioni nell'elenco **Assegnazioni** dell'app selezionando la riga che contiene l'assegnazione specifica da modificare. Inoltre, è possibile rimuovere un'assegnazione facendo clic sui puntini di sospensione (...) alla fine di una riga e selezionando **Rimuovi**. È possibile anche modificare la visualizzazione dell'elenco **Assegnazioni** scegliendo di raggruppare per **Tipo di assegnazione** o per **Inclusi/Esclusi**.

![Assegnazioni di app in Intune - Procedura completata](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>Passaggi successivi

* Per altre informazioni sull'inclusione ed esclusione di assegnazioni di gruppi per le app, vedere il [Blog di Microsoft Intune](https://aka.ms/new_app_assignment_process).
