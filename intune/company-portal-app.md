---
title: Come configurare l'app Portale aziendale
titleSuffix: Microsoft Intune
description: Informazioni su come applicare specifiche personalizzazioni aziendali all'app Portale aziendale.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2defc433ef39562750c4579f302a9c5367c6464a
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828245"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Come configurare l'app Portale aziendale di Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Il portale aziendale di Microsoft Intune è il punto in cui gli utenti possono accedere ai dati aziendali ed eseguire attività comuni quali la registrazione dei dispositivi, l'installazione di app e la ricerca delle informazioni di assistenza del reparto IT.        

> [!Tip]        
> Quando si personalizza il portale aziendale, le configurazioni vengono applicate sia al sito Web che alle app Portale aziendale.       

La personalizzazione del portale aziendale consente di offrire agli utenti finali un'esperienza familiare e utile. A tale scopo, dal carico di lavoro **App client** scegliere **Installazione** > **Personalizzazione del portale aziendale** e configurare le impostazioni richieste.  

> [!Note]       
> Se si usa Azure per enti pubblici, l'utente finale riceve i log delle app per prendere decisioni in merito alla condivisione quando avvia il processo per visualizzare la Guida per un problema. Se tuttavia non si usa Azure per enti pubblici, il portale aziendale per Windows 10 invierà i log delle app direttamente a Microsoft quando l'utente avvia il processo per visualizzare la Guida per un problema. Inviando i log delle app a Microsoft sarà più semplice risolvere i problemi. 

## <a name="company-information-and-privacy-statement"></a>Informazioni e informativa sulla privacy della società        
Il nome dell'azienda viene visualizzato come titolo del portale aziendale. L'informativa sulla privacy viene visualizzata quando un utente fa clic sul relativo collegamento.

I campi contrassegnati con un asterisco (*) sono obbligatori.       


| Nome del campo | Lunghezza massima | Altre informazioni |
|---|---|---|
|**Nome società**| 40 | Questo nome viene visualizzato come titolo del portale aziendale e appare come testo nell'intera esperienza utente Intune. |
| **URL dell'informativa sulla privacy** |     79     | È possibile indicare l'informativa sulla privacy della propria azienda che verrà visualizzata quando gli utenti fanno clic sui collegamenti relativi alla privacy dal portale aziendale. Immettere un URL valido nel formato `<https://www.contoso.com>`. |

## <a name="support-information"></a>Informazioni di supporto      
Immettere le informazioni di supporto della società, in modo da garantire al dipendente un contatto per le domande relative a Intune.       

|Nome del campo|Lunghezza massima|Altre informazioni|
|---|---|---|
|**Nome di contatto** | 40 | Questo nome viene visualizzato nella pagina **Contatta l'IT**. |
|**Numero di telefono** | 20 | Questo numero di contatto viene visualizzato nella pagina **Contatta l'IT** che consente ai dipendenti di contattare l'organizzazione per ottenere supporto. |
|**Indirizzo di posta elettronica**| 40 | Questo indirizzo di contatto viene visualizzato nella pagina **Contatta l'IT**. È necessario immettere un indirizzo di posta elettronica valido nel formato `alias@domainname.com`. |
|**Nome del sito Web**| 40 | Questo è il nome descrittivo visualizzato per l'URL del sito Web del supporto tecnico. Se si specifica solo un URL del sito Web e nessun nome descrittivo, nella pagina **Contatta l'IT** del portale aziendale verrà visualizzato Vai al sito Web IT. |
|**URL del sito Web**| 150 | Se si dispone di un sito Web di supporto che si desidera venga usato dagli utenti, è necessario specificare qui l'URL. Il formato dell'URL deve essere `https://www.contoso.com`. Se non si specifica un URL, non verrà visualizzato alcun valore nella pagina **Contatta l'IT** del portale aziendale. |
| **Informazioni aggiuntive**| 120 | Visualizzato nella pagina **Contatta l'IT** |


## <a name="company-branding-customization"></a>Personalizzazione del branding aziendale       
È possibile personalizzare il portale aziendale con logo, nome dell'azienda, colore del tema e sfondo.     

### <a name="theme-color"></a>Colore del tema
È possibile applicare un colore del tema al portale aziendale. Selezionare un colore standard o immettere un codice esadecimale a sei cifre corrispondente a un colore personalizzato.

|Nome del campo|Altre informazioni|
|---|---|
|**Tipo di colore**| Selezionare un colore del tema da applicare al portale aziendale. È possibile scegliere un colore standard o immettere un codice esadecimale specifico. |
|**Scegliere un colore** o **Codice colore in formato esadecimale**| Selezionare un colore del tema da applicare al portale aziendale. È possibile scegliere un colore standard o immettere un codice esadecimale specifico. Queste opzioni sono disponibili in base all'opzione **Tipo di colore** selezionata.  |

### <a name="company-logo"></a>Logo società
Caricare il logo della società per renderlo visibile nell'intera esperienza utente di Intune.

|Nome del campo|Altre informazioni|
|---|---|
|**Mostra logo della società**|Quando si attiva questa opzione, è possibile caricare il logo aziendale da visualizzare nel portale aziendale. È possibile caricare due loghi: uno che verrà visualizzato quando lo sfondo del portale è bianco e uno che verrà visualizzato quando lo sfondo del portale aziendale usa il colore del tema selezionato. |
|**Caricare un logo da usare su sfondi con colore del tema**| Questa opzione è disponibile se si è scelto di visualizzare il logo della società. Il logo deve essere un file con estensione jpg o png e avere una risoluzione massima di 400 x 400 pixel e una dimensione massima di 750 kB. |
|**Caricare il logo da usare su sfondi chiari**| Questa opzione è disponibile se si è scelto di visualizzare il logo della società. Il logo deve essere un file con estensione jpg o png e avere una risoluzione massima di 400 x 400 pixel e una dimensione massima di 750 kB. |
|**Mostra il nome della società accanto al logo**| Selezionare questa opzione per visualizzare il nome della società immesso accanto al logo caricato. |

Dopo aver salvato le modifiche è possibile scegliere **Visualizzare l'anteprima delle impostazioni nel portale Web di Intune** nella parte superiore del pannello per visualizzare come appaiono le configurazioni.
