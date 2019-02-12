---
title: Portale del supporto tecnico per la risoluzione dei problemi
titlesuffix: Microsoft Intune
description: Il personale del supporto tecnico usa questo portale per risolvere i problemi tecnici degli utenti.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 874d191d79c22dd7b044df2e5a8e813324e35e11
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55844174"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti aziendali

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Il portale di risoluzione dei problemi consente agli operatori del supporto tecnico e agli amministratori di Intune di visualizzare le informazioni degli utenti per rispondere alle richieste di assistenza degli utenti. Le organizzazioni che dispongono di help desk possono assegnare il ruolo di **operatore di help desk** a un gruppo di utenti. I membri del ruolo operatore di help desk possono usare il riquadro **Risoluzione dei problemi**.

Il riquadro **Risoluzione dei problemi** visualizza anche i problemi di registrazione dell'utente. Informazioni dettagliate sul problema e i passaggi suggeriti per la correzione possono essere utili ad amministratori e operatori di help desk per la risoluzione dei problemi. Alcuni problemi di registrazione non vengono rilevati ed è possibile che per alcuni errori non siano disponibili suggerimenti per la correzione.

Per istruzioni sull'aggiunta di un ruolo operatore di help desk, vedere [Controllo degli accessi in base al ruolo (RBAC) con Intune](/intune/role-based-access-control).

Quando un utente contatta l'help desk per un problema tecnico di Intune, l'operatore di help desk immette il nome dell'utente. Intune visualizza dati utili che consentono di risolvere molti problemi di livello 1, tra cui:

- Stato utente
- Assignments
- Problemi di conformità
- Un dispositivo che non risponde
- Un dispositivo che non riceve le impostazioni VPN o Wi-Fi
- Un errore di installazione dell'app

## <a name="to-review-troubleshooting-details"></a>Per esaminare le informazioni sulla risoluzione dei problemi

Nel riquadro Risoluzione dei problemi scegliere **Selezionare l'utente** per visualizzare le informazioni relative all'utente. Le informazioni utente sono utili per definire lo stato corrente degli utenti e dei loro dispositivi.  

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Risoluzione dei problemi**.
4. Fare clic su **Seleziona** per selezionare un utente per risolvere i problemi.
5. Selezionare un utente digitando il nome o l'indirizzo di posta elettronica. Fare clic su **Seleziona**. Le informazioni di risoluzione dei problemi per l'utente vengono visualizzate nel riquadro Risoluzione dei problemi. La tabella seguente descrive tali informazioni.

> [!Note]  
> È anche possibile accedere al riquadro **Risoluzione dei problemi** digitando nel browser l'indirizzo seguente: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Aree del dashboard Risoluzione dei problemi

È possibile usare il riquadro **Risoluzione dei problemi** per esaminare le informazioni dell'utente.

![](/intune/media/troubleshooting-dash.png)

| Area | Name | Descrizione |
| ---  | ---  | ---         |
| 1.   | Stato dell'account  | Mostra lo stato del tenant di Intune corrente come **Attivo** o **Inattivo**.       |
| 2.   | Selezione utente  | Nome dell'utente attualmente selezionato. Fare clic su **Cambia utente** per scegliere un nuovo utente.       |
| 3.   | Stato utente  | Visualizza lo stato della licenza Intune dell'utente, il numero di dispositivi, la conformità di ciascun dispositivo, il numero di app e la conformità delle app.       |
| 4.   | Informazioni utente  | Usare l'elenco per selezionare i dettagli da esaminare nel riquadro. <br>È possibile selezionare: <ul><li>App client<li>Criteri di conformità<li> Criteri di configurazione<li>Criteri di protezione delle app <li>Restrizioni di registrazione</ul>      |
| 5.   | Appartenenza al gruppo  | Mostra i gruppi correnti di cui l'utente selezionato è membro.       |

## <a name="client-apps-reference"></a>Riferimento per le app client

Le app che eseguono dispositivi
- gestiti da Intune e Azure Active Directory (AD) 
- di proprietà di utenti gestiti da Intune e Azure Active Directory (AD).

### <a name="properties"></a>Proprietà

Proprietà delle app client.

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
| Proprietà          | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**).                                               |
| Conforme con Intune   | Nome del tipo di dispositivo.                                                                                                     |
| Conforme con Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Installazione dell'app | Indica se nel singolo dispositivo l'installazione dell'app è stata eseguita correttamente o non è riuscita. |
| Sistema operativo                 | Sistema operativo installato nel dispositivo.                                                                                       |
| Versione sistema operativo         | Numero di versione del sistema operativo del dispositivo.                                                                                  |
| Ultima archiviazione      | Nome del tipo di dispositivo.                                                                                                     |

### <a name="app-protection-status"></a>Stato protezione app

I criteri di protezione app sono disponibili per le app per dispositivi mobili che si integrano con le tecnologie Enterprise Mobility + Security (EMS). Questi criteri garantiscono un grado base di protezione per i dati aziendali che vengono scaricati nelle app per dispositivi mobili, tra cui le app Office. 

| Proprietà    | Descrizione                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Stato      | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**). |
| Nome app    | Nome dell'applicazione.                                                           |
| Nome dispositivo | Nome del tipo di dispositivo.                                                       |
| Tipo di dispositivo | Nome del tipo di dispositivo.                                                       |
| Criteri    | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**). |
| Ultima sincronizzazione   | Timestamp dell'ultima sincronizzazione del dispositivo con Intune.                   |

## <a name="app-protection-policies-reference"></a>Riferimento dei criteri di protezione app

Sono disponibili criteri di protezione delle app per dispositivi mobili che si integrano con le tecnologie EMS. Questi criteri garantiscono un grado base di protezione per i dati aziendali che vengono scaricati nelle app per dispositivi mobili, tra cui le app Office. 

### <a name="properties"></a>Proprietà

La tabella riepiloga lo stato dei criteri di protezione app per i dispositivi gestiti da Intune.

| Proprietà    | Descrizione                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | Nome dell'applicazione.                                                                                                        |
| Distribuito    | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Piattaforma    | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**).                                               |
| Registrazione  | Nome del tipo di dispositivo.                                                                                                     |
| Ultimo aggiornamento | Timestamp della modifica del criterio.                                                                                              |

### <a name="devices"></a>Dispositivi

Dispositivi gestiti da Intune o da utenti gestiti da Intune o Azure AD.

| Proprietà           | Testo                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome periferica        | Nome del tipo di dispositivo.                                                                                                     |
| Gestito da         | Timestamp della modifica del criterio.                                                                                              |
| Tipo di aggiunta ad Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Proprietà          | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**).                                               |
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
| Tipo di criteri   | Il tipo di proprietà del dispositivo (**Società**, **Personale** e **Sconosciuto**).                                               |
| Ultima modifica | Nome del tipo di dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivi

Dispositivi gestiti da Intune o da utenti gestiti da Intune o Azure AD.

| Proprietà           | Descrizione                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome dispositivo        | Nome del tipo di dispositivo.                                                                                                     |
| Gestito da         | Timestamp della modifica del criterio.                                                                                              |
| Tipo di aggiunta ad Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Proprietà          | Il tipo di proprietà del dispositivo (**Società**, **Personale** e **Sconosciuto**).                                               |
| Conforme con Intune   | Nome del tipo di dispositivo.                                                                                                     |
| Conforme con Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Sistema operativo                 | Sistema operativo installato nel dispositivo.                                                                                       |
| Versione sistema operativo         | Numero di versione del sistema operativo del dispositivo.                                                                                  |
| Ultima archiviazione      | Nome del tipo di dispositivo.                                                                                                     |

### <a name="app-protection-policies"></a>Criteri di protezione delle app

I criteri di protezione app sono disponibili per le app per dispositivi mobili che si integrano con le tecnologie Enterprise Mobility + Security (EMS). Questi criteri garantiscono un grado base di protezione per i dati aziendali che vengono scaricati nelle app per dispositivi mobili, tra cui le app Office. 

| Proprietà    | Descrizione                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Stato      | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**). |
| Nome app    | Nome dell'applicazione.                                                           |
| Nome dispositivo | Nome del tipo di dispositivo.                                                       |
| Tipo di dispositivo | Nome del tipo di dispositivo.                                                       |
| Criteri    | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**). |
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
| Tipo di criteri   | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**).                                               |
| Ultima modifica | Nome del tipo di dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivi

Dispositivi gestiti da Intune o da utenti gestiti da Intune o Azure AD.

| Proprietà           | Descrizione                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome dispositivo        | Nome del tipo di dispositivo.                                                                                                     |
| Gestito da         | Timestamp della modifica del criterio.                                                                                              |
| Tipo di aggiunta ad Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Proprietà          | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**).                                               |
| Conforme con Intune   | Nome del tipo di dispositivo.                                                                                                     |
| Conforme con Azure AD | Stato di ogni app di protezione delle app degli utenti I possibili stati per le app sono **Archiviato** e **Non archiviato**. |
| Sistema operativo                 | Sistema operativo installato nel dispositivo.                                                                                       |
| Versione sistema operativo         | Numero di versione del sistema operativo del dispositivo.                                                                                  |
| Ultima archiviazione      | Nome del tipo di dispositivo.                                                                                                     |


### <a name="app-protection-policies"></a>Criteri di protezione delle app

I criteri di protezione app sono disponibili per le app per dispositivi mobili che si integrano con le tecnologie Enterprise Mobility + Security (EMS). Questi criteri garantiscono un grado base di protezione per i dati aziendali che vengono scaricati nelle app per dispositivi mobili, tra cui le app Office. 

| Proprietà    | Descrizione                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Stato      | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**). |
| Nome app    | Nome dell'applicazione.                                                           |
| Nome dispositivo | Nome del tipo di dispositivo.                                                       |
| Tipo di dispositivo | Nome del tipo di dispositivo.                                                       |
| Criteri    | Il tipo di proprietà del dispositivo (**Società**, **Personale** o **Sconosciuto**). |
| Ultima sincronizzazione   | Timestamp dell'ultima sincronizzazione del dispositivo con Intune.                   |

## <a name="enrollment-failure-reference"></a>Riferimento per gli errori di registrazione

Nella tabella Errori di registrazione sono elencati i tentativi di registrazione non riusciti. Un dispositivo riportato nella tabella seguente potrebbe essere stato registrato successivamente durante un altro tentativo. Alcuni tentativi non riusciti potrebbero non essere presenti. Le informazioni di mitigazione non sono disponibili per tutti gli errori.

| Colonna della tabella | Descrizione |
|-------------|----------|
| Avvio della registrazione | L'ora in cui l'utente ha iniziato la registrazione. |
| Sistema operativo | Sistema operativo del dispositivo. |
| Versione sistema operativo | Versione del sistema operativo del dispositivo. |
| Errore | Motivo dell'errore. |

### <a name="failure-details"></a>Dettagli errore

Quando si sceglie la riga di un errore, vengono forniti ulteriori dettagli.

| Sezione | Descrizione |
|-------------|----------|
| Dettagli errore | Una spiegazione più dettagliata dell'errore. |
| Possibili soluzioni | Passaggi consigliati per risolvere l'errore. Alcuni errori potrebbero non avere soluzione. |
| Risorse (facoltative) | Collegamenti per altre informazioni o aree del portale in cui intervenire. |

### <a name="enrollment-errors"></a>Errori di registrazione

| Errore | Dettagli |
|-------------|----------|
| iOS Timeout or Failure (Timeout o errore iOS) | Si è verificato un timeout tra il dispositivo e Intune perché l'utente ha impiegato troppo tempo a completare la registrazione. |
| L'utente non è stato trovato o non ha la licenza | L'utente non ha una licenza o è stato rimosso dal servizio. |
| Il dispositivo è già registrato | Qualcuno ha tentato di registrare un dispositivo usando il Portale aziendale su un dispositivo che risulta ancora registrato da un altro utente. |
| Nessun onboarding in Intune | È stata tentata una registrazione ma l'autorità di gestione dei dispositivi mobili (MDM) di Intune non era configurata. |
| Enrollment authorization failed (Autorizzazione di registrazione non riuscita) | È stata tentata una registrazione utilizzando una versione precedente del portale aziendale. |
| Dispositivo non supportato | Il dispositivo non soddisfa i requisiti minimi per la registrazione in Intune. |
| Le restrizioni della registrazione non sono state rispettate | Questa registrazione è stata bloccata a causa di una restrizione di registrazione configurata dall'amministratore. |
| Versione del dispositivo troppo bassa | L'amministratore ha configurato una restrizione a livello di registrazione che richiede una versione successiva del dispositivo. |
| Versione del dispositivo troppo alta | L'amministratore ha configurato una restrizione a livello di registrazione che richiede una versione precedente del dispositivo. |
| Il dispositivo non può essere registrato come dispositivo personale | L'amministratore ha configurato una restrizione a livello di registrazione che blocca le iscrizioni personali e il dispositivo in errore non è configurato come dispositivo aziendale. |
| Piattaforma del dispositivo bloccata | L'amministratore ha configurato una restrizione a livello di registrazione che blocca la piattaforma del dispositivo. |
| Token di massa scaduto | Il token di massa nel pacchetto di provisioning è scaduto. |
| Non sono stati trovati dettagli o dispositivo di AutoPilot | Quando si tenta di eseguire la registrazione, il dispositivo di Autopilot non viene rilevato. |
| Profilo di Autopilot non trovato o non assegnato | Il dispositivo non ha un profilo di Autopilot attivo. |
| Metodo di registrazione di Autopilot imprevisto | Il dispositivo ha cercato di registrarsi con un metodo non consentito. |
| Dispositivo di AutoPilot rimosso | Il dispositivo che ha eseguito un tentativo di registrazione è stato rimosso da Autopilot per questo account. |
| Numero massimo dispositivi raggiunto | Questa registrazione è stata bloccata a causa di una restrizione del limite di dispositivi configurata dall'amministratore. |
| Onboarding di Apple | La registrazione di tutti i dispositivi iOS è stata bloccata a causa di un certificato push MDM Apple mancante o scaduto in Intune. |
| Il dispositivo non è preregistrato | Il dispositivo non è stato preregistrato come aziendale e tutte le registrazioni personali sono state bloccate da un amministratore. |
| La funzionalità non è supportata | L'utente ha probabilmente tentato di eseguire la registrazione con un metodo non compatibile con la configurazione di Intune. |

## <a name="collect-available-data-from-mobile-device"></a>Raccogliere i dati disponibili dal dispositivo mobile

Usare le risorse seguenti per raccogliere i dati del dispositivo durante la risoluzione dei problemi dei dispositivi dell'utente:
  - [Send iOS enrollment errors to your IT administrator (Inviare gli errori di registrazione iOS all'amministratore IT)](/intune-user-help/send-errors-to-your-it-admin-ios)
  - [Aiutare il supporto tecnico dell'azienda a risolvere i problemi dei dispositivi con la registrazione dettagliata](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
  - [Inviare i log di Android al supporto tecnico dell'azienda usando un cavo USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Send Android diagnostic data logs to your IT administrator using email (Inviare i log dei dati Android di diagnostica all'amministratore IT tramite posta elettronica)](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
  - [Send Android enrollment errors to your IT administrator (Inviare gli errori di registrazione Android all'amministratore IT)](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>Passaggi successivi

È possibile ottenere altre informazioni sull'uso del controllo degli accessi in base al ruolo (RBAC) per definire i ruoli nel dispositivo aziendale, gestire app per dispositivi mobili e implementare attività di protezione dati. Per altre informazioni, vedere [Controllo degli accessi in base al ruolo (RBAC) con Intune](/intune/role-based-access-control).

È possibile ottenere informazioni sui problemi noti in Microsoft Intune. Per altre informazioni, vedere [Problemi noti in Microsoft Intune](/intune/known-issues).

È possibile apprendere come creare un ticket di supporto e ottenere supporto quando è necessario. [Ottenere supporto](/intune/get-support).
