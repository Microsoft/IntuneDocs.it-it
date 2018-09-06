---
title: Impostazioni di posta elettronica per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Creare un profilo di posta elettronica di configurazione del dispositivo che usa server Exchange e recupera gli attributi da Azure Active Directory. È anche possibile abilitare SSL, autenticare gli utenti con certificati o nome utente/password e sincronizzare posta elettronica nei dispositivi iOS con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d27e90655e54051d73989202d2bc849a66208f5
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910803"
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

- **Email address attribute from AAD** (Attributo indirizzo di posta elettronica da AAD): scegliere la modalità di generazione dell'indirizzo di posta elettronica per l'utente. Selezionare **Nome dell'entità utente** (`user1@contoso.com` o `user1`) per usare il nome completo dell'entità utente come indirizzo di posta elettronica oppure selezionare **Indirizzo SMTP primario** (`user1@contoso.com`)per usare l'indirizzo SMTP primario per accedere a Exchange.
- **Metodo di autenticazione**: selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione usato dal profilo di posta elettronica. L'autenticazione a più fattori di Azure non è supportata.
  - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza che viene usato per autenticare la connessione di Exchange.
- **SSL**: selezionare **Abilita** per usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **S/MIME**: selezionare **Abilita S/MIME** per inviare la posta elettronica in uscita usando la firma S/MIME. Quando questa opzione è abilitata, è anche possibile crittografare la posta elettronica per i destinatari che possono ricevere posta elettronica crittografata e decrittografare la posta elettronica ricevuta dai mittenti.
  - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato PKCS creato in precedenza per autenticare la connessione di Exchange e/o crittografare gli scambi di posta elettronica.
- **Numero di messaggi di posta elettronica da sincronizzare**: selezionare il numero di giorni di posta elettronica da sincronizzare. In alternativa, selezionare **Illimitata** per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Consenti di spostare i messaggi negli altri account di posta elettronica**: selezionare **Abilita** per consentire agli utenti di spostare i messaggi di posta elettronica tra diversi account configurati nel dispositivo.
- **Consenti l'invio di messaggi di posta elettronica da applicazioni di terze parti**: selezionare **Abilita** per consentire all'utente di selezionare questo profilo come account predefinito per l'invio di posta elettronica e consentire ad applicazioni di terze parti di aprire la posta elettronica nella relativa app nativa, ad esempio per allegare file ai messaggi.
- **Sincronizza gli indirizzi di posta elettronica usati di recente**: selezionare **Abilita** per consentire agli utenti di sincronizzare con il server l'elenco di indirizzi di posta elettronica usati di recente sul dispositivo.

## <a name="next-steps"></a>Passaggi successivi
[Configurare le impostazioni di posta elettronica in Intune](email-settings-configure.md)
