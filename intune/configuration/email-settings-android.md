---
title: Impostazioni di posta elettronica di Android in Microsoft Intune - Azure | Microsoft Docs
description: Creare profili di posta elettronica di configurazione di un dispositivo che usano server Exchange e recuperano gli attributi da Azure Active Directory. Abilitare SSL o SMIME, autenticare gli utenti con certificati o nome utente/password e sincronizzare posta elettronica e pianificazioni in dispositivi Android Samsung Knox con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 647e1cd6925df27d42186599ad6786e866742b44
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734674"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Impostazioni dei dispositivi Android per configurare posta elettronica, autenticazione e sincronizzazione in Intune

Questo articolo elenca e descrive le diverse impostazioni di posta elettronica che è possibile controllare nei dispositivi Android Samsung Knox in Intune. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per configurare un server di posta elettronica, usare SSL per crittografare i messaggi di posta elettronica a altro ancora.

L'amministratore di Intune è in grado di creare e assegnare le impostazioni di posta elettronica ai dispositivi Android Samsung Knox Standard.

Per altre informazioni sui profili di posta elettronica in Intune, vedere [Configurare le impostazioni di posta elettronica](email-settings-configure.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Server di posta elettronica**: immettere il nome host del server Exchange. Immettere ad esempio `outlook.office365.com`.
- **Nome account**: immettere il nome visualizzato per l'account di posta elettronica. Questo nome viene visualizzato nel dispositivo degli utenti.
- **Attributo nome utente da AAD**: questo nome è l'attributo che Intune ottiene da Azure Active Directory (Azure AD). Intune genera in modo dinamico il nome utente usato da questo profilo. Le opzioni disponibili sono:
  - **Nome dell'entità utente**: ottiene il nome, ad esempio `user1` o `user1@contoso.com`
  - **Nome utente**: ottiene solo il nome, ad esempio `user1`
  - **Nome account SAM**: richiede il dominio, ad esempio `domain\user1`. Il nome account SAM viene usato solo con i dispositivi Android.

    Specificare anche:  
    - **Origine del nome di dominio utente**: scegliere **AAD** (Azure Active Directory) o **Personalizzato**.

      Quando si sceglie di ottenere gli attributi da **AAD**, specificare:
      - **Attributo nome di dominio utente da AAD**: scegliere di ottenere l'attributo **Nome completo** o **Nome NetBIOS** dell'utente

      Quando si sceglie di usare attributi di tipo **Personalizzato**, specificare:
      - **Nome di dominio personalizzato da usare**: immettere un valore usato da Intune per il nome dominio, ad esempio `contoso.com` o `contoso`

- **Attributo indirizzo di posta elettronica da AAD**: questo nome è l'attributo dell'indirizzo di posta elettronica che Intune ottiene da Azure AD. Intune genera in modo dinamico l'indirizzo di posta elettronica usato da questo profilo. Le opzioni disponibili sono:
  - **Nome dell'entità utente**: usa come indirizzo di posta elettronica il nome dell'entità completo, ad esempio `user1@contoso.com` o `user1`.
  - **Indirizzo SMTP primario**: usa l'indirizzo SMTP primario, ad esempio `user1@contoso.com`, per accedere a Exchange.

- **Metodo di autenticazione**: selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione usato dal profilo di posta elettronica.
  - Se si seleziona l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.

### <a name="security-settings"></a>Impostazioni di sicurezza

- **SSL**: consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **S/MIME**: consente di usare la crittografia S/MIME per inviare posta elettronica in uscita.
  - Se si seleziona l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.

### <a name="synchronization-settings"></a>Impostazioni di sincronizzazione

- **Numero di messaggi di posta elettronica da sincronizzare**: selezionare il numero di giorni di posta elettronica da sincronizzare o selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Pianificazione sincronizzazione**: selezionare la pianificazione in base a cui i dispositivi sincronizzano i dati dal server Exchange. È anche possibile selezionare **Quando arrivano i messaggi**, per sincronizzare i dati all'arrivo, oppure **Manuale**, per consentire all'utente del dispositivo di avviare la sincronizzazione.

### <a name="content-sync-settings"></a>Impostazioni di sincronizzazione del contenuto

- **Tipo di contenuto da sincronizzare**: selezionare i tipi di contenuto da sincronizzare nei dispositivi. **Non configurato** disabilita questa impostazione. Se l'impostazione è **Non configurato** e un'utente finale abilita la sincronizzazione nel dispositivo, la sincronizzazione viene nuovamente disabilitata quando il dispositivo si sincronizza con Intune, poiché viene di nuovo applicato il criterio. 

  È possibile sincronizzare il contenuto seguente:  
  - **Contatti**: scegliere **Abilita** per consentire agli utenti finali di sincronizzare i contatti nei propri dispositivi.
  - **Calendario**: scegliere **Abilita** per consentire agli utenti finali di sincronizzare il calendario nei propri dispositivi.
  - **Attività**: scegliere **Abilita** per consentire agli utenti finali di sincronizzare qualsiasi attività nei propri dispositivi.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili di posta elettronica per [Android Enterprise - profilo di lavoro](email-settings-android-enterprise.md), [iOS](email-settings-ios.md), [Windows 10 e versioni successive](email-settings-windows-10.md) e [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
