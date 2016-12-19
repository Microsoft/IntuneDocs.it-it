---
title: Risolvere i problemi di integrazione di Lookout | Documentazione Microsoft
description: Questo argomento descrive la risoluzione dei problemi che si verificano comunemente con l&quot;integrazione di Lookout
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6ff74f0b46baf384dbdedf13ad75538dd33a089
ms.openlocfilehash: 416f200bdb72bae98897cb8d279dbdb767757da9


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>Risolvere i problemi di integrazione di Lookout con Intune
Questo argomento descrive alcuni problemi comuni che possono verificarsi con la configurazione della protezione dalle minacce per dispositivi mobili (MTP, Mobile Threat Protection) di Lookout.
## <a name="troubleshoot-login-errors"></a>Risolvere i problemi relativi all'accesso
### <a name="403-errors"></a>Errori 403
È possibile che venga visualizzato l'errore 403 quando si accede alla [console di Lookout MTP](https://aad.lookout.com): **non si è autorizzati ad accedere al servizio** Questa situazione può verificarsi quando il nome utente specificato non è un membro del gruppo di Azure Active Directory (Azure AD) configurato per l'accesso a Lookout MTP.

Lookout MTP è configurato per consentire l'accesso solo agli utenti di un gruppo di Azure AD configurato. In caso di dubbi sul gruppo configurato per l'accesso a Lookout MTP, contattare il servizio di supporto di Lookout.

È possibile contattare il servizio di supporto di Lookout tramite i metodi seguenti:

* Posta elettronica: enterprisesupport@lookout.com
* Accedere alla [console MTP](http://aad.lookout.com) e passare al modulo **Support** (Supporto).
* Visitare https://enterprise.support.lookout.com/hc/en-us/requests e registrare una richiesta di supporto.

### <a name="unable-to-sign-in"></a>Impossibile accedere
L'errore seguente può essere visualizzato quando l'utente amministratore globale di Azure AD non ha accettato la configurazione iniziale di Lookout.

![screenshot della schermata di accesso a Lookout che mostra l'errore di accesso](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

Per risolvere questo problema, l'utente amministratore globale deve accedere a https://aad.lookout.com/les?action=consent e accettare la richiesta per avviare la configurazione. È possibile trovare informazioni più dettagliate nell'argomento [Configurare la sottoscrizione con Lookout MTP](../deploy-use/set-up-your-subscription-with-lookout-mtp.md)

## <a name="troubleshoot-device-status-issues"></a>Risolvere i problemi relativi allo stato del dispositivo

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>Il dispositivo non viene visualizzato nell'elenco dei dispositivi nella console di Lookout MTP

Ciò potrebbe verificarsi in uno degli scenari seguenti:
* Quando l'utente proprietario del dispositivo non è incluso nell'**Enrollment Group** (Gruppo registrazione) specificato nella **console di Lookout MTP**.  Dal modulo **System** (Sistema) passare alla scheda **Intune Connector** e cercare le impostazioni **Enrollment Management** (Gestione della registrazione).  Verranno visualizzati uno o più gruppi di Azure AD configurati per la registrazione.  Verificare che l'utente proprietario del dispositivo mancante faccia parte di uno dei gruppi di Azure AD specificati.  Dopo aver aggiunto un nuovo utente al gruppo di registrazione, dovrà trascorrere un tempo pari al massimo all'intervallo di polling configurato (per impostazione predefinita 5 minuti) per visualizzare il dispositivo nel modulo **Devices** (Dispositivi) della console di Lookout MTP.

* Se il dispositivo non è supportato da Lookout MTP.  I dispositivi che sono non supportati verranno visualizzati nella sezione **Managed Devices** (Dispositivi gestiti) delle impostazioni del connettore nella console di Lookout MTP.

### <a name="device-continues-to-be-reported-as-pending"></a>Il dispositivo continua a essere indicato come **Pending** (In sospeso)

Quando un dispositivo è indicato come **Pending** (In sospeso) significa che l'utente finale non ha aperto l'app Lookout for Work e toccato il pulsante **Activate** (Attiva). Per altri dettagli sull'attivazione del dispositivo con l'app Lookout for Work, leggere l'argomento seguente:

[Viene richiesto di installare Lookout for Work nel dispositivo Android ](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>Nella console di Lookout MTP un dispositivo viene visualizzato come attivo, ma non ha un ID di dispositivo.  
Questo significa che l'utente proprietario del dispositivo non è incluso nel gruppo di registrazione specificato nella console di Lookout MTP.   Un dispositivo può avere questo stato se l'utente proprietario viene rimosso dal gruppo di registrazione oppure se viene rimosso il gruppo di registrazione a cui appartiene l'utente.

Dal modulo **System** (Sistema) nella console di Lookout MTP passare alla scheda **Intune Connector** e controllare le impostazioni in **Enrollment** (Registrazione).  Verranno visualizzati uno o più gruppi di Azure AD configurati per la registrazione.  Verificare che l'utente proprietario del dispositivo faccia parte di uno dei gruppi di Azure AD specificati.  

Quando un dispositivo è in questo stato, Lookout continuerà a inviare notifica all'utente di eventuali minacce rilevate, ma non invierà alcuna informazione sulle minacce a Intune.

### <a name="device-shows-disconnected-state"></a>Per il dispositivo viene indicato lo stato disconnesso

Lo stato disconnesso indica che Lookout MTP non ha ricevuto segnali dal dispositivo per un periodo più lungo dell'intervallo di tempo preconfigurato (il valore predefinito è 30 giorni con un minimo di 7 giorni). Ciò significa che l'app Portale aziendale o Lookout for Work non è installata nel dispositivo o è stata disinstallata. Con la reinstallazione delle app dovrebbe risolversi il problema. Quando l'utente apre Lookout for Work e attiva l'app, il dispositivo si risincronizza con Lookout MTP e Intune.    

### <a name="forcing-a-resync-on-the-device"></a>Forzatura della risincronizzazione del dispositivo
Dal modulo **Devices** (Dispositivi) della console di Lookout MTP l'amministratore può selezionare il dispositivo e scegliere di eliminarlo.   Quando il proprietario del dispositivo apre di nuovo l'app Lookout for Work e tocca **Activate** (Attiva), verrà eseguita una risincronizzazione completa dello stato del dispositivo.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>Il proprietario del dispositivo non usa più il dispositivo
È necessario cancellare il dispositivo e chiedere al nuovo utente di eseguire la registrazione.  Dalla [console di amministrazione Intune](https://manage.microsoft.com) selezionare il dispositivo, fare con il pulsante destro del mouse e scegliere **Disattiva/Cancella** per rimuovere il dispositivo dalla gestione. Dopo la disattivazione del dispositivo è possibile eliminarlo.

![screenshot del modulo del dispositivo nella console di amministrazione Intune con l'opzione disattiva/cancella visualizzata](../media/mtp/mtp-retire-device-intune-console.png)

È anche possibile passare al modulo **Devices** (Dispositivi) della console di Lookout MTP e scegliere **Elimina**.  

Fino a quando il nuovo utente è incluso in uno dei gruppi di registrazione specificati nella console di Lookout MTP, il dispositivo verrà visualizzato non appena Azure AD associa il dispositivo al nuovo utente.

## <a name="compliance-remediation-workflows"></a>Flussi di lavoro per risolvere i problemi di conformità
[Viene richiesto di installare Lookout for Work nel dispositivo Android]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[È necessario risolvere una minaccia rilevata da Lookout for Work nel dispositivo Android ](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)


### <a name="see-also"></a>Vedere anche
[Configurare la sottoscrizione con Lookout MTP](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)



<!--HONumber=Dec16_HO2-->


