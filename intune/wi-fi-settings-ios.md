---
title: Configurare le impostazioni Wi-Fi in Microsoft Intune per i dispositivi che eseguono iOS
titleSuffix: ''
description: Informazioni sulle impostazioni di configurazione Wi-Fi in Intune per i dispositivi che eseguono iOS
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 65bfb5bcd756d59a75aec947356ad9fe5fcb5d05
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831193"
---
# <a name="wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Impostazioni Wi-Fi per dispositivi iOS in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra tutte le impostazioni Wi-Fi che è possibile configurare in Microsoft Intune per i dispositivi che eseguono iOS.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Impostazioni Wi-Fi per i profili di base ed enterprise

- **Nome rete**: immettere un nome per questa connessione Wi-Fi. È il nome che gli utenti visualizzano quando sfogliano l'elenco delle connessioni disponibili nel dispositivo.
- **SSID**: nome breve per identificatore del set di servizi di rete. Si tratta del nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il nome di rete configurato in precedenza.
- **Connetti automaticamente**: consente al dispositivo di connettersi ogni volta che si trova nel campo della rete.
- **Rete nascosta**: impedisce che la rete venga visualizzata nell'elenco delle reti disponibili sul dispositivo.
- **Chiave precondivisa** - 
- **Impostazioni proxy**: scegliere tra:
    - **Nessuno**: non viene configurata nessuna impostazione proxy.
    - **Manuale**: immettere l'**Indirizzo server proxy** (come indirizzo IP), associato al **Numero di porta**.
    - **Automatico**: consente di usare un file per configurare il server proxy. Immettere l'**URL del server proxy**, ad esempio **http://proxy.contoso.com**, contenente il file di configurazione.

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
|**Nomi server di certificazione**|Specificare uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Se si specificano queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti quando si connettono alla rete Wi-Fi.|Tipo EAP è impostato su **EAP-TLS**, **EAP-TTLS** o **PEAP**.|
|**Certificato radice per la convalida server**|Scegliere il profilo del certificato radice attendibile usato per autenticare la connessione. |Tipo EAP è impostato su **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacy dell'identità (identità esterna)**|Specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|Tipo EAP è impostato su **PEAP**|


#### <a name="client-authentication"></a>Autenticazione client


|                                     Nome impostazione                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Altre informazioni                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                  Usare quando                  |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------|
| <strong>Certificato client per l'autenticazione client (certificato di identità)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Scegliere il profilo di certificato SCEP o PKCS usato per autenticare la connessione.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |    Tipo EAP è impostato su <strong>EAP-TLS</strong>    |
|                        <strong>Metodo di autenticazione</strong>                        | Selezionare il metodo di autenticazione per la connessione:<br>- <strong>Certificati</strong> per selezionare il certificato client SCEP o PKCS che corrisponde al certificato di identità presentato al server.<br><br>- <strong>Nome utente e password</strong> per specificare un metodo diverso per l'autenticazione. <br><br>Se si seleziona <strong>Nome utente e password</strong>, configurare:<br><br>-  <strong>Metodo non EAP (identità interna)</strong> e quindi selezionare la modalità di autenticazione della connessione:<br>- <strong>Nessuno</strong><br>- <strong>Password Authentication Protocol (PAP)</strong><br>- <strong>Challenge Handshake Authentication Protocol (CHAP)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP versione 2 (MS-CHAP v2)</strong><br>Le opzioni disponibili dipendono dal tipo EAP selezionato.<br><br><strong>e</strong><br><br>- <strong>Privacy dell'identità (identità esterna)</strong>: specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro. | Tipo EAP è impostato su <strong>EAP-TTLS</strong> o * |

