---
title: Configurare l'accesso del dispositivo iOS alle risorse aziendali | Microsoft Docs
description: Questo articolo descrive come rendere il dispositivo iOS gestito da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 92d1ca850d8bb542f0b7fe027ab7af8c12089ef8
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181756"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurare l'accesso del dispositivo iOS alle risorse aziendali  

Registrare un dispositivo iOS nell'app Portale aziendale Intune per ottenere accesso protetto alla posta elettronica, ai file e alle app dell'organizzazione.

Dopo la registrazione, il dispositivo diventa *gestito*. L'organizzazione può assegnare criteri e app al dispositivo tramite un provider di gestione di dispositivi mobili (MDM), ad esempio Intune.  

> [!NOTE]
> Microsoft non vende per alcun motivo a terze parti i dati raccolti dal servizio.  

Per mantenere l'accesso alle informazioni aziendali o dell'istituto di istruzione dal dispositivo, è necessario configurare il dispositivo in base alle impostazioni preferite dell'organizzazione. Questo articolo descrive come usare il Portale aziendale per registrare il dispositivo e mantenere i requisiti relativi alle impostazioni dell'organizzazione.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> Se si è provato ad accedere alla posta elettronica aziendale nell'app Posta ed è stata ricevuta una richiesta di impostare il dispositivo come gestito, questo è il posto giusto. Eseguire le istruzioni seguenti per accedere alla posta elettronica e ad altre risorse aziendali sul dispositivo iOS.  


## <a name="what-to-expect-from-the-company-portal-app"></a>Aspettative relative all'app Portale aziendale  

### <a name="security"></a>Sicurezza  
Durante la configurazione iniziale, l'app richiede l'autenticazione presso l'organizzazione. Quindi, comunica le eventuali impostazioni dispositivo che è necessario aggiornare. Ad esempio, le organizzazioni spesso definiscono il numero di caratteri minimo o massimo che la password deve soddisfare.

### <a name="protection"></a>Protezione  
Quando il dispositivo è registrato, l'app Portale aziendale continuerà ad assicurarsi che il dispositivo sia protetto. Ad esempio, se si installa un'app da un'origine non attendibile, si riceve un avviso dall'app e, talvolta, l'accesso ai dati aziendali viene revocato. Questi tipi di criteri sono comuni nelle organizzazioni e spesso richiedono la disinstallazione dell'app non attendibile prima di poter ottenere di nuovo l'accesso.  

### <a name="setting-notifications"></a>Impostazione delle notifiche  
Se dopo la registrazione l'organizzazione applica un nuovo requisito di sicurezza, ad esempio l'autenticazione a più fattori, l'app Portale aziendale invierà una notifica. L'utente potrà quindi modificare le impostazioni per continuare a lavorare dal proprio dispositivo.  

Per altre informazioni sulla registrazione, vedere [Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrare il dispositivo iOS  

Passare all'App Store per scaricare e installare l'[app Portale aziendale Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) nel dispositivo. Durante la registrazione è anche necessario mantenere una connessione Wi-Fi e avere accesso a Safari. 

La sospensione per un periodo più lungo di qualche minuto durante la registrazione può determinare la chiusura dell'app o la fine della configurazione. Se ciò accade, aprire l'app Portale aziendale e riprovare.  

1. Aprire l'app Portale aziendale e accedere con l'account aziendale o dell'istituto di istruzione.  

2. Quando viene chiesto di indicare se si vuole ricevere notifiche dal Portale aziendale, toccare **Consenti**. Il Portale aziendale usa le notifiche per avvisare se, ad esempio, è necessario aggiornare le impostazioni del dispositivo.  

3. Nella schermata di **configurazione dell'accesso** selezionare **Inizia**.   

    ![Screenshot di esempio del Portale aziendale, schermata di configurazione dell'accesso.](./media/ios-enrollment-checklist-1909.PNG)  

4. Viene visualizzata la schermata **Selezionare il tipo di dispositivo e di registrazione** e viene richiesto il tipo di dispositivo.  
    * Toccare **(Organizzazione) possiede il dispositivo** se il dispositivo è stato ricevuto dall'organizzazione. Per completare la configurazione, passare a [Proteggere l'intero dispositivo](#secure-entire-device) in questo articolo.  
    * Toccare **Sono il proprietario del dispositivo** se si usa un dispositivo personale portato da casa. Continuare quindi con il passaggio successivo.  

    Se questa schermata non viene visualizzata, passare a [Proteggere l'intero dispositivo](#secure-entire-device) per completare la configurazione.  
    
    ![Screenshot di esempio di Portale aziendale, schermata "Selezionare il tipo di dispositivo e di registrazione", opzioni del tipo di dispositivo.](./media/ios-device-type-1909.PNG)  


5. Scegliere la modalità di protezione dei dati nel dispositivo dopo la registrazione.  
    * Toccare **Proteggi l'intero dispositivo** per proteggere tutte le app e i dati nel dispositivo. Passare quindi a [Proteggere l'intero dispositivo](enroll-your-device-in-intune-ios.md#secure-entire-device) per completare la configurazione.
    * Toccare **Proteggi solo le app e i dati correlati al lavoro** per proteggere solo le app e i dati a cui si accede con l'account aziendale. Passare quindi a [Proteggere solo le app e i dati correlati al lavoro](enroll-your-device-in-intune-ios.md#secure-work-related-apps-and-data).  

    ![Screenshot di esempio di Portale aziendale, schermata "Selezionare il tipo di dispositivo e di registrazione", opzioni del tipo di registrazione.](./media/ios-enrollment-type-1909.PNG)  


### <a name="secure-entire-device"></a>Proteggere l'intero dispositivo  

1. Nella schermata **Gestione dei dispositivi e privacy dell'utente** prendere visione dell'elenco di informazioni relative al dispositivo la cui visualizzazione è concessa o non concessa all'organizzazione. Quindi toccare **Continua**.  


 > [!IMPORTANT]
> I passaggi e le schermate successivi variano a seconda della versione di iOS. Seguire i passaggi per la versione di iOS in uso. 

2. Safari apre il sito Web del Portale aziendale nel dispositivo. Quando viene chiesto di scaricare il profilo di configurazione, toccare **Consenti**. In un dispositivo che esegue  
    * iOS 12.2 e versioni successive: al termine del download toccare **Chiudi**. Continuare quindi con il passaggio 3.  
    * iOS 12.1 e versioni precedenti: al termine del download, si verrà automaticamente reindirizzati all'app Impostazioni. Procedere al passaggio 4.  
 
    Se si tocca accidentalmente **Ignora**, aggiornare la pagina. Verrà chiesto di aprire l'app Portale aziendale. Nell'app toccare **Ripetere il download**.

  > [!NOTE]
  > È necessario installare il profilo di gestione come descritto nei passaggi successivi entro 8 minuti dal download. In caso contrario, il profilo verrà rimosso e sarà necessario riavviare la registrazione.  

3. Quando viene chiesto di aprire il Portale aziendale, toccare **Apri**. Leggere le informazioni nella schermata **Come installare il profilo di gestione**.  

4. Passare all'app Impostazioni e toccare **Registra in < nome organizzazione >** o **Profilo scaricato**.  

    ![Screenshot di esempio dell'app Impostazioni, opzione Registra in organizzazione.](./media/enroll-in-organization-ios-1909.PNG)  

   Se nessuna delle due opzioni viene visualizzata, passare a **Generale** > **Gestione di profili e dispositivi**> **Profilo di gestione**. Se non è ancora visibile un profilo di gestione, potrebbe essere necessario scaricarlo di nuovo.  

5. Toccare **Installa**.  
    
6. Immettere la password del dispositivo. Quindi toccare **Installa**.    

7. La schermata successiva riporta un avviso di sistema standard sulla gestione dei dispositivi. Per continuare l'installazione, toccare **Installa**. Se viene chiesto di considerare attendibile la gestione remota, toccare **Considera attendibile**.  

8. Al termine dell'installazione, toccare **Fine**. Per verificare che il dispositivo sia stato installato, passare alle impostazioni **Gestione di profili e dispositivi**. Il profilo dovrebbe essere visualizzato in **Gestione dispositivi mobili**.   

    ![Screenshot di esempio dell'app Impostazioni, impostazioni Gestione di profili e dispositivi con il profilo di gestione.](./media/ios-12-cp-enroll-1904.PNG)  

9. Tornare all'app Portale aziendale. Il Portale aziendale avvierà la sincronizzazione e la configurazione del dispositivo. Il Portale aziendale può richiedere di aggiornare altre impostazioni del dispositivo. Se ciò avviene, toccare **Continua**.  

10. La configurazione sarà completa quando per tutti gli elementi dell'elenco viene visualizzato un segno di spunta verde. Toccare **Fine**.   

> [!Note]
> Se l'organizzazione monitora i limiti di voce e dati oppure mette a disposizione dell'utente un dispositivo di proprietà dell'azienda, potrebbe essere necessario completare altri passaggi. Se viene chiesto di installare l'app **Datalert**, vedere [Registrare il dispositivo nella gestione delle spese per telecomunicazioni](enroll-your-device-with-telecom-expense-management-ios.md). Se l'organizzazione partecipa al programma DEP (Device Enrollment Program) di Apple, vedere [come registrare un dispositivo di proprietà dell'azienda](enroll-your-device-dep-ios.md).  

### <a name="secure-work-related-apps-and-data"></a>Proteggere solo le app e i dati correlati al lavoro  
1. Viene visualizzata la schermata **Scarica Microsoft Authenticator** (se si dispone già di Authenticator questa schermata non verrà visualizzata, quindi procedere al passaggio 2).  
    1. Toccare **Scarica da App Store**.
    2. Quando si apre App Store, installare l'app. 
    3. Tornare al Portale aziendale e toccare **Continua**.    
    
   Dopo l'installazione di Microsoft Authenticator, non sarà necessario eseguire altre operazioni con l'app. Deve essere semplicemente presente nel dispositivo. 

   ![Screenshot di esempio di Portale aziendale, schermata "Scarica Microsoft Authenticator".](./media/download-ms-authenticator-1909.PNG)  

2. Nella schermata **Gestione dei dispositivi e privacy dell'utente** prendere visione dell'elenco di informazioni relative al dispositivo la cui visualizzazione è concessa o non concessa all'organizzazione. Quindi toccare **Continua**.  


 > [!IMPORTANT]
> I passaggi e le schermate successivi variano a seconda della versione di iOS. Seguire i passaggi per la versione di iOS in uso. 

3. Safari apre il sito Web del Portale aziendale nel dispositivo. Quando viene chiesto di scaricare il profilo di configurazione, toccare **Consenti**. In un dispositivo che esegue  
    * iOS 12.2 e versioni successive: al termine del download toccare **Chiudi**. Continuare quindi con il passaggio 4.  
    * iOS 12.1 e versioni precedenti: al termine del download, si verrà automaticamente reindirizzati all'app Impostazioni. Procedere al passaggio 5.  
 
    Se si tocca accidentalmente **Ignora**, aggiornare la pagina. Verrà chiesto di aprire l'app Portale aziendale. Nell'app è possibile toccare **Ripetere il download**.

  > [!NOTE]
  > È necessario installare il profilo di gestione come descritto nei passaggi successivi entro 8 minuti dal download. In caso contrario, il profilo verrà rimosso e sarà necessario riavviare la registrazione.  

4. Quando viene chiesto di aprire il Portale aziendale, toccare **Apri**. Leggere le informazioni nella schermata **Come installare il profilo di gestione**. 

5. Passare all'app Impostazioni e toccare **Registra in < nome organizzazione >** o **Profilo scaricato**.  

    ![Screenshot di esempio dell'app Impostazioni, opzione Registra in organizzazione.](./media/enroll-in-organization-ios-1909.PNG)  

   Se nessuna delle due opzioni viene visualizzata, passare a **Generale** > **Gestione di profili e dispositivi**> **Profilo di gestione**. Se non è ancora visibile un profilo di gestione, potrebbe essere necessario scaricarlo di nuovo.   


6. Nella schermata **Registrazione utente** toccare **Registra iPhone**.  

    ![Screenshot di esempio dell'app Impostazioni, schermata Registrazione utente, con evidenziato il pulsante Registra.](./media/user-enrollment-information-1909.PNG)  

7. Immettere la password del dispositivo. Quindi toccare **Installa**.  

8. Nella schermata **Accedi** immettere la password per l'ID Apple gestito. Nella maggior parte dei casi, queste credenziali saranno le stesse usate per accedere all'account aziendale o dell'Istituto di istruzione, a meno che l'organizzazione non abbia fornito un set di credenziali diverso. 
9. Toccare **Accedi**.  
10. Un messaggio di operazione completata verrà visualizzato sullo schermo brevemente dopo l'installazione del profilo. Per verificare che il dispositivo sia stato installato, passare alle impostazioni  **Gestione di profili e dispositivi**. Il profilo dovrebbe essere visualizzato in  **Gestione dispositivi mobili**.  

    ![Screenshot di esempio dell'app Impostazioni, impostazioni Gestione di profili e dispositivi con il profilo di gestione.](./media/ios-12-cp-enroll-1904.PNG)  

11. Tornare all'app Portale aziendale. Il Portale aziendale avvierà la sincronizzazione e la configurazione del dispositivo. Il Portale aziendale può richiedere di aggiornare altre impostazioni del dispositivo. Se ciò avviene, toccare **Continua**.    

12. La configurazione sarà completa quando per tutti gli elementi dell'elenco viene visualizzato un segno di spunta verde. Toccare  **Fine**.  

## <a name="it-administrator-support"></a>Supporto per amministratori IT  
Gli amministratori IT che riscontrano problemi durante la registrazione dei dispositivi possono vedere [Risoluzione dei problemi di registrazione dei dispositivi iOS in Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Questo articolo elenca gli errori comuni, le cause e le procedure per risolverli.  

## <a name="next-steps"></a>Passaggi successivi  
Trovare app utili per le attività lavorative o scolastiche. Informazioni su [come vengono rese disponibili le app](use-managed-apps-on-your-device-ios.md) tramite il Portale aziendale.  

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
