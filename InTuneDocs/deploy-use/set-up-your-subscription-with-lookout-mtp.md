---
title: Configurare la sottoscrizione con Lookout | Microsoft Intune
description: Questo argomento include informazioni dettagliate su come configurare la protezione dalle minacce per il dispositivo di Lookout.
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: bd22d4d19a8337194d331931995c0bd2321a90c5


---

# <a name="set-up-your-subscription-for-lookout-device-threat-protection"></a>Configurare la sottoscrizione per la protezione dalle minacce per il dispositivo di Lookout
Per preparare la sottoscrizione per il servizio di protezione dalle minacce per il dispositivo di Lookout, il servizio di supporto tecnico di Lookout ((enterprisesupport@lookout.com)) ha bisogno delle informazioni seguenti sulla sottoscrizione di Azure Active Directory (Azure AD). Il tenant di Lookout Mobility Endpoint Security verrà associato alla sottoscrizione di Azure AD per l'integrazione di Lookout con Intune. 

* **ID tenant di Azure AD**
* **ID oggetto gruppo di Azure AD** per l'accesso **completo** alla console di Lookout
* **ID oggetto gruppo di Azure AD** per l'accesso **limitato** alla console di Lookout (facoltativo)

> [!IMPORTANT]
> Un tenant esistente di Lookout Mobile Endpoint Security non ancora associato al tenant di Azure AD non può essere usato per l'integrazione con Azure AD e Intune. Contattare il supporto di Lookout per creare un nuovo tenant di Lookout Mobile Endpoint Security. Usare il nuovo tenant per caricare gli utenti di Azure AD.

Usare la sezione seguente per raccogliere le informazioni che dovranno essere fornite al team di supporto tecnico di Lookout.  

## <a name="get-your-azure-ad-information"></a>Recuperare le informazioni di Azure AD
### <a name="azure-ad-tenant-id"></a>ID tenant di Azure AD
Accedere al [portale di gestione di Azure AD](https://manage.windowsazure.com) e selezionare la propria sottoscrizione. 

![screenshot della pagina di Azure AD con il nome del tenant](../media/mtp/aad_tenant_name.png) Quando si sceglie il nome della sottoscrizione, l'URL risultante include l'ID sottoscrizione.  Se risulta problematico trovare l'ID sottoscrizione, questo [articolo del supporto tecnico Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) include suggerimenti per trovare l'ID sottoscrizione.   
### <a name="azure-ad-group-id"></a>ID gruppo di Azure AD
La console di Lookout supporta 2 livelli di accesso:  
* **Accesso completo:** l'amministratore di Azure AD può creare un gruppo per gli utenti che avranno accesso completo e, facoltativamente, creare un gruppo per gli utenti che avranno accesso limitato.  Solo gli utenti di questi gruppi saranno in grado di accedere alla **console di Lookout**.
* **Accesso limitato:** gli utenti in questo gruppo non avranno alcun accesso a diversi moduli correlati alla configurazione e alla registrazione della console di Lookout e avranno accesso in sola lettura al modulo **Security Policy** (Criteri di sicurezza) della console di Lookout.  

Per altri dettagli sulle autorizzazioni, leggere [questo articolo](https://personal.support.lookout.com/hc/en-us/articles/114094105653) nel sito Web di Lookout.

L'**ID oggetto gruppo** è reperibile nella pagina **Proprietà** del gruppo nella **console di gestione di Azure AD**.

![screenshot della pagina delle proprietà con il campo ID oggetto evidenziato](../media/mtp/aad_group_object_id.png)

Dopo aver raccolto le informazioni, contattare il supporto di Lookout (indirizzo di posta elettronica: enterprisesupport@lookout.com).

Il servizio di supporto tecnico di Lookout collaborerà con il contatto principale dell'utente per il caricamento della sottoscrizione e per creare l'account aziendale per Lookout, usando le informazioni raccolte.


## <a name="configure-your-subscription-with-lookout-device-threat-protection"></a>Configurare la sottoscrizione con la protezione dalle minacce per il dispositivo di Lookout
### <a name="step-1-set-up-your-device-threat-protection"></a>Passaggio 1: configurare la protezione dalle minacce per il dispositivo
Dopo che il servizio di supporto tecnico di Lookout ha creato l'account aziendale per Lookout, è possibile usarlo per accedere alla console di Lookout.   Lookout invierà un messaggio di posta elettronica al contatto principale per l'azienda con un collegamento all'URL di accesso: https://aad.lookout.com/les?action=consent

È necessario usare un account utente con il ruolo di amministratore globale di Azure AD al primo accesso alla console di Lookout, perché queste informazioni sono necessarie per la registrazione del tenant di Azure AD.   Per gli accessi successivi non è necessario che l'utente abbia questo livello di privilegi per Azure AD.  Al primo accesso viene visualizzata una pagina di consenso. Scegliere **Accept** (Accetto) per completare la registrazione.

![screenshot della pagina per il primo accesso alla console di Lookout](../media/mtp/lookout_mtp_initial_login.png) Dopo aver accettato e fornito il consenso, si verrà reindirizzati alla console di Lookout. Gli accessi successivi dopo la registrazione iniziale possono essere eseguiti dall'URL https://aad.lookout.com

In caso di problemi durante l'accesso, vedere l'[articolo dedicato alla risoluzione dei problemi](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration).

I passaggi successivi descrivono le attività da eseguire per completare la configurazione di Lookout nella [console di Lookout](https://aad.lookout.com).

### <a name="step-2-configure-the-intune-connector"></a>Passaggio 2: Configurare Intune Connector

1.  Nella console di Lookout, nel modulo **System** (Sistema), scegliere la scheda **Connectors** (Connettori) e quindi selezionare **Intune**.

  ![screeenshot della console di Lookout con la scheda Connectors (Connettori) aperta e l'opzione Intune evidenziata](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  Nella sezione delle impostazioni di connessione configurare la frequenza di heartbeat in minuti.  Il connettore di Intune è pronto.  

  ![screenshot della scheda delle impostazioni di connessione che mostra la frequenza di heartbeat configurata](../media/mtp/lookout-mtp-connection-settings.png)

### <a name="step-3-configure-enrollment-groups"></a>Passaggio 3: Configurare i gruppi di registrazione
Nella sezione **Enrollment Management** (Gestione della registrazione) definire un set di utenti i cui dispositivi devono essere registrati in Lookout. La procedura consigliata consiste nell'iniziare con un piccolo gruppo di utenti di test e acquisire familiarità con il funzionamento dell'integrazione.  Una volta soddisfatti dei risultati del test, è possibile estendere la registrazione ad altri gruppi di utenti.

Per iniziare con i gruppi di registrazione, definire innanzitutto un gruppo di sicurezza di Azure AD che rappresenta un primo set di utenti valido da registrare nella protezione dalle minacce per il dispositivo di Lookout. Dopo aver creato il gruppo in Azure AD, nella console di Lookout passare alla sezione **Enrollement Management** (Gestione della registrazione) e aggiungere il valore per **Display Name** (Nome visualizzato) relativo al gruppo di sicurezza di Azure AD per la registrazione.

Quando un utente è in un gruppo di registrazione, tutti i dispositivi di tale utente identificati e supportati in Azure AD vengono registrati e sono idonei per l'attivazione nella protezione dalle minacce per il dispositivo di Lookout.  Alla prima apertura dell'app Lookout for Work nel dispositivo supportato, il dispositivo viene attivato in Lookout.

![screenshot della pagina di registrazione di Intune Connector](../media/mtp/lookout-mtp-enrollment.png)

La procedura consigliata prevede l'uso dell'incremento predefinito (5 minuti) per verificare la presenza di nuovi dispositivi.

>[!IMPORTANT]
> Per il nome visualizzato viene fatta distinzione tra maiuscole e minuscole.  Usare il **Nome visualizzato** indicato nella pagina **Proprietà** del gruppo di sicurezza nel portale di Azure. Notare nell'immagine seguente che il nome visualizzato ha le iniziali maiuscole nella pagina **Proprietà** del gruppo di sicurezza.  Nel titolo è tuttavia visualizzato tutto in minuscolo e questa forma non deve essere usata per l'immissione nella console di Lookout.
>![screenshot del portale di Azure, servizio Azure Active Directory, pagina delle proprietà](../media/mtp/aad-group-display-name.png)

La versione corrente presenta le limitazioni seguenti:  
* Non è prevista la convalida dei nomi visualizzati dei gruppi.  Assicurarsi di usare il valore indicato nel campo **NOME VISUALIZZATO** nel portale di Azure per il gruppo di sicurezza di Azure AD.
* La creazione di gruppi all'interno di altri gruppi non è attualmente supportata.  I gruppi di sicurezza di Azure AD specificati devono contenere solo utenti e non gruppi annidati.


### <a name="step-4-configure-state-sync"></a>Passaggio 4: Configurare la sincronizzazione dello stato
Nell'opzione **State Sync** (Sincronizzazione stato) specificare il tipo di dati che deve essere inviato a Intune.  Attualmente, è necessario abilitare sia lo stato del dispositivo che lo stato delle minacce per il corretto funzionamento dell'integrazione di Lookout e Intune.  Queste opzioni sono abilitate per impostazione predefinita.
### <a name="step-5-configure-error-report-email-recipient-information"></a>Passaggio 5: Configurare le informazioni per il destinatario dei report sugli errori tramite posta elettronica
Nella sezione **Error Management** (Gestione degli errori) immettere l'indirizzo di posta elettronica del destinatario dei report sugli errori.

![screenshot della pagina di gestione degli errori di Intune Connector](../media/mtp/lookout-mtp-connector-error-notifications.png)

### <a name="step-6-configure-enrollment-settings"></a>Passaggio 6. Configurare le impostazioni di registrazione
Nel modulo **System** (Sistema), nella pagina **Connectors** (Connettori), specificare il numero di giorni dopo i quali un dispositivo deve essere considerato disconnesso.  I dispositivi disconnessi sono considerati non conformi. L'accesso alle applicazioni aziendali tramite questi dispositivi in base ai criteri di accesso condizionale di Intune è bloccato. È possibile specificare un valore compreso tra 1 e 90 giorni.

![](../media/mtp/lookout-console-enrollment-settings.png)

### <a name="step-7-configure-email-notifications"></a>Passaggio 7: Configurare le notifiche tramite posta elettronica
Per ricevere avvisi relativi alle minacce tramite posta elettronica, accedere alla [console di Lookout](https://aad.lookout.com) con l'account utente che deve ricevere le notifiche. Nella scheda **Preferences** (Preferenze) del modulo **System** (Sistema) scegliere le notifiche desiderate e impostarle su **ON** (Attivato). Salvare le modifiche.

![screenshot della pagina delle preferenze con l'account utente visualizzato](../media/mtp/lookout-mtp-email-notifications.png) Se non si vogliono più ricevere notifiche tramite posta elettronica, impostare le notifiche su **OFF** (Disattivato) e salvare le modifiche.
### <a name="step-8-configure-threat-classification"></a>Passaggio 8: Configurare la classificazione delle minacce
La protezione dalle minacce per il dispositivo di Lookout usa vari tipi di classificazione per le minacce per i dispositivi mobili. Alle [classificazioni delle minacce di Lookout](http://personal.support.lookout.com/hc/en-us/articles/114094130693) sono associati livelli di rischio predefiniti. che possono essere modificati in qualsiasi momento per adattarli ai requisiti aziendali.

![screenshot della pagina dei criteri con minacce e classificazioni](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> I livelli di rischio qui specificati rappresentano un aspetto importante della protezione dalle minacce per il dispositivo perché l'integrazione con Intune calcola la conformità dei dispositivi in base a questi livelli di rischio in fase di esecuzione. In altre parole, l'amministratore di Intune imposta una regola nei criteri per identificare un dispositivo come non conforme se presenta una minaccia attiva con un livello minimo di rischio: alto, medio o basso. Il calcolo di conformità dei dispositivi in Intune dipende direttamente dai criteri di classificazione delle minacce nella protezione dalle minacce per il dispositivo di Lookout.

## <a name="watching-enrollment"></a>Monitoraggio della registrazione
Dopo aver completato la configurazione, la protezione dalle minacce per il dispositivo di Lookout inizia a eseguire il polling di Azure AD per i dispositivi corrispondenti ai gruppi di registrazione specificati.  Le informazioni sui dispositivi registrati sono disponibili nel modulo Devices (Dispositivi).  Per i dispositivi viene visualizzato lo stato iniziale in sospeso.  Lo stato del dispositivo cambia dopo l'installazione, l'apertura e l'attivazione nel dispositivo dell'app Lookout for Work.  Per informazioni dettagliate su come ottenere l'app Lookout for Work nel dispositivo, vedere l'argomento [Configurare e distribuire l'app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md).
## <a name="next-steps"></a>Passaggi successivi
[Abilitare la connessione a Lookout MTP in Intune](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Dec16_HO2-->


