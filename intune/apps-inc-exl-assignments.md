---
title: Includere ed escludere assegnazioni di app in Microsoft Intune
titlesuffix: ''
description: Informazioni su come usare Microsoft Intune per includere ed escludere le assegnazioni di app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fee473cd6cb6fa7e8a092ebd70192f2b7f8a8b84
ms.sourcegitcommit: 279f923b1802445e501324a262d14e8bfdddabde
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2018
ms.locfileid: "53737934"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Includere ed escludere assegnazioni di app in Microsoft Intune

In Intune è possibile determinare chi ha accesso a un'app assegnando i gruppi di utenti da includere ed escludere. Prima di assegnare i gruppi all'app, è necessario impostare il tipo di assegnazione per un'app. Il tipo di assegnazione rende l'app disponibile o richiesta oppure disinstalla l'app. 

Per impostare la disponibilità di un'app, è possibile includere ed escludere le assegnazioni di app a un gruppo di utenti o dispositivi usando una combinazione di assegnazioni di gruppi di inclusione ed esclusione. Questa funzionalità può essere utile quando si rende disponibile l'app includendo un gruppo numeroso e quindi si limitano gli utenti selezionati escludendo anche un gruppo più piccolo. Il gruppo più piccolo potrebbe essere un gruppo di test o un gruppo amministrativo. 

Quando si escludono i gruppi da un'assegnazione di un'app, è necessario escludere solo gruppi di utenti o gruppi di dispositivi. Non è possibile escludere una combinazione di gruppi di utenti e gruppi di dispositivi. 

Intune non considera l'associazione tra utente e dispositivo quando esclude i gruppi. L'inclusione di gruppi di utenti mentre si escludono i gruppi di dispositivi molto probabilmente non dà i risultati necessari. L'inclusione ha la precedenza sull'esclusione. Ad esempio, se si seleziona un'app iOS per **Tutti gli utenti** e si escludono **Tutti gli iPad**, il risultato finale è che tutti gli utenti che usano un iPad ricevono comunque l'app. Se tuttavia si seleziona l'app iOS per **Tutti i dispositivi** e si escludono **Tutti gli iPad**, la distribuzione sarà corretta.  

> [!NOTE]
> Quando si imposta un'assegnazione di gruppo per un'app, il tipo **Non applicabile** è deprecato e viene sostituito con la funzionalità di esclusione di gruppi. 
>
> Intune fornisce per praticità i gruppi **Tutti gli utenti** e **Tutti i dispositivi** creati in precedenza nella console. Per praticità, i gruppi hanno ottimizzazioni predefinite. È consigliabile usare questi gruppi per scegliere tutti gli utenti e tutti i dispositivi invece dei gruppi "tutti gli utenti" o "tutti i dispositivi" che potrebbero essere stati creati manualmente.  
>
> Android Enterprise supporta l'inclusione e l'esclusione di gruppi. È possibile usare i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi** per l'assegnazione di app Android Enterprise. 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>Includere ed escludere gruppi durante l'assegnazione di app 
Per assegnare un'app ai gruppi usando l'assegnazione di inclusione ed esclusione:
1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Dal menu **Intune** scegliere **App client**.
4. Nel riquadro **App client** selezionare **App**. Viene visualizzato l'elenco di app aggiunte.
5. Selezionare l'app che si vuole assegnare. Un dashboard visualizza le informazioni sull'app. 
6. Nella sezione **Gestisci** del menu selezionare **Assegnazioni**. 

    ![Includere assegnazioni di app quando si assegnano app](./media/apps-inc-exl-01.png)
7. Selezionare **Aggiungi gruppo** per aggiungere i gruppi di utenti assegnati all'app. 
8. Nel riquadro **Aggiungi gruppo** selezionare un **tipo di assegnazione** tra quelli disponibili.
9. Come tipo di assegnazione, selezionare **Disponibile con o senza registrazione**.

    ![Assegnazioni di app di Intune - Aggiungi gruppo](./media/apps-inc-exl-02.png)
10. Selezionare **Gruppi inclusi** per selezionare il gruppo di utenti per cui si vuole rendere questa app disponibile.

    > [!NOTE]
    > Quando si aggiunge un gruppo, se sono già stati inclusi altri gruppi per un tipo di assegnazione specifico, l'app risulterà preselezionata e non potrà essere modificata per gli altri tipi di assegnazione di inclusione. Il gruppo usato non potrà essere usato come gruppo incluso.

11. Selezionare **Sì** per rendere questa app disponibile a tutti gli utenti.

    ![Assegnazioni di app di Intune - Includere gruppi](./media/apps-inc-exl-03.png)
12. Fare clic su **OK** per impostare il gruppo da includere.
13. Selezionare **Gruppi esclusi** per selezionare il gruppo di utenti per cui si vuole rendere questa app non disponibile. 
14. Selezionare i gruppi da escludere. Questa app verrà resa non disponibile per tali gruppi.

    ![Assegnazioni di app di Intune - Escludere gruppi](./media/apps-inc-exl-04.png)
15. Selezionare **Seleziona** per completare la selezione dei gruppi.
16. Nel riquadro **Aggiungi gruppo** selezionare **OK**. Verrà visualizzato l'elenco **Assegnazioni** dell'app.
17. Fare clic su **Salva** per attivare le assegnazioni di gruppi per l'app.

Quando si creano le assegnazioni di gruppi, i gruppi che sono già stati assegnati non sono disponibili per la modifica. Se si vuole selezionare un gruppo che non è attualmente disponibile, prima rimuovere l'app dall'elenco assegnato dell'app. 

Per modificare le assegnazioni, nell'elenco **Assegnazioni** dell'app selezionare la riga che contiene l'assegnazione specifica da modificare. È anche possibile rimuovere un'assegnazione selezionando i puntini di sospensione (**...**) alla fine di una riga e quindi selezionando **Rimuovi**. Per modificare la visualizzazione dell'elenco **Assegnazioni**, raggruppare per **Tipo di assegnazione** o per **Inclusi/Esclusi**.

![Assegnazioni di app in Intune - Procedura completata](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sull'inclusione e l'esclusione di assegnazioni di gruppi per le app, vedere il [blog di Microsoft Intune](https://aka.ms/new_app_assignment_process).
- Vedere come [monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).
