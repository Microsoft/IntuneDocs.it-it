---
title: Impostazioni Wi-Fi per i dispositivi Android Enterprise e i dispositivi in modalità tutto schermo - Microsoft Intune | Microsoft Docs
description: Creare o aggiungere un profilo di configurazione del dispositivo Wi-Fi per dispositivi Android Enterprise e Android in modalità a tutto schermo. Vedere le diverse impostazioni, incluse l'aggiunta di certificati, la scelta di un tipo EAP e la selezione di un metodo di autenticazione in Microsoft Intune. Per i dispositivi in modalità a tutto schermo, immettere anche la chiave precondivisa della rete.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1589189147fd034a034791c2090c2a78134d866e
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050592"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Aggiungere le impostazioni Wi-Fi per i dispositivi che eseguono Android Enterprise e i dispositivi Android in modalità tutto schermo in Microsoft Intune

È possibile creare un profilo con impostazioni Wi-Fi specifiche e quindi distribuire questo profilo ai dispositivi Android Enterprise e Android in modalità tutto schermo. Microsoft Intune offre numerose funzionalità, tra cui l'autenticazione nella rete, l'uso di una chiave precondivisa e altro ancora.

Questo articolo descrive queste impostazioni. [Usare le impostazioni Wi-Fi nei dispositivi](wi-fi-settings-configure.md) contiene altre informazioni sulla funzionalità Wi-Fi in Microsoft Intune.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di dispositivo](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only---kiosk"></a>Solo proprietario del dispositivo - Modalità tutto schermo

Selezionare questa opzione se si usa un dispositivo Android Enterprise in modalità tutto schermo.

- **Nome rete**: immettere un nome per questa connessione Wi-Fi. Questo valore è il nome che gli utenti visualizzano quando sfogliano l'elenco delle connessioni disponibili nel dispositivo.
- **SSID**: acronimo di Service Set Identifier, **identificatore del set di servizi**. Questa impostazione è il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il **nome di rete** configurato in precedenza.
- **Connetti automaticamente**: scegliere **Abilita** per connettersi automaticamente a questa rete quando il dispositivo è nel campo. Scegliere **Disabilita** per impedire la connessione automatica ai dispositivi.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.
- **Tipo Wi-Fi**: selezionare il protocollo di sicurezza per l'autenticazione nella rete Wi-Fi. Le opzioni disponibili sono:

  - **Apri (nessuna autenticazione)** : usare questa opzione solo se la rete non è protetta.
  - **WEP - Chiave precondivisa**: immettere la password in **Chiave precondivisa**. Quando viene configurata la rete dell'organizzazione, viene configurata anche una password o una chiave di rete. Immettere questa password o chiave di rete per il valore di chiave precondivisa.
  - **WPA - Chiave precondivisa**: immettere la password in **Chiave precondivisa**. Quando viene configurata la rete dell'organizzazione, viene configurata anche una password o una chiave di rete. Immettere questa password o chiave di rete per il valore di chiave precondivisa.

Selezionare **OK** per salvare le modifiche.

## <a name="work-profile-only"></a>Solo profilo di lavoro

### <a name="basic-settings"></a>Impostazioni di base

- **Tipo Wi-Fi**: scegliere **Base**.
- **SSID**: acronimo di Service Set Identifier, **identificatore del set di servizi**. Questa impostazione è il nome reale della rete wireless a cui si connettono i dispositivi.
- **Connetti automaticamente**: scegliere **Abilita** per connettersi automaticamente a questa rete quando il dispositivo è nel campo. Scegliere **Disabilita** per impedire la connessione automatica ai dispositivi.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.

## <a name="enterprise-profile"></a>Profilo enterprise

- **Tipo Wi-Fi**: scegliere **Enterprise**.
- **SSID**: acronimo di Service Set Identifier, **identificatore del set di servizi**. Questa impostazione è il nome reale della rete wireless a cui si connettono i dispositivi.
- **Connetti automaticamente**: scegliere **Abilita** per connettersi automaticamente a questa rete quando il dispositivo è nel campo. Scegliere **Disabilita** per impedire la connessione automatica ai dispositivi.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.
- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette. Le opzioni disponibili sono: 

  - **EAP-TLS**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

      Selezionare **OK** per salvare le modifiche.

    - **Autenticazione client** - **Certificato client per l'autenticazione client (certificato di identità)** : scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

      Selezionare **OK** per salvare le modifiche.

  - **EAP-TTLS**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

      Selezionare **OK** per salvare le modifiche.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP (identità interna)** : scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi.

          Le opzioni disponibili sono: **Password Authentication Protocol (PAP)** , **Challenge Handshake Authentication Protocol (CHAP)** , **Microsoft CHAP (MS-CHAP)** o **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

        Selezionare **OK** per salvare le modifiche.

      - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

  - **PEAP**: immettere anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo di certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

      Selezionare **OK** per salvare le modifiche.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP per l'autenticazione (identità interna)** : scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi.

          Le opzioni disponibili: **Nessuno** o **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

        Selezionare **OK** per salvare le modifiche.

      - **Privacy dell'identità (identità esterna)** : immettere il testo inviato nella risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

Selezionare **OK** > **Crea** per salvare le modifiche. Il profilo verrà creato e visualizzato nell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Il profilo viene creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili Wi-Fi per dispositivi [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [macOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md) e [Windows 8.1](wi-fi-settings-import-windows-8-1.md).
