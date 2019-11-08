---
title: Installare Mobile Threat Defense nel dispositivo mobile
description: Informazioni su come installare Mobile Threat Defense nel dispositivo mobile.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f395a9cedc72a8184cfe3e29d6fcd3117a1473d
ms.sourcegitcommit: 259462591835f3607392aa6b179882dbac830a89
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72980358"
---
# <a name="install-mobile-threat-defense"></a>Installare Mobile Threat Defense   

Come parte dei requisiti di sicurezza dell'organizzazione, potrebbe essere necessario installare un'app del fornitore mobile Threat Defense (MTD). Questo tipo di app rileva e avvisa l'utente delle minacce sul dispositivo, ad esempio app sospette, reti o vulnerabilità del sistema operativo.  

Se non si ha l'app MTD necessaria, verrà impedito l'accesso alle app protette con l'account aziendale o dell'Istituto di istruzione. In questo articolo si apprenderà [come installare un'app MTD](set-up-mobile-threat-defense.md#install-app) per sbloccarla.  

È disponibile un'ampia gamma di app del fornitore MTD per l'installazione. l'organizzazione consentirà di conoscerne l'uso. 


## <a name="information-your-organization-can-see"></a>Informazioni che possono essere visualizzate nell'organizzazione   

L'organizzazione non può visualizzare i dati, ad esempio testi, messaggi di posta elettronica e immagini, nelle app personali. L'app MTD segnala le informazioni sulle app, ad esempio il nome e la versione, per l'organizzazione. Le informazioni effettive restituite variano a seconda del fornitore di MTD usato dall'azienda. L'organizzazione potrebbe vedere:   

* Nome app  
* ID dell'app: nome univoco che identifica l'app in Google Play.  
* Numero di versione e versione breve dell'app: numeri di versione specifici di un'app.  
* Bundle e dimensioni dinamiche dell'app: quantità di spazio usato dall'app nel dispositivo. 


## <a name="install-app"></a>Installare l'app    
Quando si accede a un'app protetta, verrà automaticamente richiesto di installare un'app MTD. Per completare l'installazione, seguire i passaggi sullo schermo. Per ulteriori informazioni, attenersi alla procedura descritta in questa sezione.  
 
Potrebbe anche essere richiesto di registrare il dispositivo. La registrazione è necessaria per confermare la propria identità e connettere l'account aziendale o dell'Istituto di istruzione al dispositivo. Se non si è registrati, verrà automaticamente eseguita la procedura guidata prima di installare l'app MTD. Quando si arriva alla schermata **Get Access** , è possibile avviare la procedura di installazione.  

Per altre informazioni sulla registrazione dei dispositivi, vedere [registrare il dispositivo personale nella rete dell'organizzazione](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network).  

### <a name="ios-setup"></a>installazione di iOS  

1. Nella schermata **Get Access** seguire le istruzioni per installare l'app MTD richiesta dall'organizzazione.   
2. Tornare alla schermata **Get Access** e selezionare **Apri**.  
3. L'app MTD chiede l'autorizzazione per aprire Microsoft Authenticator. Selezionare **Open** (Apri). 
4. Selezionare l'account aziendale da usare per l'accesso. 
5. Attendere mentre l'app MTD analizza il dispositivo per individuare le minacce alla sicurezza. 
6. Tornare all'app School o work a cui si è tentato di accedere in origine. A questo punto, l'organizzazione potrebbe richiedere di configurare altri requisiti di sicurezza delle app, ad esempio la creazione di un PIN.   
7. A questo punto dovrebbe essere possibile accedere all'app. Se si è ancora bloccati:  
    * Nella schermata **Get Access** selezionare **Controlla**di più.  
    * Passare all'app MTD e verificare la presenza di minacce esistenti. Completare i passaggi consigliati per risolvere la minaccia e ottenere nuovamente l'accesso.    

### <a name="android-setup"></a>Installazione per Android 

1. Nella schermata **Get Access** seguire le istruzioni per installare l'app MTD richiesta dall'organizzazione.  
2. Tornare alla schermata **Get Access** e selezionare **Apri**.  
3. L'app MTD richiede l'autorizzazione per accedere ad alcune aree del dispositivo, se necessario. Affinché questa applicazione funzioni correttamente, è necessario **consentire** l'accesso ai contatti. Le autorizzazioni richieste variano tra i fornitori di MTD.  
4. Selezionare l'account aziendale da usare per l'accesso.  
5. Attendere mentre l'app MTD analizza il dispositivo per individuare le minacce alla sicurezza.  
6. Tornare all'app School o work a cui si è tentato di accedere in origine. A questo punto, l'organizzazione potrebbe richiedere di configurare altri requisiti di sicurezza delle app, ad esempio la creazione di un PIN.  
7. A questo punto dovrebbe essere possibile accedere all'app. Se si è ancora bloccati:  
    * Nella schermata **Get Access** selezionare **Controlla**di più.  
    * Passare all'app MTD e verificare la presenza di minacce esistenti. Completare i passaggi consigliati per risolvere la minaccia e ottenere nuovamente l'accesso.  

### <a name="installation-failed"></a>L'installazione non è riuscita  

Se l'installazione non riesce, contattare il personale di supporto IT. Visitare il [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per trovare le informazioni di contatto dell'organizzazione.  

È anche possibile inviare i log dell'app al personale del supporto IT per fornire loro un contesto più approfondito sull'installazione.  
* Utenti Android: [caricare e inviare tramite posta elettronica i log](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android) da portale aziendale.   

* utenti dispositivo iOS: [recuperare e inviare i log](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs) da Microsoft Edge per iOS.  

## <a name="resolve-a-threat"></a>Risolvere una minaccia  
Se una minaccia supera il livello di minaccia definito dall'organizzazione, l'organizzazione effettuerà una delle operazioni seguenti:  
   
* Blocca l'accesso: impedisce di usare le app protette dell'organizzazione durante l'accesso all'account aziendale o dell'Istituto di istruzione.  
* Cancellazione dati: Elimina i dati aziendali o dell'Istituto di istruzione da una o più app protette dell'organizzazione.  

Per risolvere una minaccia e ottenere nuovamente l'accesso, aprire l'app MTD nel dispositivo. Leggere le informazioni fornite per apprendere come la minaccia potrebbe influire sul dispositivo e come risolverlo. Dopo aver seguito i passaggi per risolvere la minaccia, tornare all'app MTD e avviare una nuova analisi. Potrebbero essere necessari alcuni minuti per riottenere l'accesso all'organizzazione.  

## <a name="next-steps"></a>Passaggi successivi  

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).

