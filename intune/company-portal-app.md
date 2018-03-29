---
title: Come configurare l'app Portale aziendale
titleSuffix: Microsoft Intune
description: Informazioni su come applicare specifiche personalizzazioni aziendali all'app Portale aziendale.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 186f6c1749d94a995ad145ca535bb59c6f02875c
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Come configurare l'app Portale aziendale di Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il portale aziendale di Microsoft Intune è il punto in cui gli utenti possono accedere ai dati aziendali ed eseguire attività comuni quali la registrazione dei dispositivi, l'installazione di app e la ricerca delle informazioni di assistenza del reparto IT.        

> [!Tip]        
> Quando si personalizza il portale aziendale, le configurazioni vengono applicate sia al sito Web che alle app Portale aziendale.       

La personalizzazione del portale aziendale consente di offrire agli utenti finali un'esperienza familiare e utile. A tale scopo, dal carico di lavoro **App per dispositivi mobili** scegliere **Installazione** > **Personalizzazione del portale aziendale** e quindi configurare le impostazioni richieste.      

## <a name="company-contact-information-and-privacy-statement"></a>Informazioni di contatto e informativa sulla privacy della società        
Il nome dell'azienda viene visualizzato come titolo del portale aziendale. I dettagli e le informazioni di contatto vengono visualizzati agli utenti nella schermata **Contatta l'IT** del portale aziendale. L'informativa sulla privacy viene visualizzata quando un utente fa clic sul relativo collegamento.        


|Nome del campo|Lunghezza massima|Altre informazioni|        
|-|-|-|     
|**Nome società**|40|È il nome che verrà visualizzato come titolo del portale aziendale.|        
|**Nome contatto del reparto IT**|40|Questo nome viene visualizzato nella pagina **Contatta l'IT**.|      
|**Numero di telefono del reparto IT**|20|Questo numero di contatto viene visualizzato nella pagina **Contatta l'IT**.|        
|**Indirizzo di posta elettronica del reparto IT**|40|Questo indirizzo di contatto viene visualizzato nella pagina **Contatta l'IT**. È necessario immettere un indirizzo di posta elettronica valido nel formato **alias@domainname.com**.|     
|**Informazioni aggiuntive**|120|Visualizzato nella pagina **Contatta l'IT**|      
|**URL dell'informativa sulla privacy dell'azienda**|79|È possibile indicare l'informativa sulla privacy della propria azienda che verrà visualizzata quando gli utenti fanno clic sui collegamenti relativi alla privacy dal portale aziendale. Immettere un URL valido nel formato **https://www.contoso.com**.|        

## <a name="support-contacts"></a>Contatti del supporto tecnico     
Il sito di assistenza viene visualizzato agli utenti nel portale aziendale in modo da consentire l'accesso all'assistenza online.        



|Nome del campo|Lunghezza massima|Altre informazioni|        
|-|-|-|     
|**URL sito Web del supporto tecnico**|150|Se si dispone di un sito Web di supporto che si desidera venga usato dagli utenti, è necessario specificare qui l'URL. Il formato dell'URL deve essere **https://www.contoso.com**. Se non si specifica un URL, non verrà visualizzato alcun valore nella pagina **Contatta l'IT** del portale aziendale.|        
|**Nome sito Web del supporto tecnico**|40|Questo è il nome descrittivo visualizzato per l'URL del sito Web del supporto tecnico. Se si specifica solo un URL del sito Web e nessun nome descrittivo, nella pagina **Contatta l'IT** del portale aziendale verrà visualizzato Vai al sito Web IT.       

## <a name="company-branding-customization"></a>Personalizzazione del branding aziendale       
È possibile personalizzare il portale aziendale con logo, nome dell'azienda, colore del tema e sfondo.     



|Nome del campo|Altre informazioni|       
|-|-|       
|**Colore del tema**|Selezionare un colore del tema da applicare al portale aziendale.|      
|**Mostra logo della società**|Quando si attiva questa opzione, è possibile caricare il logo aziendale da visualizzare nel portale aziendale. È possibile caricare due loghi: uno che verrà visualizzato quando lo sfondo del portale è bianco e uno che verrà visualizzato quando lo sfondo del portale aziendale usa il colore del tema selezionato. Ogni logo deve essere un file con estensione jpg o png, avere una risoluzione massima di 400 x 100 pixel e una dimensione massima di 750 KB.<br>È anche possibile visualizzare il nome della società immesso accanto al logo caricato.|      

Dopo aver salvato le modifiche, è possibile scegliere **Visualizzare l'anteprima delle impostazioni nel portale Web di Intune** per visualizzare come appaiono le configurazioni.
