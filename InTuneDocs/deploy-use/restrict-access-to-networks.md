---
title: Limitare l&quot;accesso alle reti con Cisco ISE | Documentazione Microsoft
description: Usare ISE Cisco con Intune in modo che i dispositivi vengano registrati in Intune e siano conformi ai relativi criteri prima di accedere a Wi-Fi e VPN controllati da Cisco ISE.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 9eb0ea307702f3ae07db4d5c5a82d03f13b727fb


---

# <a name="using-cisco-ise-with-microsoft-intune"></a>Uso di Cisco ISE con Microsoft Intune
L'integrazione di Intune con Cisco ISE (Identity Services Engine) consente di creare criteri di rete nell'ambiente ISE usando lo stato di conformità e registrazione dei dispositivi di Intune. È possibile usare questi criteri per verificare che l'accesso alla rete aziendale sia limitato ai dispositivi gestiti da Intune e conformi ai criteri di Intune.

## <a name="configuration-steps"></a>Procedura di configurazione

Per abilitare l'integrazione, non è necessario eseguire installazioni nel tenant di Intune. Sarà necessario concedere al server Cisco ISE l'autorizzazione ad accedere al tenant di Intune. Al termine di questa operazione, il resto dell'installazione viene eseguita nel server Cisco ISE. Questo articolo illustra come concedere al server ISE le autorizzazioni necessarie per accedere al tenant di Intune.

### <a name="step-1-manage-the-certificates"></a>Passaggio 1: Gestire i certificati
Esportare il certificato dalla console di Azure Active Directory (Azure AD) e quindi importarlo nell'archivio dei certificati attendibili della console ISE:

#### <a name="internet-explorer-11"></a>Internet Explorer 11


   a. Eseguire Internet Explorer come amministratore e accedere alla console di Azure AD.

   b. Scegliere l'icona del lucchetto nella barra degli indirizzi e quindi **Visualizza certificati**.

   c. Nella scheda **Dettagli** delle proprietà del certificato scegliere **Copia su file**.

   d. Nella pagina iniziale **dell'Esportazione guidata certificati** fare clic su **Avanti**.

   e. Nella pagina **Formato di file di esportazione** lasciare l'impostazione predefinita, **Binario codificato DER x.509 (. CER)**, e scegliere **Avanti**.  

   f. Nella pagina **File da esportare** scegliere **Sfoglia** per selezionare un percorso in cui salvare il file e specificare un nome di file. Anche se apparentemente si sta selezionando un file da esportare, in realtà si assegna un nome al file in cui verrà salvato il certificato esportato. Scegliere **Avanti** &gt; **Fine**.

   g. Dall'interno della console ISE importare il certificato di Intune, ovvero il file esportato, nell'archivio dei **certificati attendibili**.

#### <a name="safari"></a>Safari

 a. Accedere alla console di Azure AD.

b. Scegliere l'icona del blocco &gt;  **Ulteriori informazioni**.

   c. Scegliere **Visualizza certificato** &gt; **Dettagli**.

   d. Scegliere il certificato, quindi **Esporta**. 

   e. Dall'interno della console ISE importare il certificato di Intune, ovvero il file esportato, nell'archivio dei **certificati attendibili**.

> [!IMPORTANT]
>
> Controllare la data di scadenza del certificato, poiché sarà necessario esportare e importare un nuovo certificato quando questo scade.


### <a name="obtain-a-self-signed-cert-from-ise"></a>Ottenere da ISE un certificato autofirmato 

1.  Nella console ISE passare ad **Amministrazione** > **Certificati** > **Certificati di sistema** > **Genera certificato autofirmato**.  
2.       Esportare il certificato autofirmato.
3. Modificare il certificato esportato in un editor di testo:

 - Eliminare ** -----BEGIN CERTIFICATE-----**
 - Eliminare ** -----END CERTIFICATE-----**
 
Verificare che tutto il testo sia una singola riga


### <a name="step-2-create-an-app-for-ise-in-your-azure-ad-tenant"></a>Passaggio 2: Creare un'app per ISE nel tenant di Azure AD
1. Nella console di Azure AD scegliere **Applicazioni** > **Aggiungi applicazione** > **Aggiungi un'applicazione che l'organizzazione sta sviluppando**.
2. Specificare un nome e un URL per l'app. L'URL può essere il sito Web aziendale.
3. Scaricare il manifesto dell'app (file JSON).
4. Modificare il file JSON del manifesto. Nell'impostazione **keyCredentials** indicare il testo del certificato modificato del passaggio 1 come valore dell'impostazione.
5. Salvare il file senza modificarne il nome.
6. Specificare per l'app le autorizzazioni per l'API Microsoft Graph e Microsoft Intune.

 a. Per Microsoft Graph, scegliere gli elementi seguenti:
    - **Autorizzazioni per l'applicazione**: Lettura dati directory
    - **Autorizzazioni delegate**:
        - Accedi ai dati di un altro utente in qualsiasi momento
        - Effettua l'accesso utente

 b. Per l'API Microsoft Intune, in **Autorizzazioni applicazione** scegliere **Get device state and compliance from Intune** (Ottieni stato del dispositivo e conformità da Intune).

7. Scegliere **Visualizza endpoint** e copiare i valori seguenti per l'uso nella configurazione delle impostazioni ISE:

|Valore nel portale di Azure AD|Campo corrispondente nel portale ISE|
|-------------------|---------------------------------|
|Endpoint API di Microsoft Azure AD Graph|URL individuazione automatica|
|Endpoint del token OAuth 2.0|URL emittente di token|
|Aggiornare il codice con l'ID client|ID client|

### <a name="step-4-upload-the-self-signed-certificate-from-ise-into-the-ise-app-you-created-in-azure-ad"></a>Passaggio 4: Caricare il certificato autofirmato da ISE nell'app ISE creata in Azure AD
1.     Ottenere il valore e l'identificazione personale del certificato con codifica base64 da un file di certificato pubblico X.509 con estensione cer. In questo esempio viene usato PowerShell:
   
      
      $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2    $cer.Import(“mycer.cer”)    $bin = $cer.GetRawCertData()    $base64Value = [System.Convert]::ToBase64String($bin)    $bin = $cer.GetCertHash()    $base64Thumbprint = [System.Convert]::ToBase64String($bin)    $keyid = [System.Guid]::NewGuid().ToString()
 
    Archiviare i valori di $base64Thumbprint, $base64Value e $keyid, da usare nel passaggio successivo.
2.       Caricare il certificato tramite il file manifesto. Accedere al [portale di gestione di Azure](https://manage.windowsazure.com).
2.      Nello snap-in Azure AD trovare l'applicazione da configurare con un certificato X.509.
3.      Scaricare il file manifesto dell'applicazione. 
5.      Sostituire la proprietà vuota "KeyCredentials": [], con il codice JSON seguente.  Il tipo complesso KeyCredentials è documentato in [Informazioni di riferimento su entità e tipi complessi](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType).

 
    “keyCredentials“: [ { “customKeyIdentifier“: “$base64Thumbprint_from_above”, “keyId“: “$keyid_from_above“, “type”: “AsymmetricX509Cert”, “usage”: “Verify”, “value”:  “$base64Value_from_above” }2. 
     ], 
 
Ad esempio:
 
    “keyCredentials“: [
    {
    “customKeyIdentifier“: “ieF43L8nkyw/PEHjWvj+PkWebXk=”,
    “keyId“: “2d6d849e-3e9e-46cd-b5ed-0f9e30d078cc”,
    “type”: “AsymmetricX509Cert”,
    “usage”: “Verify”,
    “value”: “MIICWjCCAgSgAwIBA***omitted for brevity***qoD4dmgJqZmXDfFyQ”
    }
    ],
 
6.      Salvare la modifica nel file manifesto dell'applicazione.
7.      Caricare il file manifesto dell'applicazione modificato tramite il portale di gestione di Azure.
8.      Facoltativo: scaricare nuovamente il manifesto per verificare che il certificato X.509 sia presente nell'applicazione.

>[!NOTE]
>
> KeyCredentials è una raccolta, quindi è possibile caricare più certificati X.509 per esigenze di rollover o eliminare più certificati in casi di compromissione.


### <a name="step-4-configure-ise-settings"></a>Passaggio 4: Configurare le impostazioni ISE
Nella console di amministrazione ISE indicare questi valori:
  - **Tipo di server**: Mobile Device Manager
  - **Tipo di autenticazione**: OAuth, credenziali del client
  - **Individuazione automatica**: sì
  - **URL individuazione automatica**: *immettere il valore del passaggio 1.*
  - **ID client**: *immettere il valore del passaggio 1.*
  - **URL emittente di token**: *immettere il valore del passaggio 1.*



## <a name="information-shared-between-your-intune-tenant-and-your-cisco-ise-server"></a>Informazioni condivise tra il tenant di Intune e il server Cisco ISE
Questa tabella elenca le informazioni condivise tra il tenant di Intune e il server Cisco ISE per i dispositivi gestiti da Intune.

|Proprietà|  Descrizione|
|---------------|------------------------------------------------------------|
|complianceState|Stringa True o False che indica se il dispositivo è conforme o non conforme.|
|IsManaged|Stringa True o False che indica se il client è gestito o meno da Intune.|
|macAddress|Indirizzo MAC del dispositivo.|
|serialNumber|Numero di serie del dispositivo. Si applica solo ai dispositivi iOS.|
|imei|Il numero IMEI (15 cifre decimali: 14 cifre più un numero di controllo) o IMEISV (16 cifre) include informazioni su origine, modello e numero di serie del dispositivo. La struttura del numero è specificata in 3GPP TS 23.003. Si applica solo ai dispositivi con schede SIM.|
|udid|Identificatore univoco del dispositivo ovvero una sequenza di 40 lettere e numeri. È specifico dei dispositivi iOS.|
|meid|Identificativo di apparecchiatura mobile, ovvero un numero univoco globale che identifica un componente fisico della stazione mobile CDMA. Il formato del corpo è definito dal report 3GPP2 S. R0048. In pratica può tuttavia essere considerato un IMEI con cifre esadecimali. Un MEID ha una lunghezza di 56 bit (14 cifre esadecimali). È costituito da tre campi, inclusi un codice regionale (RR) di 8 bit, un codice di produttore di 24 bit e un numero di serie di 24 bit assegnato dal produttore.|
|osVersion|Versione del sistema operativo del dispositivo.
|modello|Modello del dispositivo.
|manufacturer|Produttore del dispositivo.
|azureDeviceId|L'ID del dispositivo dopo l'aggiunta dell'area di lavoro in Azure AD. È un GUID vuoto per i dispositivi non aggiunti.|
|lastContactTimeUtc|Data e ora in cui il dispositivo ha eseguito l'ultima archiviazione con il servizio di gestione di Intune.


## <a name="user-experience"></a>Esperienza utente

Quando un utente tenta di accedere alle risorse usando un dispositivo non registrato, riceve una richiesta simile alla seguente:

![Esempio di richiesta di registrazione](../media/cisco-ise-user-iphone.png)

Quando l'utente sceglie di eseguire la registrazione, viene reindirizzato al processo di registrazione di Intune. L'esperienza di registrazione in Intune è illustrata negli argomenti seguenti:

- [Registrare il dispositivo Android in Intune](/intune/enduser/enroll-your-device-in-Intune-android)</br>
- [Registrare il dispositivo iOS in Intune](/intune/enduser/enroll-your-device-in-intune-ios)</br>
- [Registrare il dispositivo Mac OS X in Intune](/intune/enduser/enroll-your-device-in-intune-mac-os-x)</br>
- [Registrare il dispositivo Windows in Intune](/intune/enduser/enroll-your-device-in-intune-windows)</br>

È anche disponibile un [set scaricabile di istruzioni per la registrazione](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) che consente di creare indicazioni personalizzate per l'esperienza utente.


### <a name="see-also"></a>Vedere anche

[Cisco Identity Services Engine Administrator Guide, Release 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)



<!--HONumber=Dec16_HO2-->


