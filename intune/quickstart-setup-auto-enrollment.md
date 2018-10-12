---
title: Guida introduttiva - Configurare la registrazione automatica in Intune
description: Guida introduttiva - Configurare la registrazione automatica per i dispositivi Windows 10 in Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581647"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Guida introduttiva: configurare la registrazione automatica per i dispositivi Windows 10

In questa guida introduttiva si configurerà Microsoft Intune per registrare automaticamente i dispositivi quando utenti specifici eseguono l'accesso a dispositivi Windows 10.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti

- Per completare questa guida introduttiva, è necessario [creare un utente](quickstart-create-user.md) e [creare un gruppo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurare la registrazione automatica di Windows 10

In questo esempio si userà la registrazione MDM per consentire la registrazione automatica sia dei dispositivi aziendali che dei dispositivi Bring Your Own.

1. In Azure, scegliere **Azure Active Directory** > **Servizi Mobility (MDM e MAM)** > **Microsoft Intune**  >   **Alcune**.
![Browser](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. Scegliere **Seleziona gruppi** > **Contoso Testers** > **Seleziona**.
3. Usare i valori predefiniti per gli URL seguenti:
    - URL delle condizioni per l'uso di MDM
    - URL individuazione MDM
    - URL conformità MDM
4. Scegliere **Salva**.
5. Accedere come utente del gruppo a un dispositivo Windows 10 e seguire le istruzioni.

## <a name="clean-up-resources"></a>Pulizia delle risorse

Per riconfigurare la registrazione automatica di Intune, consultare [Configurare la registrazione dei dispositivi Windows](windows-enroll.md).

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come configurare la registrazione automatica per i dispositivi Windows 10. Sono disponibili altri modi per registrare i dispositivi su tutte le piattaforme.

> [!div class="nextstepaction"]
> [Che cos'è la registrazione dei dispositivi?](device-enrollment.md) Articolo