---
title: Proteggere la posta elettronica per Exchange Online
description: Proteggere e controllare l'accesso alla posta elettronica aziendale in Exchange Online con accesso condizionale.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5ea0e0c31dc3b24c0093d6e3b73d38f2bee50bd7
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="protect-email-access-to-exchange-online-and-new-exchange-online-dedicated-with-intune"></a>Proteggere l'accesso alla posta elettronica per Exchange Online e il nuovo ambiente Exchange Online dedicato con Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

È possibile configurare l'accesso condizionale per Exchange locale o per Exchange Online dedicato usando Microsoft Intune. Per altre informazioni sul funzionamento dell'accesso condizionale, leggere l'articolo [Proteggere l'accesso alla posta elettronica, a Office 365 e ad altri servizi](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!NOTE]
>Se è disponibile un ambiente Exchange Online dedicato e si deve stabilire se si trova nell'ambiente di configurazione nuovo o legacy, contattare l'account manager.

## <a name="before-you-begin"></a>Prima di iniziare

Per configurare l'accesso condizionale è necessario:

-   Avere un **abbonamento a Office 365 che include Exchange Online (ad esempio E3)** e gli utenti devono avere una licenza per Exchange Online.

- Avere una **sottoscrizione di Enterprise Mobility + Security (EMS)** o una **sottoscrizione di Azure Active Directory Premium (Azure AD)** e gli utenti devono essere licenziatari di EMS o Azure AD. Per altre informazioni dettagliate, vedere la [pagina dei prezzi di Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) o la [pagina dei prezzi di Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

-  Può essere opportuno configurare l'opzione facoltativa **Intune Service to Service Connector** che connette Intune a Exchange Online e consente di gestire le informazioni sui dispositivi tramite la console di Intune. Non è necessario usare il connettore per i criteri di conformità o i criteri di accesso condizionale, ma è obbligatorio per eseguire i report utili per valutare l'impatto dell'accesso condizionale.
    -  Altre informazioni su [Service to Service Connector di Intune](intune-service-to-service-exchange-connector.md).

   > [!NOTE]
   > Non configurare Service to Service Connector di Intune se si prevede di usare l'accesso condizionale sia per Exchange Online che per Exchange locale.

### <a name="device-compliance-requirements"></a>Requisiti di conformità del dispositivo

Quando si configurano i criteri per l'accesso condizionale e li si assegna a un utente, prima che un utente possa connettersi alla posta elettronica, il **dispositivo** in uso deve:

- Essere un PC aggiunto a un dominio o **registrato** in Intune.

- Essere **registrato in Azure Active Directory**. Ciò avviene automaticamente quando il dispositivo è registrato in Intune. Inoltre, l'ID client Exchange ActiveSync deve essere registrato con Azure Active Directory.

  Il servizio Registrazione dispositivo di Azure Active Directory viene attivato automaticamente per i clienti di Intune e Office 365. I clienti che hanno già distribuito il servizio di registrazione dei dispositivi di ADFS non visualizzeranno i dispositivi registrati in Active Directory locale.

- Essere **conforme** a qualsiasi criterio di conformità di Intune distribuito per quel dispositivo o aggiunto a un dominio locale.

### <a name="when-the-device-is-not-compliant"></a>Quando il dispositivo non è conforme

Se un criterio di accesso condizionale non viene soddisfatto, il dispositivo viene inserito immediatamente in quarantena. L'utente riceve un messaggio di posta elettronica e, quando esegue l'accesso, viene visualizzata una delle seguenti notifiche di quarantena:

- Se il dispositivo non è registrato in Intune oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente istruzioni su come installare l'app Portale aziendale, registrare il dispositivo e attivare la posta elettronica. Questo processo associa anche l'ID Exchange ActiveSync del dispositivo con il record in Azure Active Directory.

-   Se il dispositivo viene dichiarato non conforme alle regole dei criteri di conformità, l'utente viene reindirizzato al sito Web del portale aziendale o all'app Portale aziendale di Intune dove sono disponibili informazioni sul problema e su come risolverlo.

### <a name="how-conditional-access-works-with-exchange-online"></a>Funzionamento dell'accesso condizionale con Exchange Online

Il diagramma seguente illustra il flusso usato dai criteri di accesso condizionale per Exchange Online.

![Diagramma che illustra gli aspetti tenuti in considerazione per determinare se a un dispositivo è consentito o meno l'accesso](../media/ConditionalAccess8-1.png)

## <a name="support-for-mobile-devices"></a>Supporto per dispositivi mobili
È possibile proteggere l'accesso alla posta elettronica di Exchange Online da **Outlook** e altre **app che usano l'autenticazione moderna**. Sono supportati:

- Android 4.0 e versioni successive, Samsung Knox Standard 4.0 e versioni successive e Android for Work
- iOS 8.0 e versioni successive

Con l'**autenticazione moderna** l'accesso basato su Active Directory Authentication Library (ADAL) diventa disponibile per i client Microsoft Office.

-   Questo tipo di autenticazione consente ai client Office di usare l'autenticazione basata su browser, nota anche come autenticazione passiva. Per eseguire l'autenticazione, l'utente viene indirizzato a una pagina Web di accesso.
-   Questo nuovo metodo di accesso offre migliori opzioni di sicurezza, come l'**autenticazione a più fattori** e l'**autenticazione basata sui certificati**. Per altre informazioni dettagliate, vedere [Funzionamento dell'autenticazione moderna ](https://support.office.com/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517). È possibile configurare le regole delle attestazioni AD FS per bloccare i protocolli di autenticazione non moderni. Istruzioni dettagliate sono disponibili in [Scenario 3: Bloccare completamente l'accesso esterno a Office 365, ad eccezione di applicazioni basate su browser](https://technet.microsoft.com/library/dn592182.aspx).

È possibile proteggere l'accesso a **Outlook Web Access (OWA)** in Exchange Online quando un utente accede a OWA da un browser in dispositivi **iOS** e **Android**. L'accesso è consentito solo dai browser supportati su dispositivi conformi:

* Safari (iOS)
* Chrome (Android)
* Intune Managed Browser (iOS, Android 5.0 e versioni successive)

   > [!IMPORTANT]
   > **I browser non supportati sono bloccati**.

**L'app OWA per iOS e Android può essere modificata in modo da evitare l'uso dell'autenticazione moderna e non è supportata. L'accesso dall'app OWA deve essere bloccato tramite le regole delle attestazioni di AD FS.**


È possibile proteggere l'accesso alla posta elettronica di Exchange dal **client di posta elettronica Exchange ActiveSync** integrato sulle piattaforme seguenti:

- Android 4.0 e versioni successive, Samsung Knox Standard 4.0 e versioni successive

- iOS 8.0 e versioni successive

- Windows Phone 8.1 e versioni successive

## <a name="support-for-pcs"></a>Supporto per PC

È possibile configurare l'accesso condizionale per i PC che eseguono le applicazioni desktop di Office al fine di accedere a **Exchange Online** e **SharePoint Online**, se i PC soddisfano i requisiti seguenti:

- Il PC deve eseguire Windows 7.0, Windows 8.1 o Windows 10.

  >[!NOTE]
  > Per usare l'accesso condizionale con PC Windows 10, è necessario aggiornare i PC con Windows 10 Anniversary Update.

  Il PC deve essere aggiunto a un dominio oppure essere conforme alle regole dei criteri di conformità.

  Affinché sia ritenuto conforme, il PC deve essere registrato in Intune e rispettare i criteri.

  Per i PC aggiunti a un dominio, è necessario configurare l'accesso condizionale per la [registrazione automatica del dispositivo](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) in Azure Active Directory.

  >[!NOTE]
  >L'accesso condizionale non è supportato nei PC che eseguono il client dei computer Intune.

- [L'autenticazione moderna di Office 365 deve essere abilitata](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) ed è necessario avere tutti gli aggiornamenti di Office più recenti.

  Con l'autenticazione moderna, i client Office 2013/Windows possono usare l'accesso basato su Active Directory Authentication Library (ADAL). Questo metodo di accesso offre migliori opzioni di sicurezza, come l'**autenticazione a più fattori** e **l'autenticazione basata sui certificati**.

- Per bloccare i protocolli di autenticazione non moderni vengono configurate regole delle attestazioni AD FS. Istruzioni dettagliate sono disponibili in [Scenario 3: Bloccare completamente l'accesso esterno a Office 365, ad eccezione di applicazioni basate su browser](https://technet.microsoft.com/library/dn592182.aspx).

## <a name="configure-conditional-access"></a>Configurare l'accesso condizionale
### <a name="step-1-configure-and-deploy-a-compliance-policy"></a>Passaggio 1: Configurare e distribuire i criteri di conformità
Assicurarsi di [creare](create-a-device-compliance-policy-in-microsoft-intune.md) e [distribuire](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) i criteri di conformità ai gruppi di utenti che riceveranno anche i criteri di accesso condizionale.


> [!IMPORTANT]
> Se i criteri di conformità non sono stati distribuiti, i dispositivi vengono considerati conformi e viene loro consentito l'accesso a Exchange.

### <a name="step-2-evaluate-the-effect-of-the-conditional-access-policy"></a>Passaggio 2: Valutare l'effetto dei criteri di accesso condizionale
È possibile usare i **Report inventario dispositivi mobili** per individuare i dispositivi che non potranno accedere a Exchange dopo aver configurato i criteri di accesso condizionale.

A tale scopo, configurare una connessione tra Intune ed Exchange usando [Microsoft Intune Service to Service Connector](intune-service-to-service-exchange-connector.md).
1.  Accedere a **Report** > **Report inventario dispositivi mobili**.
![Screenshot della pagina Report inventario dispositivi mobili](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  Nei parametri del report selezionare il gruppo Intune da valutare e, se necessario, le piattaforme del dispositivo a cui applicare i criteri.
3.  Dopo aver selezionato i criteri che soddisfano le esigenze dell'organizzazione, scegliere **Visualizza report**.
Il Visualizzatore report verrà aperto in una nuova finestra.
![Screenshot di un report inventario dispositivi mobili di esempio](../media/IntuneSA2cViewReport.PNG)

Dopo aver eseguito il report, esaminare le quattro colonne seguenti per determinare se un utente verrà bloccato:

-   **Canale di gestione**: indica se il dispositivo è gestito da Intune, Exchange ActiveSync o entrambi.

-   **AAD registrato**: indica se il dispositivo è registrato in Active Directory (aggiunto all'area di lavoro).

-   **Conforme**: indica se il dispositivo è conforme ai criteri di conformità distribuiti.

-   **ID Exchange ActiveSync**: i dispositivi iOS e Android devono avere un ID Exchange ActiveSync associato al record di registrazione del dispositivo in Azure Active Directory. Ciò si verifica quando l'utente sceglie il collegamento di **attivazione della posta elettronica** nel messaggio di posta elettronica di quarantena.

    > [!NOTE]
    > Per i dispositivi Windows Phone un valore viene sempre visualizzato in questa colonna.

L'accesso a Exchange da parte dei dispositivi che appartengono a un gruppo di destinazione viene bloccato a meno che i valori delle colonne non corrispondano a quelli elencati nella tabella seguente:

--------------------------

|                          Canale di gestione                          | AAD registrato | Conforme | ID Exchange ActiveSync |    Azione risultante     |
|----------------------------------------------------------------------|----------------|-----------|------------------------|-------------------------|
| <strong>Gestito da Microsoft Intune ed Exchange ActiveSync</strong> |      Sì       |    Sì    |  Viene visualizzato un valore  | Accesso alla posta elettronica consentito |
|                           Qualsiasi altro valore                            |       No       |    No     | Non viene visualizzato alcun valore  | Accesso alla posta elettronica bloccato |

----------------------
È possibile esportare il contenuto del report e usare la colonna **Indirizzo di posta elettronica** per informare gli utenti che verranno bloccati.

### <a name="step-3-configure-user-groups-for-the-conditional-access-policy"></a>Passaggio 3: Configurare i gruppi di utenti per i criteri di accesso condizionale.
I criteri di accesso condizionale sono destinati a diversi gruppi di utenti di sicurezza di Azure Active Directory. È anche possibile escludere alcuni gruppi di utenti dai criteri di accesso condizionale. Quando a un utente viene applicato un criterio, ogni dispositivo usato da tale utente deve essere conforme per accedere alla posta elettronica.

È possibile configurare questi gruppi nel **centro di amministrazione di Office 365**o nel **portale per gli account di Intune**.

È possibile specificare due tipi di gruppi in ogni criterio:

-   **Gruppi di destinazione**: gruppi di utenti a cui sono applicati i criteri.

-   **Gruppi esentati**: gruppi di utenti esentati dai criteri (facoltativo).

Se un utente si trova in entrambi i gruppi, sarà esentato dai criteri.

Vengono valutati solo i gruppi di utenti a cui sono applicati i criteri di accesso condizionale.

### <a name="step-4-configure-the-conditional-access-policy"></a>Passaggio 4: Configurare i criteri di accesso condizionale

> [!NOTE]
> È anche possibile creare criteri di accesso condizionale nella console di gestione di Azure AD. La console di gestione di Azure AD consente di creare i criteri di accesso condizionale per i dispositivi di Intune (definiti come **criteri di accesso condizionale basato su dispositivo** in Azure AD) oltre ad altri criteri di accesso condizionale come l'autenticazione a più fattori.
> 
> È anche possibile impostare i criteri di accesso condizionale per app aziendali di terze parti supportate da Azure AD, come Salesforce e Box. Per altri dettagli, vedere [Come impostare criteri di accesso condizionale basato su dispositivo di Azure Active Directory per controllare gli accessi delle applicazioni connesse ad Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/).


1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** > **Accesso condizionale** > **Criteri di Exchange Online**.

2. Nella pagina **Criteri di Exchange Online** scegliere **Abilita criteri di accesso condizionale per Exchange Online**.

   > [!NOTE]
   > Se i criteri di conformità non sono stati distribuiti, i dispositivi vengono considerati conformi.
   >
   > Indipendentemente dallo stato di conformità, tutti gli utenti interessati dai criteri devono registrare i propri dispositivi in Intune.

3. In **Accesso all'applicazione**, per le app che usano l'autenticazione moderna, sono disponibili due modi per scegliere le piattaforme a cui applicare i criteri. Le piattaforme supportate includono Android, iOS, Windows e Windows Phone.

   -   **Tutte le piattaforme**

       Tutti i dispositivi usati per accedere a **Exchange Online** dovranno essere registrati in Intune e dovranno essere conformi ai criteri. Qualsiasi applicazione client che usa l'**autenticazione moderna** è soggetta ai criteri di accesso condizionale. Se la piattaforma non è attualmente supportata da Intune, l'accesso a **Exchange Online** è bloccato.

       La selezione dell'opzione **Tutte le piattaforme** indica che Azure Active Directory applica questo criterio a tutte le richieste di autenticazione, indipendentemente dalla piattaforma segnalata dall'applicazione client. Tutte le piattaforme devono essere registrate e conformi, ad eccezione di:
       *   Dispositivi Windows, che dovranno essere registrati e conformi e/o aggiunti a un dominio con Active Directory locale.
       * Piattaforme non supportate come Mac OS. Tuttavia, le app che usano l'autenticazione moderna da queste piattaforme sono comunque bloccate.

   -   **Piattaforme specifiche**

        I criteri di accesso condizionale si applicano a tutte le app client che usano l'**autenticazione moderna** nelle piattaforme di dispositivi specificate.

4. In **Outlook Web Access (OWA)** è possibile scegliere di consentire l'accesso a Exchange Online solo dai browser supportati: Safari (iOS) e Chrome (Android). Non è possibile accedere da altri browser. Vengono applicate le stesse restrizioni di piattaforma selezionate per l'accesso all'applicazione per Outlook.

   Nei dispositivi **Android** gli utenti devono abilitare l'accesso al browser. Per eseguire questa operazione, l'utente deve abilitare l'opzione **Abilita l'accesso al browser** nel dispositivo registrato come indicato di seguito:
   1.    Aprire l'**app Portale aziendale**.
   2.    Passare alla pagina **Impostazioni** dai puntini di sospensione (...) o usando il pulsante di menu hardware.
   3.    Premere il pulsante **Abilita l'accesso al browser**.
   4.    Nel browser Chrome disconnettersi da Office 365 e riavviare Chrome.

   Nelle piattaforme **iOS** e **Android**, per identificare il dispositivo usato per accedere al servizio, Azure Active Directory emette un certificato TLS (Transport Layer Security) per il dispositivo. Il dispositivo visualizza il certificato richiedendo all'utente la selezione del certificato, come illustrato nelle schermate seguenti. Per continuare a usare il browser, è necessario che l'utente selezioni il certificato.

   **iOS**

   ![Schermata del messaggio di richiesta del certificato in un iPad](../media/mdm-browser-ca-ios-cert-prompt.png)

   **Android**

   ![schermata del messaggio di richiesta del certificato in un dispositivo Android](../media/mdm-browser-ca-android-cert-prompt.png)

5. In **App Exchange ActiveSync** è possibile scegliere di bloccare i dispositivi non conformi dall'accesso a Exchange Online. È anche possibile scegliere se consentire o bloccare l'accesso alla posta elettronica quando il dispositivo non esegue una piattaforma supportata. Le piattaforme supportate includono Android, iOS, Windows e Windows Phone.

   App Exchange Active Sync in **dispositivi Android for Work**:
   -  Nei dispositivi Android for Work sono supportate solo le app **Gmail**e **Nine Work** nel **profilo di lavoro**. Perché l'accesso condizionale funzioni nei dispositivi Android for Work, è necessario distribuire un profilo di posta elettronica per l'app Gmail o Nine Work e anche distribuirlo come installazione **obbligatoria**.

6. In **Gruppi di destinazione** selezionare i gruppi di sicurezza di Active Directory degli utenti ai quali applicare i criteri. È possibile scegliere come destinazione tutti gli utenti o un elenco di gruppi di utenti selezionato.
   ![Screenshot della pagina dei criteri di accesso condizionale di Exchange Online che illustra le opzioni dei gruppi di destinazione e di esenzione](../media/IntuneSA5eTargetedExemptedGroups.PNG)
   > [!NOTE]
   > Per gli utenti inclusi nei **Gruppi di destinazione** i criteri di Intune sostituiscono le regole e i criteri di Exchange.
   >
   > Exchange applicherà le regole di autorizzazione, blocco e quarantena e i criteri di Exchange solo nei casi seguenti:
   >
   > -   Un utente non dispone di una licenza per Intune.
   > -   Un utente dispone di una licenza per Intune, ma non appartiene ad alcun gruppo di sicurezza di destinazione nei criteri di accesso condizionale.

7. In **Gruppi esentati**selezionare i gruppi di sicurezza di Active Directory degli utenti che verranno esentati da questi criteri. Se un utente è incluso sia nel gruppo di destinazione che in quello esentato, viene esentato dai criteri.

8. Al termine dell'operazione scegliere **Salva**.

-   Non è necessario distribuire i criteri di accesso condizionale perché diventano immediatamente effettivi.

-   Dopo la creazione di un account di posta elettronica da parte di un utente, il dispositivo viene bloccato immediatamente.

-   Se un utente bloccato registra il dispositivo in Intune e risolve eventuali problemi di non conformità, l'accesso alla posta elettronica viene sbloccato entro due minuti.

-   Se l'utente annulla la registrazione del dispositivo, la posta elettronica viene bloccata dopo circa sei ore.

Per **alcuni scenari di esempio sulla configurazione dei criteri di accesso condizionale per proteggere l'accesso dei dispositivi**, vedere [Proteggere l'accesso alla posta elettronica: scenari di esempio](restrict-email-access-example-scenarios.md).

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorare i criteri di conformità e di accesso condizionale

#### <a name="to-view-devices-that-are-blocked-from-exchange"></a>Per visualizzare i dispositivi bloccati da Exchange

Nel dashboard di Intune scegliere il riquadro **Dispositivi bloccati da Exchange** per visualizzare il numero di dispositivi bloccati e i collegamenti ad altre informazioni.
![Screenshot del dashboard di Intune che mostra il numero di dispositivi che non possono accedere a Exchange](../media/IntuneSA6BlockedDevices.PNG)

## <a name="next-steps"></a>Passaggi successivi
- [Proteggere l'accesso a SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

- [Proteggere l'accesso a Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
