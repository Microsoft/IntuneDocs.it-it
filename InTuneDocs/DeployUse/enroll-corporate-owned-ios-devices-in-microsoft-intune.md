---
# required metadata

title: Registrare dispositivi iOS di proprietà dell'azienda in Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrare i dispositivi iOS di proprietà dell'azienda in Microsoft Intune
Microsoft Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda mediante il programma di registrazione dispositivi di Apple (DEP) o lo strumento [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) eseguito in un computer Mac.

I dispositivi iOS aziendali possono essere registrati in tre modi:

-   **Registrazione di Assistente configurazione** : esegue il ripristino delle impostazioni predefinite del dispositivo e lo prepara per consentire al nuovo utente del dispositivo di installarlo. Questo metodo prevede che l'amministratore connetta tramite USB il dispositivo iOS a un computer Mac che ha in esecuzione Apple Configurator per preconfigurare la registrazione. A questo punto i dispositivi vengono consegnati ai rispettivi utenti che eseguono il processo Assistente configurazione, che configura il dispositivo con le credenziali dell'account aziendale o dell'istituto di istruzione e completa il processo di registrazione. [Registrare dispositivi iOS con Apple Configurator e Assistente configurazione](ios-setup-assistant-enrollment-in-microsoft-intune.md)

-   **Registrazione diretta**: crea un file compatibile con Apple Configurator da usare durante la preparazione dei dispositivi. Non viene eseguito il ripristino delle impostazioni di fabbrica del dispositivo, che risulta però non associato a un utente. Questo metodo prevede che l'amministratore connetta tramite USB il dispositivo iOS a un computer Mac che ha in esecuzione Apple Configurator per registrare il dispositivo. [Registrare dispositivi iOS con la registrazione diretta di Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md)

-   **Programma di registrazione dispositivi (DEP)**: distribuisce un profilo di registrazione via etere ai dispositivi acquistati tramite il programma di registrazione dispositivi di Apple (DEP). Quando l'utente esegue Assistente configurazione nel dispositivo, il dispositivo viene registrato in Intune.  La registrazione dei dispositivi registrati tramite DEP non può essere annullata dagli utenti. [Registrare dispositivi iOS con il programma di registrazione dispositivi](ios-device-enrollment-program-in-microsoft-intune.md)




### Vedere anche
[Prepararsi alla registrazione dei dispositivi in Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


