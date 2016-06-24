---
# required metadata

title: Consentire agli utenti finali di comprendere i messaggi dell'app Portale aziendale | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Consentire agli utenti finali di comprendere i messaggi dell'app Portale aziendale

Le informazioni seguenti si applicano solo a dispositivi Android 6.0 e versioni successive. Durante la registrazione dei dispositivi, gli utenti finali vedono due messaggi, che vengono visualizzati durante il processo di registrazione:

- Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?
- Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?

Vedere i paragrafi seguenti per informazioni dettagliate su questi messaggi e per le informazioni correlate che è possibile condividere con gli utenti finali.

## Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?

### Testo del messaggio e passaggio in cui viene visualizzato
Il testo del messaggio è **Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?** e viene visualizzato quando gli utenti accedono all'app Portale aziendale per la prima volta per registrare il dispositivo.

### Significato del messaggio
Il messaggio chiede agli utenti di consentire l'invio del numero di telefono e del codice IMEI del loro dispositivo al servizio Intune e la relativa visualizzazione di questi elementi nella console di amministrazione nella pagina Hardware.

> [!NOTE]
> **L'app Portale aziendale non effettua o gestisce mai chiamate telefoniche.** Il testo del messaggio è controllato da Google e non può essere modificato.

Per visualizzare la pagina **Hardware**, accedere a **Gruppi** > **Tutti i dispositivi mobili** > **Dispositivi**. Selezionare il dispositivo dell'utente e passare a **Visualizza proprietà** > **Hardware**.

### Cosa succede se gli utenti consentono o non consentono l'accesso
Se gli utenti consentono l'accesso, il numero di telefono e il codice IMEI del dispositivo verranno visualizzati nella pagina Hardware nella console di amministrazione.

Se gli utenti non consentono l'accesso, possono continuare a usare l'app Portale aziendale e registrare il dispositivo, ma il numero di telefono e il codice IMEI del loro dispositivo risulteranno vuoti nella pagina Hardware nella console di amministrazione. Al secondo accesso all'app Portale aziendale dopo aver negato l'accesso, nel messaggio sarà visualizzata la casella di controllo **Non visualizzare più questo messaggio** che gli utenti potranno selezionare per evitare di visualizzare di nuovo il messaggio.

Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato all'accesso successivo all'app Portale aziendale dopo la registrazione.</br></br>Se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Telefono** e quindi attivare l'autorizzazione.

### Dove trovare altre informazioni a riguardo
Passaggio 5 in [Registrare il dispositivo Android in Intune](/Intune/EndUser/enroll-your-device-in-intune-android)

## Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?

### Testo del messaggio e passaggio in cui viene visualizzato
Il testo del messaggio è **Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?**, e viene visualizzato quando gli utenti toccano **Invia dati** per inviare i log di dati all'amministratore IT.

### Significato del messaggio
Il messaggio richiede agli utenti di consentire al dispositivo di scrivere i log di dati nella scheda SD del dispositivo e abilitare lo spostamento dei log tramite un cavo USB.   

> [!NOTE]
> **L'app Portale aziendale non accede mai a foto, elementi multimediali e file degli utenti.** Il testo del messaggio è controllato da Google e non può essere modificato.

### Cosa succede se gli utenti consentono o non consentono l'accesso
Se gli utenti consentono l'accesso, i log verranno copiati nella scheda SD.

Se gli utenti non consentono l'accesso, possono comunque inviare i log di dati, ma questi non verranno copiati nella scheda SD del dispositivo.

Al secondo accesso all'app Portale aziendale dopo aver negato l'accesso, nel messaggio sarà visualizzata la casella di controllo **Non visualizzare più questo messaggio** che gli utenti potranno selezionare per evitare di visualizzare di nuovo il messaggio. Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato al successivo tentativo di invio dei log. Se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Archiviazione** e quindi attivare l'autorizzazione.

### Dove trovare altre informazioni a riguardo
[Inviare i log dei dati di diagnostica all'amministratore IT tramite posta elettronica](/Intune/EndUser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)


### Vedere anche
[Informazioni sull'uso di Intune per gli utenti finali](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune.md)


<!--HONumber=May16_HO2-->


