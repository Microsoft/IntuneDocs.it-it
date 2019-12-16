---
title: Richiedere l'autenticazione a più fattori per la registrazione di dispositivi Intune
titleSuffix: Microsoft Intune
description: Come richiedere l'autenticazione a più fattori in Azure AD per la registrazione di dispositivi Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db04b93deffd2476a97b952fd1c6942fa79e1f05
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955389"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Richiedere l'autenticazione a più fattori per le registrazioni di dispositivi Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune può usare l'autenticazione a più fattori (MFA) di Azure Active Directory per la registrazione dei dispositivi e al contempo contribuire a proteggere le risorse aziendali.

L'autenticazione MFA funziona richiedendo due o più dei seguenti metodi di verifica:

- Un elemento noto (in genere una password o un PIN).
- Un oggetto fisico (un dispositivo attendibile non facile da duplicare, come un telefono).
- Una caratteristica fisica biometrica, ad esempio un'impronta digitale.

Multi-Factor Authentication è supportata per i dispositivi iOS, Android, Windows 8.1, Windows Phone 8.1 o Windows 10 Mobile o versioni successive.

Quando si abilita Multi-Factor Authentication, gli utenti finali devono fornire due tipi di credenziali per registrare un dispositivo.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurare Intune per la richiesta dell'autenticazione a più fattori alla registrazione del dispositivo

Per richiedere l'autenticazione MFA quando viene registrato un dispositivo, seguire questa procedura:

>[!Important]
>Per implementare questo criterio è necessario che agli utenti sia stata assegnata Azure Active Directory Premium P1 o versione successiva.

>[!Important]
>Non configurare le **regole di accesso in base al dispositivo** per la registrazione di Microsoft Intune.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), scegliere **Dispositivi** > **Accesso condizionale**. Il nodo di accesso condizionale accessibile da *Intune* è lo stesso nodo accessibile da *Azure AD*.
2. Scegliere **Nuovo criterio**.
3. In **Nuovo** criterio digitare un nome descrittivo per il criterio.
4. Nella sezione **Assegnazioni** scegliere **Utenti e gruppi**. 
5. In **Utenti e gruppi** scegliere **Selezionare utenti o gruppi** e selezionare **Utenti e gruppi**. Quindi selezionare gli utenti e/o i gruppi che riceveranno questi criteri e scegliere **Fine**.
6. Nella sezione **Assegnazioni** scegliere **App cloud**.
7. In **App cloud**, nella scheda **Includi** scegliere **Selezionare le app**, quindi **Seleziona** > **Registrazione di Microsoft Intune** e al termine fare clic su **Fine**. Scegliendo **Registrazione di Microsoft Intune**, l'autenticazione a più fattori dell'accesso condizionale viene applicata solo alla registrazione del dispositivo (richiesta di autenticazione a più fattori una sola volta).
8. Nella sezione **Assegnazioni** in **Condizioni** non è necessario configurare impostazioni per MFA.
9. Nella sezione **Controlli di accesso** scegliere **Concedi**.
10. In **Concedi** scegliere **Concedi accesso** e quindi selezionare **Richiedi autenticazione a più fattori**. Non selezionare **Richiedi che i dispositivi siano contrassegnati come conformi** perché non è possibile valutare la conformità di un dispositivo fino a quando non è registrato. Quindi scegliere **Seleziona**.
11. In **Nuovo criterio** scegliere **Attiva criterio** > **Sì** e quindi scegliere **Crea**.



## <a name="next-steps"></a>Passaggi successivi

Quando gli utenti finali registrano i dispositivi, devono eseguire l'autenticazione con un secondo tipo di identificazione, ad esempio un PIN, un telefono o dati biometrici.
