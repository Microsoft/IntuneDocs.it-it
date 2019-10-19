---
title: Come reimpostare il passcode dal sito Web del portale aziendale | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2056d37b00f5e2ae7b36c6e1c02f20dc244eb290
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502120"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Come reimpostare il passcode del dispositivo dal sito Web del portale aziendale

Se il PIN o la password di un dispositivo vengono smarriti, è possibile usare il [sito Web Portale aziendale](https://portal.manage.microsoft.com) per reimpostarli. 

L'opzione Reimposta il codice potrebbe non essere visualizzata per un dispositivo registrato dall'azienda. In tal caso, contattare il supporto tecnico dell'azienda per reimpostarlo.  

La reimpostazione del codice non è disponibile per i dispositivi che eseguono Android 7,0 e versioni successive. Se si dimentica il codice di accesso in uno di questi dispositivi, è necessario reimpostarlo sulle impostazioni predefinite.  

## <a name="reset-your-passcode"></a>Reimpostare il passcode

1. Aprire il [sito Web Portale aziendale](https://portal.manage.microsoft.com) e selezionare il pulsante __Menu__ > __Dispositivi__.  

2. Selezionare il dispositivo per il quale è necessario reimpostare il passcode.  

    ![Screenshot della pagina Dispositivi, con due riquadri che illustrano i dispositivi non identificati, denominati in modo generico. Direttamente sotto i dispositivi è presente un banner di colore grigio che richiede all'utente di identificare il dispositivo in uso o aggiungerne uno nuovo.](./media/rename-reset-device-step2-1808.png) 

3. Selezionare **Reimposta passcode**. Se l'opzione per il passcode non viene visualizzata nella parte superiore della pagina, selezionare **Altro (...)**  > **Reimposta passcode**.   

   ![Pagina dei dettagli per un dispositivo selezionato nel sito Web Portale aziendale, con una serie di collegamenti nella parte superiore tra cui Rinomina, Rimuovi, Reimposta dispositivo, Reimposta passcode e Blocco remoto. ](./media/rename-reset-device-1808.png)   

    ![Screenshot dell'icona Altro, evidenziata con una freccia rossa.](./media/rename-reset-device-step3-more-1808.png)  

4. Quando richiesto, fare clic su **Disconnetti**. Quando viene richiesto, eseguire nuovamente l'accesso. Accedere nuovamente al sito Web Portale aziendale entro cinque minuti o il passcode del dispositivo non viene reimpostato.  

   > [!NOTE]
   > È necessario accedere nuovamente per confermare la propria identità. Questa operazione serve per evitare tentativi di reimpostare il passcode del dispositivo da parte di utenti malintenzionati.

   ![Screenshot di esempio che illustra una richiesta di disconnessione da Portale aziendale. I pulsanti per l'input dell'utente sono Disconnetti e Annulla.](./media/iwp-reset-passcode-popup-1808.png)

5. Viene visualizzato un messaggio che avvisa che il passcode del dispositivo esistente sta per essere rimosso. Fare clic su **Reimposta passcode** per confermare.  
    > [!WARNING]
    > Dopo aver reimpostato il passcode, chiunque abbia accesso fisico al dispositivo sarà in grado di accedere alla maggior parte delle informazioni personali e aziendali sul dispositivo. Se non si ha il dispositivo attualmente in proprio possesso, non reimpostare il passcode.  

   ![Screenshot di esempio che illustra il secondo messaggio di reimpostazione del passcode. Include collegamenti per altre informazioni sull'impostazione di un nuovo passcode nella documentazione e singoli pulsanti per reimpostare il passcode e annullare.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Se si esegue la reimpostazione del passcode per un dispositivo iOS, il passcode esistente verrà rimosso. Per i dispositivi Android o Windows, verrà generato un passcode temporaneo per sbloccare il dispositivo e impostare un nuovo passcode. 

   > [!NOTE]
   > È possibile trovare la password temporanea per i dispositivi Android e Windows in Portale aziendale, nella pagina dei dettagli del dispositivo. Vedere la sezione [Configurare un nuovo passcode](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode) per altre descrizioni di passcode specifiche per sistema operativo.  
   
7. Nel dispositivo passare a **Impostazioni** e modificare il passcode temporaneo. 

8. Viene visualizzato un flag in alto a destra del sito Web Portale aziendale. Fare clic per leggere la notifica e confermare che la password è stata reimpostata correttamente.  

## <a name="set-up-a-new-passcode"></a>Configurare un nuovo passcode  

In questa sezione viene descritto come reimpostare il passcode e il comportamento della password temporanea per ogni piattaforma del dispositivo.  

**Android**: rimuove il passcode esistente e crea un passcode temporaneo con lettere e numeri.

**iOS**: rimuove il passcode esistente senza crearne uno temporaneo. Se si usa Touch ID per aprire il dispositivo o effettuare acquisti, è necessario configurarlo di nuovo.  

**Windows 10 Mobile**: rimuove il passcode esistente e crea un passcode temporaneo con lettere e numeri. Se configurato, il riconoscimento facciale di Windows Hello funzionerà comunque con il dispositivo.

**Windows Phone 8.1**: rimuove il passcode esistente e crea un passcode temporaneo con numeri.  

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
