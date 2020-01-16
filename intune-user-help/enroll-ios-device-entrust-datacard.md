---
title: Registrare un dispositivo iOS o iPados con Portale aziendale Intune e Entrust Datacard
description: Registrare un dispositivo iOS o iPados e configurare l'autenticazione delle credenziali derivate con Entrust Datacard.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: b976e9a47a56c7af1e754f5b5b0162410e278025
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856393"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-entrust-datacard"></a>Configurare un dispositivo iOS o iPados con Portale aziendale e Entrust Datacard

Registrare il dispositivo nell'app Portale aziendale Intune per ottenere l'accesso protetto per dispositivi mobili alla posta elettronica, ai file e alle app dell'organizzazione. Dopo la registrazione, il dispositivo diventa *gestito*. L'organizzazione può assegnare criteri e app al dispositivo tramite un provider di gestione di dispositivi mobili (MDM), ad esempio Intune.  

Durante la registrazione, si installeranno anche le credenziali derivate nel dispositivo. Per l'organizzazione potrebbe essere necessario usare le credenziali derivate come metodo di autenticazione quando si accede alle risorse o per la firma e la crittografia dei messaggi di posta elettronica. 

È probabile che sia necessario configurare una credenziale derivata se si usa una smart card per:  

* Accedi a app scolastiche o aziendali, Wi-Fi e reti private virtuali (VPN)
* Firmare e crittografare i messaggi di posta elettronica dell'Istituto di istruzione o di lavoro usando i certificati  

Contenuto dell'articolo:  

   * Registrare un dispositivo mobile iOS o iPados con Portale aziendale Intune.  
   * Ottenere le credenziali derivate dal provider di credenziali derivate dell'organizzazione [Entrust Datacard](https://www.entrustdatacard.com/).  

### <a name="what-are-derived-credentials"></a>Che cosa sono le credenziali derivate?  
Una credenziale derivata è un certificato derivato dalle credenziali della smart card e installato nel dispositivo. Consente di accedere in remoto alle risorse di lavoro, impedendo agli utenti non autorizzati di accedere a informazioni riservate.  

Le credenziali derivate vengono usate per: 
* Autenticare gli studenti e i dipendenti che accedono a app scolastiche o aziendali, Wi-Fi e VPN
* Firma e crittografia di messaggi di posta elettronica scolastici o aziendali con certificati S/MIME

Le credenziali derivate sono un'implementazione delle linee guida del National Institute of Standards and Technology (NIST) per le credenziali derivate di verifica dell'identità personale (PIV) come parte della Pubblicazione speciale 800-157.  

## <a name="prerequisites"></a>Prerequisiti

 Per completare la registrazione, è necessario disporre di:

* La tua scuola o la smart card fornita dal lavoro
* Accesso a un computer o a un chiosco multimediale in cui è possibile accedere con la smart card
* Dispositivo mobile
* L'app Portale aziendale Intune per iOS e iPados è installata nel dispositivo  


## <a name="enroll-device"></a>Registrare il dispositivo  
1. Aprire l'app Portale aziendale per iOS/iPados sul dispositivo mobile e accedere con l'account aziendale.  

2. Annotare il codice sullo schermo.  

    ![Immagine di esempio di Portale aziendale app con messaggio e codice sullo schermo.](./media/copy-code-intercede.png)   

3. Passare al dispositivo abilitato per la smart card e passare a https://microsoft.com/devicelogin. 
4. Immettere il codice precedentemente scritto.  

    ![Schermata di esempio della richiesta di immissione del codice del sito Web Portale aziendale.](./media/enter-code-intercede.png)   

5. Inserire la smart card per accedere.   
6. Tornare all'app Portale aziendale sul dispositivo mobile e seguire le istruzioni visualizzate per registrare il dispositivo.  
7. Al termine della registrazione, Portale aziendale invierà una notifica per la configurazione della smart card. Toccare la notifica. Se non si riceve una notifica, controllare la posta elettronica.   

    ![Screenshot di esempio della notifica push Portale aziendale nella schermata iniziale del dispositivo.](./media/action-required-in-app-intercede.png)  

8. Nella schermata di **accesso alla smart card per dispositivi mobili** :   
    a. Toccare il collegamento alle istruzioni di configurazione dell'organizzazione. Se l'organizzazione non fornisce istruzioni aggiuntive, verrà inviato a questo articolo.  
    b. Toccare **Begin**.  

    ![Schermata di esempio della Portale aziendale configurare la schermata di accesso con smart card per dispositivi mobili.](./media/smart-card-info-intercede.png)

9. Passare al dispositivo abilitato per la smart card e aprire IdentityGuard. 
10. Individuare l'area di accesso Smart Credential e selezionare il pulsante di accesso.  
11. Quando viene richiesto di selezionare un certificato, selezionare le credenziali della smart card. Quindi selezionare **OK**. 
12. Immettere il PIN della smart card.  
13. Verrà richiesto di scegliere da un elenco di azioni. Selezionare quello che consente di effettuare la registrazione per una credenziale mobile intelligente derivata. Il collegamento o il pulsante potrebbe indicare **che desidero iscrivermi per le credenziali della smart card per dispositivi mobili derivate.**  
14. Selezionare che l'applicazione abilitata per Smart Credential è stata scaricata e installata correttamente. Quindi continuare con la schermata successiva.   
15. Immettere le informazioni sulle credenziali della smart card derivate.  
    a. Per nome identità immettere un nome qualsiasi, ad esempio *Entrust derived cred*.  
    b. Nel menu a discesa selezionare **Entrust IdentityGudard mobile smart Credential**.  
    c. Passare alla schermata successiva. Al suo interno verrà visualizzato un codice a matrice con una password numerica.  

16. Tornare al dispositivo mobile. Nella schermata Portale aziendale > **ottenere codice** a matrice toccare **continua**. 

    ![Screenshot di esempio della schermata Portale aziendale ottenere codice a matrice.](./media/get-qr-code-intercede.png)  
17. Toccare **Usa fotocamera** > **OK**.  

    ![Schermata di esempio di una richiesta di Portale aziendale, che richiede l'autorizzazione per consentire l'accesso alla fotocamera.](./media/allow-cp-camera-access-intercede.png)  
18. Eseguire la scansione dell'immagine del codice a matrice che si trova sul dispositivo abilitato per smart card.  
19. Immettere la password numerica visualizzata sotto il codice a matrice.  

    ![Schermata di esempio della schermata richiesta Portale aziendale password, immettere il campo password.](./media/enter-password-derived-credentials.png)   

20. Attendere che Portale aziendale completi la configurazione del dispositivo.  


## <a name="next-steps"></a>Passaggi successivi  
Al termine della registrazione, sarà possibile accedere alle risorse di lavoro, ad esempio posta elettronica, Wi-Fi e tutte le app che l'organizzazione rende disponibile. Per ulteriori informazioni su come ottenere, cercare, installare e disinstallare le app nella Portale aziendale vedere:

* [Gestire le app dal sito Web del portale aziendale](manage-apps-cpweb.md)  
* [Usare le app gestite nel dispositivo](use-managed-apps-on-your-device-ios.md)  

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  
