---
title: Panoramica degli scenari guidati
titleSuffix: Microsoft Intune
description: Informazioni sugli scenari guidati di Intune disponibili nel portale di gestione dei dispositivi per Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 460cabead711e6fa4559bcec39e556448cdf2237
ms.sourcegitcommit: 2c8a41ee95a3fde150667a377770e51b621ead65
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73635356"
---
# <a name="intune-guided-scenarios-overview"></a>Panoramica degli scenari guidati di Intune 

Uno scenario guidato è costituito da una serie personalizzata di passaggi incentrati su un caso d'uso end-to-end. Gli scenari comuni sono basati sul ruolo svolto da un amministratore, un utente o un dispositivo nell'organizzazione. Questi ruoli richiedono in genere una raccolta di profili, impostazioni, applicazioni e controlli di sicurezza orchestrati con attenzione per offrire livelli ottimali di esperienza utente e sicurezza.    

Se non si ha familiarità con tutti i passaggi e le risorse necessari per implementare uno scenario specifico di Intune, è possibile usare gli scenari guidati come punto di partenza. Lo scenario guidato prevede l'assemblaggio automatico di criteri, app, assegnazioni e altre configurazioni di gestione. Inoltre, gli scenari guidati possono omettere intenzionalmente alcune opzioni non applicabili o non comuni per lo scenario in questione. 

Gli scenari guidati non sono uno spazio di gestione diverso dai flussi di lavoro normali di Intune. Questi flussi di lavoro sono progettati per essere usati insieme ai flussi di lavoro esistenti di Intune per i profili, le app e i criteri. Dopo il completamento di uno scenario guidato, tutte le future attività di gestione dello scenario devono essere eseguite tramite i menu esistenti per i criteri, le app e i profili. Uno scenario guidato non salva un tipo di risorsa "scenario guidato" o tiene traccia delle modifiche future apportate alle risorse. Ogni risorsa creata da uno scenario guidato verrà visualizzata nel rispettivo carico di lavoro. Tutte le opzioni, anche quelle omesse nello scenario guidato, saranno disponibili per la modifica nei menu esistenti.  

## <a name="types-of-guided-scenarios"></a>Tipi di scenari guidati 

Per motivi di semplicità, tutti gli scenari guidati omettono le funzionalità di ambito complesse, ad esempio tag di ambito <link>, gruppi di esclusione e assegnazioni di gruppi virtuali <link>. Tutte le risorse create da uno scenario guidato erediteranno ogni tag di ambito dell'amministratore che completa lo scenario. Alcuni scenari offrono un certo livello di personalizzazione per l'impostazione comune per coprire scenari strettamente correlati. Questi scenari supportano solo l'assegnazione dei gruppi ai gruppi di inclusione. Per altri scenari guidati, l'intero scenario garantisce un'esperienza coerente non offrendo alcuna personalizzazione e genera automaticamente un nuovo gruppo che riceverà tutte le assegnazioni. Una volta completato lo scenario guidato, è possibile usare assegnazioni più elaborate direttamente tramite i carichi di lavoro esistenti per criteri, app e profili.  

Sono disponibili gli scenari guidati seguenti: 
- Distribuisci Microsoft Edge per dispositivi mobili 
- Mostrami un PC gestito dal cloud
- Proteggi le app di Office per dispositivi mobili 

## <a name="guided-scenario-functionality"></a>Funzionalità dello scenario guidato 

Gli scenari guidati offrono funzionalità specifiche. Le informazioni dettagliate seguenti illustrano le operazioni che possono e non possono essere eseguite nel corso di uno scenario guidato.

### <a name="launching"></a>Avvio  

Tutti gli scenari guidati sono disponibili dal **[portale di gestione dei dispositivi](https://devicemanagement.microsoft.com)**  > **Risoluzione dei problemi e supporto tecnico** > **Scenari guidati**. 

Lo scenario guidato inizia con un'introduzione che illustra lo scopo dello scenario ed eventuali prerequisiti necessari per completare la configurazione. A questo punto, vengono controllate le autorizzazioni di amministratore per verificare che siano disponibili tutti i privilegi necessari per completare lo scenario.  

Una volta superati tutti i controlli dei prerequisiti, lo scenario offre le impostazioni appropriate per la personalizzazione. Gli scenari guidati sono progettati in modo da richiedere input solo per il numero minimo di impostazioni e in modo da nascondere le impostazioni non comuni o avanzate a meno che non siano necessarie o in base a circostanze particolari. Ogni scenario guidato include collegamenti alla documentazione con informazioni dettagliate aggiuntive. 

Dopo aver immesso tutte le impostazioni obbligatorie, lo scenario guidato presenta un riepilogo delle impostazioni immesse e delle risorse richieste dallo scenario. A questo punto, nulla è stato salvato a meno che non sia stato indicato in modo esplicito.

Il passaggio successivo consiste nel distribuire lo scenario. La distribuzione di uno scenario crea e salva tutte le risorse necessarie e le impostazioni selezionate. Il tempo necessario per completare una distribuzione varia in base allo scenario. Al termine della distribuzione, lo scenario guidato presenta un elenco delle risorse create con collegamenti alla visualizzazione di gestione di ogni risorsa, al carico di lavoro normale della risorsa e alla documentazione. 

> [!IMPORTANT]
> L'elenco presentato alla fine dello scenario guidato non viene salvato ed è visualizzabile solo quando lo scenario guidato è aperto.  
Se si verifica un errore durante la distribuzione dello scenario, verranno annullate tutte le modifiche. 

### <a name="editing"></a>Modifica 

Non è possibile usare gli scenari guidati per modificare le risorse esistenti. Una volta creati, le risorse, i gruppi e le assegnazioni devono tutti essere modificati usando i carichi di lavoro esistenti.

### <a name="monitoring"></a>Monitoraggio 

Gli scenari guidati non possono essere usati per monitorare le risorse esistenti oltre al processo di creazione iniziale. Una volta creati, le risorse, i gruppi e le assegnazioni devono tutti essere monitorati usando i carichi di lavoro esistenti. 

### <a name="retiring"></a>Ritiro 

Gli scenari guidati non possono essere usati per ritirare risorse esistenti, oltre alla pulizia automatica durante un errore nella distribuzione iniziale. Una volta creati, le risorse, i gruppi e le assegnazioni devono tutti essere ritirati usando i carichi di lavoro esistenti. 

### <a name="updating"></a>Aggiornamento

Con l'evolversi della tecnologia, Intune potrebbe aggiornare occasionalmente uno scenario guidato per migliorare l'esperienza utente, la sicurezza o altri aspetti dello scenario. Questo aggiornamento influirà solo sulle nuove distribuzioni effettuate dallo scenario guidato. Intune non aggiornerà le risorse esistenti generate in precedenza dallo scenario guidato in base alle nuove procedure consigliate o raccomandazioni.  

## <a name="next-steps"></a>Passaggi successivi

Per acquisire familiarità velocemente con Microsoft Intune, usare gli scenari guidati di Intune. Gli utenti senza esperienza di Intune possono configurare il tenant di Intune seguendo l'[avvio rapido per la versione di valutazione gratuita](free-trial-sign-up.md).
