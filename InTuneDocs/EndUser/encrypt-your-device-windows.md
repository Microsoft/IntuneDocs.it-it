---
# required metadata

title: Crittografare il dispositivo Windows| Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8d022ea7-d9b6-43c4-adcd-4f6421606a7f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Crittografare il dispositivo Windows
Per proteggere i dati aziendali o dell'istituto di istruzione, è possibile che l'amministratore IT debba crittografare il dispositivo Windows. Se viene visualizzato un messaggio che indica che è necessario crittografare il dispositivo, l'amministratore IT comunica all'utente quali dei passi seguenti devono essere eseguiti per crittografare il dispositivo.

Il dispositivo può essere crittografato dopo aver aggiunto un account Microsoft o aver abilitato BitLocker.

**Opzione 1: Aggiungere un account Microsoft**

1.  Cercare e quindi avviare l'app **Impostazioni PC**.

2.  Fare clic su **Account** &gt; ** Il tuo account** e quindi fare clic su **Connetti a un account Microsoft**.

3.  Seguire le istruzioni visualizzate.

4.  Verificare che il dispositivo sia registrato con Intune seguendo le istruzioni in [Registrare il dispositivo Windows in Intune](enroll-your-device-in-intune-windows.md)..

**Opzione 2: Abilitare BitLocker**

1.  Cercare e quindi avviare l'app **Gestione BitLocker**.

2.  Fare clic su **Attiva BitLocker** e quindi seguire le istruzioni specificate per crittografare le singole unità.

3.  Verificare che il dispositivo sia registrato con Intune seguendo le istruzioni in [Registrare il dispositivo Windows in Intune](enroll-your-device-in-intune-windows.md)..


### Vedere anche
[Uso del dispositivo Windows con Intune](using-your-windows-device-with-intune.md)

<!--HONumber=May16_HO1-->


