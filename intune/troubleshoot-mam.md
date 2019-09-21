---
title: Risolvere i problemi relativi alla gestione di applicazioni mobili
titleSuffix: Microsoft Intune
description: Questo argomento descrive alcuni suggerimenti per la risoluzione dei problemi relativi alle distribuzioni di accesso condizionale.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5e1ea8a0f8ea054b2eb75e1c98e60f184b0a45c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166752"
---
# <a name="troubleshoot-mobile-application-management"></a>Risolvere i problemi relativi alla gestione di applicazioni mobili

In questo argomento vengono fornite le soluzioni ai problemi comuni che si sono verificati durante l'utilizzo di Protezione app di Intune (noto anche come gestione di applicazioni per dispositivi mobili o MAM).

Se queste informazioni non consentono di risolvere il problema, vedere [Come ottenere supporto per Microsoft Intune](get-support.md) per trovare altri modi per ottenere assistenza.

## <a name="common-it-administrator-issues"></a>Problemi comuni di amministrazione IT

Questi sono i problemi comuni che un amministratore IT può sperimentare durante l'uso dei criteri di protezione delle app di Intune.

| Problema | Descrizione | Soluzione |
| -- | -- | -- |
| Criteri non applicati a Skype for Business | I criteri di protezione delle app senza registrazione del dispositivo, eseguita nel portale di Azure, non vengono applicati all'app Skype for Business in dispositivi iOS e Android. | È necessario configurare Skype for Business per l'autenticazione moderna.  Per configurare l'autenticazione moderna per Skype, seguire le istruzioni in [Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Abilitare il tenant per l'autenticazione moderna). |
| Criteri per le app di Office non applicati | I criteri di protezione delle app non vengono applicati ad alcuna [app di Office supportata](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) per qualsiasi utente. | Verificare che l'utente abbia una licenza per Intune e che le app di Office siano la destinazione di un criterio di protezione delle app distribuito. L'applicazione di un criterio di protezione dell'app appena distribuito può richiedere fino a otto ore. |
| L'amministratore non può configurare criteri di protezione delle app nel portale di Azure | L'utente amministratore IT non riesce a configurare i criteri di protezione delle app nel portale di Azure. | I ruoli utente seguenti hanno accesso al portale di Azure: <ul><li>Amministratore globale, configurabile nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/)</li><li>Proprietario, configurabile nel [portale di Azure](https://portal.azure.com/).</li><li>Collaboratore, configurabile nel [portale di Azure](https://portal.azure.com/).</li></ul> Fare riferimento a [Controllo degli accessi in base al ruolo (RBAC) con Microsoft Intune](role-based-access-control.md) per informazioni sulla configurazione di questi ruoli.|
|Account utente mancanti nei report dei criteri di protezione delle app | I report della console di amministrazione non mostrano gli account utente a cui sono stati distribuiti di recente criteri di protezione delle app. | Se un utente è stato selezionato di recente come destinazione di criteri di protezione delle app, possono trascorrere fino a 24 ore prima che l'utente compaia nei report come utente di destinazione. |
| Modifiche dei criteri non funzionanti | Per l'applicazione di modifiche o aggiornamenti dei criteri di protezione delle app possono essere richieste fino a 8 ore. | Se applicabile, l'utente finale può disconnettersi dall'app e rieseguire l'accesso per forzare la sincronizzazione con il servizio. |
| Criteri di protezione delle app non funzionanti con DEP | I criteri di protezione delle app non vengono applicati ai dispositivi DEP di Apple. | Assicurarsi di usare l'affinità utente con il programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple. L'affinità utente è obbligatoria per qualsiasi app che richiede l'autenticazione utente nell'ambito del programma DEP. <br><br>Fare riferimento a [Registrare automaticamente i dispositivi iOS nel programma Device Enrollment Program di Apple](device-enrollment-program-enroll-ios.md) per altre informazioni sulla registrazione nel programma DEP iOS.|
| Criteri di trasferimento dati non funzionanti con iOS | I criteri **Consenti all'app di trasferire i dati ad altre app** e **Consenti all'app di ricevere i dati da altre app** non consentono di gestire correttamente il trasferimento dei dati in iOS. | Vedere [Come gestire il trasferimento di dati tra app iOS in Microsoft Intune](data-transfer-between-apps-manage-ios.md). |

## <a name="common-end-user-issues"></a>Problemi comuni degli utenti finali

I problemi comuni degli utenti finali sono suddivisi nelle categorie seguenti:

* **Scenari di utilizzo normale**: un utente finale potrebbe riscontrare questi scenari per le app con criteri di protezione delle app di Intune. Non si tratta di veri e propri problemi, ma potrebbero essere percepiti come bug o errori.

* **Finestre di dialogo di utilizzo normali**: si tratta di finestre di dialogo di utilizzo che potrebbero essere visualizzate da un utente finale nelle app con criteri di protezione delle app di Intune. Questi messaggi e finestre di dialogo **non** indicano un errore o un bug.

* **Messaggi e finestre di dialogo di errore**: si tratta di messaggi e di finestre di dialogo di errore che potrebbero essere visualizzati da un utente finale nelle app con criteri di protezione delle app di Intune. Spesso indicano un errore effettuato dall'amministratore IT o un bug relativo alla protezione delle app di Intune.

### <a name="normal-usage-scenarios"></a>Scenari di utilizzo normali

Piattaforma | Scenario | Spiegazione |
---| --- | --- |
iOS | L'utente finale può usare l'estensione di condivisione iOS per aprire i dati aziendali o dell'istituto di istruzione nelle app non gestite, anche con i criteri di trasferimento dei dati impostati su **App gestite da criteri** o **Nessuna**. Questo scenario non comporta la perdita dei dati? | I criteri di protezione delle app di Intune non possono controllare l'estensione di condivisione di iOS senza la gestione del dispositivo. Pertanto, **Intune crittografa i dati "aziendali" prima che vengano condivisi all'esterno dell'app**. È possibile convalidare questo scenario provando ad aprire il file "aziendale" all'esterno dell'app gestita. Il file deve essere crittografato e non deve poter essere aperto all'esterno dell'app gestita.
iOS | Perché l'utente finale ha **richiesto di installare l'app Microsoft Authenticator** | Questa operazione è necessaria quando si applica l'accesso condizionale basato su app, vedere [richiedere l'app client approvata](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access).
Android | Perché l'utente finale **deve installare l'app Portale aziendale**, anche se si usa la protezione delle app MAM senza registrazione del dispositivo?  | In Android, gran parte delle funzionalità di protezione delle app è inclusa nell'app Portale aziendale. **La registrazione dei dispositivi non è necessaria anche se l'app Portale aziendale è sempre obbligatoria**. Per la protezione delle app senza registrazione, è sufficiente che l'utente finale installi l'app Portale aziendale nel dispositivo.
iOS/Android | Criteri di protezione delle app non applicati alla posta elettronica della bozza nell'app Outlook | Poiché Outlook supporta sia il contesto aziendale che quello personale, non impone la gestione delle applicazioni mobili nella bozza di posta elettronica.
iOS/Android | Criteri di protezione delle app non applicati ai nuovi documenti in WXP (Word, Excel, PowerPoint) | Poiché WXP supporta sia il contesto aziendale che quello personale, non impone la gestione delle applicazioni mobili nei nuovi documenti fino a quando non vengono salvati in un percorso aziendale identificato, ad esempio OneDrive.
iOS/Android | App che non consentono il salvataggio con memoria locale quando è abilitato il criterio | Il comportamento dell'app per questa impostazione è controllato dallo sviluppatore dell'app.
Android | Android ha più restrizioni rispetto a iOS sulle app "native" che possono accedere al contenuto protetto da MAM | Android è una piattaforma aperta e l'associazione di app "native" può essere modificata dall'utente finale a app potenzialmente non sicure. Applicare le [eccezioni dei criteri di trasferimento dei dati](app-protection-policies-exception.md) per esentare app specifiche.
Android | Il Azure Information Protection (AIP) può essere salvato in formato PDF quando è stato impedito il salvataggio | AIP rispetta i criteri MAM per "Disabilita stampa" quando viene usato Salva con nome PDF.
iOS | L'apertura di allegati PDF nell'app Outlook ha esito negativo con "azione non consentita | Questo problema può verificarsi se l'utente non ha eseguito l'autenticazione ad Acrobat Reader per Intune o ha usato l'identificazione personale per l'autenticazione nella propria organizzazione. Aprire prima Acrobat Reader ed eseguire l'autenticazione usando le credenziali UPN.


### <a name="normal-usage-dialogs"></a>Finestre di dialogo di utilizzo normali

Piattaforma | Messaggio o finestra di dialogo | Spiegazione |
--- | --- | --- |
iOS, Android | **Accesso**: Per proteggere i propri dati, l'organizzazione deve gestire questa app. Per completare l'azione, accedere con l'account aziendale o dell'istituto di istruzione. | L'utente finale deve accedere con l'account aziendale o dell'istituto di istruzione per poter usare questa app, che richiede criteri di protezione delle app. Per l'applicazione dei criteri è necessario che l'utente esegua l'autenticazione in Azure Active Directory.
iOS, Android |**Riavvio richiesto**: L'organizzazione protegge ora i propri dati in questa app. Per continuare è necessario riavviare l'app. | L'app ha appena ricevuto i criteri di protezione delle app di Intune e deve eseguire il riavvio per applicare i criteri.
iOS, Android |**L'azione non è consentita**: L'organizzazione consente solo di aprire i dati aziendali o dell'istituto di istruzione in questa app. | L'amministratore ha impostato il criterio **Consenti all'app di ricevere i dati da altre app** su **App gestite da criteri**. L'utente finale può quindi trasferire dati in questa app solo da altre app con criteri di protezione delle app.
iOS, Android |**L'azione non è consentita**: L'organizzazione consente solo di trasferire i propri dati ad altre app gestite. | L'amministratore ha impostato il criterio **Consenti all'app di trasferire i dati ad altre app** su **App gestite da criteri**. L'utente finale può quindi trasferire dati da questa app solo in altre app con criteri di protezione delle app.
iOS, Android |**Avviso di cancellazione dati**: L'organizzazione ha rimosso i propri dati associati a questa app. Per continuare, riavviare l'app. | L'amministratore IT ha avviato una cancellazione di app usando la protezione delle app di Intune.
Android | **È necessaria l'app Portale aziendale**: Per usare l'account aziendale o dell'istituto di istruzione con questa app, è necessario installare l'app Portale aziendale di Intune. Fare clic su "Vai allo Store" per continuare. | In Android, gran parte delle funzionalità di protezione delle app è inclusa nell'app Portale aziendale. **La registrazione dei dispositivi non è necessaria anche se l'app Portale aziendale è sempre obbligatoria**. Per la protezione delle app senza registrazione, è sufficiente che l'utente finale installi l'app Portale aziendale nel dispositivo.

### <a name="error-messages-and-dialogs-on-ios"></a>Messaggi e finestre di dialogo di errore in iOS

Messaggio o finestra di dialogo di errore | Causa | Soluzione |
-- | --- | --- |
**L'app non è configurata**: questa app non è stata configurata per l'uso da parte dell'utente. Per assistenza contattare l'amministratore IT. | Non è stato rilevato un criterio di protezione dell'app richiesto per questa app. |Verificare che sia stato distribuito un criterio di protezione dell'app iOS al gruppo di sicurezza dell'utente e che questa app rappresenti la destinazione.
**Introduzione a Intune Managed Browser**: questa app funziona in modo ottimale se gestita da Microsoft Intune. L'app può essere usata per navigare in rete ma, quando è gestita da Microsoft Intune, è possibile accedere ad altre funzionalità di protezione dati. | Non è stato rilevato un criterio di protezione dell'app richiesto per l'app Intune Managed Browser. <br><br>L'utente può ancora usare l'app per esplorare il Web, ma l'app non è gestita da Intune. | Verificare che sia stato distribuito un criterio di protezione dell'app iOS al gruppo di sicurezza dell'utente e che l'app Intune Managed Browser rappresenti la destinazione.
**L'accesso non è riuscito**: l'accesso non è disponibile al momento. Riprovare più tardi. | Non è stato possibile registrare l'utente con il servizio MAM dopo che l'utente ha provato ad accedere con il proprio account aziendale o dell'istituto di istruzione. | Verificare che sia stato distribuito un criterio di protezione dell'app iOS al gruppo di sicurezza dell'utente e che questa app rappresenti la destinazione.
**L'account non è configurato**: l'organizzazione non ha configurato l'account per l'accesso ai dati aziendali o dell'istituto di istruzione. Per assistenza, contattare l'amministratore IT. | L'account utente non ha una licenza Intune A Direct. | Verificare che all'account dell'utente sia assegnata una licenza di Intune nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com).
**Dispositivo non conforme**: questa app non può essere usata perché si sta usando un dispositivo jailbroken. Per assistenza contattare l'amministratore IT. | Intune ha rilevato che l'utente sta usando un dispositivo jailbroken. | Ripristinare le impostazioni predefinite del dispositivo. Seguire [queste istruzioni](https://support.apple.com/HT201274) dal sito di supporto di Apple.
**Connessione a Internet richiesta**: è necessaria una connessione a Internet per verificare se è possibile usare questa app. | Il dispositivo non è connesso a Internet. | Connettere il dispositivo a una rete Wi-Fi o dati.
**Errore sconosciuto**: provare a riavviare l'app. Se il problema persiste, contattare l'amministratore IT per assistenza. | Si è verificato un errore sconosciuto. | Attendere qualche minuto e riprovare. Se l'errore persiste, creare un [ticket di supporto](get-support.md#create-an-online-support-ticket) con Intune.
**Accesso ai dati dell'organizzazione**: l'account aziendale o dell'istituto di istruzione specificato non ha accesso a questa app. Può essere necessario accedere con un altro account. Per assistenza contattare l'amministratore IT. | Intune rileva che l'utente ha provato ad accedere con il secondo account aziendale o dell'istituto di istruzione che è diverso dall'account registrato in MAM per il dispositivo. MAM può gestire un solo account aziendale o dell'istituto di istruzione alla volta per ogni dispositivo. | Richiedere all'utente di accedere con l'account il cui nome utente è popolato dalla schermata di accesso. Potrebbe essere necessario [configurare l'impostazione UPN dell'utente per Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). <br> <br> In alternativa, richiedere all'utente di accedere con il nuovo account aziendale o dell'istituto di istruzione e rimuovere l'account registrato in MAM esistente.
**Problema di connessione**: si è verificato un problema di connessione imprevisto. Controllare la connessione e riprovare.  |  Errore imprevisto. | Attendere qualche minuto e riprovare. Se l'errore persiste, creare un [ticket di supporto](get-support.md#create-an-online-support-ticket) con Intune.
**Avviso**: questa app non può più essere usata. Per altre informazioni, contattare l'amministratore IT. | Non è stato possibile convalidare il certificato dell'app. | Assicurarsi che la versione dell'app sia aggiornata. <br><br> Reinstallare l'app.
**Errore**: questa applicazione ha riscontrato un errore e verrà chiusa. Se l'errore persiste, contattare l'amministratore IT. | Non è stato possibile leggere il PIN dell'app MAM da Apple iOS Keychain. | Riavviare il dispositivo. Assicurarsi che la versione dell'app sia aggiornata. <br><br> Reinstallare l'app.

### <a name="error-messages-and-dialogs-on-android"></a>Messaggi e finestre di dialogo di errore in Android

Finestra di dialogo/Messaggio di errore | Causa | Soluzione |
-- | --- | --- |
**L'app non è configurata**: questa app non è stata configurata per l'uso da parte dell'utente. Per assistenza contattare l'amministratore IT. | Non è stato rilevato un criterio di protezione dell'app richiesto per questa app. |Verificare che sia stato distribuito un criterio di protezione dell'app Android al gruppo di sicurezza dell'utente e che questa app rappresenti la destinazione.
**Failed app launch**: si è verificato un problema di avvio dell'applicazione. Provare ad aggiornare l'app o l'app Portale aziendale di Intune. Per assistenza, contattare l'amministratore IT. | Intune ha rilevato un criterio di protezione dell'app valido, ma l'app si blocca durante l'inizializzazione di MAM. | Assicurarsi che la versione dell'app sia aggiornata. <br><br> Assicurarsi che l'app Portale aziendale di Intune sia installata e aggiornata nel dispositivo. <br><br> Se l'errore persiste, usare l'app Portale aziendale per inviare i log a Intune o creare un [ticket di supporto](get-support.md#create-an-online-support-ticket).
**Non sono state trovate app**: nel dispositivo non sono presenti app consentite dall'organizzazione per aprire questo contenuto. Per assistenza contattare l'amministratore IT. | L'utente ha provato ad aprire i dati aziendali o dell'istituto di istruzione con un'altra app, ma Intune non riesce a trovare altre app gestite che possono aprire i dati. | Assicurarsi che sia stato distribuito un criterio di protezione dell'app Android alla protezione dell'utente e che la destinazione sia almeno un'altra app abilitata per MAM che può aprire i dati in questione.
**Accesso non riuscito**: provare a ripetere l'accesso. Se il problema persiste, contattare l'amministratore IT per assistenza. | Non è stato possibile autenticare l'account con cui l'utente ha provato ad accedere. | Assicurarsi che l'utente esegua l'accesso con l'account aziendale o dell'istituto di istruzione che è già registrato con il servizio MAM di Intune (il primo account aziendale o dell'istituto di istruzione con cui è stato effettuato correttamente l'accesso in questa app). <br><br> Cancellare i dati dell'app. <br><br> Assicurarsi che la versione dell'app sia aggiornata. <br><br> Assicurarsi che la versione dell'app Portale aziendale sia aggiornata.
**Connessione a Internet richiesta**: è necessaria una connessione a Internet per verificare se è possibile usare questa app. | Il dispositivo non è connesso a Internet. | Connettere il dispositivo a una rete Wi-Fi o dati.
**Dispositivo non conforme**: questa app non può essere usata perché si sta usando un dispositivo rooted. Per assistenza contattare l'amministratore IT. | Intune ha rilevato che l'utente sta usando un dispositivo rooted. | Ripristinare le impostazioni predefinite del dispositivo.
**L'account non è configurato**: questa app deve essere gestita da Microsoft Intune, ma l'account non è stato configurato. Per assistenza contattare l'amministratore IT. | L'account utente non ha una licenza Intune A Direct. | Verificare che all'account dell'utente sia assegnata una licenza di Intune nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com).
**Unable to register the app**: questa app deve essere gestita da Microsoft Intune, ma non è possibile effettuare la registrazione in questo momento. Per assistenza contattare l'amministratore IT. | Non è stato possibile registrare automaticamente l'app con il servizio MAM quando i criteri di protezione dell'applicazione sono obbligatori. | Cancellare i dati dell'app. <br><br> Inviare i log a Intune tramite l'app Portale aziendale o creare un ticket di supporto. Per altre informazioni, vedere [Come ottenere supporto per Microsoft Intune](get-support.md).

## <a name="next-steps"></a>Passaggi successivi

- [Convalidare la configurazione dei criteri di gestione delle applicazioni mobili](app-protection-policies-validate.md)
- Per informazioni su come usare i file di log per la risoluzione dei problemi di Protezione app di Intune, vedere[https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372)
- Per altre informazioni sulla risoluzione dei problemi di Intune, vedere [Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti aziendali](help-desk-operators.md). 
- È possibile ottenere informazioni sui problemi noti in Microsoft Intune. Per altre informazioni, vedere [Problemi noti in Microsoft Intune](known-issues.md).
- È possibile ottenere altre informazioni. Vedere [Come ottenere supporto per Microsoft Intune](get-support.md).
