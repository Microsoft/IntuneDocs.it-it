---
title: Distribuire app a dispositivi Android for Work | Documentazione Microsoft
description: Usare questo argomento per sincronizzare e quindi distribuire app ai dispositivi Android for Work da Google Play for Work.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 31e28514ab4bdb0f5af261a1f7c87633ca0bd4a6
ms.openlocfilehash: e67ec317b22e18d0be8bca449b9382f74935d6e8


---

# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Come distribuire app a dispositivi Android for Work con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

La distribuzione di app a dispositivi Android for Work avviene in modo diverso rispetto alla distribuzione a dispositivi Android standard. Tutte le app installate per Android for Work provengono da Google Play for Work. Accedere allo store, cercare le app desiderate e approvarle.
L'app viene quindi visualizzata nel nodo **App acquistate con Volume Purchase Program** della console di Intune. Da qui è possibile gestire la distribuzione dell'app allo stesso modo in cui si distribuiscono le altre app.

Inoltre, se sono state create app line-of-business (LOB), è possibile distribuirle. A tale scopo, è necessario creare un account Google Developer che consente di pubblicare le app in un'area privata di Google Play e di sincronizzarle con Intune.

## <a name="before-you-start"></a>Prima di iniziare

1. Assicurarsi di aver configurato l'uso di Intune con Android for Work nella scheda **Amministrazione** della console di Intune.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizzare un'app da Google Play for Work


1. Passare a [Google Play for Work](https://play.google.com/work). Accedere con lo stesso account usato per configurare la connessione tra Intune e Android for Work.
2. Cercare nello store l'app che si vuole distribuire usando Intune.
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

## <a name="deploy-an-android-for-work-app"></a>Distribuire un'app Android for Work

In genere la sincronizzazione di Intune con Google Play for Work viene eseguita due volte al giorno. Se è stata approvata un'app dallo store e l'app non è ancora visibile nel nodo **App acquistate con Volume Purchase Program** dell'area di lavoro **App** è possibile forzare una sincronizzazione immediata come descritto di seguito:

1. Nella [console di amministrazione di Intune](https://manage.microsoft.com) scegliere **Amministrazione** > **Gestione dei dispositivi mobili** > **Android for Work**.
2. Nella pagina **Configurazione della gestione del dispositivo mobile Android for Work** scegliere **Sincronizza**.
3. La pagina visualizza anche l'ora e lo stato dell'ultima sincronizzazione.

Quando l'app è visualizzata nel nodo **App acquistate con Volume Purchase Program** dell'area di lavoro **App**, è possibile [distribuirla come qualsiasi altra app](deploy-apps-in-microsoft-intune.md). È possibile distribuire l'app solo a gruppi di utenti. Attualmente, è possibile selezionare solo le azioni **Obbligatorio** e **Disinstalla**. Da ottobre 2016 verrà aggiunta l'azione di distribuzione **Disponibile** ai nuovi tenant.

Una volta distribuita, l'app verrà installata nei dispositivi selezionati come destinazione. All'utente del dispositivo non verrà richiesta l'approvazione.



<!--HONumber=Feb17_HO1-->


