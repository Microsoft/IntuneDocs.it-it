---
title: Registrazione di tipo amministratore di dispositivi Android in Microsoft Intune
titleSuffix: ''
description: Registrare dispositivi Android in Intune tramite la registrazione di tipo amministratore di dispositivi.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
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
ms.openlocfilehash: ebeb5830136ad6dae19babbc8ecf45c1d6e5c36c
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885964"
---
# <a name="android-device-administrator-enrollment"></a>Registrazione di tipo amministratore di dispositivi Android

Amministratore di dispositivi Android, a volte denominata gestione Android "legacy" e resa disponibile con Android 2.2, indica una modalità di gestione dei dispositivi Android. Funzionalità di gestione migliorate, tuttavia, sono ora disponibili in [Android Enterprise](https://www.android.com/enterprise/management/) (con la versione Android 5.0). Con l'obiettivo di passare a una gestione dei dispositivi moderna, più ricca e sicura, Google sta riducendo il supporto per l'amministratore di dispositivi nelle nuove versioni di Android.

Pertanto, al fine di evitare questa riduzione di funzionalità, non è consigliabile registrare nuovi dispositivi tramite il processo di amministratore di dispositivi descritto di seguito.

Per gli stessi motivi, è anche consigliabile eseguire la migrazione dei dispositivi dalla gestione di tipo amministratore di dispositivi se questi verranno aggiornati ad Android 10. 

Per altre informazioni sul supporto di Intune per il supporto di amministratore di dispositivi Android, vedere la [sezione Notifiche](../fundamentals/whats-new.md#decreasing-support-for-android-device-administrator).

Se si decide che gli utenti possano comunque registrare i propri dispositivi Android con la gestione di tipo amministratore di dispositivi, passare alla sezione successiva.  

Per altre informazioni sulle funzionalità di Android Enterprise di Google, vedere questi articoli:
- [Indicazioni di Google per la migrazione da amministratore di dispositivi ad Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentazione di Google sul piano per deprecare l'API amministratore di dispositivi](https://developers.google.com/android/work/device-admin-deprecation)


## <a name="set-up-device-administrator-enrollment"></a>Configurare la registrazione di tipo amministratore di dispositivi

1. Per preparare la gestione dei dispositivi mobili è necessario impostare l'autorità per la gestione dei dispositivi mobili su **Microsoft Intune**. Vedere [Impostare l'autorità MDM](../fundamentals/mdm-authority-set.md) per le istruzioni. Questo elemento viene impostato una sola volta quando si configura Intune per la gestione dei dispositivi mobili per la prima volta.
2. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e scegliere > **Dispositivi** > **Android** > **Registrazione Android** > **Dispositivi personali e di proprietà aziendale con privilegi di amministratore di dispositivi** > **Usa l'amministratore di dispositivi per gestire i dispositivi**.
3. [Informare gli utenti su come registrare i loro dispositivi](/intune-user-help/enroll-your-device-in-intune-android).  

Dopo che un utente ha eseguito la registrazione, è possibile iniziare a gestirne i dispositivi in Intune con attività quali, ad esempio, [l'assegnazione dei criteri di conformità](../protect/compliance-policy-create-android.md), [la gestione delle app](../apps/app-management.md) e così via.

Per informazioni su altre attività dell'utente, vedere gli articoli seguenti:
- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](../fundamentals/end-user-educate.md)
- [Uso del dispositivo Android con Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>Bloccare la registrazione di tipo amministratore di dispositivi
Per bloccare la registrazione dei dispositivi di tipo amministratore di dispositivi Android o soltanto quelli di proprietà personale, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md).



## <a name="next-steps"></a>Passaggi successivi
- [Assegnare criteri di conformità](../protect/compliance-policy-create-android.md)
- [Gestione delle app](../apps/app-management.md)
