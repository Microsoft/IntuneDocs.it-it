---
title: Impostazioni Wi-Fi per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di configurazione Wi-Fi usando le impostazioni Wi-Fi per dispositivi Windows 10 e versioni successive in Microsoft Intune. È possibile configurare impostazioni di base o impostazioni a livello aziendale.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/8/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.reviewer: tycast
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 528819452accf4a7f17e54b3c05693dee5cab74f
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71239448"
---
# <a name="add-wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Aggiungere le impostazioni Wi-Fi per dispositivi Windows 10 e versioni successive in Intune

È possibile creare un profilo con impostazioni Wi-Fi specifiche e quindi distribuire questo profilo ai dispositivi Windows 10 e versioni successive. Microsoft Intune offre numerose funzionalità, tra cui l'autenticazione nella rete, l'uso di una chiave precondivisa e altro ancora.

Questo articolo descrive queste impostazioni.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di dispositivo](device-profile-create.md).

## <a name="basic-profile"></a>Profilo di base

- **Tipo Wi-Fi**: scegliere **Base**. 

- **Nome Wi-Fi (SSID)** : acronimo di Service Set Identifier, identificatore del set di servizi. Questo valore è il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, tuttavia, gli utenti vedono solo il **nome della connessione** configurata.

- **Nome connessione**: immettere un nome descrittivo per la connessione Wi-Fi. Il testo immesso è il nome che gli utenti vedono quando visualizzano le connessioni disponibili nel dispositivo.

- **Connetti automaticamente quando la rete è disponibile**: se impostata su **Sì**, i dispositivi si connettono automaticamente quando la rete è disponibile. Se impostata su **No**, i dispositivi non si connettono automaticamente.

  - **Connetti alla rete preferita se disponibile**: se per i dispositivi è disponibile una rete preferita, scegliere **Sì** per usare la rete preferita. Scegliere **No** per usare la rete Wi-Fi in questo profilo di configurazione.

    Si supponga ad esempio di creare una rete Wi-Fi **ContosoCorp** e di usare **ContosoCorp** all'interno di questo profilo di configurazione. Nel raggio di copertura è disponibile anche una rete Wi-Fi **ContosoGuest**. Quando si trovano nel raggio di copertura, i dispositivi aziendali devono connettersi automaticamente a **ContosoCorp**. In questo scenario impostare la proprietà **Connetti alla rete preferita se disponibile** su **No**.

  - **Connetti quando la rete non sta trasmettendo il nome (SSID)** : scegliere **Sì** per indicare al profilo di configurazione di connettersi automaticamente alla rete, anche quando la rete è nascosta, ovvero quando il relativo SSID non viene trasmesso pubblicamente. Scegliere **No** se non si vuole che il profilo di configurazione si connetta alla rete nascosta.

- **Limite per la connessione a consumo**: l'amministratore può scegliere come viene misurato il traffico di rete. Le applicazioni possono quindi modificare il comportamento del traffico di rete in base a questa impostazione. Le opzioni disponibili sono:

  - **Senza restrizioni**: impostazione predefinita. La connessione non è a consumo e non sono previste restrizioni sul traffico.
  - **Fisso**: usare questa opzione se la rete è configurata con un limite fisso per il traffico di rete. Quando viene raggiunto questo limite, l'accesso alla rete non viene più consentito.
  - **Variabile**: usare questa opzione se il traffico di rete viene addebitato per byte (costo per byte).

- **Tipo di sicurezza wireless**: immettere il protocollo di sicurezza usato per autenticare i dispositivi nella rete. Le opzioni disponibili sono:
  - **Apri (nessuna autenticazione)** : usare questa opzione solo se la rete non è protetta.
  - **WPA/WPA2-Personal**: opzione che offre maggiore protezione in genere usata per la connettività Wi-Fi. Per maggiore sicurezza, è anche possibile immettere una password chiave precondivisa o una chiave di rete. 

    - **Chiave precondivisa** (PSK): facoltativa. Visualizzato quando si sceglie **WPA/WPA2-Personal** come tipo di sicurezza. Quando viene configurata la rete dell'organizzazione, viene configurata anche una password o una chiave di rete. Immettere questa password o chiave di rete per il valore di chiave precondivisa. Immettere una stringa con un numero di caratteri compreso tra 8 e 64. Se la password o la chiave di rete è di 64 caratteri, immettere caratteri esadecimali.
    
      > [!NOTE]
      > Quando si salva il profilo Wi-Fi, il valore della chiave precondivisa immesso non viene visualizzato per motivi di sicurezza. Resta visualizzata l'opzione **Non configurata** per la chiave precondivisa anche se è già stata salvata nel profilo. Per modificare la chiave precondivisa, immettere una nuova chiave e salvare il profilo. Se si salva una chiave precondivisa, si modificano i criteri e si lascia vuota la chiave precondivisa, verrà ancora usata la chiave precondivisa esistente.
      
      > [!IMPORTANT]
      > La PSK è la stessa per tutti i dispositivi a cui viene indirizzata la profule. Se la chiave è compromessa, può essere usata da qualsiasi dispositivo per connettersi alla rete Wi-Fi. Proteggere precondivise per evitare accessi non autorizzati.

- **Impostazioni del proxy aziendale**: scegliere questa impostazione per usare le impostazioni proxy all'interno dell'organizzazione. Le opzioni disponibili sono:
  - **Nessuna**: non sono state configurate impostazioni proxy.
  - **Configura manualmente**: immettere l'**indirizzo IP del server proxy** e il relativo **numero di porta**.
  - **Configura automaticamente**: immettere l'URL che punta a uno script di configurazione automatica del proxy. Immettere ad esempio `http://proxy.contoso.com/proxy.pac`.

Selezionare **OK** > **Crea** per salvare le modifiche. Il profilo verrà creato e visualizzato nell'elenco dei profili.

## <a name="enterprise-profile"></a>Profilo enterprise

- **Tipo Wi-Fi**: scegliere **Enterprise**. 

- **Nome Wi-Fi (SSID)** : acronimo di Service Set Identifier, identificatore del set di servizi. Questo valore è il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, tuttavia, gli utenti vedono solo il **nome della connessione** configurata.

- **Nome connessione**: immettere un nome descrittivo per la connessione Wi-Fi. Il testo immesso è il nome che gli utenti vedono quando visualizzano le connessioni disponibili nel dispositivo.

- **Connetti automaticamente quando la rete è disponibile**: se impostata su **Sì**, i dispositivi si connettono automaticamente quando la rete è disponibile. Se impostata su **No**, i dispositivi non si connettono automaticamente.
  - **Connetti alla rete preferita se disponibile**: se per i dispositivi è disponibile una rete preferita, scegliere **Sì** per usare la rete preferita. Scegliere **No** per usare la rete Wi-Fi in questo profilo di configurazione.

    Si supponga ad esempio di creare una rete Wi-Fi **ContosoCorp** e di usare **ContosoCorp** all'interno di questo profilo di configurazione. Nel raggio di copertura è disponibile anche una rete Wi-Fi **ContosoGuest**. Quando si trovano nel raggio di copertura, i dispositivi aziendali devono connettersi automaticamente a **ContosoCorp**. In questo scenario impostare la proprietà **Connetti alla rete preferita se disponibile** su **No**.

  - **Connetti quando la rete non sta trasmettendo il nome (SSID)** : scegliere **Sì** per indicare al profilo di configurazione di connettersi automaticamente alla rete, anche quando la rete è nascosta, ovvero quando il relativo SSID non viene trasmesso pubblicamente. Scegliere **No** se non si vuole che il profilo di configurazione si connetta alla rete nascosta.

- **Limite per la connessione a consumo**: l'amministratore può scegliere come viene misurato il traffico di rete. Le applicazioni possono quindi modificare il comportamento del traffico di rete in base a questa impostazione. Le opzioni disponibili sono:

  - **Senza restrizioni**: impostazione predefinita. La connessione non è a consumo e non sono previste restrizioni sul traffico.
  - **Fisso**: usare questa opzione se la rete è configurata con un limite fisso per il traffico di rete. Quando viene raggiunto questo limite, l'accesso alla rete non viene più consentito.
  - **Variabile**: usare questa opzione se il traffico di rete viene addebitato per byte.

- **Accesso Single Sign-On (SSO)** : consente di configurare l'accesso Single Sign-On (SSO) in cui le credenziali vengono condivise per l'accesso al computer e alla rete Wi-Fi. Le opzioni disponibili sono:
  - **Disabilita**: disabilita il comportamento SSO. L'utente deve eseguire l'autenticazione alla rete separatamente.
  - **Enable before user signs into device** (Abilita prima dell'accesso dell'utente al dispositivo): consente di usare SSO per l'autenticazione in rete prima della procedura di accesso dell'utente.
  - **Enable after user signs into device**: (Abilita dopo l'accesso dell'utente al dispositivo): consente di usare SSO per l'autenticazione in rete dopo il completamento della procedura di accesso dell'utente.
  - **Maximum time to authenticate before timeout** (Tempo massimo per l'autenticazione prima del timeout): immettere il numero massimo di secondi di attesa prima dell'autenticazione in rete, da 1 a 120 secondi.
  - **Allow Windows to prompt user for additional authentication credentials** (Consenti a Windows di chiedere credenziali di autenticazione aggiuntive all'utente): se si sceglie **Sì**, il sistema Windows potrà chiedere credenziali aggiuntive all'utente, se il metodo di autenticazione lo richiede. Scegliere **No** per nascondere questi prompt.

- **Consenti memorizzazione nella cache Pairwise Master Key (PMK)** : selezionare **Sì** per memorizzare nella cache la PMK usata nell'autenticazione. La memorizzazione nella cache in genere consente una procedura di autenticazione in rete più rapida. Scegliere **No** per imporre l'handshake di autenticazione ogni volta che l'utente si connette alla rete Wi-Fi.

  - **Maximum time a PMK is stored in cache** (Tempo massimo di memorizzazione di una PMK nella cache): immettere il numero di minuti di memorizzazione di una PMK (Pairwise Master Key) nella cache, da 5 a 1440 minuti.
  - **Maximum number of PMKs stored in cache** (Numero massimo di PMK memorizzate nella cache): immettere il numero di chiavi memorizzate nella cache, da 1 a 255.

- **Abilita la preautenticazione**: la preautenticazione consente l'autenticazione del profilo presso tutti i punti di accesso alla rete nel profilo prima della connessione. Quando si passa da un punto di accesso a un altro, la preautenticazione riconnette più rapidamente l'utente o i dispositivi. Scegliere **Sì** per consentire l'autenticazione del profilo presso tutti i punti di accesso alla rete inclusi nel raggio di copertura. Scegliere **No** per chiedere all'utente o al dispositivo di eseguire separatamente l'autenticazione a ogni punto di accesso.

  - **Numero massimo tentativi di preautenticazione**: immettere il numero di tentativi di preautenticazione, da 1 a 16.

- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) per autenticare le connessioni wireless protette. Le opzioni disponibili sono:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **PEAP** (Protected EAP)

    **Impostazioni EAP-TLS, EAP-TTLS e PEAP aggiuntive**:
    
    > [!NOTE]
    > Quando si usa un tipo EAP, attualmente sono supportati solo i profili di certificato SCEP. I profili di certificato PKCS non sono supportati. Quando si chiede a un utente di immettere un certificato, assicurarsi di scegliere un certificato SCEP.

    - **Server Trust**  

      **Nomi server di certificazione**: usare con i tipi EAP **EAP-TLS**, **EAP-TTLS** o **PEAP**. Immettere uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Se si immettono queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti quando si connettono alla rete Wi-Fi.  

      **Certificato radice per la convalida server**: usare con i tipi EAP **EAP-TLS**, **EAP-TTLS** o **PEAP**. Scegliere il profilo del certificato radice attendibile usato per autenticare la connessione.  

      **Privacy dell'identità (identità esterna)** : usare con il tipo EAP **PEAP**. Immettere il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.  

    - **Autenticazione client**

      **Certificato client per l'autenticazione client (certificato di identità)** : usare con il tipo EAP **EAP-TLS**. Scegliere il profilo di certificato usato per autenticare la connessione.

      **Metodo di autenticazione**: usare con il tipo EAP **EAP-TTLS**. Selezionare il metodo di autenticazione per la connessione:  

      - **Certificati**: selezionare il certificato client che corrisponde al certificato di identità presentato al server.
      - **Nome utente e password**: immettere un **metodo non EAP (identità interna)** per l'autenticazione. Le opzioni disponibili sono:

        - **Password Authentication Protocol (PAP)**
        - **Challenge Handshake (CHAP)**
        - **Microsoft CHAP (MS-CHAP)**
        - **Microsoft CHAP versione 2 (MS-CHAP v2)**

      **Privacy dell'identità (identità esterna)** : usare con il tipo EAP **EAP-TTLS**. Immettere il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

- **Impostazioni del proxy aziendale**: scegliere questa impostazione per usare le impostazioni proxy all'interno dell'organizzazione. Le opzioni disponibili sono:
  - **Nessuna**: non sono state configurate impostazioni proxy.
  - **Configura manualmente**: immettere l'**indirizzo IP del server proxy** e il relativo **numero di porta**.
  - **Configura automaticamente**: immettere l'URL che punta a uno script di configurazione automatica del proxy. Immettere ad esempio `http://proxy.contoso.com/proxy.pac`.

- **Force Wi-Fi profile to be compliant with the Federal Information Processing Standard (FIPS)** (Forza la conformità del profilo Wi-Fi allo standard FIPS): scegliere **Sì** quando si esegue la convalida basata sullo standard FIPS 140-2. Questo standard è richiesto per tutte le agenzie governative federali degli Stati Uniti che usano sistemi di sicurezza basati su crittografia per proteggere informazioni sensibili ma non classificate archiviate in modalità digitale. Scegliere **No** per non essere conformi a FIPS.

Selezionare **OK** > **Crea** per salvare le modifiche. Il profilo verrà creato e visualizzato nell'elenco dei profili.

## <a name="use-an-imported-settings-file"></a>Usare un file di impostazioni importato

Per le impostazioni non disponibili in Intune, è possibile esportare le impostazioni Wi-Fi da un altro dispositivo Windows. Questa esportazione crea un file XML contenente tutte le impostazioni. Importare quindi il file in Intune e usarlo come profilo Wi-Fi. Vedere [Esportare e importare impostazioni Wi-Fi per i dispositivi Windows](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Passaggi successivi

Il profilo viene creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md).

## <a name="more-resources"></a>Altre risorse

- Visualizzare le impostazioni disponibili per [Windows 8.1](wi-fi-settings-import-windows-8-1.md).
- [Panoramica delle impostazioni Wi-Fi](wi-fi-settings-configure.md), incluse altre piattaforme
