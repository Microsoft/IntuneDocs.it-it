---
title: "Registrare i dispositivi iOS di proprietà dell&quot;azienda | Microsoft Intune"
description: "Registrazione di dispositivi iOS di proprietà dell&quot;azienda usando il programma di registrazione dispositivi di Apple o Apple Configurator"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 00ca6ea06aa63646d6ede6337f8e70d1ab956c5f
ms.openlocfilehash: cfc97f4ed931a5c7dc5b38eafd0a2d081bc30975


---

# <a name="enroll-corporate-owned-ios-devices-in-microsoft-intune"></a>Registrare i dispositivi iOS di proprietà dell'azienda in Microsoft Intune
Microsoft Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda mediante il programma di registrazione dispositivi di Apple (DEP) o lo strumento [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) eseguito in un computer Mac.

**Prerequisito:** un [certificato per Apple Push Notification Service](set-up-ios-and-mac-management-with-microsoft-intune.md).

È possibile registrare i dispositivi iOS aziendali in tre modi: tramite Apple Configurator, DEP o il portale aziendale.

## <a name="use-apple-configurator"></a>Usare Apple Configurator

È possibile registrare i dispositivi iOS esportando un profilo di registrazione aziendale e collegando tali dispositivi mobili a un Mac che esegue Apple Configurator. Apple Configurator supporta due forme di registrazione:

- **Registrazione di Assistente configurazione**: esegue il ripristino delle impostazioni predefinite del dispositivo e lo prepara per consentire al nuovo utente del dispositivo di installarlo. Questo metodo prevede che l'amministratore connetta il dispositivo iOS tramite USB a un computer Mac in cui è in esecuzione [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) per preconfigurare la registrazione. I dispositivi vengono quindi distribuiti agli utenti che eseguono il processo di Assistente configurazione. Questo processo consente di configurare il dispositivo con le proprie credenziali aziendali o dell'istituto di istruzione e di completare la registrazione. Per altre informazioni, vedere [Enroll iOS devices using Apple Configurator and Setup Assistant](ios-setup-assistant-enrollment-in-microsoft-intune.md) (Registrare dispositivi iOS con Apple Configurator e Assistente configurazione).

- **Registrazione diretta**: crea un file compatibile con Apple Configurator da usare durante la preparazione dei dispositivi. Non viene eseguito il ripristino delle impostazioni di fabbrica del dispositivo, che risulta però non associato a un utente. Questo metodo prevede che l'amministratore connetta il dispositivo iOS tramite USB a un computer Mac in cui è in esecuzione [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) per registrare il dispositivo. Per altre informazioni, vedere [Enroll iOS devices using Apple Configurator Direct Enrollment](ios-direct-enrollment-in-microsoft-intune.md) (Registrare dispositivi iOS con Apple Configurator e Registrazione diretta).

## <a name="use-the-device-enrollment-program-dep"></a>Usare il programma di registrazione dispositivi
Il programma di registrazione dispositivi distribuisce un profilo di registrazione ai dispositivi acquistati tramite il programma di registrazione dispositivi. Quando un utente esegue Assistente configurazione nel dispositivo, il dispositivo viene registrato in Intune.  La registrazione dei dispositivi registrati tramite DEP non può essere annullata dagli utenti. Per altre informazioni, vedere [Enroll Device Enrollment Program iOS devices](ios-device-enrollment-program-in-microsoft-intune.md) (Registrare dispositivi iOS con il programma di registrazione dispositivi).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Usare il portale aziendale nei dispositivi registrati con il programma di registrazione dispositivi o Apple Configurator

I dispositivi configurati con affinità utente possono installare ed eseguire l'app del portale aziendale per scaricare le app e gestire i dispositivi. Dopo che gli utenti ricevono i dispositivi, devono eseguire alcuni passaggi supplementari per completare l'Assistente configurazione e installare l'app del portale aziendale.

L'affinità utente è necessaria per supportare quanto segue:
  - App per la gestione di applicazioni mobili (MAM)
  - Accesso condizionale ai dati aziendali e della posta elettronica
  - App Portale aziendale

**Come registrare i dispositivi iOS di proprietà dell'azienda con l'affinità utente**
1. Quando gli utenti accendono i dispositivi, viene chiesto di completare l'Assistente configurazione. Durante la configurazione, agli utenti viene chiesto di fornire le credenziali. Devono usare le credenziali (nome personale univoco o UPN) associate alla propria sottoscrizione in Intune.

2. Durante la configurazione, agli utenti viene chiesto di fornire un ID Apple. Devono specificare l'ID Apple, per consentire al dispositivo di installare il portale aziendale. Possono inoltre specificare l'ID dal menu delle impostazioni di iOS al termine dell'installazione.

3. Al termine dell'installazione, il dispositivo iOS deve installare l'app del portale aziendale dall'App Store.

4. A questo punto l'utente può accedere al portale aziendale con l'UPN usato durante la configurazione del dispositivo.

5. Dopo l'accesso, viene chiesto di registrare il dispositivo. Il primo passaggio consiste nell'identificazione del dispositivo. L'app visualizza un elenco di dispositivi iOS già registrati dall'azienda e assegnati all'account di Intune dell'utente. L'utente deve scegliere il dispositivo corrispondente.

  Se il dispositivo non è registrato dall'azienda, è necessario selezionare **nuovo dispositivo** per continuare con il flusso di registrazione standard.

6. Nella schermata successiva l'utente deve confermare il numero di serie del nuovo dispositivo. L'utente può toccare il collegamento **confermare il numero di serie** per avviare l'app Impostazioni e verificare il numero di serie. Deve quindi immettere gli ultimi quattro caratteri del numero di serie nell'app del portale aziendale.

  Questo passaggio verifica che il dispositivo sia il dispositivo aziendale registrato in Intune. Se il numero di serie sul dispositivo non corrisponde, è stato selezionato il dispositivo errato. L'utente deve tornare alla schermata precedente e selezionare un dispositivo diverso.

7. Dopo aver verificato il numero di serie, l'app del portale aziendale reindirizza al sito Web del portale aziendale per completare la registrazione. A questo punto, il sito Web chiede all'utente di tornare all'app.

8. La registrazione è stata completata. L'utente può ora usare il dispositivo con il set completo di funzionalità.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Informazioni sui dispositivi gestiti di proprietà dell'azienda senza affinità utente

Nei dispositivi configurati senza affinità utente il portale aziendale non è supportato e non si dovrebbe installare l'app. Il Portale aziendale è progettato per gli utenti che hanno credenziali aziendali e richiedono l'accesso a risorse aziendali personalizzate, ad esempio la posta elettronica. I dispositivi registrati senza affinità utente non sono pensati per l'accesso utente dedicato. Chioschi multimediali, POS o dispositivi di utilità condivisi sono casi d'uso tipici per i dispositivi registrati senza affinità utente.

Se è necessaria l'affinità utente, assicurarsi che nel profilo di registrazione del dispositivo sia selezionata l'opzione **Affinità utente** prima di registrare il dispositivo. Per modificare lo stato di affinità in un dispositivo è necessario ritirare il dispositivo e quindi registrarlo nuovamente.



### <a name="see-also"></a>Vedere anche
[Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO3-->


