---
title: Usare impostazioni VPN per dispositivi Android in Microsoft Intune - Azure | Microsoft Docs
description: Vedere tutte le impostazioni per creare connessioni VPN nei dispositivi Android in Microsoft Intune. Immettere il nome della connessione, l'indirizzo IP o il nome di dominio completo del server VPN, scegliere il modo in cui gli utenti eseguono l'autenticazione e scegliere i tipi di connessione Citrix, SonicWall, Check Point capsule e Pulse Secure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d9fefc2413e2dafbf5d0ad67ea15f5f8406cc1c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506550"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Impostazioni del dispositivo Android per configurare la VPN in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo elenca e descrive le diverse impostazioni di connessione VPN che è possibile controllare nei dispositivi Android. Come parte della soluzione di gestione dei dispositivi mobili (MDM), usare queste impostazioni per creare una connessione VPN, scegliere la modalità di autenticazione della VPN, selezionare un tipo di server VPN e altro ancora.

L'amministratore di Intune può creare e assegnare impostazioni VPN a dispositivi Android. 

Per altre informazioni sui profili VPN in Intune, vedere [profili VPN](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](vpn-settings-configure.md#create-a-device-profile) e scegliere **Android**.

## <a name="base-vpn"></a>VPN di base

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano le connessioni VPN disponibili nel dispositivo. Immettere ad esempio `Contoso VPN`.
- **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo (FQDN) del server VPN a cui si connetteranno i dispositivi. Ad esempio, immettere **192.168.1.1** o **vpn.contoso.com**.

  - **Metodo di autenticazione**: scegliere il metodo di autenticazione dei dispositivi al server VPN. Le opzioni disponibili sono:

    - **Certificati**: selezionare un profilo di certificato SCEP o PKCS esistente per autenticare la connessione. [Configura certificati](../protect/certificates-configure.md) elenca i passaggi necessari per creare un profilo di certificato.
    - **Nome utente e password**: al momento dell'accesso al server VPN, agli utenti finali viene chiesto di immettere il nome utente e la password.

- **Tipo di connessione**: selezionare il tipo di connessione VPN. Le opzioni disponibili sono:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **Impronta digitale** (solo Check Point Capsule VPN): immettere una stringa, ad esempio **Codice impronta digitale Contoso**, per verificare l'attendibilità del server VPN. Al client viene inviata un'impronta digitale, in modo che il client sappia di considerare attendibile qualsiasi server con la stessa impronta digitale. Se il dispositivo non è dotato di impronta digitale, chiederà all'utente di considerare attendibile il server VPN mentre visualizza l'impronta digitale. L'utente verifica manualmente l'impronta digitale e sceglie di considerarlo attendibile per connettersi.
- **Immettere le coppie chiave-valore per gli attributi della VPN Citrix** (solo Citrix): immettere le coppie chiave-valore fornite da Citrix. Questi valori configurano le proprietà della connessione VPN. 

  È anche possibile **importare** un file con valori delimitati da virgole (CSV) con coppie di chiavi e valori. Assicurarsi di esaminare i **dati con le intestazioni** e le proprietà **chiave** .

  Dopo aver aggiunto le coppie chiave-valore, usare **Esporta** per eseguire il backup dei dati in un file con estensione CSV.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili VPN per dispositivi [Android Enterprise](vpn-settings-android-enterprise.md), [iOS](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 e versioni successive](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)e [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) .
