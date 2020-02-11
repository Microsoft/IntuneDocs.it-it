---
title: Guida introduttiva - Configurare la registrazione automatica in Intune
description: Guida introduttiva - Configurare la registrazione automatica per i dispositivi Windows 10 in Intune.
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e5cc7cf3661caa2b2640d9370d26402b7702d36b
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541045"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Guida introduttiva: Configurare la registrazione automatica per i dispositivi Windows 10

In questa guida introduttiva si configurerà Microsoft Intune per registrare automaticamente i dispositivi quando utenti specifici eseguono l'accesso a dispositivi Windows 10.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti

- Sottoscrizione di Microsoft Intune - [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).
- Per completare questa guida introduttiva, è necessario [creare un utente](../fundamentals/quickstart-create-user.md) e [creare un gruppo](../fundamentals/quickstart-create-group.md).

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Accedere a Intune in Microsoft Endpoint Manager

Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) come Amministratore globale o come Amministratore del servizio Intune. Se è stata creata una sottoscrizione della versione di valutazione di Intune, l'account creato con tale sottoscrizione sarà un amministratore globale.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurare la registrazione automatica di Windows 10

In questo esempio si userà la registrazione MDM per consentire la registrazione automatica sia dei dispositivi aziendali che dei dispositivi Bring Your Own. Verrà eseguita l'iscrizione per una sottoscrizione Azure Active Directory Premium gratuita.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Tutti i servizi** > **M365 Azure Active Directory** > **Azure Active Directory** > **Mobility (MDM e MAM)** .
2. Selezionare **Per accedere a questa funzionalità, usare una versione di valutazione gratuita Premium**. Questa opzione consentirà la registrazione automatica usando la versione di valutazione gratuita Premium di Azure Active Directory. 

    ![Selezionare la versione di valutazione gratuita Premium di Azure Active Directory](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

3. Selezionare la versione di valutazione gratuita **Enterprise Mobility + Security E5**. 
4. Fare clic su **Versione di valutazione gratuita** > **Attiva** per attivare la versione di valutazione gratuita.

    ![Scegliere la versione di valutazione gratuita Enterprise Mobility + Security E5](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

    > [!NOTE]
    > L'attivazione potrebbe richiedere un minuto. 

3. Selezionare **Microsoft Intune** per configurare Intune. 

    ![Scegliere Microsoft Intune dall'elenco](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Selezionare **In parte** in **Ambito utente MDM** per usare la registrazione automatica MDM per gestire i dati aziendali nei dispositivi Windows dei dipendenti. La registrazione automatica MAM verrà configurata per gli scenari di dispositivi aggiunti ad AAD e Bring Your Own Device (BYOD).

    ![Selezionare 'In parte' dall'elenco Configura](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Fare clic su **Selezione gruppi** > **Contoso Testers** (Tester Contoso)  > **Seleziona** come gruppo assegnato.

    ![Selezionare il gruppo da registrare](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Selezionare **In parte** in **Ambito utente MAM** per gestire i dati nei dispositivi della forza lavoro.

    ![Selezionare il gruppo da registrare](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-06.png)

7. Scegliere **Seleziona gruppi** > **Contoso Testers** (Tester Contoso)  > **Seleziona** come gruppo assegnato. 
8. Usare i valori predefiniti per i valori di configurazione rimanenti.
9. Scegliere **Salva**.

## <a name="clean-up-resources"></a>Pulizia delle risorse

Per riconfigurare la registrazione automatica di Intune, consultare [Configurare la registrazione dei dispositivi Windows](windows-enroll.md).

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come configurare la registrazione automatica per i dispositivi Windows 10. Per altre informazioni sulla registrazione dei dispositivi, vedere [Che cos'è la registrazione dei dispositivi?](device-enrollment.md)

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: Registrare il dispositivo Windows 10](../quickstart-enroll-windows-device.md)
