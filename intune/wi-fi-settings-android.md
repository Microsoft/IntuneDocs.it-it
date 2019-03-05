---
title: Configurare le impostazioni Wi-Fi per dispositivi Android in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Creare o aggiungere un profilo di configurazione Wi-Fi per i dispositivi Android. Vedere le diverse impostazioni, incluse l'aggiunta di certificati, la scelta di un tipo EAP e la selezione di un metodo di autenticazione in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d199256d77f19655d8d3e78c545ab1f236021d0
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236864"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Aggiungere le impostazioni Wi-Fi per i dispositivi che eseguono Android in Microsoft Intune

È possibile creare un profilo con impostazioni Wi-Fi specifiche e quindi distribuire questo profilo ai dispositivi Android. Microsoft Intune offre numerose funzionalità, tra cui l'autenticazione in rete, l'aggiunta di un certificato PKS o SCEP e altro ancora.

Queste impostazioni Wi-Fi sono suddivise in due categorie: impostazioni di base e impostazioni di livello enterprise.

Questo articolo descrive queste impostazioni.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di dispositivo](device-profile-create.md).

## <a name="basic-profile"></a>Profilo di base

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

- [Panoramica delle impostazioni Wi-Fi](wi-fi-settings-configure.md), incluse altre piattaforme.

- Se si usano dispositivi Android Enterprise o Android in modalità tutto schermo, vedere le [impostazioni Wi-Fi per i dispositivi che eseguono Android Enterprise e Android in modalità tutto schermo](wi-fi-settings-android-enterprise.md).
