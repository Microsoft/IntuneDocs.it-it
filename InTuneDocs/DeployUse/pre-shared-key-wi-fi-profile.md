---
title: Wi-Fi tramite PSK | Microsoft Intune
description: Usare la configurazione personalizzata per creare un profilo Wi-Fi con una chiave precondivisa.
keywords: 
author: nbigman
manager: Arob98
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e977c7c7-e204-47a6-b851-7ad7673ceaab
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 72288296d966b9b9fae4fd721b4460528213f626
ms.openlocfilehash: afdd0c3569c0c294a9bef47755de2d9e77e7507d



---
# Creare un profilo Wi-Fi con una chiave precondivisa
Di seguito viene illustrato come usare la **configurazione personalizzata** di Intune per creare un profilo Wi-Fi con una chiave precondivisa. Questo argomento include anche un esempio di come creare un profilo Wi-Fi basato su EAP.

Nota:
-   Può risultare più semplice copiare il codice da un computer che si connette alla rete, come descritto di seguito.
- Per Android, è possibile scegliere di usare lo script [Android PSK Generator](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/) fornito da Johnathon Biersack.
-   È possibile aggiungere più reti e chiavi aggiungendo altre impostazioni URI OMA.
-  Per iOS, usare lo strumento Apple Configurator in una stazione Mac per configurare il profilo. In alternativa, usare lo script [iOS PSK Mobile Config Generator](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/) fornito da Johnathon Biersack.


1.  Per creare un profilo Wi-Fi con una chiave precondivisa per Android o Windows o un profilo Wi-Fi basato su EAP, quando si crea un criterio scegliere **Configurazione personalizzata** per tale piattaforma del dispositivo, anziché un profilo Wi-Fi.

2.  Specificare un nome e una descrizione
3.  Aggiungere una nuova impostazione URI OMA:

   a.   Immettere un nome per questa impostazione di rete Wi-Fi.

   b.   Immettere una descrizione dell'impostazione URI OMA o lasciare il campo vuoto.

   c.   **Tipo di dati**: impostare su "String(XML)"

   d.   **URI OMA**: ./Vendor/MSFT/Wi-Fi /Profile/<SSID>/Settings

Nota: assicurarsi di includere il carattere punto (.) all'inizio.

SSID è l'identificatore del set di servizi per cui si stanno creando i criteri. Ad esempio:
`./Vendor/MSFT/Wi-Fi/Profile/Hotspot-1/Settings`

  e.    Campo del valore: posizione in cui si incolla il codice XML. Di seguito è presentato un esempio. Ogni valore deve essere adattato alle impostazioni di rete. Vedere la sezione relativa ai commenti del codice per alcuni puntatori.


    <!--
    <Name of wifi profile> = Name of profile
    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
    <nonBroadcast><true/false></nonBroadcast>
    <Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
    <Type of encryption> = Type of encryption used by the network
    <protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
    <password> = Password to connect to the network
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

## Profilo Wi-Fi basato su EAP
Di seguito è riportato un esempio di codice XML per un profilo Wi-Fi basato su EAP:

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

4.  Fare clic su OK, quindi salvare e distribuire il criterio.
NOTA: questo criterio può essere distribuito solo ai gruppi di utenti.

Alla successiva verifica da parte del dispositivo, verranno applicati i criteri e verrà creato un profilo Wi-Fi nel dispositivo. Il dispositivo sarà in grado di connettersi automaticamente alla rete.
## Creare il file XML da una connessione Wi-Fi esistente
È possibile creare il file XML da una connessione Wi-Fi esistente:
1.     In un computer connesso alla rete wireless o che ha eseguito recentemente la connessione a tale rete, aprire la cartella seguente: C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}. È consigliabile usare un computer che non si è connesso a molte reti wireless, in quanto sarà necessario eseguire una ricerca in ogni profilo per trovare quella più adatta.
3.     Cercare nei file XML per individuare quello con il nome corretto.
4.     Dopo aver individuato il file XML corretto, copiare e incollare il codice XML nel campo Dati della pagina delle impostazioni URI OMA.

## Distribuire i criteri

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire, quindi fare clic su **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   **Per distribuire il criterio**: selezionare uno o più gruppi in cui si vuole distribuire il criterio, quindi fare clic su **Aggiungi** &gt; **OK**.

    -   **Per chiudere la finestra di dialogo senza distribuire il criterio**, fare clic su **Annulla**.

Quando si seleziona un criterio distribuito, è possibile visualizzare altre informazioni sulla distribuzione nella parte inferiore dell'elenco di criteri.

### Vedere anche
[Connessioni Wi-Fi in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


