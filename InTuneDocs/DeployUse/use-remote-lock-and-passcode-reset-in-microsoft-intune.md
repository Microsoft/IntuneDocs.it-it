---
title: Usare blocco remoto e reimpostazione passcode | Microsoft Intune
description: "Intune include funzionalità per il blocco remoto e la reimpostazione del passcode."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
translationtype: Human Translation
ms.sourcegitcommit: 899f50cfec9e7c20d2981c077f93e0fccf37dc2b
ms.openlocfilehash: 0b52bd8360f11e226674aefe80a578c451c2679d

---
# Protezione dei dispositivi con blocco remoto e reimpostazione passcode
Microsoft Intune include funzionalità per il blocco remoto e la reimpostazione del passcode.

## Bloccare un dispositivo in modalità remota
Se un utente perde il dispositivo, è possibile bloccare il dispositivo in modalità remota. Nella tabella seguente è illustrato il funzionamento del blocco remoto su diverse piattaforme per dispositivi mobili. Blocco remoto non è supportato

|Piattaforma|Blocco remoto|
|------------|---------------|
|iOS|Supportato|
|Android|Supportato|
|Windows 10 e Windows 10 Mobile|Supportato|
|Windows Phone 8 e Windows Phone 8.1|Supportato|
|Windows RT 8.1 e Windows RT|Funzionalità supportata se l'utente corrente del dispositivo è lo stesso utente che ha registrato il dispositivo.|
|Windows 8.1|Funzionalità supportata se l'utente corrente del dispositivo è lo stesso utente che ha registrato il dispositivo.|

Blocco remoto non è supportato per i PC Windows registrati con il client software di Intune.

### Per bloccare un dispositivo mobile in modalità remota tramite la console di Intune

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i dispositivi mobili**.

2.  Scegliere **Tutti i dispositivi gestiti direttamente** per i dispositivi registrati in Intune o **Tutti i dispositivi gestiti di Exchange ActiveSync**.

    > [!TIP]
    > È anche possibile accedere al dispositivo di un utente. Scegliere **Tutti gli utenti**. Nella pagina delle proprietà dell'utente scegliere **Dispositivi**, quindi il nome del dispositivo mobile di cui cancellare i dati.

3.  Nell'elenco scegliere il dispositivo o i dispositivi da bloccare. Sulla barra delle applicazioni scegliere **Attività remote**, quindi selezionare **Blocco remoto**.

## Reimpostare il passcode in un dispositivo
Se un utente dimentica il passcode, è possibile aiutarlo rimuovendo il passcode da un dispositivo oppure forzando l'uso di un nuovo passcode temporaneo su un dispositivo. Nella tabella seguente è illustrato il funzionamento della reimpostazione del passcode su diverse piattaforme per dispositivi mobili.

|Piattaforma|Reimpostazione del passcode|
|------------|------------------|
|iOS|Funzionalità supportata per cancellare il passcode da un dispositivo. Non implica la creazione di un nuovo passcode temporaneo.|
|Android|Funzionalità supportata; implica la creazione di un passcode temporaneo.|
|Windows 10 Mobile|Supportato|
|Windows Phone 8 e Windows Phone 8.1|Supportato|
|Windows RT 8.1 e Windows RT|Funzionalità non supportata|
|Windows 8.1|Funzionalità non supportata|

Reimpostazione passcode non è supportato per i PC Windows registrati con il client software di Intune.

### Per reimpostare un passcode

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i dispositivi mobili**.

2.  Scegliere **Tutti i dispositivi gestiti direttamente** per i dispositivi registrati in Intune o **Tutti i dispositivi gestiti di Exchange ActiveSync**.

    > [!TIP]
    > È anche possibile accedere al dispositivo di un utente. Fare clic su **Tutti gli utenti**. Nella pagina delle proprietà dell'utente fare clic su **Dispositivi,** quindi sul nome del dispositivo mobile di cui cancellare i dati.

3.  Nell'elenco scegliere il dispositivo o i dispositivi da bloccare. Sulla barra delle applicazioni scegliere **Attività remote** e quindi selezionare **Reimpostazione passcode**.


### Vedere anche
[Ritirare i dispositivi](retire-devices-from-microsoft-intune-management.md)
[Argomento relativo alla cancellazione selettiva di Windows per la gestione dei dati dei dispositivi](http://technet.microsoft.com/library/dn486874.aspx)



<!--HONumber=Sep16_HO2-->


