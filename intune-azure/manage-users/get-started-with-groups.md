---
title: Introduzione ai gruppi nell&quot;anteprima di Intune nel portale di Azure | Documentazione Microsoft
description: "Informazioni sulle novità dei gruppi nell&quot;anteprima di Intune nel portale di Azure"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 01/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 27a9c9d8269b302fa9735972056d38e7919f42b5


---

# <a name="get-started-with-groups"></a>Introduzione ai gruppi

[!INCLUDE[azure preview](../includes/azure_preview.md)]

Sulla base del feedback degli utenti sono state apportate alcune modifiche alla modalità di uso dei gruppi in Microsoft Intune.
Se si usa Intune dal portale di Azure, i gruppi di Intune sono stati migrati a gruppi di sicurezza di Azure Active Directory.

Il vantaggio è la possibilità di usare allo stesso modo i gruppi in tutte le app Enterprise Mobility + Security e Azure AD. Sarà anche possibile usare PowerShell e l'API Graph per estendere e personalizzare questa nuova funzionalità.

I gruppi di sicurezza di Azure AD supportano tutti i tipi di distribuzione di Intune, sia per gli utenti che per i dispositivi. Inoltre, è possibile usare i gruppi dinamici di Azure AD che vengono aggiornati automaticamente in base agli attributi specificati. Si potrebbe creare, ad esempio, un gruppo per i dispositivi che eseguono iOS 9. Ogni volta che viene registrato un nuovo dispositivo che esegue iOS 9, questo verrà aggiunto automaticamente al gruppo dinamico.

## <a name="what-is-not-available"></a>Funzionalità non disponibili

Alcune delle funzionalità dei gruppi di Intune precedentemente previste non sono disponibili in Azure AD:

- Non sono più disponibili i gruppi di Intune **Utenti non raggruppati** e **Dispositivi non raggruppati**.
- L'opzione **Escludi membri specifici** da un gruppo non è presente nel portale di Azure. È comunque possibile usare un gruppo di sicurezza di Azure AD con regole avanzate per replicare questo comportamento. Ad esempio, è possibile creare una regola avanzata che include tutti gli utenti del reparto vendite in un gruppo di sicurezza, ma non gli utenti che contengono la parola "Assistant" nella posizione professionale, con questa regola avanzata: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- Non è stata eseguita la migrazione del gruppo **Tutti i dispositivi gestiti di Exchange ActiveSync** predefinito della console di Intune ad Azure AD. È comunque ancora possibile accedere alle informazioni sui dispositivi gestiti di EAS dal portale di Azure.


## <a name="how-to-get-started"></a>Come iniziare

- Leggere gli argomenti seguenti relativi ad Azure AD per informazioni sui gruppi di sicurezza di Azure AD e sul relativo funzionamento:
    -  [Gestione dell'accesso alle risorse con i gruppi di Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
    -  [Gestione dei gruppi in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Uso di attributi per la creazione di regole avanzate](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-  Assicurarsi che tutti gli amministratori che devono creare gruppi vengano aggiunti al ruolo di Azure AD **Amministratore del servizio Intune**. Tenere presente che il ruolo Amministratore dei servizi di Azure AD non ha le autorizzazioni **Gestisci gruppo**.
-  Se si usano gruppi con l'opzione **Escludi membri specifici**, valutare se è possibile riprogettare questi gruppi per evitare esclusioni oppure se è possibile usare regole avanzate nella query di Azure AD per ottenere lo stesso risultato.


## <a name="what-happened-to-intune-groups"></a>Cosa è accaduto ai gruppi di Intune

| Gruppi in Intune|Gruppo in Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Gruppo di utenti statico|Gruppo di sicurezza di Azure AD statico|
|Gruppo di utenti dinamico|Gruppi di sicurezza statici di Azure AD con una gerarchia di gruppo di sicurezza di Azure AD|
|Gruppo di dispositivi statico|Gruppo di sicurezza di Azure AD statico|
|Gruppo di dispositivi dinamico|Gruppo di sicurezza di Azure AD dinamico|
|Gruppo con una condizione di inclusione|Gruppo di sicurezza di Azure AD statico che contiene gli eventuali membri statici o dinamici dalla condizione di inclusione in Intune|
|Gruppo con una condizione di esclusione|Non incluso nella migrazione|
|Gruppi predefiniti **Tutti gli utenti**, **Utenti non raggruppati**, **Tutti i dispositivi**, **Dispositivi non raggruppati**, **Tutti i computer**, **Tutti i dispositivi mobili**, **Tutti i dispositivi gestiti direttamente** e **Tutti i dispositivi gestiti di Exchange ActiveSync**|Gruppi di sicurezza di Azure AD|

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

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>Cosa accade alle app e ai criteri precedentemente distribuiti?

I criteri e le app continuano a essere distribuiti ai gruppi, esattamente come prima. Questi gruppi dovranno essere tuttavia gestiti dal portale di Azure, invece che dalla console di Intune classica.



<!--HONumber=Feb17_HO1-->


