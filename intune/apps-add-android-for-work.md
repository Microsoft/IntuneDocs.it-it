---
title: Assegnare app a dispositivi Android for Work
titlesuffix: Microsoft Intune
description: Informazioni su come sincronizzare e assegnare app ai dispositivi Android for Work da Google Play for Work.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1742c33642667a9e7b8ca2f780094345959cd86c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="assign-apps-to-android-for-work-devices-with-intune"></a>Assegnare app a dispositivi Android for Work con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work è un programma per i dispositivi Android. Tutte le app installate in dispositivi Android for Work provengono da Google Play for Work. L'assegnazione di app a dispositivi Android for Work avviene in modo diverso rispetto all'assegnazione di app a dispositivi Android standard. Accedere allo store, cercare le app desiderate e approvarle. L'app viene quindi visualizzata nel nodo **App con licenza** del portale di Azure ed è possibile gestire l'assegnazione dell'app allo stesso modo di qualsiasi altra app.

Inoltre, se sono state create app line-of-business personalizzate, è possibile assegnarle come segue:
- Registrarsi per ottenere un account Google Developer che consente di pubblicare le app in un'area privata dello store Google Play.
- Sincronizzare le app con Intune.

## <a name="before-you-start"></a>Prima di iniziare

Assicurarsi di avere configurato l'uso di Intune con Android for Work nel carico di lavoro **Registrazione del dispositivo** del portale di Azure.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizzare un'app da Google Play for Work

1. Passare a [Google Play for Work](https://play.google.com/work). Accedere con lo stesso account usato per configurare la connessione tra Intune e Android for Work.
2. Cercare nello store l'app che si vuole assegnare usando Intune e selezionarla.
3. Nella pagina in cui è visualizzata l'app selezionare **Approva**.  
    Nell'esempio seguente è stata scelta l'app Microsoft Excel.

    ![Pulsante Approva in Google Play for Work](media/approve.png)
    
   Viene visualizzata una finestra per l'app in cui viene richiesto di concedere le autorizzazioni che consentono all'app di eseguire diverse operazioni. 

4. Selezionare **Approva** per accettare le autorizzazioni per l'app e continuare.

    ![Pulsante Approva per le autorizzazioni per l'app](media/approve-app-permissions.png)

5. Selezionare un'opzione per gestire le nuove richieste di autorizzazioni per l'app e quindi selezionare **Salva**.

    ![Opzioni per gestire le nuove richieste di autorizzazioni per l'app](media/approve-app-settings.png)

    L'app viene approvata e visualizzata nella console di amministrazione IT. È quindi possibile [sincronizzare l'app Android for Work con Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Sincronizzare un'app Android for Work con Intune

Se è stata approvata un'app dallo store e l'app non è ancora visualizzata nel nodo **App con licenza** del carico di lavoro **App per dispositivi mobili**, forzare una sincronizzazione immediata in questo modo:

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App per dispositivi mobili**.
4. Nel riquadro del carico di lavoro **App per dispositivi mobili**, in **Configurazione**, selezionare **Android for Work**.
5. Nel riquadro **Android for Work** selezionare **Sincronizza**.  
    La pagina aggiorna l'ora e lo stato dell'ultima sincronizzazione.
6. Nel riquadro del carico di lavoro **App per dispositivi mobili** selezionare **App**.  
    Viene visualizzata la nuova app Android for Work disponibile.

Quando l'app viene visualizzata nel nodo **Licenze dell'app** del riquadro del carico di lavoro **App per dispositivi mobili**, è possibile [assegnarla come qualsiasi altra app](/intune-azure/manage-apps/deploy-apps). È possibile assegnare l'app solo a gruppi di utenti.

Dopo aver assegnato l'app, questa viene installata nei dispositivi selezionati come destinazione. All'utente del dispositivo non viene chiesto di approvare l'installazione.

## <a name="manage-android-for-work-app-permissions"></a>Gestire le autorizzazioni per le app Android for Work
Android for Work richiede l'approvazione delle app nella console Web gestita di Google Play prima di sincronizzarle con Intune e assegnarle agli utenti. Poiché Android for Work consente di eseguire automaticamente il push delle app nei dispositivi degli utenti, è necessario accettare le autorizzazioni dell'app per conto di tutti gli utenti. Gli utenti non vedono alcuna autorizzazione dell'app durante l'installazione delle app ed è quindi importante leggere e comprendere le autorizzazioni.

Quando lo sviluppatore di un'app pubblica una nuova versione dell'app con autorizzazioni aggiornate, le autorizzazioni non vengono accettate automaticamente, anche se sono state approvate le autorizzazioni precedenti. I dispositivi che eseguono la versione precedente dell'app possono comunque usarla. Tuttavia, l'app non viene aggiornata fino a quando non vengono approvate le nuove autorizzazioni. I dispositivi in cui non è installata l'app non la installano fino a quando non vengono approvate le nuove autorizzazioni dell'app.

### <a name="update-app-permissions"></a>Aggiornare le autorizzazioni di app

Visitare periodicamente la console di Google Play gestita per verificare se sono disponibili nuove autorizzazioni. È possibile configurare Google Play per l'invio di un messaggio di posta elettronica quando sono necessarie nuove autorizzazioni per un'app approvata. Se si assegna un'app e si nota che non è installata nei dispositivi, verificare la disponibilità di nuove autorizzazioni seguendo questa procedura:

1. Andare a [Google Play](http://play.google.com/work).
2. Accedere con l'account Google usato per pubblicare e approvare le app.
3. Selezionare la scheda **Aggiornamenti** e verificare se sono necessari aggiornamenti per le app.  
    Le app elencate richiedono nuove autorizzazioni e non vengono assegnate finché non vengono applicate.

In alternativa, è possibile configurare Google Play per approvare di nuovo automaticamente le autorizzazioni delle app per ogni app. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Utilizzo di un'app line-of-business dallo store Google Play for Work

1. Accedere alla [console di sviluppo di Google Play](https://play.google.com/apps/publish) con lo stesso account usato per configurare la connessione tra Intune e Android for Work.  
    Se si accede per la prima volta, è necessario registrarsi e pagare una quota per diventare membro del programma per gli sviluppatori Google.
2. Nella console selezionare **Add new application** (Aggiungi nuova applicazione).
3. Caricare e specificare informazioni sull'app allo stesso modo in cui si pubblicano le altre app in Google Play. È tuttavia necessario selezionare **Only make this application available to my organization (<*organization name*>)** (Rendi disponibile l'app soltanto per la mia organizzazione).

    ![Rendere disponibile l'app soltanto per la propria organizzazione](media/restrict.png)

    Questa operazione garantisce che l'app sia disponibile soltanto per la propria organizzazione e non nello store pubblico Google Play.

    Per altre informazioni sul caricamento e sulla pubblicazione di app Android, vedere la [Guida di Play Console di Google](https://support.google.com/googleplay/android-developer/answer/113469).
4. Dopo avere pubblicato l'app, accedere a [Google Play](https://play.google.com/work) con lo stesso account usato per configurare la connessione tra Intune e Android for Work.
5. Nel nodo **App** dello store verificare che l'app pubblicata sia visualizzata.  
    L'app viene approvata automaticamente per essere sincronizzata con Intune.

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md) 

