---
title: Impostazioni di posta elettronica per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Creare un profilo di posta elettronica di configurazione del dispositivo che usa server Exchange e recupera gli attributi da Azure Active Directory. È anche possibile abilitare SSL, autenticare gli utenti con certificati o nome utente/password e sincronizzare posta elettronica nei dispositivi iOS con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b3aa3e7a4cd79ab990afe7f02a1d6960bc66494a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180188"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>Impostazioni del profilo di posta elettronica per dispositivi iOS - Intune

Usare le impostazioni del profilo di posta elettronica per configurare i dispositivi che eseguono iOS.

> [!IMPORTANT]
> Sono in corso alcuni miglioramenti alla funzionalità S/MIME descritti in questo articolo. Di conseguenza, la funzionalità S/MIME viene temporaneamente rimossa in Intune. Quando questa funzionalità viene rilasciata, questa nota verrà rimossa.

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
- **Metodo di autenticazione**: selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione usato dal profilo di posta elettronica. L'autenticazione a più fattori di Azure non è supportata.
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

- **S/MIME**: selezionare **Abilita S/MIME** per inviare la posta elettronica in uscita usando la firma S/MIME. Quando questa opzione è abilitata, è anche possibile crittografare la posta elettronica per i destinatari che possono ricevere posta elettronica crittografata e decrittografare la posta elettronica ricevuta dai mittenti.
  - Se si seleziona l'opzione **Certificato**, scegliere un profilo certificato PKCS esistente per autenticare la connessione di Exchange e/o crittografare gli scambi di posta elettronica.
- **Numero di messaggi di posta elettronica da sincronizzare**: selezionare il numero di giorni di posta elettronica da sincronizzare. In alternativa, selezionare **Illimitata** per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Consenti di spostare i messaggi negli altri account di posta elettronica**: selezionare **Abilita** per consentire agli utenti di spostare i messaggi di posta elettronica tra diversi account configurati dagli utenti nei dispositivi.
- **Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti**: selezionare **Abilita** per consentire agli utenti di selezionare questo profilo come account predefinito per l'invio di posta elettronica. Ciò consente alle applicazioni di terze parti di aprire i messaggi di posta elettronica nell'app nativa, ad esempio per allegare file ai messaggi.
- **Sincronizza gli indirizzi di posta elettronica usati di recente**: selezionare **Abilita** per consentire agli utenti di sincronizzare con il server l'elenco di indirizzi di posta elettronica usati di recente sul dispositivo.

## <a name="next-steps"></a>Passaggi successivi
[Configurare le impostazioni di posta elettronica in Intune](email-settings-configure.md)
