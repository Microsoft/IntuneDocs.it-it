---
title: Informazioni su Microsoft Intune | Documentazione Microsoft
description: Informazioni su Intune, il componente per la gestione di dispositivi mobili della soluzione Enterprise Mobility + Security che assicura la protezione dei dati aziendali.
keywords: informazioni su Intune
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: e373fe71f54472bca538ba4a14beff39d090e23d


---

# <a name="what-is-intune"></a>Informazioni su Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune è un servizio di gestione della mobilità aziendale (EMM) basato su cloud che consente alla forza lavoro di essere produttiva, garantendo al tempo stesso la protezione dei dati aziendali. Con Intune, è possibile:
* Gestire i dispositivi mobili usati dalla forza lavoro per accedere ai dati aziendali.
* Gestire le app per dispositivi mobili usate dalla forza lavoro.
* Proteggere le informazioni aziendali grazie alla possibilità di controllare le modalità di accesso e condivisione dei dati da parte della forza lavoro.
* Assicurarsi che i dispositivi e le app siano conformi ai requisiti di sicurezza aziendali.

Intune è integrato con Azure Active Directory (Azure AD) per il controllo delle identità e degli accessi e con Azure Rights Management (Azure RMS) per la protezione dei dati. Costituisce lo *strumento di gestione* di Microsoft Enterprise Mobility + Security (EMS), mentre Office 365 è lo *strumento di produttività* della soluzione di mobilità di Microsoft.  

Insieme, Office 365 e EMS consentono alla forza lavoro di essere produttiva con tutti i dispositivi, garantendo al tempo stesso la protezione delle informazioni aziendali. Office 365 in combinazione con EMS costituisce una suite integrata completa per la mobilità aziendale, con strumenti per la produttività, la gestione delle identità, il controllo degli accessi, la gestione e la protezione dei dati. Rappresenta un metodo efficace per distribuire e gestire una soluzione di mobilità nell'organizzazione.

## <a name="how-does-intune-work"></a>Come funziona Intune?
Intune consente la gestione dei dispositivi mobili (MDM, Mobile Device Management) e la gestione delle app mobili (MAM, Mobile App Management). Le funzionalità MDM e MAM di Intune contribuiscono quindi alla suite EMS con scenari di protezione e conformità dei dati.  

Le modalità di utilizzo delle funzionalità MDM/MAM di Intune e della protezione dei dati EMS variano in base al [problema aziendale da risolvere](#common-business-problems-that-intune-helps-solve). Ad esempio:
* Se si crea un pool di dispositivi a utilizzo singolo da condividere tra gli addetti alla vendita di un negozio, verranno usate maggiormente le funzionalità MDM.
* Sarà necessario fare affidamento sulle funzionalità MAM e di protezione dei dati se si consente alla forza lavoro di usare i propri dispositivi personali per accedere ai dati aziendali (BYOD).  
* Se si dotano gli Information Worker di telefoni aziendali, occorrerà usare in ugual misura entrambe le tecnologie.

## <a name="intune-mobile-device-management-mdm-explained"></a>Spiegazione delle funzionalità di gestione dei dispositivi mobili (MDM) di Intune
Le funzionalità MDM si basano sull'uso dei protocolli o delle API disponibili nei sistemi operativi mobili e includono attività quali:
* Registrazione dei dispositivi nella gestione, in modo che il reparto IT disponga di un inventario dei dispositivi che accedono ai servizi aziendali
* Configurazione dei dispositivi per garantire che soddisfino gli standard di integrità e sicurezza aziendali
* Fornitura di certificati e profili Wi-Fi/VPN per accedere ai servizi aziendali
* Creazione di report e misurazione della conformità dei dispositivi agli standard aziendali
* Rimozione dei dati aziendali dai dispositivi gestiti  

Spesso gli utenti pensano che il **controllo dell'accesso ai dati aziendali** sia una funzionalità MDM. Microsoft non la pensa allo stesso modo dal momento che non è una funzionalità disponibile nei sistemi operativi mobili. Si tratta piuttosto di uno strumento offerto dal provider di identità. In questo caso, il provider di identità è Azure Active Directory (Azure AD), il sistema di gestione dell'accesso e delle identità di Microsoft.  

Intune si integra con Azure AD abilitando una vasta gamma di scenari di controllo dell'accesso. Ad esempio, è possibile richiedere che un dispositivo mobile sia conforme agli standard aziendali, come definito in Intune, prima che il dispositivo possa accedere a un servizio aziendale come Exchange. Analogamente, è possibile bloccare il servizio aziendale a un set specifico di app per dispositivi mobili. Ad esempio, Exchange Online può essere bloccato in modo da essere accessibile solo da Outlook o Outlook Mobile.

## <a name="intune-mobile-app-management-mam-explained"></a>Spiegazione delle funzionalità di gestione delle app mobili (MAM) di Intune
Quando si parla di funzionalità MAM, si intende la serie di operazioni che le soluzioni Microsoft consentono di eseguire ai professionisti IT con le app per dispositivi mobili, ad esempio:
* Pubblicazione delle app per dispositivi mobili per i dipendenti
* Configurazione delle app
* Controllo delle modalità di utilizzo e condivisione dei dati aziendali nelle app per dispositivi mobili
* Rimozione dei dati aziendali dalle app per dispositivi mobili   
* Aggiornamento delle app per dispositivi mobili
* Creazione di report sull'inventario delle app per dispositivi mobili
* Monitoraggio dell'uso delle app per dispositivi mobili

Il termine MAM può indicare una di queste attività singolarmente o specifiche combinazioni di operazioni. In particolare, è normale fondere il concetto di configurazione delle app (vale a dire usando tecnologie come la [configurazione delle app gestite in iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)) con quello di protezione dei dati aziendali all'interno delle app per dispositivi mobili. Ciò avviene perché alcune app per dispositivi mobili espongono impostazioni che consentono la configurazione delle relative funzionalità di protezione dei dati.

Questo aspetto, in combinazione con le funzionalità del sistema operativo per la protezione dei dati (ad esempio, funzionalità MDM come Windows Information Protection in Windows 10), garantisce un livello elevato di protezione per i dati nei dispositivi mobili.

Quando si usa Intune con gli altri servizi di EMS, si assicura all'organizzazione un grado di sicurezza delle app per dispositivi mobili di gran lunga superiore a quello fornito dal sistema operativo mobile e dalle stesse app per dispositivi mobili tramite la configurazione delle app. Un'app gestita con EMS ha accesso a un set più ampio di funzionalità di protezione dei dati e delle app per dispositivi mobili che include:

* [Single Sign-On](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Multi-Factor Authentication](https://docs.microsoft.com/en-us/multi-factor-authentication/multi-factor-authentication)
* [Accesso condizionale all'app (abilitazione dell'accesso se l'app per dispositivi mobili contiene dati aziendali)](https://docs.microsoft.com/en-us/intune/deploy-use/allow-policy-managed-apps-access-to-o365)
* [Isolamento dei dati aziendali da quelli personali all'interno della stessa app](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Criteri di protezione dell'app (PIN, crittografia, salvataggio con nome, Appunti e così via)](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Cancellazione dei dati aziendali da un'app mobile](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Supporto per Rights Management](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-azure-rms)

![Immagine dei livelli di protezione dei dati per la gestione delle app](./media/managing-mobile-apps.png)

### <a name="intune-mobile-app-security"></a>Protezione delle app per dispositivi mobili di Intune
Garantire la protezione delle app fa parte delle funzionalità MAM e quando si parla di sicurezza delle app per dispositivi mobili in Intune si intende:
* Mantenere i dati personali separati dalle informazioni IT aziendali
* Limitare le operazioni che gli utenti possono eseguire con le informazioni aziendali, ad esempio copia, taglia/incolla, salvataggio e visualizzazione
* Rimuovere i dati aziendali dalle app per dispositivi mobili, operazione nota anche come cancellazione selettiva o cancellazione dei dati aziendali

Un modo in cui Intune garantisce la protezione delle app per dispositivi mobili è attraverso la funzionalità dei **criteri di protezione delle app**. I criteri di protezione delle app usano l'identità di Azure AD per isolare i dati aziendali da quelli personali. Ai dati accessibili tramite credenziali aziendali verranno assegnati altri tipi di protezione aziendale.

Quando un utente accede al proprio dispositivo con le sue credenziali aziendali, la relativa identità aziendale consente l'accesso ai dati che non risultano accessibili con l'identità personale. Mano a mano che i dati aziendali vengono usati, Intune, in combinazione con altre tecnologie EMS, controlla le modalità di salvataggio e condivisione. Questi stessi livelli di protezione non vengono applicati ai dati che risultano accessibili quando l'utente accede al proprio dispositivo con la sua identità personale. In questo modo, il reparto IT ha il controllo dei dati aziendali, mentre l'utente finale mantiene il controllo e la riservatezza dei dati personali.

## <a name="emm-with-and-without-device-enrollment"></a>Gestione della mobilità aziendale con e senza registrazione del dispositivo
La maggior parte delle soluzioni di gestione della mobilità aziendale supporta tecnologie di base per i dispositivi mobili e per le app per dispositivi mobili, che sono in genere associate al dispositivo che viene registrato nella soluzione MDM dell'organizzazione. Intune supporta questi scenari, oltre a molti scenari "senza registrazione".  

Le organizzazioni si differenziano a seconda che adottino o meno scenari "senza registrazione". Alcune organizzazioni li adottano come scenari standardizzati. Altre li consentono per i dispositivi complementari, come i tablet personali. Altre non li supportano affatto. Anche in quest'ultimo caso, in cui un'organizzazione richiede che tutti i dispositivi dei dipendenti siano registrati in MDM, queste organizzazioni supportano in genere scenari "senza registrazione" per collaboratori, fornitori e per altri dispositivi che hanno un'esenzione specifica.

È anche possibile usare la tecnologia "senza registrazione" di Intune in dispositivi registrati. Ad esempio, un dispositivo registrato in MDM può avere livelli di protezione Open-In forniti dal sistema operativo mobile. Inoltre, il reparto IT può applicare criteri di protezione delle app alle app per dispositivi mobili gestite da EMS per controllare il salvataggio con nome o per fornire l'autenticazione a più fattori.

Indipendentemente dalla posizione dell'organizzazione sulle app e i dispositivi mobili registrati e non registrati, Intune, come parte di EMS, include strumenti che contribuiranno ad aumentare la produttività della forza lavoro proteggendo al tempo stesso i dati aziendali.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemi aziendali comuni che Intune contribuisce a risolvere
L'elenco seguente di problemi aziendali include collegamenti a informazioni più dettagliate sulle soluzioni offerte. Solo l'ultima voce richiede la registrazione MDM come parte della soluzione:

* [Proteggere dati e messaggi di posta elettronica a livello locale in modo da consentire l'accesso dai dispositivi mobili](common-ways-to-use-intune.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteggere dati e messaggi di posta elettronica di Office 365 in modo da consentire l'accesso sicuro dai dispositivi mobili](common-ways-to-use-intune.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Rilasciare telefoni di proprietà dell'azienda alla forza lavoro](common-ways-to-use-intune.md#issue-corporate-owned-phones-to-your-information-workers)
* [Offrire un programma BYOD (Bring Your Own Device) o per un dispositivo personale a tutti i dipendenti](common-ways-to-use-intune.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Abilitare i dipendenti per l'accesso protetto a Office 365 da un chiosco pubblico non gestito](common-ways-to-use-intune.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Assegnare tablet condivisi con limitazioni d'uso ai task worker](common-ways-to-use-intune.md#issue-limited-use-shared-tablets-to-your-task-workers)

### <a name="next-steps"></a>Passaggi successivi
* Leggere informazioni su alcuni [metodi comuni per l'uso di Intune](common-ways-to-use-intune.md).
* Acquisire familiarità con il prodotto [con una versione di valutazione di 30 giorni di Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md).
* Approfondire i [requisiti tecnici e le funzionalità](/intune/get-started/what-to-know-before-you-start-microsoft-intune) di Intune.



<!--HONumber=Dec16_HO2-->


