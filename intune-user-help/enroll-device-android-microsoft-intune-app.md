---
title: Registrare dispositivi aziendali con l'app Microsoft Intune | Microsoft Docs
description: Descrive come registrare un dispositivo Android aziendale in Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/07/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81c842eb27b1b9131c164ced5aeed86a78a37353
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506286"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Registrare il dispositivo aziendale con l'app Microsoft Intune

Registrare il dispositivo Android aziendale per ottenere accesso sicuro alla posta elettronica, alle app e ad altri dati aziendali resi disponibili dall'organizzazione. L'app Microsoft Intune supporta i dispositivi aziendali che eseguono Android 6.0 e versioni successive. Verrà installata durante la registrazione nei dispositivi nuovi e in quelli in cui vengono ripristinate le impostazioni predefinite. 

Sono disponibili quattro modi per effettuare la registrazione. L'organizzazione deve comunicare quale opzione usare.
 
* NFC (Near Field Communication)  
* Token  
* Codice a matrice   
* Google Zero Touch  

## <a name="enroll-device"></a>Registrare il dispositivo 
Seguire questa procedura per configurare e registrare il dispositivo.  

> [!NOTE]
> La versione di Android o il produttore del dispositivo potrebbero richiedere l'esecuzione di passaggi aggiuntivi non inclusi in questa procedura. Anche i colori e il testo visualizzati negli screenshot potrebbero essere diversi nel dispositivo specifico.  

1. Accendere il dispositivo nuovo o con le impostazioni predefinite ripristinate.  
2. Nella schermata **Benvenuto** selezionare la lingua.   Se è stato indicato di eseguire la registrazione con un codice a matrice o NFC, seguire la procedura corrispondente riportata di seguito.  
     * NFC: toccare con il dispositivo supportato da NFC il dispositivo di un programmatore per connettersi alla rete dell'organizzazione. Seguire le istruzioni visualizzate. Quando si raggiunge la schermata delle condizioni del servizio di Chrome, procedere al passaggio 5.  

     * Codice a matrice: seguire la procedura descritta in [Registrazione con codice a matrice](#qr-code-enrollment).  

     Se si è ricevuta indicazione di usare un altro metodo, procedere al passaggio 3.    

3. Connettersi alla rete Wi-Fi e toccare **AVANTI**. Seguire la procedura corrispondente al metodo di registrazione. 

    * Token: quando si arriva alla schermata di accesso di Google, seguire la procedura in [Registrazione con token](#token-enrollment).  
    * Google Zero Touch: dopo la connessione alla rete Wi-Fi, il dispositivo verrà riconosciuto dall'organizzazione. Procedere al passaggio 4 e seguire le istruzioni visualizzate fino al completamento dell'installazione.    
 
       ![Immagine di esempio della schermata delle condizioni di Google che viene visualizzata se si usa Google Zero Touch, con il pulsante Accept & Continue (Accetta e continua) evidenziato.](./media/google-zero-touch-intune-app-01.png)   
   
4. Esaminare le condizioni di Google. Toccare quindi **ACCEPT & CONTINUE** (Accetta e continua).  

      ![Immagine di esempio della schermata delle condizioni di Google, con il pulsante Accept & Continue (Accetta e continua) evidenziato.](./media/fully-managed-intune-app-04.png)   

6. Esaminare le condizioni d'uso di Chrome. Toccare quindi **ACCEPT & CONTINUE** (Accetta e continua).  

   ![Immagine di esempio della schermata Termini di servizio di Chrome, con il pulsante Accept & Continue (Accetta e continua) evidenziato.](./media/fully-managed-intune-app-06.png)   

7. Nelle schermate di accesso accedere con l'account aziendale o dell'istituto di istruzione.   

    a. Immettere l'indirizzo di posta elettronica e toccare **Avanti**.      
    b. Immettere la password e toccare **Accedi**.  

8. A seconda dei requisiti dell'organizzazione, potrebbe essere richiesto di aggiornare le impostazioni, ad esempio per la schermata di blocco o la crittografia. Se vengono visualizzate queste richieste, toccare **SET** (Imposta) e seguire le istruzioni visualizzate.  

   ![Immagine di esempio della schermata Set up your work phone (Configura telefono aziendale), con il pulsante Set (Imposta) evidenziato.](./media/fully-managed-intune-app-10.png)   

9. Per installare le app aziendali nel dispositivo, toccare **INSTALL** (Installa). Al termine dell'installazione, toccare **NEXT** (Avanti).  

   ![Immagine di esempio della schermata Set up your work phone (Configura telefono aziendale), con il pulsante Install (Installa) evidenziato.](./media/fully-managed-intune-app-11.png)   

10. Toccare **Start (avvia** ) per aprire l'app Microsoft Intune e registrare il dispositivo. 

    ![Immagine di esempio della schermata Set up your work phone (Configura telefono aziendale), con il pulsante Start (Avvia) evidenziato.](./media/fully-managed-intune-app-17.png)   

11. Toccare **accedi** e quindi toccare **Avanti** per avviare la registrazione. Quando viene visualizzato il messaggio che indica che la registrazione è stata completata, toccare **fine**.  

    ![Immagine di esempio relativa alla configurazione dell'accesso, alla schermata di registrazione del dispositivo, all'evidenziazione del pulsante fine.](./media/fully-managed-intune-app-19.png)   

10. Quando viene visualizzato il messaggio che il dispositivo è pronto, toccare **DONE** (Fine).  

    ![Immagine di esempio della schermata Set up your work phone (Configura telefono aziendale), con il pulsante Done (Fine) evidenziato.](./media/fully-managed-intune-app-18.png)   

Se si riscontrano problemi durante l'accesso alle risorse dell'organizzazione, potrebbe essere necessario aggiornare altre impostazioni nel dispositivo. Accedere all'app Microsoft Intune per verificare la disponibilità di aggiornamenti necessari.   


## <a name="qr-code-enrollment"></a>Registrazione con codice a matrice  
In questa sezione verrà eseguita la scansione del codice a matrice fornito dall'azienda.  Al termine, si verrà reindirizzati nuovamente alla procedura per la registrazione del dispositivo.     
  
1. Nella schermata **iniziale** toccare la schermata cinque volte per avviare il programma di configurazione del codice a matrice.  

   ![Immagine di esempio della schermata iniziale di configurazione del dispositivo con evidenziate le istruzioni per toccare lo schermo.](./media/qr-code-intune-app-01.png)  

2. Seguire le istruzioni visualizzate per la connessione alla rete Wi-Fi.  
3. Se il dispositivo non include uno scanner di codici a matrice, le schermate di installazione indicheranno lo stato di avanzamento mentre viene installato uno scanner. Attendere il completamento dell'installazione.  
4. Quando richiesto, eseguire la scansione del codice a matrice del profilo di registrazione fornito dall'organizzazione.  
5. Tornare alla procedura [Registrare il dispositivo](#enroll-device), passaggio 4 per continuare l'installazione.  

## <a name="token-enrollment"></a>Registrazione del token  
In questa sezione si immetterà il token fornito dall'azienda. Al termine, si verrà reindirizzati nuovamente alla procedura per la registrazione del dispositivo.  

1. Nella schermata di accesso a Google, in **Indirizzo email o numero di telefono** digitare **afw#setup**. Toccare **Avanti**. 

   ![Immagine di esempio della schermata di accesso a Google, che mostra che è stato digitato "afw#setup" nel campo.](./media/token-intune-app-01.png)   

2. Scegliere **Installa** per l'app **Android Device Policy**. Proseguire con l'installazione. A seconda del dispositivo, potrebbe essere necessario leggere e accettare condizioni aggiuntive.    

3. Nella schermata **Enroll this device** (Registra dispositivo) selezionare **Next** (Avanti).  

4. Selezionare **Enter code** (Immetti codice).  

5. Nella schermata **Scan or enter code** (Scansione o immissione codice) digitare il codice assegnato dall'organizzazione.  Fare quindi clic su **Avanti**.  

   ![Immagine di esempio della schermata Scan or enter code (Scansione o immissione codice) con evidenziato il pulsante Next (Avanti).](./media/token-intune-app-04.png)  

6. Tornare alla procedura [Registrare il dispositivo](#enroll-device), passaggio 4 per continuare l'installazione.  



## <a name="next-steps"></a>Passaggi successivi   
Serve ancora assistenza? Contattare il supporto tecnico aziendale (accedere al [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per informazioni sul contatto) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.  
