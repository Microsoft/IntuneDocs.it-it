---
title: Configurare l'accesso del dispositivo iOS alle risorse aziendali | Microsoft Docs
description: Questo articolo descrive come rendere il dispositivo iOS gestito da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0c7ac239a67a51ba7165771206883f3c46f5f55
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292425"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurare l'accesso del dispositivo iOS alle risorse aziendali  

Registrare un dispositivo iOS nell'app Portale aziendale Intune per ottenere accesso protetto alla posta elettronica, ai file e alle app dell'organizzazione.

Dopo aver registrato il dispositivo, diventa *gestito*. L'organizzazione è possibile assegnare i criteri e le app al dispositivo tramite un provider di gestione (MDM) dei dispositivi mobili, ad esempio Intune.  

Per mantenere l'accesso alle informazioni aziendali o dell'istituto di istruzione tramite il dispositivo, è necessario configurare nel dispositivo le impostazioni preferite dell'organizzazione. Questo articolo descrive come usare il portale aziendale per eseguire la registrazione dispositivo e gestire i requisiti di impostazione di un'organizzazione. 

> [!NOTE]
> Se si è provato ad accedere alla posta elettronica aziendale nell'app Posta ed è stata ricevuta una richiesta di impostare il dispositivo come gestito, questo è il posto giusto. Eseguire le istruzioni seguenti per accedere alla posta elettronica e ad altre risorse aziendali sul dispositivo iOS.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Aspettative relative all'app Portale aziendale  

### <a name="security"></a>Sicurezza  
Durante la configurazione iniziale, l'app richiede l'autenticazione presso l'organizzazione. Quindi, comunica le eventuali impostazioni dispositivo che è necessario aggiornare. Ad esempio, le organizzazioni spesso definiscono il numero di caratteri minimo o massimo che la password deve soddisfare.     

### <a name="protection"></a>Protezione  
Quando il dispositivo è registrato, l'app Portale aziendale continuerà ad assicurarsi che il dispositivo sia protetto. Ad esempio, se si installa un'app da un'origine non attendibile, si riceve un avviso dall'app e, talvolta, l'accesso ai dati aziendali viene revocato. Questo tipo di criterio è comune nelle organizzazioni e spesso è necessario disinstallare l'app non attendibile prima che si possa ottenere nuovamente l'accesso.  

### <a name="setting-notifications"></a>Impostazione delle notifiche  
Se dopo la registrazione l'organizzazione applica un nuovo requisito di sicurezza, ad esempio l'autenticazione a più fattori, l'app Portale aziendale invierà una notifica. L'utente potrà quindi modificare le impostazioni per continuare a lavorare dal proprio dispositivo.  

Per altre informazioni sulla registrazione, vedere [Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrare il dispositivo iOS  

Passare all'App store per scaricare e installare il [app portale aziendale Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) nel dispositivo. È anche necessario mantenere una connessione Wi-Fi e avere accesso al browser Safari durante la registrazione. 

Sospende l'esecuzione per più di pochi minuti durante la registrazione potrebbe causare l'app chiudere o uscire dall'installazione. In questo caso, aprire l'app portale aziendale e riprovare.  

1. Aprire l'app Portale aziendale e accedere con l'account aziendale o dell'istituto di istruzione. 

    ![Screenshot di esempio dell'app portale aziendale, di accesso.](./media/ios-01-cp-enroll-1903.PNG)  

2. Quando viene richiesto di ricevere le notifiche di portale aziendale, toccare **Consenti.** Portale aziendale Usa le notifiche da ricevere un avviso se, ad esempio, le impostazioni del dispositivo devono essere aggiornati. 

    ![Screenshot di esempio della home page di portale aziendale, prompt dei comandi "Notifiche".](./media/ios-04-cp-enroll-1903.PNG)  

3. Nel **configurare l'accesso** schermata, seleziona **iniziare.**  

     ![Screenshot di esempio del portale aziendale, schermata "Configurare l'accesso".](./media/ios-05-cp-enroll-1903.PNG)  

4. Leggere l'elenco di informazioni sui dispositivi dell'organizzazione possa e non può visualizzare. Quindi toccare **continuazione**.  

5. Leggere le istruzioni nel **quali sono le novità?** dello schermo. Quando è pronti per scaricare e installare il profilo di gestione, toccare **continuazione**.  

 > [!IMPORTANT]
> Questi passaggi e le schermate successivo variano a seconda della versione di iOS. Seguire i passaggi per la versione di iOS. 

6. Safari viene aperto il sito Web portale aziendale nel dispositivo. Quando viene richiesto di scaricare il profilo di configurazione, toccare **Consenti**. Se si usa un dispositivo che esegue:  
    * iOS 12,2 e versioni successive: una volta completato il download, toccare **eseguita.** Continuare al passaggio 7 in questo articolo.
    * 12.1 e versioni precedenti di iOS: si verrà reindirizzati automaticamente l'App impostazioni. Andare al passaggio 8 in questo articolo.  
 
    Se si tocca accidentalmente **Ignore**, aggiornare la pagina. Verrà chiesto di aprire l'app portale aziendale. Dall'app, è possibile toccare **scaricare nuovamente**.

  > [!NOTE]
  > È necessario installare il profilo di gestione, come descritto nei passaggi successivi all'interno di 8 minuti di download del pacchetto. In caso contrario, verrà rimosso il profilo e sarà necessario riavviare la registrazione.  

7. iOS 12,2 e solo in un secondo momento: quando viene richiesto di aprire App portale aziendale, toccare **aprire**. Il **profilo di gestione installazione** schermata vengono elencati i passaggi per installare il profilo.

    ![Screenshot di esempio del portale aziendale, schermata Installa profilo di gestione.](./media/ios-1904-settings-icon.PNG)  

8. Passare all'app impostazioni e toccare **profilo scaricato**.  

    Se **profilo scaricato** non viene visualizzata come opzione, passare alla **generali** > **profili**. Se il profilo non ancora visibile, si potrebbe essere necessario scaricarlo nuovamente.  

    ![Screenshot di esempio dell'app impostazioni profilo scaricato l'impostazione.](./media/ios-1904-settings-badge.PNG)  

9. Toccare **Installa**.  
    
10. Modificare la password del dispositivo Quindi toccare **installare**.    

    ![Screenshot di esempio dell'app impostazioni, schermata Installa profilo con un cursore sulla * * Install * * pulsante.](./media/ios-1904-password-install.PNG)  


11. Nella schermata successiva è un avviso di sistema standard per la gestione dei dispositivi. Per continuare l'installazione, toccare **installare**. Se viene richiesto di attendibilità gestione remota, toccare **Trust**.  

    ![Screenshot di esempio dell'app impostazioni, schermata di avviso di sistema standard per il certificato radice e la gestione dei dispositivi mobili.](./media/ios-15-cp-enroll-1903.PNG)  

12. Al termine dell'installazione, toccare **Fine**. Per verificare che il profilo è stato installato, andare alla **profili e la gestione dei dispositivi** impostazioni. Verrà visualizzato il profilo elencato in **gestione dei dispositivi mobili**.   

    ![Screenshot di esempio di impostazioni app, profili e la gestione dei dispositivi, impostazioni che mostra il profilo di gestione.](./media/ios-00-cp-enroll-1903.PNG)  

13. Tornare all'app Portale aziendale. Portale aziendale verrà avviata per la sincronizzazione e configurare il dispositivo. Portale aziendale potrebbe essere richiesto di aggiornare le impostazioni aggiuntive del dispositivo. Se, toccare **continuazione**.  

    ![Screenshot di esempio del portale aziendale, schermata "Configurare l'accesso", con un triangolo giallo accanto al requisito di impostazione.](./media/ios-12-cp-enroll-1903.PNG)  

14. Si saprà che l'installazione è completa quando tutti gli elementi nell'elenco mostrano un cerchio verde. Toccare **Fine**.   
    
    ![Screenshot del portale aziendale di esempio "tutto pronto!" schermata che mostra tutti i cerchi verdi.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Se l'organizzazione monitora i limiti vocali e i dati o offre un dispositivo aziendale, potrebbe essere ancora alcuni passaggi da completare. Se viene chiesto di installare il **Datalert** app, vedere [la registrazione del dispositivo nella gestione delle spese per telecomunicazioni](enroll-your-device-with-telecom-expense-management-ios.md). Se l'organizzazione fa parte di Apple Device Enrollment Program, scoprire [come registrare il dispositivo di proprietà della società](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Passaggi successivi  
Trovare le app che consentiranno al lavoro o dell'istituto di istruzione. Scopri [modo in cui le app vengono resi disponibili](use-managed-apps-on-your-device-ios.md) tramite portale aziendale.  

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
