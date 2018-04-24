---
title: Impostazioni di posta elettronica di Microsoft Intune per dispositivi iOS
titleSuffix: ''
description: Informazioni sulle impostazioni di Microsoft Intune che è possibile usare per configurare le impostazioni di posta elettronica nei dispositivi che eseguono iOS.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7b050e94114b0d3c9dcec765f4dd6e7700a801f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-ios"></a>Impostazioni del profilo di posta elettronica in Microsoft Intune per i dispositivi che eseguono iOS 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni del profilo di posta elettronica che è possibile configurare per i dispositivi che eseguono iOS.

## <a name="email-settings"></a>Impostazioni di posta elettronica

- **Server di posta elettronica** - Il nome host del server Exchange dell'azienda.
- **Nome account** - Il nome visualizzato dell'account di posta elettronica come appare agli utenti nei dispositivi.
- **Attributo nome utente da AAD** - Si tratta dell'attributo in Active Directory (AD) o Azure AD che viene usato per generare il nome utente per questo profilo di posta elettronica. Selezionare **Indirizzo SMTP primario**, ad esempio **user1@contoso.com** o **Nome entità utente**, ad esempio **utente1** o **user1@contoso.com**.
- **Indirizzo di posta elettronica** - La modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Indirizzo SMTP primario** per accedere a Exchange con l'indirizzo SMTP primario o **Nome entità utente** per usare il nome completo dell'entità come indirizzo di posta elettronica.
- **Metodo di autenticazione** - Selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione utilizzato dal profilo di posta elettronica.
    - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza che viene usato per autenticare la connessione di Exchange.
- **SSL** - Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **S/MIME**: consente di inviare la posta elettronica in uscita usando la firma S/MIME.
    - Se è stata selezionata l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza che viene usato per autenticare la connessione di Exchange.
- **Numero di messaggi di posta elettronica da sincronizzare** - Selezionare il numero di giorni di posta elettronica da sincronizzare o selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Consentire lo spostamento dei messaggi ad altri account di posta elettronica** - Consente agli utenti di spostare i messaggi di posta elettronica tra diversi account configurati nel dispositivo.
- **Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti** - Consente all'utente di selezionare questo profilo come account predefinito per l'invio di posta elettronica e consente ad applicazioni di terze parti di aprire la posta elettronica nella relativa app nativa, ad esempio per allegare file ai messaggi.
- **Sincronizza gli indirizzi di posta elettronica utilizzati di recente** - Questa funzione consente agli utenti di sincronizzare l'elenco di indirizzi di posta elettronica utilizzati di recente sul dispositivo con il server.
