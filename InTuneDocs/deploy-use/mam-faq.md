# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Domande frequenti sulla gestione di applicazioni mobili e sulla protezione delle app

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo articolo fornisce risposte ad alcune domande frequenti sulla gestione di applicazioni mobili (MAM) di Intune e sulla protezione delle app di Intune.

## <a name="mam-basics"></a>Informazioni di base su MAM


**Che cos'è MAM?** La [gestione di applicazioni mobili di Intune](overview-of-app-lifecycle-in-microsoft-intune.md) fa riferimento alla suite delle funzionalità di gestione di Intune e consente di pubblicare, distribuire, configurare, proteggere, monitorare e aggiornare le app mobili degli utenti.

**Quali sono i vantaggi della protezione delle app di MAM?** MAM protegge i dati di un'organizzazione all'interno di un'applicazione. Con MAM-WE un'app correlata all'istituto di istruzione o all'azienda contenente dati sensibili può essere gestita in quasi tutti i dispositivi, inclusi i dispositivi personali in scenari bring-your-own-device (BYOD). La maggior parte delle app di produttività, ad esempio le app per Microsoft Office, può essere gestita da MAM di Intune. Visualizzare l'elenco ufficiale delle [app abilitate per Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) disponibile al pubblico.

**Quali configurazioni dei dispositivi sono supportate da MAM?** MAM di Intune supporta due configurazioni:
  1. **Intune MDM + MAM**: questa è la prima configurazione supportata da MAM al primo avvio. Gli amministratori IT possono gestire le app solo usando criteri di protezione MAM e di protezione delle app nei dispositivi registrati con la gestione di dispositivi mobili (MDM) di Intune. Per gestire le app con MDM ed MAM, i clienti devono usare la console autonoma di Intune in http://manage.microsoft.com.

  2. **MAM senza registrazione del dispositivo**: MAM senza registrazione del dispositivo, o MAM-WE, consente agli amministratori IT di gestire le app tramite i criteri di protezione MAM e di protezione delle app in dispositivi non registrati con MDM di Intune. Ciò significa che le app possono essere gestite da Intune nei dispositivi registrati con i provider EMM di terze parti. Per gestire le app usando MAM-WE, i clienti devono usare la console di Intune nel portale di Azure in http://portal.azure.com.


## <a name="app-protection-policies"></a>Criteri di protezione delle app

**Che cosa sono i criteri di protezione delle app**? I criteri di protezione delle app sono regole che assicurano che i dati di un'organizzazione rimangano sicuri o contenuti in un'app gestita. Un criterio può essere una regola che viene applicata quando l'utente tenta di accedere o spostare dati "aziendali" o un set di azioni vietate o monitorate quando l'utente è all'interno dell'app.

**Esempi di criteri di protezione delle app**. Per informazioni dettagliate sulle singole impostazioni dei criteri di protezione delle app, vedere [Impostazioni dei criteri di protezione delle app per Android](android-mam-policy-settings.md) e [Impostazioni dei criteri di protezione delle app iOS](ios-mam-policy-settings.md).

## <a name="apps-you-can-manage-with-app-protection-policies"></a>App gestibili con i criteri di protezione delle app

**Quali app possono essere gestite dai criteri di protezione delle app?** Qualsiasi app abilitata da [Intune App SDK](../develop/intune-app-sdk.md) o di cui è stato eseguito il wrapping tramite lo [strumento di wrapping delle app di Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) può essere gestita mediante i criteri di protezione delle app di Intune. Visualizzare l'elenco ufficiale delle [app abilitate per Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) disponibile al pubblico.

**Quali sono i requisiti di base per usare i criteri di protezione delle app in un'app abilitata per Intune?**
  1. L'utente finale deve avere un account Azure Active Directory (AAD). Per imparare a creare gli utenti Intune in Azure Active Directory, vedere [Aggiungere utenti e concedere autorizzazioni amministrative a Intune](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md).

  2. L'utente finale deve disporre di una licenza per Microsoft Intune assegnata all'account Azure Active Directory. Per informazioni su come assegnare le licenze Intune agli utenti finali, vedere [Gestire le licenze di Intune](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4.md).

  3. L'utente finale deve appartenere a un gruppo di sicurezza che è la destinazione di un criterio di protezione delle app. Gli stessi criteri di protezione delle app devono avere come destinazione l'app specifica in uso. I criteri di protezione delle app possono essere creati e distribuiti nella console di Intune nel [portale di Azure](http://portal.azure.com). È ora possibile creare gruppi di sicurezza nel [portale di Office](http://portal.office.com).

  4. L'utente finale deve accedere all'app usando il proprio account AAD.

**Quali sono i requisiti aggiuntivi per usare l'[app Outlook per dispositivi mobili](https://www.microsoft.com/en-us/outlook-com/mobile/)?**

  1. L'utente finale deve avere l'app Outlook per dispositivi mobili installata nel dispositivo.

  2. L'utente finale deve avere una licenza e una cassetta postale di [Office 365 Exchange Online](https://products.office.com/en-us/exchange/exchange-online) collegata al proprio account Azure Active Directory.

  >[!NOTE]
  > L'app Outlook per dispositivi mobili attualmente supporta solo Microsoft Exchange Online e non supporta Exchange locale o Exchange in Office 365 dedicato.

**Quali sono i requisiti aggiuntivi per usare le app [Word, Excel e PowerPoint](https://products.office.com/business/office)?**

  1. L'utente finale deve avere una licenza per [Office 365 Business o Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) collegata all'account Azure Active Directory. La sottoscrizione deve includere le app di Office nei dispositivi mobili e un account di archiviazione cloud con [OneDrive for Business](https://onedrive.live.com/about/business/). È possibile assegnare le licenze di Office 365 nel [portale di Office](http://portal.office.com) seguendo queste [istruzioni](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc?ui=en-US&rs=en-US&ad=US).

  2. L'utente finale deve avere l'app [OneDrive](https://onedrive.live.com/about/) installata nei propri dispositivi e accedere con il proprio account AAD.

  3. All'app OneDrive deve essere assegnata una destinazione tramite i criteri di protezione delle app distribuiti all'utente finale.

  >[!NOTE]
  > Le app per dispositivi mobili di Office attualmente supportano solo SharePoint Online e SharePoint locale.

**Perché è necessario OneDrive per Office?** Intune contrassegna tutti i dati nell'app come "aziendali" o "personali". Quando hanno origine da una sede aziendale, i dati vengono considerati "aziendali". Per le app di Office, Intune considera quanto segue come sedi aziendali: posta elettronica (Exchange) o archiviazione cloud (app OneDrive con un account OneDrive for Business).

**Quali sono i requisiti aggiuntivi per usare Skype for Business?** Vedere i requisiti della licenza per [Skype for Business](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > L'app Skype for Business per dispositivi mobili attualmente supporta solo Skype for Business Online.

## <a name="app-protection-features"></a>Funzionalità di protezione delle app

**Che cos'è il supporto di più identità?** Il supporto di più identità consente a Intune App SDK di applicare i criteri di protezione delle app solo all'account aziendale o dell'istituto di istruzione registrato nell'app. Se nell'app viene registrato un account personale, i dati rimangono invariati.

**Qual è lo scopo del supporto di più identità?** Il supporto di più identità consente alle app con destinatari "aziendali" e consumer (ad esempio le app di Office) di essere rilasciate pubblicamente con funzionalità di protezione delle app di Intune per gli account "aziendali".

**Quando viene visualizzata la schermata del PIN?** La schermata del PIN di Intune viene visualizzata solo quando l'utente tenta di accedere ai dati "aziendali" nell'app. Ad esempio, nelle app Word/Excel/PowerPoint, tale schermata viene visualizzata quando l'utente finale tenta di aprire un documento da OneDrive for Business (presupponendo che sia stato correttamente distribuito un criterio di protezione delle app che applica il PIN).

**Informazioni su Outlook e le identità multiple.** Poiché Outlook dispone di una vista combinata per la posta elettronica personale e "aziendale", l'app Outlook richiede il PIN Intune all'avvio.

**Che cos'è il PIN dell'app Intune?** Il PIN è un codice di accesso usato per verificare che l'accesso ai dati dell'organizzazione in un'applicazione venga eseguito dall'utente appropriato.

  1. **Quando viene richiesto all'utente di immettere il PIN?** Intune richiede l'immissione del PIN dell'app dell'utente quando quest'ultimo sta per accedere ai dati "aziendali". Nelle app a identità multipla, ad esempio Word/Excel/PowerPoint, all'utente viene richiesto il PIN quando tenta di aprire un file o un documento "aziendale". Nelle app a identità singola, ad esempio app line-of-business abilitate per l'uso dello strumento di wrapping delle app, il PIN viene richiesto all'avvio, poiché Intune App SDK riconosce che l'esperienza dell'utente nell'app è sempre "aziendale".

  2. **Il PIN è sicuro?** Il PIN consente l'accesso ai dati aziendali nell'app solo all'utente appropriato. Pertanto, un utente finale deve accedere con il proprio account aziendale o dell'istituto di istruzione prima di poter impostare o reimpostare il PIN dell'app Intune. Questa autenticazione viene gestita da Azure Active Directory tramite scambio di token di sicurezza e non è trasparente per Intune App SDK. Dal punto di vista della sicurezza, il modo migliore per proteggere i dati aziendali o dell'istituto di istruzione è la crittografia. La crittografia non è correlata al PIN dell'app, ma costituisce i criteri di protezione delle app.

  3. **In che modo Intune protegge il PIN dagli attacchi di forza bruta?** Nell'ambito dei criteri del PIN dell'app, l'amministratore IT può impostare il numero massimo di volte in cui un utente può provare a eseguire l'autenticazione del PIN prima di bloccare l'app. Dopo aver raggiunto il numero di tentativi, Intune App SDK può cancellare i dati "aziendali" nell'app.

**Informazioni sulla crittografia.** Gli amministratori IT possono distribuire un criterio di protezione delle app che richiede di crittografare i dati dell'app. Nell'ambito dei criteri, l'amministratore IT può specificare anche il momento in cui il contenuto viene crittografato.

  1. **In che modo Intune crittografa i dati?** Per informazioni dettagliate sulle impostazioni di crittografia dei criteri di protezione delle app, vedere [Impostazioni dei criteri di protezione delle app per Android](android-mam-policy-settings.md) e [Impostazioni dei criteri di protezione delle app iOS](ios-mam-policy-settings.md).

  2. **Quali dati vengono crittografati?** Vengono crittografati solo i dati contrassegnati come "aziendali" in base ai criteri di protezione delle app dell'amministratore IT. Quando hanno origine da una sede aziendale, i dati vengono considerati "aziendali". Per le app di Office, Intune considera quanto segue come sedi aziendali: posta elettronica (Exchange) o archiviazione cloud (app OneDrive con un account OneDrive for Business). Per le app line-of-business abilitate per lo strumento di wrapping delle app di Intune, tutti i dati delle app vengono considerati "aziendali".

**In che modo Intune cancella i dati in remoto?** Intune può cancellare i dati dell'app in due modi diversi: cancellazione completa e cancellazione selettiva. Per altre informazioni sulla cancellazione da remoto, vedere [Proteggere i dati con la cancellazione selettiva o completa tramite Microsoft Intune](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md).

  1. **Che cos'è la cancellazione completa?** La [cancellazione completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe) rimuove tutti i dati dell'utente e le impostazioni dal **dispositivo** ripristinandolo alle impostazioni predefinite di fabbrica. Il dispositivo verrà rimosso da Intune.
  >[!NOTE]
  > La cancellazione completa può essere eseguita solo sui dispositivi registrati con la gestione di dispositivi mobili (MDM) di Intune.

  2. **Che cos'è la cancellazione selettiva?** Per informazioni sulla cancellazione selettiva, vedere [Proteggere i dati con la cancellazione selettiva o completa tramite Microsoft Intune](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe).

  3. **A quale velocità si verifica la cancellazione selettiva?** Se l'utente sta usando l'app quando viene avviata la cancellazione selettiva, Intune App SDK controlla ogni 30 minuti la presenza di una richiesta di cancellazione selettiva dal servizio MAM di Intune. L'SDK verifica inoltre la presenza della cancellazione selettiva quando l'utente avvia l'app per la prima volta e accede con l'account aziendale o dell'istituto di istruzione.

**Perché i servizi locali non funzionano con le app protette di Intune?** La protezione delle app di Intune dipende dalla coerenza dell'identità dell'utente tra l'applicazione e Intune App SDK. L'unico modo per garantire questo scenario è tramite l'autenticazione moderna. Esistono scenari in cui le app possono funzionare con una configurazione locale, ma non sono garantiti, né coerenti.

**Esiste un modo sicuro per aprire i collegamenti Web da app gestite?** Sì. L'amministratore IT può distribuire e impostare i criteri di protezione delle app per l'[app Intune Managed Browser](manage-internet-access-using-managed-browser-policies.md), un Web browser sviluppato da Microsoft Intune che è possibile gestire facilmente con Intune. L'amministratore IT può richiedere che tutti i collegamenti Web nelle app abilitate per Intune vengano aperti tramite l'app Managed Browser.


## <a name="app-experience-on-android"></a>Esperienze app in Android

**Perché l'app Portale aziendale è necessaria per il funzionamento della protezione dell'app di Intune su dispositivi Android?** Gran parte delle funzionalità di protezione dell'app viene compilata nell'app Portale aziendale. La registrazione dei dispositivi _non è necessaria_ anche se l'app Portale aziendale è sempre obbligatoria. Per MAM-WE, è sufficiente che l'utente finale installi l'app Portale aziendale nel dispositivo.

## <a name="app-experience-on-ios"></a>Esperienze app in iOS

**È possibile usare l'estensione di condivisione iOS per aprire i dati aziendali dell'istituto di istruzione nelle app non gestite, anche con i criteri di trasferimento dei dati impostati su "solo app gestite" o "nessuna app". Questo scenario non comporta la perdita dei dati?** I criteri di protezione delle app di Intune non possono controllare l'estensione di condivisione di iOS senza la gestione del dispositivo. Pertanto, Intune _**crittografa i dati "aziendali" prima che vengano condivisi all'esterno dell'app**_. È possibile convalidare questo scenario provando ad aprire il file "aziendale" all'esterno dell'app gestita. Il file deve essere crittografato e non deve poter essere aperto all'esterno dell'app gestita.


<!--HONumber=Jan17_HO1-->


