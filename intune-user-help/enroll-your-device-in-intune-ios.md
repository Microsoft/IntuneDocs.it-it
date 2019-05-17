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

Dopo la registrazione, il dispositivo diventa *gestito*. L'organizzazione può assegnare criteri e app al dispositivo tramite un provider di gestione di dispositivi mobili (MDM), ad esempio Intune.  

Per mantenere l'accesso alle informazioni aziendali o dell'istituto di istruzione dal dispositivo, è necessario configurare il dispositivo in base alle impostazioni preferite dell'organizzazione. Questo articolo descrive come usare il Portale aziendale per registrare il dispositivo e mantenere i requisiti relativi alle impostazioni dell'organizzazione. 

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

    ![Screenshot di esempio dell'app Portale aziendale, accesso.](./media/ios-01-cp-enroll-1903.PNG)  

2. Quando viene chiesto di indicare se si vuole ricevere notifiche dal Portale aziendale, toccare **Consenti**. Il Portale aziendale usa le notifiche per avvisare se, ad esempio, è necessario aggiornare le impostazioni del dispositivo. 

    ![Screenshot di esempio della home page del Portale aziendale, prompt "Notifiche".](./media/ios-04-cp-enroll-1903.PNG)  

3. Nella schermata di **configurazione dell'accesso** selezionare **Inizia**.  

     ![Screenshot di esempio del Portale aziendale, schermata di configurazione dell'accesso.](./media/ios-05-cp-enroll-1903.PNG)  

4. Prendere visione dell'elenco di informazioni relative al dispositivo la cui visualizzazione è concessa o non concessa all'organizzazione. Quindi toccare **Continua**.  

5. Leggere le istruzioni nella schermata **Passaggi successivi**. Quando si è pronti a scaricare e installare il profilo di gestione, toccare **Continua**.  

 > [!IMPORTANT]
> I passaggi e le schermate successivi variano a seconda della versione di iOS. Seguire i passaggi per la versione di iOS in uso. 

6. Safari apre il sito Web del Portale aziendale nel dispositivo. Quando viene chiesto di scaricare il profilo di configurazione, toccare **Consenti**. In un dispositivo che esegue  
    * iOS 12.2 e versioni successive: al termine del download, toccare **Fine**. Proseguire al passaggio 7 di questo articolo.
    * iOS 12.1 e versioni precedenti: si verrà automaticamente reindirizzati all'app Impostazioni. Proseguire al passaggio 8 di questo articolo.  
 
    Se si tocca accidentalmente **Ignora**, aggiornare la pagina. Verrà chiesto di aprire l'app Portale aziendale. Nell'app è possibile toccare **Ripetere il download**.

  > [!NOTE]
  > È necessario installare il profilo di gestione come descritto nei passaggi successivi entro 8 minuti dal download. In caso contrario, il profilo verrà rimosso e sarà necessario riavviare la registrazione.  

7. Solo iOS 12.2 e versioni successive: quando viene chiesto di aprire il Portale aziendale, toccare **Apri**. La schermata di **installazione del profilo di gestione** elenca i passaggi necessari per installare il profilo.

    ![Screenshot di esempio del Portale aziendale, schermata di installazione del profilo di gestione.](./media/ios-1904-settings-icon.PNG)  

8. Passare all'app Impostazioni e toccare **Profile Downloaded** (Profilo scaricato).  

    Se l'opzione **Profile Downloaded** (Profilo scaricato) non viene visualizzata, passare a **Generale** > **Profili**. Se il profilo non è visualizzato potrebbe essere necessario scaricarlo di nuovo.  

    ![Screenshot di esempio dell'app Impostazioni, impostazione Profile Downloaded (Profilo scaricato).](./media/ios-1904-settings-badge.PNG)  

9. Toccare **Installa**.  
    
10. Immettere la password del dispositivo. Quindi toccare **Installa**.    

    ![Screenshot di esempio dell'app Impostazioni, schermata di installazione del profilo con il cursore sul pulsante **Installa**.](./media/ios-1904-password-install.PNG)  


11. La schermata successiva riporta un avviso di sistema standard per la gestione dei dispositivi. Per continuare l'installazione, toccare **Installa**. Se viene chiesto di considerare attendibile la gestione remota, toccare **Considera attendibile**.  

    ![Screenshot di esempio dell'app Impostazioni, schermata di avviso di sistema standard per il certificato radice e la gestione di dispositivi mobili.](./media/ios-15-cp-enroll-1903.PNG)  

12. Al termine dell'installazione, toccare **Fine**. Per verificare che il dispositivo sia stato installato, passare alle impostazioni **Gestione di profili e dispositivi**. Il profilo dovrebbe essere visualizzato in **Gestione dispositivi mobili**.   

    ![Screenshot di esempio dell'app Impostazioni, impostazioni Gestione di profili e dispositivi con il profilo di gestione.](./media/ios-00-cp-enroll-1903.PNG)  

13. Tornare all'app Portale aziendale. Il Portale aziendale avvierà la sincronizzazione e la configurazione del dispositivo. Il Portale aziendale può richiedere di aggiornare altre impostazioni del dispositivo. Se ciò avviene, toccare **Continua**.  

    ![Screenshot di esempio del Portale aziendale, schermata di configurazione dell'accesso con un triangolo giallo accanto al requisito di impostazione.](./media/ios-12-cp-enroll-1903.PNG)  

14. La configurazione sarà completa quando per tutti gli elementi dell'elenco viene visualizzato un cerchio verde. Toccare **Fine**.   
    
    ![Screenshot di esempio del Portale aziendale, schermata "La configurazione è completata." in cui sono visualizzati tutti cerchi verdi.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Se l'organizzazione monitora i limiti di voce e dati oppure mette a disposizione dell'utente un dispositivo di proprietà dell'azienda, potrebbe essere necessario completare altri passaggi. Se viene chiesto di installare l'app **Datalert**, vedere [Registrare il dispositivo nella gestione delle spese per telecomunicazioni](enroll-your-device-with-telecom-expense-management-ios.md). Se l'organizzazione partecipa al programma DEP (Device Enrollment Program) di Apple, vedere [come registrare un dispositivo di proprietà dell'azienda](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Passaggi successivi  
Trovare app utili per le attività lavorative o scolastiche. Informazioni su [come vengono rese disponibili le app](use-managed-apps-on-your-device-ios.md) tramite il Portale aziendale.  

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
