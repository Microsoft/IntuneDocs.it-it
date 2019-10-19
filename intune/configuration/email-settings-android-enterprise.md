---
title: Impostazioni di posta elettronica di Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Creare profili di posta elettronica di configurazione di un dispositivo che usano server Exchange e recuperano gli attributi da Azure Active Directory. Abilitare SSL o SMIME, autenticare gli utenti con certificati o nome utente/password e sincronizzare posta elettronica e pianificazioni nei dispositivi del profilo di lavoro Android con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 92d81e383a9964aaecbdd151397879236ffcb726
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72493566"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Impostazioni dei dispositivi Android Enterprise per configurare posta elettronica, autenticazione e sincronizzazione in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo elenca e descrive le diverse impostazioni di posta elettronica che è possibile controllare nei dispositivi Android Enterprise. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per configurare un server di posta elettronica, usare SSL per crittografare i messaggi di posta elettronica a altro ancora.

L'amministratore di Intune è in grado di creare e assegnare le impostazioni di posta elettronica ai dispositivi Android Enterprise nel profilo di lavoro.

Per altre informazioni sui profili di posta elettronica in Intune, vedere [Configurare le impostazioni di posta elettronica](email-settings-configure.md).

## <a name="before-you-begin"></a>Prima di iniziare

Creare un [profilo di configurazione del dispositivo](email-settings-configure.md#create-a-device-profile) (scegliere il profilo di lavoro) o creare un [criterio di configurazione dell'app](../apps/app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Android Enterprise

- **App di posta elettronica**: selezionare **Gmail** o **Nine Work**
- **Server di posta elettronica**: nome host del server Exchange dell'azienda. Immettere ad esempio `outlook.office365.com`.
- **Attributo nome utente da AAD**: questo nome è l'attributo che Intune ottiene da Azure Active Directory (Azure AD). Intune genera in modo dinamico il nome utente usato da questo profilo. Le opzioni disponibili sono:

  - **Nome dell'entità utente**: ottiene il nome, ad esempio `user1` o `user1@contoso.com`
  - **Nome utente**: ottiene solo il nome, ad esempio `user1`

- **Attributo indirizzo di posta elettronica da AAD**: questo nome è l'attributo dell'indirizzo di posta elettronica che Intune ottiene da Azure AD. Intune genera in modo dinamico l'indirizzo di posta elettronica usato da questo profilo. Le opzioni disponibili sono:
  - **Nome dell'entità utente**: usa come indirizzo di posta elettronica il nome dell'entità completo, ad esempio `user1@contoso.com` o `user1`.
  - **Indirizzo SMTP primario**: usa l'indirizzo SMTP primario, ad esempio `user1@contoso.com`, per accedere a Exchange.

- **Metodo di autenticazione**: selezionare **Nome utente e password** o **Certificati** come metodo di autenticazione usato dal profilo di posta elettronica.
  - Se si seleziona l'opzione **Certificato**, selezionare un profilo certificato client SCEP o PKCS creato in precedenza per autenticare la connessione di Exchange.
- **SSL**: scegliere **Abilita** per usare la comunicazione Secure Sockets Layer (SSL) durante l'invio e la ricezione di messaggi di posta elettronica e durante la comunicazione con il server Exchange.
- **Numero di messaggi di posta elettronica da sincronizzare**: scegliere il periodo di tempo di posta elettronica da sincronizzare. In alternativa, selezionare **Illimitata** per sincronizzare tutti i messaggi di posta elettronica disponibili.
- **Tipo di contenuto da sincronizzare** (solo Nine Work): scegliere quali dati sincronizzare nei dispositivi. Le opzioni disponibili sono:
  - **Contatti**: scegliere **Abilita** per consentire agli utenti finali di sincronizzare i contatti nei propri dispositivi.
  - **Calendario**: scegliere **Abilita** per consentire agli utenti finali di sincronizzare il calendario nei propri dispositivi.
  - **Attività**: scegliere **Abilita** per consentire agli utenti finali di sincronizzare qualsiasi attività nei propri dispositivi.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili di posta elettronica per dispositivi [Android Samsung Knox](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 e versioni successive](email-settings-windows-10.md) e [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
