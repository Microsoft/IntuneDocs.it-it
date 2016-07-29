---
title: Abilitare l'accesso alle risorse aziendali | Microsoft Intune
description: I profili Wi-Fi, VPN e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: ae9b3be57e4008d25f5222025c057fc4211f1119


---

# Abilitare l'accesso alle risorse aziendali con Microsoft Intune
I profili Microsoft Intune Wi-Fi, VPN e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari per svolgere le proprie attività, ovunque si trovino. I profili di certificati consentono di proteggere tale accesso.

## [Profili Wi-Fi](wi-fi-connections-in-microsoft-intune.md) e piattaforme supportate

Distribuire le impostazioni di rete wireless agli utenti. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi alla rete aziendale.
#### Piattaforme supportate

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|Sì (è possibile importare un profilo Wi-Fi Windows)|Sì (è possibile configurare un URI OMA) |sì|Sì|sì|

## [Profili VPN](vpn-connections-in-microsoft-intune.md) e piattaforme supportate
Distribuire le impostazioni di rete privata virtuale (VPN) per gli utenti. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi alle risorse nella rete aziendale.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|Sì|Sì|Sì|Sì|Sì|

## [Profili di posta elettronica](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) e piattaforme supportate
È possibile creare, distribuire e monitorare le impostazioni native di posta elettronica nei dispositivi aziendali.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|No|Sì|Sì|No|Sì|
> [!NOTE]
> [Questo post di blog del team di Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/) offre informazioni su come configurare un profilo Wi-Fi Windows Phone 8.1 usando un URI OMA.

## [Profili di certificati](secure-resource-access-with-certificate-profiles.md) e piattaforme supportate
Consentono di proteggere l'accesso alle risorse aziendali tra cui reti wireless e le connessioni VPN.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|Sì|Sì|Sì|Sì|Sì|



<!--HONumber=Jul16_HO4-->


