---
title: Registrare un dispositivo iOS o iPados con Portale aziendale Intune e intercedere
description: Informazioni su come registrare un dispositivo iOS o iPados e configurare l'autenticazione delle credenziali derivate con Intercedi.
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
ms.openlocfilehash: 02293b29f8634161582af2348b1cb30039ca3c52
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415711"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-intercede"></a>Configurare il dispositivo iOS o iPados con Portale aziendale e intercedere

Registrare il dispositivo nell'app Portale aziendale Intune per ottenere l'accesso protetto per dispositivi mobili alla posta elettronica, ai file e alle app dell'organizzazione.  Dopo la registrazione, il dispositivo diventa *gestito*. L'organizzazione può assegnare criteri e app al dispositivo tramite un provider di gestione di dispositivi mobili (MDM), ad esempio Intune.  

Durante la registrazione, si installeranno anche le credenziali derivate nel dispositivo. Per l'organizzazione potrebbe essere necessario usare le credenziali derivate come metodo di autenticazione quando si accede alle risorse o per la firma e la crittografia dei messaggi di posta elettronica. 

È probabile che sia necessario configurare una credenziale derivata se si usa una smart card per:

* Accedi a app scolastiche o aziendali, Wi-Fi e reti private virtuali (VPN)
* Firmare e crittografare i messaggi di posta elettronica dell'Istituto di istruzione o di lavoro usando i certificati  

Contenuto dell'articolo:  

* Registrare un dispositivo mobile iOS o iPados con Portale aziendale Intune.  
* Ottenere le credenziali derivate dal provider di credenziali derivate dell'organizzazione, [intercedere](https://www.intercede.com/).   


## <a name="what-are-derived-credentials"></a>Che cosa sono le credenziali derivate?  
Una credenziale derivata è un certificato derivato dalle credenziali della smart card e installato nel dispositivo. Consente di accedere in remoto alle risorse di lavoro, impedendo agli utenti non autorizzati di accedere a informazioni riservate.  

Le credenziali derivate vengono usate per: 
* Autenticare gli studenti e i dipendenti che accedono a app scolastiche o aziendali, Wi-Fi e VPN
* Firma e crittografia di messaggi di posta elettronica scolastici o aziendali con certificati S/MIME  

Le credenziali derivate sono un'implementazione delle linee guida del National Institute of Standards and Technology (NIST) per le credenziali derivate di verifica dell'identità personale (PIV) come parte della Pubblicazione speciale 800-157.  

## <a name="prerequisites"></a>Prerequisiti

 Per completare la registrazione, è necessario disporre di:

* La tua scuola o la smart card fornita dal lavoro
* Accesso a un computer o a un chiosco self-service in cui è possibile accedere con la smart card
* Il dispositivo mobile
* L'app Portale aziendale Intune per iOS e iPados è installata nel dispositivo


## <a name="enroll-device"></a>Registrare il dispositivo  
1. Aprire l'app Portale aziendale per iOS/iPados sul dispositivo mobile e accedere con l'account aziendale.  
2. Annotare il codice visualizzato sullo schermo.  

    ![Immagine di esempio di Portale aziendale app con messaggio e codice sullo schermo.](./media/copy-code-intercede.png)  
1. Passare al dispositivo abilitato per la smart card e passare a https://microsoft.com/devicelogin. 

1. Immettere il codice precedentemente scritto.
 
2. Inserire la smart card per accedere.   

3. Tornare all'app Portale aziendale sul dispositivo mobile e seguire le istruzioni visualizzate per registrare il dispositivo.  
4. Al termine della registrazione, Portale aziendale invierà una notifica per la configurazione della smart card. Toccare la notifica. Se non si riceve una notifica, controllare la posta elettronica.   

    ![Screenshot di esempio della notifica push Portale aziendale nella schermata iniziale del dispositivo.](./media/action-required-in-app-intercede.png)  

5. Nella schermata di **accesso alla smart card per dispositivi mobili** :  
    a. Toccare il collegamento alle istruzioni di configurazione dell'organizzazione. Se l'organizzazione non fornisce istruzioni aggiuntive, verrà inviato a questo articolo.  
    b. Toccare **Begin**.  

    ![Schermata di esempio della Portale aziendale configurare la schermata di accesso con smart card per dispositivi mobili.](./media/smart-card-info-intercede.png)  

6. Passare al dispositivo abilitato per la smart card o al chiosco self-service e aprire l'app MyID. Accedere con le credenziali di lavoro.  
7. Selezionare l'opzione per richiedere l'ID. 
8. Quando viene chiesto quale profilo si vuole usare, selezionare l'opzione per l'attivazione con una credenziale mobile. Viene visualizzato un codice A matrice.  
9. Tornare al dispositivo mobile. Nella schermata Portale aziendale > **ottenere codice** a matrice toccare **continua**.  

    ![Screenshot di esempio della schermata Portale aziendale ottenere codice a matrice.](./media/get-qr-code-intercede.png) 
 
10. Toccare **Usa fotocamera** > **OK**.  

    ![Schermata di esempio di una richiesta di Portale aziendale, che richiede l'autorizzazione per consentire l'accesso alla fotocamera.](./media/allow-cp-camera-access-intercede.png)  

11. Eseguire la scansione dell'immagine del codice a matrice che si trova sul dispositivo abilitato per smart card. 
12. Attendere che Portale aziendale completi la configurazione del dispositivo.  

## <a name="next-steps"></a>Passaggi successivi  
Al termine della registrazione, sarà possibile accedere alle risorse di lavoro, ad esempio posta elettronica, Wi-Fi e tutte le app che l'organizzazione rende disponibile. Per ulteriori informazioni su come ottenere, cercare, installare e disinstallare le app nella Portale aziendale vedere:

* [Gestire le app dal sito Web del portale aziendale](manage-apps-cpweb.md)  
* [Usare le app gestite nel dispositivo](use-managed-apps-on-your-device-ios.md)  

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
