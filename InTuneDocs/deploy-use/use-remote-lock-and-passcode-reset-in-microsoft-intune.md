---
title: Blocco remoto e reimpostazione del passcode | Documentazione Microsoft
description: "Intune include funzionalità per il blocco remoto e la reimpostazione del passcode."
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/06/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 665d3347636d5ec0c698ffb93b768028c9d59ce3
ms.openlocfilehash: b918c9843bdc6cfbbfd9c2da9d698b255487152c
ms.lasthandoff: 03/07/2017

---
# <a name="help-protect-your-devices-with-remote-lock-and-passcode-reset"></a>Protezione dei dispositivi con blocco remoto e reimpostazione passcode

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune include funzionalità per il blocco remoto e la reimpostazione del passcode.

## <a name="lock-a-device-remotely"></a>Bloccare un dispositivo in modalità remota
Se un utente perde un dispositivo, è possibile bloccare il dispositivo in modalità remota. Per poter usare il blocco remoto è necessario che nel dispositivo sia impostato un PIN o passcode.

Nella tabella seguente è illustrato il funzionamento del blocco remoto su diverse piattaforme per dispositivi mobili.

|Piattaforma|Blocco remoto|
|------------|---------------|
|macOS|Non supportato|
|iOS|Supportato|
|Android|Supportato|
|Android for Work|Supportato|
|Windows 10 (Mobile)|Supportato|
|Windows 10 (Desktop)|Non supportato|
|Windows Phone 8 e Windows Phone 8.1|Supportato|
|Windows RT 8.1 e Windows RT|Funzionalità supportata se l'utente corrente del dispositivo è lo stesso utente che ha registrato il dispositivo.|
|Windows 8.1|Funzionalità supportata se l'utente corrente del dispositivo è lo stesso utente che ha registrato il dispositivo.|

Blocco remoto non è supportato per i PC Windows registrati con il client software di Intune.

### <a name="lock-a-mobile-device-remotely-through-the-intune-console"></a>Bloccare un dispositivo mobile in modalità remota tramite la console di Intune

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i dispositivi mobili**.

2.  Scegliere **Tutti i dispositivi gestiti direttamente** per i dispositivi registrati in Intune o **Tutti i dispositivi gestiti di Exchange ActiveSync**.

    > [!TIP]
    > È anche possibile accedere al dispositivo di un utente. Scegliere **Tutti gli utenti**. Nella pagina delle proprietà dell'utente scegliere **Dispositivi** e quindi il nome del dispositivo mobile da bloccare.

3.  Nell'elenco scegliere il dispositivo o i dispositivi da bloccare. Sulla barra delle applicazioni scegliere **Attività remote** e quindi selezionare **Blocco remoto**.

## <a name="reset-the-passcode-on-a-device"></a>Reimpostare il passcode in un dispositivo
Se un utente dimentica un passcode, è possibile aiutarlo rimuovendo il passcode da un dispositivo oppure forzando l'uso di un nuovo passcode temporaneo su un dispositivo. La tabella seguente illustra il funzionamento della reimpostazione del passcode su diverse piattaforme per dispositivi mobili.

|Piattaforma|Reimpostazione del passcode|
|------------|------------------|
|macOS|Non supportato|
|iOS|Funzionalità supportata per cancellare il passcode da un dispositivo. Non implica la creazione di un nuovo passcode temporaneo.|
|Android|Supportato nelle versioni precedenti alla 7.0. Crea un passcode temporaneo.|
|Android for Work|Non supportato|
|Windows 10 Mobile|Supportato|
|Windows Phone 8 e Windows Phone 8.1|Supportato|
|Windows RT 8.1|Funzionalità non supportata|
|Windows 8.1|Funzionalità non supportata|
|Windows 10 Desktop|Funzionalità non supportata|

Reimpostazione passcode non è supportato per i PC Windows registrati con il client software di Intune.

### <a name="reset-a-passcode"></a>Reimpostare un passcode

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i dispositivi mobili**.

2.  Scegliere **Tutti i dispositivi gestiti direttamente** per i dispositivi registrati in Intune o **Tutti i dispositivi gestiti di Exchange ActiveSync**.

    > [!TIP]
    > È anche possibile accedere al dispositivo di un utente. Fare clic su **Tutti gli utenti**. Nella pagina delle proprietà dell'utente fare clic su **Dispositivi,** quindi sul nome del dispositivo mobile di cui cancellare i dati.

3.  Nell'elenco scegliere il dispositivo o i dispositivi da bloccare. Sulla barra delle applicazioni scegliere **Attività remote** e quindi selezionare **Reimpostazione passcode**.


### <a name="see-also"></a>Vedere anche
[Ritirare i dispositivi](retire-devices-from-microsoft-intune-management.md) e [Cancellazione selettiva di Windows per la gestione di dati del dispositivo](http://technet.microsoft.com/library/dn486874.aspx)

