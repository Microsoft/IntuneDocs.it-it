---
title: Includere ed escludere assegnazioni di app in Microsoft Intune
titleSuffix: ''
description: Informazioni su come usare Microsoft Intune per includere ed escludere le assegnazioni di app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f073c8ad7a8e087a791ee756683011fac6947162
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547957"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Includere ed escludere assegnazioni di app in Microsoft Intune

In Intune è possibile determinare chi ha accesso a un'app assegnando i gruppi di utenti da includere ed escludere. Prima di assegnare i gruppi all'app, è necessario impostare il tipo di assegnazione per un'app. Il tipo di assegnazione rende l'app disponibile o richiesta oppure disinstalla l'app. 

Per impostare la disponibilità di un'app, è possibile includere ed escludere le assegnazioni di app a un gruppo di utenti o dispositivi usando una combinazione di assegnazioni di gruppi di inclusione ed esclusione. Questa funzionalità può essere utile quando si rende disponibile l'app includendo un gruppo numeroso e quindi si limitano gli utenti selezionati escludendo anche un gruppo più piccolo. Il gruppo più piccolo potrebbe essere un gruppo di test o un gruppo amministrativo. 

È consigliabile creare e assegnare app specifiche per i gruppi di utenti e altre distinte per i gruppi di dispositivi. Per altre informazioni sui gruppi, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md).  

Esistono scenari importanti quando si includono o si escludono assegnazioni di app:

- L'esclusione ha la precedenza sull'inclusione negli scenari seguenti, relativi a gruppi dello stesso tipo:
    - Inclusione ed esclusione di gruppi di utenti durante l'assegnazione di app
    - Inclusione ed esclusione di gruppi di dispositivi durante l'assegnazione di app

    Se ad esempio si assegna un gruppo di dispositivi al gruppo di utenti **Tutti gli utenti aziendali**, ma si escludono i membri del gruppo di utenti **Dirigenti**, **Tutti gli utenti aziendali**, ad eccezione dei **Dirigenti**, riceveranno l'assegnazione, perché entrambi i gruppi sono gruppi di utenti.
- Intune non valuta le relazioni di gruppi di utenti e dispositivi. Se si assegnano app a gruppi misti, i risultati potrebbero non essere quelli voluti o previsti.

    Si supponga ad esempio di assegnare un gruppo di dispositivi al gruppo di utenti **Tutti gli utenti**, escludendo però il gruppo di dispositivi **Tutti i dispositivi personali**. In questa assegnazione di app a gruppo misto il gruppo **Tutti gli utenti** riceverà l'app. L'esclusione non viene applicata.

Non è quindi consigliabile assegnare app a gruppi misti.

> [!NOTE]
> Quando si imposta un'assegnazione di gruppo per un'app, il tipo **Non applicabile** è deprecato e viene sostituito con la funzionalità di esclusione di gruppi. 
>
> Intune fornisce per praticità i gruppi **Tutti gli utenti** e **Tutti i dispositivi** creati in precedenza nella console. Per praticità, i gruppi hanno ottimizzazioni predefinite. È consigliabile usare questi gruppi per scegliere tutti gli utenti e tutti i dispositivi invece dei gruppi "tutti gli utenti" o "tutti i dispositivi" che potrebbero essere stati creati manualmente.  
>
> Android Enterprise supporta l'inclusione e l'esclusione di gruppi. È possibile usare i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi** per l'assegnazione di app Android Enterprise. 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>Includere ed escludere gruppi durante l'assegnazione di app 
Per assegnare un'app ai gruppi usando l'assegnazione di inclusione ed esclusione:
1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro **App client** selezionare **App**. Viene visualizzato l'elenco di app aggiunte.
5. Selezionare l'app che si vuole assegnare. Un dashboard visualizza le informazioni sull'app. 
6. Nella sezione **Gestisci** del menu selezionare **Assegnazioni**. 

    ![Includere assegnazioni di app quando si assegnano app](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)
7. Selezionare **Aggiungi gruppo** per aggiungere i gruppi di utenti assegnati all'app. 
8. Nel riquadro **Aggiungi gruppo** selezionare un **tipo di assegnazione** tra quelli disponibili.
9. Come tipo di assegnazione, selezionare **Disponibile con o senza registrazione**.

    ![Assegnazioni di app di Intune - Aggiungi gruppo](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
10. Selezionare **Gruppi inclusi** per selezionare il gruppo di utenti per cui si vuole rendere questa app disponibile.

    > [!NOTE]
    > Quando si aggiunge un gruppo, se sono già stati inclusi altri gruppi per un tipo di assegnazione specifico, l'app risulterà preselezionata e non potrà essere modificata per gli altri tipi di assegnazione di inclusione. Il gruppo usato non potrà essere usato come gruppo incluso.

11. Selezionare **Sì** per rendere questa app disponibile a tutti gli utenti.

    ![Assegnazioni di app di Intune - Includere gruppi](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
12. Fare clic su **OK** per impostare il gruppo da includere.
13. Selezionare **Gruppi esclusi** per selezionare il gruppo di utenti per cui si vuole rendere questa app non disponibile. 
14. Selezionare i gruppi da escludere. Questa app verrà resa non disponibile per tali gruppi.

    ![Assegnazioni di app di Intune - Escludere gruppi](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
15. Selezionare **Seleziona** per completare la selezione dei gruppi.
16. Nel riquadro **Aggiungi gruppo** selezionare **OK**. Verrà visualizzato l'elenco **Assegnazioni** dell'app.
17. Fare clic su **Salva** per attivare le assegnazioni di gruppi per l'app.

Quando si creano le assegnazioni di gruppi, i gruppi che sono già stati assegnati non sono disponibili per la modifica. Se si vuole selezionare un gruppo che non è attualmente disponibile, prima rimuovere l'app dall'elenco assegnato dell'app. 

Per modificare le assegnazioni, nell'elenco **Assegnazioni** dell'app selezionare la riga che contiene l'assegnazione specifica da modificare. È anche possibile rimuovere un'assegnazione selezionando i puntini di sospensione ( **...** ) alla fine di una riga e quindi selezionando **Rimuovi**. Per modificare la visualizzazione dell'elenco **Assegnazioni**, raggruppare per **Tipo di assegnazione** o per **Inclusi/Esclusi**.

![Assegnazioni di app in Intune - Procedura completata](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sull'inclusione e l'esclusione di assegnazioni di gruppi per le app, vedere il [blog di Microsoft Intune](https://aka.ms/new_app_assignment_process).
- Vedere come [monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).
