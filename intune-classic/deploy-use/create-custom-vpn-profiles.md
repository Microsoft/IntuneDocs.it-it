---
title: Configurazioni personalizzate per i profili VPN di Microsoft Intune
description: Usare configurazioni personalizzate per creare profili VPN in Intune.
keywords: 
author: lleonard-msft
ms.author: alleonar
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
ms.openlocfilehash: d640dd9e80965561e5ddf24c42b5ba4278e49892
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
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

Quindi, [distribuire i criteri](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy) come di consueto.

## <a name="example-uri-settings"></a>Impostazioni URI di esempio

Queste impostazioni possono essere usate per la creazione di una configurazione personalizzata in una VPN di un'azienda fittizia denominata Contoso.
Per dettagli completi su tutte le impostazioni che è possibile usare, vedere [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx) (Provider di servizi di configurazione VPNv2).

**VPN nativa di Contoso (IKEv2):**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

**vpn.contoso.com**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

**Ikev2<br />** ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

**SplitTunnel**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

**Eap**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
``` xml
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
   <EapMethod>
      <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
      <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
      <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
      <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
   </EapMethod>
   <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
      <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
         <Type>13</Type>
         <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
            <CredentialsSource>
               <CertificateStore>
                  <SimpleCertSelection>true</SimpleCertSelection>
               </CertificateStore>
            </CredentialsSource>
            <ServerValidation>
               <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
               <ServerNames></ServerNames>
            </ServerValidation>
            <DifferentUsername>false</DifferentUsername>
            <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </PerformServerValidation>
            <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </AcceptServerName>
         </EapType>
      </Eap>
   </Config>
</EapHostConfig>
```
**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**<br />
True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**<br />
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**<br />
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**<br />
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**<br />
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**<br />
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Per eventuali domande sulle modalità d'uso di queste impostazioni o maggiori dettagli sulle azioni che eseguono, i clienti possono fare riferimento alla [documentazione del provider del servizio di configurazione (CSP)](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx).

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
