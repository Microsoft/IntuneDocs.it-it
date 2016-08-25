---
title: Personalizzare il portale aziendale | Microsoft Intune
description: Illustra come personalizzare il portale aziendale per la sottoscrizione di Intune
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: b7288cff2e589faac32b9d2a80655079d9490590


---


# Personalizzare il portale aziendale
Il [!INCLUDE[wit_iwportal_1](../includes/wit_iwportal_1_md.md)] è il punto in cui gli utenti possono accedere ai dati aziendali ed eseguire attività comuni quali la registrazione dei dispositivi, l'installazione di app e la ricerca delle informazioni di assistenza del reparto IT.

> [!TIP]
> Quando si personalizza il portale aziendale, le configurazioni vengono applicate sia al sito Web che alle app Portale aziendale.

La personalizzazione del portale aziendale consente di offrire agli utenti finali un'esperienza familiare e utile. A tale scopo, accedere alla [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) come amministratore tenant o del servizio, scegliere **Amministrazione** &gt; **Portale aziendale** e configurare le impostazioni del Portale aziendale.

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## Informazioni di contatto e informativa sulla privacy della società
Il nome dell'azienda viene visualizzato come titolo del portale aziendale. I dettagli e le informazioni di contatto vengono visualizzati agli utenti nella schermata Contatta l'IT del portale aziendale. L'informativa sulla privacy viene visualizzata quando un utente fa clic sul relativo collegamento.

|Nome del campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |Nome società|40|È il nome che verrà visualizzato come titolo del portale aziendale.|
    |Nome contatto del reparto IT|40|Questo nome viene visualizzato nella pagina **Contatta l'IT**.|
    |Numero di telefono del reparto IT|20|Questo numero di contatto viene visualizzato nella pagina **Contatta l'IT**.|
    |Indirizzo di posta elettronica del reparto IT|40|Questo indirizzo di contatto viene visualizzato nella pagina **Contatta l'IT**. È necessario immettere un indirizzo di posta elettronica valido nel formato **alias@nomedominio.com**.|
    |Informazioni aggiuntive|120|Visualizzato nella pagina **Contatta l'IT**|
    |URL dell'informativa sulla privacy dell'azienda|79|È possibile indicare l'informativa sulla privacy della propria azienda che verrà visualizzata quando gli utenti fanno clic sui collegamenti relativi alla privacy dal portale aziendale. Immettere un URL valido nel formato https://www.contoso.com.|

## Contatti del supporto tecnico
Il sito di assistenza viene visualizzato agli utenti nel portale aziendale in modo da consentire l'accesso all'assistenza online.

|Nome del campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |URL sito Web del supporto tecnico|150|Se si dispone di un sito Web di supporto che si desidera venga usato dagli utenti, è necessario specificare qui l'URL. Il formato dell'URL deve essere https://www.contoso.com. Se non si specifica un URL, non verrà visualizzato alcun valore nella pagina **Contatta l'IT** del portale aziendale.|
    |Nome sito Web|40|Questo è il nome descrittivo visualizzato per l'URL del sito Web del supporto tecnico. Se si specifica solo un URL del sito Web e nessun nome descrittivo, nella pagina **Contatta l'IT** del portale aziendale verrà visualizzato **Vai al sito Web IT**.|

## Personalizzazione del branding aziendale
È possibile personalizzare il portale aziendale con logo, nome dell'azienda, colore del tema e sfondo.

|Nome del campo|Altre informazioni|
    |----------|----------------|
    |Colore del tema|Selezionare un colore del tema da applicare al portale aziendale.|
    |Includere il logo aziendale|Quando si attiva questa opzione, è possibile caricare il logo aziendale da visualizzare nel portale aziendale. È possibile caricare due loghi: uno che verrà visualizzato quando lo sfondo del portale è bianco e uno che verrà visualizzato quando lo sfondo del portale aziendale usa il colore del tema selezionato. Ogni logo deve essere un file con estensione jpg o png, avere una risoluzione massima di 400 x 100 pixel e una dimensione massima di 750 KB.|
    |Scegliere uno sfondo per l'app Portale aziendale di [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]|Questa impostazione influisce sullo sfondo solo per l'app Portale aziendale di [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)].|


Una volta salvate le modifiche, è possibile usare i collegamenti riportati in fondo alla pagina **Portale aziendale** della console di amministrazione per visualizzare il sito Web del portale aziendale. Questi collegamenti non possono essere modificati. Quando un utente esegue l'accesso, questi collegamenti visualizzano le sottoscrizioni nel portale aziendale.

### Passaggi successivi
A questo punto, il passaggio 7 della *Guida introduttiva a Intune* è stato completato.
>[!div class="step-by-step"]

>[&larr;**Creare criteri e applicazioni**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)       [**Registrare dispositivi** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  



<!--HONumber=Jul16_HO4-->


