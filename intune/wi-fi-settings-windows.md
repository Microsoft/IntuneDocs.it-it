---
title: Impostazioni Wi-Fi per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di configurazione Wi-Fi usando le impostazioni Wi-Fi per dispositivi Windows 10 e versioni successive in Microsoft Intune. È possibile configurare impostazioni di base o impostazioni a livello aziendale.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f6532c63612b806f9824f5b9ca98f1ebbbc943f
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321740"
---
## <a name="wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Impostazioni Wi-Fi per dispositivi Windows 10 e versioni successive in Intune

Le impostazioni Wi-Fi vengono usate in un profilo di configurazione applicabile ai dispositivi che eseguono Windows 10 e versioni successive. Alcune delle opzioni possibili sono:

- Basic
- Enterprise

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di dispositivo](device-profile-create.md).

## <a name="settings-for-basic-and-enterprise-profiles"></a>Impostazioni per profili di base e aziendali

- **Nome Wi-Fi (SSID)**: acronimo di Service Set Identifier, identificatore del set di servizi. Questo valore è il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, tuttavia, gli utenti vedono solo il **nome della connessione** configurata.
- **Nome connessione**: immettere un nome descrittivo per la connessione Wi-Fi. Il testo immesso è il nome che gli utenti vedono quando visualizzano le connessioni disponibili nel dispositivo.
- **Connetti automaticamente quando la rete è disponibile**: se impostata su **Sì**, i dispositivi si connettono automaticamente quando la rete è disponibile. Se impostata su **No**, i dispositivi non si connettono automaticamente.
  - **Connetti alla rete preferita se disponibile**: se per i dispositivi è disponibile una rete preferita, scegliere **Sì** per usare la rete preferita. Scegliere **No** per usare la rete Wi-Fi in questo profilo di configurazione.

    Si supponga ad esempio di creare una rete Wi-Fi **ContosoCorp** e di usare **ContosoCorp** all'interno di questo profilo di configurazione. Nel raggio di copertura è disponibile anche una rete Wi-Fi **ContosoGuest**. Quando si trovano nel raggio di copertura, i dispositivi aziendali devono connettersi automaticamente a **ContosoCorp**. In questo scenario impostare la proprietà **Connetti alla rete preferita se disponibile** su **No**.

  - **Connetti quando la rete non sta trasmettendo il nome (SSID)**: scegliere **Sì** per indicare al profilo di configurazione di connettersi automaticamente alla rete, anche quando la rete è nascosta, ovvero quando il relativo SSID non viene trasmesso pubblicamente. Scegliere **No** se non si vuole che il profilo di configurazione si connetta alla rete nascosta.

- **Impostazioni del proxy aziendale**: scegliere questa impostazione per usare le impostazioni proxy all'interno dell'organizzazione. Le opzioni disponibili sono:
  - **Nessuna**: non sono state configurate impostazioni proxy.
  - **Configura manualmente**: immettere l'**indirizzo IP del server proxy** e il relativo **numero di porta**.
  - **Configura automaticamente**: immettere l'URL che punta a uno script di configurazione automatica del proxy. Immettere ad esempio `http://proxy.contoso.com/proxy.pac`.

## <a name="settings-for-basic-profiles-only"></a>Impostazioni solo per i profili di base

- **Tipo di sicurezza wireless**: immettere il protocollo di sicurezza usato per autenticare i dispositivi nella rete. Le opzioni disponibili sono:
  - **Apri (nessuna autenticazione)**: usare questa opzione solo se la rete non è protetta.
  - **WPA/WPA2-Personale**

## <a name="settings-for-enterprise-profiles-only"></a>Impostazioni solo per i profili aziendali

- **Accesso Single Sign-On (SSO)**: consente di configurare l'accesso Single Sign-On (SSO) in cui le credenziali vengono condivise per l'accesso al computer e alla rete Wi-Fi. Le opzioni disponibili sono:
  - **Disabilita**: disabilita il comportamento SSO. L'utente deve eseguire l'autenticazione alla rete separatamente.
  - **Enable before user signs into device** (Abilita prima dell'accesso dell'utente al dispositivo): consente di usare SSO per l'autenticazione in rete prima della procedura di accesso dell'utente.
  - **Enable after user signs into device**: (Abilita dopo l'accesso dell'utente al dispositivo): consente di usare SSO per l'autenticazione in rete dopo il completamento della procedura di accesso dell'utente.
  - **Maximum time to authenticate before timeout** (Tempo massimo per l'autenticazione prima del timeout): immettere il numero massimo di secondi di attesa prima dell'autenticazione in rete, da 1 a 120 secondi.
  - **Allow Windows to prompt user for additional authentication credentials** (Consenti a Windows di chiedere credenziali di autenticazione aggiuntive all'utente): se si sceglie **Sì**, il sistema Windows potrà chiedere credenziali aggiuntive all'utente, se il metodo di autenticazione lo richiede. Scegliere **No** per nascondere questi prompt.

- **Consenti memorizzazione nella cache Pairwise Master Key (PMK)**: selezionare **Sì** per memorizzare nella cache la PMK usata nell'autenticazione. La memorizzazione nella cache in genere consente una procedura di autenticazione in rete più rapida. Scegliere **No** per imporre l'handshake di autenticazione ogni volta che l'utente si connette alla rete Wi-Fi.

  - **Maximum time a PMK is stored in cache** (Tempo massimo di memorizzazione di una PMK nella cache): immettere il numero di minuti di memorizzazione di una PMK (Pairwise Master Key) nella cache, da 5 a 1440 minuti.
  - **Maximum number of PMKs stored in cache** (Numero massimo di PMK memorizzate nella cache): immettere il numero di chiavi memorizzate nella cache, da 1 a 255.

- **Abilita la preautenticazione**: la preautenticazione consente l'autenticazione del profilo presso tutti i punti di accesso alla rete nel profilo prima della connessione. Quando si passa da un punto di accesso a un altro, la preautenticazione riconnette più rapidamente l'utente o i dispositivi. Scegliere **Sì** per consentire l'autenticazione del profilo presso tutti i punti di accesso alla rete inclusi nel raggio di copertura. Scegliere **No** per chiedere all'utente o al dispositivo di eseguire separatamente l'autenticazione a ogni punto di accesso.

  - **Numero massimo tentativi di preautenticazione**: immettere il numero di tentativi di preautenticazione, da 1 a 16.

- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) per autenticare le connessioni wireless protette. Le opzioni disponibili sono:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **PEAP** (Protected EAP)

### <a name="more-options-when-you-choose-the-eap-type"></a>Altre opzioni quando si sceglie il tipo EAP

> [!NOTE]
> Quando si usa un tipo EAP, attualmente sono supportati solo i profili di certificato SCEP. I profili di certificato PKCS non sono supportati. Quando si chiede a un utente di immettere un certificato, assicurarsi di scegliere un certificato SCEP.

#### <a name="server-trust"></a>Server Trust

|Nome impostazione|Altre informazioni|Usare quando|
|--------------|-------------|----------|
|**Nomi server di certificazione**|Immettere uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Se si immettono queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti quando si connettono alla rete Wi-Fi.|Tipo EAP è impostato su **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Certificato radice per la convalida server**|Scegliere il profilo del certificato radice attendibile usato per autenticare la connessione. |Tipo EAP è impostato su **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacy dell'identità (identità esterna)**|Immettere il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.|Tipo EAP è impostato su **PEAP**|

#### <a name="client-authentication"></a>Autenticazione client

| Nome impostazione | Altre informazioni | Usare quando |
|---|---|---|
| **Certificato client per l'autenticazione client (certificato di identità)** |  Scegliere il profilo di certificato SCEP usato per autenticare la connessione. | Tipo EAP è impostato su **EAP-TLS** |
| **Metodo di autenticazione** | Selezionare il metodo di autenticazione per la connessione:<br><br>- **Certificati**: selezionare il certificato client SCEP che corrisponde al certificato di identità presentato al server.<br><br>- **Nome utente e password**: immettere un **metodo non EAP (identità interna)** per l'autenticazione. Le opzioni disponibili sono:<br><br>- **Password Authentication Protocol (PAP)**<br>- **Challenge Handshake (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP versione 2 (MS-CHAP v2)**<br><br>- **Privacy dell'identità (identità esterna)**: immettere il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro. | Il tipo EAP è **EAP-TTLS** |

## <a name="use-an-imported-settings-file"></a>Usare un file di impostazioni importato

Per le impostazioni non disponibili in Intune, è possibile esportare le impostazioni Wi-Fi da un altro dispositivo Windows. Questa esportazione crea un file XML contenente tutte le impostazioni. Importare quindi il file in Intune e usarlo come profilo Wi-Fi. Vedere [Esportare e importare impostazioni Wi-Fi per i dispositivi Windows](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Passaggi successivi
[Configurare le impostazioni Wi-Fi in Intune](wi-fi-settings-configure.md)
