---
title: Portale del Supporto tecnico per la risoluzione dei problemi | Microsoft Docs
titlesuffix: Azure portal
description: Il personale del supporto tecnico usa il portale per risolvere i problemi tecnici degli utenti
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 09/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 845b225fe60ecde71f364b224a0984638662a3db
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il portale di risoluzione dei problemi consente agli operatori del supporto tecnico e agli amministratori di Intune di visualizzare le informazioni degli utenti per rispondere alle richieste di assistenza degli utenti. Le organizzazioni che dispongono di help desk possono assegnare il ruolo di **operatore di help desk** a un gruppo di utenti. I membri del ruolo operatore di help desk possono usare il pannello **Risoluzione dei problemi**.

Il pannello **Risoluzione dei problemi** visualizza anche i problemi di registrazione dell'utente. Informazioni dettagliate sul problema e i passaggi suggeriti per la correzione possono essere utili ad amministratori e operatori di help desk per la risoluzione dei problemi. Alcuni problemi di registrazione non vengono rilevati ed è possibile che per alcuni errori non siano disponibili suggerimenti per la correzione. 

Per istruzioni sull'aggiunta di un ruolo operatore di help desk, vedere [Controllo degli accessi in base al ruolo (RBAC) con Intune](/intune/role-based-access-control).

Quando un utente contatta l'help desk per un problema tecnico di Intune, l'operatore di help desk immette il nome dell'utente. Intune visualizza dati utili che consentono di risolvere molti problemi di livello 1, tra cui:

- Stato utente
- Assignments
- Problemi di conformità
- Un dispositivo che non risponde
- Un dispositivo che non riceve le impostazioni VPN o Wi-Fi
- Un errore di installazione dell'app

## <a name="to-review-troubleshooting-details"></a>Per esaminare le informazioni sulla risoluzione dei problemi

Nel pannello Risoluzione dei problemi scegliere **Selezionare l'utente** per visualizzare le informazioni relative all'utente. Le informazioni utente sono utili per definire lo stato corrente degli utenti e dei loro dispositivi.  

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Risoluzione dei problemi**.
4. Fare clic su **Selezionare l'utente**.
5. Selezionare un utente digitando il nome o l'indirizzo di posta elettronica. Fare clic su **Seleziona**. Le informazioni di risoluzione dei problemi per l'utente vengono visualizzate nel pannello Risoluzione dei problemi. Le tabelle seguenti descrivono tali informazioni.

> [!Note]  
> È anche possibile accedere al pannello **Risoluzione dei problemi** digitando il seguente indirizzo nel browser: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Aree del dashboard Risoluzione dei problemi

È possibile usare il pannello **Risoluzione dei problemi** per esaminare le informazioni dell'utente. 

![](/intune/media/troubleshooting-dash.png)

| Area | Name | Descrizione |
| ---  | ---  | ---         |
| 1.   | Stato dell'account  | Mostra lo stato del tenant di Intune corrente come **Attivo** o **Inattivo**.       |
| 2.   | Selezione utente  | Nome dell'utente attualmente selezionato. Fare clic su **Cambia utente** per scegliere un nuovo utente.       |
| 3.   | Stato utente  | Visualizza lo stato della licenza Intune dell'utente, il numero di dispositivi, la conformità di ciascun dispositivo, il numero di app e la conformità delle app.       |
| 4.   | Informazioni utente  | Usare l'elenco per selezionare i dettagli da esaminare nel pannello. <br>È possibile selezionare: <ul><li>App per dispositivi mobili<li>Criteri di protezione delle app<li>Criteri di conformità<li> Criteri di configurazione</ul>      |
| 5.   | Appartenenza al gruppo  | Yadda       |

## <a name="mobile-apps-reference"></a>Riferimento per le app per dispositivi mobili

App in esecuzione nei dispositivi (o dispositivi di proprietà degli utenti) gestiti da Intune e Azure Active Directory (AD).

### <a name="properties"></a>Proprietà

Proprietà delle app per dispositivi mobili.

| Proprietà      | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | Nome dell'applicazione.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Sistema operativo            | Sistema operativo installato nel dispositivo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Tipo          | È possibile scegliere un tipo di assegnazione per ciascuna applicazione.  <br> **Disponibile**: gli utenti installano l'app dall'app Portale aziendale o dal relativo sito Web.  <br> **Non applicabile**: l'app non è installata o visualizzata nel portale aziendale. <br> **Disinstalla**: l'applicazione è disinstallata sui dispositivi nei gruppi selezionati.  <br> **Available with or without enrollment** (Disponibile con o senza registrazione): assegnare questa app a gruppi di utenti i cui dispositivi non sono registrati con Intune. |
| Ultima modifica | Nome del tipo di dispositivo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### <a name="devices"></a>Dispositivi

Dispositivi gestiti da Intune o da utenti gestiti da Intune o Azure AD.

| Proprietà           | Descrizione                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome dispositivo        | Nome del tipo di dispositivo.                                                                                                     |
| Gestito da         | Timestamp della modifica del criterio.                                                                                              |
| Tipo di aggiunta ad Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Proprietà          | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**.                                               |
| Conforme con Intune   | Nome del tipo di dispositivo.                                                                                                     |
| Conforme con Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Sistema operativo                 | Sistema operativo installato nel dispositivo.                                                                                       |
| Versione sistema operativo         | Numero di versione del sistema operativo del dispositivo.                                                                                  |
| Ultima archiviazione      | Nome del tipo di dispositivo.                                                                                                     |

### <a name="app-protection-status"></a>Stato protezione app

I criteri di protezione app sono disponibili per le app per dispositivi mobili che si integrano con le tecnologie Enterprise Mobility + Security (EMS). Ciò garantisce un grado base di protezione per i dati aziendali che vengono scaricati nelle app per dispositivi mobili, tra cui le app Office. 

| Proprietà    | Descrizione                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Stato      | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**. |
| Nome app    | Nome dell'applicazione.                                                           |
| Nome dispositivo | Nome del tipo di dispositivo.                                                       |
| Tipo di dispositivo | Nome del tipo di dispositivo.                                                       |
| Criteri    | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**. |
| Ultima sincronizzazione   | Timestamp dell'ultima sincronizzazione del dispositivo con Intune.                   |

## <a name="app-protection-policies-reference"></a>Riferimento dei criteri di protezione app

I criteri di protezione app sono disponibili per le app per dispositivi mobili che si integrano con le tecnologie Enterprise Mobility + Security (EMS). Ciò garantisce un grado base di protezione per i dati aziendali che vengono scaricati nelle app per dispositivi mobili, tra cui le app Office. 

### <a name="properties"></a>Proprietà

La tabella riepiloga lo stato dei criteri di protezione app per i dispositivi gestiti da Intune.

| Proprietà    | Descrizione                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | Nome dell'applicazione.                                                                                                        |
| Distribuito    | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Piattaforma    | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**.                                               |
| Registrazione  | Nome del tipo di dispositivo.                                                                                                     |
| Ultimo aggiornamento | Timestamp della modifica del criterio.                                                                                              |

### <a name="devices"></a>Dispositivi

Dispositivi gestiti da Intune o da utenti gestiti da Intune o Azure AD.

| Proprietà           | Testo                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome periferica        | Nome del tipo di dispositivo.                                                                                                     |
| Gestito da         | Timestamp della modifica del criterio.                                                                                              |
| Tipo di aggiunta ad Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Proprietà          | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**.                                               |
| Conforme con Intune   | Nome del tipo di dispositivo.                                                                                                     |
| Conforme con Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Conforme con Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Sistema operativo                 | Sistema operativo installato nel dispositivo.                                                                                       |
| Versione sistema operativo         | Numero di versione del sistema operativo del dispositivo.                                                                                  |
| Ultima archiviazione      | Nome del tipo di dispositivo.                                                                                                     |

## <a name="compliance-policies-reference"></a>Riferimento dei criteri di conformità

Questi criteri garantiscono che i dispositivi usati per accedere alle app e ai dati aziendali rispettino alcune regole, come l'uso di un PIN per l'accesso al dispositivo e la crittografia dei dati archiviati nel dispositivo stesso.

### <a name="properties"></a>Proprietà

Proprietà dei criteri di conformità.

| Proprietà      | Descrizione                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assegnazione    | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Name          | Nome dell'applicazione.                                                                                                        |
| Sistema operativo            | Sistema operativo installato nel dispositivo.                                                                                       |
| Tipo di criteri   | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**.                                               |
| Ultima modifica | Nome del tipo di dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivi

Dispositivi gestiti da Intune o da utenti gestiti da Intune o Azure AD.

| Proprietà           | Descrizione                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome dispositivo        | Nome del tipo di dispositivo.                                                                                                     |
| Gestito da         | Timestamp della modifica del criterio.                                                                                              |
| Tipo di aggiunta ad Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Proprietà          | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**.                                               |
| Conforme con Intune   | Nome del tipo di dispositivo.                                                                                                     |
| Conforme con Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Sistema operativo                 | Sistema operativo installato nel dispositivo.                                                                                       |
| Versione sistema operativo         | Numero di versione del sistema operativo del dispositivo.                                                                                  |
| Ultima archiviazione      | Nome del tipo di dispositivo.                                                                                                     |

### <a name="app-protection-policies"></a>Criteri di protezione delle app

I criteri di protezione app sono disponibili per le app per dispositivi mobili che si integrano con le tecnologie Enterprise Mobility + Security (EMS). Ciò garantisce un grado base di protezione per i dati aziendali che vengono scaricati nelle app per dispositivi mobili, tra cui le app Office. 

| Proprietà    | Descrizione                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Stato      | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**. |
| Nome app    | Nome dell'applicazione.                                                           |
| Nome dispositivo | Nome del tipo di dispositivo.                                                       |
| Tipo di dispositivo | Nome del tipo di dispositivo.                                                       |
| Criteri    | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**. |
| Ultima sincronizzazione   | Timestamp dell'ultima sincronizzazione del dispositivo con Intune.                   |

## <a name="configuration-policies-reference"></a>Riferimento dei criteri di configurazione

I criteri di configurazione sono disponibili per app per dispositivi mobili con configurazioni specifiche del fornitore. 

### <a name="properties"></a>Proprietà

Proprietà dei criteri di configurazione.

| Proprietà      | Descrizione                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assegnazione    | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Name          | Nome dell'applicazione.                                                                                                        |
| Sistema operativo            | Sistema operativo installato nel dispositivo.                                                                                       |
| Tipo di criteri   | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**.                                               |
| Ultima modifica | Nome del tipo di dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivi

Dispositivi gestiti da Intune o da utenti gestiti da Intune o Azure AD.

| Proprietà           | Descrizione                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome dispositivo        | Nome del tipo di dispositivo.                                                                                                     |
| Gestito da         | Timestamp della modifica del criterio.                                                                                              |
| Tipo di aggiunta ad Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Proprietà          | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**.                                               |
| Conforme con Intune   | Nome del tipo di dispositivo.                                                                                                     |
| Conforme con Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Sistema operativo                 | Sistema operativo installato nel dispositivo.                                                                                       |
| Versione sistema operativo         | Numero di versione del sistema operativo del dispositivo.                                                                                  |
| Ultima archiviazione      | Nome del tipo di dispositivo.                                                                                                     |


### <a name="app-protection-policies"></a>Criteri di protezione delle app

I criteri di protezione app sono disponibili per le app per dispositivi mobili che si integrano con le tecnologie Enterprise Mobility + Security (EMS). Ciò garantisce un grado base di protezione per i dati aziendali che vengono scaricati nelle app per dispositivi mobili, tra cui le app Office. 

| Proprietà    | Descrizione                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Stato      | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**. |
| Nome app    | Nome dell'applicazione.                                                           |
| Nome dispositivo | Nome del tipo di dispositivo.                                                       |
| Tipo di dispositivo | Nome del tipo di dispositivo.                                                       |
| Criteri    | Tipo di proprietà del dispositivo. Può essere **Società**, **Personale** o **Sconosciuto**. |
| Ultima sincronizzazione   | Timestamp dell'ultima sincronizzazione del dispositivo con Intune.                   |

## <a name="next-steps"></a>Passaggi successivi

È possibile ottenere altre informazioni sull'uso del controllo degli accessi in base al ruolo (RBAC) per definire i ruoli nel dispositivo aziendale, gestire app per dispositivi mobili e implementare attività di protezione dati. Per altre informazioni, vedere [Controllo degli accessi in base al ruolo (RBAC) con Intune](/intune/role-based-access-control).

È possibile ottenere informazioni sui problemi noti in Microsoft Intune. Per altre informazioni, vedere [Problemi noti in Microsoft Intune](/intune/known-issues).

È possibile apprendere come creare un ticket di supporto e ottenere supporto quando è necessario. [Ottenere supporto](/intune/get-support).