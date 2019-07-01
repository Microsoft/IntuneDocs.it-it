---
title: Gestire le app dal sito Web portale aziendale di Intune
description: Gestire e visualizzare le app disponibili e installate
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 06/27/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c7b91e63a559c45cbbcbd7056a7f5e259e07481
ms.sourcegitcommit: 690e680e854b7d707421c5e06f134e493f4f4194
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416863"
---
# <a name="manage-apps-from-the-company-portal-website"></a>Gestire le app dal sito Web del portale aziendale 
Visitare il [sito Web portale aziendale](https://portal.manage.microsoft.com) per visualizzare e gestire le App dell'organizzazione. 

## <a name="view-all-apps"></a>Visualizza tutte le app  
Nel menu, selezionare **app** per visualizzare tutte le app rese disponibili dall'organizzazione. 

   ![Sito Web screenshot del portale aziendale, pagina delle App, che mostra le opzioni di ridefinizione.](./media/intune-view-apps-1907.png)  

Questa pagina elenca i dettagli seguenti su ogni applicazione:  

* Nome: Il nome dell'app, con un collegamento alla pagina dei dettagli dell'app.
* Server di pubblicazione: Il nome dello sviluppatore o società che ha distribuito l'app. Un server di pubblicazione è in genere un fornitore di software o la tua organizzazione.  
* Data pubblicazione: La data che l'app è stata resa disponibile per il download. Pubblicare data è stato possibile visualizzare la versione iniziale di un'app o aggiorna un'app più recente.
* Stato: Stato corrente dell'app nel dispositivo, che include installazione, installato e disponibile. 
* Categoria: L'app (funzione) o scopi, ad esempio in primo piano, engineering, formazione e produttività.  

### <a name="search-and-refine"></a>Ricerca e ottimizzali in   

Usare la barra di ricerca per trovare le app. I risultati della ricerca sono ordinati automaticamente per pertinenza.  

   ![Sito Web screenshot del portale aziendale, pagina delle App, che mostra le opzioni di ridefinizione.](./media/intune-refine-all-apps-1907.png)  

Selezionare **perfezionare** per visualizzare, filtrare e ordinare le opzioni. Filtrare l'elenco per visualizzare le app con criteri specifici indicati, incluse **tipo**, **disponibilità**, e **editori**. Selezionare **ordinamento** riorganizzare le app da:

* Nome dell'App, crescente o decrescente in ordine alfabetico 
* Nome dell'editore, crescente o decrescente in ordine alfabetico 
* Data, meno recente o più recente di pubblicazione  

## <a name="view-installed-apps"></a>Visualizzare installato le app  
Nel menu, selezionare **App installate** per visualizzare un elenco di tutte le app installate nel dispositivo.  

   ![Sito Web screenshot del portale aziendale, pagina App installate.](./media/intune-installed-apps-1907.png)  


Questa pagina elenca i dettagli seguenti su ogni applicazione:  

* Nome: Il nome dell'app, con un collegamento alla pagina dei dettagli dell'app.
* Tipo di assegnazione: come l'app viene assegnata e reso disponibile al Licenziatario. Vedere disponibilità e le app necessarie per altri dettagli. L'organizzazione può rendere un'app disponibile per l'installazione manualmente, o possono richiedere e installare automaticamente un'app nel dispositivo.  
* Server di pubblicazione: Il nome dello sviluppatore o società che ha distribuito l'app. Un server di pubblicazione è in genere un fornitore di software o la tua organizzazione.  
* Data pubblicazione: La data che l'app è stata resa disponibile per il download. Pubblicare data è stato possibile visualizzare la versione iniziale di un'app o aggiorna un'app più recente.
* Stato: Installazione stato corrente dell'app nel dispositivo. Le app possono mostrare come installare, installazione e installare non è riuscita. Le app obbligatorie potrebbe richiedere fino a 10 minuti per visualizzare un stato aggiornato.  

### <a name="search-and-refine"></a>Ricerca e ottimizzali in  

Usare la barra di ricerca per trovare le app. I risultati della ricerca sono ordinati automaticamente per pertinenza.  

   ![Sito Web di schermata del portale aziendale, le app installate, perfezionare le opzioni.](./media/intune-installed-refine-1907.png)  

Selezionare **perfezionare** per visualizzare, filtrare e ordinare le opzioni. Filtrare l'elenco per visualizzare le app con criteri specifici indicati, incluse **tipi**, **i server di pubblicazione**, e **stati**. Selezionare **ordinamento** riorganizzare le app da:

* Nome dell'App, crescente o decrescente in ordine alfabetico  
* Nome dell'editore, crescente o decrescente in ordine alfabetico  
* Data, meno recente o più recente di pubblicazione  

Servono altre informazioni? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  

### <a name="available-and-required-apps"></a>App disponibili e necessarie
Le app vengono assegnate all'utente da parte dell'organizzazione ed etichettate come disponibile o richiesta. Il **le app installate** pagina Mostra le app a cui si dispone con la **tipo di assegnazione** colonna. 


* Le app disponibili: queste App sono selezionate per l'organizzazione e sono utili e appropriate per l'azienda o dell'istituto di istruzione. Sono facoltativi per installare e sono le uniche App sono disponibili nel portale aziendale per l'installazione. 

* Le applicazioni richieste: distribuiti dall'organizzazione potrebbe essere necessario App aziendali e dell'istituto di istruzione direttamente sul tuo dispositivo. Queste App vengono installate automaticamente per l'utente senza l'intervento. 

Le app sono inoltre disponibili in base al tipo di dispositivo. Ad esempio, se si usa il sito Web del portale aziendale in un dispositivo Windows, si avrà accesso alle app per Windows, ma non alle app per iOS.  

## <a name="view-app-details"></a>Visualizza i dettagli dell'app  
Selezionare un'app nel **le app** oppure **le app installate** pagina per visualizzarne i dettagli. È visualizzata **dettagli dell'App**, in cui è disponibile l'app e i requisiti. Se un'app non è già installata nel dispositivo, è possibile installarlo da questa pagina. 


   ![Sito Web screenshot del portale aziendale, pagina dei dettagli dell'App.](./media/intune-app-details-1907.png)  

## <a name="next-steps"></a>Passaggi successivi
Ulteriore assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
