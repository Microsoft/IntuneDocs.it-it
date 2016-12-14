---
title: Abilitare l&quot;accesso alle risorse aziendali | Microsoft Intune
description: I profili Wi-Fi, VPN e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: f91c3530599b75093f536fd85eaf21d0b4e86e50


---

# <a name="enable-access-to-company-resources-with-microsoft-intune"></a>Abilitare l'accesso alle risorse aziendali con Microsoft Intune
I profili Microsoft Intune Wi-Fi, VPN e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari, mettendoli in grado di svolgere le loro attività ovunque si trovino. I profili di certificati consentono di proteggere tale accesso.

## <a name="wi-fi-profileswi-fi-connections-in-microsoft-intunemd-and-supported-platforms"></a>[Profili Wi-Fi](wi-fi-connections-in-microsoft-intune.md) e piattaforme supportate

Distribuire le impostazioni di rete wireless agli utenti. Queste impostazioni consentono agli utenti di connettersi facilmente alla rete aziendale.
#### <a name="supported-platforms"></a>Piattaforme supportate

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Sì (è possibile importare un profilo Wi-Fi Windows)|Sì (è possibile configurare un URI OMA) |sì|Sì|sì|

## <a name="vpn-profilesvpn-connections-in-microsoft-intunemd-and-supported-platforms"></a>[Profili VPN](vpn-connections-in-microsoft-intune.md) e piattaforme supportate
Distribuire le impostazioni di rete privata virtuale (VPN) per gli utenti. Queste impostazioni consentono agli utenti di connettersi facilmente alla rete aziendale.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|sì|Sì|Sì|Sì|sì|

## <a name="email-profilesconfigure-access-to-corporate-email-using-email-profiles-with-microsoft-intunemd-and-supported-platforms"></a>[Profili di posta elettronica](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) e piattaforme supportate
È possibile creare, distribuire e monitorare le impostazioni native di posta elettronica nei dispositivi aziendali.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|No|Sì|Sì|No|sì|
> [!NOTE]
> [Questo post di blog del team di Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/) offre informazioni su come configurare un profilo Wi-Fi Windows Phone 8.1 usando un URI OMA.

## <a name="certificate-profilessecure-resource-access-with-certificate-profilesmd-and-supported-platforms"></a>[Profili di certificati](secure-resource-access-with-certificate-profiles.md) e piattaforme supportate
Consentono di proteggere l'accesso alle risorse aziendali tra cui reti wireless e le connessioni VPN.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|sì|Sì|Sì|Sì|sì|



<!--HONumber=Nov16_HO1-->

