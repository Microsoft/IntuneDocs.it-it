---
title: "Autenticazione a più fattori per Windows | Documentazione Microsoft"
description: "Intune integra l&quot;autenticazione a più fattori per consentire di proteggere le risorse aziendali."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: cc60ffb2cd7a1d0cad141712ba7e2341954b1f02


---

# <a name="protect-windows-devices-with-multi-factor-authentication"></a>Proteggere i dispositivi Windows con l'autenticazione a più fattori

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune integra l'autenticazione a più fattori per consentire di proteggere le risorse aziendali. Per questo tipo di autenticazione sono necessari altri fattori di autenticazione, ad esempio l'autenticazione di testo, oltre a nomi utente e password. Intune supporta l'uso dell'autenticazione a più fattori durante la registrazione di dispositivi desktop o mobili di Windows 8.1 o versioni successive, Windows Phone 8.1 o Windows 10.

>[!NOTE]
>
>È possibile abilitare l'autenticazione a più fattori a livello di singolo utente e a livello di gruppo nel server ADFS.  


## <a name="on-premises-infrastructure-requirements-for-adfs-mfa"></a>Requisiti dell'infrastruttura locale per i profili SCEP
Per impostare l'autenticazione a più fattori, è necessario:

-   Registrazione automatica, come descritto in [Configurare la gestione dei dispositivi Windows](set-up-windows-device-management-with-microsoft-intune.md).
-   **Un dominio di Active Directory a cui appartiene il server AD FS.**

-   **Server Active Directory Federation Services (AD FS) configurato per l'autenticazione a più fattori (MFA).** Un server che esegue Windows Server 2012 R2 ed è impostato come server AD FS. Per altre informazioni, vedere [Proteggere le risorse del cloud e locali mediante il server Azure Multi-Factor Authentication con ADFS per Windows Server 2012 R2](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

I server devono soddisfare i requisiti di sistema indicati in [Requisiti di sistema e informazioni sull'installazione per Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx).

 


#### <a name="mfa-with-intune"></a>Autenticazione a più fattori con Intune
Se l'organizzazione ha un'infrastruttura IT che include un dominio di Active Directory con Active Directory Federation Services (AD FS), è possibile impostare l'autenticazione a più fattori nel server federativo e quindi abilitare l'autenticazione a più fattori per la registrazione in Intune. Se in Intune viene configurata l'autenticazione a più fattori, gli utenti possono eseguire l'autenticazione una sola volta e quindi usare le risorse aziendali senza ripetere ogni volta il processo di autenticazione a più fattori.

>[!NOTE]
>
>È possibile abilitare l'autenticazione a più fattori a livello di singolo utente e a livello di gruppo nel server ADFS.  

#### <a name="mfa-without-intune"></a>Autenticazione a più fattori senza Intune
Se l'autenticazione a più fattori nel server federativo viene impostata ma non abilitata per la registrazione in Intune, gli utenti dovranno usare l'autenticazione a più fattori tutte le volte che accedono alle risorse aziendali, non solo al momento della registrazione del dispositivo.

È anche possibile usare l'autenticazione a più fattori di Azure Active Directory (Azure AD) per richiedere l'autenticazione a più fattori a livello di singolo utente ogni volta che gli utenti accedono alle risorse aziendali. MFA Azure AD è un servizio cloud che non richiede alcuna infrastruttura IT in locale. Per informazioni sulla configurazione dell'autenticazione a più fattori di Azure AD, vedere [Introduzione ad Azure Multi-Factor Authentication nel cloud](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/).

## <a name="requiring-adfs-mfa-during-enrollment-of-windows-devices"></a>Richiedere l'autenticazione a più fattori di AD FS durante la registrazione dei dispositivi Windows
Per informazioni su come abilitare l'autenticazione a più fattori in ADFS, vedere [Gestire i rischi con l'autenticazione a più fattori aggiuntiva per le applicazioni con esigenze particolari](http://technet.microsoft.com/library/dn280949.aspx).

## <a name="set-up-device-enrollment-mfa-in-intune"></a>Impostare l'autenticazione a più fattori per la registrazione dei dispositivi in Intune
>[!Important]  
>Abilitare l'autenticazione a più fattori nell'ambiente tenant o locale di Azure AD prima di richiedere l'autenticazione a più fattori per la registrazione in Intune di dispositivi Windows. In caso contrario, gli utenti ricevono un messaggio di errore se tentano di registrare i propri dispositivi Windows o di collegare questi ultimi ad Azure AD e la registrazione automatica è configurata durante l'aggiunta ad Azure AD.

1.  Nella console di amministrazione di Intune scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Autenticazione a più fattori**.

2.  Scegliere **Configurare l'autenticazione a più fattori** e quindi **Abilita autenticazione a più fattori**.



<!--HONumber=Dec16_HO5-->


