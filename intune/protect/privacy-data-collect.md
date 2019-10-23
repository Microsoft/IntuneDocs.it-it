---
title: Raccolta di dati in Intune
titleSuffix: Microsoft Intune
description: Informazioni sulla raccolta dei dati personali in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e93e69b5cce2c54ae07410309b33870dd828f563
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509076"
---
# <a name="data-collection-in-intune"></a>Raccolta di dati in Intune

Quando gli utenti registrano i dispositivi aziendali o personali con Intune, Intune raccoglie e condivide alcuni dati personali. Intune raccoglie i dati personali dalle origini seguenti:

- Uso di Intune nel portale di Azure da parte dell'amministratore.
- Dispositivi degli utenti finali (quando vengono registrati per la gestione in Intune e durante l'utilizzo).
- Account dei clienti per servizi di terze parti (come da istruzioni dell'amministratore).
- Informazioni di diagnostica, sulle prestazioni e sull'utilizzo.

Da queste origini, Intune raccoglie le informazioni che rientrano nelle tre categorie seguenti: [dati identificati](#identified-data), [dati pseudonimizzati](#pseudonymized-data) e [dati aggregati](#aggregated-data).

> [!NOTE]
> Microsoft non vende per alcun motivo a terze parti i dati raccolti dal servizio.

## <a name="identified-data"></a>Dati identificati

I dati più personali raccolti da Intune sono i dati identificati. Questi dati sono associati a un utente, un dispositivo o un'applicazione e sono essenziali per le finalità della gestione. I dati identificati vengono usati per gestire i dispositivi e le applicazioni dell'utente e per il provisioning del servizio Intune.

I dati identificati raccolti da Intune possono includere, a titolo di esempio: 

- Informazioni sull'utente
  - Nome del proprietario/nome visualizzato dell'utente (il nome registrato in Azure dell'utente identificato con l'ID utente di Azure)
  - Nome dell'entità utente o indirizzo di posta elettronica
  - Identificatore dell'utente di terze parti (ad esempio ID Apple)
- Informazioni sull'inventario hardware
  - Nome dispositivo
  - Produttore
  - Sistema operativo
  - Numero di serie
  - Numero IMEI
  - Indirizzo IP
  - MacAddress Wi-Fi
  - ICCID
  - Numero di telefono
- Informazioni del log di controllo, compresi i dati sulle attività seguenti
  - Gestire
  - Creazione
  - Aggiornamento (modifica)
  - Eliminazione
  - Assegna
  - Attività remote
- Informazioni di supporto
  - Informazioni di contatto (nome, numero di telefono, indirizzo di posta elettronica)
  - Comunicazioni tramite posta elettronica con membri dei team Microsoft di supporto, del prodotto e/o dell'esperienza clienti
- Informazioni di controllo di accesso (Intune usa questi dati per gestire l'accesso ai ruoli e alle funzioni amministrativi tramite funzionalità come il [controllo degli accessi in base al ruolo](../fundamentals/role-based-access-control.md)).
  - Autenticatori statici (password del cliente)
  - Chiavi di privacy per i certificati 
- Informazioni su amministratore e account
  - Nome e cognome dell'amministratore
  - Nome utente dell'amministratore
  - UPN (posta elettronica)
  - Numero di telefono
  - Indirizzo di posta elettronica del proprietario dell'account
  - ID di Active Directory di ogni amministratore IT del cliente
  - Dati di pagamento per la fatturazione del cliente
  - Chiave di sottoscrizione
- Inventario delle applicazioni, ad esempio
  - nome dell'app
  - Versione
  - ID dell'app
  - dimensioni
  - percorso di installazione
  - I dati di inventario dell'applicazione vengono raccolti solo quando contrassegnati dall'amministratore come dispositivo aziendale o quando è attivata la funzionalità per le app conformi.  
- ID tenant di terze parti del cliente, ad esempio l'ID Apple. 

## <a name="pseudonymized-data"></a>Dati pseudonimizzati

I dati pseudonimizzati sono associati a un identificatore univoco, in genere un numero generato dal sistema che da solo non consente di identificare un individuo, ma viene usato per fornire i servizi aziendali agli utenti. 

I dati pseudonimizzati raccolti da Intune possono includere, a titolo di esempio: 

- Dati di diagnostica, sulle prestazioni e sull'utilizzo associati a un utente e/o a un dispositivo
  - Il numero di volte in cui viene usata una funzionalità
  - I comandi forniti alla funzionalità
  - Il tempo di risposta di un servizio
  - Percentuali di successo delle installazioni e di altri processi
  - Errori dell'applicazione Portale aziendale di Intune
  - Identificatori di utenti e dispositivi
  - Identificatori per scopi di riferimento, correlazione e gestione 
- I dati dei dispositivi non associati a un dispositivo o utente (se questi dati sono associati a un dispositivo o un utente, Intune li considera dati identificati)
  - ID dispositivo Intune
  - ID dispositivo di Azure Active Directory
  - ID di gestione dei dispositivi in Intune
  - ID tenant
  - ID account
  - ID dispositivo EAS
  - ID specifici della piattaforma
  - ID Apple per dispositivi iOS
  - Indirizzo Mac per dispositivi Mac
  - ID Windows per dispositivi Windows
- Informazioni sulle applicazioni gestite
  - ID delle applicazioni gestite
  - Tag del dispositivo delle applicazioni gestite
  - ID di gestione dei dispositivi in Intune
  - ID dispositivo di Azure Active Directory
  - Chiavi di crittografia

## <a name="aggregated-data"></a>Dati aggregati

I dati aggregati vengono usati per eseguire il provisioning e migliorare il servizio Intune. 

I dati aggregati raccolti da Intune possono includere, a titolo di esempio: 

- Dati di utilizzo amministrativi da tutti i tenant di Intune (ad esempio, controlli amministrativi selezionati durante le interazioni con la console di amministrazione)
- Informazioni sull'account tenant (questi dati sono disponibili nel pannello di Intune)
  - Numero di dispositivi o utenti registrati
  - Numero di piattaforme per dispositivi identificate  
  - Numero di dispositivi installati
  - installedDeviceCount: numero di dispositivi in cui è installata l'applicazione.
  - notApplicableDeviceCount: numero di dispositivi per cui è l'applicazione non è applicabile.
  - notInstalledDeviceCount: numero di dispositivi per cui l'applicazione è applicabile, ma non è installata.
  - pendingInstallDeviceCount: numero di dispositivi per cui l'applicazione è applicabile e l'installazione è in sospeso.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni su come Intune [archivia ed elabora](privacy-data-store-process.md) e [condivide](privacy-data-secure-share.md) i dati personali. 
