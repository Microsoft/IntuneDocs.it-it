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
ms.openlocfilehash: 4168f78bff8937ca403cdb75b1028954cbbebd6f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Come assegnare app a dispositivi Android for Work con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work è un programma per i dispositivi Android. Tutte le app installate in dispositivi Android for Work provengono da Google Play for Work. L'assegnazione di app a dispositivi Android for Work avviene in modo diverso rispetto all'assegnazione di app a dispositivi Android standard. Accedere allo store, cercare le app desiderate e approvarle. L'app viene quindi visualizzata nel nodo **App con licenza** del portale di Azure. Da qui è possibile gestire l'assegnazione dell'app allo stesso modo in cui si assegnano le altre app.

Inoltre, se sono state create app line-of-business (LOB) personalizzate, è possibile assegnarle come segue:
- Registrarsi per ottenere un account Google Developer che consente di pubblicare le app in un'area privata dello store Google Play.
- Sincronizzare le app con Intune.

## <a name="before-you-start"></a>Prima di iniziare

Assicurarsi di avere configurato l'uso di Intune con Android for Work nel carico di lavoro **Registrazione del dispositivo** del portale di Azure.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizzare un'app da Google Play for Work

1. Passare a [Google Play for Work](https://play.google.com/work). Accedere con lo stesso account usato per configurare la connessione tra Intune e Android for Work.
2. Cercare nello store l'app che si vuole assegnare con Intune e selezionarla.
3. Selezionare **Approva** nella pagina in cui è visualizzata l'app. Gli esempi seguenti mostrano che è stata scelta l'app Microsoft Excel.</br>

    ![Esempio - Approvare un'app in Google Play for Work](media/approve.png)</br>
    
   Viene visualizzata una finestra per l'app in cui viene richiesto di concedere le autorizzazioni che consentono all'app di eseguire diverse operazioni. 

4. Selezionare **Approva** per accettare le autorizzazioni per l'app e continuare.</br>

    ![Esempio - Approvare le autorizzazioni per un'app](media/approve-app-permissions.png)

5. Scegliere come gestire le nuove richieste di autorizzazioni per le app. Selezionare quindi **Salva** per salvare la modalità di gestione delle nuove richieste di autorizzazioni per le app.</br>

    ![Esempio - Salvare le nuove richieste di autorizzazioni per le app](media/approve-app-settings.png)</br>

    L'app viene approvata e visualizzata nella console di amministrazione IT. A questo punto, è possibile [sincronizzare l'app Android for Work con Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Sincronizzare un'app Android for Work con Intune

Se è stata approvata un'app dallo store e l'app non è ancora visualizzata nel nodo **App con licenza** del carico di lavoro **App per dispositivi mobili**, forzare una sincronizzazione immediata in questo modo:

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Android for Work** nella sezione **Installazione**.
5. Nel riquadro Android for Work scegliere **Sincronizza**. La pagina aggiornerà l'ora e lo stato dell'ultima sincronizzazione.
6. Nel carico di lavoro **App per dispositivi mobili** selezionare **App** per visualizzare la nuova app Android for Work disponibile.

Quando l'app viene visualizzata nel nodo **Licenze dell'app** del carico di lavoro **App per dispositivi mobili**, è possibile [assegnarla come qualsiasi altra app](/intune-azure/manage-apps/deploy-apps). È possibile assegnare l'app solo a gruppi di utenti.

Dopo aver assegnato l'app, questa viene installata nei dispositivi selezionati come destinazione. All'utente del dispositivo non viene chiesto di approvare l'installazione.

## <a name="manage-android-for-work-app-permissions"></a>Gestire le autorizzazioni per le app Android for Work
Android for Work richiede l'approvazione delle app nella console Web gestita di Google Play prima di sincronizzarle con Intune e distribuirle agli utenti.  Poiché Android for Work consente di eseguire automaticamente il push di queste app nei dispositivi degli utenti, è necessario accettare le autorizzazioni dell'app per conto di tutti gli utenti.  Gli utenti finali non vedono alcuna autorizzazione dell'app durante l'installazione ed è quindi importante leggere e comprendere queste autorizzazioni.

Quando lo sviluppatore di un'app pubblica una nuova versione dell'app con autorizzazioni aggiornate, tali autorizzazioni non vengono accettate automaticamente, anche se sono state approvate le autorizzazioni precedenti. I dispositivi che eseguono la versione precedente dell'app possono comunque usarla. Tuttavia, l'app non viene aggiornata fino a quando non vengono approvate le nuove autorizzazioni. I dispositivi in cui non è installata l'app non la installano fino a quando non vengono approvate le nuove autorizzazioni dell'app.

### <a name="how-to-update-app-permissions"></a>Come aggiornare le autorizzazioni di app

Visitare periodicamente la console di Google Play gestita per verificare se sono disponibili nuove autorizzazioni. È possibile configurare Google Play per l'invio di un messaggio di posta elettronica quando sono necessarie nuove autorizzazioni per un'app approvata. Se si assegna un'app e si nota che non è installata nei dispositivi, verificare la disponibilità di nuove autorizzazioni seguendo questi passaggi:

1. Vedere http://play.google.com/work
2. Accedere con l'account Google usato per pubblicare e approvare le app.
3. Nella scheda **Aggiornamenti** verificare se sono presenti app che richiedono un aggiornamento.  Le app elencate richiedono nuove autorizzazioni e non vengono assegnate finché non vengono applicate.  

In alternativa, è possibile configurare Google Play per approvare di nuovo automaticamente le autorizzazioni delle app per ogni app. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Utilizzo di un'app line-of-business dallo store Google Play for Work

1. Passare a Google Play Developer Console [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Accedere con lo stesso account usato per configurare la connessione tra Intune e Android for Work. Se si accede per la prima volta, è necessario registrarsi e pagare una quota per diventare membro del programma per gli sviluppatori Google.
3. Nella console scegliere **Aggiungi nuova applicazione**.
4. Caricare e specificare informazioni sull'app allo stesso modo in cui si pubblicano le altre app in Google Play. È necessario tuttavia selezionare l'impostazione **Only make this application available to my organization (<*organization name*>)** (Rendi disponibile l'app soltanto per la mia organizzazione):</br>

    ![Opzione per rendere disponibile l'app soltanto per la propria organizzazione](media/restrict.png)</br>

Questa operazione garantisce che l'app sia disponibile soltanto per la propria organizzazione e non nello store pubblico Google Play.
Per altre informazioni su come caricare e pubblicare app Android, vedere la [Guida di Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
5. Dopo aver pubblicato l'app, passare a [Google Play for Work](https://play.google.com/work). Accedere con lo stesso account usato per configurare la connessione tra Intune e Android for Work.
6. Nel nodo **App** dello store verificare che l'app pubblicata sia visibile. L'app viene approvata automaticamente per essere sincronizzata con Intune.

## <a name="next-steps"></a>Passaggi successivi

- [Come assegnare app ai gruppi](apps-deploy.md)

