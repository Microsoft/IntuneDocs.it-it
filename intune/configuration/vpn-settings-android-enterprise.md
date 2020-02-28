---
title: Usare impostazioni VPN per Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Vedere tutte le impostazioni per creare connessioni VPN nei dispositivi Android Enterprise in Microsoft Intune. Immettere il nome della connessione, l'indirizzo IP o il nome di dominio completo del server VPN, scegliere la modalità di autenticazione degli utenti e scegliere i tipi di connessione Citrix, SonicWall, Check Point Capsule e Pulse Secure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81300651355e52f438ea2a314eeb1d0d48e3fcbc
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510865"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Impostazioni del dispositivo Android Enterprise per la configurazione della rete privata virtuale (VPN) in Intune

Questo articolo elenca e descrive le diverse impostazioni di connessione VPN che è possibile controllare nei dispositivi Android Enterprise. Come parte della soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per creare una connessione VPN, scegliere la modalità di autenticazione della VPN, selezionare un tipo di server VPN e altro ancora.

L'amministratore di Intune può creare e assegnare impostazioni VPN a dispositivi Android Enterprise. 

Per altre informazioni sui profili VPN in Intune, vedere [Profili VPN](vpn-settings-configure.md).

> [!NOTE]
> Per configurare una VPN sempre attiva, è necessario creare un profilo VPN e creare anche un profilo di [restrizioni del dispositivo](device-restrictions-android-for-work.md#connectivity) con l'impostazione di VPN sempre attiva configurata.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](vpn-settings-configure.md#create-a-device-profile) e scegliere **Android Enterprise**.

## <a name="device-owner-only"></a>Solo proprietario del dispositivo

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano le connessioni VPN disponibili nel dispositivo. Immettere ad esempio `Contoso VPN`.
- **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo (FQDN) del server VPN a cui si connetteranno i dispositivi. Ad esempio, immettere **192.168.1.1** o **vpn.contoso.com**.

  - **Metodo di autenticazione**: scegliere il metodo di autenticazione dei dispositivi al server VPN. Le opzioni disponibili sono:
  
    - **Certificati**: selezionare un profilo di certificato SCEP o PKCS esistente per autenticare la connessione. [Configura certificati](../protect/certificates-configure.md) elenca i passaggi necessari per creare un profilo di certificato.
    - **Nome utente e password**: al momento dell'accesso al server VPN, agli utenti finali viene chiesto di immettere nome utente e password.

- **Tipo di connessione**: selezionare il tipo di connessione VPN. Le opzioni disponibili sono:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Solo profilo di lavoro

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano le connessioni VPN disponibili nel dispositivo. Immettere ad esempio `Contoso VPN`.
- **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo (FQDN) del server VPN a cui si connetteranno i dispositivi. Ad esempio, immettere **192.168.1.1** o **vpn.contoso.com**.

  - **Metodo di autenticazione**: scegliere il metodo di autenticazione dei dispositivi al server VPN. Le opzioni disponibili sono:
  
    - **Certificati**: selezionare un profilo di certificato SCEP o PKCS esistente per autenticare la connessione. [Configura certificati](../protect/certificates-configure.md) elenca i passaggi necessari per creare un profilo di certificato.
    - **Nome utente e password**: al momento dell'accesso al server VPN, agli utenti finali viene chiesto di immettere nome utente e password.

- **Tipo di connessione**: selezionare il tipo di connessione VPN. Le opzioni disponibili sono:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili VPN per dispositivi [Android](vpn-settings-android.md), [iOS/iPadOS](vpn-settings-ios.md), [macOS](vpn-settings-macos.md), [Windows 10 e versioni successive](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md) e [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md).
