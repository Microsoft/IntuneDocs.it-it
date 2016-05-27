---
# required metadata

title: Metodi comuni per l'uso di Intune | Microsoft Intune
description:
keywords:
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Metodi comuni per l'uso di Intune

Prima di approfondire le attività di implementazione è importante allineare agli obiettivi aziendali gli utenti della società interessati dalla mobilità aziendale.  Questo è importante sia quando la mobilità aziendale rappresenta una novità, sia quando si esegue la migrazione da un altro prodotto.  Le esigenze connesse alla mobilità aziendale si evolvono in modo dinamico e l'approccio adottato da Microsoft per soddisfare queste esigenze in alcuni casi può essere diverso da quello di altre soluzioni sul mercato.  Il modo migliore per conformarsi agli obiettivi aziendali è esprimere ciò che si vuole ottenere attraverso scenari da implementare per dipendenti, partner e personale IT.  Di seguito sono descritti brevemente i 6 scenari più comuni, tutti basati su Intune, e per ogni scenario sono indicati i collegamenti alle informazioni sulla pianificazione e la distribuzione.

>[!NOTE] Si vuole sapere come Microsoft IT usa Intune per consentire ai dipendenti Microsoft di accedere alle risorse aziendali sui propri dispositivi mobili proteggendo allo stesso tempo i dati della società? [Leggere questo case study tecnico](https://www.microsoft.com/itshowcase/Article/Content/588) per vedere in dettaglio in che modo Microsoft IT usa Intune e altri servizi per gestire identità, dispositivi, applicazioni e dati.  

## Protezione di dati e messaggi di posta elettronica a livello locale in modo da consentire l'accesso sicuro dai dispositivi mobili
La maggior parte delle strategie di mobilità aziendale inizia con un piano che consenta l'accesso sicuro alla posta elettronica da Internet ai dipendenti che usano dispositivi mobili. Molte organizzazioni usano ancora server dati e applicazioni locali, come Microsoft Exchange, ospitati nella propria rete aziendale. Intune ed Enterprise Mobility Suite (EMS) offrono un'esclusiva soluzione di accesso condizionale integrata per Exchange Server, che garantisce che nessuna app per dispositivi mobili sia in grado di accedere alla posta elettronica finché il dispositivo è registrato con Intune, senza richiedere la distribuzione di un altro computer gateway al margine della rete aziendale.

Oltre alla posta elettronica, Intune supporta l'abilitazione dell'accesso alle applicazioni per dispositivi mobili che richiedono l'accesso protetto ai dati locali, ad esempio un server app line-of-business.  Questa operazione viene in genere eseguita usando certificati gestiti da Intune per il controllo di accesso combinato con un gateway VPN standard o un proxy nel perimetro, ad esempio il Proxy di applicazione di Microsoft Azure AD.  In questi casi, l'unico modo per accedere ai dati aziendali è registrare il dispositivo nel sistema di gestione.  Eseguita la registrazione, il sistema di gestione garantisce che i dispositivi che accedono ai dati aziendali siano compatibili con i criteri specificati.  È anche disponibile in Intune uno strumento per la disposizione testo per app che consente di contenere i dati a cui si accede all'interno dell'app line-of-business, in modo non sia possibile passare i dati aziendali alle app o ai servizi consumer.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## Protezione di dati e messaggi di posta elettronica di Office 365 in modo da consentire l'accesso sicuro dai dispositivi mobili
Proteggere i dati aziendali in Office 365 (posta elettronica, documenti, messaggi immediati, contatti) non potrebbe essere più semplice né più trasparente per gli utenti. Intune ed Enterprise Mobility Suite offrono un'esclusiva soluzione di accesso condizionale integrata che garantisce che nessun utente, app o dispositivo possa accedere ai dati di Office 365 a meno che non soddisfi i requisiti di conformità dell'azienda (eseguita l'autenticazione a più fattori, registrazione con Intune, uso dell'app gestita, versione del sistema operativo supportata, pin del dispositivo, profilo di rischio ridotto e così via). Le app Office per dispositivi mobili nei rispettivi app store sono predisposte per l'applicazione di criteri per il contenimento dei dati, configurabili in Intune, che consentono di impedire la condivisione dei dati con le app (ad esempio, le app di posta elettronica native) e i percorsi di archiviazione, come Dropbox, che non sono gestiti dall'IT.  Tutte queste funzionalità sono disponibili in Office 365 ed EMS.  Non è necessario distribuire un'infrastruttura aggiuntiva per ottenere questo valore.

Una procedura comune per la distribuzione di Office 365 consiste nell'obbligo di registrare i dispositivi nel sistema di gestione se richiedono il provisioning completo con configurazioni aziendali per app/certificati/Wi-Fi/VPN, come spesso accade per i dispositivi di proprietà dell'azienda.  Se tuttavia l'utente deve semplicemente accedere alla posta elettronica e ai documenti aziendali, come spesso accade per i dispositivi personali, l'utente dovrà usare le app Office per dispositivi mobili, a cui sono stati applicati i criteri di contenimento dei dati, e ignorare completamente la registrazione del dispositivo.  In entrambi i casi, i dati di Office 365 verranno protetti dai criteri definiti dall'utente.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## Offrire un programma BYOD (Bring Your Own Device) a tutti i dipendenti
L'approccio BYOD è sempre più popolare tra le organizzazioni come mezzo per ridurre le spese di hardware o aumentare la produttività dei dispositivi mobili dei dipendenti. Oggi quasi tutti gli utenti hanno un telefono personale, quindi perché dovrebbero averne un altro? Il problema principale è da sempre convincere i dipendenti a registrare i dispositivi personali nel sistema di gestione, perché temono ciò che il reparto IT sarà in grado di vedere e fare con il loro dispositivo.  

Quando la registrazione del dispositivo non è fattibile, Intune offre un approccio BYOD alternativo che consiste nel limitare la gestione alle app che contengono dati aziendali.  Intune protegge i dati aziendali anche se l'app in questione accede sia ai dati aziendali che ai dati personali, come avviene per le app Office per dispositivi mobili.  In qualità di amministratore, l'utente può richiedere agli utenti di accedere a Office 365 dalle app Office per dispositivi mobili e di configurare le app con i criteri che assicurano la protezione dei dati (crittografia, protezione con pin e così via).  Questi criteri evitano la perdita di dati in app non gestite e percorsi di archiviazione, all'interno o all'esterno delle app.  Ad esempio, i criteri impediranno a un utente di copiare il testo da un profilo di posta elettronica aziendale in un profilo di posta elettronica personale, anche se entrambi i profili sono configurati all'interno di Outlook Mobile.  È possibile distribuire configurazioni simili per altri servizi e applicazioni richiesti dagli utenti BYOD.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## Rilasciare telefoni di proprietà dell'azienda agli information worker
La maggior parte degli information worker oggi usa dispositivi mobili, quindi la produttività dei dispositivi mobili è essenziale per essere competitivi.  Questi dipendenti devono accedere senza problemi a tutte le applicazioni e ai dati aziendali in qualsiasi momento, ovunque si trovino.  È necessario garantire che i dati aziendali siano protetti e che i costi amministrativi siano contenuti.  

Intune offre soluzioni per il provisioning e la gestione in blocco integrate con le principali piattaforme di gestione dei dispositivi aziendali presenti sul mercato, come il programma di registrazione del dispositivo mobile di Apple e la piattaforma di sicurezza mobile Samsung KNOX.  La creazione centralizzata delle configurazioni dei dispositivi con Intune trasforma il provisioning dei dispositivi aziendali in un processo estremamente automatizzato.  

Immaginiamo di dare a un dipendente un iPhone nuovo. Il dipendente accende il dispositivo e viene guidato attraverso una procedura di configurazione personalizzata per l'azienda in cui deve autenticarsi. L'iPhone è perfettamente è configurato con criteri di sicurezza (crittografia dell'unità disco rigido, pin del dispositivo e così via), profili di posta elettronica/Wi-Fi/VPN/certificato e un set di app di base. Quindi, il dipendente avvia l'app Portale aziendale di Intune per accedere alle app aziendali facoltative a sua disposizione.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## Rilasciare tablet condivisi con limitazioni d'uso ai task worker
I task worker usano sempre più le tecnologie mobili.  Ad esempio, oggi è normale vedere gli addetti alla vendita di un negozio che usano tablet condivisi.  Sia che usino per portare a termine una vendita o per controllare rapidamente l'inventario, i tablet consentono di intensificare l'interazione con i clienti.  La semplicità dell'esperienza utente in questo caso è essenziale.  Per questo motivo, i tablet usati dai dipendenti in genere presentano delle limitazioni d'uso, ad esempio il dipendente può interagire solo con una singola app line-of-business.  Intune consente di eseguire il provisioning in blocco e di proteggere e gestire centralmente i tablet condivisi, che possono essere configurati in modo da funzionare con limitazioni d'uso.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## Abilitare i dipendenti per l'accesso protetto a Office 365 da un chiosco pubblico non gestito
Talvolta i dipendenti devono usare dispositivi, app o browser che non è possibile gestire, ad esempio i computer pubblici disponibili presso le fiere e gli hotel.  In questi casi è opportuno consentire ai dipendenti di accedere alla posta elettronica aziendale?  Intune ed Enterprise Mobility Suite offrono diverse possibilità.  La risposta può essere semplicemente "no" limitando l'accesso alla posta elettronica ai dispositivi gestiti dall'organizzazione.  In alternativa, è possibile scegliere di consentire un accesso limitato sui computer non attendibili richiedendo l'autenticazione a più fattori e consentendo l'accesso del browser (Outlook Web Access) solo in una modalità in cui i file non possono essere scaricati (ad esempio, gli allegati di posta elettronica).  Ciò assicura che i dipendenti fortemente autenticati non lascino accidentalmente i dati aziendali su computer non attendibili.

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->


<!--HONumber=May16_HO1-->


