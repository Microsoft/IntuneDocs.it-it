---
title: Connettere l'account di Intune all'account di Google Play gestito.
titleSuffix: Microsoft Intune
description: Informazioni su come connettere l'account di Intune all'account di Google Play gestito.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 581d88e49391bc874625e9c84318c039706b0c1b
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124827"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Connettere l'account di Intune all'account di Google Play gestito

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Per supportare il [profilo di lavoro Android Enterprise](android-work-profile-enroll.md) e i [dispositivi Android Enterprise completamente gestiti](android-fully-managed-enroll.md) e [dedicati](android-kiosk-enroll.md), è necessario connettere l'account del tenant di Intune all'account di Google Play gestito.  

Per facilitare la configurazione e l'uso delle funzionalità di gestione di Android Enterprise, dopo la connessione a Google Play, Intune aggiunge automaticamente quattro app comuni correlate ad Android Enterprise alla console di amministrazione di Intune. Le quattro app per Android Enterprise sono le seguenti:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Usata per gli scenari di Android Enterprise completamente gestiti.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - Consente di accedere agli account se si usa la verifica a due fattori.
- **[Portale aziendale di Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Usare per gli scenari con criteri di protezione app e profili di lavoro di Android Enterprise.
- [Schermata iniziale gestita](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Usata per gli scenari di Android Enterprise dedicati/in modalità a schermo intero.

> [!NOTE]
> A causa dell'interazione tra i domini Google e Microsoft, questa procedura potrebbe richiedere la modifica delle impostazioni del browser.  Verificare che "portal.azure.com" e "play.google.com" si trovino nella stessa area di sicurezza del browser.

1. Se non è stato ancora fatto, preparare la gestione dei dispositivi mobili [impostando l'autorità di gestione dei dispositivi mobili](../fundamentals/mdm-authority-set.md) come **Microsoft Intune**.
2. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e scegliere **Dispositivi** > **Android** > **Registrazione Android** > **Google Play gestito**.  Se si usa un ruolo di amministratore di Intune personalizzato, l'accesso richiede le autorizzazioni di lettura e aggiornamento dell'organizzazione.
   
   ![Schermata di registrazione di Android Enterprise](./media/connect-intune-android-enterprise/android-work-bind.png)

3. Selezionare **Accetto** per concedere a Microsoft l'autorizzazione a [inviare informazioni su utente e dispositivo a Google](../protect/data-intune-sends-to-google.md). 
   
4. Scegliere **Avviare Google per connettersi subito** per aprire il sito Web Google Play gestito. Il sito Web viene aperto in una nuova scheda del browser.
  
5. Nella pagina di accesso di Google immettere le credenziali dell'account Google che verrà associato a tutte le attività di gestione di Android Enterprise per questo tenant. Questo sarà l'account Google che verrà condiviso dagli amministratori IT dell'organizzazione per gestire e pubblicare le app nella console di Google Play. È possibile usare un account Google esistente oppure crearne uno nuovo. L'account scelto non deve essere associato a un dominio G-Suite.
    
    > [!Note]
    > Se si usa il browser Microsoft Edge, fare clic su **Accedi** nell'angolo superiore destro per accedere all'account Google.

6. Specificare il nome della società in **Nome organizzazione**. Come **provider della gestione della mobilità aziendale** deve essere visualizzato **Microsoft Intune**.

7. Accettare il contratto di Android e scegliere **Conferma**. La richiesta verrà elaborata.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Disconnettere l'account amministrativo di Android Enterprise

È possibile disattivare la registrazione e la gestione di Android Enterprise. A tale scopo, è innanzitutto necessario ritirare tutti i dispositivi Android Enterprise registrati, inclusi i dispositivi con profilo di lavoro, i dispositivi dedicati e i dispositivi completamente gestiti. Scegliere quindi **Disconnetti** nella console di amministrazione di Intune per rimuovere tutti i dispositivi con profilo di lavoro Android Enterprise registrati e i dispositivi completamente gestiti dalla registrazione. L'operazione rimuove anche la relazione tra l'account di Google Play gestito e Intune.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) come amministratore di Intune.
2. Scegliere **Dispositivi** > **Android** > **Registrazione Android** > **Google Play gestito** > **Disconnetti**.
3. Scegliere **Sì** per disconnettere e annullare la registrazione di tutti i dispositivi Android Enterprise da Intune.

## <a name="next-steps"></a>Passaggi successivi

Dopo la connessione all'account di Google Play gestito, è possibile [configurare i dispositivi con profilo di lavoro Android Enterprise](android-work-profile-enroll.md) e [configurare i dispositivi Android Enterprise dedicati](android-kiosk-enroll.md) e [configurare i dispositivi Android Enterprise completamente gestiti](android-fully-managed-enroll.md)
