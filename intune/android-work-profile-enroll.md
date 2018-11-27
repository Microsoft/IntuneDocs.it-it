---
title: Registrare i dispositivi del profilo di lavoro Android in Intune
titlesuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi del profilo di lavoro Android in Intune.
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
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b3592ceb2b1a4e7ba32fc0a8b3de53e0f0329d8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179729"
---
# <a name="set-up-enrollment-of-android-work-profile-devices"></a>Configurare la registrazione dei dispositivi del profilo di lavoro Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune consente la distribuzione di app e impostazioni ai dispositivi con profilo di lavoro Android per assicurarsi che le informazioni di lavoro e quelle personali restino separate. Per informazioni dettagliate su Android Enterprise, vedere [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisiti di Android Enterprise).

Per configurare la gestione del profilo di lavoro Android, seguire questa procedura:

1. [Connettere l'account del tenant di Intune all'account Android Enterprise](connect-intune-android-enterprise.md).
2. Configurare la registrazione del profilo di lavoro Android. I profili di lavoro Android sono [supportati solo in alcuni dispositivi Android specifici](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Tutti i dispositivi che supportano i profili di lavoro Android supportano anche la gestione di Android convenzionale. Intune consente di specificare la modalità di gestione dei dispositivi che supportano i profili di lavoro Android nelle [restrizioni di registrazione](enrollment-restrictions-set.md).
    - **Blocca (impostazione predefinita)**: tutti i dispositivi Android, inclusi i dispositivi che supportano i profili di lavoro Android, vengono registrati come dispositivi Android convenzionali.
    - **Consenti**: tutti i dispositivi che supportano i profili di lavoro Android vengono registrati come dispositivi del profilo di lavoro Android. I dispositivi Android che non supportano i profili di lavoro Android vengono registrati come dispositivi Android convenzionali.
3. [Informare gli utenti su come registrare i loro dispositivi](/intune-user-help/enroll-your-device-in-intune-android).


Per registrare nei profili di lavoro Android dispositivi che sono già stati registrati come dispositivi Android convenzionali, è necessario annullare e quindi rieseguire la registrazione dei dispositivi.

Se si stanno registrando dispositivi del profilo di lavoro Android con un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md), è possibile registrare un massimo di 10 dispositivi per ogni account.

Per altre informazioni, vedere [Dati inviati da Intune a Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Approvare l'app Portale aziendale nella versione gestita di Google Play Store

Per garantire che gli utenti abbiano sempre accesso alla versione più aggiornata dell'app Portale aziendale, è necessario approvare l'app Portale aziendale per Android nella versione gestita di Google Play store. In seguito all'approvazione, gli utenti ottengono gli aggiornamenti automatici. Se non viene approvata, l'app Portale aziendale diventerà non aggiornata e potrebbe non ricevere correzioni di bug importanti o nuove funzionalità rilasciate da Microsoft.

Seguire questa procedura per approvare l'app Portale aziendale Intune:

1.  Passare all'app Portale aziendale Intune nella [versione gestita di Google Play Store](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Accedere alla versione gestita di Google Play Store con lo stesso account di Google usato per configurare l'associazione per Android Enterprise.
3.  Fare clic su **Approva** e verrà aperta una nuova finestra di dialogo.
4.  Controllare le autorizzazioni in questa finestra di dialogo e quindi fare clic su **Approva**. Questa operazione è necessaria per consentire queste autorizzazioni allo scopo di consentire all'app Portale aziendale di gestire il profilo di lavoro nel dispositivo.
5.  Selezionare **Keep approved when app requests new permissions** (Mantieni approvazione quando l'app richiede nuove autorizzazioni) e quindi fare clic su **Salva**.

## <a name="next-steps-for-android-work-profiles"></a>Passaggi successivi per i profili di lavoro Android
- [Distribuire app del profilo di lavoro Android](apps-add-android-for-work.md)
- [Aggiungere criteri di configurazione del profilo di lavoro Android](device-profiles.md)
