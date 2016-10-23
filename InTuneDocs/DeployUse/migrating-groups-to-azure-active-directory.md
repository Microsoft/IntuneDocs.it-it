---
title: Migrazione ai gruppi di Azure Active Directory | Microsoft Intune
description: Informazioni sulla migrazione di gruppi da Intune ad Azure AD
keywords: 
author: nbigman
manager: angerobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
translationtype: Human Translation
ms.sourcegitcommit: d92c9ffe42b36770a32c28941de3c402aec9dd68
ms.openlocfilehash: 08bcc258f64e6385ae6fa648ddb8f2b5fe68942e


---

## Nuova esperienza di amministrazione per i gruppi
    
Sulla base dei commenti e dei suggerimenti degli utenti in cui venivano richieste funzionalità di raggruppamento e assegnazione in Enterprise Mobility + Security, Microsoft ha deciso di convertire i gruppi di Intune in gruppi di sicurezza basati su Azure Active Directory. In questo modo la gestione dei gruppi verrà unificata in Intune e Azure Active Directory (Azure AD). Questa nuova esperienza consentirà di evitare la duplicazione dei gruppi tra i servizi e offrirà estendibilità tramite PowerShell e Graph. 

### Come e quando sarà possibile eseguire la migrazione ai nuovi gruppi?
La migrazione dei clienti correnti avverrà in certo lasso di tempo, non prima di dicembre 2016. Prima della migrazione, i gruppi riceveranno una notifica. Per domande e chiarimenti sulla migrazione, contattare il team addetto all'indirizzo [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### Quali saranno le nuove funzionalità disponibili?
Di seguito sono indicate le nuove funzionalità che verranno introdotte: 
 
-    I gruppi di sicurezza di Azure AD saranno supportati in Intune per tutti i tipi di distribuzione. 
-    I gruppi di sicurezza di Azure AD supporteranno il raggruppamento sia di dispositivi che di utenti.
-    I gruppi di sicurezza di Azure AD supporteranno i gruppi dinamici con attributi dei dispositivi di Intune. Ad esempio, sarà possibile raggruppare dinamicamente dei dispositivi in base alla piattaforma, ad esempio iOS. In questo modo, quando nell'organizzazione viene registrato un nuovo dispositivo iOS, tale dispositivo verrà aggiunto automaticamente al gruppo dinamico di dispositivi iOS.
-    Esperienze di amministrazione condivisa per la gestione dei gruppi in Azure AD e Intune.
- Ad Azure AD verrà aggiunto il *ruolo di amministratore del servizio di Intune* per consentire agli amministratori del servizio Intune di eseguire attività di gestione dei gruppi in Azure AD.

 
### Quali funzionalità di Intune non saranno disponibili?
Anche se l'esperienza di raggruppamento registrerà dei miglioramenti, alcune funzionalità di Intune non saranno disponibili dopo la migrazione.

#### Funzionalità di gestione dei gruppi

-   Non sarà possibile escludere membri o gruppi quando si crea un nuovo gruppo. I gruppi dinamici di Azure AD, tuttavia, consentiranno di usare gli attributi per creare regole avanzate di esclusione di membri sulla base di criteri. Ad esempio, è possibile creare una regola avanzata che include tutti gli utenti del reparto vendite in un gruppo di sicurezza, ma non gli utenti che contengono la parola "Assistente" nel titolo, con l'impostazione seguente: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`. Per altre informazioni, vedere [Uso di attributi per la creazione di regole avanzate](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-   I gruppi **Utenti non raggruppati** e **Dispositivi non raggruppati** non saranno supportati. La migrazione di tali gruppi non verrà eseguita.

#### Funzionalità dipendenti dai gruppi

-   Il ruolo Amministratore del servizio non disporrà delle autorizzazioni di tipo **Gestisci gruppi**.
-   Non sarà possibile raggruppare dispositivi Exchange ActiveSync.  Il gruppo **All EAS Managed Devices** (Tutti i dispositivi gestiti da EAS) verrà convertito in visualizzazione di report.
-  La trasformazione in report tramite Pivot con gruppi non sarà disponibile.
-  La possibilità di scegliere gruppi personalizzati come destinazione delle regole di notifica non sarà supportata.

### Quali operazioni è necessario eseguire in preparazione del cambiamento?
 Di seguito sono indicati alcuni accorgimenti che consentiranno di facilitare la migrazione:
 
- Prima della migrazione, eliminare i gruppi di Intune non desiderati o non necessari.
- Valutare l'uso dell'esclusione nei gruppi e considerare come riprogettare i gruppi in modo che non sia necessario usare l'esclusione o che sia possibile usare regole avanzate per ottenere lo stesso scopo.
-  Se sono presenti amministratori che non dispongono delle autorizzazioni per la creazione di gruppi in Azure AD, chiedere all'amministratore di Azure AD di aggiungerli al ruolo di **amministratore del servizio di Intune** di Azure AD.

Sono inoltre disponibili altre informazioni sui gruppi di sicurezza di Azure AD:
-  Per una panoramica, leggere [Gestione dell'accesso alle risorse con i gruppi di Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
-  Per informazioni su come creare e gestire i gruppi di Azure AD, vedere [Gestione dei gruppi in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/).
-  Per altre informazioni sulle regole avanzate per i gruppi di sicurezza, vedere [Uso di attributi per la creazione di regole avanzate](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).

> [!NOTE]
È possibile notare che la documentazione relativa ai gruppi di sicurezza di Azure AD non descrive la creazione di gruppi per i dispositivi. Tale funzionalità verrà abilitata in Azure AD prima che la migrazione dei gruppi di Intune abbia inizio.

## Dettagli sulla migrazione
Di seguito sono presentati i dettagli sulla modalità in cui verrà eseguita la migrazione dei gruppi ad Azure AD.

### Migrazione dei gruppi esistenti

| Il gruppo di Intune diventa...|...un gruppo di sicurezza di Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Gruppi di utenti statici destinati dai criteri di Intune|Gruppi di sicurezza statici di Azure Active Directory contenenti gli stessi utenti|
|Gruppi di utenti dinamici destinati dai criteri di Intune|Gruppi di sicurezza statici di Azure AD con una gerarchia di gruppo di sicurezza di Azure AD|
|Gruppi di dispositivi statici destinati dai criteri di Intune|Gruppi di sicurezza statici di Azure AD con dispositivi|
|Gruppi di dispositivi dinamici con attributi del dispositivo destinati dai criteri di Intune|Gruppi di sicurezza dinamici di Azure AD con attributi del dispositivo|
|Gruppo con una condizione di inclusione|Gruppo di sicurezza statico separato di Azure AD che contiene un gruppo e qualsiasi membro statico o dinamico consentito dalla condizione di inclusione in Intune|
|Gruppo con una condizione di esclusione|...la migrazione non verrà eseguita. Escludere le condizioni non supportate durante la creazione di gruppi statici in Azure AD. Quando si crea un gruppo dinamico in Azure AD, è possibile usare una condizione di esclusione.|
|Gruppi predefiniti **Tutti gli utenti**, **Utenti non raggruppati**, **Tutti i dispositivi**, **Dispositivi non raggruppati**, **Tutti i computer**, **Tutti i dispositivi mobili**, **Tutti i dispositivi gestiti di gestione dei dispositivi mobili** e **Tutti i dispositivi gestiti di EAS** usati nei criteri di Intune  |Gruppi di sicurezza di Azure AD. I gruppi predefiniti non usati dovranno essere creati dal cliente quando necessario mediante gruppi dinamici.|

### Modifiche nelle visualizzazioni gerarchiche
La visualizzazione gerarchica per i gruppi con relazioni padre/figlio in Intune è una relazione di tipo soprainsieme-sottoinsieme, mentre in Azure AD non è così. I figli possono avere membri senza elemento padre. I gruppi possono essere di natura ciclica in Azure AD: un gruppo padre può essere figlio di un gruppo figlio.

### Conversione dell'attributo durante la migrazione
Gli attributi sono proprietà del dispositivo che possono essere usate nella definizione dei gruppi. Questa tabella descrive come viene eseguita la migrazione di tali criteri nei gruppi di sicurezza di Azure AD.

| Attributo di Intune|Attributo di Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Attributo unità organizzativa per i gruppi di dispositivi|Attributo dell'unità organizzativa per i gruppi dinamici. Attribuire i valori resi disponibili per l'amministratore relativi a ogni tenant, aggiungendo quest'ultimo come uno dei componenti tenant per la visualizzazione.|
|Attributo del nome di dominio per i gruppi di dispositivi|Attributo del nome di dominio per i gruppi dinamici. Attribuire i valori resi disponibili per l'amministratore relativi a ogni tenant, aggiungendo quest'ultimo come uno dei componenti tenant per la visualizzazione.|
|Gruppo di sicurezza come attributo per i gruppi di utenti|I gruppi non possono essere attributi nelle query dinamiche di Azure AD. I gruppi dinamici possono contenere solo attributi specifici del dispositivo o dell'utente.|
|Attributo Manager per i gruppi di utenti|Regola avanzata per l'attributo *Manager* in gruppi dinamici|
|Tutti gli utenti dal gruppo utenti padre|Gruppo statico con il gruppo come membro|
|Tutti i dispositivi mobili del gruppo di dispositivi padre|Gruppo statico con il gruppo come membro|
|Tutti i dispositivi mobili gestiti dalla gestione diretta di Microsoft Intune|Attributo di tipo di gestione con 'gestione dei dispositivi mobili' come valore per un gruppo dinamico|
|Tutti i dispositivi mobili gestiti da EAS|I dispositivi EAS non possono essere raggruppati in Azure AD. Il gruppo **All EAS Managed Devices** (Tutti i dispositivi gestiti da EAS) verrà convertito in visualizzazione di report.|
|Gruppi nidificati all'interno di gruppi statici |Gruppi nidificati all'interno di gruppi statici|
|Gruppi nidificati all'interno di gruppi dinamici|Gruppo dinamico con un livello di annidamento|


## Migrazione dei criteri
Durante la migrazione dei gruppi, si continuerà a gestire i criteri nella console di Intune. Nella console di Intune sarà disponibile un collegamento alla console di gestione di Azure in cui gestire i gruppi. I criteri continueranno a essere distribuiti ai gruppi di sicurezza migrati di Azure AD corrispondenti ai precedenti gruppi di Intune.

Quando viene eseguita la migrazione delle funzionalità di Intune al portale di gestione di Azure (circa il primo trimestre del 2017), i criteri e i gruppi verranno gestiti in questa posizione.

     
### Vedere anche
[Gestione dell'accesso alle risorse con i gruppi di Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)

[Gestione dei gruppi in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)

[Utilizzo degli attributi per creare regole avanzate](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)



<!--HONumber=Oct16_HO2-->


