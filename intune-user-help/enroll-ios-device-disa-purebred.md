---
title: Registrare un dispositivo iOS o iPados con Portale aziendale Intune e DISA purosangue
description: Informazioni su come registrare un dispositivo iOS o iPados e configurare l'autenticazione delle credenziali derivate con DISA purosangue.
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c484b98466c1418016f4ebc6cc805e412d7891e
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415789"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>Configurare un dispositivo iOS o iPados con Portale aziendale e DISA purosangue  

Registrare il dispositivo nell'app Portale aziendale Intune per ottenere l'accesso protetto per dispositivi mobili alla posta elettronica, ai file e alle app dell'organizzazione. Dopo la registrazione, il dispositivo diventa *gestito*. L'organizzazione può assegnare criteri e app al dispositivo tramite un provider di gestione di dispositivi mobili (MDM), ad esempio Intune.  

Durante la registrazione, si installeranno anche le credenziali derivate nel dispositivo. Per l'organizzazione potrebbe essere necessario usare le credenziali derivate come metodo di autenticazione quando si accede alle risorse o per la firma e la crittografia dei messaggi di posta elettronica. 

È probabile che sia necessario configurare una credenziale derivata se si usa una smart card per:

* Accedi a app scolastiche o aziendali, Wi-Fi e reti private virtuali (VPN)
* Firmare e crittografare i messaggi di posta elettronica dell'Istituto di istruzione o di lavoro usando i certificati  

Contenuto dell'articolo:  

   * Registrare un dispositivo mobile iOS o iPados con Portale aziendale Intune.  
   * Ottenere le credenziali derivate dal provider di credenziali derivate dell'organizzazione, [DISA purosangue](https://cyber.mil/pki-pke/purebred/).  

## <a name="what-are-derived-credentials"></a>Che cosa sono le credenziali derivate?  
Una credenziale derivata è un certificato derivato dalle credenziali della smart card e installato nel dispositivo. Consente di accedere in remoto alle risorse di lavoro, impedendo agli utenti non autorizzati di accedere a informazioni riservate.  

Le credenziali derivate vengono usate per: 
* Autenticare gli studenti e i dipendenti che accedono a app scolastiche o aziendali, Wi-Fi e VPN
* Firma e crittografia di messaggi di posta elettronica scolastici o aziendali con certificati S/MIME

Le credenziali derivate sono un'implementazione delle linee guida del National Institute of Standards and Technology (NIST) per le credenziali derivate di verifica dell'identità personale (PIV) come parte della Pubblicazione speciale 800-157.  

## <a name="prerequisites"></a>Prerequisiti

 Per completare la registrazione, è necessario disporre di:

* La tua scuola o la smart card fornita dal lavoro
* Accesso a un computer o a un chiosco multimediale in cui è possibile accedere con la smart card
* Il dispositivo mobile
* L'app Portale aziendale Intune per iOS e iPados è installata nel dispositivo   

Durante l'installazione sarà inoltre necessario contattare un agente o un rappresentante di razza.      

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
    b. Fare clic su **Apri** per aprire l'app purosangue.  

    ![Schermata di esempio della Portale aziendale configurare la schermata di accesso con smart card per dispositivi mobili.](./media/smart-card-open-disa-purebred.png)  
9. Quando viene richiesto di consentire Portale aziendale di aprire l'app di registrazione purosangue, selezionare **Apri**.   

    ![Screenshot di esempio della richiesta di Portale aziendale per aprire l'app DISA razza.](./media/open-app-prompt-disa-purbred.png)  
10. Quando l'app funziona, collaborare con l'agente di razza aziendale per configurare e scaricare il profilo di configurazione di pre-registrazione di purosangue.   
11. Passare all'app Impostazioni > profili di > **generali** **& gestione dispositivi** > **profilo di installazione** e toccare **Installa**.  
12. Immettere il passcode del dispositivo.  
13. Installare il profilo. Potrebbe essere necessario toccare **Installa** più di una volta per avviare l'installazione. 
14. Tornare all'app per la registrazione di purosangue. Seguire le istruzioni dell'agente per continuare.  
 
15. Dopo aver scaricato il profilo di configurazione, passare all'app Impostazioni > profili di > **generali** **& gestione dispositivi** > **profilo di installazione** e toccare **Installa**.   
16.  Immettere il passcode del dispositivo.
17. Installare il profilo. Potrebbe essere necessario toccare **Installa** più di una volta per avviare l'installazione. 
18. Al termine dell'installazione, tornare all'app Portale aziendale.  
19.  Nella schermata **Configura accesso alla smart card per dispositivi mobili** toccare **continua**.  

20. Dalla schermata **Importa certificati** è possibile recuperare e importare le credenziali derivate ottenute da DISA purosangue.  

    a. Toccare **Continua**.   

    ![screenshot di esempio della schermata Portale aziendale set Import Certificates.](./media/import-certificate-disa-purebred.png)  
    b. Passare a iCloud drive **browse** > **locations** e toccare **More locations**.  

    ![screenshot di esempio dell'unità iCloud, scegliere l'opzione Seleziona più posizioni dal menu Sfoglia.](./media/icloud-drive-more-locations.png)  
    c. Toccare l'opzione per abilitare la **catena di chiavi purosangue**.  

    ![Screenshot di esempio dell'unità iCloud, visualizzazione Sfoglia, che evidenzia che l'opzione della catena di chiavi purosangue è abilitata.](./media/icloud-drive-enable-purebred-keychain.png)   

    d. Toccare **pacchetto di credenziali purosangue**.  

    ![screenshot di esempio di una schermata iOS con un'opzione selezionabile del pacchetto di credenziali di esempio.](./media/purebred-credential-package.png)  
    f. Viene visualizzato un elenco di certificati. Selezionarne uno e quindi toccare **Importa chiave**.  

    ![Screenshot di esempio di un elenco di certificati selezionabili, con uno già selezionato.](./media/import-purebred-keychain.png) 
21. Tornare all'app Portale aziendale e attendere il completamento della configurazione del dispositivo da parte di Portale aziendale.   

## <a name="next-steps"></a>Passaggi successivi  
Al termine della registrazione, sarà possibile accedere alle risorse di lavoro, ad esempio posta elettronica, Wi-Fi e tutte le app che l'organizzazione rende disponibile. Per ulteriori informazioni su come ottenere, cercare, installare e disinstallare le app nella Portale aziendale vedere:

* [Gestire le app dal sito Web del portale aziendale](manage-apps-cpweb.md)  
* [Usare le app gestite nel dispositivo](use-managed-apps-on-your-device-ios.md)  

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
