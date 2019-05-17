---
title: Registrare i dispositivi con profilo di lavoro Android Enterprise in Intune
titleSuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi con profilo di lavoro Android Enterprise in Intune.
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
ms.openlocfilehash: 66574fe66f90b73d8ebf5835c5b16e93276579e4
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568219"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Configurare la registrazione dei dispositivi con profilo di lavoro Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune consente la distribuzione di app e impostazioni ai dispositivi con profilo di lavoro Android Enterprise per assicurare che le informazioni di lavoro e quelle personali restino separate. Per informazioni dettagliate su Android Enterprise, vedere [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisiti di Android Enterprise).

Per configurare la gestione del profilo di lavoro Android Enterprise, seguire questa procedura:

1. [Connettere l'account del tenant di Intune all'account Android Enterprise](connect-intune-android-enterprise.md).
2. Specificare le impostazioni di registrazione del profilo di lavoro Android Enterprise. I profili di lavoro Android Enterprise sono [supportati solo in alcuni dispositivi Android specifici](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). I dispositivi che supportano i profili di lavoro Android Enterprise supportano anche la gestione di Android convenzionale. Intune consente di specificare la modalità di gestione dei dispositivi che supportano i profili di lavoro Android Enterprise in [Restrizioni registrazione](enrollment-restrictions-set.md).
    - **Blocca (impostazione predefinita)**:  tutti i dispositivi Android, inclusi quelli che supportano i profili di lavoro Android Enterprise, vengono registrati come dispositivi Android convenzionali.
    - **Consenti**: tutti i dispositivi che supportano i profili di lavoro Android Enterprise vengono registrati come dispositivi con profilo di lavoro Android Enterprise. I dispositivi Android che non supportano i profili di lavoro Android Enterprise vengono registrati come dispositivi Android convenzionali.
3. [Informare gli utenti su come registrare i loro dispositivi](/intune-user-help/enroll-your-device-in-intune-android).


Se si vogliono registrare dispositivi che usano profili di lavoro Android Enterprise ma che sono già stati registrati come dispositivi Android convenzionali, è necessario annullare e quindi rieseguire la registrazione di tali dispositivi.

Se si stanno registrando dispositivi con profilo di lavoro Android Enterprise usando un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md), è possibile registrare un massimo di 10 dispositivi per ogni account.

Per altre informazioni, vedere [Dati inviati da Intune a Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Approvare l'app Portale aziendale in Google Play Store gestito

Per garantire che gli utenti abbiano sempre accesso alla versione più aggiornata dell'app Portale aziendale, è necessario approvare l'app Portale aziendale per Android in Google Play Store gestito. In seguito all'approvazione, gli utenti ottengono gli aggiornamenti automatici. Se non viene approvata, l'app Portale aziendale diventerà non aggiornata e potrebbe non ricevere correzioni di bug importanti o nuove funzionalità rilasciate da Microsoft.

Seguire questa procedura per approvare l'app Portale aziendale Intune:

1.  Passare all'app Portale aziendale in [Google Play Store gestito](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Accedere a Google Play Store gestito con lo stesso account di Google usato per configurare il binding per Android Enterprise.
3.  Fare clic su **Approva** e verrà aperta una nuova finestra di dialogo.
4.  Controllare le autorizzazioni in questa finestra di dialogo e quindi fare clic su **Approva**. Questa operazione è necessaria per consentire queste autorizzazioni allo scopo di consentire all'app Portale aziendale di gestire il profilo di lavoro nel dispositivo.
5.  Selezionare **Keep approved when app requests new permissions** (Mantieni approvazione quando l'app richiede nuove autorizzazioni) e quindi fare clic su **Salva**.

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Passaggi successivi per i profili di lavoro Android Enterprise
- [Aggiungere app di Google Play gestite a dispositivi Android Enterprise con Intune](apps-add-android-for-work.md)
- [Applicare le impostazioni delle funzionalità nei dispositivi usando i profili dei dispositivi in Microsoft Intune](device-profiles.md)
