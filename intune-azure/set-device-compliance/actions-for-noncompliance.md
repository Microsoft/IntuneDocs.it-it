---
title: "Azioni per la mancata conformità"
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come creare azioni per i dispositivi non conformi'
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 16da087e741e335144266c838c0a91050bd7d520
ms.lasthandoff: 03/15/2017


---

# <a name="create-actions-for-non-compliance"></a>Creare azioni per la mancata conformità

Le **azioni per la mancata conformità** consentono di configurare una sequenza temporale di azioni da applicare ai dispositivi che non risultano conformi. È ad esempio possibile inviare notifiche agli utenti di dispositivi non conformi tramite posta elettronica o impedire a tali dispositivi di accedere alle risorse aziendali tramite l'accesso condizionale.

## <a name="use-case-scenario"></a>Scenario di un caso d'uso

Per impostazione predefinita, quando un dispositivo risulta non conforme in base a uno dei criteri di conformità di Intune, l'accesso condizionale blocca immediatamente tale dispositivo e l'utente riceve un messaggio di posta elettronica con le istruzioni per rispettare i criteri di conformità. Le **azioni per la mancata conformità** consentono di decidere con maggiore flessibilità l'azione da intraprendere quando un dispositivo risulta non conforme. È ad esempio possibile decidere di non bloccare immediatamente il dispositivo e di concedere all'utente un periodo di tolleranza per adeguarsi ai criteri di conformità.

Esistono due tipi di azioni:

-   Inviare all'utente una notifica di posta elettronica

-   Bloccare l'accesso alle risorse aziendali tramite l'accesso condizionale

## <a name="notify-the-user-via-email"></a>Inviare all'utente una notifica di posta elettronica

È possibile scegliere tra modelli di posta elettronica predefiniti creati in precedenza oppure creare una notifica di posta elettronica personalizzata. Sono disponibili opzioni per personalizzare l'oggetto, il corpo del messaggio, compreso il logo della società, le informazioni di contatto ed eventuali altri destinatari.

## <a name="block-corporate-resource-access-through-conditional-access"></a>Bloccare l'accesso alle risorse aziendali tramite l'accesso condizionale

È possibile pianificare il numero di giorni in cui bloccare l'accesso del dispositivo alle risorse aziendali. È possibile scegliere di applicare il blocco immediatamente oppure concedere all'utente un periodo di tolleranza per adeguarsi ai criteri di conformità dei dispositivi.

## <a name="before-you-begin"></a>Prima di iniziare

Per configurare le azioni per la mancata conformità è necessario aver creato almeno un criterio di conformità dei dispositivi.

-   Vedere la procedura per creare criteri di conformità dei dispositivi per:

    -   [Android](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)

    -   [Android for Work](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android-for-work)

    -   [iOS](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-ios)

    -   [Windows](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-windows)

Quando si prevede di applicare criteri di conformità per impedire ai dispositivi di usare le risorse aziendali, è necessario aver configurato l'accesso condizionale EMS.

- Vedere la procedura per [configurare l'accesso condizionale EMS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

È inoltre necessario aver creato un modello di messaggio di notifica. Questo modello verrà usato in un secondo momento, durante la creazione delle azioni per la mancata conformità, per inviare notifiche di posta elettronica agli utenti.

### <a name="to-add-a-notification-message-template"></a>Per aggiungere un modello di messaggio di notifica

Nel pannello **Criteri di conformità del dispositivo**:

1.  In **Gestione** scegliere **Notifiche** in modo da visualizzare il pannello dei modelli dei messaggi di notifica.

    ![Come aggiungere un modello di notifica](../media/afnc-1.png)

2.  Scegliere **Aggiungi** e definire gli elementi seguenti:

    a.  Descrizione

    b.  Da

    c.  Oggetto

    d.  Messaggio

    e.  Intestazione del messaggio di posta elettronica - Includere il logo dell'azienda

    f.  Piè di pagina del messaggio di posta elettronica - Includere il nome dell'azienda

    g.  Piè di pagina del messaggio di posta elettronica - Includere le informazioni sul contatto

     ![Modello di messaggio di notifica](../media/afnc-2.png)

Dopo aver aggiunto le informazioni necessarie, è possibile fare clic su **Crea**. Il modello di messaggio di notifica è disponibile per l'uso.

> [!NOTE] 
> È anche possibile modificare un modello di notifica creato in precedenza.

## <a name="to-create-actions-for-non-compliance"></a>Per creare azioni per la mancata conformità

È possibile aggiungere un'azione nel momento in cui si crea un nuovo criterio di conformità dei dispositivi o si modifica un criterio esistente.

1.  Nel pannello **Criteri di conformità del dispositivo**, in **Gestione**, scegliere **Criteri**.

2.  Fare clic su un criterio di conformità dei dispositivi.

    ![Criteri di conformità](../media/afnc-3.png)

3.  Verrà aperto il pannello **Device compliance policy properties** (Proprietà dei criteri di conformità del dispositivo) in cui scegliere **Azioni per la non conformità**.

4.  Verrà aperto il pannello Azioni per la non conformità in cui scegliere **Aggiungi** per specificare i parametri dell'azione.

    ![Pannello Azioni per la non conformità](../media/afnc-4.png)

Sono disponibili le seguenti azioni per la mancata conformità:

-   **Applica i criteri di accesso condizionale**

-   **Invia un messaggio di posta elettronica all'utente finale**

### <a name="enforce-conditional-access-policy"></a>Applica i criteri di accesso condizionale

Per aggiungere questa azione per la mancata conformità:

1.  Nel pannello **Azioni per la non conformità** scegliere **Aggiungi**.

2.  Nel pannello **Parametri dell'azione** selezionare **Applica i criteri di accesso condizionale** dall'elenco a discesa Azione.

3.  In **Pianificazione** è possibile specificare il numero di giorni (da 0 a 255) per applicare i criteri di accesso condizionale. Se si specifica **0** come numero di giorni, l'accesso condizionale deve bloccare **immediatamente** l'accesso alle risorse aziendali non appena i dispositivi risultano non conformi ai criteri.

    ![Pianificare azioni per la mancata conformità](../media/afnc-5.png)

4.  Scegliere **Aggiungi** e quindi **OK** nel pannello **Azioni**.

5.  Nel pannello **Device compliance policy properties** (Proprietà dei criteri di conformità del dispositivo) scegliere **Salva**.

### <a name="send-e-mail-to-end-user"></a>Invia un messaggio di posta elettronica all'utente finale

È possibile usare un modello di messaggio di posta elettronica da inviare agli utenti non conformi. Questi messaggi sono utili per favorire la conformità dei dispositivi all'interno dell'organizzazione.

Per aggiungere questa azione per la mancata conformità:

1.  Nel pannello **Azioni per la non conformità** scegliere **Aggiungi**.

2.  Nel pannello **Parametri dell'azione** selezionare **Invia un messaggio di posta elettronica all'utente finale** dall'elenco a discesa Azione.

3.  Scegliere un modello di messaggio creato in precedenza facendo clic su **Modello di messaggio**. È possibile visualizzare il contenuto del modello di messaggio e quindi scegliere **Seleziona**.

    ![Modello di messaggio](../media/afnc-6.png)

> [!NOTE] 
> Il modello di messaggio può essere visualizzato ma non modificato. Se si vuole modificare il modello di messaggio, è necessario tornare nel pannello **Notifiche**.

1.  In **Pianificazione** immettere il numero di giorni, dopo il rilevamento della mancata conformità, entro i quali il messaggio di posta elettronica deve essere inviato agli utenti. Se si specifica **0** come numero di giorni, il messaggio verrà inviato **immediatamente**.

2.  Scegliere **Aggiungi** e quindi **OK** nel pannello **Azioni**.

3.  Nel pannello **Device compliance policy properties** (Proprietà dei criteri di conformità del dispositivo) scegliere **Salva**.

