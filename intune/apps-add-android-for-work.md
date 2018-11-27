---
title: Assegnare app ai dispositivi del profilo di lavoro Android
titlesuffix: Microsoft Intune
description: Informazioni su come sincronizzare e assegnare app ai dispositivi del profilo di lavoro Android dalla versione gestita di Google Play Store.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: c7d5d29df0f91a4cff1060cd10a5d2355e196e39
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180138"
---
# <a name="assign-apps-to-android-work-profile-devices-with-intune"></a>Assegnare app ai dispositivi del profilo di lavoro Android con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android Enterprise è un programma per dispositivi del profilo di lavoro Android e in modalità tutto schermo. Per i dispositivi del profilo di lavoro Android, Android Enterprise è un set di funzionalità e servizi che separa le app e i dati personali da quelli aziendali. Android Enterprise offre opzioni di gestione e privacy aggiuntive quando gli utenti usano i dispositivi Android personali per lavoro. Intune consente la distribuzione di app e impostazioni ai dispositivi del profilo di lavoro Android per assicurarsi che le informazioni di lavoro e quelle personali restino separate. Tutte le app installate nei dispositivi del profilo di lavoro Android provengono dalla versione gestita di Google Play Store. L'assegnazione di app ai dispositivi del profilo di lavoro Android avviene in modo diverso rispetto all'assegnazione di app a dispositivi Android standard. Accedere allo store, cercare le app desiderate e approvarle. L'app viene quindi visualizzata nel nodo **App con licenza** del portale di Azure ed è possibile gestire l'assegnazione dell'app allo stesso modo di qualsiasi altra app.

Inoltre, se sono state create app line-of-business personalizzate, è possibile assegnarle come segue:
- Registrarsi per ottenere un account Google Developer che consente di pubblicare le app in un'area privata dello store Google Play.
- Sincronizzare le app con Intune.

## <a name="before-you-start"></a>Prima di iniziare

Assicurarsi di avere configurato l'uso di Intune con i profili di lavoro Android nel carico di lavoro **Registrazione del dispositivo** del portale di Azure. Per altre informazioni, vedere [Registrare i dispositivi Android](android-work-profile-enroll.md).

## <a name="synchronize-an-app-from-the-managed-google-play-store"></a>Sincronizzare un'app dalla versione gestita di Google Play Store

1. Passare alla [versione gestita di Google Play Store](https://play.google.com/work). Accedere con lo stesso account usato per configurare la connessione tra Intune e Android Enterprise.
2. Cercare nello store l'app che si vuole assegnare usando Intune e selezionarla.
3. Nella pagina in cui è visualizzata l'app selezionare **Approva**.  
    Nell'esempio seguente è stata scelta l'app Microsoft Excel.

    ![Pulsante di approvazione nella versione gestita di Google Play Store](media/approve.png)
    
   Viene visualizzata una finestra per l'app in cui viene richiesto di concedere le autorizzazioni che consentono all'app di eseguire diverse operazioni. 

4. Selezionare **Approva** per accettare le autorizzazioni per l'app e continuare.

    ![Pulsante Approva per le autorizzazioni per l'app](media/approve-app-permissions.png)

5. Selezionare un'opzione per gestire le nuove richieste di autorizzazioni per l'app e quindi selezionare **Salva**.

    ![Opzioni per gestire le nuove richieste di autorizzazioni per l'app](media/approve-app-settings.png)

    L'app viene approvata e visualizzata nella console di amministrazione IT. È quindi possibile [sincronizzare l'app del profilo di lavoro Android con Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-a-managed-google-play-app-with-intune"></a>Sincronizzare un'app della versione gestita di Google Play con Intune

Se è stata approvata un'app dallo store e l'app non è ancora visualizzata nel nodo **App con licenza** del carico di lavoro **App client**, forzare una sincronizzazione immediata in questo modo:

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro del carico di lavoro **App client** in **Installazione** selezionare **Google Play gestito**.
5. Nel riquadro **Google Play gestito** scegliere **Aggiorna**.  
    La pagina aggiorna l'ora e lo stato dell'ultima sincronizzazione.
6. Nel riquadro del carico di lavoro **App client** selezionare **App**.  
    L'app della versione gestita di Google Play, appena resa disponibile, viene visualizzata.

Quando l'app viene visualizzata nel nodo **App licenses** (Licenze delle app) del riquadro del carico di lavoro **App client**, è possibile [assegnarla come qualsiasi altra app](/intune-azure/manage-apps/deploy-apps). È possibile assegnare l'app solo a gruppi di utenti.

Dopo aver assegnato l'app, questa viene installata nei dispositivi selezionati come destinazione. All'utente del dispositivo non viene chiesto di approvare l'installazione.

## <a name="manage-android-enterprise-app-permissions"></a>Gestire le autorizzazioni per le app Android Enterprise
Android Enterprise richiede l'approvazione delle app nella console Web della versione gestita di Google Play prima di sincronizzarle con Intune e assegnarle agli utenti. Poiché Android Enterprise consente di eseguire automaticamente il push delle app ai dispositivi degli utenti, è necessario accettare le autorizzazioni dell'app per conto di tutti gli utenti. Gli utenti non vedono le autorizzazioni durante l'installazione delle app. È quindi importante comprendere le autorizzazioni.

Quando lo sviluppatore di un'app aggiorna le autorizzazioni con una nuova versione dell'app, queste non vengono automaticamente accettate, anche se le autorizzazioni precedenti erano state approvate. I dispositivi che eseguono la versione precedente dell'app possono comunque usarla. Tuttavia, l'app non viene aggiornata fino a quando non vengono approvate le nuove autorizzazioni. I dispositivi in cui non è installata l'app non la installano fino a quando non vengono approvate le nuove autorizzazioni dell'app.

### <a name="update-app-permissions"></a>Aggiornare le autorizzazioni di app

Visitare periodicamente la console di Google Play gestita per verificare se sono disponibili nuove autorizzazioni. È possibile configurare Google Play per l'invio di un messaggio di posta elettronica quando sono necessarie nuove autorizzazioni per un'app approvata. Se si assegna un'app e si nota che non è installata nei dispositivi, verificare la disponibilità di nuove autorizzazioni seguendo questa procedura:

1. Andare a [Google Play](http://play.google.com/work).
2. Accedere con l'account Google usato per pubblicare e approvare le app.
3. Selezionare la scheda **Aggiornamenti** e verificare se sono necessari aggiornamenti per le app.  
    Le app elencate richiedono nuove autorizzazioni e non vengono assegnate finché non vengono applicate.

In alternativa, è possibile configurare Google Play per approvare di nuovo automaticamente le autorizzazioni delle app per ogni app. 

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>Uso di un'app line-of-business dalla versione gestita di Google Play Store

1. Accedere a [Google Play Developer Console](https://play.google.com/apps/publish) con lo stesso account usato per configurare la connessione tra Intune e Android Enterprise.  
    Se si accede per la prima volta, è necessario registrarsi e pagare una quota per diventare membro del programma per gli sviluppatori Google.
2. Nella console selezionare **Add new application** (Aggiungi nuova applicazione).
3. Caricare e specificare informazioni sull'app allo stesso modo in cui si pubblicano le altre app in Google Play. È tuttavia necessario selezionare **Only make this application available to my organization (<*organization name*>)** (Rendi disponibile l'app soltanto per la mia organizzazione).

    ![Rendere disponibile l'app soltanto per la propria organizzazione](media/restrict.png)

    Questa operazione rende disponibile l'app soltanto per la propria organizzazione. Non sarà disponibile nel Google Play Store pubblico.

    Per altre informazioni sul caricamento e sulla pubblicazione di app Android, vedere la [Guida di Play Console di Google](https://support.google.com/googleplay/android-developer/answer/113469).
4. Dopo avere pubblicato l'app, accedere alla [versione gestita di Google Play Store](https://play.google.com/work) con lo stesso account usato per configurare la connessione tra Intune e Android Enterprise.
5. Nel nodo **App** dello store verificare che l'app pubblicata sia visualizzata.  
    L'app viene approvata automaticamente per essere sincronizzata con Intune.

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md) 

