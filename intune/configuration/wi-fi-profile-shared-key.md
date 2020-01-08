---
title: Creare un profilo Wi-Fi con chiave precondivisa in Microsoft Intune - Azure | Microsoft Docs
description: Usare un profilo personalizzato per creare un profilo Wi-Fi con una chiave precondivisa e ottenere il codice XML di esempio per i profili Wi-Fi basati su Android, Windows ed EAP in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a65000d46941876b95e0b110d21f2dfb900ca33
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206228"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>Usare un profilo di dispositivo personalizzato per la creazione di un profilo Wi-Fi con una chiave precondivisa in Intune



Le chiavi precondivise (PSK) vengono in genere usate per autenticare gli utenti in reti Wi-Fi o in reti LAN wireless. Con Intune è possibile creare un profilo Wi-Fi con una chiave precondivisa. Per creare il profilo, usare la funzionalità per i **profili di dispositivo personalizzati** all'interno di Intune. Questo articolo include anche alcuni esempi di come creare un profilo Wi-Fi basato su EAP.

Questa funzionalità supporta:

- Android
- Windows
- Wi-Fi basato su EAP

> [!IMPORTANT]
> - L'uso di una chiave precondivisa con Windows 10 determina la visualizzazione di un errore di correzione in Intune. Quando ciò accade, il profilo Wi-Fi viene assegnato correttamente al dispositivo e il profilo funziona come previsto.
> - Se si esporta un profilo Wi-Fi che include una chiave precondivisa, verificare che il file sia protetto. La chiave è in testo normale ed è quindi necessario proteggerla.

## <a name="before-you-begin"></a>Prima di iniziare

- Può risultare più semplice copiare il codice da un computer che si connette alla rete, come descritto di seguito in questo articolo.
- È possibile aggiungere più reti e chiavi aggiungendo altre impostazioni URI OMA.
- Per iOS, usare Apple Configurator in una stazione Mac per impostare il profilo.
- PSK richiede una stringa di 64 cifre esadecimali o una passphrase tra gli 8 e i 63 caratteri ASCII stampabili. Alcuni caratteri, ad esempio asterisco ( * ), non sono supportati.

## <a name="create-a-custom-profile"></a>Creare un profilo personalizzato

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio un buon nome di criterio è **Impostazioni del profilo Wi-Fi OMA-URI personalizzato per dispositivi Android**.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: Scegliere la piattaforma.
    - **Tipo di profilo**: Selezionare **Personalizzato**.

4. In **Impostazioni** selezionare **Aggiungi**. Aggiungere una nuova impostazione OMA-URI con le proprietà seguenti:

    1. **Nome**: Immettere un nome per l'impostazione OMA-URI.
    2. **Descrizione**: Immettere una descrizione per l'impostazione OMA-URI. Questa impostazione è facoltativa ma consigliata.
    3. **OMA-URI**: Immettere una delle opzioni seguenti:

        - **Per Android**: `./Vendor/MSFT/WiFi/Profile/SSID/Settings`
        - **Per Windows**: `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`

        > [!NOTE]
        > Assicurarsi di includere il carattere punto (.) all'inizio.

        SSID è l'identificatore del set di servizi per cui si stanno creando i criteri. Ad esempio, se il Wi-Fi è denominato `Hotspot-1`, immettere `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

    4. **Tipo di dati**: Selezionare **String**.

    5. **Valore**: Incollare il codice XML. Vedere gli [esempi](#android-or-windows-wi-fi-profile-example) in questo articolo. Aggiornare ogni valore in modo corrispondente alle impostazioni di rete. La sezione relativa ai commenti del codice include alcuni puntatori.

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene visualizzato nell'elenco profili. Ora [assegnare](../device-profile-assign.md) il profilo ai gruppi di utenti. Questi criteri possono essere assegnati solo a gruppi di utenti.

Alla successiva verifica da parte del dispositivo, vengono applicati i criteri e viene creato un profilo Wi-Fi nel dispositivo. Il dispositivo può quindi connettersi automaticamente alla rete.

## <a name="android-or-windows-wi-fi-profile-example"></a>Esempio di profilo Wi-Fi Android o Windows

L'esempio seguente include il codice XML per un profilo Wi-Fi Android o Windows. L'esempio è fornito per mostrare il formato corretto e fornire altri dettagli. È solo un esempio e non è da intendersi come configurazione consigliata per l'ambiente.

### <a name="what-you-need-to-know"></a>Informazioni importanti

- `<protected>false</protected>` deve essere impostato su **false**. Se **true**, il dispositivo potrebbe aspettarsi una password crittografata e quindi tentare di decrittografarla, con potenziale esito negativo della connessione.

- `<hex>53534944</hex>` deve essere impostato sul valore esadecimale di `<name><SSID of wifi profile></name>`. I dispositivi Windows 10 possono restituire un errore `x87D1FDE8 Remediation failed` falso, ma il dispositivo contiene comunque il profilo.

- Il codice XML contiene caratteri speciali, come la e commerciale (`&`). L'uso di caratteri speciali può impedire al codice XML di funzionare nel modo previsto. 

### <a name="example"></a>Esempio

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
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
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>Esempio di profilo Wi-Fi basato su EAP
L'esempio seguente include il codice XML per un profilo Wi-Fi basato su EAP: L'esempio è fornito per mostrare il formato corretto e fornire altri dettagli. È solo un esempio e non è da intendersi come configurazione consigliata per l'ambiente.


```xml
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

È possibile creare il file XML da una connessione Wi-Fi esistente. In un computer Windows, eseguire i passaggi seguenti:

1. Creare una cartella locale per i profili Wi-Fi esportati, ad esempio c:\WiFi.
2. Aprire un prompt dei comandi come amministratore (fare clic con il pulsante destro del mouse su `cmd` > **Esegui come amministratore**).
3. Eseguire `netsh wlan show profiles`. Vengono elencati i nomi di tutti i profili.
4. Eseguire `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`. Questo comando crea un file denominato `Wi-Fi-YourProfileName.xml` in c:\Wifi.

    - Se si sta esportando un profilo Wi-Fi che include una chiave precondivisa, aggiungere `key=clear` al comando:
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear` esporta la chiave in chiaro, passaggio necessario per usare il profilo efficacemente.

Dopo aver eseguito il file XML, copiare e incollare la sintassi XML in impostazioni OMA-URI > **Tipo di dati**. [Creare un profilo personalizzato](#create-a-custom-profile) (in questo articolo) illustra la procedura.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` include anche tutti i profili in formato XML.

## <a name="best-practices"></a>Procedure consigliate

- Prima di distribuire un profilo Wi-Fi con una chiave precondivisa, verificare che il dispositivo possa connettersi direttamente all'endpoint.

- Durante la rotazione delle chiavi (password o passphrase), prevedere un tempo di inattività e pianificare le distribuzioni. Considerare di effettuare il push dei nuovi profili Wi-Fi durante ore non lavorative. Avvisare anche gli utenti che la connettività potrebbe essere compromessa.

- Per una transizione senza problemi, assicurarsi che il dispositivo dell'utente disponga di una connessione a Internet alternativa. Ad esempio, l'utente può tornare al Wi-Fi guest (o a un'altra rete Wi-Fi) o avere connettività cellulare per la comunicazione con Intune. Questa connessione alternativa consente all'utente di ricevere gli aggiornamenti dei criteri quando viene aggiornato il profilo Wi-Fi aziendale nel dispositivo.

## <a name="next-steps"></a>Passaggi successivi

Assicurarsi di [assegnare il profilo](device-profile-assign.md) e di [monitorarne lo stato](device-profile-monitor.md).
