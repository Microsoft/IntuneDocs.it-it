---
title: Impostazioni di posta elettronica di Intune per dispositivi Android e Android for Work
titleSuffix: Intune on Azure
description: "Informazioni sulle opzioni di Intune che è possibile usare per configurare le connessioni di posta elettronica nei dispositivi Android.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1f80e09241609b420a186011ff8dd059f0dd8df
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="email-profile-settings-for-android--devices-in-microsoft-intune"></a>Impostazioni dei profili di posta elettronica per i dispositivi Android in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Come amministratore di Intune, è possibile creare e assegnare le impostazioni di posta elettronica per i dispositivi Android seguenti:
- [Android Samsung KNOX Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>Impostazioni di posta elettronica per Android Samsung KNOX Standard
- **Server di posta elettronica** - Il nome host del server Exchange dell'azienda.
- **Nome account** - Il nome visualizzato dell'account di posta elettronica come appare agli utenti nei dispositivi.
- **Attributo nome utente da AAD** - Si tratta dell'attributo in Active Directory (AD) o Azure AD usato per generare il nome utente per questo profilo di posta elettronica. Selezionare **Indirizzo SMTP primario**, ad esempio user1@contoso.com o **Nome entità utente**, ad esempio utente1 o user1@contoso.com.
- **Indirizzo di posta elettronica** - La modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Indirizzo SMTP primario** per accedere a Exchange con l'indirizzo SMTP primario o **Nome entità utente** per usare il nome completo dell'entità come indirizzo di posta elettronica.
- **Metodo di autenticazione** - Selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione utilizzato dal profilo di posta elettronica.
    - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.

### <a name="security-settings"></a>Impostazioni di sicurezza

- **SSL** - Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **S/MIME** - Consente di usare la crittografia S/MIME per inviare posta elettronica in uscita.
    - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.

### <a name="synchronization-settings"></a>Impostazioni di sincronizzazione

- **Numero di messaggi di posta elettronica da sincronizzare** - Selezionare il numero di giorni di posta elettronica da sincronizzare o selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Pianificazione sincronizzazione** - Selezionare la pianificazione in base a cui i dispositivi sincronizzano i dati dal server di Exchange. È anche possibile selezionare **Quando arrivano i messaggi**, per sincronizzare i dati all'arrivo, oppure **Manuale**, per consentire all'utente del dispositivo di avviare la sincronizzazione.

### <a name="content-sync-settings"></a>Impostazioni di sincronizzazione del contenuto

- **Tipo di contenuto da sincronizzare** - Selezionare i tipi di contenuto da sincronizzare nei dispositivi da:
    - **Contatti**
    - **Calendarioio**
    - **Attività**

## <a name="android-for-work-email-settings"></a>Impostazioni di posta elettronica per Android for Work

- **App di posta elettronica** - Selezionare **Gmail** o **Nine Work**
- **Server di posta elettronica** - Il nome host del server Exchange dell'azienda.
- **Attributo nome utente da AAD** - Si tratta dell'attributo in Active Directory (AD) o Azure AD che verrà usato per generare il nome utente per questo profilo di posta elettronica. Selezionare **Indirizzo SMTP primario**, ad esempio user1@contoso.com o **Nome entità utente**, ad esempio utente1 o user1@contoso.com.
- **Indirizzo di posta elettronica** - La modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Nome dell'entità utente** per usare il nome dell'entità utente completo come indirizzo di posta elettronica o **Nome utente**.
- **Metodo di autenticazione** - Selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione utilizzato dal profilo di posta elettronica.
    - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.
- **SSL** - Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **Numero di messaggi di posta elettronica da sincronizzare** - Selezionare il numero di giorni di posta elettronica da sincronizzare o selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Tipo di contenuto da sincronizzare** (solo Nine Work) - Selezionare i tipi di contenuto da sincronizzare nei dispositivi da:
    - **Contatti**
    - **Calendarioio**
    - **Attività**
