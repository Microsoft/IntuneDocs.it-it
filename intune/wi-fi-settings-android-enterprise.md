---
title: Impostazioni Wi-Fi per dispositivi Android Enterprise e in modalità tutto schermo
titleSuffix: Microsoft Intune
description: Creare o aggiungere un profilo di configurazione del dispositivo Wi-Fi per dispositivi Android Enterprise e Android in modalità a tutto schermo. Vedere le diverse impostazioni, incluse l'aggiunta di certificati, la scelta di un tipo EAP e la selezione di un metodo di autenticazione in Microsoft Intune. Per i dispositivi in modalità a tutto schermo, immettere anche la chiave precondivisa della rete.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 1424cd43c6ccde17724a4165fe74def4da291e29
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112358"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Aggiungere le impostazioni Wi-Fi per i dispositivi che eseguono Android Enterprise e i dispositivi Android in modalità tutto schermo in Microsoft Intune

È possibile creare un profilo con impostazioni Wi-Fi specifiche e quindi distribuire questo profilo ai dispositivi Android Enterprise e Android in modalità tutto schermo. Microsoft Intune offre numerose funzionalità, tra cui l'autenticazione nella rete, l'uso di una chiave precondivisa e altro ancora.

Questo articolo descrive queste impostazioni.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di dispositivo](device-profile-create.md).

## <a name="device-owner-only---kiosk"></a>Solo proprietario del dispositivo - Modalità tutto schermo

Selezionare questa opzione se si usa un dispositivo Android Enterprise in modalità tutto schermo.

- **Nome rete**: immettere un nome per questa connessione Wi-Fi. Questo valore è il nome che gli utenti visualizzano quando sfogliano l'elenco delle connessioni disponibili nel dispositivo.
- **SSID**: acronimo di **Service Set Identifier**, identificatore del set di servizi. Questa impostazione è il nome reale della rete wireless a cui si connettono i dispositivi. Quando scelgono la connessione, gli utenti, tuttavia, visualizzano solo il **nome di rete** configurato in precedenza.
- **Connetti automaticamente**: scegliere **Abilita** per connettersi automaticamente a questa rete quando il dispositivo è nel campo. Scegliere **Disabilita** per impedire la connessione automatica ai dispositivi.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.
- **Tipo Wi-Fi**: selezionare il protocollo di sicurezza per l'autenticazione nella rete Wi-Fi. Le opzioni disponibili sono:

  - **Apri (nessuna autenticazione)**: usare questa opzione solo se la rete non è protetta.
  - **WEP - Chiave precondivisa**: immettere la password in **Chiave precondivisa**. Quando viene configurata la rete dell'organizzazione, viene configurata anche una password o una chiave di rete. Immettere questa password o chiave di rete per il valore di chiave precondivisa.
  - **WPA - Chiave precondivisa**: immettere la password in **Chiave precondivisa**. Quando viene configurata la rete dell'organizzazione, viene configurata anche una password o una chiave di rete. Immettere questa password o chiave di rete per il valore di chiave precondivisa.

Selezionare **OK** per salvare le modifiche.

## <a name="work-profile-only"></a>Solo profilo di lavoro

### <a name="basic-settings"></a>Impostazioni di base

- **Tipo Wi-Fi**: Scegliere **Basic**.
- **SSID**: acronimo di **Service Set Identifier**, identificatore del set di servizi. Questa impostazione è il nome reale della rete wireless a cui si connettono i dispositivi.
- **Connetti automaticamente**: scegliere **Abilita** per connettersi automaticamente a questa rete quando il dispositivo è nel campo. Scegliere **Disabilita** per impedire la connessione automatica ai dispositivi.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.

## <a name="enterprise-profile"></a>Profilo enterprise

- **Tipo Wi-Fi**: scegliere **Enterprise**.
- **SSID**: acronimo di **Service Set Identifier**, identificatore del set di servizi. Questa impostazione è il nome reale della rete wireless a cui si connettono i dispositivi.
- **Connetti automaticamente**: scegliere **Abilita** per connettersi automaticamente a questa rete quando il dispositivo è nel campo. Scegliere **Disabilita** per impedire la connessione automatica ai dispositivi.
- **Rete nascosta**: scegliere **Abilita** per nascondere questa rete dall'elenco delle reti disponibili nel dispositivo. L'identificatore SSID non viene trasmesso. Scegliere **Disabilita** per visualizzare questa rete nell'elenco delle reti disponibili nel dispositivo.
- **Tipo EAP**: scegliere il tipo di protocollo EAP (Extensible Authentication Protocol) usato per autenticare le connessioni wireless protette. Le opzioni disponibili sono: 

  - **EAP-TLS**: Specificare anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo del certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

      Selezionare **OK** per salvare le modifiche.

    - **Autenticazione client** - **Certificato client per l'autenticazione client (certificato di identità)**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

      Selezionare **OK** per salvare le modifiche.

  - **EAP-TTLS**: Specificare anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo del certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

      Selezionare **OK** per salvare le modifiche.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP (identità interna)**: scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi.

          Le opzioni disponibili sono: **Password Authentication Protocol (PAP)**, **Challenge Handshake Authentication Protocol (CHAP)**, **Microsoft CHAP (MS-CHAP)** o **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

        Selezionare **OK** per salvare le modifiche.

      - **Privacy dell'identità (identità esterna)**: immettere il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

  - **PEAP**: Specificare anche:

    - **Server trust** - **Certificato radice per la convalida server**: scegliere un profilo del certificato radice attendibile esistente. Questo certificato viene presentato al server quando il client si connette alla rete e viene usato per autenticare la connessione.

      Selezionare **OK** per salvare le modifiche.

    - **Autenticazione client**: scegliere un **metodo di autenticazione**. Le opzioni disponibili sono:

      - **Nome utente e password**: richiedere all'utente di specificare nome utente e password per autenticare la connessione. Specificare anche:
        - **Metodo non EAP per l'autenticazione (identità interna)**: scegliere la modalità di autenticazione della connessione. Assicurarsi di scegliere lo stesso protocollo configurato nella rete Wi-Fi.

          Le opzioni disponibili sono: **Nessuno** o **Microsoft CHAP versione 2 (MS-CHAP v2)**

      - **Certificati**: scegliere il profilo di certificato client SCEP o PKCS che viene distribuito nel dispositivo. Questo certificato corrisponde all'identità presentata dal dispositivo al server per autenticare la connessione.

        Selezionare **OK** per salvare le modifiche.

      - **Privacy dell'identità (identità esterna)**: immettere il testo inviato in risposta a una richiesta di identità EAP. Questo testo può essere costituito da qualsiasi valore, ad esempio `anonymous`. Durante l'autenticazione, viene inviata inizialmente questa identità anonima, seguita da quella effettiva inviata tramite un tunnel sicuro.

Selezionare **OK** > **Crea** per salvare le modifiche. Il profilo verrà creato e visualizzato nell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Il profilo viene creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md).

## <a name="more-resources"></a>Altre risorse

- Vedere le impostazioni disponibili per i dispositivi Android in [Configurare le impostazioni Wi-Fi per dispositivi Android in Microsoft Intune](wi-fi-settings-android.md).
- [Panoramica delle impostazioni Wi-Fi](wi-fi-settings-configure.md), incluse altre piattaforme.