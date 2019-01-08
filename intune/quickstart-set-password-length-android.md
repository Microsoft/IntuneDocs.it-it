---
title: Guida introduttiva - Creare un criterio di conformità della password per i dispositivi Android
titlesuffix: Microsoft Intune
description: In questa guida introduttiva si userà Microsoft Intune per impostare la lunghezza della password obbligatoria per i dispositivi Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 87fb7091079086e5c455376cb5c4ae8e10f28ec1
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179253"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Guida introduttiva: Creare un criterio di conformità della password per i dispositivi Android

In questa guida introduttiva si userà Microsoft Intune per richiedere agli utenti della forza lavoro che usano Android di immettere una password di una lunghezza specifica prima di ottenere l'accesso alle informazioni nei dispositivi Android. 

I criteri di conformità del dispositivo in Intune specificano le regole e le impostazioni che i dispositivi devono soddisfare per essere considerati conformi. È possibile usare criteri di conformità con accesso condizionale per consentire o bloccare l'accesso alle risorse aziendali. È anche possibile ottenere i report di dispositivo e intraprendere azioni per la mancata conformità.

> [!IMPORTANT]
> Oltre alle impostazioni della password, è consigliabile prendere in considerazione altre impostazioni di sicurezza del sistema per proteggere la forza lavoro. Per altre informazioni, vedere [Impostazioni di sicurezza del sistema](compliance-policy-create-android-for-work.md#system-security-settings).

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune. 

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi

In questa guida introduttiva si userà Intune per richiedere agli utenti della forza lavoro che usano Android di immettere una password di una lunghezza specifica prima di ottenere l'accesso alle informazioni nei dispositivi Android.

1. In Intune selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
2. Aggiungere **Conformità Android** come **Nome**. Aggiungere anche una **Descrizione**.
3. Per **Piattaforma**, selezionare **Android**. 
4. Selezionare **Impostazioni** > **Sicurezza del sistema** per visualizzare il pannello **Sicurezza del sistema** per Android.
5. Fare clic su **Rendi obbligatorio** accanto a **Richiedi una password per sbloccare i dispositivi mobili**.
6. Immettere **6** accanto a **Lunghezza minima password**. 

    ![Screenshot della creazione di un gruppo in Microsoft Intune](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. Al termine, fare clic su **OK** > **OK** > **Crea** per creare il criterio.

Dopo averlo creato, il criterio comparirà nell'elenco dei criteri di conformità dei dispositivi. 

## <a name="clean-up-resources"></a>Pulizia delle risorse

Quando non è più necessario, eliminare il criterio. A tale scopo, selezionare il criterio di conformità e fare clic su **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato usato Intune per creare criteri di conformità per i dispositivi Android della forza lavoro per richiedere una password di almeno sei caratteri. Per altre informazioni sulla creazione dei criteri di conformità, vedere [Introduzione ai criteri di conformità dei dispositivi in Intune](device-compliance-get-started.md).

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Guida introduttiva: Inviare notifiche a dispositivi non conformi](quickstart-send-notification.md)