---
title: Glossario di Intune
titleSuffix: Azure portal
description: Informazioni su alcuni termini usati in Microsoft Intune
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 07/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: 6c066dde1c302c647514659b45e17cc5ac186a13
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="microsoft-intune-glossary"></a>Glossario di Microsoft Intune

## <a name="a"></a>A

|||
|-|-|
|Assegnazione delle app|Consente agli utenti di [trovare, scaricare e installare](/intune/app-management) le app necessarie. Era precedentemente denominata *distribuzione di app*.|
|Profilo di configurazione dell'app <br/><br/>Criteri di configurazione delle app|Disponibili per app per dispositivi mobili con configurazioni specifiche del fornitore. Configura un'app [iOS](/intune/app-configuration-policies-use-ios) o [Android](/intune/app-configuration-policies-use-android) con impostazioni specifiche prima dell'esecuzione.|
|Monitoraggio delle app|Consente di [esaminare lo stato e le attività recenti](/intune/apps-monitor) relativi all'assegnazione delle app.|
|Attività di rimozione dei dati di protezione dell'app|[Rimuove i dati dell'app](/intune/app-protection-policies) dal dispositivo dell'utente.|
|Criterio di protezione dell'app|Disponibile per app per dispositivi mobili che si integrano con le tecnologie Enterprise Mobility + Security (EMS). Garantisce che le app dell'utente siano conformi ai [criteri di protezione dei dati aziendali](/intune/app-protection-policies).|
|App SDK|[Microsoft Intune App SDK](/intune/app-sdk) consente di aggiungere funzionalità alle proprie app interne consentendone la gestione tramite i criteri di protezione delle app di Intune.|
|Azione di disinstallazione delle app|Consente di [disinstallare le app](/intune/apps-deploy) dai dispositivi dell'utente.|
|Strumento di wrapping delle app|[Applicazione della riga di comando](/intune/apps-prepare-mobile-application-management) che crea un wrapper per un'app line-of-business, consentendone la gestione tramite i criteri di gestione delle app di Intune.|
|Azione di assegnazione|Scelta effettuata quando si [assegna un'app](/intune/apps-deploy). È possibile scegliere di rendere l'installazione dell'app obbligatoria (richiesta) o facoltativa (disponibile) oppure è possibile scegliere di disinstallare l'app.|
|Installazione disponibile|Quando si assegna un'app con questa azione, l'app viene visualizzata nel portale aziendale e gli utenti possono [installarla su richiesta](/intune/apps-deploy).|
|Portale di Azure|La nuova console per Intune [Altre informazioni](/intune/what-is-intune).|

## <a name="b"></a>B
|||
|-|-|
|BYOD|[Bring your own device](/intune/device-enrollment). Gli utenti possono installare l'app del portale aziendale di Intune nel dispositivo ed eseguire la registrazione per accedere alle risorse della società come posta elettronica, applicazioni aziendali, dati aziendali e supporto.|

## <a name="c"></a>C
|||
|-|-|
|Profilo certificato|Usare questo tipo di criteri per [proteggere l'accesso alle risorse aziendali](/intune/certificates-configure) con certificati quando si usano profili Wi-Fi, VPN o di posta elettronica.|
|COD|I [dispositivi di proprietà della società](/intune/device-enrollment) possono essere registrati in diversi modi, a seconda delle esigenze dell'organizzazione e dei tipi di dispositivi gestiti.|
|Portale aziendale|App o sito Web che consente agli utenti l'[accesso ai dati e alle app aziendali](/intune/company-portal-customize).|
|Criteri di conformità|Assicurarsi che i dispositivi [rispettino alcune regole](/intune/device-compliance), come l'uso di un PIN per l'accesso al dispositivo e la crittografia dei dati archiviati nel dispositivo stesso.|
|Applicazioni conformi e non conformi|Parte di un [profilo di restrizione dei dispositivi](/intune/device-restrictions-configure), queste impostazioni consentono di definire un elenco di app che gli utenti possono o non possono eseguire. Intune informerà quindi l'utente tramite report relativi al fatto che un'app non conforme è stata installata o eseguita. Per alcune piattaforme, Intune può bloccare l'installazione di un'app non conforme.|
|Accesso condizionale|[Consente l'accesso alla posta elettronica aziendale, a Office 365 e ad altri servizi](/intune/conditional-access) solo dai dispositivi conformi alle regole impostate.|
|Criteri personalizzati|[Questi criteri vengono usati](/intune/custom-settings-configure) quando i criteri di configurazione generali non contengono un'impostazione integrata in grado di soddisfare le proprie esigenze. È possibile usare un criterio personalizzato per creare un'impostazione simile ad Apple Configurator o URI OMA.|

## <a name="d"></a>D
|||
|-|-|
|Distribuzione|Azione di invio di un'app o un criterio a un dispositivo o a un utente gestito. Questa azione ora è denominata *assegnazione*.|
|Manager di registrazione dispositivi|Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un singolo account utente. L'account del [manager di registrazione dispositivi](/intune/device-enrollment-program-enroll-ios) è un account speciale di Intune che consente di registrare fino a 1000 dispositivi.|
|Profili di dispositivo|[Questi profili](/intune/device-profile-create) consentono di configurare una vasta gamma di impostazioni di sicurezza, funzionalità e accesso nei dispositivi gestiti.|

## <a name="e"></a>E
|||
|-|-|
|Profilo di posta elettronica|Questi criteri possono essere usati per definire le [impostazioni di accesso alla posta elettronica](/intune/email-settings-configure) nei dispositivi mobili, riducendo al minimo le configurazioni che l'utente finale deve eseguire.|
|EMS|Microsoft Enterprise Mobility + Security (in precedenza Enterprise Mobility Suite) mantiene i dati aziendali protetti consentendo agli utenti di [accedere alle app e al contenuto necessari](https://www.microsoft.com/cloud-platform/enterprise-mobility).|
|Utente finale|[Utenti di dispositivi quali telefoni e PC](/intune/end-user-educate) gestiti tramite Intune.|
|Registrazione|Microsoft Intune usa la [registrazione](/intune/device-enrollment) per gestire i dispositivi e consentire l'accesso alle risorse.|

## <a name="f"></a>F
|||
|-|-|
|FastTrack|[Servizio Microsoft](https://technet.microsoft.com/library/mt228265.aspx) per gli utenti di Intune con 150 licenze in un piano idoneo. Con questo servizio, gli esperti Microsoft possono collaborare con l'utente per l'uso e l'esecuzione di Intune.|

## <a name="g"></a>G
|||
|-|-|
|Gruppi|I gruppi consentono di [raccogliere insieme logicamente gli utenti o i dispositivi](/intune/groups-get-started). Ad esempio, è possibile creare un gruppo di tutti i PC Windows. Sarà quindi possibile assegnare app e profili a questi gruppi.|

## <a name="h"></a>H
|||
|-|-|
|Strategia ibrida|Configurazione in cui è possibile gestire i dispositivi registrati con Intune tramite la console di System Center Configuration Manager.|

## <a name="i"></a>I
|||
|-|-|
|Portale di Azure|Il portale di Azure che viene usato per la maggior parte delle operazioni di gestione di Intune.|
|Client software di Intune|Metodo alternativo di [gestione di alcuni PC Windows](/intune-classic/get-started/choose-how-to-manage-devices) per aiutare a scegliere il metodo da usare.|
|Autore del software Intune|Strumento che consente di [definire le app da distribuire e di caricarle nello spazio di archiviazione cloud](/intune-classic/deploy-use/add-apps).|
|Argomento|Consente di visualizzare l'[hardware e il software installato](/intune/device-inventory) nei dispositivi gestiti.|

## <a name="k"></a>K
|||
|-|-|
|Modalità tutto schermo|Configurata come parte di un [profilo di restrizione dei dispositivi](/intune/device-restrictions-configure), questa modalità consente di bloccare i dispositivi. È ad esempio possibile configurare un dispositivo di vendita al dettaglio per consentire solo l'esecuzione di alcune app.|

## <a name="m"></a>M
|||
|-|-|
|Managed Browser|[Applicazione per Web browser](/intune/app-configuration-managed-browser) che è possibile assegnare nell'organizzazione usando Intune. Un criterio di Managed Browser consente di configurare un elenco Consenti o Blocca che limita i siti Web che gli utenti di Managed Browser possono visitare.|
|Autorità di gestione dei dispositivi mobili|L'[autorità di gestione dei dispositivi mobili](/intune/mdm-authority-set) definisce il servizio di gestione autorizzato a gestire un set di dispositivi. L'autorità di gestione di dispositivi mobili (MDM) prevede due opzioni: l'uso di Intune da solo e l'uso di Configuration Manager con Intune.|
|Criteri di configurazione delle app mobili|Disponibili per app per dispositivi mobili con configurazioni specifiche del fornitore. Ad esempio, un criterio di [iOS](/intune/app-configuration-policies-use-ios) o [Android](/intune/app-configuration-policies-use-android) usato per fornire impostazioni ad app compatibili quando vengono eseguite, ad esempio un nome della società o un indirizzo del server.|
|Criteri di provisioning di app mobili|Criterio di iOS che consente di verificare che i [profili di provisioning](/intune/app-provisioning-profile-ios) delle app per iOS assegnati non scadano.|
|Gestione per applicazioni mobili|[Gestione delle applicazioni mobili](/intune/app-lifecycle) consente di pubblicare, distribuire, configurare, proteggere, monitorare e aggiornare le app mobili degli utenti aziendali.
|Gestione dispositivi mobili|[Gestione dei dispositivi mobili](/intune/device-lifecycle) consente di registrare i dispositivi in Intune per poter configurare, monitorare, eseguire il provisioning e gestire tali dispositivi.



## <a name="o"></a>O
|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management. Protocollo di gestione di dispositivi standard di settore usato da molti produttori di hardware per abilitare il controllo delle funzionalità dei dispositivi mobili e dei PC.|
|URI OMA|Open Mobile Alliance Uniform Resource Identifier. Consente di identificare le impostazioni di singoli dispositivi conformi allo standard OMA-DM. Queste impostazioni possono essere usate nei [profili personalizzati di Intune](/intune/custom-settings-configure) quando non è disponibile alcuna impostazione predefinita in grado di soddisfare le proprie esigenze.|

## <a name="p"></a>P
|||
|-|-|
|Reimpostazione del passcode|Funzionalità di Intune che consente di forzare l'utente finale a [reimpostare il passcode](/intune/device-passcode-reset) sui dispositivi supportati.|

## <a name="r"></a>R
|||
|-|-|
|Blocco remoto|Funzionalità di Intune che consente di [bloccare i dispositivi supportati](/intune/device-remote-lock), anche se non si è in possesso del dispositivo.|
|Installazione richiesta|Quando si assegna un'app con questa azione, non è necessario l'[intervento dell'utente](/intune/apps-deploy) per completare l'installazione. In alcune piattaforme, è possibile che l'utente finale debba accettare l'installazione.|


## <a name="s"></a>S
|||
|-|-|
|Cancellazione selettiva|La [cancellazione selettiva](/intune/device-company-data-remove) rimuove solo i dati aziendali protetti dai criteri di protezione delle app, inclusi le impostazioni e i profili di posta elettronica da un dispositivo. La cancellazione selettiva lascia i dati personali dell'utente sul dispositivo.|
|Sideload|Azione di installazione di un'app line-of-business senza accedervi da un App Store.|
|Sottoscrizione|Il contratto immesso consente di accedere a un tenant di Intune.|

## <a name="t"></a>T
|||
|-|-|
|TeamViewer|Applicazione di terze parti che funziona con Intune per fornire [funzionalità di assistenza remota](/intune/device-profile-android-teamviewer) per il dispositivo Android gestito con Intune.|
|Tenant|Una singola istanza del servizio Intune a cui è possibile accedere con una sottoscrizione.|
|Termini e condizioni|Tipo di criteri assegnati agli utenti che contengono informazioni che gli utenti devono [leggere e accettare](/intune/terms-and-conditions-create) prima di poter usare il portale aziendale per registrarsi e accedere al proprio lavoro.|

## <a name="v"></a>V
|||
|-|-|
|App e libri acquistati con Volume Purchase Program|Alcuni App Store consentono di acquistare più licenze per un'app o un libro da usare nell'azienda. Intune consente di gestire le app e i libri [acquistati tramite questo programma](/intune/vpp-apps). È possibile importare le informazioni sulle licenze dall'App Store, tenere traccia del numero di licenze usate e impedire di installare più copie dell'app rispetto a quelle possedute.|
|Profilo VPN|Criteri che assegnano le [impostazioni VPN](/intune/vpn-settings-configure) ai dispositivi gestiti, riducendo al minimo le configurazioni da parte dell'utente.|

## <a name="w"></a>W
|||
|-|-|
|Profilo Wi-Fi|Criteri che assegnano le [impostazioni di rete wireless](/intune/wi-fi-settings-configure) ai dispositivi per consentire agli utenti di connettersi alla rete aziendale senza la necessità di conoscere o configurare le impostazioni.
