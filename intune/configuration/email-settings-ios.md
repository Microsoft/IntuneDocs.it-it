---
title: Configurare impostazioni di posta elettronica per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Vedere l'elenco di tutte le impostazioni di posta elettronica che è possibile configurare e aggiungere ai dispositivi iOS in Microsoft Intune, incluso l'uso dei server Exchange e il recupero degli attributi da Azure Active Directory. È anche possibile abilitare SSL, autenticare gli utenti con certificati o nome utente/password e sincronizzare posta elettronica nei dispositivi iOS usando i profili di configurazione dispositivo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73de0ac94ff02e43fe73ca6357f6008ba71e3b93
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74390827"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Aggiungere impostazioni di posta elettronica per dispositivi iOS in Microsoft Intune

In Microsoft Intune è possibile creare e configurare la posta elettronica per connettersi a un server di posta elettronica, scegliere come si autenticano gli utenti, usare S/MIME per la crittografia e altro ancora.

Questo articolo elenca e descrive tutte le impostazioni di posta elettronica disponibili per i dispositivi iOS. È possibile creare un profilo di configurazione del dispositivo per eseguire il push o la distribuzione delle impostazioni di posta elettronica nei dispositivi iOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](../email-settings-configure.md).

> [!NOTE]
> Queste impostazioni sono disponibili per tutti i tipi di registrazione. Per altre informazioni sui tipi di registrazione, vedere [registrazione iOS](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Impostazioni account di Exchange ActiveSync

- **Server di posta elettronica**: immettere il nome host del server Exchange.
- **Nome account**: immettere il nome visualizzato per l'account di posta elettronica. Questo nome viene visualizzato nel dispositivo degli utenti.
- **Attributo nome utente da AAD**: questo nome è l'attributo che Intune ottiene da Azure Active Directory (AAD). Intune genera in modo dinamico il nome utente usato da questo profilo. Le opzioni disponibili sono:
  - **Nome dell'entità utente**: ottiene il nome, ad esempio `user1` o `user1@contoso.com`
  - **Indirizzo SMTP primario**: ottiene il nome nel formato dell'indirizzo di posta elettronica, ad esempio `user1@contoso.com`
  - **Nome account SAM**: richiede il dominio, ad esempio `domain\user1`. Specificare anche:  
    - **Origine del nome di dominio utente**: scegliere **AAD** (Azure Active Directory) o **Personalizzato**.
      - **AAD**: ottenere gli attributi da Azure ad. Specificare anche:
        - **Attributo nome di dominio utente da AAD**: scegliere di ottenere l'attributo **Nome completo** (`contoso.com`) o **Nome NetBIOS** (`contoso`) dell'utente.

      - **Personalizzata**: ottenere gli attributi da un nome di dominio personalizzato. Specificare anche:
        - **Nome di dominio personalizzato da usare**: immettere un valore usato da Intune per il nome dominio, ad esempio `contoso.com` o `contoso`.

- **Email address attribute from AAD** (Attributo indirizzo di posta elettronica da AAD): scegliere la modalità di generazione dell'indirizzo di posta elettronica per l'utente. Le opzioni disponibili sono:
  - **Nome dell'entità utente**: usare come indirizzo di posta elettronica il nome dell'entità completo, ad esempio `user1@contoso.com` o `user1`.
  - **Indirizzo SMTP primario**: usare l'indirizzo SMTP primario per accedere a Exchange, ad esempio `user1@contoso.com`.
- **Metodo di autenticazione**: scegliere il modo in cui gli utenti possono eseguire l'autenticazione al server di posta elettronica. Le opzioni disponibili sono:
  - **Certificato**: selezionare un profilo certificato SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange. Questa opzione offre l'esperienza più sicura e trasparente per gli utenti.
  - Nome utente **e password**: agli utenti viene richiesto di immettere il nome utente e la password.
  - **Credenziale derivata**: usare un certificato derivato dalla smart card di un utente. Per altre informazioni, vedere [use derived Credentials in Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > L'autenticazione a più fattori di Azure non è supportata.
  
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

## <a name="exchange-activesync-profile-configuration"></a>Configurazione del profilo di Exchange ActiveSync

> [!IMPORTANT]
> La configurazione di queste impostazioni distribuisce un nuovo profilo al dispositivo, anche quando viene aggiornato un profilo di posta elettronica esistente per includere queste impostazioni. Agli utenti viene richiesto di immettere la password dell'account Exchange ActiveSync. Queste impostazioni hanno effetto quando viene immessa la password.

- **Scambiare dati da sincronizzare**: quando si usa Exchange ActiveSync, scegliere i servizi di Exchange sincronizzati nel dispositivo: calendario, contatti, promemoria, note e indirizzo di posta elettronica. Le opzioni disponibili sono:
  - **Tutti i dati** (impostazione predefinita): la sincronizzazione è abilitata per tutti i servizi.
  - **Solo posta elettronica**: la sincronizzazione è abilitata solo per la posta elettronica. La sincronizzazione è disabilitata per gli altri servizi.
  - **Solo calendario**: la sincronizzazione è abilitata solo per il calendario. La sincronizzazione è disabilitata per gli altri servizi.
  - **Solo calendari e contatti**: la sincronizzazione è abilitata solo per calendario e contatti. La sincronizzazione è disabilitata per gli altri servizi.
  - **Solo contatti**: la sincronizzazione è abilitata solo per i contatti. La sincronizzazione è disabilitata per gli altri servizi.

  Questa funzionalità si applica a:  
  - iOS 13.0 e versioni successive
  - iPadOS 13.0 e versioni successive

- **Consenti agli utenti di modificare le impostazioni di sincronizzazione**: scegliere se gli utenti possono modificare le impostazioni di Exchange ActiveSync per i servizi di Exchange nel dispositivo: calendario, contatti, promemoria, note e indirizzo di posta elettronica. Le opzioni disponibili sono:

  - **Sì** (impostazione predefinita): gli utenti possono modificare il comportamento di sincronizzazione di tutti i servizi. Se **si sceglie Sì** , è possibile apportare modifiche a *tutti i* servizi.
  - **No**: gli utenti non possono modificare le impostazioni di sincronizzazione di tutti i servizi. La scelta di **Nessun** blocco cambia in *tutti i* servizi.

  > [!TIP]
  > Se è stato configurato l'impostazione per sincronizzare i **dati di Exchange** per sincronizzare solo alcuni servizi, è consigliabile selezionare **No** per questa impostazione. La scelta di **No** impedisce agli utenti di modificare il servizio di Exchange sincronizzato.

  Questa funzionalità si applica a:  
  - iOS 13.0 e versioni successive
  - iPadOS 13.0 e versioni successive

## <a name="exchange-activesync-email-settings"></a>Impostazioni di posta elettronica di Exchange ActiveSync

- **S/MIME**: s/MIME USA certificati di posta elettronica che forniscono maggiore sicurezza alle comunicazioni di posta elettronica mediante la firma, la crittografia e la decrittografia. Quando si usa S/MIME con un messaggio di posta elettronica, si conferma l'autenticità del mittente e l'integrità e la riservatezza del messaggio.

  Le opzioni disponibili sono:

  - **Disable s/MIME** (impostazione predefinita): non usa un certificato di posta elettronica s/MIME per firmare, crittografare o decrittografare i messaggi di posta elettronica.
  - **Abilita S/MIME**: consente agli utenti di firmare e/o crittografare la posta elettronica nell'applicazione di posta elettronica nativa di iOS. Specificare anche:

    - **Firma S/MIME abilitata**: **Disabilita** (impostazione predefinita) non consente agli utenti di firmare digitalmente il messaggio. **Abilita** consente agli utenti di firmare digitalmente i messaggi di posta elettronica in uscita per l'account specificato. La firma consente agli utenti che ricevono i messaggi di essere sicuri che il messaggio proveniva da quell'utente specifico e non da qualcuno che fingeva di essere il mittente.
      - **Consenti all'utente di modificare l'impostazione**: **Abilita** consente agli utenti di modificare le opzioni di firma. **Disable** (impostazione predefinita) impedisce agli utenti di modificare la firma e impone agli utenti di usare la firma configurata.
      - **Tipo di certificato di firma**: opzioni:
        - **Non configurato**: Intune non aggiorna o modifica questa impostazione.
        - **None**: un amministratore non impone un certificato specifico. Selezionare questa opzione in modo che gli utenti possano scegliere il proprio certificato.
        - **Credenziale derivata**: usare un certificato derivato dalla smart card di un utente. Per altre informazioni, vedere [use derived Credentials in Microsoft Intune](../protect/derived-credentials.md).
        - **Certificati**: selezionare un profilo certificato PKCS o SCEP usato per firmare i messaggi di posta elettronica.
      - **Consenti all'utente di modificare l'impostazione**: **Abilita** consente agli utenti di modificare il certificato di firma. **Disabilita** (impostazione predefinita) impedisce agli utenti di modificare il certificato di firma e imporre di usare il certificato configurato.

        Questa funzionalità si applica a:  
        - iOS 12 e versioni successive
        - iPadOS 12 e versioni successive

    - **Crittografa per impostazione predefinita**: scegliere **Abilita** per crittografare tutti i messaggi come comportamento predefinito. **Disabilita** (impostazione predefinita) non crittografa tutti i messaggi come comportamento predefinito.
      - **Consenti all'utente di cambiare impostazione**: **Abilita** consente agli utenti di modificare il comportamento di crittografia predefinito. **Disabilita** impedisce agli utenti di modificare il comportamento di crittografia predefinito e impone agli utenti di usare la crittografia configurata.

        Questa funzionalità si applica a:  
        - iOS 12 e versioni successive
        - iPadOS 12 e versioni successive

    - **Force per-message encryption** (Forza crittografia per singoli messaggi): la crittografia per singoli messaggi consente agli utenti di scegliere quali messaggi di posta elettronica crittografare prima dell'invio.

      **Abilita** mostra l'opzione di crittografia per singoli messaggi quando si crea un nuovo messaggio di posta elettronica. Gli utenti possono quindi scegliere se usare o non usare la crittografia per singoli messaggi. Se l'impostazione **Crittografa per impostazione predefinita** è abilitata, abilitando la crittografia per singoli messaggi si consente agli utenti di non usare la crittografia per singoli messaggi.

      **Disabilita** (impostazione predefinita) impedisce agli utenti di visualizzare l'opzione di crittografia per singoli messaggi. Se l'impostazione **Crittografa per impostazione predefinita** è disabilitata, abilitando la crittografia per singoli messaggi si consente agli utenti di usare la crittografia per singoli messaggi.

      - **Tipo di certificato di crittografia**: opzioni:
        - **Non configurato**: Intune non aggiorna o modifica questa impostazione.
        - **None**: un amministratore non impone un certificato specifico. Selezionare questa opzione in modo che gli utenti possano scegliere il proprio certificato.
        - **Credenziale derivata**: usare un certificato derivato dalla smart card di un utente. Per altre informazioni, vedere [use derived Credentials in Microsoft Intune](../protect/derived-credentials.md).
        - **Certificati**: selezionare un profilo certificato PKCS o SCEP usato per firmare i messaggi di posta elettronica.
      - **Consenti all'utente di cambiare impostazione**: **Abilita** consente agli utenti di modificare il certificato di crittografia. **Disabilita** (impostazione predefinita) impedisce agli utenti di modificare il certificato di crittografia e impone agli utenti di usare il certificato configurato.

        Questa funzionalità si applica a:  
        - iOS 12 e versioni successive
        - iPadOS 12 e versioni successive

- **Numero di messaggi di posta elettronica da sincronizzare**: selezionare il numero di giorni di posta elettronica da sincronizzare. In alternativa, selezionare **Illimitata** per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Consenti di spostare i messaggi negli altri account di posta elettronica**: **Abilita** (impostazione predefinita) consente agli utenti di spostare i messaggi di posta elettronica tra diversi account configurati dagli utenti nei dispositivi.
- **Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti**: **Abilita** consente agli utenti di selezionare questo profilo come account predefinito per l'invio di posta elettronica. Ciò consente alle applicazioni di terze parti di aprire i messaggi di posta elettronica nell'app nativa, ad esempio per allegare file ai messaggi.
- **Sincronizza gli indirizzi di posta elettronica usati di recente**: **Abilita** (impostazione predefinita) consente agli utenti di sincronizzare con il server l'elenco di indirizzi di posta elettronica usati di recente sul dispositivo.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](../device-profile-monitor.md).

Configurare le impostazioni di posta elettronica nei dispositivi [Android](../email-settings-android.md), [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md)e [Windows Phone 8,1](email-settings-windows-phone-8-1.md) .
