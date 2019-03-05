---
title: Impostazioni di posta elettronica di Microsoft Intune per Windows Phone 8.1
titleSuffix: ''
description: Informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni di posta elettronica nei dispositivi che eseguono Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ec2ccddce5af20fb84ba9ac3a62a57b5566ea81
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231180"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Impostazioni del profilo di posta elettronica in Microsoft Intune per i dispositivi che eseguono Windows Phone 8.1

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni del profilo di posta elettronica che è possibile configurare per i dispositivi che eseguono Windows Phone 8.1.


- **Applica tutte le impostazioni solo a Windows Phone 8.1**: si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni vengono applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni vengono applicate anche ai dispositivi Windows 10 Mobile.
- **Server di posta elettronica** - Il nome host del server Exchange dell'azienda.
- **Nome account** - Il nome visualizzato dell'account di posta elettronica come appare agli utenti nei dispositivi.
- **Attributo nome utente da AAD** - Si tratta dell'attributo in Active Directory (AD) o Azure AD che viene usato per generare il nome utente per questo profilo di posta elettronica. Selezionare **Indirizzo SMTP primario**, ad esempio **user1@contoso.com** o **Nome entità utente**, ad esempio **utente1** o **user1@contoso.com**.
- **Indirizzo di posta elettronica** - La modalità di generazione dell'indirizzo di posta elettronica per l'utente in ogni dispositivo. Selezionare **Indirizzo SMTP primario** per accedere a Exchange con l'indirizzo SMTP primario o **Nome entità utente** per usare il nome completo dell'entità come indirizzo di posta elettronica.


## <a name="security-settings"></a>Impostazioni di sicurezza

- **SSL** - Consente di usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.



## <a name="synchronization-settings"></a>Impostazioni di sincronizzazione

- **Numero di messaggi di posta elettronica da sincronizzare** - Selezionare il numero di giorni di posta elettronica da sincronizzare o selezionare **Illimitata** nell'elenco a discesa per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Pianificazione sincronizzazione** - Selezionare la pianificazione in base a cui i dispositivi sincronizzano i dati dal server di Exchange. È anche possibile selezionare **Quando arrivano i messaggi**, per sincronizzare i dati non appena arrivano, oppure **Manuale**, per consentire all'utente del dispositivo di avviare la sincronizzazione.

## <a name="content-sync-settings"></a>Impostazioni di sincronizzazione del contenuto

- **Tipo di contenuto da sincronizzare** - Selezionare i tipi di contenuto da sincronizzare nei dispositivi da:
    - **Contatti**
    - **Calendarioio**
    - **Attività**
