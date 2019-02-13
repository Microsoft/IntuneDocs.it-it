---
title: Registrare il dispositivo macOS in Intune con il Portale aziendale | Microsoft Docs
description: Descrive come registrare un dispositivo macOS in Intune con l'app Portale aziendale
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c9ea11cd19fee8f491329020753501996b47f40
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834722"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Registrare il dispositivo macOS in Intune con l'app Portale aziendale

Registrare un dispositivo macOS nell'app Portale aziendale Intune per ottenere accesso protetto alla posta elettronica, ai file e alle app dell'organizzazione.

Le organizzazioni richiedono spesso di attivare la gestione del dispositivo prima di concedere l'accesso ai dati proprietari da quest'ultimo. Quando un dispositivo è gestito, le organizzazioni possono effettuare il push di criteri e app verso di esso tramite il provider di gestione dei dispositivi mobili. Per ottenere accesso continuato alle informazioni aziendali o dell'istituto di istruzione tramite il dispositivo, è necessario configurare nel dispositivo le impostazioni dei criteri corrispondenti.  

Questo articolo descrive come l'app Portale aziendale Intune per macOS consenta di registrare, configurare e gestire il dispositivo in modo da soddisfare i requisiti dell'organizzazione.

## <a name="what-to-expect-from-the-company-portal-app"></a>Aspettative relative all'app Portale aziendale

Durante la configurazione iniziale, l'app richiede l'autenticazione presso l'organizzazione. Quindi, comunica le eventuali impostazioni dispositivo che è necessario effettuare. Ad esempio, le organizzazioni spesso definiscono il numero di caratteri minimo o massimo che la password deve soddisfare.    

Quando il dispositivo è registrato, l'app Portale aziendale continuerà ad assicurarsi che il dispositivo sia protetto. Ad esempio, se si installa un'app da un'origine non attendibile, si riceve un avviso dall'app e, talvolta, l'accesso ai dati aziendali viene revocato. Criteri di protezione delle app come questi sono comuni nelle organizzazioni e spesso richiedono che l'app non attendibile venga disinstallata prima di concedere nuovamente l'accesso.

Se dopo la registrazione l'organizzazione applica un nuovo requisito di sicurezza, ad esempio l'autenticazione a più fattori, l'app Portale aziendale invierà una notifica. L'utente potrà quindi modificare le impostazioni per continuare a lavorare dal proprio dispositivo.  

Per altre informazioni sulla registrazione, vedere [Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo macOS in Intune?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-device-managed"></a>Attivare la gestione del dispositivo  
Usare la procedura seguente per registrare i dispositivi macOS che eseguono OS X El Capitan 10.11 e versioni successive.   


1. Per accedere al sito Web del portale aziendale, aprire una nuova finestra in __Safari__ e passare a https://portal.manage.microsoft.com.  

2. Eseguire l'accesso al sito Web del portale aziendale con l'account aziendale o dell'istituto di istruzione.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Selezionare **Menu** > **Dispositivi** nell'angolo superiore sinistro della pagina.  

4. Nella pagina __Dispositivi__ verrà visualizzato l'elenco dei dispositivi gestiti o un banner. Il contenuto della pagina dipende dalla presenza, o meno, di dispositivi gestiti. 
    * Per aggiungere un dispositivo che non è elencato, selezionare il banner con scritto **Tap here to tell us which device you're using or add a new device** (Toccare qui per specificare il dispositivo in uso o aggiungere un nuovo dispositivo).
    * In assenza di dispositivi, viene visualizzato il banner: **You don't have any managed devices. Add this one by tapping here. (Non ci sono dispositivi gestiti. Aggiungere questo toccando qui)** Fare clic sul banner per aggiungere il dispositivo.  

     ![Screenshot della pagina dei dispositivi, con un quadrato rosso attorno all'opzione banner per evidenziare dove fare clic.](./media/CP-enroll-MACOS-1808.png)  
5.  Completare il passaggio seguente che corrisponde al messaggio attualmente visualizzato nel portale aziendale.  
    * Se si aggiunge un dispositivo per la prima volta, verrà richiesto di scaricare l'app Portale aziendale nel dispositivo. Fare clic su **Download** per continuare.  

         ![Screenshot di esempio della schermata dei messaggi di richiesta per scaricare l'app Portale aziendale macOS. L'utente ha la possibilità di selezionare il pulsante Download blu in basso a sinistra nel messaggio o il pulsante Annulla grigio in basso a destra.](./media/CP-enroll-download-macOS-1808.png)  

    * Se si dispone già di almeno un dispositivo macOS gestito, si riceverà un messaggio con un elenco dei dispositivi macOS gestiti attualmente. Selezionare **Il dispositivo non è elencato qui** > **Download** per scaricare l'app Portale aziendale sul dispositivo che si sta aggiungendo.  

         ![Screenshot di esempio della schermata dei messaggi di richiesta per scaricare l'app Portale aziendale macOS. L'utente ha la possibilità di selezionare *Il dispositivo non è elencato qui* o un dispositivo specifico nella parte centrale della pagina. Viene visualizzato un pulsante Download blu in basso a sinistra nel messaggio e un pulsante Annulla grigio in basso a destra](./media/cp-mac-os-device-isnt-here-1808.png)  

6. Il dispositivo verifica che sia possibile aprire in modo sicuro il file di installazione **CompanyPortal.pkg**. Al termine, aprire il programma di installazione e completare l'installazione.  

7. Quando il programma ha completato l'installazione, passare a **Launchpad** e aprire **Portale aziendale**.  

8. Il dispositivo macOS richiederà di confermare che si desidera aprire l'app Portale aziendale. Fare clic su **Apri**.  

   > [!TIP]
   > Intune deve accedere al computer per assicurarsi che il dispositivo sia sufficientemente sicuro per accedere alle risorse dell'organizzazione. Se l'app Portale aziendale non si apre sul computer, provare a [disattivare Gatekeeper](https://support.apple.com/HT202491). Quindi aprire l'app.

9. La prima schermata visualizzata nell'app Portale aziendale chiede di eseguire l'**Accesso**. Usare lo stesso account aziendale o dell'istituto di istruzione utilizzato per eseguire l'accesso al sito Web del portale aziendale.

10. Il portale aziendale verifica le informazioni sull'account e visualizza gli stati relativi a **Registrazione del dispositivo** e **Conformità del dispositivo**. Triangoli gialli evidenziano le azioni da eseguire per proteggere il dispositivo macOS per l'istituto di istruzione o il lavoro. Fare clic su **Inizia** per iniziare la registrazione. 

11. Se richiesto, digitare le informazioni di accesso del computer.  

Potrebbero occorrere alcuni minuti per registrare il dispositivo per la gestione. Durante l'attesa è possibile eseguire altre operazioni sul computer. Al termine della configurazione dell'accesso aziendale viene visualizzato un messaggio relativo al completamento dell'operazione.  

## <a name="unverified-profiles"></a>Profili non verificati
Quando si visualizzano i profili di gestione di dispositivi mobili (MDM) installati per il dispositivo macOS, alcuni profili potrebbero presentare uno stato **Non verificato**. Purché il **profilo di gestione** non presenti uno stato **Verificato**, non sarà necessario preoccuparsene.  

È il profilo di gestione a definire la connessione al canale MDM. Purché il profilo di gestione sia verificato, tutti gli altri profili distribuiti nel computer tramite tale canale ereditano le caratteristiche di sicurezza del profilo di gestione.

Inoltre, poiché questi altri profili non richiedono verifiche singole, vengono generati e distribuiti più rapidamente nei dispositivi. 

## <a name="updating-the-company-portal-app"></a>Aggiornamento dell'app Portale aziendale

L'aggiornamento dell'app Portale aziendale viene eseguito come quello di qualsiasi altra app di Office, tramite Microsoft AutoUpdate per Mac. Vedere altre informazioni sull'[aggiornamento di app Microsoft per macOS](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Passaggi successivi  
Servono altre informazioni? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  


