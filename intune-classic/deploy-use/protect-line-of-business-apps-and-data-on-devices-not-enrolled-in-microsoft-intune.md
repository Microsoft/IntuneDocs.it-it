---
title: Proteggere le app line-of-business in dispositivi non registrati
description: Questo argomento illustra come preparare le app line-of-business in modo da applicare i criteri di gestione delle applicazioni mobili che consentono di evitare la perdita di dati.
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0b09daa05db673817bea67cd8b88c2ac63be7f1e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="protect-line-of-business-apps-and-data-on-devices-that-are-not-enrolled-in-microsoft-intune"></a>Proteggere app e dati line-of-business su dispositivi non registrati

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I criteri di gestione delle applicazioni mobili consentono di proteggere i dati aziendali limitando le azioni che possono causare la perdita dei dati aziendali e applicando i requisiti di accesso ai dati, ad esempio il PIN dell'app. Prima di applicare i criteri di gestione delle applicazioni mobili alle app line-of-business per iOS e Android, è necessario eseguire il wrapping dell'app con lo strumento di wrapping delle app di Microsoft Intune. Il wrapping dell'app è il processo di applicazione di un livello di gestione a un'app per dispositivi mobili senza alcuna modifica dell'applicazione, che viene quindi distribuita agli utenti.  

Questo argomento elenca i passaggi per l'applicazione dei criteri MAM alle app a cui gli utenti hanno accesso su **dispositivi di proprietà dei dipendenti e non gestiti** e dispositivi gestiti da **soluzioni di gestione di dispositivi mobili (MDM) di terze parti**.  Per preparare le app line-of-business eseguite su **dispositivi registrati in gestione di dispositivi mobili di Intune**, vedere [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](/intune/apps-prepare-mobile-application-management).


##  <a name="step-1-prepare-the-app"></a>Passaggio 1: Preparare l'app.

Prima di applicare i criteri MAM a un'app è necessario eseguire il wrapping di quest'ultima con lo strumento di wrapping delle app di Microsoft Intune per [iOS](prepare-ios-apps-for-mo/intune/apps-prepare-mobile-application-managementoid](/intune/app-wrapper-prepare-android). In alternativa, usare [Intune App SDK](/intune/app-sdk) per integrare manualmente le funzionalità di Intune per la protezione delle app.

Per informazioni sull'uso dello strumento di wrapping delle app rispetto a Intune App SDK, vedere [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](/intune/apps-prepare-mobile-application-management).

## <a name="step-2-add-the-app"></a>Passaggio 2: Aggiungere l'app.

Per associare l'app line-of-business ai criteri MAM, è necessario aggiungere i dettagli dell'app alla sottoscrizione o al tenant Intune con la procedura seguente:

1. Nel [portale di Azure](https://portal.azure.com/) passare a **Gestione di applicazioni mobili di Intune**  >  **Impostazioni** e scegliere **App line-of-business**.

  ![Screenshot del pannello delle impostazioni con l'opzione line-of-business](../media/mam-azure-portal-lob-on-settings.png)

2. Nel pannello **App line-of-business** scegliere **Aggiungi app personalizzata**.

  ![Screenshot del pannello App line-of-business con il pulsante Aggiungi app personalizzata nella parte superiore](../media/mam-azure-portal-add-lob-app-action.png)
3.  Specificare il nome dell'app, l'identificatore del bundle nel campo Identificatore dell'app e la piattaforma (iOS o Android).

  ![Screenshot del pannello Aggiungi app personalizzata](../media/mam-azure-portal-add-app-details.png)

  Questo passaggio crea una voce unica per l'app. L'app viene visualizzata anche nell'elenco App di destinazione di un criterio MAM del tenant, come descritto nel passaggio successivo.

## <a name="step-3-apply-mam-policies"></a>Passaggio 3: Applicare i criteri MAM
Dopo aver caricato nel servizio i metadati dell'app, questa appare nell'elenco delle app. È ora possibile [creare un nuovo criterio o usare un criterio esistente](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) e applicarlo all'app line-of-business aggiunta nel passaggio 2.

>[!IMPORTANT]
>È necessario assegnare il criterio MAM agli utenti che useranno l'applicazione sottoposta a wrapping.  Gli utenti a cui non è stato distribuito questo criterio non potranno usare l'app.


  ![Screenshot del pannello App di destinazione con la nuova app line-of-business](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## <a name="step-4-distribute-the-app"></a>Passaggio 4: Distribuire l'app.
È possibile distribuire app agli utenti nei modi seguenti:
* Per i dispositivi registrati in una soluzione MDM di terze parti è possibile distribuire le app con la soluzione MDM.
* Per i dispositivi non gestiti da una soluzione MDM è necessaria una soluzione personalizzata. Gli utenti dovranno scaricare e installare l'app sul loro dispositivo.

## <a name="change-the-metadata"></a>Modificare i metadati
Per la modifica di dettagli dell'app come il nome o l'identificatore bundle è necessario [rimuovere l'app](#remove-apps) e quindi [aggiungerla](#step-2-add-the-app) con i nuovi metadati.

##  <a name="remove-apps"></a>Rimuovere app
È possibile rimuovere un'app line-of-business dall'elenco di app. L'app viene rimossa dall'elenco e l'associazione ai criteri MAM viene eliminata. L'app, tuttavia, non viene rimossa o disinstallata dal dispositivo dell'utente.  

1.  Nel [portale di Azure](https://portal.azure.com/) passare a **Gestione di applicazioni mobili di Intune** > **Impostazioni**. Nel pannello **Impostazioni** scegliere **Line-of-business** per aprire l'elenco delle app esistenti.  
2.  Chiudere l'app da rimuovere e scegliere **(...)**.

  ![Screenshot del pannello App line-of-business con il menu con puntini di sospensione](../media/mam-azure-portal-lob-context-menu.png)
3.  Scegliere **Elimina applicazione** per eliminare l'app.

  ![Screenshot del pannello line-of-business con l'opzione di eliminazione dell'applicazione](../media/mam-azure-portal-delete-app.png)

  Le app vengono rimosse dall'elenco di app line-of-business e dall'elenco delle app di destinazione nel criterio MAM.
