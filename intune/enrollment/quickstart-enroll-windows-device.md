---
title: Guida introduttiva - Registrare il dispositivo Windows 10 Desktop in Microsoft Intune
description: Guida introduttiva - Usare il portale aziendale per registrare il dispositivo Windows 10 Desktop in Microsoft Intune.
services: microsoft-intune
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/30/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0aeeb55804a2bdd3ef1143bbb88dee968892c5c7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509280"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>Guida introduttiva: Registrare il dispositivo Windows 10

In questa guida introduttiva si assume innanzitutto il ruolo di utente di Intune e si registra il dispositivo Windows 10 in Microsoft Intune. Quindi, si tornerà a Intune per verificare il dispositivo registrato.

La registrazione dei dispositivi in Microsoft Intune consente ai dispositivi Windows di 10 accedere ai dati protetti dell'organizzazione, inclusi posta elettronica, file e altre risorse. Questo vale sia per i dispositivi Windows 10 Desktop che per quelli Windows 10 Mobile. La registrazione dei dispositivi contribuisce a proteggere l'accesso per l'utente e per la propria organizzazione e consente di mantenere i dati di lavoro distinti da quelli personali.

> [!TIP]
> Altre informazioni su cosa accade quando si [registra il dispositivo in Intune](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows) e cosa significa per le [informazioni sul dispositivo](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune).

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti

- Sottoscrizione di Microsoft Intune - [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md)
- Per completare questa guida introduttiva, è necessario eseguire i passaggi necessari per [configurare la registrazione automatica in Intune](quickstart-setup-auto-enrollment.md).

## <a name="confirm-your-windows-10-desktop-version"></a>Verificare la versione di Windows 10 Desktop

Prima della registrazione di Windows 10 Desktop, è necessario verificare la versione di Windows installata.

1. Fare clic con il pulsante destro del mouse sull'icona **Start** di Windows e selezionare **Impostazioni** per visualizzare le opzioni Impostazioni di Windows.

   ![Screenshot di Impostazioni di Windows - Sistema](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. Selezionare **Sistema** > **Informazioni**. 

   ![Screenshot delle impostazioni di sistema](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > È anche possibile digitare la frase "Informazioni sul PC" nella **barra di ricerca**, quindi selezionare **Informazioni sul PC**.

3. Nella finestra **Impostazioni** viene visualizzato un elenco delle **specifiche di Windows** per il PC. In questo elenco individuare la **Versione**.

4. Verificare che la **Versione** di Windows 10 sia la **1607 o una versione successiva**.

    > [!IMPORTANT]
    > La procedura descritta in questa guida introduttiva si applica a Windows 10 versione **1607 o successiva**. Se la versione in uso è la versione **1511 o una versione precedente**, continuare con [questa procedura](/intune-user-help/enroll-windows-10-device).  

## <a name="enroll-windows-10-desktop"></a>Registrare Windows 10 Desktop

1. Tornare a Impostazioni di Windows e selezionare **Account**.

   ![Screenshot delle impostazioni di sistema - Account](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. Selezionare **Accedi all'azienda o all'istituto di istruzione** > **Connetti**.

    ![Selezionare Accedi all'azienda o all'istituto di istruzione](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. Accedere a Intune con l'account aziendale o dell'istituto di istruzione e quindi selezionare **Avanti**. Se è stata eseguita la procedura descritta nell'articolo di avvio rapido sulla [creazione di un utente e l'assegnazione di una licenza](../fundamentals/quickstart-create-user.md), è possibile accedere con l'account utente creato.

    > [!NOTE]
    > Se si sta configurando ".onmicrosoft.com", l'account utente includerà **.onmicrosoft.com** nell'indirizzo dell'account. 

   ![Immettere l'account aziendale o dell'istituto di istruzione](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    Verrà visualizzato un messaggio che indica che la società o l'istituto di istruzione sta registrando il dispositivo.

4. Quando viene visualizzata la schermata **La configurazione è completata**, selezionare **Fine**. La procedura è stata completata.

5. L'account aggiunto è ora visualizzato nelle impostazioni **Accedi all'azienda o all'istituto di istruzione** in Windows Desktop.

   ![Screenshot dell'account aggiunto](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    Se i passaggi precedenti sono stati seguiti, ma non è ancora possibile accedere ai file e agli account di posta elettronica aziendali o dell'istituto di istruzione, seguire i passaggi in [Passaggi di risoluzione dei problemi da seguire se si visualizza Accedi all'azienda o all'istituto di istruzione](/intune-user-help/troubleshoot-your-windows-10-device-windows#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

## <a name="confirm-your-device-enrollment-in-intune"></a>Verificare la registrazione del dispositivo in Intune

1. Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune.
2. Selezionare **Dispositivi** > **Tutti i dispositivi** per visualizzare i dispositivi registrati in Intune.
3. Verificare la presenza di un nuovo dispositivo registrato in Intune.

   ![Screenshot dei dispositivi registrati in Intune](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>Pulizia delle risorse

Per annullare la registrazione del dispositivo Windows, vedere [Rimuovere il dispositivo Windows dalla gestione](/intune-user-help/unenroll-your-device-from-intune-windows).

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come registrare un dispositivo Windows 10 in Intune. Sono disponibili altri modi per registrare i dispositivi su tutte le piattaforme. Per altre informazioni sull'uso dei dispositivi con Intune, vedere [Usare dispositivi gestiti per lo svolgimento del lavoro](/intune-user-help/use-managed-devices-to-get-work-done).

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: Impostare una lunghezza della password obbligatoria per i dispositivi Android](../quickstart-set-password-length-android.md)
