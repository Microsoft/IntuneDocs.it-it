---
title: Registrare con Manager di registrazione dispositivi | Microsoft Intune
description: "L'account di Manager di registrazione dispositivi consente di gestire un numero elevato di dispositivi mobili condivisi e di proprietà dell'azienda con un unico account utente."
keywords: 
author: NathBarn
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
ms.sourcegitcommit: de3296e81c88b3ac04e3ba3f3d3ca222a59df7bd
ms.openlocfilehash: 450a5764005643a2f890780530d1f2880a4e517b


---


# Registrare i dispositivi di proprietà dell'azienda con Manager di registrazione dispositivi in Microsoft Intune
Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un singolo account utente. L'account *manager di registrazione dispositivi * (DEM, Device Enrollment Manager) è un account speciale di Intune con l'autorizzazione a registrare fino a 1000 dispositivi. Usare i dispositivi registrati tramite l'account manager di registrazione dispositivi come dispositivi condivisi piuttosto che come dispositivi personali ("BYOD"). Gli utenti non saranno in grado, ad esempio, di usare le app di posta elettronica "native". È possibile assegnare a un gestore del negozio o a un supervisore, ad esempio, un account di manager di registrazione dispositivi per consentire l'esecuzione delle operazioni seguenti:

-   Registrare dispositivi in Intune

-   Accedere al portale aziendale per ottenere le app aziendali

-   Installare e disinstallare il software

-   Configurare l'accesso ai dati aziendali


**Esempi di scenario con un manager di registrazione dispositivi:** Un ristorante vuole adottare tablet POS per il personale di sala e il monitoraggio degli ordini per il personale di cucina. I dipendenti non hanno quindi bisogno di accedere a dati aziendali o di effettuare l'accesso come utente. L'amministratore di Intune crea un account di manager di registrazione dispositivi e registra i dispositivi di proprietà dell'azienda con tale account. In alternativa, l'amministratore potrebbe concedere le credenziali di manager di registrazione dispositivi a un responsabile del ristorante, per consentirgli di registrare e gestire i dispositivi.

L'amministratore o il manager può quindi distribuire app specifiche del ruolo nei dispositivi del ristorante. Un amministratore può inoltre selezionare il dispositivo nella console di Intune e ritirarlo dalla gestione dei dispositivi mobili con la console di amministrazione.

I dispositivi registrati con un account manager di registrazione dispositivi presentano le restrizioni seguenti:
  - Nessun utente specifico. Tutti i dispositivi sono "senza utente". Pertanto, nessun accesso alla posta elettronica o ai dati aziendali, anche se la VPN, ad esempio, può comunque consentire l'accesso ai dati alle app dei dispositivi
  - Nessun accesso condizionale. Questi infatti sono scenari per utente
  - Nessuna possibilità di reimpostazione dei dispositivi dal portale aziendale
  - Visualizzazione del solo dispositivo locale nell'app Portale aziendale o nel sito web
  - Nessuna app Apple VPP (Volume Purchase Program) a causa della necessità di un ID Apple per utente per la gestione delle app
  - Non è possibile neanche la registrazione ad Apple Configurator o a un programma di registrazione di dispositivi di Apple (dispositivi iOS)

> [!NOTE]
> Per distribuire le app aziendali ai dispositivi gestiti con il manager di registrazione dispositivi, distribuire l'app Portale aziendale come **Installazione richiesta** all'account utente del manager di registrazione dispositivi.
> Per consentire prestazioni migliori, se si visualizza l'app Portale aziendale in un dispositivo DEM, viene visualizzato solo il dispositivo locale. La gestione remota di altri dispositivi DEM è possibile solo dalla console di amministrazione di Intune.

## Creare account del manager di registrazione dispositivi
Gli account manager di registrazione dispositivi sono account utente con l'autorizzazione per registrare un numero elevato di dispositivi di proprietà dell'azienda. Solo gli utenti presenti nella console di Intune possono essere manager di registrazione dispositivi.

#### Aggiungere un manager di registrazione dispositivi a Intune

1.  Passare al [portale per gli account di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) ed eseguire l'accesso con l'account amministratore.

2.  Scegliere **Aggiungi utente**.

3.  Verificare che sia elencato l'account utente che sarà un manager di registrazione dispositivi. In caso negativo, per aggiungere l'utente scegliere **Nuovo** e completare il processo di aggiunta dell'utente. È necessaria una licenza di sottoscrizione per ciascun utente che accede al servizio e il *manager di registrazione dispositivi* non può essere un amministratore di Intune. Determinare se è necessario aggiungere altre licenze prima di usare questa funzionalità.

4.  Accedere alla [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) con le credenziali di amministratore.

5.  Nel riquadro di spostamento scegliere **Amministrazione**, passare a **Gestione amministratori** e selezionare **Manager di registrazione dispositivi**. Verrà visualizzata la pagina Manager di registrazione dispositivi.

6.  Scegliere **Aggiungi...**. Verrà visualizzata la finestra di dialogo **Aggiungi manager di registrazione dispositivi** .

7.  Immettere l' **ID utente** dell'account Intune e quindi scegliere **OK**. L'utente manager di registrazione dispositivi non può essere un amministratore di Intune.

8.  Il manager di registrazione dispositivi ora può registrare i dispositivi mobili usando la stessa procedura usata da un utente finale per uno scenario BYOD nel Portale aziendale.

## Eliminare un manager di registrazione dispositivi da Intune

1.  Accedere al [portale di amministrazione di Microsoft Intune](http://manage.microsoft.com) con le credenziali di amministratore.

2.  Nel riquadro di spostamento scegliere **Amministrazione**, passare a **Gestione amministratori** e selezionare **Manager di registrazione dispositivi**. Verrà visualizzata la pagina Manager di registrazione dispositivi.

3.  Selezionare l'**utente** manager di registrazione dispositivi da eliminare e quindi scegliere **Elimina**. Questo utente non verrà eliminato da Intune e i dispositivi gestiti da questo utente rimarranno registrati in Intune. L'eliminazione di un manager di registrazione dispositivi impedisce che l'utente registri più dispositivi in Intune.

4.  Scegliere **Sì** per confermare l'eliminazione del manager di registrazione dispositivi.

L'eliminazione di un manager di registrazione dispositivi non influisce sui dispositivi registrati. Quando viene eliminato un manager di registrazione dispositivi:

-   I dispositivi registrati non sono interessati

-   I dispositivi registrati continuano a essere completamente gestiti

-   Le credenziali dell'account del manager di registrazione dispositivi eliminato restano valide per collegarsi al Portale aziendale per l'accesso alle app

-   Le credenziali dell'account del manager di registrazione dispositivi eliminato non possono ancora cancellare o disattivare i dispositivi

-   La relazione dell'account del manager di registrazione dispositivi per eliminato con i dispositivi registrati resta valida, ma non è possibile registrare ulteriori dispositivi



<!--HONumber=Jul16_HO5-->


