---
title: Glossario di Intune
description: Informazioni su alcuni termini di Microsoft Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 86d00901-fac7-4471-aac2-f1d13a4879b6
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 9ddf972795d9ced6aff6dd01da4469d49f11c951
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-glossary"></a>Glossario di Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="a"></a>A

|||
|-|-|
|Profilo di configurazione dell'app|Configura un'app iOS con [impostazioni specifiche](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune) prima dell'esecuzione.|
|Distribuzione di app|Consente agli utenti di [trovare, scaricare e installare](/intune-classic/deploy-use/deploy-apps) le app necessarie.|
|Monitoraggio delle app|Consente di [esaminare lo stato e le attività recenti](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune) relativi alla distribuzione delle app.|
|Attività di rimozione dei dati di protezione dell'app|[Rimuove i dati dell'app](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) dal dispositivo dell'utente.|
|Criterio di protezione dell'app|Garantisce che le app dell'utente siano conformi ai [criteri di protezione dei dati aziendali](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune).|
|Segnalazione app|Consente di [esaminare i dati cronologici](/intune-classic/deploy-use/understand-microsoft-intune-operations-by-using-reports) sulle attività e lo stato di distribuzione delle app.|
|App SDK|[Microsoft Intune App SDK](/intune/app-sdk) consente di aggiungere funzionalità alle proprie app interne consentendone la gestione tramite i criteri di gestione delle applicazioni mobili di Intune.|
|Azione di disinstallazione delle app|Consente di [disinstallare le app](/intune-classic/deploy-use/deploy-apps) dai dispositivi dell'utente.|
|Strumento di wrapping delle app|[Applicazione della riga di comando](/intune/apps-prepare-mobile-application-management) che crea un wrapper per l'app line-of-business, consentendo quindi all'app di essere gestita dai criteri di gestione delle applicazioni mobili di Intune.|
|Installazione disponibile|Quando si distribuisce un'app con questa azione, l'app viene visualizzata nel portale aziendale e gli utenti possono [installarla su richiesta](/intune-classic/deploy-use/deploy-apps).|
|Portale di Azure|La nuova console per Intune che sarà presto disponibile. [Altre informazioni sul nuovo portale](/intune/what-is-intune).|

## <a name="b"></a>B

|||
|-|-|
|BYOD|[Bring your own device](/intune-classic/get-started/choose-how-to-enroll-devices1). Gli utenti possono installare l'app del portale aziendale di Intune nel dispositivo ed eseguire la registrazione per accedere alle risorse della società come posta elettronica, applicazioni aziendali, dati aziendali e supporto.|

## <a name="c"></a>C

|||
|-|-|
|Profilo certificato|Usare questo tipo di criteri per [proteggere l'accesso alle risorse aziendali](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles) con certificati quando si usano profili Wi-Fi, VPN o di posta elettronica.|
|Spazio di archiviazione nel cloud|Posizione in cui [vengono archiviate](/intune-classic/deploy-use/add-apps#cloud-storage-space) le app o i dati creati relativi alle app.|
|COD|I [dispositivi di proprietà della società](/intune-classic/get-started/choose-how-to-enroll-devices1) possono essere registrati in vari modi, a seconda delle esigenze dell'organizzazione e dei tipi di dispositivi gestiti.|
|Portale aziendale|App o sito Web che consente agli utenti l'[accesso ai dati e alle app aziendali](/intune-classic/get-started/microsoft-intune-company-portal).|
|Criteri di conformità|Assicurarsi che i dispositivi usati per accedere alle app e ai dati aziendali [rispettino alcune regole](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune), come l'uso di un PIN per l'accesso al dispositivo e la crittografia dei dati archiviati nel dispositivo stesso.|
|Applicazioni conformi e non conformi|Parte dei [criteri di configurazione generale](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies), queste impostazioni consentono di definire un elenco di app che gli utenti possono o non possono eseguire. Intune informerà quindi l'utente tramite report relativi al fatto che un'app non conforme è stata installata o eseguita. Per alcune piattaforme, Intune può bloccare l'installazione di un'app non conforme.|
|Accesso condizionale|[Consente l'accesso alla posta elettronica aziendale, a Office 365 e ad altri servizi](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) solo dai dispositivi conformi alle regole impostate.|
|Criteri personalizzati|[Questi criteri vengono usati](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) quando i criteri di configurazione generali non contengono un'impostazione integrata in grado di soddisfare le proprie esigenze. È possibile usare un criterio personalizzato per creare un'impostazione simile ad Apple Configurator o URI OMA.|

## <a name="d"></a>D

|||
|-|-|
|Distribuzione|Azione di invio di un'app o un criterio a un dispositivo o a un utente gestito.|
|Azione di distribuzione|Scelta effettuata quando si [distribuisce un'app](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune). È possibile scegliere di rendere l'installazione dell'app obbligatoria o facoltativa oppure è possibile scegliere di disinstallare l'app.|
|Manager di registrazione dispositivi|Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un singolo account utente. L'account del [manager di registrazione dispositivi](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) è un account speciale di Intune che consente di registrare fino a 1000 dispositivi.|
|Mapping del gruppo di dispositivi|Consente di [aggiungere automaticamente i dispositivi ai gruppi](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune) in base a una categoria di dispositivi (ad esempio, "Personale" o "Vendite") che l'utente o l'utente finale può assegnare al dispositivo.|

## <a name="e"></a>E

|||
|-|-|
|Profilo di posta elettronica|Questi criteri possono essere usati per definire le [impostazioni di accesso alla posta elettronica](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) per client di posta elettronica specifici nei dispositivi mobili, riducendo al minimo le configurazioni che l'utente finale deve eseguire.|
|EMS|Microsoft Enterprise Mobility + Security (in precedenza Enterprise Mobility Suite) mantiene i dati aziendali protetti consentendo agli utenti di [accedere alle app e al contenuto necessari](https://www.microsoft.com/cloud-platform/enterprise-mobility).|
|Utente finale|[Utenti di dispositivi quali telefoni e PC](/intune/end-user-educate) gestiti tramite Intune.|
|Registrazione|Microsoft Intune usa la [registrazione](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune) per gestire i dispositivi e consentire l'accesso alle risorse.|

## <a name="f"></a>F

|||
|-|-|
|FastTrack|[Servizio Microsoft](https://technet.microsoft.com/library/mt228265.aspx) per gli utenti di Intune con 150 licenze in un piano idoneo. Con questo servizio, gli esperti Microsoft collaboreranno con l'utente per l'uso e l'esecuzione di Intune.|

## <a name="g"></a>G

|||
|-|-|
|Gruppi|I gruppi consentono di [raccogliere insieme logicamente gli utenti o i dispositivi](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune). Ad esempio, è possibile creare un gruppo di tutti i PC Windows. È quindi possibile distribuire le app e i criteri a tali gruppi.|

## <a name="h"></a>H

|||
|-|-|
|Strategia ibrida|Configurazione in cui è possibile gestire i dispositivi registrati con Intune [tramite la console di System Center Configuration Manager](/intune-classic/get-started/integration-with-cloud-services).|

## <a name="i"></a>I

|||
|-|-|
|Console di amministrazione di Intune|Console corrente che viene usata per la maggior parte delle operazioni di gestione di Intune.|
|Client software di Intune|Metodo alternativo di [gestione di alcuni PC Windows](/intune-classic/get-started/choose-how-to-manage-devices) per aiutare a scegliere il metodo da usare.|
|Autore del software Intune|Strumento che consente di [definire le app da distribuire e di caricarle nello spazio di archiviazione cloud](/intune-classic/deploy-use/add-apps).|
|Argomento|Consente di visualizzare l'[hardware e il software installato](/intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune) nei dispositivi gestiti.|

## <a name="k"></a>K

|||
|-|-|
|Modalità tutto schermo|Configurata come parte di un [criterio di configurazione generale](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies), questa modalità consente di bloccare i dispositivi. Ad esempio, è possibile configurare un dispositivo di vendita al dettaglio per consentire solo l'esecuzione di un'app.|

## <a name="m"></a>M

|||
|-|-|
|Managed Browser|[Applicazione per Web browser](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies) che è possibile distribuire nell'organizzazione usando Microsoft Intune. Un criterio di Managed Browser consente di configurare un elenco Consenti o Blocca che limita i siti Web che gli utenti di Managed Browser possono visitare.|
|Gestione per applicazioni mobili|[Gestione delle applicazioni mobili](/intune/app-lifecycle) consente di pubblicare, distribuire, configurare, proteggere, monitorare e aggiornare le app mobili degli utenti aziendali.
|Gestione dispositivi mobili|[Gestione dei dispositivi mobili](/intune/device-lifecycle) consente di registrare i dispositivi in Intune per poter configurare, monitorare, eseguire il provisioning ed eseguire operazioni su tali dispositivi.
|Autorità di gestione dei dispositivi mobili|L'[autorità di gestione dei dispositivi mobili](/intune-classic/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) definisce il servizio di gestione autorizzato a gestire un set di dispositivi. L'autorità di gestione di dispositivi mobili (MDM) prevede due opzioni: l'uso di Intune da solo e l'uso di Configuration Manager con Intune.|
|Criteri di provisioning di app mobili|Criterio di iOS che consente di verificare che i [profili di provisioning](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles) delle app per iOS distribuiti non scadano.|
|Criteri di configurazione delle app mobili|Criterio di iOS usato per [fornire impostazioni ad app per iOS compatibili](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune) quando vengono eseguite, ad esempio, un nome della società o un indirizzo del server.|

## <a name="o"></a>O

|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management. Protocollo di gestione di dispositivi standard di settore usato da molti produttori di hardware per abilitare il controllo delle funzionalità dei dispositivi mobili e dei PC.|
|URI OMA|Open Mobile Alliance Uniform Resource Identifier. Consente di identificare le impostazioni di singoli dispositivi conformi allo standard OMA-DM. Molte di queste impostazioni possono essere usate nei [criteri personalizzati di Intune](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) quando non è disponibile alcuna impostazione predefinita in grado di soddisfare le proprie esigenze.|

## <a name="p"></a>P

|||
|-|-|
|Criteri|[Pacchetto di informazioni](/intune-classic/deploy-use/microsoft-intune-policy-reference) inviato da Intune a un dispositivo. Ad esempio, è possibile distribuire al dispositivo le impostazioni di sicurezza o le informazioni di conformità del dispositivo.|
|Reimpostazione del passcode|Funzionalità di Intune che consente di forzare l'utente finale a [reimpostare il passcode](/intune-classic/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune) sui dispositivi supportati.|

## <a name="r"></a>R

|||
|-|-|
|Blocco remoto|Funzionalità di Intune che consente di [bloccare i dispositivi supportati](/intune-classic/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune), anche se non si è in possesso del dispositivo.|
|Reports|Intune offre una gamma di [report integrati](/intune-classic/deploy-use/understand-microsoft-intune-operations-by-using-reports) che contengono informazioni sui dispositivi gestiti.|
|Installazione richiesta|Quando si distribuisce un'app con questa azione, l'app viene installata nel dispositivo [senza alcun intervento da parte dell'utente](/intune-classic/deploy-use/deploy-apps) (sebbene per alcune piattaforme è possibile che l'utente finale possa dover accettare l'installazione).|
|Requisiti|[Operazione di distribuzione dell'app](/intune-classic/deploy-use/add-apps) che consente di selezionare i requisiti che devono essere soddisfatti in un dispositivo prima dell'installazione dell'app. Ad esempio, può essere necessario specificare la versione del sistema operativo iOS da installare prima dell'installazione dell'app.|

## <a name="s"></a>S

|||
|-|-|
|Cancellazione selettiva|La [cancellazione selettiva](/intune-classic/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune) rimuove solo i dati aziendali, compresi i dati di gestione delle applicazioni mobili, ove applicabile, le impostazioni e i profili di posta elettronica da un dispositivo. La cancellazione selettiva lascia i dati personali dell'utente sul dispositivo.|
|Sottoscrizione|Il contratto immesso consente di accedere a un tenant di Intune.|

## <a name="t"></a>T

|||
|-|-|
|TeamViewer|Applicazione di terze parti che funziona con Intune per fornire [funzionalità di assistenza remota](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-for-windows-pcs) per i PC Windows gestiti con il client software di Intune.|
|Tenant|Una singola istanza del servizio Intune a cui è possibile accedere con una sottoscrizione.|
|Termini e condizioni|Tipo di criteri distribuiti agli utenti che contengono informazioni che gli utenti devono [leggere e accettare](/intune-classic/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune) prima di poter usare il portale aziendale per registrare e accedere al proprio lavoro.|

## <a name="v"></a>V

|||
|-|-|
|App acquistate con Volume Purchase Program|Alcuni App Store consentono di acquistare più licenze per un'app da eseguire nell'azienda. Intune semplifica la gestione delle app [acquistate con questo programma](/intune-classic/deploy-use/manage-volume-purchased-apps-in-microsoft-intune) importando le informazioni di licenza dall'App Store, verificando il numero di licenze usate e impedendo l'installazione di più copie dell'app rispetto a quelle possedute.|
|Profilo VPN|Criteri che distribuiscono le [impostazioni VPN](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune) ai dispositivi gestiti, riducendo al minimo le configurazioni da parte dell'utente.|

## <a name="w"></a>W

|               |                                                                                                                                                                                                                                 |
|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Profilo Wi-Fi | Criteri che distribuiscono le [impostazioni di rete wireless](/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune) ai dispositivi per consentire agli utenti di connettersi alla rete aziendale senza la necessità di conoscere o configurare le impostazioni. |

