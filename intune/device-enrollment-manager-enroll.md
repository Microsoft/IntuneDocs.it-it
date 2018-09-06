---
title: Registrare i dispositivi usando un account del manager di registrazione dispositivi
titlesuffix: Microsoft Intune
description: Usare l'account del manager di registrazione dispositivi per registrare i dispositivi in Intune. "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce785ad7898f9e792feeadcd1623bd0989f0d6d0
ms.sourcegitcommit: 40b1d82df99f09a75a17065cdd0e84d8038f460a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "40255536"
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>Registrare i dispositivi usando un account del manager di registrazione dispositivi

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un singolo account utente. L'account del *manager di registrazione dispositivi* (DEM, Device Enrollment Manager) è un account utente speciale che consente di registrare fino a 1.000 dispositivi. Gli utenti esistenti vengono aggiunti all'account del manager di registrazione dispositivi per rendere disponibili le opzioni DEM. Ogni dispositivo registrato usa una singola licenza. Si consiglia di usare i dispositivi registrati tramite tale account come dispositivi condivisi piuttosto che come dispositivi personali ("BYOD").  

Per poter essere aggiunti come manager di registrazione dispositivi, gli utenti devono essere presenti nel [portale di Azure](https://portal.azure.com). Per una sicurezza ottimale, l'utente manager di registrazione dispositivi non deve essere anche amministratore di Intune.

>[!NOTE]
>Il metodo di registrazione DEM non può essere usato con questi altri metodi di registrazione: [Apple Configurator tramite l'Assistente configurazione](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator con registrazione diretta](apple-configurator-direct-enroll-ios.md), [Apple School Manager (ASM)](apple-school-manager-set-up-ios.md) o [Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Esempio di scenario con manager di registrazione dispositivi

Un ristorante vuole offrire 50 tablet POS al personale di sala e monitor per gli ordini per il personale di cucina. I dipendenti non hanno bisogno di accedere ai dati aziendali o di accedere come utenti. L'amministratore di Intune crea un nuovo account del manager di registrazione dispositivi per il supervisore del ristorante.  Questo account è separato dall'account principale del supervisore e viene usato solo per la registrazione dei dispositivi condivisi con Intune. Il supervisore potrà quindi registrare 50 tablet usando le credenziali DEM.

Solo gli utenti presenti nel [portale di Azure](https://portal.azure.com) possono essere manager di registrazione dispositivi. L'utente manager di registrazione dispositivi non può essere un amministratore di Intune.

L'utente manager di registrazione dispositivi può:

-   Registrare un massimo di 1000 dispositivi in Intune
-   Accedere al portale aziendale per ottenere le app aziendali
-   Configurare l'accesso ai dati aziendali distribuendo app specifiche dei ruoli ai tablet

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitazioni dei dispositivi registrati con un account del manager di registrazione dispositivi

I dispositivi registrati con un account di manager di registrazione dispositivi presentano le restrizioni seguenti:

  - Nessun accesso per singolo utente. Poiché ai dispositivi non è assegnato alcun utente, il dispositivo non ha accesso alla posta elettronica o ai dati aziendali. È comunque possibile usare configurazioni VPN, ad esempio, per fornire l'accesso ai dati alle app dei dispositivi.
  - L'utente manager di registrazione dispositivi non può annullare la registrazione di dispositivi registrati DEM sul dispositivo tramite il portale aziendale. L'amministratore di Intune può annullare la registrazione.
  - Visualizzazione del solo dispositivo locale nell'app o nel sito Web del portale aziendale.
  - Gli utenti non possono usare le app Volume Purchase Program (VPP) di Apple con licenze utente poiché è necessario un ID Apple per utente per la gestione delle app.
  - (Solo iOS) Se si usa un manager di registrazione dispositivi per la registrazione dei dispositivi iOS, non è possibile usare Apple Configurator, Apple Device Enrollment Program (DEP) o Apple School Manager (ASM) per la registrazione dei dispositivi.
  - (Solo Android) È previsto un limite al numero di dispositivi del profilo di lavoro Android che possono essere registrati con un singolo account DEM. Per ogni account DEM è possibile registrare fino a 10 profili di lavoro Android. Questa limitazione non si applica alla registrazione di Android legacy.
  - I dispositivi possono installare le app VPP se sono dotati delle licenze dispositivo.
  - Per usare DEM non è necessaria una licenza dispositivo di Intune. Altre informazioni sulle [licenze utente e dispositivo](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> È possibile distribuire app aziendali ai dispositivi gestiti dal manager di registrazione dispositivi. Distribuire l'app Portale aziendale come **installazione richiesta** all'account utente del manager di registrazione dispositivi.
> Per consentire prestazioni migliori, se si visualizza l'app Portale aziendale in un dispositivo DEM, viene visualizzato solo il dispositivo locale. La gestione remota di altri dispositivi DEM è possibile solo dalla console di amministrazione di Intune.


## <a name="add-a-device-enrollment-manager"></a>Aggiungere un manager di registrazione dispositivi

1.  Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Manager di registrazione dispositivi**.

2.  Selezionare **Aggiungi**.

3.  Nel pannello **Aggiungi utente** immettere un nome entità utente per l'utente manager di registrazione dispositivi, quindi selezionare **Aggiungi**. L'utente manager di registrazione dispositivi viene aggiunto all'elenco di utenti manager di registrazione dispositivi.

## <a name="permissions-for-dem"></a>Autorizzazioni per il manager di registrazione dispositivi

I ruoli di Azure AD Amministratore globale o Amministratore del servizio Intune sono necessari per
- completare le attività correlate alla registrazione DEM nel portale di amministrazione
- visualizzare tutti gli utenti DEM, nonostante il fatto che le autorizzazioni di controllo degli accessi in base al ruolo siano elencate e disponibili nel ruolo utente personalizzato.

Un utente a cui non è assegnato il ruolo Amministratore globale o Amministratore del servizio Intune, ma che ha le autorizzazioni di lettura per il ruolo Manager di registrazione dispositivi, può visualizzare solo gli utenti DEM che ha creato. Il supporto del ruolo Controllo degli accessi in base al ruolo per queste funzionalità verrà annunciato in futuro.


## <a name="remove-a-device-enrollment-manager"></a>Rimuovere un manager di registrazione dispositivi

Quando viene rimosso un manager di registrazione dispositivi:

-   I dispositivi registrati non sono interessati e continuano a essere completamente gestiti.
-   Le credenziali dell'account del manager di registrazione dispositivi rimosse sono ancora valide.
-   Il manager di registrazione dispositivi rimosso non può ancora cancellare o ritirare i dispositivi.
-   Il manager di registrazione dispositivi rimosso può registrare solo un numero di dispositivi fino al limite per utente configurato dall'amministratore di Intune.

**Per rimuovere un manager di registrazione dispositivi**

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** e quindi scegliere **Manager di registrazione dispositivi**.
2. Nel pannello **Manager di registrazione dispositivi** selezionare l'utente manager di registrazione dispositivi e selezionare **Elimina**.

