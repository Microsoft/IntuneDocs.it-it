---
title: Creare un profilo Wi-Fi con una chiave precondivisa
titleSuffix: Azure portal
description: Usare un profilo personalizzato di Intune per creare un profilo Wi-Fi con una chiave precondivisa."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bfcce8d38bc403a13aa28cc762370a7cfaa0bc2d
ms.sourcegitcommit: 1df625330f4e8f7f661b5f2b9f16b5590971838d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2017
---
# <a name="use-a-custom-device-profile-to-create-a-wi-fi-profile-with-a-pre-shared-key"></a>Usare un profilo di dispositivo personalizzato per la creazione di un profilo Wi-Fi con una chiave precondivisa
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Di seguito viene illustrato come usare i **profili di dispositivo personalizzati** di Intune per creare un profilo Wi-Fi con una chiave precondivisa. Questo argomento include anche un esempio di come creare un profilo Wi-Fi basato su EAP.

> [!NOTE]
-   Può risultare più semplice copiare il codice da un computer che si connette alla rete, come descritto di seguito.
- Per Android, è possibile scegliere di usare lo script [Android PSK Generator](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/) fornito da Johnathon Biersack.
-   È possibile aggiungere più reti e chiavi aggiungendo altre impostazioni URI OMA.
-  Per iOS, usare Apple Configurator in una stazione Mac per impostare il profilo. In alternativa, usare lo script [iOS PSK Mobile Config Generator](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/) fornito da Johnathon Biersack.


1.  Per creare un profilo Wi-Fi con una chiave precondivisa per Android o Windows o un profilo Wi-Fi basato su EAP, quando si crea un profilo di dispositivo scegliere **Personalizzato** per la piattaforma del dispositivo anziché un profilo Wi-Fi.

2.  Specificare un nome e una descrizione
3.  Aggiungere una nuova impostazione URI OMA:

   a.   Immettere un nome per questa impostazione di rete Wi-Fi.

   b.   Immettere una descrizione dell'impostazione URI OMA o lasciare il campo vuoto.

   c.   **Tipo di dati**: impostare su **Stringa**.

   d.   **OMA-URI**:

    - **Per Android**: ./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **err Windows**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
Assicurarsi di includere il carattere punto (.) all'inizio.

    SSID è l'identificatore del set di servizi per cui si stanno creando i criteri. Ad esempio `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

  e. **Campo valore** è la posizione in cui si incolla il codice XML. Di seguito è presentato un esempio. Ogni valore deve essere adattato alle impostazioni di rete. Vedere la sezione relativa ai commenti del codice per alcuni puntatori.
4. Scegliere **OK**, salvare e assegnare i criteri.

    > [!NOTE]
    > Questi criteri possono essere assegnati solo a gruppi di utenti.

Alla successiva verifica da parte del dispositivo, verranno applicati i criteri e verrà creato un profilo Wi-Fi nel dispositivo. Il dispositivo sarà in grado di connettersi automaticamente alla rete.

## <a name="android-or-windows-wi-fi-profile"></a>Profilo Wi-Fi Windows o Android

Di seguito è riportato un esempio di codice XML per un profilo Wi-Fi Windows o Android:

> [!IMPORTANT]
>
> `<protected>false</protected>`deve essere impostato su **false**, perché con l'impostazione **true** il dispositivo può aspettarsi una password crittografata e quindi tentare di decrittografarla, con potenziale esito negativo della connessione.
>
>  `<hex>53534944</hex>` deve essere impostato sul valore esadecimale di `<name><SSID of wifi profile></name>`.
>  I dispositivi Windows 10 possono restituire un errore *0x87D1FDE8 Correzione non riuscita* falso, ma verrà comunque eseguito il provisioning con il profilo.

```
<!--
<Name of wifi profile> = Name of profile
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Password to connect to the network
x>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
-->
<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>networkKey</keyType>
        <protected>false</protected>
        <keyMaterial>MyPassword</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## <a name="eap-based-wi-fi-profile"></a>Profilo Wi-Fi basato su EAP
Di seguito è riportato un esempio di codice XML per un profilo Wi-Fi basato su EAP:

```
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
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
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>Creare il file XML da una connessione Wi-Fi esistente
È possibile creare il file XML da una connessione Wi-Fi esistente:
1. In un computer connesso alla rete wireless o che ha eseguito recentemente la connessione a tale rete, aprire la cartella seguente: C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}.

    È consigliabile usare un computer che non si è connesso a molte reti wireless, in quanto sarà necessario eseguire una ricerca in ogni profilo per trovare quella più adatta.
3.     Cercare nei file XML per individuare quello con il nome corretto.
4.     Dopo aver individuato il file XML corretto, copiare e incollare il codice XML nel campo Dati della pagina delle impostazioni URI OMA.

## <a name="best-practices"></a>Procedure consigliate
Prima di distribuire un profilo Wi-Fi con una chiave precondivisa, verificare che il dispositivo possa connettersi direttamente all'endpoint.

Durante la rotazione delle chiavi (password o passphrase), prevedere un tempo di inattività e pianificare di conseguenza le distribuzioni. Considerare di effettuare il push dei nuovi profili Wi-Fi durante ore non lavorative. Avvisare anche gli utenti che la connettività potrebbe essere compromessa.
 
Per garantire una transizione graduale e distribuire tempestivamente gli aggiornamenti dei criteri, è necessario che almeno uno dei canali di comunicazione dei dispositivi rimanga aperto a Intune. A tale scopo, usare la connettività del cellulare oppure prevedere un accesso Wi-Fi guest in modo che gli utenti possano connettersi solo agli endpoint di Intune.


