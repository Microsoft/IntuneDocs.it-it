---
title: Sincronizzare manualmente il dispositivo Windows | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 443c6de7-5187-4dc4-b844-6085a0c659bd
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 4b5f0129d6824a51c36662a1cc7ef4e8a2de9e20
ms.openlocfilehash: ff5a4313337c89da00cb87e0f4dd6c8dcc233361
ms.lasthandoff: 02/18/2017


---

# <a name="sync-your-windows-device-manually"></a>Sincronizzare il dispositivo Windows manualmente

A volte, il tentativo di installare un'app nel dispositivo Windows può richiedere più tempo del previsto. In questo caso, è possibile provare a sincronizzare manualmente il dispositivo Windows. La sincronizzazione può essere utile per velocizzare l'installazione.

> [!Note]
> L'installazione delle app potrebbe richiedere un po' di tempo se si usa una rete lenta o è in corso il download di contenuto da un numero elevato di dispositivi contemporaneamente.

Le versioni di Windows seguenti supportano la sincronizzazione manuale. Sfortunatamente, se il dispositivo usa una versione diversa di Windows, non è possibile avviare una sincronizzazione manuale.

* [Sincronizzazione in Windows 10 Desktop](#windows-10-desktop)
* [Sincronizzazione in Windows 10 Mobile](#windows-10-mobile)
* [Sincronizzazione in Windows Phone 8.1](#windows-phone-81)

## <a name="windows-10-desktop"></a>Windows 10 Desktop
Esistono più versioni di Windows 10, quindi esistono sono due procedure distinte. Per determinare quale procedura eseguire, esaminare gli screenshot e quindi eseguire la procedura con un aspetto simile a quanto visualizzato sul dispositivo.

1. Scegliere **Start** e quindi scegliere **Impostazioni**.

    ![Il pulsante Start](./media/win10pc-sync-1-start-button.png)

2. Nella pagina **Impostazioni** scegliere **Account**.

    ![Scelta di Account nella pagina Impostazioni](./media/win10pc-sync-2-settings-accounts.png)

3. Esaminare le due schermate seguenti e trovare quella simile a quanto viene visualizzato sul dispositivo. Seguire i passaggi corrispondenti alla schermata visualizzata sul dispositivo.

    Se si visualizza questa schermata, in cui compare "Accedi all'azienda o all'istituto di istruzione", attenersi alle istruzioni in [Passaggi da seguire se si visualizza Accedi all'azienda o all'istituto di istruzione](#steps-to-follow-if-you-see-access-work-or-school).

    ![Passaggi di sincronizzazione da seguire se si visualizza Accedi all'azienda o all'istituto di istruzione](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Se si visualizza questa schermata, in cui compare "Accesso società", seguire i passaggi in [Passaggi da seguire se si visualizza Accesso società](#steps-to-follow-if-you-see-your-account).

    ![Scelta di Accesso società come tipo di account](./media/win10pc-sync-3-work-access.png)

### <a name="steps-to-follow-if-you-see-access-work-or-school"></a>Passaggi da seguire se si visualizza Accedi all'azienda o all'istituto di istruzione

1. Nella pagina **Account** scegliere **Accedi all'azienda o all'istituto di istruzione**.

    ![Scegliere Accedi all'azienda o all'istituto di istruzione.](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2. Scegliere l'account aziendale o dell'istituto di istruzione. A seconda della configurazione eseguita dall'amministratore IT, è possibile che vengano visualizzati due account simili all'esempio illustrato di seguito. Accanto a un account è visibile l'icona Sincronia file e accanto all'altro è presente il logo Microsoft.

    - Se è visualizzato l'account con Sincronia file, selezionarlo e cercare il pulsante **Informazioni** sotto di esso.
    - Se è visualizzato solo l'account con il logo Microsoft, selezionarlo e cercare il pulsante **Informazioni** sotto di esso.

    ![Scegliere il nome dell'account accanto a Sincronia file o al logo Microsoft](./media/win10pc-rs1-sync-info-button.png)

3. Scegliere il pulsante **Info**. Verrà visualizzata una finestra di dialogo simile all'esempio illustrato di seguito.

    ![Scegliere il nome dell'account accanto a Sincronia file o al logo Microsoft](./media/win10pc-rs1-sync-button.png)

4. Scegliere il pulsante **Sincronizza**. Il dispositivo verrà sincronizzato con Intune.

### <a name="steps-to-follow-if-you-see-work-access"></a>Passaggi da seguire se si visualizza Accesso società

1. Nella pagina **Account** scegliere **Accesso società**.

    ![Scelta di Accesso società come tipo di account](./media/win10pc-sync-3-work-access.png)

2. Nella sezione **Registrati per la gestione dispositivi** fare clic sul nome della società, come illustrato nell'evidenziazione blu in basso.

    ![Scelta del nome della società per la gestione dei dispositivi](./media/win10pc-sync-4-tap-com-name.png)

3. Scegliere il pulsante **Sincronizza**.

    ![Scelta del pulsante Sincronizza](./media/win10pc-sync-5-tap-sync.png)

   Il pulsante diventa inattivo fino al completamento della sincronizzazione.

   ## <a name="windows-10-mobile"></a>Windows 10 Mobile
   Sincronizzare manualmente il dispositivo Windows 10 Mobile per accelerare un'installazione lenta:

   1. Accedere a **Tutte le app** > **Impostazioni** > **Account**.

       ![Scelta di Account nella schermata Impostazioni](./media/win10m-sync-1-settings-accounts.png)

   2. Scegliere **Accesso società**.

       ![Scelta di Accesso società come tipo di account](./media/win10m-sync-2-work-access.png)

   3. In **Registrati per la gestione dispositivi** scegliere il nome della società.

       ![Scelta del nome della società per la gestione dei dispositivi](./media/win10m-sync-3-tap-comp-name.png)

   4. Scegliere l'icona **Sincronizza**.

       ![Scelta dell'icona Sincronizza.](./media/win10m-sync-4-tap-sync.png)

       Nella parte superiore dello schermo viene visualizzato il messaggio "We're synching your account" (Sincronizzazione account in corso). Il pulsante **Sincronizza** resta disattivato fino al completamento della sincronizzazione del dispositivo.

## <a name="windows-phone-81"></a>Windows Phone 8.1
Sincronizzare manualmente il dispositivo Windows Phone 8.1 per accelerare un'installazione lenta:

1. Accedere a **Tutte le app** > **Impostazioni** > **azienda**.

    ![Elenco di impostazioni](./media/wp81-1-sync-settings-workplace.png)

2. Scegliere il nome della propria società.

    ![Scelta del nome della società per l'account aziendale](./media/wp81-2-sync-tap-compname.png)

3. Scegliere l'icona **Sincronizza**.

    ![Scelta dell'icona Sincronizza.](./media/wp81-3-sync-tap-sync-button.png)

   Nella parte superiore dello schermo viene visualizzato il messaggio "We're synching your account" (Sincronizzazione account in corso) fino al termine della sincronizzazione del dispositivo.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

