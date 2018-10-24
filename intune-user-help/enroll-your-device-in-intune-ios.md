---
title: Configurare l'accesso del dispositivo iOS alle risorse aziendali | Microsoft Docs
description: Questo articolo descrive come rendere il dispositivo iOS gestito da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 85d0df026e49b36e148620ce2d06b4afaaf98ace
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2018
ms.locfileid: "48827888"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurare l'accesso del dispositivo iOS alle risorse aziendali

Registrare un dispositivo iOS nell'app Portale aziendale Intune per ottenere accesso protetto alla posta elettronica, ai file e alle app dell'organizzazione.

Prima di poter accedere ai dati di proprietà da un dispositivo aziendale o personale, è necessario impostare il dispositivo come gestito. Quando il dispositivo è gestito, l'organizzazione gli assegna criteri e app tramite il provider di gestione di dispositivi mobili (MDM). 

Per mantenere l'accesso alle informazioni aziendali o dell'istituto di istruzione tramite il dispositivo, è necessario configurare nel dispositivo le impostazioni preferite dell'organizzazione. Questo articolo descrive come il portale aziendale consenta di registrare, configurare e gestire il dispositivo in modo da soddisfare questi requisiti.

> [!NOTE]
> Se si è provato ad accedere alla posta elettronica aziendale nell'app Posta ed è stata ricevuta una richiesta di impostare il dispositivo come gestito, questo è il posto giusto. Eseguire le istruzioni seguenti per accedere alla posta elettronica e ad altre risorse aziendali sul dispositivo iOS.

## <a name="what-to-expect-from-the-company-portal-app"></a>Aspettative relative all'app Portale aziendale

### <a name="security"></a>Sicurezza
Durante la configurazione iniziale, l'app richiede l'autenticazione presso l'organizzazione. Quindi, comunica le eventuali impostazioni dispositivo che è necessario aggiornare. Ad esempio, le organizzazioni spesso definiscono il numero di caratteri minimo o massimo che la password deve soddisfare.    

### <a name="protection"></a>Protezione
Quando il dispositivo è registrato, l'app Portale aziendale continuerà ad assicurarsi che il dispositivo sia protetto. Ad esempio, se si installa un'app da un'origine non attendibile, si riceve un avviso dall'app e, talvolta, l'accesso ai dati aziendali viene revocato. I criteri di protezione delle app come questo sono comuni nelle organizzazioni. Richiedono spesso di disinstallare l'app non attendibile prima di poter ottenere nuovamente l'accesso.

### <a name="setting-notifications"></a>Impostazione delle notifiche
Se dopo la registrazione l'organizzazione applica un nuovo requisito di sicurezza, ad esempio l'autenticazione a più fattori, l'app Portale aziendale invierà una notifica. L'utente potrà quindi modificare le impostazioni per continuare a lavorare dal proprio dispositivo.  

Per altre informazioni sulla registrazione, vedere [Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios). 

## <a name="before-you-start"></a>Prima di iniziare

- Prima di iniziare la registrazione, accertarsi di aver completato l'intero processo. Se viene sospeso per più di pochi minuti, il programma di installazione potrebbe interrompersi, nel qual caso sarebbe necessario ricominciare da capo.  
- Se il processo ha esito negativo, tornare all'app Portale aziendale e riprovare.  
- Controllare che la connessione wi-fi sia attiva e che Safari funzioni correttamente nel dispositivo.
- Scaricare e installare l'[app Portale aziendale Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md).  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Uso dell'app Portale aziendale per configurare l'accesso alle risorse aziendali

|Elemento visualizzato|Spiegazione|
|---|---|
|![Schermata di accesso dell'app Portale aziendale con il pulsante "Accedi" in basso.](./media/ios-01-cp-enroll-1802.png)|Aprire l'app Portale aziendale e toccare **Accedi**.|
|![Richiesta di accesso di Azure AD.](./media/ios-02-cp-enroll-1802.png)|Immettere l'indirizzo di posta elettronica della società e toccare **Avanti**.|
|![Richiesta di password di Azure Active Directory.](./media/ios-03-cp-enroll-1802.png)|Immettere la password e quindi toccare **Accedi**.|
|![Schermata iniziale di caricamento delle risorse aziendali.](./media/ios-04-cp-enroll-1802.png)|Attendere il caricamento della schermata.|
|![Pagina di termini e condizioni.](./media/ios-05-cp-enroll-1802.png)|Leggere i termini e le condizioni e fare clic su **Accetta tutto**.|
|![Schermata di configurazione dell'accesso aziendale. È necessario eseguire determinate azioni sia nella schermata di gestione sia in quella delle impostazioni.](./media/ios-06-cp-enroll-1802.png)|Toccare **Inizio** per iniziare il processo che consentirà al dispositivo di accedere alle risorse aziendali. Se non è possibile eseguire subito questa operazione, fare clic su **Rimanda** per rimandare il processo. In questo caso, tuttavia, non sarà possibile ottenere messaggi di posta elettronica, documenti e altro ancora.|
|![Schermata relativa agli elementi che può vedere la società.](./media/ios-07-cp-enroll-1802.png)|Toccando il link **Altre informazioni** in fondo alla schermata, è possibile sapere quali informazioni può visualizzare la società. Altrimenti, toccare **Continua**.|
|![Schermata Passaggi successivi.](./media/ios-08-cp-enroll-1802.png)|Questa schermata illustra cosa accade durante il processo di configurazione. Sarà necessario eseguire alcune operazioni in Safari, nell'app Impostazioni e nell'app Portale aziendale. Toccare **Continua**.|
|![Caricamento della schermata visualizzata dopo aver toccato Avanti nella schermata Passaggi successivi.](./media/ios-09-cp-enroll-1802.png)|Attendere il caricamento della schermata.|
|![Reindirizzamento a Safari per la registrazione.](./media/ios-cp-sent-to-safari-1808.png)|Si viene reindirizzati al browser Safari per ottenere informazioni di gestione sul dispositivo.|
|![Messaggio di richiesta del sistema per chiedere l'autorizzazione ad aprire l'app Impostazioni.](./media/ios-8-cp-enroll-1711.png)|Toccare **Consenti** per aprire l'app Impostazioni e scaricare il profilo di configurazione. Il profilo viene installato per consentire all'azienda di gestire le informazioni aziendali presenti sul dispositivo.|
|![Screenshot della schermata Installa profilo nelle impostazioni del dispositivo.](./media/ios-9-cp-enroll-1711.png)|Toccare **Installa**.|
|![Finestra di dialogo modale di installazione del profilo nella parte inferiore della schermata.](./media/ios-10-cp-enroll-1711.png)|Toccare **Installa**.|
|![Schermata di caricamento del processo di installazione del profilo.](./media/ios-11-cp-enroll-1711.png)|Attendere il caricamento della schermata.|
|![Schermata di avviso relativa alla gestione del profilo.](./media/ios-12-cp-enroll-1711.png)|Questo avviso, scritto da Apple, consente di saperne di più sui tipi di azione che possono essere eseguiti su un dispositivo sottoposto a gestione. Per altre informazioni, vedere [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)|
|![Messaggio di richiesta del sistema per chiedere l'attendibilità della gestione remota.](./media/ios-13-cp-enroll-1711.png)|Toccare **Attendibilità** per consentire all'azienda di gestire le impostazioni e le informazioni aziendali presenti sul dispositivo.|
|![Schermata di caricamento della fase di completamento del processo di installazione del profilo.](./media/ios-14-cp-enroll-1711.png)|Attendere il caricamento della schermata.|
|![Schermata di conferma dell'installazione del profilo.](./media/ios-15-cp-enroll-1711.png)|Il profilo è ora installato e le impostazioni e le informazioni aziendali presenti sul dispositivo sono quasi pronte per essere gestite.|
|![Reindirizzamento a Safari per la registrazione.](./media/ios-16-cp-enroll-1711.png)|Si viene reindirizzati al browser Safari per completare l'acquisizione delle informazioni di gestione relative al dispositivo. |
|![Messaggio di richiesta del sistema per chiedere l'apertura dell'app Portale aziendale.](./media/ios-17-cp-enroll-1711.png)|Toccare **Apri**.|
|![Schermata di caricamento delle risorse aziendali.](./media/ios-21-cp-enroll-1802.png)|Attendere il caricamento della schermata.|
|![Selezionare una categoria di dispositivi nell'app Portale aziendale.](./media/ios-22-cp-enroll-1802.png)|Scegliere la categoria più idonea per il dispositivo in uso. Questa scelta dipende in genere dal proprietario del dispositivo e dal luogo in cui si trova il dispositivo nella maggior parte dei casi.|
|![Categoria selezionata.](./media/ios-23-cp-enroll-1802.png)||
|![Gestione del dispositivo eseguita con esito positivo. Necessità di aggiornare le impostazioni.](./media/ios-24-cp-enroll-1802.png)|Il dispositivo risulta ora correttamente gestito. Probabilmente, tuttavia, esistono ancora alcune impostazioni, ad esempio la lunghezza della password, che l'azienda richiede che vengano aggiornate. Toccare **Continua** per procedere.|
|![Conferma delle impostazioni del dispositivo.](./media/ios-25-cp-enroll-1802.png)|L'app Portale aziendale verificherà che non siano presenti impostazioni da aggiornare.|
|![Controllo delle impostazioni completato con versione del sistema operativo non corretta](./media/ios-26-cp-enroll-1802.png)|L'app Portale aziendale fornirà le istruzioni necessarie per correggere eventuali problemi con le impostazioni. Al termine della risoluzione dei problemi, toccare **Verifica le impostazioni**.|
|![Schermata di caricamento di conferma delle impostazioni del dispositivo](./media/ios-27-cp-enroll-1802.png)|Il dispositivo verificherà che le impostazioni siano sufficientemente sicure per accedere alle risorse aziendali.|
|![Impostazioni registrate e aggiornate correttamente](./media/ios-28-cp-enroll-1802.png)|A questo punto, il dispositivo è ora registrato in Intune.|

> [!Note]
> È possibile che sia necessario eseguire ancora alcuni passaggi prima che il dispositivo sia completamente gestito. Vedere altre informazioni sulla [registrazione del dispositivo con la gestione delle spese per le telecomunicazioni](enroll-your-device-with-telecom-expense-management-ios.md). Se l'organizzazione usa Device Enrollment Program di Apple, vedere altre informazioni [qui](enroll-your-device-dep-ios.md).

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
