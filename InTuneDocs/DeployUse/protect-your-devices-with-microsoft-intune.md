---
# required metadata

title: Proteggere i dispositivi | Microsoft Intune
description:
keywords:
author: Robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteggere i dispositivi con Microsoft Intune
Dopo aver configurato la gestione dei dispositivi con Intune, può essere utile verificare che i dispositivi siano protetti da accessi non autorizzati e da altre minacce. Ecco alcune delle funzionalità di Intune che consentono di eseguire questa verifica.

> [!TIP]
> Questo argomento non descrive tutte le modalità in cui Intune può contribuire a proteggere i dispositivi. Ad esempio, è possibile usare i criteri di Intune per configurare molte impostazioni di sicurezza per i dispositivi, ad esempio la configurazione delle password, le impostazioni di crittografia e le funzionalità hardware come il Bluetooth e la fotocamera del dispositivo. Per altre informazioni su queste impostazioni, vedere l'articolo relativo alla [gestione delle impostazioni e delle funzionalità nei dispositivi con Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

## Reimpostare i passcode quando gli utenti vengono bloccati dai dispositivi
Poiché il primo passaggio nella protezione dei dati aziendali nei dispositivi mobili prevede l'uso di un passcode per usare il dispositivo, a volte è necessario [reimpostare un passcode](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) o aiutare un utente a farlo rimuovendo il passcode o impostando in remoto un passcode temporaneo. È anche possibile [bloccare un dispositivo in remoto](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) se viene smarrito o rubato.

## Aggiungere un ulteriore livello di protezione ai dispositivi Windows
[Multi-Factor Authentication (MFA)](protect-windows-devices-with-multi-factor-authentication.md) costituisce un modo più sicuro per autenticare gli utenti di dispositivi Windows e Windows Phone in rete.  Con MFA, oltre inserire nome utente e password, gli utenti devono infatti confermare la propria identità tramite una telefonata o un SMS.

## Controllare le impostazioni di Microsoft Passport nei dispositivi Windows
Con Intune è possibile eseguire l'integrazione con [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), un metodo di accesso alternativo per Windows 10 e versioni successive che usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale.

## Proteggere i PC Windows gestiti con il client di Intune
Intune continua a supportare i criteri di sicurezza per i PC Windows non registrati ma gestiti con il software per client computer di Intune. Per scoprire come questi criteri aiutano a proteggere i PC Windows, vedere l'articolo [Usare i criteri per proteggere i PC Windows che eseguono il software client di Intune](policies-to-protect-windows-pcs-in-microsoft-intune.md).


<!--HONumber=May16_HO2-->


