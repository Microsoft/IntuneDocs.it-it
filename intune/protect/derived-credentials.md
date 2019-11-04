---
title: Usare le credenziali derivate per i dispositivi mobili in Microsoft Intune - Azure | Microsoft Docs
description: Usare le credenziali derivate nei dispositivi mobili come metodo di autenticazione per i profili VPN, di posta elettronica, Wi-Fi, le applicazioni e la crittografia S/MIME di Intune. Le credenziali derivate sono un'implementazione delle linee guida del NIST per la Pubblicazione speciale 800-157.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1716da820fd0d9a4b6d1bbc5024440cfb141c5a1
ms.sourcegitcommit: 0d6f323152ec62f7d383891cce12ea0a4289cd8f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889558"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Usare le credenziali derivate in Microsoft Intune

*Questo articolo si applica ai dispositivi che eseguono iOS*

In un ambiente in cui sono richieste smart card per l'autenticazione o la crittografia e la firma, è ora possibile usare Intune per effettuare il provisioning dei dispositivi mobili con un certificato derivato dalla smart card di un utente. Il certificato viene chiamato *credenziali derivate*. Intune [supporta vari emittenti di credenziali derivate](#supported-issuers), anche se è possibile usare un solo emittente per ogni tenant alla volta. 

Le credenziali derivate sono un'implementazione delle linee guida del National Institute of Standards and Technology (NIST) per le credenziali derivate di verifica dell'identità personale (PIV) come parte della Pubblicazione speciale 800-157.  

**Con l'implementazione di Intune** :  

- L'amministratore di Intune configura il tenant in modo che funzioni con un emittente di credenziali derivate supportato. Non è necessario configurare impostazioni specifiche di Intune nel sistema dell'emittente di credenziali derivate.

- L'amministratore di Intune specifica le **credenziali derivate** come *metodo di autenticazione* per gli oggetti seguenti:  

  - Tipi di profili comuni come Wi-Fi, VPN e posta elettronica, inclusa l'app di posta elettronica nativa iOS 

  - Autenticazione delle app

  - Firma e crittografia S/MIME 

- Gli utenti ottengono le credenziali derivate usando la smart card in un computer per l'autenticazione con l'emittente delle credenziali derivate. L'emittente rilascia quindi al dispositivo mobile un certificato derivato dalla smart card. 

- Dopo che il dispositivo ha ricevuto le credenziali derivate, queste vengono usate per l'autenticazione e per la firma e la crittografia S/MIME quando le app o i profili di accesso alle risorse richiedono le credenziali derivate. 

## <a name="prerequisites"></a>Prerequisiti

Prima di configurare il tenant per l'uso di credenziali derivate, vedere le informazioni seguenti.

### <a name="supported-platforms"></a>Piattaforme supportate

Intune supporta le credenziali derivate nelle piattaforme del sistema operativo seguenti:
- iOS/iPadOS
 
### <a name="supported-issuers"></a>Emittenti supportati

Intune supporta un singolo emittente di credenziali derivate per ogni tenant. È possibile configurare Intune in modo che funzioni con gli emittenti seguenti:  

- **DISA Purebred**: https://cyber.mil/pki-pke/purebred/ 
- **Entrust Datacard**: https://www.entrustdatacard.com/
- **Intercede**: https://www.intercede.com/

Per informazioni dettagliate importanti sull'uso dei diversi emittenti, rivedere le linee guida per l'emittente in questione<!-- , including the issuers end-user workflow-->. Per altre informazioni, vedere [Pianificare l'uso delle credenziali derivate](#plan-for-derived-credentials) in questo articolo.

> [!IMPORTANT]  
> Se si elimina un emittente di credenziali derivate dal tenant, le credenziali derivate configurate tramite tale emittente non funzioneranno più.  
> 
> Vedere [Modificare l'emittente delle credenziali derivate](#change-the-derived-credential-issuer) più avanti in questo articolo.   

### <a name="company-portal-app"></a>App Portale aziendale

Pianificare la distribuzione dell'app Portale aziendale Intune nei dispositivi che si registreranno per le credenziali derivate. Gli utenti del dispositivo usano l'app Portale aziendale per avviare il processo di registrazione delle credenziali. 

Per i dispositivi iOS, vedere [Aggiungere app dello Store iOS a Microsoft Intune](../apps/store-apps-ios.md).

## <a name="plan-for-derived-credentials"></a>Pianificare l'uso delle credenziali derivate

Prima di configurare un'autorità emittente di credenziali derivate, è necessario comprendere le considerazioni seguenti.  

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) Esaminare la documentazione relativa all'emittente delle credenziali derivate prescelto  

Prima di configurare un emittente, rivedere la documentazione dell'emittente per comprendere come il sistema fornisce le credenziali derivate ai dispositivi.  

A seconda dell'emittente scelto, potrebbe essere necessario prevedere la disponibilità di personale al momento della registrazione per aiutare gli utenti a completare il processo. È anche necessario esaminare le configurazioni di Intune correnti per assicurarsi che non blocchino l'accesso necessario per consentire ai dispositivi o agli utenti di completare la richiesta di credenziali. 

Ad esempio, è possibile usare l'accesso condizionale per impedire l'accesso alla posta elettronica per i dispositivi non conformi. Se ci si affida a notifiche tramite posta elettronica per comunicare all'utente di avviare il processo di registrazione delle credenziali derivate, è possibile che gli utenti non ricevano queste istruzioni fino a quando non sono conformi ai criteri.  

Analogamente, alcuni flussi di lavoro delle richieste di credenziali derivate richiedono l'uso della fotocamera del dispositivo per eseguire la scansione di un codice a matrice su schermo. Questo codice collega tale dispositivo alla richiesta di autenticazione avviata per l'emittente delle credenziali derivate con le credenziali della smart card dell'utente. Se i criteri di configurazione del dispositivo bloccano l'uso della fotocamera, l'utente non può completare la richiesta di registrazione delle credenziali derivate.  

Informazioni generali:  

- È possibile configurare un solo emittente per ogni tenant alla volta e tale emittente è disponibile per tutti gli utenti e i dispositivi supportati nel tenant.

- Gli utenti non riceveranno alcuna notifica che devono registrarsi per le credenziali derivate fino a quando non diventano i destinatari di criteri che richiedono credenziali derivate.

- La notifica può avvenire tramite l'app Portale aziendale, tramite posta elettronica o con entrambi i metodi. Se si sceglie di usare le notifiche tramite posta elettronica e si usa l'accesso condizionale abilitato, gli utenti potrebbero non ricevere la notifica tramite posta elettronica se il dispositivo non è conforme.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) Esaminare il flusso di lavoro dell'utente finale per l'emittente prescelto

Di seguito sono riportate alcune considerazioni chiave per ogni partner supportato<!--  , and links to that issuers end-user workflow -->.  Acquisire familiarità con queste informazioni per assicurarsi che i criteri e le configurazioni di Intune non impediscano a utenti e dispositivi di completare correttamente la registrazione delle credenziali derivate da tale emittente.

#### <a name="disa-purebred"></a>DISA Purebred

Informazioni sul flusso di lavoro dell'utente finale e sui requisiti principali:  
<!-- TEMP EDIT - preceeding line to be replaced with the following once user content is ready. 
Review the [user workflow for DISA Purebred](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred). Key requirements for this workflow include:  
-->

- Gli utenti devono accedere a un computer o a un chiosco multimediale in cui possono usare la smart card per l'autenticazione con l'emittente. 

- I dispositivi che eseguiranno la registrazione per le credenziali derivate devono installare l'app Portale aziendale Intune.

- Usare Intune per [distribuire l'app DISA Purebred](#deploy-the-disa-purebred-app) nei dispositivi che si registreranno per le credenziali derivate. Questa app deve essere distribuita tramite Intune in modo che sia gestita e possa quindi interagire con l'app Portale aziendale Intune. Questa app viene usata dagli utenti del dispositivo per completare la richiesta di credenziali derivate. 

- L'app DISA Purebred richiede una [VPN per app](../configuration/vpn-settings-configure.md) per assicurarsi che l'app possa accedere a DISA Purebred durante la registrazione per le credenziali derivate. 

- Gli utenti del dispositivo devono collaborare con un agente attivo durante il processo di registrazione. Durante la registrazione all'utente vengono forniti passcode monouso con un durata limitata man mano che eseguono il processo di registrazione.   

Per informazioni su come ottenere e configurare l'app DISA Purebred, vedere [Distribuire l'app DISA Purebred](#deploy-the-disa-purebred-app) più avanti in questo articolo.  

#### <a name="entrust-datacard"></a>Entrust Datacard  

Informazioni sul flusso di lavoro dell'utente finale e sui requisiti principali:  
<!-- TEMP EDIT - preceeding line to be replaced with the following once user content is ready. 
Review the [user workflow for Entrust Datacard](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust). Key requirements for this workflow include: 
--> 
- Gli utenti devono accedere a un computer o a un chiosco multimediale in cui possono usare la smart card per l'autenticazione con l'emittente. 

- I dispositivi che eseguiranno la registrazione per le credenziali derivate devono installare l'app Portale aziendale Intune.

- Uso della fotocamera di un dispositivo per eseguire la scansione di un codice a matrice che collega la richiesta di autenticazione alla richiesta di credenziali derivate dal dispositivo mobile.

#### <a name="intercede"></a>Intercede

Informazioni sul flusso di lavoro dell'utente finale e sui requisiti principali:  
<!-- TEMP EDIT - preceeding line to be replaced with the following once user content is ready. 
Review the [user workflow for Intercede](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede). Key requirements for this workflow include: 
-->
- Gli utenti devono accedere a un computer o a un chiosco multimediale in cui possono usare la smart card per l'autenticazione con l'emittente. 

- I dispositivi che eseguiranno la registrazione per le credenziali derivate devono installare l'app Portale aziendale Intune.

- Uso della fotocamera di un dispositivo per eseguire la scansione di un codice a matrice che collega la richiesta di autenticazione alla richiesta di credenziali derivate dal dispositivo mobile.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) Distribuire un certificato radice trusted nei dispositivi 

Un certificato radice trusted viene usato con le credenziali derivate per verificare che la catena di certificati delle credenziali derivate sia valida e trusted. Anche se non vi viene fatto riferimento direttamente dai criteri, il certificato radice trusted è richiesto. Vedere [Configurare un profilo certificato per i dispositivi in Microsoft Intune](certificates-configure.md).

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) Fornire istruzioni per gli utenti finali su come ottenere le credenziali derivate 

Creare istruzioni e fornire agli utenti su come avviare il processo di registrazione per le credenziali derivate e spostarsi nel flusso di lavoro di registrazione delle credenziali derivate per l'emittente prescelto. 

Si consiglia di fornire un URL tramite il quale accedere alle istruzioni. Questo URL viene specificato quando si configura l'emittente di credenziali derivate per il tenant e tale URL viene reso disponibile all'interno dell'app Portale aziendale. Se non si specifica un URL personalizzato, Intune fornisce un collegamento a dettagli generici. Questi dettagli non possono coprire tutti gli scenari e potrebbero non essere accurati per l'ambiente in uso. 

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) Distribuire i criteri di Intune che richiedono credenziali derivate 

Creare nuovi criteri o modificare i criteri esistenti per usare le credenziali derivate. Le credenziali derivate sostituiscono altri metodi di autenticazione per l'autenticazione di app, Wi-Fi, VPN, posta elettronica e per la firma e la crittografia S/MIME. 

Evitare di richiedere l'uso di credenziali derivate per accedere a un processo che verrà usato come parte del processo per ottenere le credenziali derivate, in quanto ciò può impedire agli utenti di completare la richiesta. 

## <a name="set-up-a-derived-credential-issuer"></a>Configurare un emittente di credenziali derivate

Prima di creare criteri che richiedono l'uso di credenziali derivate, configurare un emittente di credenziali nella console di Intune. L'emittente di credenziali derivate è un'impostazione a livello di tenant. I tenant supportano un solo emittente alla volta. 

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e passare a **Configurazione del dispositivo** > **Credenziali derivate**.  

   ![Configurare le credenziali derivate nella console](./media/derived-credentials/configure-provider.png)   

2. Specificare un **Nome visualizzato** descrittivo per i criteri dell'emittente di credenziali derivate.  Questo nome non viene visualizzato agli utenti del dispositivo.

3. In **Emittente delle credenziali derivate** selezionare l'emittente di credenziali derivate scelto per il tenant:
   - DISA Purebred
   - Entrust Datacard
   - Intercede  

4. Specificare un **URL della guida per le credenziali derivate** per fornire un collegamento a un percorso che includa istruzioni personalizzate per consentire agli utenti di ottenere le credenziali derivate per l'organizzazione. Le istruzioni devono essere specifiche per l'organizzazione e per il flusso di lavoro necessario per ottenere le credenziali dall'emittente prescelto. Il collegamento viene visualizzato nell'app Portale aziendale e deve essere accessibile dal dispositivo. 

   Se non si specifica un URL personalizzato, Intune fornisce un collegamento a dettagli generici che non possono coprire tutti gli scenari. Queste linee guida generiche potrebbero non essere accurate per l'ambiente in uso.

5. Selezionare una o più opzioni per **Tipo di notifica**. I tipi di notifica sono i metodi usati per informare gli utenti sugli scenari seguenti:

   - Registrare un dispositivo con un emittente per ottenere nuove credenziali derivate. 
   - Ottenere nuove credenziali derivate quando quelle correnti sono vicine alla scadenza. 
   - Usare credenziali derivate con criteri per l'autenticazione Wi-Fi, VPN, di posta elettronica o di app e per la firma e la crittografia S/MIME. 

6. Quando si è pronti, selezionare **Salva** per completare la configurazione dell'emittente delle credenziali derivate. 

Dopo aver salvato la configurazione, è possibile apportare modifiche a tutti i campi, ad eccezione di *Emittente delle credenziali derivate*.  Per modificare l'emittente, vedere [Modificare l'emittente delle credenziali derivate](#change-the-derived-credential-issuer). 

## <a name="deploy-the-disa-purebred-app"></a>Distribuire l'app DISA Purebred

*Questa sezione si applica solo quando si usa DISA Purebred*.

Per usare **DISA Purebred** come emittente di credenziali derivate per Intune, è necessario ottenere l'app DISA Purebred e quindi usare Intune per distribuire l'app nei dispositivi. Gli utenti del dispositivo usano l'app nel dispositivo per richiedere le credenziali derivate da DISA Purebred. 

Oltre a distribuire l'app con Intune, configurare una rete VPN per app di Intune per l'applicazione DISA Purebred. 

**Completare le attività seguenti**: 
  
1. Scaricare l'[applicazione DISA Purebred](https://cyber.mil/pki-pke/purebred/).
2. Distribuire l'applicazione DISA Purebred in Intune.  Vedere [Aggiungere un'app line-of-business per iOS a Microsoft Intune](../apps/lob-apps-ios.md).
3. [Creare una VPN per app](../configuration/vpn-settings-configure.md) per l'applicazione DISA Purebred.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>Usare credenziali derivate per l'autenticazione e per la firma e la crittografia S/MIME

È possibile specificare **Credenziale derivata** per i tipi di profilo e gli scopi seguenti:  
- [Applicazioni](#use-derived-credentials-for-app-authentication)
- [Posta elettronica](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [Firma e crittografia S/MIME](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  Per i profili Wi-Fi, *Metodo di autenticazione* è disponibile solo quando l'opzione **Tipo EAP** è impostata su uno dei valori seguenti: 
  - EAP - TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>Usare le credenziali derivate per l'autenticazione di app

Usare le credenziali derivate per l'autenticazione basata su certificati per siti e applicazioni Web. Per recapitare le credenziali derivate per l'autenticazione di app, seguire questa procedura nella console di Intune:  

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), passare a **Configurazione del dispositivo** > **Profili** e selezionare **Crea profilo**.

2. Immettere un nome descrittivo per il profilo in **Nome**.

3. Per **Piattaforma**, selezionare **iOS**.

4. Per **Tipo di profilo** selezionare **Credenziale derivata**.

5. Selezionare **OK** e quindi fare clic su **Crea**.

6. Selezionare **Assegnazioni** per scegliere i gruppi che devono ricevere i criteri.
 
Gli utenti ricevono l'app o la notifica tramite posta elettronica in base alle impostazioni specificate durante la configurazione dell'emittente delle credenziali derivate. La notifica informa l'utente di avviare il Portale aziendale in modo che sia possibile elaborare i criteri delle credenziali derivate.

## <a name="renew-a-derived-credential"></a>Rinnovare le credenziali derivate

Le credenziali derivate non possono essere estese o rinnovate. Gli utenti devono invece usare il flusso di lavoro delle richieste di credenziali per richiedere nuove credenziali derivate per il dispositivo.

Se si configurano uno o più metodi per **Tipo di notifica**, Intune invia automaticamente una notifica agli utenti quando le credenziali derivate correnti raggiungono l'80% della durata. La notifica dà indicazione agli utenti di eseguire il processo di richiesta delle credenziali per ottenere nuove credenziali derivate. 

Dopo la ricezione delle nuove credenziali derivate nel dispositivo, i criteri che usano le credenziali derivate vengono ridistribuiti in tale dispositivo. 


## <a name="change-the-derived-credential-issuer"></a>Modificare l'emittente delle credenziali derivate

A livello di tenant, è possibile modificare l'emittente delle credenziali, anche se è supportato un solo emittente per tenant alla volta. 

Dopo aver modificato l'emittente, viene richiesto agli utenti di ottenere nuove credenziali derivate dal nuovo emittente. Questa operazione deve esser eseguita prima di poter usare le credenziali derivate per l'autenticazione.

### <a name="change-the-issuer-for-your-tenant"></a>Modificare l'emittente per il tenant

> [!IMPORTANT]  
> Se si elimina un emittente e si riconfigura immediatamente lo stesso emittente, sarà comunque necessario aggiornare i profili e i dispositivi per l'uso delle credenziali derivate da tale emittente. Le credenziali derivate ottenute prima dell'eliminazione dell'emittente non sono più valide. 

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e passare a **Configurazione del dispositivo** > **Credenziali derivate**.

2. Selezionare **Elimina** per rimuovere l'emittente delle credenziali derivate corrente.

3. Configurare un nuovo emittente. 


### <a name="update-profiles-that-use-derived-credentials"></a>Aggiornare i profili che usano le credenziali derivate

Dopo aver eliminato un emittente e averne aggiunto uno nuovo, modificare ogni profilo che usa le credenziali derivate. Questa regola si applica anche se si ripristina l'emittente precedente. Qualsiasi modifica del profilo attiverà un aggiornamento, inclusa una semplice modifica della *Descrizione* del profilo.

### <a name="update-derived-credentials-on-devices"></a>Aggiornare le credenziali derivate nei dispositivi

Dopo l'eliminazione di un emittente e l'aggiunta di uno nuovo, gli utenti del dispositivo devono richiedere nuove credenziali derivate. Questa regola si applica anche quando si aggiunge lo stesso emittente che è stato rimosso. Il processo per richiedere le nuove credenziali derivate è identico a quello per la registrazione di un nuovo dispositivo o per il rinnovo di credenziali esistenti. 

## <a name="next-steps"></a>Passaggi successivi

[Creare profili di configurazione dei dispositivi](../configuration/device-profile-create.md)


 