---
title: Impostazioni Wi-Fi di Intune per dispositivi iOS | Anteprima di Intune in Azure | Documentazione Microsoft
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni Wi-Fi nei dispositivi iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89229a5e-3421-4221-a62f-fa800620cc0d
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ac907e4cb63e4175dafc4c50239d3e0cbe581ad9
ms.openlocfilehash: 1790878c1d1b4ad8381e6c3a3689542877ec6d26


---

# <a name="intune-wi-fi-settings-for-ios-devices-in-intune-azure-preview"></a>Impostazioni Wi-Fi di Intune per dispositivi iOS nell'anteprima di Intune in Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Impostazioni Wi-Fi per i profili di base ed enterprise

- **Nome rete**: immettere un nome per questa connessione Wi-Fi. È il nome che gli utenti visualizzano quando sfogliano l'elenco delle connessioni disponibili nel dispositivo.
- **SSID**: nome breve per identificatore del set di servizi di rete. Si tratta del nome reale della rete wireless a cui si connetteranno i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il nome di rete creato in precedenza.
- **Connetti automaticamente**: consente al dispositivo di connettersi ogni volta che si trova nel campo della rete.
- **Rete nascosta**: impedisce che la rete venga visualizzata nell'elenco delle reti disponibili sul dispositivo.
- **Impostazioni proxy**: scegliere tra:
    - **Nessuno**: non viene configurata nessuna impostazione proxy.
    - **Manuale**: immettere l'**Indirizzo server proxy** (come indirizzo IP), associato al **Numero di porta**.
    - **Automatico**: consente di usare un file per configurare il server proxy. Immettere l'**URL del server proxy** (ad esempio **http://proxy.contoso.com**) che contiene il file di configurazione.

## <a name="wi-fi-settings-for-basic-profiles-only"></a>Impostazioni Wi-Fi solo per i profili di base

- **Tipo di sicurezza**: selezionare il protocollo di sicurezza da usare per l'autenticazione alla rete Wi-Fi da:
    - **Apri (nessuna autenticazione)**: usare questa opzione solo se la rete non è protetta.
    - **WPA/WPA2 - Personale**
    - **WEP**

## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Impostazioni Wi-Fi solo per i profili enterprise

- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette:
    - **EAP-FAST**
    - **EAP-SIM**
    - **EAP-TLS**
    - **EAP-TTLS**
    - **LEAP**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Altre opzioni quando si sceglie un tipo EAP


|Nome impostazione|Altre informazioni|Usare quando|
|--------------|-------------|----------|
|**Impostazioni Protected Access Credential (PAC)**|Selezionare questa opzione per usare credenziali di accesso protetto per stabilire un tunnel autenticato tra il client e il server di autenticazione. Selezionare un'opzione tra:<br>- **Uso (PAC)**: se presente, verrà usato un file PAC esistente.<br>- **Uso e provisioning di PAC**: consente di eseguire il provisioning del file PAC nei dispositivi.<br>- **Uso e provisioning di PAC in modo anonimo**: consente di eseguire il provisioning del file PAC nei dispositivi e garantisce che tale processo venga eseguito senza autenticazione del server.|Tipo EAP è impostato su **EAP-FAST**|

#### <a name="server-trust"></a>Server Trust


|Nome impostazione|Altre informazioni|Usare quando|
|--------------|-------------|----------|
|**Nomi server di certificazione**|Specificare uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Se si forniscono queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti finali quando si connettono alla rete Wi-Fi.|Tipo EAP è impostato su **EAP-TLS**, **EAP-TTLS** o **PEAP**.|
|**Certificato radice per la convalida server**|Scegliere il profilo del certificato radice attendibile usato per autenticare la connessione. |Tipo EAP è impostato su **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacy dell'identità (identità esterna)**|Specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|Tipo EAP è impostato su **PEAP**|


#### <a name="client-authentication"></a>Autenticazione client


|Nome impostazione|Altre informazioni|Usare quando|
|--------------|-------------|----------|
|**Certificato client per l'autenticazione client (certificato di identità)**|Scegliere il profilo di certificato SCEP o PKCS usato per autenticare la connessione.|Tipo EAP è impostato su **EAP-TLS**|
|**Metodo di autenticazione**|Selezionare il metodo di autenticazione per la connessione:<br>- **Certificati** per selezionare il certificato client SCEP o PKCS che corrisponde al certificato di identità presentato al server.<br><br>- **Nome utente e password** per specificare un metodo diverso per l'autenticazione. <br><br>Se si seleziona **Nome utente e password**, configurare:<br><br>-  **Metodo non EAP (identità interna)**, quindi selezionare la modalità di autenticazione della connessione:<br>- **Nessuno**<br>- **Password Authentication Protocol (PAP)**<br>- **Challenge Handshake Authentication Protocol (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP versione 2 (MS-CHAP v2)**<br>Le opzioni disponibili dipendono dal tipo EAP selezionato.<br><br>**e**<br><br>- **Privacy dell'identità (identità esterna)**: specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|Tipo EAP è impostato su **EAP-TTLS** o *



<!--HONumber=Feb17_HO1-->


