---
title: Configurazioni personalizzate per i profili VPN di Microsoft Intune | Documentazione Microsoft
description: Usare configurazioni personalizzate per creare profili VPN in Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 260c328d37174c94bde37162ec011aded26a9f72
ms.lasthandoff: 04/14/2017


---

# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Configurazioni personalizzate per i profili VPN di Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>Creare una configurazione personalizzata
È possibile usare configurazioni personalizzate di Intune per creare profili VPN per:

* Dispositivi che eseguono Android 4 e versioni successive
* Dispositivi Android for Work
* Dispositivi registrati che eseguono Windows 8.1 e versioni successive
* Dispositivi che eseguono Windows Phone 8.1 e versioni successive
* Dispositivi registrati che eseguono Windows 10 Desktop
* Dispositivi che eseguono Windows 10 Mobile

Questo tipo di criteri può essere utile quando i criteri VPN Intune standard non includono le impostazioni che si vuole usare.

## <a name="to-create-a-custom-configuration-policy"></a>Per creare criteri di configurazione personalizzati:

   1. Nella [console di amministrazione di Intune](https://manage.microsoft.com) scegliere **Criteri** > **Aggiungi criterio** > *espandere la piattaforma* > **Configurazione personalizzata** > **Crea criterio**.
   2. Immettere un nome per il criterio.
   3. Per ogni impostazione URI da specificare scegliere **Aggiungi** e specificare le informazioni richieste. Ad esempio:

   ![Finestra di dialogo Configurazione personalizzata per il profilo VPN](./media/Intune_Add_VPN_URI.png)

   4.  Dopo aver immesso tutte le impostazioni URI, scegliere **Salva criterio** e quindi distribuire i criteri.

Quindi, [distribuire i criteri](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy) come di consueto.

## <a name="example-uri-settings"></a>Impostazioni URI di esempio

Queste impostazioni possono essere usate per la creazione di una configurazione personalizzata in una VPN di un'azienda fittizia denominata Contoso.
Per dettagli completi su tutte le impostazioni che è possibile usare, vedere [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx) (Provider di servizi di configurazione VPNv2).

VPN nativa di Contoso (IKEv2): ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn** true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Per eventuali domande su come usare queste impostazioni o per altre informazioni sul loro funzionamento, i clienti possono fare riferimento alla documentazione del provider del servizio di configurazione (CSP, Configuration Service Provider): https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx.

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>Impostazioni URI per VPN Android per singole app in PulseSecure
### <a name="custom-uri-for-package-list"></a>URI PERSONALIZZATO PER L'ELENCO PACCHETTI
-  Tipo di dati = stringa
-  URI OMA = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  Valore = elenco di pacchetti separati da delimitatore.
   - Delimitatori: punto e virgola (;), due punti (:), virgola (,), barra verticale (|)

Esempi:
- com.Android.Chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>URI PERSONALIZZATO PER LA MODALITÀ (FACOLTATIVO)
- Tipo di dati = stringa
- URI OMA = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> Note
> - Usare lo stesso *nome* assegnato al profilo personalizzato
> - Valori possibili: *GLOBAL*, *WHITELIST*, *BLACKLIST*
> - Se non è specificato un elenco pacchetti, assume l'impostazione *GLOBAL* (compatibilità con le versioni precedenti con profili validi per l'intero sistema).
> - Se è specificato un elenco pacchetti, assume l'impostazione *WHITELIST*.


### <a name="see-also"></a>Vedere anche
[Connessioni VPN in Microsoft Intune](vpn-connections-in-microsoft-intune.md)

