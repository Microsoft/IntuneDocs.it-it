---
title: Impostazioni Wi-Fi di Intune per dispositivi Android
titleSuffix: Azure portal
description: Informazioni sulla configurazione in Intune delle impostazioni di connessione Wi-Fi per i dispositivi e Android e Android for Work."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 103e17a4-2993-4359-b340-73e2acf4cf7d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a20ebf026850f28888cd63eb43396a12430bb3cd
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="wi-fi-settings-for-android-and-android-for-work-devices-in-microsoft-intune"></a>Impostazioni Wi-Fi per i dispositivi Android e Android for Work in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Impostazioni Wi-Fi per i profili di base ed enterprise

Le impostazioni Wi-Fi seguenti sono disponibili sia per i dispositivi Android che per i dispositivi Android for Work:

- **Nome rete**: immettere un nome per questa connessione Wi-Fi. È il nome che gli utenti visualizzano quando sfogliano l'elenco delle connessioni disponibili nel dispositivo.
- **SSID**: nome breve per identificatore del set di servizi di rete. Si tratta del nome reale della rete wireless a cui si connetteranno i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il nome di rete creato in precedenza.
- **Connetti automaticamente**: consente al dispositivo di connettersi ogni volta che si trova nel campo della rete.
- **Rete nascosta**: impedisce che la rete venga visualizzata nell'elenco delle reti disponibili sul dispositivo.


## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Impostazioni Wi-Fi solo per i profili enterprise

- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette:
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Altre opzioni quando si sceglie un tipo EAP

#### <a name="server-trust"></a>Server Trust



|Nome impostazione|Altre informazioni|Usare quando|
|-------------|---------------|-----------|
|**Nomi server di certificazione**|Specificare uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Se si forniscono queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti finali quando si connettono alla rete Wi-Fi.|Tipo EAP è impostato su **EAP-TLS** o **EAP-TTLS**|
|**Certificato radice per la convalida server**|Scegliere il profilo del certificato radice attendibile usato per autenticare la connessione. |Tipo EAP è impostato su **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacy dell'identità (identità esterna)**|Specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|Tipo EAP è impostato su **PEAP**|


#### <a name="client-authentication"></a>Autenticazione client


|Nome impostazione|Altre informazioni|Usare quando|
|----------|--------------|----------|
|**Certificato client per l'autenticazione client (certificato di identità)**|Scegliere il profilo di certificato SCEP o PKCS usato per autenticare la connessione.|Tipo EAP è impostato su **EAP-TLS**|
|**Metodo di autenticazione**|Selezionare il metodo di autenticazione per la connessione:<br>- **Certificati** per selezionare il certificato client SCEP o PKCS che corrisponde al certificato di identità presentato al server.<br><br>- **Nome utente e password** per specificare un metodo diverso per l'autenticazione. <br><br>Se si seleziona **Nome utente e password**, configurare:<br><br>-  **Metodo non EAP (identità interna)**, quindi selezionare la modalità di autenticazione della connessione:<br>- **Nessuno**<br>- **Password Authentication Protocol (PAP)**<br>- **Challenge Handshake Authentication Protocol (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP versione 2 (MS-CHAP v2)**<br>Le opzioni disponibili dipendono dal tipo EAP selezionato.<br><br>**e**<br><br>- **Privacy dell'identità (identità esterna)**: specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|Tipo EAP è impostato su **EAP-TTLS** o **PEAP**|
