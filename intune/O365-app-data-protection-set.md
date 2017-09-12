---
title: Impostare la gestione dati di base nelle app di Office 365 in Intune
titlesuffix: Azure portal
description: Documentazione di supporto relativa alla procedura guidata per la gestione delle app di Office 365."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b818152d2172ccf85a8323ba3ff70a0b270d20df
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps"></a>Esperienza utente relativa alla protezione base nelle app di Office 365 gestite

La procedura guidata per la**gestione delle app di Office 365** crea un criterio di protezione delle app per ogni piattaforma del dispositivo.

La procedura guidata attiva i criteri seguenti:

**iOS**
* Crittografa dati app

**Android**
* Crittografa dati app
* Richiedi PIN semplice per l'accesso

Questi criteri assicurano la gestione delle app di Office 365, offrendo la possibilità di cancellare i dati di lavoro dalle app di Office, quando è necessario. Assicurano anche la protezione base in caso di smarrimento o furto del dispositivo, garantendo la crittografia dei dati di lavoro e l'immissione obbligatoria di un PIN per visualizzare i dati nelle app di Office 365.


Questo articolo usa OneDrive for Business come esempio per dimostrare che l'esperienza dell'utente in un'applicazione gestita da Intune.


>[!NOTE]
>In un dispositivo personale l'utente deve solitamente scaricare l'app. Se il dispositivo è gestito da una soluzione di gestione di dispositivi mobili (MDM), è possibile distribuire l'app nel dispositivo.

## <a name="user-experience-on-an-ios-device"></a>Esperienza utente in un dispositivo iOS

1. Avviare l'app OneDrive for Business per aprire la pagina di accesso.  <br/> ![Immagine della schermata di accesso di OneDrive per iOS](./media/onedrive-ios-sign-in.png)
2. Digitare il nome utente dell'account aziendale. Si verrà reindirizzati alla pagina di autenticazione di Office 365 in cui immettere le credenziali aziendali. <br/> ![Immagine della pagina di accesso a Office 365](./media/o365-sign-in-ios.png)
3. Dopo la corretta autenticazione delle credenziali in Azure Active Directory, verranno applicati i criteri di protezione delle app e verrà richiesto di riavviare l'app OneDrive for Business.  <br/>![Immagine della richiesta di riavvio per iOS](./media/ios-restart-prompt.png)    
  > [!NOTE]
  > Il messaggio indicante che il riavvio è richiesto viene visualizzato solo per i dispositivi non registrati in Intune.


4. Riavviare l'app OneDrive for Business. L'app viene avviata con i criteri di protezione delle app attivati e viene richiesto di impostare un PIN per il dispositivo, se questa operazione non è stata ancora eseguita. <br/> ![Immagine della richiesta di creare un PIN](./media/pin-prompt-ios.png)    
  > [!NOTE]
  > Questo messaggio non verrà visualizzato alla maggior parte degli utenti. Il messaggio verrà visualizzato solo agli utenti che non hanno attivato un PIN nel proprio dispositivo iOS.


5. Dopo avere impostato e confermato il PIN, tornare all'app OneDrive for Business. Verrà visualizzato un avviso singolo indicante che l'amministratore IT sta ora proteggendo i dati di lavoro in OneDrive. <br/> ![Immagine dell'avviso singolo inviato dall'amministratore IT](./media/one-time-notice.png)
6. Fare clic su questo avviso per accedere ai file in OneDrive for Business. <br/> ![Immagine dei file di OneDrive nel dispositivo iOS](./media/onedrive-files-ios.png) <br/>

>[!NOTE]
>Quando si modifica un criterio distribuito, le modifiche verranno applicate alla successiva apertura dell'applicazione.


## <a name="user-experience-on-an-android-device"></a>Esperienza utente con un dispositivo iOS

1. Avviare l'app OneDrive for Business per aprire la pagina di accesso.  <br/> ![Immagine della schermata iniziale dell'app OneDrive](./media/onedrive-android-welcome.png)
2. Digitare il nome utente dell'account aziendale. Si verrà reindirizzati alla pagina di autenticazione di Office 365 in cui immettere le credenziali aziendali. <br/> ![Immagine dell'accesso a Office 365 in Android](./media/o365-sign-in-android.png)
3. Dopo che le credenziali saranno state autenticate da Azure Active Directory, verrà visualizzato un messaggio con le istruzioni per installare l'app Portale aziendale, se non è già installata nel dispositivo. Toccare **Vai allo Store** per continuare. <br/> ![Immagine del messaggio per ottenere l'app Portale aziendale](./media/get-company-portal-android.png) <br/>Se l'app Portale aziendale è già installata nel telefono, l'app OneDrive for Business verrà avviata automaticamente ed è possibile passare direttamente alla nota finale.    
  > [!IMPORTANT]
  > In Android, dopo aver configurato le app di Office da gestire con criteri di protezione delle app, l'utente del dispositivo **deve** installare l'app Portale aziendale per accedere ai messaggi di posta elettronica e ai documenti di lavoro, anche se per leggere effettivamente i messaggi o i documenti l'utente finale non ha necessità di aprire o accedere all'app.

4. A questo punto si viene reindirizzati allo store Google Play, da cui è possibile scaricare e installare l'app Portale aziendale. L'app consente di mantenere i dati sicuri e protetti. <br/> ![Immagine dell'app nello store Google Play](./media/google-play-get-app-android.png)
5. Dopo avere completato l'installazione, scegliere **Accetta** per accettare i termini. L'app OneDrive for Business verrà avviata automaticamente.


>[!NOTE]
>Alla successiva apertura di OneDrive for Business, è possibile che venga visualizzata una richiesta di impostare un PIN, se richiesto dall'IT. Dopo aver impostato e confermato il PIN, è possibile passare a OneDrive for Business.

![Immagine della richiesta del PIN](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>Quali criteri vengono impostati da questa procedura guidata?
|     |       | |
|----|--------|-|
|**Nome**|Gestire le app di Office 365| |
| **Descrizione**|Creato dalla procedura guidata per la gestione delle app di Office 365| |
| |  | |
| **Nome dell'impostazione** |**Valore dei criteri iOS** | **Valore dei criteri Android** |
|Impedisci backup in iTunes e iCloud| No | N/D |
|Impedisci backup in Android |N/D | No|
|Consenti all'app di trasferire i dati ad altre app | Tutte le app | Tutte le app|
|Consenti all'app di ricevere i dati da altre app| Tutte le app | Tutte le app|
|Impedisci Salva con nome | No | No|
|Limita le operazioni taglia, copia e incolla con le altre app | Qualsiasi app | Qualsiasi app |
|Limitare il contenuto Web per la visualizzazione in Managed Browser dell'azienda | No| No|
|Crittografa dati app | Quando il dispositivo è bloccato | sì|
|Disabilita sincronizzazione contatti | No| No|
|Disabilita stampa | No | No|
|Richiedi PIN per l'accesso | No | sì|
|Numero di tentativi prima della reimpostazione del PIN | N/D |5|
|Consenti PIN semplice | N/D |sì|
|Lunghezza PIN | N/D | 4|
|Consenti impronta digitale anziché PIN | N/D | sì |
|Richiedi credenziali aziendali per l'accesso | No | No|
|Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted | No | No|
|Controlla di nuovo i requisiti di accesso dopo (minuti) - Timeout | 30 | 30|
|Controlla di nuovo i requisiti di accesso dopo (minuti) - Periodo di prova offline | 720 |720|
|Intervallo offline (giorni) prima della cancellazione dei dati dell'app | 90 | 90|
|Blocca acquisizione schermo (solo per dispositivi Android) | N/D | No |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>Perché un criterio PIN per le app viene configurato solo per i dispositivi Android?
La crittografia funziona in modo diverso in iOS e in Android.

In iOS per le app associate a un criterio di protezione delle app di Intune, i dati inattivi vengono crittografati usando la crittografia a livello di dispositivo offerta dal sistema operativo. L'attivazione del criterio di crittografia delle app implica automaticamente la richiesta all'utente di avere a disposizione e immettere un PIN di dispositivo per accedere ai dati di lavoro. Agli utenti che non dispongono già di un PIN di dispositivo configurato nel dispositivo verrà chiesto di creare uno.

In Android, per le app associate a un criterio di protezione delle app di Intune, i dati vengono crittografati in modo sincrono durante le attività di I/O su file. Il contenuto nella memoria del dispositivo è sempre crittografato. Nei dispositivi non gestiti dalla soluzione MDM, i criteri di protezione delle app non possono imporre il requisito di un PIN per il dispositivo. Per assicurarsi che agli utenti venga richiesto un PIN per accedere ai dati di lavoro, la procedura guidata abilita i criteri relativi al PIN delle app.

È sempre possibile modificare queste impostazioni per soddisfare i requisiti dell'organizzazione.

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>Come è possibile visualizzare e modificare i criteri creati dalla procedura guidata?
Per visualizzare o aggiornare questi criteri o eventuali criteri creati nel portale di Intune di Azure, dal dashboard scegliere **Gestisci app** > **Criteri di protezione app**. A destra verrà aperto l'elenco di criteri. Scegliere il criterio da visualizzare per esaminare e modificare le impostazioni. <br/>
![Immagine del percorso dell'interfaccia utente per visualizzare i criteri](./media/image-for-faq.png)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sui [criteri di protezione delle app](https://docs.microsoft.comapp-protection-policy.md).
