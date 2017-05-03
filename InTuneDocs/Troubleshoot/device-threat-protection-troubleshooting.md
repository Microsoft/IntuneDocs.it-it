---
title: Risolvere i problemi di integrazione di Lookout | Documentazione Microsoft
description: Questo argomento descrive la risoluzione dei problemi che si verificano comunemente con l&quot;integrazione di Lookout
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: de2f224f203257fe539196557180f0b5da5d8373
ms.lasthandoff: 04/14/2017


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>Risolvere i problemi di integrazione di Lookout con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento descrive alcuni problemi comuni che possono verificarsi con la configurazione della protezione dalle minacce per dispositivi mobili (MTP, Mobile Threat Protection) di Lookout.

**Errori di accesso**

## <a name="403-errors"></a>Errori 403
Viene visualizzatore l'errore 403 quando si accede alla [console di Lookout MTP](https://aad.lookout.com): **non si è autorizzati ad accedere al servizio** Questa situazione può verificarsi quando il nome utente specificato non è un membro del gruppo di Azure Active Directory (AD) configurato per l'accesso a Lookout MTP.

Lookout MTP consente l'accesso al servizio solo agli utenti di un gruppo di Azure AD configurato. Per determinare il gruppo configurato per l'accesso a Lookout MTP, contattare il servizio di supporto di Lookout:

* Posta elettronica: enterprisesupport@lookout.com
* Accedere alla [console MTP](http://aad.lookout.com) e passare al modulo **Support** (Supporto).
* Andare a https://enterprise.support.lookout.com/hc/requests e inviare una richiesta di supporto.

## <a name="unable-to-sign-in"></a>Impossibile accedere
L'errore seguente viene visualizzato quando l'utente amministratore globale di Azure AD non ha accettato la configurazione iniziale di Lookout.

![screenshot della schermata di accesso a Lookout che mostra l'errore di accesso](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

Per risolvere questo problema, l'utente amministratore globale deve accedere a https://aad.lookout.com/les?action=consent e accettare la richiesta per avviare la configurazione. È possibile trovare informazioni più dettagliate nell'argomento [Configurare la sottoscrizione con Lookout MTP](../deploy-use/set-up-your-subscription-with-lookout-mtp.md)

**Problemi di stato del dispositivo**

## <a name="device-missing-from-lookout-device-list"></a>Dispositivo mancante nell'elenco di dispositivi di Lookout

Ciò potrebbe verificarsi in uno degli scenari seguenti:
* L'utente del dispositivo non è incluso nell'**Enrollment Group** (Gruppo registrazione) specificato nella **console di Lookout MTP**.  Nella [console di Lookout](http://aad.lookout.com) passare a **System** > **Intune Connector** > **Enrollment Management** (Sistema, Connettore Intune, Gestione registrazione).  Controllare i gruppi di Azure AD configurati per la registrazione e verificare che l'utente del dispositivo faccia parte di uno dei gruppi di Azure AD.  Dopo aver aggiunto un utente al gruppo di registrazione, può trascorrere un tempo pari al massimo all'intervallo di polling configurato (per impostazione predefinita 5 minuti) prima che il dispositivo venga visualizzato nel modulo **Devices** (Dispositivi) della console di Lookout MTP.
* Se il dispositivo non è supportato da Lookout MTP.  I dispositivi che sono non supportati verranno visualizzati nella sezione **Managed Devices** (Dispositivi gestiti) delle impostazioni del connettore nella console di Lookout MTP.

### <a name="device-reported-as-pending"></a>Il dispositivo è indicato come **Pending** (In sospeso)

Un dispositivo è indicato come **Pending** (In sospeso) se l'utente finale non ha aperto l'app Lookout for Work e toccato il pulsante **Activate** (Attiva). Per altri dettagli sull'attivazione dei dispositivi con l'app Lookout for Work, vedere [Viene richiesto di installare Lookout for Work nel dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android) o [Richiesta di installare Lookout for Work nel dispositivo iOS](https://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-ios)

## <a name="device-whos-active-but-has-no-device-id"></a>Dispositivo attivo, ma privo di ID dispositivo
Se nella console di Lookout MTP non è disponibile l'ID dispositivo per un dispositivo attivo, significa che l'utente del dispositivo non è incluso nel gruppo di registrazione. Un dispositivo può avere questo stato se l'utente del dispositivo è stato rimosso dal gruppo di registrazione oppure se viene rimosso il gruppo di registrazione.

Nella [console di Lookout](http://aad.lookout.com) passare a **System** > **Intune Connector** > **Enrollment**  (Sistema, Connettore Intune, Registrazione) e controllare le impostazioni.  Controllare i gruppi di Azure AD e verificare che l'utente del dispositivo faccia parte di uno dei gruppi di Azure AD.

Quando un dispositivo è in questo stato, Lookout continuerà a inviare notifica all'utente di eventuali minacce rilevate, ma non invierà alcuna informazione sulle minacce a Intune.

## <a name="device-reported-as-disconnected"></a>Il dispositivo è indicato come **disconnesso**

**Disconnesso** significa che il dispositivo non è stato ancora sincronizzato con Lookout MTP nell'intervallo configurato, ovvero 30 giorni per impostazione predefinita con un minimo di 7 giorni. L'app Portale aziendale o Lookout for Work non è disponibile nel dispositivo. Con la reinstallazione delle app dovrebbe risolversi il problema. Quando l'utente apre Lookout for Work e attiva l'app, il dispositivo si risincronizza con Lookout MTP e Intune.

### <a name="forcing-a-device-sync"></a>Sincronizzazione forzata del dispositivo
Dal modulo **Devices** (Dispositivi) della console di Lookout MTP l'amministratore può selezionare il dispositivo e scegliere di eliminarlo.   Quando il proprietario del dispositivo apre di nuovo l'app Lookout for Work e tocca **Activate** (Attiva), verrà eseguita una risincronizzazione completa dello stato del dispositivo.

## <a name="device-has-a-new-user"></a>Nuovo utente per il dispositivo
È necessario cancellare il dispositivo e chiedere al nuovo utente di eseguire la registrazione.  Dalla [console di amministrazione Intune](https://manage.microsoft.com) selezionare il dispositivo, fare con il pulsante destro del mouse e scegliere **Disattiva/Cancella** per rimuovere il dispositivo dalla gestione. Dopo la disattivazione del dispositivo è possibile eliminarlo.

![screenshot del modulo del dispositivo nella console di amministrazione Intune con l'opzione disattiva/cancella visualizzata](../media/mtp/mtp-retire-device-intune-console.png)

È anche possibile passare al modulo **Devices** (Dispositivi) della [console di Lookout](http://aad.lookout.com) e scegliere **Delete** (Elimina).

Se il nuovo utente è incluso in uno dei gruppi di registrazione di Lookout MTP, il dispositivo verrà visualizzato non appena Azure AD associa il dispositivo al nuovo utente.

## <a name="compliance-remediation-workflows"></a>Flussi di lavoro per risolvere i problemi di conformità
- [Viene richiesto di installare Lookout for Work nel dispositivo Android]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)
- [È necessario risolvere una minaccia rilevata da Lookout for Work nel dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [È necessario risolvere una minaccia rilevata da Lookout for Work nel dispositivo iOS](https://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>Vedere anche
[Configurare la sottoscrizione con Lookout MTP](https://docs.microsoft.com/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)

