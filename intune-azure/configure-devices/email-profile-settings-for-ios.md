---
title: Impostazioni di posta elettronica di Intune per dispositivi iOS
titleSuffix: Intune Azure preview
description: "Anteprima di Intune Azure: informazioni sulle opzioni di Intune che è possibile usare per configurare le connessioni di posta elettronica nei dispositivi iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9f0fa6af-3669-439a-bd0d-75d8b1a0b135
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 78f99bba07180c06f979fec997a7bfb749d879c8
ms.openlocfilehash: f18fd3ceee5c73a96444092691c590c7d9a7419c
ms.lasthandoff: 02/24/2017


---

# <a name="email-profile-settings-for-ios-devices-in-microsoft-intune"></a>Impostazioni dei profili di posta elettronica per i dispositivi iOS in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **Server di posta elettronica** - Il nome host del server Exchange dell'azienda.
- **Nome account** - Il nome visualizzato dell'account di posta elettronica come appare agli utenti nei dispositivi.
- **Attributo nome utente da AAD** - Si tratta dell'attributo in Active Directory (AD) o Azure AD che verrà usato per generare il nome utente per questo profilo di posta elettronica. Selezionare **Indirizzo SMTP primario**, ad esempio **user1@contoso.com** o **Nome entità utente**, ad esempio **utente1** o **user1@contoso.com**.
- **Indirizzo di posta elettronica** - La modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Indirizzo SMTP primario** per accedere a Exchange con l'indirizzo SMTP primario o **Nome entità utente** per usare il nome completo dell'entità come indirizzo di posta elettronica.
- **Metodo di autenticazione** - Selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione utilizzato dal profilo di posta elettronica.
    - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza che verrà usato per autenticare la connessione di Exchange.
- **SSL** - Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **S/MIME**: consente di inviare la posta elettronica in uscita usando la firma S/MIME.
    - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza che verrà usato per autenticare la connessione di Exchange.
- **Numero di messaggi di posta elettronica da sincronizzare** - Selezionare il numero di giorni di posta elettronica da sincronizzare o selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Consentire lo spostamento dei messaggi ad altri account di posta elettronica** - Consente agli utenti di spostare i messaggi di posta elettronica tra diversi account configurati nel dispositivo.
- **Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti** - Consente all'utente di selezionare questo profilo come account predefinito per l'invio di posta elettronica e consente ad applicazioni di terze parti di aprire la posta elettronica nella relativa app nativa, ad esempio per allegare file ai messaggi.
- **Sincronizza gli indirizzi di posta elettronica utilizzati di recente** - Questa funzione consente agli utenti di sincronizzare l'elenco di indirizzi di posta elettronica utilizzati di recente sul dispositivo con il server.

