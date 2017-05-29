---
title: Impostazioni VPN di Intune per dispositivi Android
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi Android."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16c056ca-320e-4107-ad03-a0cf96c28885
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8c8690b191c7358c8fd60c241177aca1372a8f54
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-android-devices-in-microsoft-intune"></a>Impostazioni VPN per dispositivi Android in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

**Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui sfogliano l'elenco delle connessioni VPN disponibili nel dispositivo.
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

- **Impronta digitale** (solo Check Point Capsule VPN): specificare una stringa, ad esempio "Codice impronta digitale Contoso", che verrà usata per verificare l'attendibilità del server VPN. È possibile inviare un'impronta digitale al client per indicargli di considerare attendibile qualsiasi server che presenta la stessa impronta digitale durante la connessione. Se il dispositivo non ha ancora l'impronta digitale, verrà richiesto all'utente di considerare attendibile il server VPN a cui si sta connettendo e verrà visualizzata l'impronta digitale (l'utente verifica manualmente l'impronta digitale e sceglie Attendibilità per connettersi).
- **Immettere le coppie chiave-valore per gli attributi della VPN Citrix** (solo Citrix): immettere le coppie chiave-valore fornite da Citrix per configurare le proprietà della connessione VPN.

