---
title: "Autenticazione a più fattori per Windows | Microsoft Intune"
description: "Intune integra l'autenticazione a più fattori per consentire di proteggere le risorse aziendali."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0ced62efd04803943cbbfd8cecef907409a03c0b
ms.openlocfilehash: 00d63fa55cd29c938dd082e2eff240f08319e01a


---

# Proteggere i dispositivi Windows con l'autenticazione a più fattori
Microsoft Intune integra l'autenticazione a più fattori per consentire di proteggere le risorse aziendali. Per questo tipo di autenticazione sono necessari altri fattori di autenticazione, ad esempio l'autenticazione di testo, oltre a nomi utente e password. Intune supporta l'uso dell'autenticazione a più fattori durante la registrazione di dispositivi desktop o mobili di Windows 8.1 o versioni successive, Windows Phone 8.1 o Windows 10.

## Requisiti dell'infrastruttura locale per i profili SCEP
Per impostare l'autenticazione a più fattori, è necessario:

-   Registrazione automatica, come descritto in [Configurare la gestione dei dispositivi Windows](set-up-windows-device-management-with-microsoft-intune.md).
-   **Un dominio di Active Directory a cui appartiene il server ADFS.**

-   **Server Directory Federation Services (ADFS) configurato per l'autenticazione a più fattori attivo.** Un server che esegue Windows Server 2012 R2 ed è impostato come server AD FS. Per altre informazioni, vedere [Proteggere le risorse del cloud e locali mediante il server Azure Multi-Factor Authentication con ADFS per Windows Server 2012 R2](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

I server devono soddisfare i requisiti di sistema indicati in [Requisiti di sistema e informazioni sull'installazione per Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx).

 


#### Autenticazione a più fattori con Intune
Se l'organizzazione ha un'infrastruttura IT che include un dominio di Active Directory con Active Directory Federation Services (AD FS), è possibile impostare l'autenticazione a più fattori nel server federativo e quindi abilitare l'autenticazione a più fattori per la registrazione in Intune. Se in Intune viene configurata l'autenticazione a più fattori, gli utenti possono eseguire l'autenticazione una sola volta e quindi usare le risorse aziendali senza ripetere ogni volta il processo di autenticazione a più fattori.

>[!NOTE]
>È possibile abilitare l'autenticazione a più fattori a livello di singolo utente e a livello di gruppo nel server ADFS.  

#### Autenticazione a più fattori senza Intune
Se l'autenticazione a più fattori nel server federativo viene impostata ma non abilitata per la registrazione in Intune, gli utenti dovranno usare l'autenticazione a più fattori tutte le volte che accedono alle risorse aziendali, non solo al momento della registrazione del dispositivo.

È anche possibile usare l'autenticazione a più fattori di Azure Active Directory (Azure AD) per richiedere l'autenticazione a più fattori a livello di singolo utente ogni volta che gli utenti accedono alle risorse aziendali. MFA Azure AD è un servizio cloud che non richiede alcuna infrastruttura IT in locale. Per informazioni sulla configurazione dell'autenticazione a più fattori di Azure AD, vedere [Introduzione ad Azure Multi-Factor Authentication nel cloud](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/).

## Richiedere l'autenticazione a più fattori di AD FS durante la registrazione dei dispositivi Windows
Per informazioni su come abilitare l'autenticazione a più fattori in ADFS, vedere [Gestire i rischi con l'autenticazione a più fattori aggiuntiva per le applicazioni con esigenze particolari](http://technet.microsoft.com/library/dn280949.aspx).

## Impostare l'autenticazione a più fattori per la registrazione dei dispositivi in Intune
>[!Important]  
>Abilitare l'autenticazione a più fattori nell'ambiente tenant o locale di Azure AD prima di richiedere l'autenticazione a più fattori per la registrazione in Intune di dispositivi Windows. In caso contrario, gli utenti ricevono un messaggio di errore se tentano di registrare i propri dispositivi Windows o di collegare questi ultimi ad Azure AD e la registrazione automatica è configurata durante l'aggiunta ad Azure AD.

1.  Nella console di amministrazione di Intune scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Autenticazione a più fattori**.

2.  Scegliere **Configurare l'autenticazione a più fattori** e quindi **Abilita autenticazione a più fattori**.



<!--HONumber=Sep16_HO3-->


