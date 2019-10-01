---
title: Configurare le impostazioni Wi-Fi per dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Creare o aggiungere un profilo di configurazione Wi-Fi per i dispositivi macOS. Vedere le diverse impostazioni, incluse l'aggiunta di certificati, la scelta di un tipo EAP e la selezione di un metodo di autenticazione in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0692a8ac0bcd1fd415d0bceb7f5a269648dd5b30
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71302572"
---
# <a name="add-wi-fi-settings-for-macos-devices-in-microsoft-intune"></a>Aggiungere le impostazioni Wi-Fi per dispositivi macOS in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile creare un profilo con impostazioni Wi-Fi specifiche e quindi distribuire questo profilo ai dispositivi macOS. Microsoft Intune offre numerose funzionalità, tra cui l'autenticazione in rete, l'aggiunta di un certificato PKS o SCEP e altro ancora.

Queste impostazioni Wi-Fi sono divise in due categorie: impostazioni di base e impostazioni di livello enterprise.

Questo articolo descrive queste impostazioni.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di dispositivo](device-profile-create.md).

> [!NOTE]
> Queste impostazioni sono disponibili per tutti i tipi di registrazione. Per ulteriori informazioni sui tipi di registrazione, vedere la pagina relativa alla [registrazione MacOS](macos-enroll.md).

## <a name="basic-profiles"></a>Profili di base

- **Tipo Wi-Fi**: scegliere **Base**.
- **Nome rete**: immettere un nome per questa connessione Wi-Fi. Questo valore è il nome che gli utenti visualizzano quando sfogliano l'elenco delle connessioni disponibili nel dispositivo.
- **SSID**: acronimo di Service Set Identifier, **identificatore del set di servizi**. Questa proprietà è il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il nome di rete configurato in precedenza.
- **Connetti automaticamente**: scegliere **Abilita** per connettersi automaticamente a questa rete quando il dispositivo è nel campo. Scegliere **Disabilita** per impedire la connessione automatica ai dispositivi.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.
- **Tipo di sicurezza**: selezionare il protocollo di sicurezza per l'autenticazione nella rete Wi-Fi. Le opzioni disponibili sono:

  - **Apri (nessuna autenticazione)** : usare questa opzione solo se la rete non è protetta.
  - **WPA o WPA2 - Personale**: immettere la password in **Chiave precondivisa**. Quando viene configurata la rete dell'organizzazione, viene configurata anche una password o una chiave di rete. Immettere questa password o chiave di rete per il valore di chiave precondivisa.
  - **WEP**

- **Impostazioni proxy**: le opzioni disponibili sono:
  - **Nessuna**: non sono state configurate impostazioni proxy.
  - **Manuale**: immettere l'**Indirizzo server proxy** come indirizzo IP e il relativo **Numero di porta**.
  - **Automatico**: usare un file per configurare il server proxy. Immettere l'**URL del server proxy**, ad esempio `http://proxy.contoso.com`, contenente il file di configurazione.

## <a name="enterprise-profiles"></a>Profili enterprise

- **Tipo Wi-Fi**: scegliere **Enterprise**.
- **SSID**: acronimo di Service Set Identifier, **identificatore del set di servizi**. Questa proprietà è il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il nome di rete configurato in precedenza.
- **Connetti automaticamente**: scegliere **Abilita** per connettersi automaticamente a questa rete quando il dispositivo è nel campo. Scegliere **Disabilita** per impedire la connessione automatica ai dispositivi.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.

- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette. Le opzioni disponibili sono:

  - **EAP-FAST**: immettere le **Impostazioni di PAC (Protected Access Credential)** . Questa opzione usa credenziali di accesso protetto per creare un tunnel autenticato tra il client e il server di autenticazione. Le opzioni disponibili sono:
    - **Non usare (PAC)**
    - **Uso (PAC)** : se esiste un file PAC, usarlo.
    - **Uso e provisioning di PAC**: creare e aggiungere il file PAC ai dispositivi.
    - **Uso e provisioning di PAC in modo anonimo**: creare e aggiungere il file PAC ai dispositivi senza effettuare l'autenticazione nel server.

  - **EAP-SIM**

  - **EAP-TLS**: immettere anche:

    - **Server trust** - **Nomi dei server per certificati**: scegliere **Aggiungi** per aggiungere uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Quando si immettono queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti quando si connettono alla rete Wi-Fi.
    - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client** - **Certificato client per l'autenticazione client (certificato di identità)** : scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

  - **EAP-TTLS**: immettere anche:

    - **Server trust** - **Nomi dei server per certificati**: scegliere **Aggiungi** per aggiungere uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Quando si immettono queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti quando si connettono alla rete Wi-Fi.
    - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP (identità interna)** : scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi.

          Le opzioni disponibili sono: **Password Authentication Protocol (PAP)** , **Challenge Handshake Authentication Protocol (CHAP)** , **Microsoft CHAP (MS-CHAP)** o **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

      - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

  - **LEAP**

  - **PEAP**: immettere anche:

    - **Server trust** - **Nomi dei server per certificati**: scegliere **Aggiungi** per aggiungere uno o più nomi comuni usati nei certificati emessi dall'autorità di certificazione (CA) attendibile. Quando si immettono queste informazioni, è possibile ignorare la finestra di dialogo relativa al trust dinamico visualizzata nei dispositivi degli utenti quando si connettono alla rete Wi-Fi.
    - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. 

      - **Certificati**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

      - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

- **Impostazioni proxy**: le opzioni disponibili sono:
  - **Nessuna**: non sono state configurate impostazioni proxy.
  - **Manuale**: immettere l'**Indirizzo server proxy** come indirizzo IP e il relativo **Numero di porta**.
  - **Automatico**: usare un file per configurare il server proxy. Immettere l'**URL del server proxy**, ad esempio `http://proxy.contoso.com`, contenente il file di configurazione.

## <a name="next-steps"></a>Passaggi successivi

Il profilo viene creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Configurare le impostazioni Wi-Fi nei dispositivi [Android](wi-fi-settings-android.md), [Android Enterprise](wi-fi-settings-android-enterprise.md), [iOS](wi-fi-settings-ios.md)e [Windows 10](wi-fi-settings-windows.md) .
