---
title: Come amministrare in remoto i dispositivi Android con TeamViewer
titleSuffix: Intune on Azure
description: Informazioni su come amministrare in remoto i dispositivi Android con TeamViewer."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 15a005ae2b84c7bd4f913f892089965c10f3b23e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="provide-remote-assistance-for-intune-managed-android-devices"></a>Fornire assistenza remota per i dispositivi Android gestiti da Intune

Intune consente di usare il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per consentire agli amministratori di offrire assistenza remota agli utenti che eseguono dispositivi Android. Usare le informazioni in questo argomento per configurare le impostazioni e iniziare a usare questa funzionalità.

## <a name="before-you-start"></a>Prima di iniziare

### <a name="required-permissions"></a>Autorizzazioni richieste

Verificare che all'utente del portale di Azure siano assegnate le autorizzazioni seguenti come [ruolo di Intune](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control):
- Per consentire all'amministratore di modificare le impostazioni di TeamViewer Connector, concedere l'autorizzazione **Aggiornare l'assistenza remota**.
- Per consentire all'amministratore di avviare una nuova sessione di assistenza remota, concedere l'autorizzazione **Richiedere l'assistenza remota**. Gli utenti con questa autorizzazione possono richiedere di avviare una sessione per qualsiasi utente, senza limiti derivanti dall'ambito di assegnazione del ruolo di Intune. Gli ambiti di assegnazione del ruolo di Intune non limitano i dispositivi o gli utenti per cui è possibile avviare richieste di assistenza remota.

>[!NOTE]
>Abilitando TeamViewer, si consente a TeamViewer Connector per Intune di creare sessioni di TeamViewer, leggere i dati di Active Directory e salvare il token di accesso dell'account TeamViewer.

### <a name="configure-the-intune-teamviewer-connector"></a>Configurare TeamViewer Connector per Intune

Prima di poter fornire assistenza remota ai dispositivi Android, sarà necessario configurare TeamViewer Connector per Intune, eseguendo le operazioni seguenti:


1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Installazione** > **TeamViewer Connector**.
5. Nel pannello **TeamViewer Connector** fare clic su **Abilita** e quindi visualizzare e accettare il contratto di licenza del servizio TeamViewer.
6. Scegliere **Accedere a TeamViewer per l'autorizzazione**.
7. Verrà visualizzata una pagina Web del sito di TeamViewer. Immettere le credenziali della licenza di TeamViewer e quindi fare clic su **Accedi**.


## <a name="how-to-remotely-administer-an-android-device"></a>Come amministrare in remoto un dispositivo Android

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi** scegliere **Gestisci** > **Tutti i dispositivi**.
5. Selezionare il dispositivo che si vuole amministrare in remoto e quindi nel pannello delle proprietà del dispositivo scegliere **Altro** > **Nuova sessione di assistenza remota**.
6. Dopo la connessione di Intune al servizio di TeamViewer, verranno visualizzate alcune informazioni sul dispositivo Android. Scegliere **Connetti** per avviare la sessione remota.

![Finestre di TeamViewer in Android](./media/android-teamviewer.png)

Nella finestra di TeamViewer è possibile eseguire una serie di azioni remote nel dispositivo Android, incluso il controllo remoto del dispositivo. Per informazioni dettagliate sulle azioni è possibile eseguire, vedere la [documentazione di TeamViewer](https://www.teamviewer.com/support/documents/).

Al termine chiudere la finestra di TeamViewer.

## <a name="end-user-notifications"></a>Notifiche per l'utente finale

Un utente finale vedrà un flag di notifica sull'icona dell'app Portale aziendale nel dispositivo e un'altra notifica all'apertura dell'app, quindi potrà accettare la richiesta di assistenza remota.
