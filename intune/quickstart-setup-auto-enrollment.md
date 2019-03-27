---
title: Guida introduttiva - Configurare la registrazione automatica in Intune
description: Guida introduttiva - Configurare la registrazione automatica per i dispositivi Windows 10 in Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 11/05/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 810adbf06ddcd0aabb5c758f6a71c898116a9cee
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57394307"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Guida introduttiva: Configurare la registrazione automatica per i dispositivi Windows 10

In questa guida introduttiva si configurerà Microsoft Intune per registrare automaticamente i dispositivi quando utenti specifici eseguono l'accesso a dispositivi Windows 10.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti

- Sottoscrizione di Microsoft Intune - [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).
- Per completare questa guida introduttiva, è necessario [creare un utente](quickstart-create-user.md) e [creare un gruppo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurare la registrazione automatica di Windows 10

In questo esempio si userà la registrazione MDM per consentire la registrazione automatica sia dei dispositivi aziendali che dei dispositivi Bring Your Own. Verrà eseguita l'iscrizione per una sottoscrizione Azure Active Directory Premium gratuita.

1. In Azure scegliere **Azure Active Directory** > **Servizi Mobility (MDM e MAM)**.
2. Selezionare **Per accedere a questa funzionalità, usare una versione di valutazione gratuita Premium**. Questa opzione consentirà la registrazione automatica usando la versione di valutazione gratuita Premium di Azure Active Directory. 

    ![Selezionare la versione di valutazione gratuita Premium di Azure Active Directory](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    Selezionare la versione di valutazione gratuita **Enterprise Mobility + Security E5**. È anche necessario scegliere **Attiva** per attivare la versione di valutazione gratuita.

    ![Scegliere la versione di valutazione gratuita Enterprise Mobility + Security E5](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. Selezionare **Microsoft Intune**. 

    ![Scegliere Microsoft Intune dall'elenco](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Selezionare **In parte** in **Ambito utente MDM** per usare la registrazione automatica MDM per gestire i dati aziendali nei dispositivi Windows dei dipendenti. La registrazione automatica MAM verrà configurata per gli scenari di dispositivi aggiunti ad AAD e Bring Your Own Device (BYOD).

    ![Selezionare 'In parte' dall'elenco Configura](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Scegliere **Seleziona gruppi** > **Contoso Testers** (Tester Contoso)  > **Seleziona** come gruppo assegnato.

    ![Selezionare il gruppo da registrare](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Selezionare **In parte** in **Ambito utente MAM** per gestire i dati nei dispositivi della forza lavoro.
7. Scegliere **Seleziona gruppi** > **Contoso Testers** (Tester Contoso)  > **Seleziona** come gruppo assegnato. 
8. Usare i valori predefiniti per i valori di configurazione rimanenti.
9. Scegliere **Salva**.

## <a name="clean-up-resources"></a>Pulizia delle risorse

Per riconfigurare la registrazione automatica di Intune, consultare [Configurare la registrazione dei dispositivi Windows](windows-enroll.md).

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come configurare la registrazione automatica per i dispositivi Windows 10. Per altre informazioni sulla registrazione dei dispositivi, vedere [Che cos'è la registrazione dei dispositivi?](device-enrollment.md)

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: Registrare il dispositivo Windows 10](quickstart-enroll-windows-device.md)
