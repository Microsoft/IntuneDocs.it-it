---
title: Multi-Factor Authentication per le registrazioni di dispositivi Intune
description: Come richiedere l'autenticazione a più fattori in Azure AD per la registrazione del dispositivo.
keywords: ''
author: dougeby
ms.author: angrobe
manager: angerobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 62568a307b5e28c9543a8bb73271da2f55c44ae4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Multi-Factor Authentication per le registrazioni di dispositivi Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune integra l'autenticazione a più fattori (MFA) di Azure AD per la registrazione del dispositivo per consentire di proteggere le risorse aziendali.

L'autenticazione MFA funziona richiedendo due o più dei seguenti metodi di verifica: 

- Un elemento noto (in genere una password o un PIN).
- Un oggetto fisico (un dispositivo attendibile non facile da duplicare, come un telefono).
- Una caratteristica personale (biometria).

L'autenticazione MFA è supportata per iOS, Android, Windows 8.1 o versione successiva o Windows Phone 8.1 o dispositivi successivi.

> [!NOTE]
> Nelle versioni precedenti di Configuration Manager (precedenti alla versione 1610), viene visualizzata l'impostazione relativa all'autenticazione a più fattori nella console di amministrazione. Non tentare di configurare l'autenticazione a più fattori nella console di amministrazione di Configuration Manager in quanto non funzionerà. Configurare l'autenticazione a più fattori come descritto in questo argomento.

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurare Intune per la richiesta dell'autenticazione a più fattori alla registrazione del dispositivo
Per richiedere l'autenticazione MFA quando viene registrato un dispositivo, seguire questa procedura:

1. Accedere al [portale di Microsoft Azure](https://manage.windowsazure.com) con le credenziali di amministratore.
2. Scegliere il tenant.
2. Selezionare la scheda **Applicazioni**. Verrà visualizzato un elenco dei servizi per cui è possibile configurare le funzionalità di sicurezza di Azure AD.
3. Scegliere **Registrazione di Microsoft Intune**.
4. Scegliere **Configura**. 
5. In **autenticazione a più fattori e regole di accesso in base alla località** è possibile:
    
    -  Abilitare le regole di accesso
    -  Scegliere se applicare le regole a tutti gli utenti o a gruppi di sicurezza di Azure AD specifici.
    -  Richiedere l'autenticazione a più fattori per la registrazione di tutti i dispositivi.
    -  Richiedere l'autenticazione a più fattori per la registrazione quando il dispositivo non è in uso.
    -  Scegliere **Block access to corporate resources** (Blocca l'accesso alle risorse aziendali) per impedire la registrazione di un dispositivo quando non è connesso alla rete aziendale. 
4. È inoltre possibile fare clic sul collegamento per **definire/modificare il percorso della rete di lavoro**, per configurare i requisiti di connettività della rete per la registrazione del dispositivo.

> [!IMPORTANT]
> 
> Non configurare le **regole di accesso in base al dispositivo** per la registrazione di Microsoft Intune.
