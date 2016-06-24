---
# required metadata

title: Proteggere i dispositivi Windows con l'autenticazione a più fattori | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteggere i dispositivi Windows con l'autenticazione a più fattori
Microsoft Intune integra l'autenticazione a più fattori per consentire di proteggere le risorse aziendali. Per questo tipo di autenticazione sono necessari altri fattori di autenticazione, ad esempio l'autenticazione di testo, oltre a nomi utente e password. Intune supporta l'uso dell'autenticazione a più fattori durante la registrazione di dispositivi desktop o mobili di Windows 8.1 o versioni successive, Windows Phone 8.1 o Windows 10. 

## Requisiti dell'infrastruttura locale per i profili SCEP
Per impostare l'autenticazione a più fattori, è necessario:

-   **Un dominio di Active Directory a cui appartiene il server ADFS.**

-   **Server Directory Federation Services (ADFS) configurato per l'autenticazione a più fattori attivo.** Un server che esegue Windows Server 2012 R2, impostare come un server ADFS. Per altre informazioni, vedere [Proteggere le risorse del cloud e locali mediante il server Azure Multi-Factor Authentication con ADFS per Windows Server 2012 R2](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

Tutti i server elencati in precedenza devono soddisfare i requisiti di sistema specificati in [Requisiti di sistema e informazioni sull'installazione per Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx)..

#### Autenticazione a più fattori con Intune
Se l'organizzazione ha un'infrastruttura IT che include un dominio di Active Directory con Active Directory Federation Services (ADFS), è possibile configurare l'autenticazione a più fattori nel server federativo e quindi abilitare l'autenticazione a più fattori per la registrazione in Intune. Configurando l'autenticazione a più fattori in Intune, si consente agli utenti di eseguire l'autenticazione una sola volta, durante la registrazione, quindi di accedere alle risorse aziendali senza ripetere ogni volta il processo di autenticazione a più fattori.

>[!NOTE]
>È possibile abilitare l'autenticazione a più fattori a livello di singolo utente e a livello di gruppo nel server ADFS.  

#### Autenticazione a più fattori senza Intune
Se l'autenticazione a più fattori nel server federativo viene configurata ma non abilitata per la registrazione in Intune, gli utenti dovranno usare l'autenticazione a più fattori ogni volta che accedono alle risorse aziendali non solo al momento della registrazione del dispositivo.

È anche possibile usare l'autenticazione a più fattori di Azure Active Directory (AAD) per richiedere l'autenticazione a più fattori ogni volta che gli utenti accedono alle risorse aziendali, a livello di singolo utente. MFA AAD è un cloud servizio che non richiede alcuna infrastruttura IT in locale. Per informazioni sulla configurazione dell'autenticazione a più fattori di AAD, vedere [Introduzione ad Azure Multi-Factor Authentication nel cloud](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/)..

## Richiedere l'autenticazione a più fattori di AD FS durante la registrazione dei dispositivi Windows
Per informazioni su come abilitare l'autenticazione a più fattori in ADFS, vedere [Gestire i rischi con l'autenticazione a più fattori aggiuntiva per le applicazioni con esigenze particolari](http://technet.microsoft.com/library/dn280949.aspx)..

## Impostare l'autenticazione a più fattori per la registrazione dei dispositivi in Intune
>[!Important]  
>Abilitare l'autenticazione a più fattori nell'ambiente tenant o locale di Azure AD prima di richiedere l'autenticazione a più fattori per la registrazione in Intune di dispositivi Windows. In caso contrario, gli utenti riceveranno un messaggio di errore quando tentano di registrare i propri dispositivi Windows o quando tentano di aggiungere i dispositivi ad Azure AD, se è configurata la registrazione automatica durante l'aggiunta ad Azure AD.

1.  Nella console di amministrazione di Intune fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Autenticazione a più fattori**.

2.  Fare clic su **Configura Multi-Factor Authentication** e quindi su **Abilita Multi-Factor Authentication**..



<!--HONumber=May16_HO1-->


