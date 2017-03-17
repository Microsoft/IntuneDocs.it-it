---
title: Migrazione ai gruppi di Azure Active Directory | Documentazione Microsoft
description: Informazioni sulla migrazione di gruppi da Intune ad Azure AD
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 12/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 911d2887791cf16d4290c3ac5189aa44086f4603
ms.openlocfilehash: d3b4b823683196148d4fb8aa296b59c9c712e99f
ms.lasthandoff: 03/11/2017


---

# <a name="a-new-way-of-using-groups-in-intune"></a>Un nuovo modo per usare i gruppi in Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Sulla base del feedback degli utenti sono state apportate alcune modifiche alla modalità di utilizzo dei gruppi in Microsoft Intune.
È in corso la migrazione di tutti i gruppi di Intune dei clienti in gruppi di sicurezza di Azure Active Directory.

Il vantaggio è la possibilità di usare allo stesso modo i gruppi in tutte le app Enterprise Mobility + Security e Azure AD. Sarà anche possibile usare PowerShell e l'API Graph per estendere e personalizzare questa nuova funzionalità.

I gruppi di sicurezza di Azure AD supportano tutti i tipi di distribuzione di Intune, sia per gli utenti che per i dispositivi. Inoltre, è possibile usare i gruppi dinamici di Azure AD che vengono aggiornati automaticamente in base agli attributi specificati. Si potrebbe creare, ad esempio, un gruppo per i dispositivi che eseguono iOS 9. Ogni volta che viene registrato un nuovo dispositivo che esegue iOS 9, questo verrà aggiunto automaticamente al gruppo dinamico.

## <a name="when-is-this-happening"></a>Tempistica prevista

Il processo di migrazione è in corso al momento e i clienti riceveranno una notifica prima della migrazione dei loro gruppi.
Se la migrazione è già stata eseguita, verrà visualizzato un messaggio simile al seguente quando si tenta di accedere ai gruppi dalla console di Intune classica:

![Messaggio visualizzato dopo la migrazione dei gruppi.](http://i.imgur.com/72KRaXj.png)

## <a name="what-wont-be-available"></a>Funzionalità non più disponibili

Alcune funzionalità esistenti dei gruppi di Intune non sono disponibili in Azure AD:

- Non verrà eseguita la migrazione dei gruppi di Intune **Utenti non raggruppati** e **Dispositivi non raggruppati**.
- L'opzione **Escludi membri specifici** per escludere membri da un gruppo esistente nella console di Intune non esiste nel portale di Azure. È comunque possibile usare un gruppo di sicurezza di Azure AD con regole avanzate per replicare questo comportamento. Ad esempio, è possibile creare una regola avanzata che include tutti gli utenti del reparto vendite in un gruppo di sicurezza, ma non gli utenti che contengono la parola "Assistant" nella posizione professionale, con questa regola avanzata: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- Non verrà eseguita la migrazione del gruppo **Tutti i dispositivi gestiti di Exchange ActiveSync** predefinito della console di Intune. È comunque ancora possibile accedere alle informazioni sui dispositivi gestiti di EAS dal portale di Azure.
- Non sarà possibile filtrare i report in base ai gruppi nella console di Intune classica.
<!--- - Custom group targeting of notification rules will not be available. ROB I took this out as I couldn't replicate the behavior. --->

## <a name="how-to-get-ready"></a>Come prepararsi

- Leggere gli argomenti seguenti relativi ad Azure AD per informazioni sui gruppi di sicurezza di Azure AD e sul relativo funzionamento:
    -  [Gestione dell'accesso alle risorse con i gruppi di Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
    -  [Gestione dei gruppi in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Uso di attributi per la creazione di regole avanzate](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
- Valutare la possibilità di rimuovere eventuali gruppi di Intune non più in uso prima della migrazione.
-  Assicurarsi che tutti gli amministratori che devono creare gruppi vengano aggiunti al ruolo di Azure AD **Amministratore del servizio Intune**. Tenere presente che il ruolo Amministratore dei servizi di Azure AD non ha le autorizzazioni **Gestisci gruppo**.
-  Se si usano gruppi con l'opzione **Escludi membri specifici**, valutare se è possibile riprogettare questi gruppi per evitare esclusioni oppure se è possibile usare regole avanzate nella query di Azure AD per ottenere lo stesso risultato.


## <a name="what-happens-to-intune-groups"></a>Cosa accade ai gruppi di Intune

| Gruppi in Intune|Gruppo in Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Gruppo di utenti statico|Gruppo di sicurezza di Azure AD statico|
|Gruppo di utenti dinamico|Gruppi di sicurezza statici di Azure AD con una gerarchia di gruppo di sicurezza di Azure AD|
|Gruppo di dispositivi statico|Gruppo di sicurezza di Azure AD statico|
|Gruppo di dispositivi dinamico|Gruppo di sicurezza di Azure AD dinamico|
|Gruppo con una condizione di inclusione|Gruppo di sicurezza di Azure AD statico che contiene gli eventuali membri statici o dinamici dalla condizione di inclusione in Intune.|
|Gruppo con una condizione di esclusione|Non incluso nella migrazione|
|Gruppi predefiniti **Tutti gli utenti**, **Utenti non raggruppati**, **Tutti i dispositivi**, **Dispositivi non raggruppati**, **Tutti i computer**, **Tutti i dispositivi mobili**, **Tutti i dispositivi gestiti direttamente** e **Tutti i dispositivi gestiti di Exchange ActiveSync**|Gruppi di sicurezza di Azure AD.|

In Intune, tutti i gruppi devono avere un gruppo padre. I gruppi possono contenere solo membri dal relativo gruppo padre. In Azure AD i gruppi figlio possono contenere membri non inclusi nel gruppo padre.

Gli attributi sono proprietà del dispositivo che possono essere usate nella definizione dei gruppi. Questa tabella descrive come viene eseguita la migrazione di tali criteri nei gruppi di sicurezza di Azure AD.

| Attributo in Intune|Attributo in Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Attributo unità organizzativa per i gruppi di dispositivi|Attributo dell'unità organizzativa per i gruppi dinamici.|
|Attributo del nome di dominio per i gruppi di dispositivi|Attributo del nome di dominio per i gruppi dinamici.|
|Gruppo di sicurezza come attributo per i gruppi di utenti|I gruppi non possono essere attributi nelle query dinamiche di Azure AD. I gruppi dinamici possono contenere solo attributi specifici del dispositivo o dell'utente.|
|Attributo Manager per i gruppi di utenti|Regola avanzata per l'attributo *Manager* in gruppi dinamici|
|Tutti gli utenti dal gruppo utenti padre|Gruppo statico con il gruppo come membro|
|Tutti i dispositivi mobili del gruppo di dispositivi padre|Gruppo statico con il gruppo come membro|
|Tutti i dispositivi mobili gestiti da Intune|Attributo di tipo di gestione con 'gestione dei dispositivi mobili' come valore per un gruppo dinamico|
|Gruppi nidificati all'interno di gruppi statici |Gruppi nidificati all'interno di gruppi statici|
|Gruppi nidificati all'interno di gruppi dinamici|Gruppo dinamico con un livello di annidamento|

## <a name="what-happens-to-policies-and-apps-youve-already-deployed"></a>Cosa accade ai criteri e alle app già distribuiti?

I criteri e le app continuano a essere distribuiti ai gruppi, esattamente come prima. Questi gruppi dovranno essere tuttavia gestiti dal portale di Azure, invece che dalla console di Intune classica.
 

