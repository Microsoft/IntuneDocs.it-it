---
# required metadata

title: Inviare i log dei dati di diagnostica all'amministratore IT tramite posta elettronica | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 85c868e7-8d63-480c-9770-4e99614a5c94

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Inviare i log dei dati di diagnostica all'amministratore IT tramite posta elettronica

Se si verifica un errore nel dispositivo Android mentre si usano le app aziendali o dell'istituto di istruzione o quando è attiva l'app Portale aziendale, è possibile inviare i log dei dati di diagnostica per aiutare l'amministratore IT a individuare e risolvere l'errore. Per includere tutti i dettagli nei log, in modo che sia più semplice per l'amministratore IT individuare il problema, attivare la registrazione dettagliata.

Per attivare la registrazione dettagliata:

1.  Aprire l'app Portale aziendale.

2.  Toccare **Menu** &gt;  **Impostazioni**.

    > [!NOTE] 
    > **Menu** può essere un pulsante software o hardware, a seconda del tipo di dispositivo Android in uso.

3.  In **Dati di diagnostica** toccare **Invia dati**..

    > [!NOTE]
    > **Solo se si usano dispositivi Android 6.0 o versioni successive:** quando si tocca **Invia dati**, viene visualizzato un messaggio che chiede se **consentire al portale aziendale di accedere a foto, supporti e file nel dispositivo**.. 

    Questo messaggio è fuorviante perché **Microsoft non accede mai a foto, supporti o file nel dispositivo.** Il testo del messaggio è controllato da Google, quindi Microsoft non può modificarlo.  Quando si consente l'accesso, il dispositivo può solo scrivere i log di dati nella scheda SD del dispositivo, da dove possono essere spostati con un cavo USB.

    Se si nega l'accesso, il messaggio viene visualizzato di nuovo la volta successiva che si tocca **Invia dati**, ma è possibile disattivare la ricezione di altri messaggi toccando la casella di controllo **Non visualizzare più questo messaggio**.  Se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** &gt; **App** &gt; **Portale aziendale** &gt; **Autorizzazioni** &gt; **Archiviazione** e quindi attivare l'autorizzazione.

4.  Seguire le istruzioni per scegliere un'app di posta elettronica da usare per inviare i log all'amministratore IT. L'app creerà un messaggio di posta elettronica preindirizzato con tutti i log allegati.


### Vedere anche
[Uso del dispositivo Android con Intune](using-your-android-device-with-intune.md)

<!--HONumber=May16_HO1-->


