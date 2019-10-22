---
title: Gestire le app dal sito Web del Portale aziendale Intune
description: Gestire e visualizzare le app disponibili e installate
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 06/27/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: edc45fb3ddab43ef77a3f072c5a1a31f8f88c957
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506104"
---
# <a name="manage-apps-from-the-company-portal-website"></a>Gestire le app dal sito Web del portale aziendale 
Visitare il [sito web portale aziendale](https://portal.manage.microsoft.com) per visualizzare e gestire le app dell'organizzazione. 

## <a name="view-all-apps"></a>Visualizza tutte le app  
Dal menu selezionare **app** per visualizzare tutte le app rese disponibili dall'organizzazione. 

   ![Screenshot del sito Web Portale aziendale, pagina app, che mostra le opzioni di perfezionamento.](./media/intune-view-apps-1907.png)  

Questa pagina elenca i dettagli seguenti su ogni app:  

* Nome: il nome dell'app, con un collegamento alla pagina dei dettagli dell'app.
* Publisher: il nome dello sviluppatore o della società che ha distribuito l'app. Un server di pubblicazione è in genere un fornitore di software o un'organizzazione.  
* Data di pubblicazione: la data in cui l'app è stata resa disponibile per il download. La data di pubblicazione potrebbe visualizzare la versione iniziale o l'aggiornamento più recente di un'app.
* Stato: lo stato corrente dell'app nel dispositivo, che include disponibile, installato e installato. 
* Categoria: funzione o scopo dell'app, ad esempio in primo piano, progettazione, istruzione e produttività.  

### <a name="search-and-refine"></a>Ricerca e perfezionamento   

Usare la barra di ricerca per trovare le app. I risultati della ricerca sono ordinati automaticamente per pertinenza.  

   ![Screenshot del sito Web Portale aziendale, pagina app, che mostra le opzioni di perfezionamento.](./media/intune-refine-all-apps-1907.png)  

Selezionare **affina** per visualizzare le opzioni di filtro e ordinamento. Filtrare l'elenco per visualizzare le app con criteri specifici, tra cui **tipo**, **disponibilità**e **autori**. Selezionare **Ordina** per ridisporre le app per:

* Nome dell'app, crescente o decrescente in ordine alfabetico 
* Nome dell'editore, crescente o decrescente in ordine alfabetico 
* Data di pubblicazione, meno recente o più recente  

## <a name="view-installed-apps"></a>Visualizza le app installate  
Dal menu selezionare **app installate** per visualizzare un elenco di tutte le app installate nel dispositivo.  

   ![Screenshot del sito Web del portale aziendale, pagina App installate.](./media/intune-installed-apps-1907.png)  


Questa pagina elenca i dettagli seguenti su ogni app:  

* Nome: il nome dell'app, con un collegamento alla pagina dei dettagli dell'app.
* Tipo di assegnazione: il modo in cui l'app viene assegnata e resa disponibile. Per altri dettagli, vedere app disponibili e richieste. L'organizzazione può rendere un'app disponibile per l'installazione o può richiedere e installare automaticamente un'app nel dispositivo.  
* Publisher: il nome dello sviluppatore o della società che ha distribuito l'app. Un server di pubblicazione è in genere un fornitore di software o un'organizzazione.  
* Data di pubblicazione: la data in cui l'app è stata resa disponibile per il download. La data di pubblicazione potrebbe visualizzare la versione iniziale o l'aggiornamento più recente di un'app.
* Stato: lo stato di installazione corrente dell'app nel dispositivo. Le app possono essere visualizzate come installazione, installazione e installazione non riuscita. Per visualizzare uno stato aggiornato, le app richieste potrebbero richiedere fino a 10 minuti.  

### <a name="search-and-refine"></a>Ricerca e perfezionamento  

Usare la barra di ricerca per trovare le app. I risultati della ricerca sono ordinati automaticamente per pertinenza.  

   ![Screenshot del sito Web del Portale aziendale, App installate, opzioni di affinamento.](./media/intune-installed-refine-1907.png)  

Selezionare **affina** per visualizzare le opzioni di filtro e ordinamento. Filtrare l'elenco per visualizzare le app con criteri specifici, inclusi i **tipi**, i **Publisher**e gli **Stati**. Selezionare **Ordina** per ridisporre le app per:

* Nome dell'app, crescente o decrescente in ordine alfabetico  
* Nome dell'editore, crescente o decrescente in ordine alfabetico  
* Data di pubblicazione, meno recente o più recente  

Servono altre informazioni? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  

### <a name="available-and-required-apps"></a>App disponibili e richieste
Le app vengono assegnate dall'organizzazione e contrassegnate come disponibili o obbligatorie. La pagina **app installate** Mostra le app presenti nella colonna **tipo di assegnazione** . 


* App disponibili: queste app sono selezionate dall'organizzazione e sono appropriate e utili per l'azienda o l'Istituto di istruzione. Sono facoltativi per l'installazione e sono le uniche app disponibili nella Portale aziendale per l'installazione. 

* App richieste: l'organizzazione potrebbe distribuire le app di lavoro e dell'Istituto di istruzione necessarie direttamente nel dispositivo. Queste app vengono installate automaticamente senza alcun intervento da parte dell'utente. 

Le app sono inoltre disponibili in base al tipo di dispositivo. Ad esempio, se si usa il sito Web del portale aziendale in un dispositivo Windows, si avrà accesso alle app per Windows, ma non alle app per iOS.  

## <a name="view-app-details"></a>Visualizza i dettagli dell'app  
Selezionare un'app nella pagina **app** o **app installate** per visualizzarne i dettagli. Verranno **illustrati i dettagli delle app**, in cui sono disponibili la descrizione e i requisiti dell'app. Se un'app non è già installata nel dispositivo, è possibile installarla da questa pagina. 


   ![Screenshot del sito Web Portale aziendale, pagina dei dettagli dell'app.](./media/intune-app-details-1907.png)  

## <a name="next-steps"></a>Passaggi successivi
Ulteriore assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
