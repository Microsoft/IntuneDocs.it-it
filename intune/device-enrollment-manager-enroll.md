---
title: Registrare i dispositivi - Manager di registrazione dispositivi
titlesuffix: Azure portal
description: Usare l'account del manager di registrazione dispositivi per registrare i dispositivi in Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5caf60d0512a33c0c88f4305b1a9eb189112ba02
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="enroll-devices-using-device-enrollment-manager"></a>Registrare i dispositivi con il manager di registrazione dispositivi

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un singolo account utente. L'account del *manager di registrazione dispositivi* (DEM, Device Enrollment Manager) è un account utente speciale che consente di registrare fino a 1.000 dispositivi. Gli utenti esistenti vengono aggiunti all'account del manager di registrazione dispositivi per rendere disponibili le funzionalità DEM. Ogni dispositivo registrato usa una singola licenza. Si consiglia di usare i dispositivi registrati tramite tale account come dispositivi condivisi piuttosto che come dispositivi personali ("BYOD").  

Per poter essere aggiunti come manager di registrazione dispositivi, gli utenti devono essere presenti nel portale di Azure. Per una sicurezza ottimale, l'utente manager di registrazione dispositivi non deve essere anche amministratore di Intune.

>[!NOTE]
>Il metodo di registrazione DEM non può essere usato con questi altri metodi di registrazione: [Apple Configurator tramite l'Assistente configurazione](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator con registrazione diretta](apple-configurator-direct-enroll-ios.md), [Apple School Manager (ASM)](apple-school-manager-set-up-ios.md) o [Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Esempio di scenario con manager di registrazione dispositivi

Un ristorante vuole offrire 50 tablet POS al personale di sala e monitor per gli ordini per il personale di cucina. I dipendenti non hanno bisogno di accedere ai dati aziendali o di accedere come utenti. L'amministratore di Intune crea un account del manager di registrazione dispositivi e aggiunge un supervisore del ristorante all'account offrendo le funzionalità DEM al supervisore. Il supervisore potrà quindi registrare 50 tablet usando le credenziali DEM.

Solo gli utenti presenti nel portale di Azure possono essere manager di registrazione dispositivi. L'utente manager di registrazione dispositivi non può essere un amministratore di Intune.

L'utente manager di registrazione dispositivi può:

-   Registrare un massimo di 1000 dispositivi in Intune
-   Accedere al portale aziendale per ottenere le app aziendali
-   Configurare l'accesso ai dati aziendali distribuendo app specifiche dei ruoli ai tablet

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitazioni dei dispositivi registrati con un account del manager di registrazione dispositivi

I dispositivi registrati con un account di manager di registrazione dispositivi presentano le restrizioni seguenti:

  - Nessun accesso per singolo utente. Poiché ai dispositivi non è assegnato alcun utente, il dispositivo non ha accesso alla posta elettronica o ai dati aziendali. È comunque possibile usare configurazioni VPN, ad esempio, per fornire l'accesso ai dati alle app dei dispositivi.
  - Nessun accesso condizionale. Questi infatti sono scenari per utente.
  - L'utente manager di registrazione dispositivi non può annullare la registrazione di dispositivi registrati DEM sul dispositivo tramite il portale aziendale. Questa operazione può essere eseguita dall'amministratore di Intune, ma non dall'utente DEM.
  - Visualizzazione del solo dispositivo locale nell'app o nel sito Web del portale aziendale.
  - Gli utenti non possono usare le app Volume Purchase Program di Apple poiché è necessario un ID Apple per utente per la gestione delle app.
  - (Solo iOS) Se si usa un manager di registrazione dispositivi per la registrazione dei dispositivi iOS, non è possibile usare Apple Configurator, Apple Device Enrollment Program (DEP) o Apple School Manager (ASM) per la registrazione dei dispositivi.
  - Ogni dispositivo richiede una licenza dispositivo. Altre informazioni sulle [licenze utente e dispositivo](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> Per distribuire le app aziendali ai dispositivi gestiti con il manager di registrazione dispositivi, distribuire l'app Portale aziendale come **Installazione richiesta** all'account utente del manager di registrazione dispositivi.
> Per consentire prestazioni migliori, se si visualizza l'app Portale aziendale in un dispositivo DEM, viene visualizzato solo il dispositivo locale. La gestione remota di altri dispositivi DEM è possibile solo dalla console di amministrazione di Intune.


## <a name="add-a-device-enrollment-manager"></a>Aggiungere un manager di registrazione dispositivi

1.  Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2.  Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Manager di registrazione dispositivi**.

3.  Selezionare **Aggiungi**.

4.  Nel pannello **Aggiungi utente** immettere un nome entità utente per l'utente manager di registrazione dispositivi, quindi selezionare **Aggiungi**. L'utente manager di registrazione dispositivi viene aggiunto all'elenco di utenti manager di registrazione dispositivi.

## <a name="permissions-for-dem"></a>Autorizzazioni per il manager di registrazione dispositivi

Sono necessari i ruoli di Azure AD Amministratore globale o Amministratore del servizio Intune per l'esecuzione delle attività di registrazione DEM. Questi ruoli sono inoltre necessari per visualizzare tutti gli utenti DEM, nonostante il fatto che le autorizzazioni di controllo degli accessi in base al ruolo siano elencate e disponibili nel ruolo utente personalizzato. Un utente a cui non è assegnato il ruolo Amministratore globale o Amministratore del servizio Intune, ma che dispone di autorizzazioni di lettura per il ruolo Manager di registrazione dispositivi, potrà visualizzare solo gli utenti DEM che ha creato. Il supporto del ruolo Controllo degli accessi in base al ruolo per queste funzionalità verrà annunciato in futuro.

Se un utente non ha il ruolo Amministratore globale o Amministratore del servizio Intune, ma dispone di autorizzazioni di lettura abilitate per il ruolo Manager di registrazione dispositivi, potrà visualizzare solo gli utenti DEM che ha creato.

## <a name="remove-a-device-enrollment-manager"></a>Rimuovere un manager di registrazione dispositivi

La rimozione di un manager di registrazione dispositivi non influisce sui dispositivi registrati. Quando viene rimosso un manager di registrazione dispositivi:

-   I dispositivi registrati non sono interessati e continuano a essere completamente gestiti.
-   Le credenziali dell'account manager di registrazione dispositivi rimosso restano valide.
-   Il manager di registrazione dispositivi rimosso non può ancora cancellare o disattivare i dispositivi.
-   Il manager di registrazione dispositivi rimosso può registrare solo un numero di dispositivi fino al limite per utente configurato dall'amministratore di Intune.

**Per rimuovere un manager di registrazione dispositivi**

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Manager di registrazione dispositivi**.
3. Nel pannello **Manager di registrazione dispositivi** fare clic con il pulsante destro del mouse sull'utente manager di registrazione dispositivi e selezionare **Rimuovi**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Visualizzare le proprietà di un manager di registrazione dispositivi

1. Nel portale di Azure scegliere **Registrazione del dispositivo** e quindi scegliere **Manager di registrazione dispositivi**.
2. Nel pannello **Manager di registrazione dispositivi** fare clic con il pulsante destro del mouse sull'utente manager di registrazione dispositivi e selezionare **Proprietà**.
