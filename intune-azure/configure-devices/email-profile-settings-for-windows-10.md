---
title: Impostazioni relative alla posta elettronica di Intune per dispositivi Windows 10 | Anteprima di Intune Azure | Documentazione Microsoft
description: "Anteprima di Intune Azure: informazioni sulle opzioni di Intune che è possibile usare per configurare le connessioni di posta elettronica nei dispositivi Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ffafbd0-4b5d-4c86-a46b-611f9b7a58e5
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: a69df096dd3ff1012eadba01213a6f2192bad3a9
ms.lasthandoff: 02/16/2017


---

# <a name="email-profile-settings-for-windows-10-devices-in-microsoft-intune"></a>Impostazioni dei profili di posta elettronica per i dispositivi Windows 10 in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **Server di posta elettronica** - Il nome host del server Exchange dell'azienda.
- **Nome account** - Il nome visualizzato dell'account di posta elettronica come appare agli utenti nei dispositivi.
- **Attributo nome utente da AAD** - Si tratta dell'attributo in Active Directory (AD) o Azure AD che verrà usato per generare il nome utente per questo profilo di posta elettronica. Selezionare **Indirizzo SMTP primario**, ad esempio **user1@contoso.com** o **Nome entità utente**, ad esempio **utente1** o **user1@contoso.com**.
- **Indirizzo di posta elettronica** - La modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Indirizzo SMTP primario** per accedere a Exchange con l'indirizzo SMTP primario o **Nome entità utente** per usare il nome completo dell'entità come indirizzo di posta elettronica.


## <a name="security-settings"></a>Impostazioni di sicurezza

- **SSL** - Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.



## <a name="synchronization-settings"></a>Impostazioni di sincronizzazione

- **Numero di messaggi di posta elettronica da sincronizzare** - Selezionare il numero di giorni di posta elettronica da sincronizzare o selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Pianificazione sincronizzazione** - Selezionare la pianificazione in base a cui i dispositivi sincronizzeranno i dati dal server di Exchange. È anche possibile selezionare **Quando arrivano i messaggi**, per sincronizzare i dati non appena arrivano, oppure **Manuale**, per consentire all'utente del dispositivo di avviare la sincronizzazione.

## <a name="content-sync-settings"></a>Impostazioni di sincronizzazione del contenuto

- **Tipo di contenuto da sincronizzare** - Selezionare i tipi di contenuto da sincronizzare nei dispositivi da:
    - **Contatti**
    - **Calendarioio**
    - **Attività**
