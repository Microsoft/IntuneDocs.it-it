---
title: Registrare il Mac con Portale aziendale Intune | Microsoft Docs
description: Informazioni su come registrare il Mac in Intune con l'app Portale aziendale.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba285fc9de58b3fb739a16722e0e05e36e840e87
ms.sourcegitcommit: 76ae5aea5deee7a590e24c3b2bb52f88125943e5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74098106"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>Registrare il dispositivo macOS usando l'app Portale aziendale  

Registrare un dispositivo macOS nell'app Portale aziendale Intune per ottenere accesso protetto alla posta elettronica aziendale o dell'istituto di istruzione, ai file e alle app.

Le organizzazioni richiedono in genere la registrazione del dispositivo prima di poter accedere ai dati proprietari. Dopo la registrazione, il dispositivo diventa *gestito*. L'organizzazione può assegnare criteri e app al dispositivo tramite un provider di gestione di dispositivi mobili (MDM), ad esempio Intune. Per ottenere accesso continuato alle informazioni aziendali o dell'istituto di istruzione tramite il dispositivo, è necessario configurare nel dispositivo le impostazioni dei criteri dell'organizzazione corrispondenti.  

Questo articolo descrive come usare l'app Portale aziendale Intune per macOS per registrare, configurare e gestire il dispositivo in modo da soddisfare i requisiti dell'organizzazione.  


## <a name="what-to-expect-from-the-company-portal-app"></a>Aspettative relative all'app Portale aziendale

Durante la configurazione iniziale, l'app Portale aziendale richiede l'accesso e l'autenticazione all'interno dell'organizzazione. Portale aziendale informa quindi le impostazioni del dispositivo che è necessario configurare per soddisfare i requisiti dell'organizzazione. Ad esempio, le organizzazioni spesso definiscono il numero di caratteri minimo o massimo che la password deve soddisfare.    

Dopo la registrazione del dispositivo, Portale aziendale assicurerà sempre che il dispositivo sia protetto in base ai requisiti dell'organizzazione. Se, ad esempio, si installa un'app da un'origine non attendibile, Portale aziendale segnalerà l'utente e potrebbe limitare l'accesso alle risorse dell'organizzazione. I criteri di protezione delle app come questo sono comuni. Per ottenere nuovamente l'accesso, è probabile che sia necessario disinstallare l'app non attendibile. 

Se dopo la registrazione l'organizzazione applica un nuovo requisito di sicurezza, ad esempio l'autenticazione a più fattori, l'app Portale aziendale invierà una notifica. L'utente potrà quindi modificare le impostazioni per continuare a lavorare dal proprio dispositivo.  

Per altre informazioni sulla registrazione, vedere [Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-macos-device-managed"></a>Gestione del dispositivo macOS  
Usare la procedura seguente per registrare il dispositivo macOS con l'organizzazione. Il dispositivo deve eseguire macOS 10,12 o versione successiva.   

> [!NOTE]
> Durante questo processo, potrebbe essere richiesto di consentire Portale aziendale di usare informazioni riservate archiviate nel keychain. Queste richieste fanno parte della sicurezza di Apple. Quando si riceve il prompt, digitare la password del keychain di accesso e selezionare **Consenti sempre**. Se si preme **invio** o **ritorna** sulla tastiera, la richiesta selezionerà invece **Consenti**, che può comportare ulteriori richieste.  

### <a name="install-company-portal-app"></a>Installare l'app Portale aziendale  
1. Passare a [registra il Mac](https://go.microsoft.com/fwlink/?linkid=853070).  
2. Viene scaricato il file del programma di installazione di Portale aziendale. pkg. Aprire il programma di installazione e continuare con la procedura. 
3. Accettare il contratto di licenza software. 
4. Immettere la password del dispositivo o l'impronta digitale registrata per installare il software.  
5. Aprire Portale aziendale. 

> [!IMPORTANT]
> Microsoft AutoUpdate potrebbe aprirsi per aggiornare il software Microsoft. Dopo aver installato tutti gli aggiornamenti, aprire l'app Portale aziendale. Per un'esperienza di installazione ottimale, installare le versioni più recenti di Microsoft AutoUpdate e Portale aziendale.  


### <a name="enroll-your-mac"></a>Registrare il Mac  


1. Accedere al Portale aziendale con l'account aziendale o dell'istituto di istruzione.  
2. Quando si apre l'app, selezionare **Begin**.  
3. Esaminare le informazioni [che l'organizzazione può o meno visualizzare](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) nel dispositivo registrato. Selezionare quindi **Continua**.  
4. Nella schermata **Installa profilo di gestione** selezionare **Scarica profilo**.   

    ![Screenshot di esempio di Portale aziendale, installare la schermata del profilo di gestione, evidenziando il pulsante "Scarica profilo".](./media/install-mgmt-profile-mac-1911.PNG)   
5. Si apriranno le preferenze di sistema del dispositivo. Selezionare **Installa** , quindi fare di nuovo clic su **Installa** . Se viene richiesto, immettere la password del dispositivo.  

    ![Screenshot di esempio delle preferenze di sistema macOS, richiesta di installazione, evidenziando il pulsante "Installa".](./media/system-preference-install-1911.PNG)  
6. Una volta installato, il profilo verrà visualizzato nell'elenco profili in profilo di **gestione.**  

   ![Screenshot di esempio di preferenze di sistema macOS, schermata dei profili, che evidenzia il profilo di gestione installato.](./media/system-preference-verify-1911.PNG)   
7. Tornare a Portale aziendale.   
8. Per l'organizzazione potrebbe essere necessario aggiornare le impostazioni del dispositivo. Al termine dell'aggiornamento delle impostazioni, selezionare **Controlla impostazioni**.  

    ![Screenshot di esempio di Portale aziendale, aggiornare la schermata delle impostazioni del dispositivo, evidenziando il pulsante "Verifica impostazioni".](./media/update-settings-mac-1911.PNG)  
9. Al termine dell'installazione, selezionare **fine**.  


 ## <a name="troubleshooting-and-feedback"></a>Risoluzione dei problemi e commenti e suggerimenti   

Se si verificano problemi durante la registrazione, passare a **guida** > **inviare un report di diagnostica** per segnalare il problema agli sviluppatori di app Microsoft. Queste informazioni vengono usate per contribuire a migliorare l'app. Queste informazioni verranno utilizzate anche per risolvere il problema se il personale del supporto IT raggiunge il proprio aiuto.  

Dopo aver segnalato il problema a Microsoft, è possibile inviare i dettagli dell'esperienza al personale del supporto IT. Selezionare **i dettagli della posta elettronica**. Digitare ciò che si è verificato nel corpo del messaggio di posta elettronica. Per trovare l'indirizzo di posta elettronica del personale di supporto, passare all'app Portale aziendale > **contatto**. In alternativa, controllare il [sito web portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
 

Inoltre, il team di Microsoft Intune Portale aziendale sarebbe lieta di ricevere commenti e suggerimenti. Passare a **Help** > **inviare commenti** e suggerimenti per condividere pensieri e idee.  

## <a name="unverified-profiles"></a>Profili non verificati  
Quando si visualizzano i profili di gestione di dispositivi mobili (MDM) installati in **Preferenze di sistema** > **Profili**, alcuni profili vengono visualizzati con lo stato non verificato. Purché il profilo di gestione presenti uno stato verificato, non sarà necessario preoccuparsene.  

È il profilo di gestione a definire la connessione al canale MDM. Purché il profilo di gestione sia verificato, tutti gli altri profili distribuiti nel computer tramite tale canale ereditano le caratteristiche di sicurezza del profilo di gestione.  

## <a name="updating-the-company-portal-app"></a>Aggiornamento dell'app Portale aziendale

L'aggiornamento dell'app Portale aziendale viene eseguito come quello di qualsiasi altra app di Office, tramite Microsoft AutoUpdate per macOS. Vedere altre informazioni sull'[aggiornamento di app Microsoft per macOS](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Passaggi successivi  
Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  


