---
title: "Registrare i dispositivi iOS di proprietà dell'azienda | Microsoft Intune"
description: "Registrazione di dispositivi iOS di proprietà dell'azienda usando il programma di registrazione dispositivi di Apple o Apple Configurator"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9b7b8f6e5182e228458f5ea75e804a638f1e2a2b
ms.openlocfilehash: ca05e94e72269c11db24b667f1d113c794cd8b23


---

# Registrare i dispositivi iOS di proprietà dell'azienda in Microsoft Intune
Microsoft Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda mediante il programma di registrazione dispositivi di Apple (DEP) o lo strumento [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) eseguito in un computer Mac.

**Prerequisito:**  [certificato per Apple Push Notification Service](set-up-ios-and-mac-management-with-microsoft-intune.md)

I dispositivi iOS aziendali possono essere registrati in tre modi:

-   **Apple Configurator**: i dispositivi iOS possono essere registrati esportando un profilo di registrazione aziendale e collegando tali dispositivi mobili a un Mac che esegue Apple Configurator. Apple Configurator supporta due forme di registrazione:

    - **Registrazione di Assistente configurazione** : esegue il ripristino delle impostazioni predefinite del dispositivo e lo prepara per consentire al nuovo utente del dispositivo di installarlo. Questo metodo prevede che l'amministratore connetta tramite USB il dispositivo iOS a un computer Mac in cui è in esecuzione [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) per preconfigurare la registrazione. A questo punto i dispositivi vengono consegnati ai rispettivi utenti che eseguono il processo Assistente configurazione, che configura il dispositivo con le credenziali dell'account aziendale o dell'istituto di istruzione e completa il processo di registrazione. [Registrare dispositivi iOS con Apple Configurator e Assistente configurazione](ios-setup-assistant-enrollment-in-microsoft-intune.md)

    - **Registrazione diretta**: crea un file compatibile con Apple Configurator da usare durante la preparazione dei dispositivi. Non viene eseguito il ripristino delle impostazioni di fabbrica del dispositivo, che risulta però non associato a un utente. Questo metodo prevede che l'amministratore connetta tramite USB il dispositivo iOS a un computer Mac in cui è in esecuzione [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) per registrare il dispositivo. [Registrare dispositivi iOS con la registrazione diretta di Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md)

-   **Programma di registrazione dispositivi (DEP)**: distribuisce un profilo di registrazione via etere ai dispositivi acquistati tramite il programma di registrazione dispositivi di Apple (DEP). Quando l'utente esegue Assistente configurazione nel dispositivo, il dispositivo viene registrato in Intune.  La registrazione dei dispositivi registrati tramite DEP non può essere annullata dagli utenti. [Registrare dispositivi iOS con il programma di registrazione dispositivi](ios-device-enrollment-program-in-microsoft-intune.md)

## Utilizzo del portale aziendale nei dispositivi registrati con DEP o Apple Configurator

I dispositivi configurati con affinità utente possono installare ed eseguire l'app Portale aziendale per scaricare le app e gestire i dispositivi. Quando gli utenti ricevono i dispositivi, devono eseguire alcuni passaggi supplementari per completare l'Assistente configurazione e installare l'app Portale aziendale.

Come registrare i dispositivi iOS di proprietà dell'azienda con l'affinità utente
1. Quando gli utenti accendono i dispositivi, viene chiesto di completare l'Assistente configurazione. Durante la configurazione, agli utenti viene chiesto di fornire le credenziali. Devono usare le credenziali (nome personale univoco o UPN) associate alla propria sottoscrizione in Intune.

2. Durante la configurazione, agli utenti viene chiesto di fornire un ID Apple. L'ID Apple è necessario per consentire al dispositivo di installare il Portale aziendale. È possibile specificare un ID Apple anche dopo la conclusione della configurazione dal menu di impostazioni iOS.

3. Al termine dell'installazione, il dispositivo iOS deve installare l'app Portale aziendale dall'App Store, ad esempio Portale aziendale di Microsoft Intune.

4. A questo punto l'utente può accedere al Portale aziendale con l'UPN usato durante la configurazione del dispositivo.

5. Dopo l'accesso, viene chiesto di registrare il dispositivo. Il primo passaggio consiste nell'identificazione del dispositivo. L'applicazione visualizza un elenco di dispositivi iOS già registrati dall'azienda e assegnati all'account di Intune dell'utente finale. Scegliere il dispositivo corrispondente.

  Se il dispositivo non è registrato dall'azienda, selezionare "nuovo dispositivo" per continuare con il flusso di registrazione standard.

6. Nella schermata successiva l'utente deve confermare il numero di serie del nuovo dispositivo. L'utente può toccare il collegamento "confermare il numero di serie" per avviare l'app Impostazioni e verificare il numero di serie. Deve quindi immettere gli ultimi 4 caratteri del numero di serie nell'app Portale aziendale.

  Questo passaggio verifica che il dispositivo sia il dispositivo aziendale registrato in Intune. Se il numero di serie sul dispositivo non corrisponde, è stato selezionato il dispositivo errato. Tornare alla schermata precedente e selezionare un dispositivo diverso.

7. Dopo aver verificato il numero di serie, l'app Portale aziendale reindirizza al sito Web del Portale aziendale per completare la registrazione e quindi chiede all'utente di tornare all'app.

8. La registrazione è stata completata. Ora si può usare il dispositivo con il set completo di funzionalità.

### Informazioni sui dispositivi gestiti di proprietà dell'azienda senza affinità utente

Nei dispositivi configurati senza affinità utente non è supportato il Portale aziendale e non si dovrebbe installare l'app. Il Portale aziendale è progettato per gli utenti che hanno credenziali aziendali e richiedono l'accesso a risorse aziendali personalizzate, ad esempio la posta elettronica. I dispositivi registrati senza affinità utente non sono pensati per l'accesso utente dedicato. Chioschi multimediali, POS o dispositivi di utilità condivisi sono casi d'uso tipici per i dispositivi registrati senza affinità utente. Se è necessaria l'affinità utente, assicurarsi che nel profilo di registrazione del dispositivo sia selezionata l'opzione Affinità utente prima di registrare il dispositivo. Per modificare lo stato di affinità in un dispositivo è necessario ritirare il dispositivo e quindi registrarlo nuovamente.



### Vedere anche
[Prepararsi alla registrazione dei dispositivi in Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


