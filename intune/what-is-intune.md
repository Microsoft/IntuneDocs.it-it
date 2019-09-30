---
title: Informazioni su Microsoft Intune
description: Informazioni su Microsoft Intune, il componente per la gestione di dispositivi mobili (MDM) e per la gestione di app per dispositivi mobili (MAM) della soluzione Enterprise Mobility + Security che assicura la protezione dei dati aziendali.
keywords: informazioni su Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/20/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2cde4e37889b981decfd18138feeb4edac46c4c8
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "71238256"
---
# <a name="what-is-microsoft-intune"></a>Informazioni su Microsoft Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune è un servizio basato sul cloud nel settore di gestione della mobilità aziendale (EMM) che consente alla forza lavoro di essere produttiva, garantendo al tempo stesso la protezione dei dati aziendali. Analogamente ad altri servizi di Azure, Microsoft Intune è disponibile nel portale di Azure. Con Intune, è possibile:
* Gestire i dispositivi mobili e i PC usati dalla forza lavoro per accedere ai dati aziendali.
* Gestire le app per dispositivi mobili usate dalla forza lavoro.
* Proteggere le informazioni aziendali grazie alla possibilità di controllare le modalità di accesso e condivisione dei dati da parte della forza lavoro.
* Assicurarsi che i dispositivi e le app siano conformi ai requisiti di sicurezza aziendali.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemi aziendali comuni che Intune contribuisce a risolvere

* [Proteggere dati e messaggi di posta elettronica a livello locale in modo da consentire l'accesso dai dispositivi mobili](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteggere dati e messaggi di posta elettronica di Office 365 in modo da consentire l'accesso sicuro dai dispositivi mobili](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Rilasciare telefoni di proprietà dell'azienda alla forza lavoro](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Offrire un programma BYOD (Bring Your Own Device) o per un dispositivo personale a tutti i dipendenti](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Abilitare i dipendenti per l'accesso protetto a Office 365 da un chiosco pubblico non gestito](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Distribuire tablet condivisi con limitazioni d'uso ai dipendenti](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)


## <a name="how-does-intune-work"></a>Come funziona Intune?
Intune è il componente della suite Enterprise Mobility + Security (EMS) di Microsoft che gestisce dispositivi e app per dispositivi mobili. Intune è integrato con altri componenti EMS come Azure Active Directory (Azure AD) per il controllo delle identità e degli accessi e Azure Information Protection per la protezione dei dati. Quando usato con Office 365 consente alla forza lavoro di essere produttiva con tutti i dispositivi, garantendo al tempo stesso la protezione delle informazioni aziendali.

![Immagine dell'architettura di Intune](./media/intunearch_sm.png)

Visualizzare una [versione ingrandita](./media/intunearchitecture.svg) del diagramma dell'architettura di Intune.

Le modalità d'uso delle funzionalità di gestione di dispositivi e app di Intune e della protezione dei dati EMS variano in base al [problema aziendale da risolvere](#common-business-problems-that-intune-helps-solve). Ad esempio:
* Se si crea un pool di dispositivi a utilizzo singolo da condividere tra gli addetti alla vendita di un negozio, verranno usate maggiormente le funzionalità di gestione dei dispositivi.
* Sarà necessario fare affidamento sulle funzionalità di gestione delle app e di protezione dei dati se si consente alla forza lavoro di usare i propri dispositivi personali per accedere ai dati aziendali (BYOD).  
* Se si dotano gli Information Worker di telefoni aziendali, occorrerà usare in ugual misura entrambe le tecnologie.

## <a name="intune-device-management-explained"></a>Descrizione della gestione dei dispositivi in Intune
Le funzionalità di gestione dei dispositivi di Intune si basano sull'uso dei protocolli o delle API disponibili nei sistemi operativi mobili e includono attività quali:
* Registrazione dei dispositivi nella gestione, in modo che il reparto IT disponga di un inventario dei dispositivi che accedono ai servizi aziendali
* Configurazione dei dispositivi per garantire che soddisfino gli standard di integrità e sicurezza aziendali
* Fornitura di certificati e profili Wi-Fi/VPN per accedere ai servizi aziendali
* Creazione di report e misurazione della conformità dei dispositivi agli standard aziendali
* Rimozione dei dati aziendali dai dispositivi gestiti  

Spesso gli utenti pensano che il **controllo di accesso ai dati aziendali** sia una funzionalità di gestione dei dispositivi. Microsoft non la pensa allo stesso modo dal momento che non è una funzionalità disponibile nei sistemi operativi mobili. Si tratta piuttosto di uno strumento offerto dal provider di identità. In questo caso, il provider di identità è Azure Active Directory (Azure AD), il sistema di gestione dell'accesso e delle identità di Microsoft.  

Intune si integra con Azure AD abilitando una vasta gamma di scenari di controllo dell'accesso. Ad esempio, è possibile richiedere che un dispositivo mobile sia conforme agli standard aziendali definiti in Intune prima che il dispositivo possa accedere a un servizio aziendale come Exchange. Analogamente, è possibile bloccare il servizio aziendale a un set specifico di app per dispositivi mobili. Ad esempio, Exchange Online può essere bloccato in modo da essere accessibile solo da Outlook o Outlook Mobile.

## <a name="intune-app-management-explained"></a>Descrizione della gestione delle app in Intune
Quando si parla di gestione delle app, si intendono le attività seguenti:
* Assegnazione delle app per dispositivi mobili ai dipendenti
* Configurazione delle app con le impostazioni standard usate quando viene eseguita l'app
* Controllo delle modalità di utilizzo e condivisione dei dati aziendali nelle app per dispositivi mobili
* Rimozione dei dati aziendali dalle app per dispositivi mobili   
* Aggiornamento delle app
* Creazione di report sull'inventario delle app per dispositivi mobili
* Monitoraggio dell'uso delle app per dispositivi mobili

Il termine Gestione delle app per dispositivi mobili (MAM) può indicare una di queste attività singolarmente o specifiche combinazioni di operazioni. In particolare, è normale combinare il concetto di configurazione delle app con quello di protezione dei dati aziendali all'interno delle app per dispositivi mobili. Ciò avviene perché alcune app per dispositivi mobili espongono impostazioni che consentono la configurazione delle relative funzionalità di protezione dei dati.

Quando si parla di configurazione delle app e di Intune, si fa riferimento in modo specifico a tecnologie come la [configurazione delle app gestite in iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

Quando si usa Intune con gli altri servizi di EMS, si assicura all'organizzazione un grado di sicurezza delle app per dispositivi mobili di gran lunga superiore a quello fornito dal sistema operativo mobile e dalle stesse app per dispositivi mobili tramite la configurazione delle app. Un'app gestita con EMS ha accesso a un set più ampio di funzionalità di protezione dei dati e delle app per dispositivi mobili che include:

* [Single Sign-On](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
* [Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)
* [Accesso condizionale all'app - consentire l'accesso se l'app per dispositivi mobili contiene dati aziendali](app-based-conditional-access-intune.md)
* [Isolamento dei dati aziendali da quelli personali all'interno della stessa app](app-protection-policy.md)
* [Criteri di protezione dell'app (PIN, crittografia, salvataggio con nome, Appunti e così via)](app-protection-policies.md)
* [Cancellazione dei dati aziendali da un'app mobile](apps-selective-wipe.md)
* [Supporto per Rights Management](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Immagine dei livelli di protezione dei dati per la gestione delle app](./media/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Sicurezza delle app di Intune
Garantire la sicurezza delle app fa parte della gestione delle app e quando si parla di sicurezza delle app per dispositivi mobili in Intune si intende:
* Mantenere i dati personali separati dalle informazioni IT aziendali
* Limitare le operazioni che gli utenti possono eseguire con le informazioni aziendali, ad esempio copia, taglia/incolla, salvataggio e visualizzazione
* Rimuovere i dati aziendali dalle app per dispositivi mobili, operazione nota anche come cancellazione selettiva o cancellazione dei dati aziendali

Un modo in cui Intune garantisce la protezione delle app per dispositivi mobili è attraverso la funzionalità dei **criteri di protezione delle app**. I criteri di protezione delle app usano l'identità di Azure AD per isolare i dati aziendali da quelli personali. Ai dati accessibili tramite credenziali aziendali verranno assegnati altri tipi di protezione aziendale.

Ad esempio, quando un utente accede al proprio dispositivo con le proprie credenziali aziendali, la relativa identità aziendale gli consente di accedere ai dati che non risultano accessibili con l'identità personale. Mano a mano che i dati aziendali vengono usati, i criteri di protezione delle app controllano le modalità di salvataggio e condivisione. Questi stessi livelli di protezione non vengono applicati ai dati che risultano accessibili quando l'utente accede al proprio dispositivo con la sua identità personale. In questo modo, il reparto IT ha il controllo dei dati aziendali, mentre l'utente finale mantiene il controllo e la riservatezza dei dati personali.

## <a name="emm-with-and-without-device-enrollment"></a>Gestione della mobilità aziendale con e senza registrazione del dispositivo
La maggior parte delle soluzioni di gestione della mobilità aziendale supporta tecnologie di base per i dispositivi mobili e per le app per dispositivi mobili, che sono in genere associate al dispositivo che viene registrato nella soluzione di gestione dei dispositivi mobili (MDM) dell'organizzazione. Intune supporta questi scenari, oltre a molti scenari "senza registrazione".  

Le organizzazioni si differenziano a seconda che adottino o meno scenari "senza registrazione". Alcune organizzazioni li adottano come scenari standardizzati. Altre li consentono per i dispositivi complementari, come i tablet personali. Altre non li supportano affatto. Anche in quest'ultimo caso, in cui un'organizzazione richiede che tutti i dispositivi dei dipendenti siano registrati in MDM, queste organizzazioni supportano in genere scenari "senza registrazione" per collaboratori, fornitori e altri dispositivi che hanno un'esenzione specifica.

È anche possibile usare la tecnologia "senza registrazione" di Intune in dispositivi registrati. Ad esempio, un dispositivo registrato in MDM può avere livelli di protezione "Open-In" forniti dal sistema operativo mobile. La protezione "Open-In" è una funzionalità di iOS di Apple che limita la possibilità di aprire un documento da un'app, come Outlook, in un'altra app, come Word, a meno che entrambe le app non siano gestite dallo stesso provider MDM. Il reparto IT può anche applicare criteri di protezione delle app alle app per dispositivi mobili gestite da EMS per controllare il salvataggio con nome o per fornire l'autenticazione a più fattori.

Indipendentemente dalla posizione dell'organizzazione sulle app e i dispositivi mobili registrati e non registrati, Intune, come parte di EMS, include strumenti che contribuiranno ad aumentare la produttività della forza lavoro proteggendo al tempo stesso i dati aziendali.

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune nel portale di Azure

Il [portale di Azure](https://portal.azure.com) è l'area in cui è disponibile il servizio Microsoft Intune.

Tra gli elementi in evidenza dell'esperienza di Microsoft Intune nel portale di Azure sono inclusi i seguenti:

- Una console integrata per tutti i componenti Enterprise Mobility + Security (EMS)
- Una console basata su HTML compilata su standard Web
- Supporto dell'API Graph di Microsoft per automatizzare molte azioni
- Gruppi di Azure Active Directory (AD) per garantire compatibilità su tutte le applicazioni Azure
- Supporto per i browser Web più recenti

Per una guida rapida per personalizzare l'esperienza del portale, vedere [Guida introduttiva a Intune nel portale di Azure](get-started-azure.md).

> [!NOTE]
> Se è stata usata una versione precedente di Microsoft Intune, le informazioni seguenti possono rivelarsi utili:
> * [Dove si trovano le funzionalità di Intune in Azure?](ui-changes.md) è un riferimento che descrive i flussi di lavoro specifici e le interfacce utente modificati con lo spostamento in Azure.
> * [Gruppi di Intune classici nel portale di Azure](groups-get-started.md) descrive le implicazioni dello spostamento nei gruppi di sicurezza di Azure Active Directory per la gestione dei gruppi.

### <a name="before-you-start"></a>Prima di iniziare

Per usare Intune nel portale di Azure, è necessario disporre di un account amministrazione e Intune e di un account tenant. Se non si ha un account, [iscriversi per crearne uno](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

### <a name="supported-web-browsers-for-the-azure-portal"></a>Web browser supportati per il portale di Azure

Il portale di Azure può essere eseguito nei più moderni PC, Mac e tablet. I telefoni cellulari non sono supportati.
Attualmente sono supportati i browser seguenti:

- Microsoft Edge (versione più recente)
- Microsoft Internet Explorer 11
- Safari (versione più recente, solo Mac)
- Chrome (versione più recente)
- Firefox (versione più recente)

Per informazioni aggiornate sui browser supportati, vedere il [portale di Azure](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices).

## <a name="next-steps"></a>Passaggi successivi
* Leggere informazioni su alcuni [metodi comuni per l'uso di Intune](common-scenarios.md).
* Acquisire familiarità con il prodotto [con una versione di valutazione di 30 giorni di Intune](free-trial-sign-up.md).
* Approfondire i [requisiti tecnici e le funzionalità](supported-devices-browsers.md) di Intune.
