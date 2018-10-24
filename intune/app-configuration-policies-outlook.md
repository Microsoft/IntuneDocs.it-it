---
title: Impostazioni di Outlook per i dispositivi iOS e Android in Microsoft Intune
description: Creare un criterio di configurazione per le impostazioni di Microsoft Outlook in esecuzione in dispositivi iOS e Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7fc9f34bbd3d14ac4291582247b1e45169c2cccc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828805"
---
# <a name="microsoft-outlook-configuration-settings"></a>Impostazioni di configurazione di Microsoft Outlook 

Usare un criterio di configurazione per le impostazioni di Microsoft Outlook in esecuzione in dispositivi iOS e Android. 

Per creare un criterio di configurazione dell'app per i dispositivi iOS gestiti, vedere [Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti](app-configuration-policies-use-ios.md). Per creare un criterio di configurazione dell'app per i dispositivi Android gestiti, vedere [Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Impostazioni di configurazione

Quando si aggiunge un criterio di configurazione in Intune, è possibile impostare impostazioni specifiche per configurare Microsoft Outlook. Nel riquadro **Impostazioni di configurazione** è possibile impostare la configurazione dell'account di posta elettronica.

### <a name="email-account-settings"></a>Impostazioni dell'account di posta elettronica

Le impostazioni di configurazione seguenti sono specifiche di Microsoft Outlook.

- **Server di posta elettronica**: immettere il nome host del server Exchange.
- **Nome dell'account di posta elettronica**: immettere il nome visualizzato per l'account di posta elettronica. Questo nome viene visualizzato nel dispositivo degli utenti.
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
- **Dominio dell'account**: (facoltativo) dominio dell'account.

## <a name="next-steps"></a>Passaggi successivi
[Configurare le impostazioni di posta elettronica in Intune](email-settings-configure.md)

