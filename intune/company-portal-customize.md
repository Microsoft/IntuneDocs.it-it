---
title: Personalizzare il portale aziendale
description: "Il portale aziendale di Intune consente agli utenti di eseguire attività comuni come registrare i dispositivi, installare app e trovare informazioni sul reparto IT."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e54f1a2ab0e62ab3ffcbf6fa1ae6f974c5f18717
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="customize-the-company-portal"></a>Personalizzare il portale aziendale

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Questo argomento descrive agli amministratori come possono personalizzare l'app Portale aziendale e il sito Web del portale aziendale di Intune.

Il Portale aziendale di Intune è il punto in cui gli utenti possono accedere ai dati aziendali ed eseguire attività comuni quali la registrazione dei dispositivi, l'installazione di app e la ricerca delle informazioni di assistenza del reparto IT.

Il Portale aziendale di Intune consente agli utenti l'accesso ai dati e alle app aziendali. Il Portale aziendale è disponibile in due forme:

-   **App Portale aziendale**: un'applicazione disponibile nei dispositivi gestiti con Intune. Altre informazioni sulle app Portale aziendale per [Android](/intune-user-help/using-your-android-device-with-intune), [iOS](/intune-user-help/using-your-iOS-or-macOS-device-with-intune) e [Windows](/intune-user-help/using-your-windows-device-with-intune).


- **Sito Web del portale aziendale**: sito Web che consente agli utenti finali di eseguire la maggior parte delle attività eseguibili tramite l'app Portale aziendale. L'URL del portale aziendale di Intune è [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com). Altre informazioni su questo sito Web nell'articolo [Uso del sito Web del Portale aziendale di Intune](/intune-user-help/using-the-intune-company-portal-website).

> [!TIP]
> Quando si personalizza il portale aziendale, le configurazioni vengono applicate sia al sito Web che alle app Portale aziendale.

Alcune attività che gli utenti possono eseguire nel Portale aziendale sono:

-   Registrare i dispositivi
-   Visualizzare lo stato dei dispositivi
-   Reimpostare il dispositivo
-   Reimpostare la password
-   Bloccare in remoto il dispositivo
-   Scaricare il software distribuito dall'organizzazione
-   Contattare il reparto IT per richiedere assistenza

## <a name="customize-company-portal-settings"></a>Personalizzare le impostazioni del portale aziendale
La personalizzazione del portale aziendale consente di offrire agli utenti finali un'esperienza familiare e utile. Accedere alla [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) come amministratore tenant o del servizio, scegliere **Amministrazione** &gt; **Portale aziendale** e configurare le impostazioni del Portale aziendale.

## <a name="company-contact-information-and-privacy-statement"></a>Informazioni di contatto e informativa sulla privacy della società
Il nome dell'azienda viene visualizzato come titolo del portale aziendale. I dettagli e le informazioni di contatto vengono visualizzati agli utenti nella schermata Contatta l'IT del portale aziendale. L'informativa sulla privacy viene visualizzata quando un utente fa clic sul relativo collegamento.

|Nome campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |Nome società|40|È il nome che verrà visualizzato come titolo del portale aziendale.|
    |Nome contatto del reparto IT|40|Questo nome viene visualizzato nella pagina **Contatta l'IT**.|
    |Numero di telefono del reparto IT|20|Questo numero di contatto viene visualizzato nella pagina **Contatta l'IT**.|
    |Indirizzo di posta elettronica del reparto IT|40|Questo indirizzo di contatto viene visualizzato nella pagina **Contatta l'IT**. È necessario immettere un indirizzo di posta elettronica valido nel formato **alias@domainname.com**.|
    |Informazioni aggiuntive|120|Visualizzato nella pagina **Contatta l'IT**|
    |URL dell'informativa sulla privacy dell'azienda|79|È possibile indicare l'informativa sulla privacy della propria azienda che verrà visualizzata quando gli utenti fanno clic sui collegamenti relativi alla privacy dal portale aziendale. Immettere un URL valido nel formato https://www.contoso.com.|

## <a name="support-contacts"></a>Contatti del supporto tecnico
Il sito di assistenza viene visualizzato agli utenti nel portale aziendale in modo da consentire l'accesso all'assistenza online.

|Nome del campo|Lunghezza massima|Altre informazioni|
    |----------|------------------------|----------------|
    |URL sito Web del supporto tecnico|150|Se si dispone di un sito Web di supporto che si desidera venga usato dagli utenti, è necessario specificare qui l'URL. Il formato dell'URL deve essere https://www.contoso.com. Se non si specifica un URL, non verrà visualizzato alcun valore nella pagina **Contatta l'IT** del portale aziendale.|
    |Nome sito Web|40|Questo è il nome descrittivo visualizzato per l'URL del sito Web del supporto tecnico. Se si specifica solo un URL del sito Web e nessun nome descrittivo, nella pagina **Contatta l'IT** del portale aziendale verrà visualizzato **Vai al sito Web IT**.|

## <a name="company-branding-customization"></a>Personalizzazione del branding aziendale
È possibile personalizzare il portale aziendale con logo, nome dell'azienda, colore del tema e sfondo.

|Nome del campo|Altre informazioni|
    |----------|----------------|
    |Colore del tema|Selezionare un colore del tema da applicare al portale aziendale.|
    |Includere il logo aziendale|Quando si attiva questa opzione, è possibile caricare il logo aziendale da visualizzare nel portale aziendale. È possibile caricare due loghi: uno che verrà visualizzato quando lo sfondo del portale è bianco e uno che verrà visualizzato quando lo sfondo del portale aziendale usa il colore del tema selezionato. Ogni logo deve essere un file con estensione jpg o png, avere una risoluzione massima di 400 x 100 pixel e una dimensione massima di 750 KB.|
    |Scegliere uno sfondo per l'app Portale aziendale di Windows 8|Questa impostazione influisce sullo sfondo solo per l'app Portale aziendale di Windows 8.|


Una volta salvate le modifiche, è possibile usare i collegamenti riportati in fondo alla pagina **Portale aziendale** della console di amministrazione per visualizzare il sito Web del portale aziendale. Questi collegamenti non possono essere modificati. Quando un utente esegue l'accesso, questi collegamenti visualizzano le sottoscrizioni nel portale aziendale.
