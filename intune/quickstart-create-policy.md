---
title: 'Guida rapida: aggiungere i criteri di conformità per un dispositivo Windows 10'
description: Usare questa guida rapida per creare criteri per la protezione dei dati aziendali e la gestione dei dispositivi che gli utenti finali usano per accedere alle risorse aziendali. Assegnare quindi i criteri ai gruppi.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9d9169ab353da30e0f7b292cea4f5b9c93e316aa
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2018
ms.locfileid: "49391553"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>Guida rapida: aggiungere i criteri di conformità per un dispositivo Windows 10
I criteri di conformità di un dispositivo Windows in Intune specificano le regole e le impostazioni che i dispositivi Windows devono soddisfare per essere considerati conformi. Questi criteri con [accesso condizionale](https://docs.microsoft.com/intune/conditional-access) possono essere usati per consentire o bloccare l'accesso alle risorse aziendali. È anche possibile ottenere i report di dispositivo e intraprendere azioni per la mancata conformità.

In questa guida introduttiva verrà creato un criterio di conformità del dispositivo per un dispositivo Windows 10 e un gruppo di dispositivi verrà assegnato al criterio.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti
- Per completare questa guida introduttiva, è necessario [creare un utente](quickstart-create-user.md) e [creare un gruppo](quickstart-create-group.md).


## <a name="sign-in-to-intune"></a>Accedere a Intune
Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune.

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi
1. Selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
2. Immettere **Conformità di Windows 10** in **Nome** e **Criterio di conformità di esempio per Windows 10** in **Descrizione**.
3. In **Piattaforma** selezionare **Windows 10 e versioni successive**.
4. In **Impostazioni** selezionare **Sicurezza del sistema** e quindi impostare **Richiedi una password per sbloccare i dispositivi mobili** su **Richiedi**. Dopo aver completato la configurazione dei criteri selezionare **OK**.
   ![Criteri di conformità](/intune/media/quickstart-create-policy/compliance-policy.png)
5. Chiudere il riquadro **Criteri di conformità di Windows 10**. 
6. Nel riquadro **Crea criterio** selezionare **Crea**. Questo passaggio crea i criteri e li elenca in **Conformità del dispositivo** > **Criteri**.
7. Selezionare il nuovo criterio e scegliere **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
8. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD esistenti. Selezionare **Contoso Testers** e scegliere **Salva** per distribuire il criterio agli utenti del gruppo. Se non è stato creato un gruppo in [Creare un gruppo per gestire gli utenti](quickstart-create-group.md), è possibile usare un gruppo di propria scelta. 

## <a name="clean-up-resources"></a>Pulizia delle risorse
Quando non è più necessario, eliminare il criterio. A tale scopo, selezionare il criterio **Conformità di Windows 10** e fare clic su **Elimina**. 

## <a name="next-steps"></a>Passaggi successivi
In questa guida introduttiva è stato creato e assegnato un semplice criterio di conformità del dispositivo. Per registrare un dispositivo Windows 10 affinché riceva il criterio, passare alla guida rapida che spiega come configurare la registrazione automatica. 
 
> [!div class="nextstepaction"]
> [Impostare la lunghezza della password per il dispositivo](quickstart-set-password-length-android.md)