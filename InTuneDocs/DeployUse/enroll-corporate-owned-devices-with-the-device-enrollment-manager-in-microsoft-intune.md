---
# required metadata

title: Registrare dispositivi di proprietà dell'azienda con il manager di registrazione dispositivi in Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrare i dispositivi di proprietà dell'azienda con Manager di registrazione dispositivi in Microsoft Intune
Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un singolo account utente. L'account del *manager di registrazione dispositivi* è uno speciale account di Intune che dispone dell'autorizzazione per registrare più di cinque dispositivi. È possibile assegnare a un gestore del negozio o a un supervisore, ad esempio, un account di manager di registrazione dispositivi per consentire l'esecuzione delle operazioni seguenti:

-   Registrare dispositivi in Intune

-   Accedere al portale aziendale per ottenere le app aziendali

-   Installare e disinstallare il software

-   Configurare l'accesso ai dati aziendali


**Esempi di scenario con un manager di registrazione dispositivi:** Un ristorante vuole adottare tablet POS per il personale di sala e il monitoraggio degli ordini per il personale di cucina. I dipendenti non hanno quindi bisogno di accedere a dati aziendali o di effettuare l'accesso come utente. L'amministratore di Intune crea un account di manager di registrazione dispositivi e registra i dispositivi di proprietà dell'azienda con tale account. In alternativa, l'amministratore potrebbe concedere le credenziali di manager di registrazione dispositivi a un responsabile del ristorante, per consentirgli di registrare e gestire i dispositivi.

L'amministratore o il manager può quindi distribuire app specifiche del ruolo nei dispositivi del ristorante. Un amministratore può inoltre selezionare il dispositivo nella console di Intune e ritirarlo dalla gestione dei dispositivi mobili con la console di amministrazione.

I dispositivi registrati con l'account di un manager di registrazione di dispositivi presentano le restrizioni seguenti:
  - Nessun utente specifico. Tutti i dispositivi sono "senza utente". Pertanto, nessun accesso alla posta elettronica o ai dati aziendali, anche se la VPN, ad esempio, può comunque consentire l'accesso ai dati alle app dei dispositivi
  - Nessun accesso condizionale. Questi infatti sono scenari per utente
  - Nessuna reimpostazione dei dispositivi dal portale aziendale
  - Nessuna app Apple VPP (Volume Purchase Program) a causa della necessità di un ID Apple per utente per la gestione delle app
  - Non è possibile neanche la registrazione ad Apple Configurator o a un programma di registrazione di dispositivi di Apple (dispositivi iOS)

> [!NOTE]
> Gli account utente di manager di registrazione dispositivi con più di 20 dispositivi registrati potrebbero riscontrare problemi nell'uso dell'app Portale aziendale. Per distribuire le app aziendali ai dispositivi gestiti con il manager di registrazione dispositivi, distribuire l'app Portale aziendale come **Installazione richiesta** all'account utente del manager di registrazione dispositivi.
> Per consentire prestazioni migliori, se si visualizza l'app Portale aziendale in un dispositivo manager di registrazione dispositivi, vengono visualizzati solo i dispositivi locali e solo se il dispositivo è stato registrato tramite l'app Portale aziendale. La gestione remota di altri dispositivi manager di registrazione dispositivi è possibile solo dalla console di Intune.

## Creare account del manager di registrazione dispositivi
Gli account manager di registrazione dispositivi sono account utente con l'autorizzazione per registrare un numero elevato di dispositivi di proprietà dell'azienda. Solo gli utenti presenti nella console di Intune possono essere manager di registrazione dispositivi.

#### Aggiungere un manager di registrazione dispositivi a Intune

1.  Passare al [portale per gli account di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) ed eseguire l'accesso con l'account amministratore.

2.  Fare clic su **Aggiungi**.

3.  Verificare che sia elencato l'account utente che sarà un manager di registrazione dispositivi. In caso contrario, per aggiungere l'utente fare clic su **Nuovo** e completare il processo di aggiunta utente. È necessaria una licenza di sottoscrizione per ciascun utente che accede al servizio e il *manager di registrazione dispositivi* non può essere un amministratore di Intune. Determinare se è necessario aggiungere altre licenze prima di usare questa funzionalità.

4.  Accedere alla [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) con le credenziali di amministratore.

5.  Nel riquadro di spostamento fare clic su **Amministrazione**, passare a **Gestione amministratori** , quindi selezionare **Manager di registrazione dispositivi**. Verrà visualizzata la pagina Manager di registrazione dispositivi.

6.  Fare clic su **Aggiungi**. Verrà visualizzata la finestra di dialogo **Aggiungi manager di registrazione dispositivi** .

7.  Immettere l' **ID utente** dell'account Intune e quindi fare clic su **OK**. L'utente manager di registrazione dispositivi non può essere un amministratore di Intune.

8.  Il manager di registrazione dispositivi ora può registrare i dispositivi mobili usando la stessa procedura usata da un utente finale per uno scenario BYOD nel Portale aziendale.

## Eliminare un manager di registrazione dispositivi da Intune

1.  Accedere al [portale di amministrazione di Microsoft Intune](http://manage.microsoft.com) con le credenziali di amministratore.

2.  Nel riquadro di spostamento fare clic su **Amministrazione** e passare a **Gestione amministratori** , quindi selezionare **Manager di registrazione dispositivi**. Verrà visualizzata la pagina Manager di registrazione dispositivi.

3.  Selezionare l' **utente** manager di registrazione dispositivi da eliminare e quindi fare clic su **Elimina**. Questo utente non verrà eliminato da Intune e i dispositivi gestiti da questo utente rimarranno registrati in Intune. L'eliminazione di un manager di registrazione dispositivi impedisce che l'utente registri più dispositivi in Intune.

4.  Fare clic su **Sì** per confermare l'eliminazione del manager di registrazione dispositivi.

L'eliminazione di un manager di registrazione dispositivi non influisce sui dispositivi registrati. Quando viene eliminato un manager di registrazione dispositivi:

-   I dispositivi registrati non sono interessati

-   I dispositivi registrati continuano a essere completamente gestiti

-   Le credenziali dell'account del manager di registrazione dispositivi eliminato restano valide per collegarsi al Portale aziendale per l'accesso alle app

-   Le credenziali dell'account del manager di registrazione dispositivi eliminato non possono ancora cancellare o disattivare i dispositivi

-   La relazione dell'account del manager di registrazione dispositivi per eliminato con i dispositivi registrati resta valida, ma non è possibile registrare ulteriori dispositivi


<!--HONumber=May16_HO3-->


