---
title: Impostazioni Wi-Fi per i dispositivi Android Enterprise e i dispositivi in modalità tutto schermo - Microsoft Intune | Microsoft Docs
description: Creare o aggiungere un profilo di configurazione del dispositivo Wi-Fi per dispositivi Android Enterprise e Android in modalità a tutto schermo. Vedere le diverse impostazioni, incluse l'aggiunta di certificati, la scelta di un tipo EAP e la selezione di un metodo di autenticazione in Microsoft Intune. Per i dispositivi in modalità a tutto schermo, immettere anche la chiave precondivisa della rete.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04d35f49f9e07cb72a1fea92210b05e0a95ec256
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390798"
---
# <a name="add-wi-fi-settings-for-android-enterprise-dedicated-and-fully-managed-devices-in-microsoft-intune"></a>Aggiungere le impostazioni Wi-Fi per i dispositivi Android Enterprise dedicati e completamente gestiti in Microsoft Intune

È possibile creare un profilo con impostazioni Wi-Fi specifiche e quindi distribuire questo profilo ai dispositivi Android Enterprise completamente gestiti e dedicati. Microsoft Intune offre numerose funzionalità, tra cui l'autenticazione nella rete, l'uso di una chiave precondivisa e altro ancora.

Questo articolo descrive queste impostazioni. [Usare le impostazioni Wi-Fi nei dispositivi](wi-fi-settings-configure.md) contiene altre informazioni sulla funzionalità Wi-Fi in Microsoft Intune.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di dispositivo](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Solo proprietario del dispositivo

Selezionare questa opzione se si esegue la distribuzione in un dispositivo Android Enterprise dedicato o completamente gestito.  I dispositivi Android Enterprise dedicati e completamente gestiti supportano attualmente la distribuzione del certificato SCEP, ma non PKCS.

### <a name="basic"></a>Basic

- **Tipo Wi-Fi**: scegliere **Base**.
- **Nome rete**: immettere un nome per questa connessione Wi-Fi. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano le connessioni Wi-FI disponibili nel dispositivo. Ad esempio, immettere **Contoso WiFi**.
- **SSID**: immettere l' **identificatore del set di servizi**, ovvero il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il **nome di rete** configurato in precedenza.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.
- **Tipo Wi-Fi**: selezionare il protocollo di sicurezza per l'autenticazione nella rete Wi-Fi. Le opzioni disponibili sono:

  - **Apri (nessuna autenticazione)** : usare questa opzione solo se la rete non è protetta.
  - **WEP - Chiave precondivisa**: immettere la password in **Chiave precondivisa**. Quando viene configurata la rete dell'organizzazione, viene configurata anche una password o una chiave di rete. Immettere questa password o chiave di rete per il valore di chiave precondivisa.
  - **WPA - Chiave precondivisa**: immettere la password in **Chiave precondivisa**. Quando viene configurata la rete dell'organizzazione, viene configurata anche una password o una chiave di rete. Immettere questa password o chiave di rete per il valore di chiave precondivisa.

### <a name="enterprise"></a>Enterprise

- **Tipo Wi-Fi**: scegliere **Enterprise**.
- **SSID**: immettere l' **identificatore del set di servizi**, ovvero il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il **nome di rete** configurato in precedenza.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.
- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette. Le opzioni disponibili sono:

  - **EAP-TLS**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client** - **Certificato client per l'autenticazione client (certificato di identità)** : scegliere il profilo di certificato client SCEP che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

    - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

  - **EAP-TTLS**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP (identità interna)** : scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi. Le opzioni disponibili sono:

          - **Password Authentication Protocol (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

      - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

  - **PEAP**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP per l'autenticazione (identità interna)** : scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi. Le opzioni disponibili sono:

          - **Nessuno**
          - **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

      - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

## <a name="work-profile-only"></a>Solo profilo di lavoro

### <a name="basic"></a>Basic

- **Tipo Wi-Fi**: scegliere **Base**.
- **SSID**: immettere l' **identificatore del set di servizi**, ovvero il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il **nome di rete** configurato in precedenza.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.

### <a name="enterprise"></a>Enterprise

- **Tipo Wi-Fi**: scegliere **Enterprise**.
- **SSID**: immettere l' **identificatore del set di servizi**, ovvero il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il **nome di rete** configurato in precedenza.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.
- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette. Le opzioni disponibili sono:

  - **EAP-TLS**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client** - **Certificato client per l'autenticazione client (certificato di identità)** : scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

    - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

  - **EAP-TTLS**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP (identità interna)** : scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi. Le opzioni disponibili sono:

          - **Password Authentication Protocol (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

      - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

  - **PEAP**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP per l'autenticazione (identità interna)** : scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi. Le opzioni disponibili sono:

          - **Nessuno**
          - **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

      - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

## <a name="next-steps"></a>Passaggi successivi

Il profilo viene creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili Wi-Fi per dispositivi [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [macOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md) e [Windows 8.1](wi-fi-settings-import-windows-8-1.md).
