---
title: Connettere l'account di Intune all'account di Google Play gestito.
titleSuffix: Microsoft Intune
description: Informazioni su come connettere l'account di Intune all'account di Google Play gestito.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19efd0821deeac0e76c60ee67e6230da554391a0
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567387"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Connettere l'account di Intune all'account di Google Play gestito

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Per supportare il [profilo di lavoro Android Enterprise](android-work-profile-enroll.md) e i [dispositivi Android Enterprise completamente gestiti](android-fully-managed-enroll.md) e [dedicati](android-kiosk-enroll.md), è necessario connettere l'account del tenant di Intune all'account di Google Play gestito.  

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

È possibile disattivare la registrazione e la gestione di Android Enterprise. A tale scopo occorre prima ritirare tutti i dispositivi con profilo di lavoro Android Enterprise registrati. Scegliere quindi **Disconnetti** nella console di amministrazione di Intune per annullare la registrazione di tutti i dispositivi con profilo di lavoro Android Enterprise e dei dispositivi dedicati registrati. L'operazione rimuove anche la relazione tra l'account di Google Play gestito e Intune.

1. Come amministratore di Intune, nel [portale di Azure](https://portal.azure.com) scegliere **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**.
2. Scegliere **Registrazione del dispositivo** > **Registrazione Android** > **Google Play gestito** > **Disconnetti**.
3. Scegliere **Sì** per disconnettere e annullare la registrazione di tutti i dispositivi Android Enterprise da Intune.

## <a name="next-steps"></a>Passaggi successivi

Dopo la connessione all'account di Google Play gestito, è possibile [configurare i dispositivi con profilo di lavoro Android Enterprise](android-work-profile-enroll.md) e [configurare i dispositivi Android Enterprise dedicati](android-kiosk-enroll.md).
