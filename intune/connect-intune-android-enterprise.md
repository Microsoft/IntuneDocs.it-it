---
title: Connettere l'account di Intune all'account Android Enterprise
titlesuffix: Microsoft Intune
description: Informazioni su come connettere l'account di Intune all'account Android Enterprise.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0152d0cb7af418b500c1ac5991f2356bd2e19965
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909083"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>Connettere l'account di Intune all'account Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Per supportare i dispositivi del profilo di lavoro Android e i dispositivi Android in modalità tutto schermo, è necessario connettere l'account del tenant di Intune all'account di Android Enterprise. 

> [!NOTE]
> A causa dell'interazione tra i domini Google e Microsoft, questa procedura potrebbe richiedere la modifica delle impostazioni del browser.  Verificare che "portal.azure.com" e "play.google.com" si trovino nella stessa area di sicurezza del browser.

1. Se non è stato ancora fatto, preparare la gestione dei dispositivi mobili [impostando l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md) come **Microsoft Intune**.
2. Accedere a [Intune dal portale di Azure](https://aka.ms/intuneportal), scegliere **Registrazione del dispositivo** > **Registrazione Android** > **Google Play gestito**.  Se si usa un ruolo di amministratore di Intune personalizzato, l'accesso richiede le autorizzazioni di lettura e aggiornamento dell'organizzazione.
   
   ![Schermata di registrazione di Android Enterprise](./media/android-work-bind.png)

3. Selezionare **Accetto** per concedere a Microsoft l'autorizzazione a [inviare informazioni su utente e dispositivo a Google](data-intune-sends-to-google.md). 
   
4. Scegliere **Avviare Google per connettersi subito** per aprire il sito Web Google Play gestito. Il sito Web viene aperto in una nuova scheda del browser.
  
5. Nella pagina di accesso di Google immettere le credenziali dell'account Google che verrà associato a tutte le attività di gestione di Android Enterprise per questo tenant. Questo sarà l'account Google che verrà condiviso dagli amministratori IT dell'organizzazione per gestire e pubblicare le app nella console di Google Play. È possibile usare un account Google esistente oppure crearne uno nuovo. L'account scelto non deve essere associato a un dominio G-Suite.
    
    > [!Note]
    > Se si usa il browser Microsoft Edge, fare clic su **Accedi** nell'angolo superiore destro per accedere all'account Google.

6. Specificare il nome della società in **Nome organizzazione**. Come **provider della gestione della mobilità aziendale** deve essere visualizzato **Microsoft Intune**.

7. Accettare il contratto di Android e scegliere **Conferma**. La richiesta verrà elaborata.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Disconnettere l'account amministrativo di Android Enterprise

È possibile disattivare la registrazione e la gestione di Android Enterprise. Se si sceglie **Disconnetti** nella console di amministrazione di Intune vengono eliminati tutti i dispositivi del profilo di lavoro Android e i dispositivi in modalità schermo tutto schermo registrati. Viene rimossa anche la relazione tra l'account di Android Enterprise e Intune.

1. Come amministratore di Intune, nel [portale di Azure](https://portal.azure.com) scegliere **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**.
2. Scegliere **Registrazione del dispositivo** > **Registrazione Android** > **Google Play gestito** > **Disconnetti**.
3. Scegliere **Sì** per disconnettere e annullare la registrazione di tutti i dispositivi Android Enterprise da Intune.

## <a name="next-steps"></a>Passaggi successivi

Dopo la connessione all'account di Android Enterprise, è possibile [configurare i dispositivi del profilo di lavoro Android](android-work-profile-enroll.md) e [configurare i dispositivi Android in modalità tutto schermo](android-kiosk-enroll.md).