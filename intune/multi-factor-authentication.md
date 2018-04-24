---
title: Richiedere l'autenticazione a più fattori per la registrazione di dispositivi Intune
titlesuffix: Microsoft Intune
description: Come richiedere l'autenticazione a più fattori in Azure AD per la registrazione di dispositivi Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
ms.custom: intune-azure
ms.openlocfilehash: 0941db852674d1ee775fc05edb92ff479d856d0c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Richiedere l'autenticazione a più fattori per le registrazioni di dispositivi Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune può usare l'autenticazione a più fattori (MFA) di Azure Active Directory per la registrazione dei dispositivi e al contempo contribuire a proteggere le risorse aziendali.

L'autenticazione MFA funziona richiedendo due o più dei seguenti metodi di verifica:

- Un elemento noto (in genere una password o un PIN).
- Un oggetto fisico (un dispositivo attendibile non facile da duplicare, come un telefono).
- Una caratteristica fisica biometrica, ad esempio un'impronta digitale.

Multi-Factor Authentication è supportata per i dispositivi iOS, Android, Windows 8.1, Windows Phone 8.1 o Windows 10 Mobile o versioni successive.

Quando si abilita Multi-Factor Authentication, gli utenti finali devono fornire due tipi di credenziali per registrare un dispositivo.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurare Intune per la richiesta dell'autenticazione a più fattori alla registrazione del dispositivo

Per richiedere l'autenticazione MFA quando viene registrato un dispositivo, seguire questa procedura:

[!Important]
>Per implementare questo criterio è necessario che agli utenti sia stata assegnata Azure Active Directory Premium P1 o versione successiva.

>[!Important]
>Non configurare le **regole di accesso in base al dispositivo** per la registrazione di Microsoft Intune.

1. Accedere al [portale di Microsoft Azure](https://portal.azure.com) con le credenziali personali.
2. Nel portale scegliere **Azure Active Directory**.
2. In **Azure Active Directory** scegliere **Gestisci** > **Applicazioni aziendali**.
3. In **Applicazioni aziendali** scegliere **Gestisci** > **Tutte le applicazioni**. Verrà visualizzato un elenco di tutte le app Azure gestite.
3. Nell'elenco scegliere **Registrazione di Microsoft Intune**.
4. In **Registrazione di Microsoft Intune** scegliere **Sicurezza** > **Accesso condizionale**.
5. Scegliere **Nuovo criterio**.
6. In **Nuovo** criterio digitare un nome descrittivo per il criterio.
7. Nella sezione **Assegnazioni** scegliere **Utenti e gruppi**.
8. In **Utenti e gruppi** scegliere gli utenti e i gruppi a cui verrà applicato il criterio e quindi scegliere **Fine**.
9. Nella sezione **Assegnazioni** scegliere **App cloud**.
10. In **App cloud**, nella scheda **Includi** scegliere **Selezionare le app**, quindi **Seleziona** > **Registrazione di Microsoft Intune** e al termine fare clic su **Fine**.
11. Nella sezione **Assegnazioni** scegliere **Condizioni**.
12. In **Condizioni** non è necessario configurare alcuna impostazione per MFA.
13. Nella sezione **Controlli di accesso** scegliere **Concedi**.
14. In **Concedi** scegliere **Concedi accesso** e quindi selezionare **Richiedi autenticazione a più fattori**.
    Non selezionare **Richiedi che i dispositivi siano contrassegnati come conformi** perché non è possibile valutare la conformità di un dispositivo fino a quando non è registrato.
15. Scegliere **Seleziona**.
16. In **Nuovo criterio** scegliere **Attiva criterio** > **Sì** e quindi scegliere **Crea**.



## <a name="next-steps"></a>Passaggi successivi

Quando gli utenti finali registrano i dispositivi, devono eseguire l'autenticazione con un secondo tipo di identificazione, ad esempio un PIN, un telefono o dati biometrici.
