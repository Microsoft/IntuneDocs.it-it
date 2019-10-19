---
title: Bloccare il dispositivo dal portale aziendale | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: c81c13d5da8eac1616ab7274b484befaa5685511
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502170"
---
# <a name="remotely-lock-your-device-from-the-company-portal-website"></a>Bloccare il dispositivo in modalità remota dal sito Web del portale aziendale

Bloccare in remoto un dispositivo smarrito o rubato dal sito Web del portale aziendale. Se supportata dal dispositivo, questa impostazione blocca lo schermo del dispositivo, indipendentemente da dove quest'ultimo si trovi. Un utente dovrà immettere il passcode corretto per sbloccare il dispositivo e utilizzarlo.   

L'impostazione di blocco remoto funziona per:

* Android
* iOS
* macOS
* Windows 10
* Windows 10 Mobile (se per il dispositivo è già stato impostato un passcode)
* Windows Phone 8.1 (se per il dispositivo è già stato impostato un passcode)  

1. Nel [sito Web del portale aziendale](https://portal.manage.microsoft.com) selezionare il pulsante __Menu__ > __Dispositivi__.  

2. Selezionare il dispositivo da bloccare.  

    ![Screenshot della pagina Dispositivi, con 2 riquadri che illustrano i dispositivi non identificati, denominati in modo generico. Direttamente sotto i dispositivi è presente un banner di colore grigio che richiede all'utente di identificare il dispositivo in uso o aggiungerne uno nuovo.](./media/rename-reset-device-step2-1808.png) 

3. Selezionare **Blocco remoto**. Se l'opzione Blocca non è visibile nella parte superiore della pagina, selezionare **Altro (...)**  > **Blocco remoto**.  

   ![Pagina dei dettagli per un dispositivo selezionato nel sito Web del portale aziendale, con una serie di collegamenti nella parte superiore tra cui Rinomina, Rimuovi, Reimposta dispositivo, Reimposta passcode e Blocco remoto. ](./media/rename-reset-device-1808.png) 

    ![Vista ingrandita dell'icona Altro, evidenziata con una freccia rossa.](./media/rename-reset-device-step3-more-1808.png)    

4. Viene visualizzato un messaggio che avvisa che il dispositivo sta per essere bloccato. Toccare **Blocco remoto** per confermare.

Dopo la conferma, il portale aziendale tenta di bloccare il dispositivo. Durante questo periodo viene visualizzato un messaggio "Blocco remoto in sospeso". Quando il dispositivo è bloccato, lo stato diventa "Blocco remoto riuscito".  

Lo stato del blocco remoto viene visualizzato in tre posizioni:

* L'area delle notifiche del sito Web.
* La pagina **Dettagli** per il dispositivo.
* Il riquadro contenente il nome del dispositivo nella sezione **Dispositivi** della pagina.  

> [!Note]
> Se una notifica avvisa che il blocco remoto non è riuscito, attendere qualche minuto. Quindi, tentare di bloccare nuovamente il dispositivo. Lo stato diventa nuovamente "Blocco remoto in sospeso". Se il nuovo tentativo non funziona, contattare il supporto tecnico aziendale per assistenza.

Se il dispositivo viene ritrovato e si vuole rimuovere il blocco dopo aver usato Blocco remoto, immettere il passcode.  

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
