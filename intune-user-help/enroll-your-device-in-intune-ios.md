---
title: Configurare l'accesso del dispositivo iOS alle risorse aziendali | Microsoft Docs
description: Questo articolo descrive come rendere il dispositivo iOS gestito da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: ee0f438d929abd6b5b90acbaeeddc41e3ce11f98
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490643"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurare l'accesso del dispositivo iOS alle risorse aziendali  

Registrare un dispositivo iOS nell'app Portale aziendale Intune per ottenere accesso protetto alla posta elettronica, ai file e alle app dell'organizzazione.

Prima di poter accedere ai dati di proprietà da un dispositivo aziendale o personale, è necessario impostare il dispositivo come gestito. Quando il dispositivo è gestito, l'organizzazione gli assegna criteri e app tramite un provider di gestione di dispositivi mobili (MDM), come Intune. 

Per mantenere l'accesso alle informazioni aziendali o dell'istituto di istruzione tramite il dispositivo, è necessario configurare nel dispositivo le impostazioni preferite dell'organizzazione. Questo articolo descrive come usare il portale aziendale per eseguire la registrazione dispositivo e gestire i requisiti di impostazione di un'organizzazione. 

> [!NOTE]
> Se si è provato ad accedere alla posta elettronica aziendale nell'app Posta ed è stata ricevuta una richiesta di impostare il dispositivo come gestito, questo è il posto giusto. Eseguire le istruzioni seguenti per accedere alla posta elettronica e ad altre risorse aziendali sul dispositivo iOS.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Aspettative relative all'app Portale aziendale  

### <a name="security"></a>Sicurezza  
Durante la configurazione iniziale, l'app richiede l'autenticazione presso l'organizzazione. Quindi, comunica le eventuali impostazioni dispositivo che è necessario aggiornare. Ad esempio, le organizzazioni spesso definiscono il numero di caratteri minimo o massimo che la password deve soddisfare.     

### <a name="protection"></a>Protezione  
Quando il dispositivo è registrato, l'app Portale aziendale continuerà ad assicurarsi che il dispositivo sia protetto. Ad esempio, se si installa un'app da un'origine non attendibile, si riceve un avviso dall'app e, talvolta, l'accesso ai dati aziendali viene revocato. Un criterio simile al seguente è comune nelle organizzazioni e spesso è necessario disinstallare l'app non attendibile prima che si possa ottenere nuovamente l'accesso.  

### <a name="setting-notifications"></a>Impostazione delle notifiche  
Se dopo la registrazione l'organizzazione applica un nuovo requisito di sicurezza, ad esempio l'autenticazione a più fattori, l'app Portale aziendale invierà una notifica. L'utente potrà quindi modificare le impostazioni per continuare a lavorare dal proprio dispositivo.  

Per altre informazioni sulla registrazione, vedere [Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrare il dispositivo iOS   

> [!IMPORTANT]
> Gli screenshot in questa sezione illustrano l'esperienza per i dispositivi che eseguono iOS versione 12.1 e versioni precedenti. Dove applicabile, sono state incluse le istruzioni specifiche per iOS versione 12.2 e versioni successive. Se si nota che la tua esperienza è diverso rispetto alle schermate visualizzate, fare riferimento alle istruzioni di 12,2.      

Passare all'App store per scaricare e installare il [app portale aziendale Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) al dispositivo. Durante la registrazione, è necessario anche una connessione Wi-Fi e l'accesso al browser Safari. 

Se viene sospesa per più di pochi minuti durante la registrazione, l'app può chiudere o uscire dall'installazione. In questo caso, aprire l'app portale aziendale e riprovare.  

1. Aprire l'app Portale aziendale e accedere con l'account aziendale o dell'istituto di istruzione. 

    ![Screenshot di esempio dell'app portale aziendale, di accesso.](./media/ios-01-cp-enroll-1903.PNG)  

2. Quando viene richiesto di ricevere le notifiche di portale aziendale, toccare **Consenti.** Portale aziendale Usa le notifiche da ricevere un avviso se, ad esempio, le impostazioni del dispositivo devono essere aggiornati. 

    ![Screenshot di esempio della home page di portale aziendale, prompt dei comandi "Notifiche".](./media/ios-04-cp-enroll-1903.PNG)  

3. Nel **configurare l'accesso** schermata, seleziona **iniziare.**  

     ![Screenshot di esempio del portale aziendale, schermata "Configurare l'accesso".](./media/ios-05-cp-enroll-1903.PNG)  

4. Leggere l'elenco di informazioni sui dispositivi dell'organizzazione possa e non può visualizzare. [Dettagli aggiuntivi su questo argomento](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md) è disponibile tramite il **ulteriori informazioni** collegamento. Al termine, toccare **continuazione**.  

    ![Screenshot di esempio dell'app portale aziendale, "Ciò che la mia organizzazione vede", con il pulsante Continua.](./media/ios-06-cp-enroll-1903.PNG)  
 
5. Il **quali sono le novità?** schermata vengono riepilogati i passaggi rimanenti. Questi passaggi potrebbero essere diversi a seconda della versione di iOS. 
    * **iOS 12,2 e versioni successive**: l'esperienza potrebbe richiedere invece di:  

        a. **Consentire il download del profilo di gestione**: nel browser aprire il sito Web portale aziendale e richiesto di consentire il download. Il download verrà salvato nell'app impostazioni.  

        b. **Aprire l'app impostazioni e installare il profilo**: È necessario passare all'app impostazioni e installare il profilo di gestione.  

        c. **Tornare all'app portale aziendale**: sarà necessario tornare all'app portale aziendale per completare l'installazione.  

    Quando si è pronti per scaricare il profilo di gestione, toccare **continuazione**.  

6. Safari viene aperto il sito Web portale aziendale. Quando viene richiesto di scaricare il profilo di configurazione, toccare **Consenti**.  
    * **iOS 12,2 e versioni successive**: attendere il profilo al termine del download in Safari e toccare **Fine**. Aprire quindi l'app **Impostazioni** nel dispositivo.  

    > [!IMPORTANT]
    > È necessario passare il **impostazioni** app e l'installazione del profilo all'interno di 8 minuti di download del pacchetto. In caso contrario, verrà rimosso il profilo e sarà necessario riavviare la registrazione. 

7. Nel **le impostazioni** app e toccare **Installa profilo scaricato** > **installare**. Se **Installa profilo scaricato** non viene visualizzata come opzione, passare alla **generali** > **profili**. Se il profilo non ancora visibile, si potrebbe essere necessario scaricarlo nuovamente.  

    ![Screenshot di esempio dell'app impostazioni, impostazione Installa profilo scaricato, con una notifica rossa che indica un profilo scaricato di recente.](./media/ios-10-cp-enroll-1903.PNG)  
    
8. Se richiesto, immettere la password del dispositivo. Quindi toccare **installare**.      

9. Nella schermata successiva è un avviso di sistema standard per la gestione dei dispositivi. Per altre informazioni su ciò che l'organizzazione può e non è possibile visualizzare nel dispositivo, vedere la relativa [articolo di documentazione Intune](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md). Per continuare l'installazione, toccare **installare**. Se viene chiesto di considerare attendibile la gestione remota, toccare **Trust**.  

    ![Screenshot di esempio dell'app impostazioni, schermata di avviso di sistema standard per il certificato radice e la gestione dei dispositivi mobili.](./media/ios-15-cp-enroll-1903.PNG)  

10. Al termine dell'installazione, toccare **Fine**. Per verificare che il profilo è stato installato, andare alla **profili e la gestione dei dispositivi** impostazioni. Verrà visualizzato il profilo elencato in **gestione dei dispositivi mobili**.   

    ![Screenshot di esempio di impostazioni app, profili e la gestione dei dispositivi, impostazioni che mostra il profilo di gestione.](./media/ios-00-cp-enroll-1903.PNG)  


11. Tornare all'app **Portale aziendale**. Portale aziendale verrà avviata per la sincronizzazione e configurare il dispositivo. Portale aziendale potrebbe essere richiesto di aggiornare le impostazioni aggiuntive del dispositivo. Se, toccare **continuazione**.

    ![Screenshot di esempio del portale aziendale, schermata "Configurare l'accesso", con un triangolo giallo accanto al requisito di impostazione.](./media/ios-12-cp-enroll-1903.PNG)  

12. Si saprà che l'installazione è completa quando tutti gli elementi nell'elenco mostrano un cerchio verde. Toccare **Fine**.  
    
    ![Screenshot del portale aziendale di esempio "tutto pronto!" schermata che mostra tutti i cerchi verdi.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Se l'organizzazione monitora i limiti vocali e i dati o offre un dispositivo aziendale, potrebbe essere ancora alcuni passaggi da completare. Se viene chiesto di installare il **Datalert** app, vedere [la registrazione del dispositivo nella gestione delle spese per telecomunicazioni](enroll-your-device-with-telecom-expense-management-ios.md). Se l'organizzazione fa parte di Apple Device Enrollment Program, scoprire [come registrare il dispositivo di proprietà della società](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Passaggi successivi  
Trovare le app che consentiranno al lavoro o dell'istituto di istruzione. Scopri [modo in cui le app vengono resi disponibili](use-managed-apps-on-your-device-ios.md) tramite portale aziendale.  

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
