---
title: Pagina Stato del tenant di Microsoft Intune
titleSuffix: Microsoft Intune
description: Usare la pagina Stato del tenant di Intune per visualizzare dettagli importanti sul tenant senza uscire dal portale di Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0cde1977b0c126f478abae06860110acc2f10444
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61514175"
---
# <a name="intune-tenant-status-page"></a>Pagina Stato del tenant di Intune
La pagina Stato del tenant è un hub centralizzato in cui è possibile visualizzare informazioni dettagliate aggiornate e importanti sul tenant. Queste informazioni includono la disponibilità e l'uso di licenze, lo stato del connettore e importanti comunicazioni sul servizio Intune.  

Per visualizzare il dashboard, nel portale di Azure passare a **Intune > Stato del tenant**.  La pagina Stato del tenant si trova nel **gruppo Guida e supporto**.  

È suddivisa in quattro aree:

## <a name="tenant-details"></a>Dettagli del tenant
L'area Dettagli del tenant fornisce informazioni immediate sul tenant. Sono disponibili dettagli come il nome e la posizione del tenant, l'autorità MDM e il numero di versione del servizio del tenant. Il numero di versione del servizio è un collegamento che apre l'articolo *Novità in Intune* della documentazione Microsoft. Nella pagina *Novità* è possibile leggere informazioni sulle funzionalità più recenti e sugli aggiornamenti al servizio Intune.  

Questa sezione fornisce anche informazioni di base sulle licenze disponibili e sul numero di licenze assegnate agli utenti. Le licenze per i dispositivi non vengono visualizzate.

## <a name="connector-status"></a>Stato connettore
L'area Stato del connettore è una posizione centralizzata in cui verificare lo stato di tutti i connettori disponibili per Intune.  

I connettori sono:
- **Connessioni configurate a servizi esterni**. Ad esempio, il servizio *Volume Purchase Program di Apple* o il servizio *Windows AutoPilot*.  Lo stato di questo tipo di connettore si basa sull'ora dell'ultima sincronizzazione riuscita.
- **Certificati o credenziali necessari per connettersi a un servizio non gestito esterno**, come i certificati *Apple Push Notification Service* (APNS). Lo stato di questo tipo di connettore si basa sul timestamp di scadenza del certificato o delle credenziali.  

Per impostazione predefinita, vengono visualizzati fino a cinque connettori. È possibile selezionare **Visualizza tutti i connettori** per espandere l'elenco e vedere tutti i connettori disponibili, inclusi quelli non configurati per l'uso.  

I connettori non integri vengono sempre visualizzati all'inizio dell'elenco. Seguono i connettori con avvisi e quindi l'elenco dei connettori integri. I connettori non ancora configurati sono visualizzati per ultimi.

Quando esiste più di un connettore di un determinato tipo, lo stato è un riepilogo di tutti i connettori di quello stesso tipo. Lo stato del connettore meno integro viene usato per indicare l'integrità del gruppo.  

**Stato del connettore**:
- **Non integro:**
    - Il certificato o le credenziali sono scadute
    - L'ultima sincronizzazione è avvenuta non prima di tre giorni fa
- **Avviso:**
    - Il certificato o le credenziali scadranno entro sette giorni
    - L'ultima sincronizzazione è avvenuta più di un giorno fa
- **Integro:**
    - Il certificato o le credenziali non scadranno nei prossimi sette giorni
    - L'ultima sincronizzazione è avvenuta meno di un giorno fa  

Quando si seleziona un connettore dall'elenco, il portale presenta la pagina del portale pertinente per la creazione o la configurazione del connettore.  Ad esempio, se si seleziona il connettore **Data di scadenza VPP**, si apre la pagina **Token iOS con Volume Purchase Program** che contiene maggiori dettagli sul connettore. È quindi possibile creare una nuova configurazione o modificare e correggere i problemi di una configurazione esistente.  

## <a name="intune-service-health"></a>Integrità del servizio Intune  
È possibile visualizzare i dettagli relativi agli eventi imprevisti e agli avvisi attivi senza dover passare al dashboard per l'integrità dei servizi o al Centro messaggi di Microsoft 365, entrambi disponibili nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com). Sono visualizzati solo gli eventi imprevisti di cui è stato notato un impatto sul tenant.  

Quando si seleziona un evento imprevisto, i relativi dettagli vengono presentati direttamente nella pagina Stato del tenant. Per visualizzare gli avvisi e gli eventi imprevisti relativi al passato, selezionare **See past Incidents/Advisories** (Visualizza eventi imprevisti/avvisi precedenti). Viene aperta l'interfaccia di amministrazione di Microsoft 365 con gli avvisi e gli eventi imprevisti degli ultimi 30 giorni per il tenant.  

Per visualizzare informazioni su *Integrità del servizio Intune*, l'account deve avere il ruolo **Amministratore globale** o **Amministratore del servizio** in Azure Active Directory o nell'interfaccia di amministrazione di Microsoft 365. Per assegnare queste autorizzazioni, accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) con autorizzazioni di amministratore globale. Selezionare **Utenti > Utenti attivi** e quindi selezionare l'account che ha bisogno dell'accesso. Selezionare **Modifica** per Ruoli, selezionare *Amministratore del servizio* o *Amministratore globale* e quindi scegliere **Salva** per salvare le modifiche e assegnare le autorizzazioni.  

Nell'interfaccia di amministrazione di Microsoft 365 è possibile solo configurare le preferenze di comunicazione per Integrità del servizio Intune.

## <a name="intune-news"></a>Novità su Intune  
Questa area consente di visualizzare comunicazioni di carattere informativo del team del servizio Intune senza dover passare al Centro messaggi di Office. Le comunicazioni includono messaggi sulle modifiche apportate di recente al servizio Intune o che verranno presto implementate per il tenant.  

Per impostazione predefinita, vengono visualizzati gli ultimi 10 messaggi attivi. Per visualizzare i messaggi meno recenti, selezionare **Visualizza i messaggi precedenti** per aprire il *Centro messaggi* nell'interfaccia di amministrazione di Microsoft 365.  

Per visualizzare informazioni relative alle novità su Intune, l'account deve avere il ruolo **Amministratore globale** o **Amministratore del servizio** in Azure Active Directory o il **ruolo con autorizzazioni di lettura per il Centro messaggi** nell'interfaccia di amministrazione di Microsoft 365.  Per assegnare queste autorizzazioni, accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) con autorizzazioni di amministratore. Selezionare **Utenti > Utenti attivi** e quindi selezionare l'account che ha bisogno dell'accesso. Selezionare **Modifica** per *Ruoli*, selezionare *Amministratore delle comunicazioni con Teams* e quindi scegliere **Salva** per salvare le modifiche e assegnare le autorizzazioni.  

Nell'interfaccia di amministrazione di Microsoft 365 è possibile solo configurare le preferenze di comunicazione per Novità su Intune.
