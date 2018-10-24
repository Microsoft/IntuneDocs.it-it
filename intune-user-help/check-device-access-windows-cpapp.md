---
title: Controllare l'accesso del dispositivo | Microsoft Docs
description: Controllare l'accesso del dispositivo per sapere se il dispositivo soddisfa i requisiti e riesce ad accedere alle risorse aziendali o dell'istituto di istruzione.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
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
ms.openlocfilehash: 162891253c63e785e07ae8c46996f40f19472317
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828836"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>Controllare l'accesso dall'app Portale aziendale per Windows

Verificare che il dispositivo abbia accesso alle risorse aziendali o dell'istituto di istruzione. 

Le organizzazioni impongono requisiti, ad esempio crittografia e limiti delle password, per assicurarsi che solo dispositivi sicuri e attendibili accedano ai dati. I dispositivi gestiti devono soddisfare e mantenere questi requisiti per accedere alle risorse dell'organizzazione.

L'azione **Verifica l'accesso** valuta le impostazioni del dispositivo e lo stato di accesso. La pagina **Dettagli dispositivo** elenca le impostazioni da modificare per ottenere di nuovo l'accesso. 

Completare i passaggi descritti in questo articolo per controllare l'accesso dall'app Portale aziendale per Windows.  

## <a name="check-access-from-device-details-page"></a>Controllare l'accesso dalla pagina Dettagli dispositivo  
1. Aprire l'app Portale aziendale per Windows e passare a **Dispositivi personali**.  

    ![Screenshot di esempio dell'app Portale aziendale per Windows, home page, con la sezione Dispositivi personali evidenziata.](./media/1809_CheckAccess_Context_Select_Device.png)  
2. Selezionare un dispositivo.  
3. Nella pagina **Dettagli dispositivo** selezionare **Verifica l'accesso**. L'app sincronizza il dispositivo con i requisiti correnti dell'organizzazione e verifica che il dispositivo li soddisfi. Questo controllo può richiedere alcuni minuti.  

    ![Screenshot di esempio dell'app Portale aziendale per Windows, pagina Dettagli dispositivo, con il pulsante Verifica l'accesso evidenziato.](./media/1809_CheckAccess_Checking_Status.png) 

4. Esaminare l'aggiornamento dello stato. Indicherà che il dispositivo **può accedere alle risorse aziendali** o **non può accedere alle risorse aziendali**.  

   ![Screenshot di esempio dell'app Portale aziendale per Windows, pagina Dettagli dispositivo, con la sezione Stato evidenziata.](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. Se il dispositivo non può accedere alle risorse, passare all'avviso nella parte superiore della pagina. Fare clic su **Più informazioni** per espandere i dettagli. Fare clic su **Meno informazioni** per comprimerli.  

    ![Screenshot di esempio dell'app Portale aziendale per Windows, pagina Dettagli dispositivo, con l'avviso nella parte superiore della pagina evidenziato.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Se applicabile, il messaggio mostra altri collegamenti e azioni di correzione. Selezionare una o più di queste opzioni per avviare subito la risoluzione dei problemi. Le azioni di risoluzione, sincronizzazione e contatto, descritte sotto, sono visibili solo quando si usa il portale aziendale nel dispositivo interessato.  

     * **Risoluzione del problema** apre un articolo della Guida pertinente, se disponibile.  
     * **Risolvi** reindirizza all'impostazione nel dispositivo.  
     * **Sincronizza** valuta il dispositivo per verificare che soddisfi i requisiti aziendali.  
     * **Contatta l'IT** reindirizza alle informazioni sul contatto del team IT.   
 
6. Dopo aver aggiornato le impostazioni, fare clic su **Verifica l'accesso** per confermare lo stato del dispositivo.  

    ![Screenshot di esempio dell'app Portale aziendale per Windows, pagina Dettagli dispositivo, con la sezione Stato evidenziata.](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>Controllare l'accesso dal menu di scelta rapida del dispositivo  
1. Aprire l'app Portale aziendale per Windows e passare a **Dispositivi personali**.  

    ![Screenshot di esempio dell'app Portale aziendale per Windows, home page, con la sezione Dispositivi personali evidenziata.](./media/1809_CheckAccess_Context_Select_Device.png)  

2. Fare clic con il pulsante destro del mouse o tenere premuto il tasto sinistro su un dispositivo per aprire il relativo [menu di scelta rapida](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus).  

    ![Screenshot di esempio dell'app Portale aziendale per Windows con home page. Il menu di scelta rapida è visibile nella sezione **Dispositivi personali** della pagina e contiene le azioni "Rinomina", "Rimuovi" e "Verifica l'accesso".](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. Selezionare **Verifica l'accesso**. L'app sincronizza il dispositivo con i requisiti correnti dell'organizzazione e verifica che il dispositivo li soddisfi. Questo controllo può richiedere alcuni minuti.  
 
4. Sotto il dispositivo viene visualizzato un messaggio che informa che il dispositivo **può accedere alle risorse aziendali** o **non può accedere alle risorse aziendali**. 

    ![Screenshot di esempio dell'app Portale aziendale per Windows, pagina Dettagli dispositivo, con la sezione Stato evidenziata.](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. Se il dispositivo non può accedere alle risorse, selezionare il dispositivo.  
6. Nella pagina **Dettagli dispositivo** passare all'avviso nella parte superiore. Fare clic su **Più informazioni** per espandere i dettagli. Fare clic su **Meno informazioni** per comprimerli.  

    ![Screenshot di esempio dell'app Portale aziendale per Windows, pagina Dettagli dispositivo, con l'avviso nella parte superiore della pagina evidenziato.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Se applicabile, il messaggio mostra altri collegamenti e azioni di correzione. Selezionare una o più di queste opzioni per avviare subito la risoluzione dei problemi. Le azioni di risoluzione, sincronizzazione e contatto, descritte sotto, sono visibili solo quando si usa il portale aziendale nel dispositivo interessato.  

     * **Risoluzione del problema** apre un articolo della Guida pertinente, se disponibile.  
     * **Risolvi** reindirizza all'impostazione nel dispositivo.  
     * **Sincronizza** valuta il dispositivo per verificare che soddisfi i requisiti aziendali.  
     * **Contatta l'IT** reindirizza alle informazioni sul contatto del team IT.    

7. Dopo aver aggiornato le impostazioni, fare clic su **Verifica l'accesso** nella parte inferiore della pagina.  

    ![Screenshot di esempio dell'app Portale aziendale per Windows, pagina Dettagli dispositivo, con l'azione Verifica l'accesso evidenziata.](./media/1809_CheckAccess_Device_details_button.png) 


Ulteriore assistenza? Per trovare le informazioni sul contatto del supporto tecnico dell'azienda, vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
