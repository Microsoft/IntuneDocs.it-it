---
title: Configurare le impostazioni Wi-Fi in Microsoft Intune per i dispositivi che eseguono Android
titleSuffix: ''
description: Informazioni sulle impostazioni di configurazione Wi-Fi in Intune per i dispositivi che eseguono Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0157815322488525a4ce7a3d6d2c90cbb8d3ff2a
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905666"
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-android-work-profiles-and-android-kiosk-devices"></a>Configurare le impostazioni Wi-Fi in Microsoft Intune per i dispositivi che eseguono Android, i profili di lavoro Android e i dispositivi in modalità tutto schermo Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni Wi-Fi che è possibile configurare in Microsoft Intune per i dispositivi che eseguono Android e i profili di lavoro Android.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Impostazioni Wi-Fi per i profili di base ed enterprise

Le impostazioni Wi-Fi seguenti sono disponibili sia per i dispositivi Android che per i dispositivi del profilo di lavoro Android:

- **Nome rete**: immettere un nome per questa connessione Wi-Fi. È il nome che gli utenti visualizzano quando sfogliano l'elenco delle connessioni disponibili nel dispositivo.
- **SSID**: nome breve per identificatore del set di servizi di rete. Si tratta del nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il nome di rete configurato in precedenza.
- **Connetti automaticamente**: consente al dispositivo di connettersi ogni volta che si trova nel campo della rete.
- **Rete nascosta**: impedisce che la rete venga visualizzata nell'elenco delle reti disponibili sul dispositivo.

## <a name="wi-fi-settings-available-for-enterprise-kiosk-profiles"></a>Impostazioni Wi-Fi disponibili per i profili di modalità tutto schermo aziendali
- **Tipo Wi-Fi**: queste impostazioni del tipo Wi-Fi sono disponibili solo quando si sceglie **Tipo di profilo** > **Proprietario dispositivo** > **Wi-Fi**.
    - **Apri (nessuna autenticazione)**
    - **WEP - Chiave precondivisa**: è necessario specificare la password nella casella **Chiave precondivisa**.
    - **WPA - Chiave precondivisa**: è necessario specificare la password nella casella **Chiave precondivisa**

## <a name="wi-fi-settings-for-android-legacy-and-android-work-profiles-only"></a>Impostazioni Wi-Fi solo per i dispositivi Android legacy e i profili di lavoro Android

- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette:
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Altre opzioni quando si sceglie un tipo EAP

#### <a name="server-trust"></a>Server Trust



|Nome dell'impostazione|Ulteriori informazioni|Usare quando|
|-------------|---------------|-----------|
|**Nomi server di certificazione**|Specificare uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Se si specificano queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti quando si connettono alla rete Wi-Fi.|Tipo EAP è impostato su **EAP-TLS** o **EAP-TTLS**|
|**Certificato radice per la convalida server**|Scegliere il profilo del certificato radice attendibile usato per autenticare la connessione. |Tipo EAP è impostato su **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacy dell'identità (identità esterna)**|Specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|Tipo EAP è impostato su **PEAP**|


#### <a name="client-authentication"></a>Autenticazione client


|                                     Nome dell'impostazione                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Ulteriori informazioni                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            Usare quando                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>Certificato client per l'autenticazione client (certificato di identità)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Scegliere il profilo di certificato SCEP o PKCS usato per autenticare la connessione.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              Tipo EAP è impostato su <strong>EAP-TLS</strong>              |
|                        <strong>Metodo di autenticazione</strong>                        | Selezionare il metodo di autenticazione per la connessione:<br>- <strong>Certificati</strong> per selezionare il certificato client SCEP o PKCS che corrisponde al certificato di identità presentato al server.<br><br>- <strong>Nome utente e password</strong> per specificare un metodo diverso per l'autenticazione. <br><br>Se si seleziona <strong>Nome utente e password</strong>, configurare:<br><br>-  <strong>Metodo non EAP (identità interna)</strong> e quindi selezionare la modalità di autenticazione della connessione:<br>- <strong>Nessuno</strong><br>- <strong>Password Authentication Protocol (PAP)</strong><br>- <strong>Challenge Handshake Authentication Protocol (CHAP)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP versione 2 (MS-CHAP v2)</strong><br>Le opzioni disponibili dipendono dal tipo EAP selezionato.<br><br><strong>e</strong><br><br>- <strong>Privacy dell'identità (identità esterna)</strong>: specificare il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro. | Tipo EAP è impostato su <strong>EAP-TTLS</strong> o <strong>PEAP</strong> |

