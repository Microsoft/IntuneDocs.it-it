---
title: Gruppi di Intune classici nel portale di Azure
titleSuffix: Intune on Azure
description: "Informazioni sulle novità dei gruppi nel portale di Azure di Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
ms.custom: intune-azure
ms.openlocfilehash: c51c3102cc78cf095e27da4ff199cb3fb5ae14a6
ms.sourcegitcommit: 45204e0fb8cb4cce449e65f2f1d7bb6f6ac4ccf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2017
---
# <a name="intune-classic-groups-in-the-azure-portal"></a>Gruppi di Intune classici nel portale di Azure

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Sulla base del feedback degli utenti sono state apportate alcune modifiche alla modalità di uso dei gruppi in Microsoft Intune.
Se si usa Intune dal portale di Azure, i gruppi di Intune sono stati migrati a gruppi di sicurezza di Azure Active Directory.

Il vantaggio consiste nella possibilità di usare ora la stessa esperienza dei gruppi in tutte le app di Enterprise Mobility + Security e di Azure AD. È anche possibile usare PowerShell e l'API Graph per estendere e personalizzare questa nuova funzionalità.

I gruppi di sicurezza di Azure AD supportano tutti i tipi di distribuzione di Intune, sia per gli utenti che per i dispositivi. Inoltre, è possibile usare i gruppi dinamici di Azure AD che vengono aggiornati automaticamente in base agli attributi specificati. Si potrebbe creare, ad esempio, un gruppo per i dispositivi che eseguono iOS 9. Ogni volta che viene registrato un dispositivo che esegue iOS 9, il dispositivo viene visualizzato automaticamente nel gruppo dinamico.

## <a name="what-is-not-available"></a>Funzionalità non disponibili

Alcune delle funzionalità dei gruppi di Intune precedentemente previste non sono disponibili in Azure AD:

- Non sono più disponibili i gruppi di Intune **Utenti non raggruppati** e **Dispositivi non raggruppati**.
- L'opzione **Escludi membri specifici** da un gruppo non è presente nel portale di Azure. È comunque possibile usare un gruppo di sicurezza di Azure AD con regole avanzate per replicare questo comportamento. Ad esempio, per creare una regola avanzata che includa in un gruppo di sicurezza tutti gli utenti del reparto vendite, ma non gli utenti che contengono la parola "Assistente" nella qualifica professionale, è possibile usare la regola avanzata seguente:

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- Non è stata eseguita la migrazione del gruppo **Tutti i dispositivi gestiti di Exchange ActiveSync** della console di Intune ad Azure AD. È comunque ancora possibile accedere alle informazioni sui dispositivi gestiti di EAS dal portale di Azure.

## <a name="how-to-get-started"></a>Come iniziare

- Leggere gli argomenti seguenti per informazioni sui gruppi di sicurezza di Azure AD e sul relativo funzionamento:
    -  [Gestione dell'accesso alle risorse con i gruppi di Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/).
    -  [Gestione dei gruppi in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Uso di attributi per la creazione di regole avanzate](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-  Assicurarsi che gli amministratori che devono creare gruppi vengano aggiunti al ruolo di Azure AD **Amministratore del servizio Intune**. Il ruolo Amministratore dei servizi di Azure AD non ha le autorizzazioni **Gestisci gruppo**.
-  Se i gruppi di Intune usavano l'opzione **Escludi membri specifici**, determinare se è possibile riprogettare questi gruppi senza esclusioni o se per soddisfare le esigenze aziendali sono necessarie regole avanzate.


## <a name="what-happened-to-intune-groups"></a>Cosa è accaduto ai gruppi di Intune
Quando i gruppi vengono migrati dal portale Intune classico a Intune nel portale di Azure, vengono applicate le regole seguenti:

| Gruppi in Intune classico|Gruppi in Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Gruppo di utenti statico|Gruppo di sicurezza di Azure AD statico|
|Gruppo di utenti dinamico|Gruppi di sicurezza statici di Azure AD con una gerarchia di gruppo di sicurezza di Azure AD|
|Gruppo di dispositivi statico|Gruppo di sicurezza di Azure AD statico|
|Gruppo di dispositivi dinamico|Gruppo di sicurezza di Azure AD dinamico|
|Gruppo con una condizione di inclusione|Gruppo di sicurezza di Azure AD statico che contiene gli eventuali membri statici o dinamici dalla condizione di inclusione in Intune|
|Gruppo con una condizione di esclusione|Non incluso nella migrazione|
|Gruppi predefiniti:<br>- **Tutti gli utenti**<br>- **Utenti non raggruppati**<br>- **Tutti i dispositivi**<br>- **Dispositivi non raggruppati**<br>- **Tutti i computer**<br>- **Tutti i dispositivi mobili**<br>- **Tutti i dispositivi gestiti con MDM**<br>- **Tutti i dispositivi gestisti con EAS**|Gruppi di sicurezza di Azure AD|

## <a name="group-hierarchy"></a>Gerarchia dei gruppi

Nella console di Intune classica, tutti i gruppi disponevano di un gruppo padre. I gruppi potevano contenere solo membri del gruppo padre corrispondente. In Azure AD i gruppi figlio possono contenere membri non presenti nel gruppo padre.

## <a name="group-attributes"></a>Attributi del gruppo
Gli attributi sono proprietà del dispositivo che possono essere usate nella definizione dei gruppi. Questa tabella descrive come viene eseguita la migrazione di tali criteri ai gruppi di sicurezza di Azure AD.

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

I criteri e le app continuano a essere distribuiti ai gruppi, esattamente come prima. Questi gruppi dovranno essere tuttavia gestiti dal portale di Azure, invece che dalla console di Intune classico.
