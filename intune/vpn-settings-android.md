---
title: Configurare le impostazioni VPN per dispositivi Android in Microsoft Intune - Azure | Microsoft Docs
description: Per creare un profilo di configurazione VPN per dispositivi Android e Android for Work, immettere il nome della connessione, l'indirizzo IP o il nome di dominio completo del server VPN, scegliere il metodo di autenticazione degli utenti al server VPN e quindi scegliere i tipi di connessione Citrix, SonicWall, Check Point Capsule, Pulse Secure e Microsoft Edge.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5e442ae550d138d532f7a2d8e829c623d09f240a
ms.sourcegitcommit: 9739a9aab032ebb2c4b52ccfb454a9e0f78b2ee4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54751162"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Configurare le impostazioni VPN per i dispositivi che eseguono Android in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono Android.

È possibile configurare le impostazioni VPN per le piattaforme seguenti:

- [Android](#android-vpn-settings)
- [Android Enterprise](#android-enterprise-vpn-settings)

A seconda delle impostazioni scelte, non tutti i valori seguenti sono configurabili.

## <a name="android-vpn-settings"></a>Impostazioni VPN per Android

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano le connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo (FQDN) del server VPN a cui si connetteranno i dispositivi. Ad esempio, immettere **192.168.1.1** o **vpn.contoso.com**.

  - **Metodo di autenticazione**: scegliere il metodo di autenticazione dei dispositivi al server VPN. Le opzioni disponibili sono:

    - **Certificati**: selezionare un profilo di certificato SCEP o PKCS esistente per autenticare la connessione. [Configura certificati](certificates-configure.md) elenca i passaggi necessari per creare un profilo di certificato.
    - **Nome utente e password**: al momento dell'accesso al server VPN, agli utenti finali viene chiesto di immettere un nome utente e una password.

- **Tipo di connessione**: selezionare il tipo di connessione VPN. Le opzioni disponibili sono:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **Impronta digitale** (solo Check Point Capsule VPN): immettere una stringa, ad esempio **Codice impronta digitale Contoso**, per verificare l'attendibilità del server VPN. È possibile inviare un'impronta digitale al client per indicargli di considerare attendibile qualsiasi server con la stessa impronta digitale durante la connessione. Se il dispositivo non è dotato di impronta digitale, chiederà all'utente di considerare attendibile il server VPN mentre visualizza l'impronta digitale. L'utente verifica manualmente l'impronta digitale e sceglie di considerarlo attendibile per connettersi.
- **Immettere le coppie chiave-valore per gli attributi della VPN Citrix** (solo Citrix): immettere le coppie chiave-valore fornite da Citrix. Questi valori configurano le proprietà della connessione VPN.

## <a name="android-enterprise-vpn-settings"></a>Impostazioni VPN per Android Enterprise

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano le connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo (FQDN) del server VPN a cui si connetteranno i dispositivi. Ad esempio, immettere **192.168.1.1** o **vpn.contoso.com**.

  - **Metodo di autenticazione**: scegliere il metodo di autenticazione dei dispositivi al server VPN. Le opzioni disponibili sono:
  
    - **Certificati**: selezionare un profilo di certificato SCEP o PKCS esistente per autenticare la connessione. [Configura certificati](certificates-configure.md) elenca i passaggi necessari per creare un profilo di certificato.
    - **Nome utente e password**: al momento dell'accesso al server VPN, agli utenti finali viene chiesto di immettere un nome utente e una password.

- **Tipo di connessione**: selezionare il tipo di connessione VPN. Le opzioni disponibili sono:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="next-steps"></a>Passaggi successivi
[Profili VPN in Intune](vpn-settings-configure.md)
