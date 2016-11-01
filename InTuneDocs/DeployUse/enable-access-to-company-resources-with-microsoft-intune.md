---
title: Abilitare l&quot;accesso alle risorse aziendali | Microsoft Intune
description: I profili Wi-Fi, VPN e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7b4acce1b1861ca2c2d1432b0258ad1e95e46d2a
ms.openlocfilehash: 2959ad5f09be686e4dae9b751e8ede5e6b60bd89


---

# <a name="enable-access-to-company-resources-with-microsoft-intune"></a>Abilitare l'accesso alle risorse aziendali con Microsoft Intune
I profili Microsoft Intune Wi-Fi, VPN e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari, mettendoli in grado di svolgere le loro attività ovunque si trovino. I profili di certificati consentono di proteggere tale accesso.

## <a name="wifi-profileswificonnectionsinmicrosoftintunemd-and-supported-platforms"></a>[Profili Wi-Fi](wi-fi-connections-in-microsoft-intune.md) e piattaforme supportate

Distribuire le impostazioni di rete wireless agli utenti. Queste impostazioni consentono agli utenti di connettersi facilmente alla rete aziendale.
#### <a name="supported-platforms"></a>Piattaforme supportate

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|Sì (è possibile importare un profilo Wi-Fi Windows)|Sì (è possibile configurare un URI OMA) |sì|Sì|sì|

## <a name="vpn-profilesvpnconnectionsinmicrosoftintunemd-and-supported-platforms"></a>[Profili VPN](vpn-connections-in-microsoft-intune.md) e piattaforme supportate
Distribuire le impostazioni di rete privata virtuale (VPN) per gli utenti. Queste impostazioni consentono agli utenti di connettersi facilmente alla rete aziendale.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|sì|Sì|Sì|Sì|sì|

## <a name="email-profilesconfigureaccesstocorporateemailusingemailprofileswithmicrosoftintunemd-and-supported-platforms"></a>[Profili di posta elettronica](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) e piattaforme supportate
È possibile creare, distribuire e monitorare le impostazioni native di posta elettronica nei dispositivi aziendali.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|No|Sì|Sì|No|sì|
> [!NOTE]
> [Questo post di blog del team di Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/) offre informazioni su come configurare un profilo Wi-Fi Windows Phone 8.1 usando un URI OMA.

## <a name="certificate-profilessecureresourceaccesswithcertificateprofilesmd-and-supported-platforms"></a>[Profili di certificati](secure-resource-access-with-certificate-profiles.md) e piattaforme supportate
Consentono di proteggere l'accesso alle risorse aziendali tra cui reti wireless e le connessioni VPN.

|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|sì|Sì|Sì|Sì|sì|



<!--HONumber=Oct16_HO2-->


