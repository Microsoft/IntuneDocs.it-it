---
title: Abilitare BYOD con Microsoft Intune
description: Flusso di lavoro generale per la configurazione di Intune al fine di abilitare una soluzione BYOD (Bring Your Own Device) per l'organizzazione.
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: vlpetros
ms.suite: ems
ms.openlocfilehash: f4e414f3696c64f8ea450394928aa055ad427afd
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="enable-byod-with-intune"></a>Abilitare BYOD con Intune

Questo argomento fornisce un flusso di lavoro generale per la configurazione di Intune al fine di abilitare una soluzione BYOD (Bring Your Own Device) per l'organizzazione. L'attività è organizzata in tre processi e sono disponibili collegamenti alle procedure di supporto.

Il flusso di lavoro è suddiviso nei tre processi seguenti. È possibile personalizzare gli aspetti di ogni processo in base ai requisiti dell'organizzazione.

-   **[Registrare i dispositivi e verificare la conformità](#enroll-devices-and-check-for-compliance) ** descrive come consentire agli utenti di registrare i propri dispositivi personali per la gestione con Intune. Intune gestisce dispositivi iOS, Mac OS, Android e Windows. In questa sezione viene inoltre descritto come distribuire i criteri ai dispositivi e verificare che soddisfino i requisiti di sicurezza di base.

- **[Fornire l'accesso alle risorse aziendali](#provide-access-to-company-resources)** illustra come è possibile consentire agli utenti di accedere alle risorse aziendali in modo semplice e sicuro. Questa operazione viene eseguita distribuendo i profili di accesso ai dispositivi gestiti. In questa sezione viene inoltre spiegato come gestire con Intune le distribuzioni di app acquistate con Volume Purchase Program.

-   **[Proteggere i dati aziendali](#protect-company-data)** offre informazioni utili su come fornire l'accesso condizionale alle risorse aziendali, evitare la perdita di dati e rimuovere le app e i dati aziendali dai dispositivi quando non sono più necessari per il lavoro oppure in caso di furto o smarrimento.

[![Diagramma del flusso di lavoro generale per l'abilitazione di BYOD con Microsoft Intune](./media/workflow-diagram-for-byod.png)](./media/workflow-diagram-for-byod.png)

<!--- > <sup>You can download this infographic at https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup> --->

## <a name="before-you-begin"></a>Prima di iniziare
Prima che gli utenti possano registrare i dispositivi, è innanzitutto necessario preparare il servizio Intune. A tale scopo, [assegnare le licenze agli utenti](licenses-assign.md) e [impostare l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md).

Al tempo stesso, è anche necessario [personalizzare il portale aziendale](company-portal-customize.md). Aggiungere il branding aziendale e fornire agli utenti informazioni sul supporto. Questo consente di creare un'esperienza di registrazione e supporto attendibile per gli utenti. È anche possibile creare [condizioni di utilizzo](terms-and-conditions-create.md) che gli utenti devono accettare prima della registrazione o [restrizioni per i dispositivi](enrollment-restrictions-set.md) per specificare le piattaforme supportate.

## <a name="enroll-devices-and-check-for-compliance"></a>Registrare i dispositivi e verificare la conformità

Dopo aver preparato il servizio Intune, è necessario soddisfare i vari requisiti di registrazione per i diversi tipi di dispositivi da gestire. Il processo di registrazione dei dispositivi per la gestione è immediato, ma varia leggermente a seconda del tipo di dispositivo.

-   **Dispositivi iOS e Mac** Per registrare iPad, iPhone o dispositivi macOS, è necessario [richiedere un certificato push MDM Apple](apple-mdm-push-certificate-get.md). Dopo aver caricato il certificato push MDM in Intune, gli utenti possono [registrare i dispositivi iOS](/intune-user-help/enroll-your-device-in-intune-ios) tramite l'app Portale aziendale e usare il sito Web del portale aziendale per [registrare i dispositivi macOS](/intune-user-help/enroll-your-device-in-intune-macos).

-   **Dispositivi Android** Non è necessario eseguire alcuna operazione per preparare il servizio Intune per la registrazione dei dispositivi Android. Gli utenti possono [registrare i dispositivi Android](/intune-user-help/enroll-your-device-in-intune-android) per la gestione usando l'app Portale aziendale disponibile in Google Play.

-   **Dispositivi Windows Phone e PC** I dispositivi Windows possono essere registrati con configurazione aggiuntiva. Per semplificare l'esperienza degli utenti finali, è possibile abilitare la registrazione automatica per i PC Windows 10 e i dispositivi mobili Windows 10 in Azure Active Directory (AD) Premium. Se non si dispone di Azure AD Premium o se è necessario supportare Windows 8.1, è possibile creare [un alias DNS per il server di registrazione](windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium) per semplificare la registrazione.


### <a name="make-sure-that-managed-devices-meet-basic-security-requirements"></a>Verificare che i dispositivi gestiti soddisfino i requisiti di sicurezza di base

Dopo che gli utenti hanno registrato i dispositivi per la gestione, il personale IT deve assicurarsi che i dispositivi usati per accedere alle app e ai dati aziendali soddisfino i requisiti di sicurezza di base, come l'uso di un PIN per l'accesso ai dispositivi e la crittografia dei dati archiviati nei dispositivi. Un set di regole di questo tipo è definito [criteri di conformità](device-compliance.md).

Quando [si distribuiscono criteri di conformità](device-compliance-get-started.md) a un utente, ogni dispositivo gestito da Intune viene controllati per determinare se soddisfa i requisiti di sicurezza di base definiti come parte dei criteri BYOD. Dopo che un dispositivo è stato valutato per determinarne la conformità ai criteri, il relativo stato viene comunicato a Intune. In alcuni casi, agli utenti potrebbe essere richiesto di correggere le impostazioni, ad esempio il PIN o la crittografia del dispositivo. In altri casi, l'app Portale aziendale notifica semplicemente all'utente le eventuali impostazioni che non soddisfano i criteri.

## <a name="provide-access-to-company-resources"></a>Fornire l'accesso alle risorse aziendali

La maggior parte dei dipendenti vuole accedere nel proprio dispositivo mobile prima di tutto a posta elettronica e documenti aziendali. I dipendenti si aspettano di configurare l'accesso senza procedure complesse e senza doversi rivolgere al supporto tecnico. Con Intune è semplice [creare e distribuire le impostazioni di posta elettronica](email-settings-configure.md) per le app di posta elettronica native preinstallate nei dispositivi mobili.


> [!NOTE]
> Intune supporta la configurazione di profili di posta elettronica Android for Work per le app di posta elettronica Gmail e Nine Work disponibili in Google Play Store.

Intune consente inoltre di controllare e proteggere l'accesso ai dati aziendali locali quando gli utenti lavorano fuori sede. I profili [Wi-Fi](wi-fi-settings-configure.md), [VPN](vpn-settings-configure.md) e di posta elettronica di Intune interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari, per svolgere le loro attività ovunque si trovino. È anche possibile accedere in modo sicuro alle applicazioni Web e ai servizi dell'azienda ospitati in locale e proteggerli usando il proxy per l'applicazione Azure Active Directory e l'accesso condizionale.

### <a name="manage-volume-purchased-apps"></a>Gestire le app acquistate con Volume Purchase Program
Con Intune è molto semplice:
* Importare le informazioni sui contratti multilicenza da qualsiasi App Store
* Tenere traccia del numero di licenze usate
* Impedire agli utenti di installare un numero di copie dell'app superiore al numero di copie acquistate
* [Distribuire app dello Store ai dispositivi gestiti](apps-deploy.md)
* Specificare app di destinazione per i dispositivi non gestiti tramite il sito Web del portale aziendale

Intune consente anche di gestire e distribuire le app acquistate con contratti multilicenza dall'App Store di iOS e da Microsoft Store per le aziende. In questo modo, è possibile ridurre il carico amministrativo associato al monitoraggio delle app acquistate con Volume Purchase Program.

> [!TIP]
> È possibile [configurare Single Sign-On (SSO) con Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). SSO consente agli utenti di accedere alle app con il nome utente e la password di dominio usati in locale. È inoltre possibile [fornire l'accesso basato su Internet alle app Web ospitate in locale](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) usando il proxy dell'applicazione Azure Active Directory.

-   [Gestire le app acquistate tramite Volume Purchase Program per dispositivi iOS](vpp-apps-ios.md). Per acquistare più licenze per app iOS, è necessario usare [Volume Purchase Program di Apple per le aziende](http://www.apple.com/business/vpp/). È necessario configurare un account VPP di Apple dal sito Web Apple e caricare il token VPP di Apple in Intune. È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso delle app acquistate con VPP.

-   [Gestire le app acquistate da Microsoft Store per le aziende](windows-store-for-business.md). In [Microsoft Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Intune, è possibile gestire dal portale di Azure le app acquistate con Volume Purchase Program.

## <a name="protect-company-data"></a>Proteggere i dati aziendali

Intune protegge i dati aziendali tramite diversi livelli di tecnologie. A livello di identità, l'accesso condizionale protegge l'accesso ai servizi. L'accesso condizionale consente l'accesso alle risorse aziendali solo ai dispositivi conformi e gestiti. A livello di app client, i criteri di protezione delle app proteggono dalla perdita di dati. I criteri di protezione delle app impediscono lo spostamento dei dati in app o percorsi di archiviazione non protetti. Questi criteri consentono inoltre di cancellare i dati aziendali quando un dispositivo viene smarrito o rubato.

### <a name="enforce-conditional-access-to-company-resources"></a>Imporre l'accesso condizionale alle risorse aziendali

È possibile combinare criteri di conformità con [criteri di accesso condizionale](device-compliance.md) per verificare se i dispositivi soddisfano i requisiti di sicurezza di base definiti dai criteri BYOD. Se un dispositivo non soddisfa i requisiti, le regole vengono applicate e viene negato l'accesso finché il dispositivo non soddisfa i requisiti dei criteri. In questo modo si ha la certezza che solo i dispositivi gestiti e conformi possano accedere ai dati aziendali da servizi come Exchange ([Exchange locale](exchange-connector-install.md) o [Exchange Online](conditional-access-exchange-create.md)), SharePoint Online, Skype for Business Online e altri ancora.
<!---first link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)
third link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune). check with Andre--->

> [!IMPORTANT]
> I criteri di accesso condizionale non possono essere usati se non vengono applicati criteri di conformità per la convalida della conformità.

### <a name="prevent-data-loss-of-company-data-with-app-protection-policies"></a>Evitare la perdita dei dati aziendali con criteri di protezione delle app

Con i criteri di protezione delle app di Intune è possibile scegliere la modalità di accesso ai dati, con o senza registrazione dei dispositivi. Questa versatilità consente di proteggere i dati aziendali in modo che un utente possa comunque accedere ai dati aziendali in modo sicuro, anche se non registra il dispositivo in Intune.

È possibile usare i [criteri di protezione delle app di Intune](app-protection-policies.md) per proteggere i dati aziendali a cui accedono i dispositivi iOS e Android. Quando si usano questi criteri a livello di app, è possibile controllare il modo in cui i dati aziendali vengono usati e condivisi dai dipendenti, anche se il dispositivo stesso non è gestito da Intune.

Usare [Windows Information Protection (WIP)](app-protection-policies-configure-windows-10.md) per eseguire la stessa operazione per i dispositivi Windows 10 gestiti. Questi criteri possono essere usati senza interferire con l'esperienza del dipendente. Non richiedono modifiche dell'ambiente di rete o di altre app.

### <a name="remove-company-data-while-leaving-personal-data-intact"></a>Rimuovere i dati aziendali mantenendo intatti i dati personali

Quando un dispositivo non viene più usato per lavoro, viene reimpiegato o risulta mancante, è necessario poter rimuovere le app e i dati aziendali dal dispositivo. A tale scopo, è possibile usare le funzionalità di Intune per rimuovere i dati aziendali e ripristinare le impostazioni predefinite. Gli utenti possono anche ripristinare in remoto i dispositivi personali dal portale aziendale di Intune, se i dispositivi sono registrati in Intune.

Il [ripristino delle impostazioni predefinite](devices-wipe.md) consente di ripristinare le impostazioni predefinite di fabbrica di un dispositivo, di rimuovere i dati e le impostazioni dell'utente, nonché di rimuovere il dispositivo dalla gestione di Intune. La funzionalità [Rimuovi i dati aziendali](devices-wipe.md#remove-company-data) rimuove solo i dati aziendali dal dispositivo, mantenendo invariati i dati personali degli utenti.

Una volta avviato, il dispositivo inizia immediatamente il processo di ripristino. Al termine del processo, tutti i dati aziendali vengono eliminati e il nome del dispositivo viene rimosso da Intune. Questo termina il ciclo di vita della gestione dei dispositivi mobili.
