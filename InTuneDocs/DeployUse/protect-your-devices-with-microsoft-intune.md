---
title: Proteggere i dispositivi | Microsoft Intune
description: Informazioni su alcuni dei metodi che consentono a Intune di proteggere i dispositivi da accessi non autorizzati e altre minacce.
keywords: 
author: Robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c999a852b68762002ac94269e27ecbf46c8f9999
ms.openlocfilehash: 3318590eaedc6f0e96fb463dc016d5786eeb38fb


---

# Proteggere i dispositivi con Microsoft Intune
Dopo aver configurato la gestione dei dispositivi con Intune, può essere utile verificare che i dispositivi siano protetti da accessi non autorizzati e da altre minacce. Ecco alcune delle funzionalità di Intune che consentono di eseguire questa verifica.

> [!TIP]
> Questo argomento non descrive tutte le modalità con cui Intune può contribuire a proteggere i dispositivi. Ad esempio, è possibile usare i criteri di Intune per configurare molte impostazioni di sicurezza per i dispositivi, ad esempio le password, le impostazioni di crittografia e le funzionalità hardware come il Bluetooth e la fotocamera del dispositivo. Per altre informazioni su queste impostazioni, vedere l'articolo relativo alla [gestione delle impostazioni e delle funzionalità nei dispositivi con Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

## Reimpostare i passcode quando gli utenti vengono bloccati dai dispositivi
Il primo passaggio per la protezione dei dati aziendali nei dispositivi mobili prevede l'impostazione di un passcode per usare il dispositivo. A volte è necessario [reimpostare un passcode](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) o aiutare un dipendente a reimpostarlo, eliminando il passcode o impostando un passcode temporaneo in remoto. È anche possibile [bloccare un dispositivo in remoto](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) se viene smarrito o rubato.

## Aggiungere un ulteriore livello di protezione ai dispositivi Windows
[Multi-Factor Authentication (MFA)](protect-windows-devices-with-multi-factor-authentication.md) costituisce un modo più sicuro per autenticare gli utenti di dispositivi Windows e Windows Phone in rete. Con MFA, oltre inserire nome utente e password, gli utenti devono confermare la propria identità con una telefonata o un SMS.

## Controllare le impostazioni di Microsoft Passport nei dispositivi Windows
Intune si integra con [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), un metodo di accesso alternativo per Windows 10 e versioni successive. Microsoft Passport for Work usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale.

## Eseguire il bypass del blocco attivazione su dispositivi iOS
Il blocco attivazione è una funzionalità che consente di proteggere i dispositivi degli utenti richiedendo l'ID Apple e la password prima di qualsiasi operazione di cancellazione o riattivazione del dispositivo. Questa procedura, tuttavia, può causare problemi, ad esempio se l'utente lascia l'azienda senza rimuovere il blocco. [Il bypass del blocco attivazione iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) consente di rimuovere il blocco dai dispositivi iOS supervisionati per poterli riallocare o per cancellarne il contenuto.

## Proteggere i PC Windows gestiti con il client di Intune
Intune continua a supportare i criteri di sicurezza per i PC Windows non registrati ma gestiti con il software client per i computer di Intune. Per scoprire come questi criteri aiutano a proteggere i PC Windows, vedere l'articolo [Usare i criteri per proteggere i PC Windows che eseguono il software client di Intune](policies-to-protect-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Aug16_HO2-->


