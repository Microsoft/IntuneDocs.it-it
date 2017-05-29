---
title: Registrare con il manager di registrazione dispositivi | Documentazione Microsoft
description: "L&quot;account del manager di registrazione dispositivi consente di gestire un numero elevato di dispositivi mobili condivisi e di proprietà dell&quot;azienda con un unico account utente."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d1f63a9e65435e2cfc421c23de3ad87363bc446d
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---


# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Registrare i dispositivi di proprietà dell'azienda con il manager di registrazione dispositivi in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un singolo account utente. L'account del *manager di registrazione dispositivi* (DEM, Device Enrollment Manager) è un account utente speciale che consente di registrare fino a 1.000 dispositivi. Gli utenti esistenti vengono aggiunti all'account del manager di registrazione dispositivi per rendere disponibili le funzionalità DEM. Ogni dispositivo registrato usa una singola licenza. Si consiglia di usare i dispositivi registrati tramite tale account come dispositivi condivisi, ovvero senza affinità utente, piuttosto che come dispositivi personali ("BYOD").  

Per poter essere aggiunti come manager di registrazione dispositivi, gli utenti devono essere presenti nel portale di Azure. Per una sicurezza ottimale, l'utente manager di registrazione dispositivi non deve essere anche amministratore di Intune.

>[!NOTE]
>Il metodo di registrazione del manager di registrazione dispositivi non può essere usato con [Assistente configurazione di Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) o con la [registrazione diretta](ios-direct-enrollment-in-microsoft-intune.md) o con il [metodo del programma di registrazione dei dispositivi](ios-device-enrollment-program-in-microsoft-intune.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Esempio di scenario con manager di registrazione dispositivi

Un ristorante vuole offrire 50 tablet POS al personale di sala e monitor per gli ordini per il personale di cucina. I dipendenti non hanno bisogno di accedere ai dati aziendali o di accedere come utenti. L'amministratore di Intune crea un account del manager di registrazione dispositivi e aggiunge un supervisore del ristorante all'account offrendo le funzionalità DEM al supervisore. Il supervisore potrà quindi registrare 50 tablet usando le credenziali DEM.

Solo gli utenti presenti nella console di Intune possono essere manager di registrazione dispositivi. L'utente manager di registrazione dispositivi non può essere un amministratore di Intune.

L'utente manager di registrazione dispositivi può:

-   Registrare un massimo di 1000 dispositivi in Intune
-   Usare l'app Portale aziendale per accedere alle app aziendali
-   Configurare l'accesso ai dati aziendali distribuendo app specifiche dei ruoli ai tablet

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitazioni dei dispositivi registrati con un account del manager di registrazione dispositivi

I dispositivi registrati con un account di manager di registrazione dispositivi presentano le restrizioni seguenti:

  - Non sono presenti utenti di dispositivi specifici. Per questa ragione, non è presente alcun accesso alla posta elettronica o ai dati aziendali. Tuttavia la VPN, ad esempio, può essere ancora usata per offrire app per dispositivi con accesso ai dati.

  - Nessun accesso condizionale. Questi infatti sono scenari per utente.

  - L'utente manager di registrazione dispositivi non può annullare la registrazione di dispositivi registrati DEM sul dispositivo tramite il portale aziendale. Questa operazione può essere eseguita dall'amministratore di Intune ma non dall'utente manager di registrazione dispositivi.

  - Visualizzazione del solo dispositivo locale nell'app o nel sito Web del portale aziendale.

  - Gli utenti non possono usare le app Volume Purchase Program di Apple poiché è necessario un ID Apple per utente per la gestione delle app.

  - (Solo iOS) Se si usa un manager di registrazione dispositivi per la registrazione dei dispositivi iOS, non è possibile usare Apple Configurator o il programma di registrazione dispositivi di Apple per la registrazione dei dispositivi.

> [!NOTE]
> Per distribuire le app aziendali ai dispositivi gestiti con il manager di registrazione dispositivi, distribuire l'app Portale aziendale come **Installazione richiesta** all'account utente del manager di registrazione dispositivi.
> Per consentire prestazioni migliori, se si visualizza l'app Portale aziendale in un dispositivo DEM, viene visualizzato solo il dispositivo locale. La gestione remota di altri dispositivi DEM è possibile solo dalla console di amministrazione di Intune.


## <a name="add-a-device-enrollment-manager"></a>Aggiungere un manager di registrazione dispositivi

1.  Assicurarsi che l'utente che si vuole aggiungere all'account del manager di registrazione dispositivi sia già presente. Se è necessario aggiungere l'utente, accedere al [Portale di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) e seguire la procedura descritta in [Aggiungere utenti singolarmente o in blocco a Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

2.  Accedere alla [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) con le credenziali di amministratore.

3.  Nel riquadro di spostamento scegliere **Amministrazione**, passare a **Gestione amministratori** e selezionare **Manager di registrazione dispositivi**. Verrà visualizzata la pagina **Manager di registrazione dispositivi**.

4.  Scegliere **Aggiungi...**. Verrà visualizzata la finestra di dialogo **Aggiungi manager di registrazione dispositivi** .

5.  Immettere l'**ID utente** dell'account Intune e quindi scegliere **OK**.

    L'utente manager di registrazione dispositivi può ora registrare i dispositivi mobili usando la stessa procedura usata da un utente finale per uno scenario BYOD nel portale aziendale. L'utente finale responsabile può installare l'app Portale aziendale e registrare il dispositivo usando le proprie credenziali DEM su un massimo di 1000 dispositivi. Per la procedura di registrazione dell'utente finale per ogni piattaforma, vedere:

  - [Registrare il dispositivo iOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)
  - [Registrare il dispositivo macOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)
  - [Registrare il dispositivo Android in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)
  - [Registrare il dispositivo Windows in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Eliminare un manager di registrazione dispositivi da Intune

1.  Accedere al [portale di amministrazione di Microsoft Intune](https://manage.microsoft.com) con le credenziali di amministratore.

2.  Nel riquadro di spostamento scegliere **Amministrazione**, passare a **Gestione amministratori** e selezionare **Manager di registrazione dispositivi**. Verrà visualizzata la pagina **Manager di registrazione dispositivi**.

3.  Selezionare l'**utente** manager di registrazione dispositivi da eliminare e quindi scegliere **Elimina**. Questo utente non verrà eliminato da Intune e i dispositivi gestiti da questo utente rimarranno registrati in Intune. L'eliminazione di un manager di registrazione dispositivi impedisce che l'utente registri più dispositivi in Intune.

4.  Scegliere **Sì** per confermare l'eliminazione del manager di registrazione dispositivi.

L'eliminazione di un manager di registrazione dispositivi non influisce sui dispositivi registrati. Quando viene eliminato un manager di registrazione dispositivi:

-   I dispositivi registrati non sono interessati.

-   I dispositivi registrati continuano a essere completamente gestiti.

-   Le credenziali dell'account del manager di registrazione dispositivi eliminato restano valide per collegarsi al portale aziendale per l'accesso alle app.

-   Le credenziali dell'account del manager di registrazione dispositivi eliminato non possono ancora cancellare o disattivare i dispositivi.

-   La relazione dell'account del manager di registrazione dispositivi eliminato con i dispositivi registrati resta valida, ma non è possibile registrare ulteriori dispositivi.

