---
title: Guida introduttiva - Impostare una lunghezza della password obbligatoria per i dispositivi Android
titlesuffix: Microsoft Intune
description: In questa guida introduttiva si userà Microsoft Intune per impostare una lunghezza della password obbligatoria per i dispositivi Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395285"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>Guida introduttiva: Impostare una lunghezza della password obbligatoria per i dispositivi Android

In questa guida introduttiva si userà Microsoft Intune per richiedere agli utenti della forza lavoro che usano Android di immettere una password di una lunghezza specifica prima di ottenere l'accesso alle informazioni nei dispositivi Android. 

> [!IMPORTANT]
> Oltre alle impostazioni della password, è consigliabile prendere in considerazione altre impostazioni di sicurezza del sistema per proteggere la forza lavoro. Per altre informazioni, vedere [Impostazioni di sicurezza del sistema](compliance-policy-create-android-for-work.md#system-security-settings).

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune. Si accede a Intune nel portale di Azure scegliendo **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi
1. Dopo aver aperto il pannello **Microsoft Intune**, selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
2. Aggiungere **Conformità Android** come **Nome**. Aggiungere anche una **Descrizione**.
3. Per **Piattaforma**, selezionare **Android**. 
4. Selezionare **Impostazioni** > **Sicurezza del sistema** per visualizzare il pannello **Sicurezza del sistema** per Android.
5. Nella sezione **Password** accanto a **Richiedi una password per sbloccare i dispositivi mobili** fare clic su **Rendi obbligatorio**.
6. Accanto a **Lunghezza minima password** immettere **6**.  

    ![Screenshot della creazione di un gruppo in Microsoft Intune](./media/quickstart-set-password-length-android-01.png)

7. Al termine, fare clic su **OK** per chiudere il pannello **Sicurezza del sistema**. 
8. Fare clic su **OK** per chiudere il pannello **Criteri di conformità di Android**. 
9. Fare clic su **Crea** per creare i criteri.

Dopo aver creato correttamente i criteri, questi compariranno nell'elenco **Conformità del dispositivo - Criteri**. 

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato usato Intune per creare criteri di conformità per i dispositivi Android della forza lavoro per richiedere una password di almeno sei caratteri.

> [!div class="nextstepaction"]
> [Configurare la registrazione automatica ](quickstart-setup-auto-enrollment.md)
