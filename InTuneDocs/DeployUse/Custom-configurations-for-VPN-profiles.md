---
title: Configurazioni personalizzate per i profili VPN | Microsoft Intune
description: Usare configurazioni personalizzate per creare profili VPN in Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fb3b6cccaa3e62be3a7271ae6a67e76f8cf8d858
ms.openlocfilehash: a1c7648a4ee4ab91e00f5305a8124a07570824fc


---

# <a name="custom-configurations-for-vpn-profiles"></a>Configurazioni personalizzate per i profili VPN

## <a name="create-a-custom-configuration"></a>Creare una configurazione personalizzata
È possibile usare configurazioni personalizzate per creare profili VPN in Intune per:

* Dispositivi che eseguono Android 4 e versioni successive
* Dispositivi Android for Work
* Dispositivi registrati che eseguono Windows 8.1 e versioni successive
* Dispositivi che eseguono Windows Phone 8.1 e versioni successive
* Dispositivi che eseguono Windows 10 Desktop e Mobile

Per creare una configurazione personalizzata:

   1. Nella console di amministrazione di Intune scegliere **Criteri** > **Aggiungi criterio** > *espandere la piattaforma* > **Configurazione personalizzata** > **Crea criterio**.
   2. Specificare un nome per il criterio.
   3. Per ogni impostazione URI scegliere **Aggiungi** e specificare le informazioni richieste. Ad esempio:

   ![Finestra di dialogo Configurazione personalizzata per il profilo VPN](./media/Intune_Add_VPN_URI.png)

   4.  Dopo aver immesso tutte le impostazioni URI, scegliere **Salva criterio** e quindi distribuire i criteri.

## <a name="deploy-a-configuration-policy"></a>Distribuire un criterio di configurazione

1.  Nell'area di lavoro **Criteri** scegliere il criterio che si vuole distribuire e quindi fare clic su **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   **Per distribuire il criterio**: scegliere uno o più gruppi a cui si vuole distribuire il criterio e quindi fare clic su **Aggiungi** &gt; **OK**.

    -   **Per chiudere la finestra di dialogo senza distribuirlo**, scegliere **Annulla**.

Quando si sceglie un criterio distribuito, è possibile visualizzare altre informazioni sulla distribuzione nella parte inferiore dell'elenco dei criteri.

##<a name="example-of-uri-settings-for-a-custom-vpn-profile-configuration"></a>Esempio di impostazioni URI per la configurazione personalizzata di un profilo VPN
Di seguito sono riportate voci di esempio per valori URI, per la creazione di una configurazione personalizzata in una VPN di un'azienda fittizia denominata Contoso. Per altre informazioni, quali il tipo di dati per ogni voce, vedere [CSP (Configuration Service Provider) VPNv2](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx).

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

Per eventuali domande su come usare queste impostazioni o per altre informazioni sulla loro funzione, i clienti possono fare riferimento alla documentazione CSP (Configuration Service Provider): https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx.

## <a name="uri-settings-for-android-perapp-vpn-on-pulsesecure"></a>Impostazioni URI per VPN Android per singole app in PulseSecure
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
(Connessioni VPN in Microsoft Intune)[vpn-connections-in-microsoft-intune.md]



<!--HONumber=Nov16_HO1-->


