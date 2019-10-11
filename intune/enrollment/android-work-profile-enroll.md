---
title: Registrare i dispositivi con profilo di lavoro Android Enterprise in Intune
titleSuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi con profilo di lavoro Android Enterprise in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c447b6b21021573d95a5ece3297e548f216b7a0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723528"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Configurare la registrazione dei dispositivi con profilo di lavoro Android Enterprise

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune consente di distribuire app e impostazioni nei dispositivi con profilo di lavoro Android Enterprise per assicurarsi che le informazioni di lavoro e quelle personali restino separate. Per informazioni dettagliate su Android Enterprise, vedere [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisiti di Android Enterprise).

Per configurare la gestione del profilo di lavoro Android Enterprise, seguire questa procedura:

1. [Connettere l'account del tenant di Intune all'account Android Enterprise](connect-intune-android-enterprise.md).
2. Specificare le impostazioni di registrazione del profilo di lavoro Android Enterprise. I profili di lavoro Android Enterprise sono [supportati solo in alcuni dispositivi Android specifici](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). I dispositivi che supportano i profili di lavoro Android Enterprise supportano anche la gestione amministratori dei dispositivi Android. Intune consente di specificare la modalità di gestione dei dispositivi che supportano i profili di lavoro Android Enterprise in [Restrizioni registrazione](enrollment-restrictions-set.md).
    - **Blocca**:  tutti i dispositivi Android, inclusi i dispositivi che supportano i profili di lavoro Android Enterprise, verranno registrati come dispositivi di tipo amministratore di dispositivi Android, a meno che non sia bloccata anche la registrazione di tipo amministratore di dispositivi Android. 
    - **Consenti (impostazione predefinita)**: tutti i dispositivi che supportano i profili di lavoro Android Enterprise vengono registrati come dispositivi con profilo di lavoro Android Enterprise. Tutti i dispositivi Android che non supportano i profili di lavoro Android Enterprise vengono registrati come dispositivi di tipo amministratore di dispositivi Android, a meno che non sia bloccata la registrazione di tipo amministratore di dispositivi Android. 
> [!NOTE]
> A partire da luglio 2019 per i nuovi tenant l'impostazione predefinita è **Consenti**. Per tutti i tenant precedenti non verranno apportate modifiche alle restrizioni di registrazione e verranno visualizzati i criteri impostati nelle restrizioni di registrazione. Per i tenant precedenti per cui non sono mai state apportate modifiche alle restrizioni di registrazione, l'impostazione predefinita rimane **Blocca** per i profili di lavoro Android Enterprise.

3. [Informare gli utenti su come registrare i loro dispositivi](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android).  

Se si vogliono registrare dispositivi che usano profili di lavoro Android Enterprise ma che sono già stati registrati come dispositivi di tipo amministratore di dispositivi Android, è necessario annullare e quindi rieseguire la registrazione.
> [!NOTE]
> L'amministratore può eseguire questa operazione in remoto usando la funzione **Ritira**. Questa funzione è disponibile nel menu azioni dopo aver selezionato il dispositivo dal pannello **Tutti i dispositivi**.

Se si stanno registrando dispositivi con profilo di lavoro Android Enterprise usando un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md), è possibile registrare un massimo di 10 dispositivi per ogni account.

Per altre informazioni, vedere [Dati inviati da Intune a Google](../protect/data-intune-sends-to-google.md).

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Passaggi successivi per i profili di lavoro Android Enterprise
- [Aggiungere app di Google Play gestite a dispositivi Android Enterprise con Intune](../apps/apps-add-android-for-work.md)
- [Applicare le impostazioni delle funzionalità nei dispositivi usando i profili dei dispositivi in Microsoft Intune](../configuration/device-profiles.md)

## <a name="see-also"></a>Vedere anche

[Configurazione e risoluzione dei problemi dei dispositivi Android Enterprise in Microsoft Intune](https://support.microsoft.com/help/4476974)
