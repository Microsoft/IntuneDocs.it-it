---
title: Impostazioni di Outlook per i dispositivi iOS e Android in Microsoft Intune
description: Creare un criterio di configurazione per le impostazioni di Microsoft Outlook in esecuzione in dispositivi iOS e Android.
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 24ed1a895dd3e4cad6111b40913b43fa9c6a3cec
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903523"
---
# <a name="microsoft-outlook-configuration-settings"></a>Impostazioni di configurazione di Microsoft Outlook 

Usare un criterio di configurazione per le impostazioni di Microsoft Outlook in esecuzione in dispositivi iOS e Android. 

Per creare un criterio di configurazione dell'app per i dispositivi iOS gestiti, vedere [Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti](app-configuration-policies-use-ios.md). Per creare un criterio di configurazione dell'app per i dispositivi Android gestiti, vedere [Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Impostazioni di configurazione

Quando si aggiunge un criterio di configurazione in Intune, è possibile impostare impostazioni specifiche per configurare Microsoft Outlook. Nel riquadro **Impostazioni di configurazione** è possibile impostare la configurazione dell'account di posta elettronica.

### <a name="basic-authentication-email-account-settings"></a>Impostazioni dell'account di posta elettronica per l'autenticazione di base
Outlook per iOS e Android offre agli amministratori di Exchange la possibilità di effettuare il "push" delle configurazioni degli account agli utenti locali che usano l'autenticazione di base con il protocollo ActiveSync. Per altre informazioni, vedere [Configurazione di account in Outlook per iOS e Android utilizzando l'autenticazione di base](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup). Per abilitare la configurazione degli account, è possibile configurare le impostazioni seguenti:

- **Server di posta elettronica**: immettere il nome host del server Exchange locale (ad esempio mail.contoso.com).
- **Nome dell'account di posta elettronica**: immettere il nome visualizzato per l'account di posta elettronica. Questo nome viene visualizzato nel dispositivo degli utenti.
- **Attributo nome utente da AAD**: questo nome è l'attributo che Intune ottiene da Azure Active Directory (Azure AD). Intune genera in modo dinamico il nome utente usato da questo profilo. Alcune delle opzioni possibili sono:
  - **Nome dell'entità utente**: ottiene il nome, ad esempio `user1` o `user1@contoso.com`
  - **Indirizzo SMTP primario**: ottiene il nome nel formato dell'indirizzo di posta elettronica, ad esempio `user1@contoso.com`
- **Email address attribute from AAD** (Attributo indirizzo di posta elettronica da AAD): scegliere la modalità di generazione dell'indirizzo di posta elettronica per l'utente. Selezionare **Nome dell'entità utente** (`user1@contoso.com` o `user1`) per usare il nome completo dell'entità utente come indirizzo di posta elettronica oppure selezionare **Indirizzo SMTP primario** (`user1@contoso.com`)per usare l'indirizzo SMTP primario per accedere a Exchange. Si consiglia di selezionare **Indirizzo SMTP primario**.
- **Dominio dell'account**: (facoltativo) dominio dell'account.

## <a name="next-steps"></a>Passaggi successivi
[Configurare le impostazioni di posta elettronica in Intune](email-settings-configure.md)

