---
title: "Autenticazione a più fattori con Azure AD| Documentazione Microsoft"
description: "Come richiedere l&quot;autenticazione a più fattori in Azure AD per la registrazione del dispositivo."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 12/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: 
translationtype: Human Translation
ms.sourcegitcommit: 85462d6cb5e3dc6ce8e94fe8fd1bc1c1c2b6e4f3
ms.openlocfilehash: 6e20eca60886781ae884107a224245639c5f107c


---

# <a name="multi-factor-authentication-for-microsoft-intune"></a>Autenticazione a più fattori per Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune integra l'autenticazione a più fattori (MFA) di Azure AD per la registrazione del dispositivo per consentire di proteggere le risorse aziendali. Per questo tipo di autenticazione sono necessari altri fattori di autenticazione, ad esempio l'autenticazione di testo, oltre a nomi utente e password. Tale autenticazione è supportata per iOS, Android, Windows 8.1 o versione successiva o Windows Phone 8.1 o dispositivi successivi.

> [!NOTE]
>
> Questa è la nuova esperienza per MFA in Intune. L'esperienza precedente, da cui viene eseguita la migrazione dei clienti, è descritta in [Proteggere i dispositivi Windows con l'autenticazione a più fattori](protect-windows-devices-with-multi-factor-authentication.md).
>
> Nelle versioni precedenti di Configuration Manager (precedenti alla versione 1610), viene visualizzata l'impostazione relativa all'autenticazione a più fattori nella console di amministrazione. Non tentare di configurare l'autenticazione a più fattori nella console di amministrazione di Configuration Manager in quanto non funzionerà. Configurare l'autenticazione a più fattori come descritto in questo argomento.

### <a name="configuring-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurare Intune per la richiesta dell'autenticazione a più fattori alla registrazione del dispositivo
Per richiedere l'autenticazione a più fattori alla registrazione del dispositivo, seguire questa procedura:

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



<!--HONumber=Dec16_HO3-->


