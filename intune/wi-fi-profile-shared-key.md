---
title: Creare un profilo Wi-Fi con chiave precondivisa - Microsoft Intune - Azure | Micrososft Docs
description: Usare un profilo personalizzato per creare un profilo Wi-Fi con una chiave precondivisa e ottenere il codice XML di esempio per i profili Wi-Fi basati su Android, Windows ed EAP in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 59736ad188cf88c994ff93b4a505731afad8f550
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186325"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key---intune"></a>Usare un profilo di dispositivo personalizzato per la creazione di un profilo Wi-Fi con una chiave precondivisa - Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le chiavi precondivise (PSK) vengono in genere usate per autenticare gli utenti in reti Wi-Fi o in reti LAN wireless. Con Intune è possibile creare un profilo Wi-Fi con una chiave precondivisa. Per creare il profilo, usare la funzionalità per i **profili di dispositivo personalizzati** all'interno di Intune. Questo articolo include anche alcuni esempi di come creare un profilo Wi-Fi basato su EAP.

> [!IMPORTANT]
>- L'uso di una chiave precondivisa con Windows 10 determina la visualizzazione di un errore di correzione in Intune. Quando ciò accade, il profilo Wi-Fi viene assegnato correttamente al dispositivo e il profilo funziona come previsto.
>- Se si esporta un profilo Wi-Fi che include una chiave precondivisa, verificare che il file sia protetto. La chiave è in testo normale ed è quindi necessario proteggerla.

## <a name="before-you-begin"></a>Prima di iniziare

- Può risultare più semplice copiare il codice da un computer che si connette alla rete, come descritto di seguito in questo articolo.
- Per Android, è anche possibile usare [Android PSK Generator](http://intunepskgenerator.johnathonb.com/).
- È possibile aggiungere più reti e chiavi aggiungendo altre impostazioni URI OMA.
- Per iOS, usare Apple Configurator in una stazione Mac per impostare il profilo. In alternativa, usare [iOS PSK Mobile Config Generator](http://intunepskgenerator.johnathonb.com/).
- PSK richiede una stringa di 64 cifre esadecimali o una passphrase tra gli 8 e i 63 caratteri ASCII stampabili. Alcuni caratteri, ad esempio asterisco (*), non sono supportati.

## <a name="create-a-custom-profile"></a>Creare un profilo personalizzato
È possibile creare un profilo personalizzato con una chiave precondivisa per Android, Windows o un profilo Wi-Fi basato su EAP. Per creare il profilo mediante il portale di Azure, vedere [Come configurare le impostazioni dispositivo personalizzate in Microsoft Intune](custom-settings-configure.md). Quando si crea il profilo di dispositivo, scegliere **Personalizzato** per la piattaforma del dispositivo. Non selezionare il profilo Wi-Fi. Quando si sceglie Personalizzato, assicurarsi di: 

1. Immettere un nome e una descrizione del profilo.
2. Aggiungere una nuova impostazione URI OMA con le proprietà seguenti: 

   a. Immettere un nome per questa impostazione di rete Wi-Fi.

   b. (Facoltativo) Immettere una descrizione dell'impostazione URI OMA o lasciare il campo vuoto.

   c. Impostare **Tipo di dati** su **String**.

   d. **OMA-URI**:

   - **Per Android**: ./Vendor/MSFT/WiFi/Profile/SSID/Settings
   - **Per Windows**: ./Vendor/MSFT/WiFi/Profile/SSID/WlanXml

     > [!NOTE]
     > Assicurarsi di includere il carattere punto (.) all'inizio.

     SSID è l'identificatore del set di servizi per cui si stanno creando i criteri. Immettere ad esempio `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

   e. **Campo valore** è la posizione in cui si incolla il codice XML. Vedere gli esempi in questo articolo. Aggiornare ogni valore in modo corrispondente alle impostazioni di rete. La sezione relativa ai commenti del codice include alcuni puntatori.
3. Selezionare **OK**, salvare e assegnare i criteri.

    > [!NOTE]
    > Questi criteri possono essere assegnati solo a gruppi di utenti.

Alla successiva verifica da parte del dispositivo, vengono applicati i criteri e viene creato un profilo Wi-Fi nel dispositivo. Il dispositivo può quindi connettersi automaticamente alla rete.

## <a name="android-or-windows-wi-fi-profile-example"></a>Esempio di profilo Wi-Fi Android o Windows

L'esempio seguente include il codice XML per un profilo Wi-Fi Android o Windows. L'esempio è fornito per mostrare il formato corretto e fornire altri dettagli. È solo un esempio e non è da intendersi come configurazione consigliata per l'ambiente.

> [!IMPORTANT]
>
> `<protected>false</protected>` deve essere impostato su **false**. Se **true**, il dispositivo potrebbe aspettarsi una password crittografata e quindi tentare di decrittografarla, con potenziale esito negativo della connessione.
>
>  `<hex>53534944</hex>` deve essere impostato sul valore esadecimale di `<name><SSID of wifi profile></name>`.
>  I dispositivi Windows 10 possono restituire un errore *0x87D1FDE8 Correzione non riuscita* falso, ma il dispositivo contiene comunque il profilo.

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

## <a name="eap-based-wi-fi-profile-example"></a>Esempio di profilo Wi-Fi basato su EAP
L'esempio seguente include il codice XML per un profilo Wi-Fi basato su EAP: l'esempio è fornito per mostrare il formato corretto e fornire altri dettagli. È solo un esempio e non è da intendersi come configurazione consigliata per l'ambiente.


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
È possibile creare un file XML da una connessione Wi-Fi esistente seguendo questa procedura: 

1. In un computer connesso alla rete wireless, o connesso di recente alla rete, aprire la cartella `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}`.

   È consigliabile usare un computer che non si è connesso a molte reti wireless. In caso contrario, può essere necessario esaminare ogni profilo per trovare quello corretto.

2. Eseguire una ricerca nei file XML per individuare quello con il nome corretto.
3. Dopo aver individuato il file XML corretto, copiare e incollare il codice XML nel campo **Dati** della pagina delle impostazioni URI OMA.

## <a name="best-practices"></a>Procedure consigliate
- Prima di distribuire un profilo Wi-Fi con una chiave precondivisa, verificare che il dispositivo possa connettersi direttamente all'endpoint.

- Durante la rotazione delle chiavi (password o passphrase), prevedere un tempo di inattività e pianificare di conseguenza le distribuzioni. Considerare di effettuare il push dei nuovi profili Wi-Fi durante ore non lavorative. Avvisare anche gli utenti che la connettività potrebbe essere compromessa.

- Per garantire una transizione senza problemi, verificare che il dispositivo dell'utente disponga di una connessione a Internet alternativa. Ad esempio, l'utente deve essere in grado di tornare al Wi-Fi guest (o a un'altra rete Wi-Fi) o avere connettività cellulare per la comunicazione con Intune. Questa connessione alternativa consente all'utente di ricevere gli aggiornamenti dei criteri quando viene aggiornato il profilo Wi-Fi aziendale nel dispositivo.
