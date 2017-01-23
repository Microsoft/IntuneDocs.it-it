---
title: Registrare con il manager di registrazione dispositivi | Documentazione Microsoft
description: "L&quot;account del manager di registrazione dispositivi consente di gestire un numero elevato di dispositivi mobili condivisi e di proprietà dell&quot;azienda con un unico account utente."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 751c6bee73175b8e6ac5ad192f12540520c676c0


---


# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Registrare i dispositivi di proprietà dell'azienda con il manager di registrazione dispositivi in Microsoft Intune
Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un singolo account utente. L'account del *manager di registrazione dispositivi* è un account speciale di Intune che consente di registrare fino a 1000 dispositivi. Ogni dispositivo registrato usa una singola licenza. Si consiglia di usare i dispositivi registrati tramite tale account come dispositivi condivisi piuttosto che come dispositivi personali ("BYOD"). Gli utenti non saranno in grado, ad esempio, di usare le app di posta elettronica "native". Le licenze per DEM vengono concesse in base al dispositivo, non all'utente.

È, ad esempio, possibile assegnare un account utente di manager di registrazione dispositivi a un gestore del negozio o a un supervisore per consentire l'esecuzione delle operazioni seguenti:

-   Registrare dispositivi in Intune.

-   Accedere al portale aziendale per ottenere le app aziendali.

-   Installare e disinstallare il software.

-   Configurare l'accesso ai dati aziendali.


**Scenario con un manager di registrazione dispositivi:** un ristorante vuole adottare tablet POS per il personale di sala e il monitoraggio degli ordini per il personale di cucina. I dipendenti non hanno bisogno di accedere ai dati aziendali o di accedere come utenti. L'amministratore di Intune crea un account di manager di registrazione dispositivi e registra i dispositivi di proprietà dell'azienda con tale account. In alternativa, l'amministratore può concedere le credenziali di manager di registrazione dispositivi a un responsabile del ristorante, per consentirgli di registrare e gestire i dispositivi.

L'amministratore o il manager può quindi distribuire app specifiche del ruolo nei dispositivi del ristorante. Un amministratore può inoltre selezionare il dispositivo nella console di Intune e ritirarlo dalla gestione dei dispositivi mobili con la console di amministrazione.

I dispositivi registrati con un account di manager di registrazione dispositivi presentano le restrizioni seguenti:
  - Nessun dispositivo "utente" specifico. Non è quindi possibile alcun accesso ai dati della posta elettronica o della società. Tuttavia la connessione VPN, ad esempio, può comunque fornire app per dispositivi con accesso ai dati.
  - Nessun accesso condizionale. Questi infatti sono scenari per utente.
  - Nessuna possibilità di reimpostazione dei dispositivi dal portale aziendale.
  - Visualizzazione del solo dispositivo locale nell'app o nel sito Web del portale aziendale.
  - Nessuna possibilità di usare app Apple VPP (Volume Purchase Program) a causa della necessità di un ID Apple per utente per la gestione delle app.
  - (iOS) Nessuna possibilità di iscrizione ad Apple Configurator o al programma di registrazione dispositivi di Apple (DEP), ma possibilità di registrare i dispositivi gestiti da DEP o da Apple Configurator senza affinità utente.

> [!NOTE]
> Per distribuire le app aziendali ai dispositivi gestiti con il manager di registrazione dispositivi, distribuire l'app Portale aziendale come **Installazione richiesta** all'account utente del manager di registrazione dispositivi.
> Per consentire prestazioni migliori, se si visualizza l'app Portale aziendale in un dispositivo DEM, viene visualizzato solo il dispositivo locale. La gestione remota di altri dispositivi DEM è possibile solo dalla console di amministrazione di Intune.

## <a name="create-device-enrollment-manager-accounts"></a>Creare account del manager di registrazione dispositivi
Gli account manager di registrazione dispositivi sono account utente con l'autorizzazione per registrare un numero elevato di dispositivi di proprietà dell'azienda. Solo gli utenti presenti nella console di Intune possono essere manager di registrazione dispositivi.

#### <a name="add-a-device-enrollment-manager-to-intune"></a>Aggiungere un manager di registrazione dispositivi a Intune

1.  Passare al [portale per gli account di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) ed eseguire l'accesso con l'account amministratore.

2.  Scegliere **Aggiungi utente**.

3.  Verificare che sia elencato l'account utente che sarà un manager di registrazione dispositivi. In caso negativo, per aggiungere l'utente scegliere **Nuovo** e completare il processo di **aggiunta dell'utente**. È necessaria una licenza di sottoscrizione per ciascun utente che accede al servizio. Il manager di registrazione dispositivi non può essere un amministratore di Intune. Verificare se è necessario aggiungere altre licenze prima di usare questa funzionalità.

4.  Accedere alla [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) con le credenziali di amministratore.

5.  Nel riquadro di spostamento scegliere **Amministrazione**, passare a **Gestione amministratori** e selezionare **Manager di registrazione dispositivi**. Verrà visualizzata la pagina **Manager di registrazione dispositivi**.

6.  Scegliere **Aggiungi...**. Verrà visualizzata la finestra di dialogo **Aggiungi manager di registrazione dispositivi** .

7.  Immettere l'**ID utente** dell'account Intune e quindi scegliere **OK**. L'utente manager di registrazione dispositivi non può essere un amministratore di Intune.

8.  Il manager di registrazione dispositivi ora può registrare i dispositivi mobili usando la stessa procedura usata da un utente finale per uno scenario BYOD nel portale aziendale. L'utente finale responsabile può installare l'app Portale aziendale e registrare il dispositivo usando le proprie credenziali DEM su un massimo di 1000 dispositivi.

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Eliminare un manager di registrazione dispositivi da Intune

1.  Accedere al [portale di amministrazione di Microsoft Intune](http://manage.microsoft.com) con le credenziali di amministratore.

2.  Nel riquadro di spostamento scegliere **Amministrazione**, passare a **Gestione amministratori** e selezionare **Manager di registrazione dispositivi**. Verrà visualizzata la pagina **Manager di registrazione dispositivi**.

3.  Selezionare l'**utente** manager di registrazione dispositivi da eliminare e quindi scegliere **Elimina**. Questo utente non verrà eliminato da Intune e i dispositivi gestiti da questo utente rimarranno registrati in Intune. L'eliminazione di un manager di registrazione dispositivi impedisce che l'utente registri più dispositivi in Intune.

4.  Scegliere **Sì** per confermare l'eliminazione del manager di registrazione dispositivi.

L'eliminazione di un manager di registrazione dispositivi non influisce sui dispositivi registrati. Quando viene eliminato un manager di registrazione dispositivi:

-   I dispositivi registrati non sono interessati.

-   I dispositivi registrati continuano a essere completamente gestiti.

-   Le credenziali dell'account del manager di registrazione dispositivi eliminato restano valide per collegarsi al portale aziendale per l'accesso alle app.

-   Le credenziali dell'account del manager di registrazione dispositivi eliminato non possono ancora cancellare o disattivare i dispositivi.

-   La relazione dell'account del manager di registrazione dispositivi eliminato con i dispositivi registrati resta valida, ma non è possibile registrare ulteriori dispositivi.



<!--HONumber=Dec16_HO2-->


