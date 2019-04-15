---
title: Metodi comuni per l'uso di Microsoft Intune
description: Informazioni su sei delle attività più comuni che è possibile gestire con Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/29/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32be10340e1e77d2f994c5f038e6328ea42a6303
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57394780"
---
# <a name="common-ways-to-use-microsoft-intune"></a>Metodi comuni per l'uso di Microsoft Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Prima di approfondire le attività di implementazione, è importante che gli utenti della società interessati dalla mobilità aziendale abbiano gli stessi obiettivi di utilizzo di Intune. L'allineamento degli stakeholder è importante sia quando la mobilità aziendale rappresenta una novità, sia quando si esegue la migrazione da un altro prodotto.  

Le esigenze connesse alla mobilità aziendale si evolvono in modo dinamico e l'approccio adottato da Microsoft per soddisfarle in alcuni casi è diverso da quello di altre soluzioni sul mercato. Il modo migliore per conformarsi agli obiettivi aziendali è esprimere i propri obiettivi attraverso scenari da implementare per dipendenti, partner e reparto IT.  

Di seguito sono descritti brevemente i sei scenari più comuni, tutti basati su Intune, e per ogni scenario sono indicati i collegamenti alle informazioni sulla pianificazione e la distribuzione.

>[!NOTE]
>Si vuole sapere come Microsoft IT usa Intune per fornire a Microsoft l'accesso alle risorse aziendali sui propri dispositivi mobili proteggendo allo stesso tempo i dati della società? [Leggere questo case study tecnico](https://www.microsoft.com/itshowcase/Article/Content/588) per vedere in dettaglio in che modo Microsoft IT usa Intune e altri servizi per gestire identità, dispositivi, applicazioni e dati.  

>[!IMPORTANT]
>Alla luce delle recenti infezioni da malware "Trident" sui dispositivi iOS, Microsoft vuole garantire che i dispositivi mobili siano aggiornati. Per questo motivo, è stato pubblicato un post di blog intitolato [Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) (Verifica dell'aggiornamento dei dispositivi mobili con Microsoft Intune), che fornisce informazioni sulle diverse modalità con cui Intune consente di mantenere i dispositivi protetti e aggiornati.

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Protezione di dati e messaggi di posta elettronica a livello locale in modo da consentire l'accesso sicuro dai dispositivi mobili
La maggior parte delle strategie di mobilità aziendale inizia con un piano che consenta l'accesso sicuro alla posta elettronica per i dipendenti che usano dispositivi mobili connessi a Internet. Molte organizzazioni usano ancora server dati e applicazioni locali, come Microsoft Exchange, ospitati nella propria rete aziendale.


Intune e Microsoft Enterprise Mobility + Security (EMS) offrono un'esclusiva [soluzione di accesso condizionale](conditional-access.md) integrata per Exchange Server, per garantire che nessuna app per dispositivi mobili possa accedere alla posta elettronica finché il dispositivo è registrato con Intune, tutto ciò senza la distribuzione di un altro computer del gateway nel perimetro della rete aziendale.

Intune supporta anche l'abilitazione dell'accesso alle applicazioni per dispositivi mobili che richiedono l'accesso protetto ai dati locali, ad esempio i server app line-of-business. Questo tipo di accesso viene in genere eseguito usando [certificati gestiti da Intune](certificates-configure.md) per il controllo di accesso, combinati con un gateway VPN standard o un proxy nel perimetro, ad esempio il proxy di applicazione di Microsoft Azure Active Directory. 

In questi casi, l'unico modo per accedere ai dati aziendali è registrare il dispositivo nel sistema di gestione. Dopo che i dispositivi sono stati registrati, il sistema di gestione garantisce che siano compatibili con i criteri specificati prima di poter accedere ai dati aziendali. In Intune sono anche disponibili lo [strumento di wrapping delle app e App SDK](apps-prepare-mobile-application-management.md) che consentono di contenere i dati a cui si accede all'interno dell'app line-of-business, in modo che non sia possibile passare i dati aziendali alle app o ai servizi consumer.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->


## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Protezione di dati e messaggi di posta elettronica di Office 365 in modo da consentire l'accesso sicuro dai dispositivi mobili
Proteggere i dati aziendali in Office 365 (posta elettronica, documenti, messaggi immediati, contatti) non potrebbe essere più semplice né più trasparente per gli utenti.

Intune e Microsoft Enterprise Mobility + Security offrono un'esclusiva soluzione di accesso condizionale integrata per garantire che nessun utente, app o dispositivo possa accedere ai dati di Office 365 a meno che non soddisfi i requisiti di conformità dell'azienda (esecuzione dell'[autenticazione a più fattori](multi-factor-authentication.md), registrazione con Intune, uso dell'app gestita, versione del sistema operativo supportata, pin del dispositivo, profilo di rischio ridotto e così via).


Le app Office per dispositivi mobili nei rispettivi app store sono predisposte per l'applicazione di criteri per il contenimento dei dati, configurabili in Intune. Ciò consente di impedire la condivisione dei dati con app (ad esempio, con le app di posta elettronica native) e posizioni di archiviazione (ad esempio, Dropbox) che non sono gestite dal reparto IT. Tutte queste funzionalità sono disponibili in Office 365 ed EMS. Non è necessario distribuire un'infrastruttura aggiuntiva per ottenere questo valore.

Una procedura comune per la distribuzione di Office 365 prevede l'obbligo di registrare i dispositivi nel sistema di gestione se richiedono la configurazione completa con configurazioni aziendali per app, certificati, Wi-Fi o VPN, come spesso accade per i dispositivi di proprietà dell'azienda.  


Se tuttavia l'utente deve semplicemente accedere alla posta elettronica e ai documenti aziendali, come spesso accade per i dispositivi personali, è possibile richiedere all'utente di usare le app di Office per dispositivi mobili, a cui sono stati applicati i [criteri di protezione delle app](app-protection-policies.md), ed evitare del tutto la registrazione del dispositivo.  



In entrambi i casi, i dati di Office 365 verranno protetti dai criteri definiti dall'utente.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->


## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>Offrire un programma Bring Your Own Device a tutti i dipendenti
L'approccio Bring Your Own Device (BYOD) è sempre più popolare tra le organizzazioni come mezzo per ridurre le spese di hardware o aumentare la produttività dei dispositivi mobili dei dipendenti. Oggi quasi tutti gli utenti hanno un telefono personale, quindi perché dovrebbero averne un altro? Il problema principale è da sempre convincere i dipendenti a registrare i dispositivi personali nel sistema di gestione, perché temono ciò che il reparto IT sarà in grado di vedere e fare con il loro dispositivo.  

Quando la registrazione del dispositivo non è fattibile, Intune offre un approccio BYOD alternativo che consiste nel [limitare la gestione alle app che contengono dati aziendali](app-protection-policies.md). Intune protegge i dati aziendali anche se l'app in questione accede sia ai dati aziendali che ai dati personali, come avviene per le app Office per dispositivi mobili.  

In qualità di amministratore, è possibile richiedere agli utenti di accedere a Office 365 dalle app Office per dispositivi mobili e di configurare le app con i criteri che assicurano la protezione dei dati (come la crittografia, la protezione con pin e così via). Questi criteri di protezione delle app evitano la perdita di dati in app e posizioni di archiviazione non gestite, all'interno o all'esterno delle app. Ad esempio, i criteri possono impedire a un utente di copiare il testo da un profilo di posta elettronica aziendale in un profilo di posta elettronica personale, anche se entrambi i profili sono configurati all'interno di Outlook Mobile. È possibile distribuire configurazioni simili per altri servizi e applicazioni richiesti dagli utenti BYOD.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-employees"></a>Distribuire telefoni di proprietà dell'azienda ai dipendenti
Oggi molti dipendenti lavorano in modo remoto, per cui i dispositivi mobili sono essenziali per la loro produttività. Questi dipendenti devono accedere senza problemi a tutte le applicazioni e ai dati aziendali in qualsiasi momento, ovunque si trovino. È necessario garantire che i dati aziendali siano protetti e che i costi amministrativi siano contenuti.  

Intune offre [soluzioni per il provisioning e la gestione in blocco](device-enrollment.md) integrate con le principali piattaforme di gestione dei dispositivi aziendali presenti sul mercato, come il Device Enrollment Program di Apple e la piattaforma di sicurezza mobile Samsung Knox. La creazione centralizzata delle configurazioni dei dispositivi con Intune consente di trasformare il provisioning dei dispositivi aziendali in un processo estremamente automatizzato.  

Immaginiamo di dare a un dipendente un iPhone nuovo. Il dipendente accende il dispositivo e viene guidato attraverso una procedura di configurazione personalizzata per l'azienda in cui deve autenticarsi. iPhone è completamente configurato con i [criteri di sicurezza](device-profiles.md).

Quindi, il dipendente avvia l'app Portale aziendale di Intune per accedere alle app aziendali facoltative che sono a sua disposizione.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-employees"></a>Distribuire tablet condivisi con limitazioni d'uso ai dipendenti
I dipendenti usano sempre di più le tecnologie mobili. Ad esempio, oggi è normale vedere gli addetti alla vendita di un negozio che usano tablet condivisi.  Sia che vengano usati per portare a termine una vendita o per controllare rapidamente l'inventario, i tablet consentono di intensificare l'interazione con i clienti.

La semplicità dell'esperienza utente in questo caso è essenziale. Per questo motivo, i tablet vengono forniti in genere ai dipendenti con limitazioni d'uso, che consentono ad esempio al dipendente di interagire con una sola app line-of-business. Intune consente di eseguire il provisioning in blocco e di proteggere e gestire centralmente i dispositivi [iOS e Android](device-profiles.md) condivisi, che possono essere configurati per il funzionamento con queste limitazioni d'uso.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>Abilitare i dipendenti per l'accesso protetto a Office 365 da un chiosco pubblico non gestito
Talvolta i dipendenti devono usare dispositivi, app o browser che non è possibile gestire, ad esempio i computer pubblici disponibili presso le fiere e negli hotel.

In questi casi è opportuno consentire ai dipendenti di accedere alla posta elettronica aziendale? Con Intune e Microsoft Enterprise Mobility + Security, la risposta può essere semplicemente "no",[ limitando l'accesso alla posta elettronica ai dispositivi gestiti dall'organizzazione](conditional-access.md). Ciò assicura che i dipendenti con autenticazione avanzata non lascino accidentalmente i dati aziendali su computer non attendibili.
