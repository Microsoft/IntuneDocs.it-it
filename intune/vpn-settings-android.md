---
title: Impostazioni VPN di Microsoft Intune per dispositivi Android
titlesuffix: 
description: "Informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono Android"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fe05b5fdd87e92f5acc35c0a750287f8fd01b92
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Configurare le impostazioni VPN in Microsoft Intune per i dispositivi che eseguono Android 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

È possibile configurare le impostazioni VPN per le piattaforme seguenti:

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

A seconda delle impostazioni scelte, non tutti i valori seguenti sono configurabili.

## <a name="android-vpn-settings"></a>Impostazioni VPN per Android
**Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
- **Metodo di autenticazione**: scegliere tra le seguenti modalità di autenticazione dei dispositivi per il server VPN:
    - **Certificati**: selezionare un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [How to configure certificates](certificates-configure.md)(Come configurare i certificati).
    - **Nome utente e password**: gli utenti finali devono fornire un nome utente e una password per accedere al server VPN.
- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **Impronta digitale** (solo Check Point Capsule VPN): specificare una stringa, ad esempio "Codice impronta digitale Contoso", che viene usata per verificare l'attendibilità del server VPN. È possibile inviare un'impronta digitale al client per indicargli di considerare attendibile qualsiasi server che presenta la stessa impronta digitale durante la connessione. Se il dispositivo non ha ancora l'impronta digitale, viene richiesto all'utente di considerare attendibile il server VPN a cui si sta connettendo e viene visualizzata l'impronta digitale (l'utente verifica manualmente l'impronta digitale e sceglie Attendibilità per connettersi).
- **Immettere le coppie chiave-valore per gli attributi della VPN Citrix** (solo Citrix): immettere le coppie chiave-valore fornite da Citrix per configurare le proprietà della connessione VPN.

## <a name="android-for-work-vpn-settings"></a>Impostazioni VPN per Android for Work

**Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
- **Metodo di autenticazione**: scegliere tra le seguenti modalità di autenticazione dei dispositivi per il server VPN:
    - **Certificati**: selezionare un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [How to configure certificates](certificates-configure.md)(Come configurare i certificati).
    - **Nome utente e password**: gli utenti finali devono fornire un nome utente e una password per accedere al server VPN.
- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

