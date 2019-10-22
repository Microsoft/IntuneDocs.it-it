---
title: Configurare impostazioni di posta elettronica per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Vedere l'elenco di tutte le impostazioni di posta elettronica che è possibile configurare e aggiungere ai dispositivi iOS in Microsoft Intune, incluso l'uso dei server Exchange e il recupero degli attributi da Azure Active Directory. È anche possibile abilitare SSL, autenticare gli utenti con certificati o nome utente/password e sincronizzare posta elettronica nei dispositivi iOS usando i profili di configurazione dispositivo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cbf9c29a1e694726b1b42f7072eea859f812751
ms.sourcegitcommit: 8c25aeefb7cbc6444a8596af22fccd1c5426877a
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72593805"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Aggiungere impostazioni di posta elettronica per dispositivi iOS in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In Microsoft Intune è possibile creare e configurare la posta elettronica per connettersi a un server di posta elettronica, scegliere come si autenticano gli utenti, usare S/MIME per la crittografia e altro ancora.

Questo articolo elenca e descrive tutte le impostazioni di posta elettronica disponibili per i dispositivi iOS. È possibile creare un profilo di configurazione del dispositivo per eseguire il push o la distribuzione delle impostazioni di posta elettronica nei dispositivi iOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](../email-settings-configure.md).

> [!NOTE]
> Queste impostazioni sono disponibili per tutti i tipi di registrazione. Per altre informazioni sui tipi di registrazione, vedere [registrazione iOS](../ios-enroll.md).

## <a name="email-settings"></a>Impostazioni di posta elettronica

- **Server di posta elettronica**: immettere il nome host del server Exchange.
- **Nome account**: immettere il nome visualizzato per l'account di posta elettronica. Questo nome viene visualizzato nel dispositivo degli utenti.
- **Attributo nome utente da AAD**: questo nome è l'attributo che Intune ottiene da Azure Active Directory (AAD). Intune genera in modo dinamico il nome utente usato da questo profilo. Le opzioni disponibili sono:
  - **Nome dell'entità utente**: ottiene il nome, ad esempio `user1` o `user1@contoso.com`
  - **Indirizzo SMTP primario**: ottiene il nome nel formato dell'indirizzo di posta elettronica, ad esempio `user1@contoso.com`
  - **Nome account SAM**: richiede il dominio, ad esempio `domain\user1`.

    Specificare anche:  
    - **Origine del nome di dominio utente**: scegliere **AAD** (Azure Active Directory) o **Personalizzato**.

      Quando si sceglie di ottenere gli attributi da **AAD**, specificare:
      - **Attributo nome di dominio utente da AAD**: scegliere di ottenere l'attributo **Nome completo** o **Nome NetBIOS** dell'utente

      Quando si sceglie di usare attributi di tipo **Personalizzato**, specificare:
      - **Nome di dominio personalizzato da usare**: immettere un valore usato da Intune per il nome dominio, ad esempio `contoso.com` o `contoso`

- **Email address attribute from AAD** (Attributo indirizzo di posta elettronica da AAD): scegliere la modalità di generazione dell'indirizzo di posta elettronica per l'utente. Selezionare **Nome dell'entità utente** (`user1@contoso.com` o `user1`) per usare il nome dell'entità utente completo come indirizzo di posta elettronica. Selezionare **Indirizzo SMTP primario** (`user1@contoso.com`) per usare l'indirizzo SMTP primario per accedere a Exchange.
- **Metodo di autenticazione**: selezionare **Nome utente e password**, **Certificati** o **Credenziale derivata** come metodo di autenticazione usato dal profilo di posta elettronica. L'autenticazione a più fattori di Azure non è supportata.
  - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza che viene usato per autenticare la connessione di Exchange.
- **SSL**: selezionare **Abilita** per usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **OAuth**: selezionare **Abilita** per usare la comunicazione Open Authorization (OAuth) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con Exchange. Se il server OAuth usa l'autenticazione del certificato, scegliere **Certificato** come **Metodo di autenticazione** e includere il certificato con il profilo. In caso contrario scegliere **Nome utente e password** come **Metodo di autenticazione**. Quando si usa OAuth, verificare quanto segue.

  - Verificare che la soluzione di posta elettronica supporti OAuth prima di destinare questo profilo agli utenti. Office 365 Exchange Online supporta OAuth. Exchange locale e altre soluzioni partner o di terze parti potrebbero non supportare OAuth. Exchange locale può essere configurato per l'autenticazione moderna (vedere il post di blog [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) (Presentazione dell'autenticazione moderna ibrida per Exchange locale)).

    Se il profilo di posta elettronica usa Oauth e il servizio di posta elettronica non la supporta, l'opzione **Reimmettere la password** non funziona. Ad esempio, non accade nulla quando l'utente sceglie **Reimmettere la password** nelle impostazioni del dispositivo Apple.

  - Quando OAuth è abilitata, gli utenti finali hanno un'esperienza di accesso alla posta elettronica con l'autenticazione moderna diversa che supporta l'autenticazione a più fattori (MFA). 

  - Alcune organizzazioni disabilitano la possibilità dell'utente finale di eseguire l'[accesso all'applicazione self-service](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). In questo scenario, l'accesso con l'autenticazione moderna potrebbe non riuscire finché un amministratore non crea l'app aziendale "Account iOS" e concede agli utenti l'accesso all'app in Azure AD.

    L'azione predefinita consiste nell'aggiungere un'applicazione che usa la funzionalità **Aggiungi app** del [portale delle app personali](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **senza l'approvazione aziendale**. Per altre informazioni, vedere [Come assegnare gli utenti alle applicazioni](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Quando si abilita OAuth, si verifica quanto segue:  
  > 1. Viene rilasciato un nuovo profilo ai dispositivi già specificati come destinazione.
  > 2. Agli utenti finali viene chiesto di specificare nuovamente le credenziali.

- **S/MIME**: selezionare **Abilita S/MIME** per consentire agli utenti di firmare e/o crittografare la posta elettronica nell'applicazione di posta elettronica nativa di iOS. 

  Quando si usa S/MIME con un messaggio di posta elettronica, si conferma l'autenticità del mittente e l'integrità e la riservatezza del messaggio.

  - **Firma S/MIME abilitata**: selezionare **Abilita** per consentire agli utenti di firmare digitalmente i messaggi di posta elettronica in uscita per l'account immesso. La firma consente agli utenti che ricevono i messaggi di essere sicuri che il messaggio proveniva da quell'utente specifico e non da qualcuno che fingeva di essere il mittente. Selezionare **Disabilita** per non consentire agli utenti di firmare digitalmente il messaggio.
    - **Consenti all'utente di cambiare impostazione**: scegliere **Abilita** per consentire agli utenti di modificare il comportamento di firma S/MIME. Selezionare **Disabilita** per impedire agli utenti di modificare l'impostazione della firma S/MIME configurata. Disponibile in iOS 12 e versioni successive.

  - **Certificato di firma S/MIME**: selezionare un profilo esistente del certificato PKCS o SCEP usato per firmare i messaggi di posta elettronica.
    - **Consenti all'utente di cambiare impostazione**: scegliere **Abilita** per consentire agli utenti di modificare il certificato di firma. Selezionare **Disabilita** per impedire agli utenti di modificare il certificato di firma e imporre di usare il certificato configurato. Disponibile in iOS 12 e versioni successive.

  - **Crittografa per impostazione predefinita**: scegliere **Abilita** per crittografare tutti i messaggi come comportamento predefinito. Selezionare **Disabilita** per non crittografare tutti i messaggi come comportamento predefinito.
    - **Consenti all'utente di cambiare impostazione**: scegliere **Abilita** per consentire agli utenti di modificare il comportamento di crittografia predefinito. Selezionare **Disabilita** per impedire agli utenti di modificare il comportamento di crittografia predefinito e imporre agli utenti di usare l'impostazione configurata. Disponibile in iOS 12 e versioni successive.

  - **Force per-message encryption** (Forza crittografia per singoli messaggi): la crittografia per singoli messaggi consente agli utenti di scegliere quali messaggi di posta elettronica crittografare prima dell'invio. Selezionare **Abilita** per mostrare l'opzione di crittografia per singoli messaggi quando si crea un nuovo messaggio di posta elettronica. Gli utenti possono quindi scegliere se usare o non usare la crittografia per singoli messaggi. Selezionare **Disabilita** per impedire agli utenti di visualizzare l'opzione di crittografia per singoli messaggi.

    Se l'impostazione **Encrypt by default** (Crittografa per impostazione predefinita) è abilitata, abilitando la crittografia per singoli messaggi si consente agli utenti di non usare la crittografia per singoli messaggi. Se l'impostazione **Encrypt by default** (Crittografa per impostazione predefinita) è disabilitata, abilitando la crittografia per singoli messaggi si consente agli utenti di usare la crittografia per singoli messaggi.

  - **Certificato di crittografia S/MIME**: selezionare un profilo esistente del certificato PKCS o SCEP usato per crittografare i messaggi di posta elettronica.
    - **Consenti all'utente di cambiare impostazione**: scegliere **Abilita** per consentire agli utenti di modificare il certificato di crittografia. Selezionare **Disabilita** per impedire agli utenti di modificare il certificato di crittografia e imporre agli utenti di usare il certificato configurato. Disponibile in iOS 12 e versioni successive.
- **Numero di messaggi di posta elettronica da sincronizzare**: selezionare il numero di giorni di posta elettronica da sincronizzare. In alternativa, selezionare **Illimitata** per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Consenti di spostare i messaggi negli altri account di posta elettronica**: selezionare **Abilita** per consentire agli utenti di spostare i messaggi di posta elettronica tra diversi account configurati dagli utenti nei dispositivi.
- **Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti**: selezionare **Abilita** per consentire agli utenti di selezionare questo profilo come account predefinito per l'invio di posta elettronica. Ciò consente alle applicazioni di terze parti di aprire i messaggi di posta elettronica nell'app nativa, ad esempio per allegare file ai messaggi.
- **Sincronizza gli indirizzi di posta elettronica usati di recente**: selezionare **Abilita** per consentire agli utenti di sincronizzare con il server l'elenco di indirizzi di posta elettronica usati di recente sul dispositivo.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](../device-profile-monitor.md).

Configurare le impostazioni di posta elettronica nei dispositivi [Android](../email-settings-android.md), [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md)e [Windows Phone 8,1](email-settings-windows-phone-8-1.md) .
