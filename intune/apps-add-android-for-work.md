---
title: Assegnare app a dispositivi Android for Work | Microsoft Docs
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune di Azure: usare questo argomento per sincronizzare e quindi assegnare app a dispositivi Android for Work dallo store Google Play for Work.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 49e86ab665d9022739c0330092734ba897ea3b02
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Come assegnare app a dispositivi Android for Work con Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

L'assegnazione di app a dispositivi Android for Work avviene in modo diverso rispetto all'assegnazione di app a dispositivi Android standard. Tutte le app installate per Android for Work provengono da Google Play for Work. Accedere allo store, cercare le app desiderate e approvarle.
L'app viene quindi visualizzata nel nodo **App con licenza** del portale di Intune. Da qui è possibile gestire l'assegnazione dell'app allo stesso modo in cui si assegnano le altre app.

Inoltre, se sono state create app line-of-business (LOB) personalizzate, è possibile assegnarle. A tale scopo, è necessario creare un account Google Developer che consente di pubblicare le app in un'area privata di Google Play e di sincronizzarle con Intune.

## <a name="before-you-start"></a>Prima di iniziare

Assicurarsi di aver configurato l'uso di Intune con Android for Work nel carico di lavoro **Registrazione del dispositivo** del portale di Intune.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizzare un'app da Google Play for Work


1. Passare a [Google Play for Work](https://play.google.com/work). Accedere con lo stesso account usato per configurare la connessione tra Intune e Android for Work.
2. Cercare nello store l'app che si vuole assegnare con Intune.
3. Nella pagina dell'app selezionata scegliere **Approva**. In questo esempio è stata scelta l'app Microsoft Excel.<br>
  ![Esempio di approvazione di un'app](media/approve.png)
4. Viene visualizzata una finestra per l'app in cui viene richiesto di concedere le autorizzazioni che consentono all'app di eseguire diverse operazioni. È necessario scegliere **Approva** per continuare.<br>
  ![Esempio di approvazione delle autorizzazioni per un'app](media/approve-app-permissions.png)
5. Dopo qualche secondo, viene visualizzato un messaggio di conferma che comunica che l'app è stata approvata ed è disponibile nella console di amministrazione IT.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Pubblicare e sincronizzare un'app line-of-business da Google Play for Work

1. Passare a Google Play Developer Console [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Accedere con lo stesso account usato per configurare la connessione tra Intune e Android for Work. Se si accede per la prima volta, è necessario registrarsi e pagare una quota per diventare membro del programma per gli sviluppatori Google.
3. Nella console scegliere **Aggiungi nuova applicazione**.
4. Caricare e specificare informazioni sull'app allo stesso modo in cui si pubblicano le altre app in Google Play. È necessario tuttavia selezionare l'impostazione **Only make this application available to my organization (<*organization name*>)** (Rendi disponibile l'app soltanto per la mia organizzazione) come mostrato di seguito.<br>
  ![Opzione per rendere disponibile l'app soltanto per la propria organizzazione](media/restrict.png)<br>
In questo modo l'app sarà disponibile soltanto per la propria organizzazione e non sarà disponibile nel canale pubblico di Google Play.
Per altre informazioni su come caricare e pubblicare app Android, vedere la [Guida di Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
5. Dopo aver pubblicato l'app, passare a [Google Play for Work](https://play.google.com/work). Accedere con lo stesso account usato per configurare la connessione tra Intune e Android for Work.
6. Nel nodo **App** dello store verificare che l'app pubblicata sia visibile. Si noti che l'app è stata approvata automaticamente per essere sincronizzata con Intune.

## <a name="assign-an-android-for-work-app"></a>Assegnare un'app Android for Work

Se è stata approvata un'app dallo store e l'app non è ancora visualizzata nel nodo **App con licenza** del carico di lavoro **App per dispositivi mobili**, è possibile forzare una sincronizzazione immediata in questo modo:

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Installazione** > **Android for Work**.
5. Nel pannello Android for Work scegliere **Sincronizza**.
6. La pagina visualizza anche l'ora e lo stato dell'ultima sincronizzazione.

Quando l'app è visualizzata nel nodo **App con licenza** del carico di lavoro **App per dispositivi mobili**, è possibile [assegnarla come qualsiasi altra app](/intune-azure/manage-apps/deploy-apps). È possibile assegnare l'app solo a gruppi di utenti.

Dopo aver assegnato l'app, questa viene installata nei dispositivi selezionati come destinazione. All'utente del dispositivo non viene chiesto di approvare l'installazione.

## <a name="manage-app-permissions"></a>Gestione delle autorizzazioni dell'app
Android for Work richiede l'approvazione delle app nella console Web gestita di Google Play prima di sincronizzarle con Intune e distribuirle agli utenti.  Poiché Android for Work consente di eseguire automaticamente il push di queste app nei dispositivi degli utenti, è necessario accettare le autorizzazioni dell'app per conto di tutti gli utenti.  Gli utenti finali non vedranno alcuna autorizzazione dell'app durante l'installazione ed è quindi importante leggere e comprendere queste autorizzazioni.

Quando lo sviluppatore di un'app pubblica una nuova versione dell'app con autorizzazioni aggiornate, tali autorizzazioni non vengono accettate automaticamente, anche se sono state approvate le autorizzazioni precedenti. I dispositivi che eseguono la versione precedente dell'app possono continuare a usarla, ma l'app non può essere aggiornata finché non vengono approvate le nuove autorizzazioni. I dispositivi in cui non è installata l'app non possono installarla finché le nuove autorizzazioni dell'app non vengono approvate.

### <a name="how-to-update-app-permissions"></a>Come aggiornare le autorizzazioni di app

È consigliabile visitare periodicamente la console di Google Play gestita per verificare se sono disponibili nuove autorizzazioni. Se si assegna un'app e si nota che non è installata nei dispositivi, verificare la disponibilità di nuove autorizzazioni seguendo questi passaggi:

1. Visitare il sito Web di Google Play all'indirizzo http://play.google.com/work
2. Accedere con l'account Google usato per pubblicare e approvare le app.
3. Nella scheda **Aggiornamenti** verificare se sono presenti app che richiedono un aggiornamento.  Le app elencate richiedono nuove autorizzazioni e non vengono assegnate finché non le ricevono.  

