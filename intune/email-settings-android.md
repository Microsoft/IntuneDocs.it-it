---
title: Impostazioni di posta elettronica di Android e Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Creare profili di posta elettronica di configurazione di un dispositivo che usano server Exchange e recuperano gli attributi da Azure Active Directory. Abilitare SSL o SMIME, autenticare gli utenti con certificati o nome utente/password e sincronizzare posta elettronica e pianificazioni in Android e nei dispositivi del profilo di lavoro Android con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b96363d679a6f09327bf9a1b46421e786d1956a8
ms.sourcegitcommit: 912aee714432c4a1e8efeee253ca2be4f972adaa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316883"
---
# <a name="android-and-android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Impostazioni dei dispositivi Android e Android Enterprise per configurare posta elettronica, autenticazione e sincronizzazione in Intune

Questo articolo descrive le diverse impostazioni di posta elettronica che è possibile controllare nei dispositivi Android e Android Enterprise. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per configurare un server di posta elettronica, usare SSL per crittografare i messaggi di posta elettronica a altro ancora.

Come amministratore di Intune, è possibile creare e assegnare le impostazioni di posta elettronica ai dispositivi Android seguenti:

- Android Samsung Knox Standard
- Android Enterprise

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](email-settings-configure.md).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Server di posta elettronica**: immettere il nome host del server Exchange dell'azienda.
- **Nome account**: immettere il nome visualizzato dell'account di posta elettronica. Questo nome viene visualizzato nel dispositivo degli utenti.
- **Attributo nome utente da AAD**: questo nome è l'attributo che Intune ottiene da Azure Active Directory (AAD). Intune genera in modo dinamico il nome utente usato da questo profilo. Le opzioni disponibili sono:
  - **Nome entità utente**: ottiene il nome, ad esempio `user1` o `user1@contoso.com`
  - **Nome utente**: ottiene solo il nome, ad esempio `user1`
  - **Nome account SAM**: richiede il dominio, ad esempio `domain\user1`. Il nome account SAM può essere usato solo con i dispositivi Android. Android Enterprise non è supportato.

    Specificare anche:  
    - **Origine del nome di dominio utente**: scegliere **AAD** (Azure Active Directory) o **Personalizzato**.

      Quando si sceglie di ottenere gli attributi da **AAD**, specificare:
      - **Attributo nome di dominio utente da AAD**: scegliere di ottenere l'attributo **Nome di dominio completo** o **Nome NetBIOS** dell'utente

      Quando si sceglie di usare attributi di tipo **Personalizzato**, specificare:
      - **Nome di dominio personalizzato da usare**: immettere un valore usato da Intune per il nome di dominio, ad esempio `contoso.com` o `contoso`

- **Attributo indirizzo di posta elettronica da AAD**: scegliere la modalità di generazione dell'indirizzo di posta elettronica per l'utente. Selezionare **Nome dell'entità utente** (`user1@contoso.com` o `user1`) per usare il nome completo dell'entità utente come indirizzo di posta elettronica oppure selezionare **Indirizzo SMTP primario** (`user1@contoso.com`)per usare l'indirizzo SMTP primario per accedere a Exchange.

- **Metodo di autenticazione**: Selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione usato dal profilo di posta elettronica.
  - Se si seleziona l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.

### <a name="security-settings"></a>Impostazioni di sicurezza

- **SSL**: Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **S/MIME**: Consente di usare la crittografia S/MIME per inviare posta elettronica in uscita.
  - Se si seleziona l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.

### <a name="synchronization-settings"></a>Impostazioni di sincronizzazione

- **Numero di messaggi di posta elettronica da sincronizzare**: selezionare il numero di giorni di posta elettronica da sincronizzare oppure selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Pianificazione sincronizzazione**: selezionare la pianificazione in base alla quale i dispositivi devono sincronizzare i dati dal server Exchange. È anche possibile selezionare **Quando arrivano i messaggi**, per sincronizzare i dati all'arrivo, oppure **Manuale**, per consentire all'utente del dispositivo di avviare la sincronizzazione.

### <a name="content-sync-settings"></a>Impostazioni di sincronizzazione del contenuto

- **Tipo di contenuto da sincronizzare**: Selezionare i tipi di contenuto da sincronizzare nei dispositivi. **Non configurato** disabilita questa impostazione. Se l'impostazione è **Non configurato** e un'utente finale abilita la sincronizzazione nel dispositivo, la sincronizzazione viene nuovamente disabilitata quando il dispositivo si sincronizza con Intune, poiché viene di nuovo applicato il criterio. 

  È possibile sincronizzare il contenuto seguente: 
  - **Contatti**
  - **Calendarioio**
  - **Attività**

## <a name="android-enterprise"></a>Android Enterprise

- **App di posta elettronica**: selezionare **Gmail** o **Nine Work**
- **Server di posta elettronica**: immettere il nome host del server Exchange dell'azienda.
- **Attributo nome utente da AAD**: questo nome è l'attributo di Active Directory (AD) o Azure AD usato per generare il nome utente per questo profilo di posta elettronica. Selezionare **Indirizzo SMTP primario**, ad esempio user1@contoso.com o **Nome entità utente**, ad esempio utente1 o user1@contoso.com.
- **Attributo indirizzo di posta elettronica da AAD**: Modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Nome dell'entità utente** per usare il nome dell'entità utente completo come indirizzo di posta elettronica o **Nome utente**.
- **Metodo di autenticazione**: Selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione usato dal profilo di posta elettronica.
  - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.
- **SSL**: Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **Numero di messaggi di posta elettronica da sincronizzare**: selezionare il numero di giorni di posta elettronica da sincronizzare oppure selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Tipo di contenuto da sincronizzare** (solo Nine Work): Selezionare i tipi di contenuto da sincronizzare nei dispositivi. **Non configurato** disabilita questa impostazione. Se l'impostazione è **Non configurato** e un'utente finale abilita la sincronizzazione nel dispositivo, la sincronizzazione viene nuovamente disabilitata quando il dispositivo si sincronizza con Intune, poiché viene di nuovo applicato il criterio. 

  È possibile sincronizzare il contenuto seguente: 
  - **Contatti**
  - **Calendarioio**
  - **Attività**

## <a name="next-steps"></a>Passaggi successivi
[Configurare le impostazioni di posta elettronica in Intune](email-settings-configure.md)
