---
title: Risolvere i problemi relativi alla gestione di applicazioni mobili | Documentazione Microsoft
description: Questo argomento descrive alcuni suggerimenti sulla risoluzione dei problemi per le distribuzioni di accesso condizionale.
keywords: 
author: NathBarn
ms.author: oldang
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: d50a5751a5afd987196336e9443dc5a429a283fd
ms.openlocfilehash: b333c0f5097fec38bf0dd78726a028fd7aaccd2f


---

# <a name="troubleshoot-mobile-application-management"></a>Risolvere i problemi relativi alla gestione di applicazioni mobili

In presenza di problemi relativi alla gestione delle applicazioni mobili Intune, è possibile iniziare da qui. Questo argomento descrive alcuni problemi comuni e contiene le possibile domande degli utenti, fornendo soluzioni e risposte.

## <a name="common-it-administrator-issues"></a>Problemi comuni di amministrazione IT

1. **Problema:** i criteri di protezione dell'app senza registrazione del dispositivo, eseguita nel portale di Azure, non vengono applicati all'app Skype for Business in dispositivi iOS e Android.

  **Soluzione**: è necessario configurare Skype for Business per l'autenticazione moderna.  Per configurare l'autenticazione moderna per Skype, seguire le istruzioni in [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Abilitare il tenant per l'autenticazione moderna).

2. **Problema:** i criteri di protezione dell'app non si applicano a qualsiasi [app di Office supportata](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) per qualsiasi utente.

  **Soluzione**: verificare che l'utente abbia una licenza per Intune e che le app di Office siano la destinazione del criterio di protezione dell'app distribuito. L'applicazione di un criterio di protezione dell'app appena distribuito può richiedere fino a otto ore.

3. **Problema:** l'utente amministratore IT non riesce a configurare i criteri di protezione dell'app nel portale di Azure.

  **Risoluzione**:

  i ruoli utente seguenti hanno accesso al portale di Azure:

  - Amministratore globale, configurabile nel [portale di Office](http://portal.office.com/)
  - Proprietario, configurabile nel [portale di Office](https://portal.azure.com/)
  - Collaboratore, configurabile nel [portale di Office](https://portal.azure.com/)<br>

  Per informazioni sulla configurazione di questi ruoli, vedere [Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili con Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md).

4. **Problema:** i report della console di amministrazione non mostrano l'account (o gli account) utente in cui è stato recentemente distribuito il criterio di protezione.

  **Soluzione**: se un utente è stato selezionato di recente come destinazione di criteri di protezione dell'app, possono trascorrere fino a 24 ore prima che l'utente compaia nei report come utente di destinazione.

5. **Problema:** per l'applicazione di modifiche o aggiornamenti dei criteri possono essere richieste fino a 8 ore.  

  **Soluzione**: l'utente finale può disconnettersi dall'app e rieseguire l'accesso per forzare la sincronizzazione con il servizio.  

6. **Problema:** i criteri di protezione dell'app non vengono applicati ai dispositivi DEP di Apple.

  **Soluzione**: assicurarsi di usare l'affinità utente con il programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple. L'affinità utente è obbligatoria per qualsiasi app che richiede l'autenticazione utente nell'ambito del programma DEP.
Per altre informazioni sulla registrazione al programma DEP iOS, vedere [Registrare i dispositivi iOS di proprietà dell'azienda usando il programma di registrazione dispositivi (DEP)](../deploy-use/ios-device-enrollment-program-in-microsoft-intune.md).

## <a name="common-end-user-issues"></a>Problemi comuni degli utenti finali

### <a name="issues-on-ios"></a>Problemi in iOS

Finestra di dialogo/Messaggio di errore | Causa | Soluzione |
-- | --- | --- |
**L'app non è configurata**: questa app non è stata configurata per l'uso da parte dell'utente. Per assistenza contattare l'amministratore IT. | Non è stato rilevato il criterio di protezione dell'app obbligatorio per questa app. |Verificare che sia stato distribuito un criterio di protezione dell'app iOS al gruppo di sicurezza dell'utente e che questa app rappresenti la destinazione.
**Introduzione a Intune Managed Browser**: questa app funziona in modo ottimale se gestita da Microsoft Intune. L'app può essere usata per navigare in rete ma, quando è gestita da Microsoft Intune, è possibile accedere ad altre funzionalità di protezione dati. | Non è stato rilevato il criterio di protezione dell'app obbligatorio per l'app Intune Managed Browser. <br><br>L'utente può ancora usare l'app per esplorare il Web, ma l'app non è gestita da Intune. | Verificare che sia stato distribuito un criterio di protezione dell'app iOS al gruppo di sicurezza dell'utente e che l'app Intune Managed Browser rappresenti la destinazione.
**L'accesso non è riuscito**: l'accesso non è disponibile al momento. Riprovare più tardi. | Non è stato possibile registrare l'utente con il servizio MAM dopo che l'utente ha provato ad accedere con il proprio account aziendale o dell'istituto di istruzione. | Verificare che sia stato distribuito un criterio di protezione dell'app iOS al gruppo di sicurezza dell'utente e che questa app rappresenti la destinazione.
**L'account non è configurato**: l'organizzazione non ha configurato l'account per l'accesso ai dati aziendali o dell'istituto di istruzione. Per assistenza, contattare l'amministratore IT. | L'account utente non ha una licenza Intune A Direct. | Verificare che all'account dell'utente sia assegnata una licenza di Intune nel [portale di Office](http://portal.office.com).
**Dispositivo non conforme**: questa app non può essere usata perché si sta usando un dispositivo jailbroken. Per assistenza contattare l'amministratore IT. | Intune ha rilevato che l'utente sta usando un dispositivo jailbroken. | Ripristinare le impostazioni predefinite del dispositivo. Seguire [queste istruzioni](https://support.apple.com/en-us/HT201274) dal sito di supporto di Apple.
**Connessione a Internet richiesta**: è necessaria una connessione a Internet per verificare se è possibile usare questa app. | Il dispositivo non è connesso a Internet. | Connettere il dispositivo a una rete Wi-Fi o dati.
**Errore sconosciuto**: provare a riavviare l'app. Se il problema persiste, contattare l'amministratore IT per assistenza. | Si è verificato un errore sconosciuto. | Attendere qualche minuto e riprovare. Se l'errore persiste, creare un ticket di supporto con Intune [qui](/how-to-get-support-for-microsoft-intune.md).
**Accesso ai dati dell'organizzazione**: l'account aziendale o dell'istituto di istruzione specificato non ha accesso a questa app. Può essere necessario accedere con un altro account. Per assistenza contattare l'amministratore IT. | Intune rileva che l'utente ha provato ad accedere con il secondo account aziendale o dell'istituto di istruzione che è diverso dall'account registrato in MAM per il dispositivo. MAM può gestire un solo account aziendale o dell'istituto di istruzione alla volta per ogni dispositivo. | Richiedere all'utente di accedere con l'account il cui nome utente è popolato dalla schermata di accesso. <br> <br> In alternativa, richiedere all'utente di accedere con il nuovo account aziendale o dell'istituto di istruzione e rimuovere l'account registrato in MAM esistente.
**Problema di connessione**: si è verificato un problema di connessione imprevisto. Controllare la connessione e riprovare.  |  Errore imprevisto. | Attendere qualche minuto e riprovare. Se l'errore persiste, creare un ticket di supporto con Intune [qui](/how-to-get-support-for-microsoft-intune.md).
**Avviso**: questa app non può più essere usata. Per altre informazioni, contattare l'amministratore IT. | Non è stato possibile convalidare il certificato dell'app. | Assicurarsi che la versione dell'app sia aggiornata. <br><br> Reinstallare l'app.
**Errore**: questa applicazione ha riscontrato un errore e verrà chiusa. Se l'errore persiste, contattare l'amministratore IT. | Non è stato possibile leggere il PIN dell'app MAM da Apple iOS Keychain. | Riavviare il dispositivo. Assicurarsi che la versione dell'app sia aggiornata. <br><br> Reinstallare l'app.


### <a name="issues-on-android"></a>Problemi in Android

Finestra di dialogo/Messaggio di errore | Causa | Soluzione |
-- | --- | --- |
**L'app non è configurata**: questa app non è stata configurata per l'uso da parte dell'utente. Per assistenza contattare l'amministratore IT. | Non è stato rilevato il criterio di protezione dell'app obbligatorio per questa app. |Verificare che sia stato distribuito un criterio di protezione dell'app iOS al gruppo di sicurezza dell'utente e che questa app rappresenti la destinazione.
**Failed app launch**: si è verificato un problema di avvio dell'applicazione. Provare ad aggiornare l'app o l'app Portale aziendale di Intune. Per assistenza, contattare l'amministratore IT. | Intune ha rilevato un criterio di protezione dell'app valido, ma l'app si blocca durante l'inizializzazione di MAM. | Assicurarsi che la versione dell'app sia aggiornata. <br><br> Assicurarsi che l'app Portale aziendale di Intune sia installata e aggiornata nel dispositivo. <br><br> Se l'errore persiste, usare l'app Portale aziendale per inviare i log a Intune o creare un ticket di supporto [qui](/how-to-get-support-for-microsoft-intune.md).
**Non sono state trovate app**: nel dispositivo non sono presenti app consentite dall'organizzazione per aprire questo contenuto. Per assistenza contattare l'amministratore IT. | L'utente ha provato ad aprire i dati aziendali o dell'istituto di istruzione con un'altra app, ma Intune non riesce a trovare altre app gestite che possono aprire i dati. | Assicurarsi che sia stato distribuito un criterio di protezione dell'app Android alla protezione dell'utente e che la destinazione sia almeno un'altra app abilitata per MAM che può aprire i dati in questione.
**Accesso non riuscito**: provare a ripetere l'accesso. Se il problema persiste, contattare l'amministratore IT per assistenza. | Non è stato possibile autenticare l'account con cui l'utente ha provato ad accedere. | Assicurarsi che l'utente esegua l'accesso con l'account aziendale o dell'istituto di istruzione che è già registrato con il servizio MAM di Intune (il primo account aziendale o dell'istituto di istruzione con cui è stato effettuato correttamente l'accesso in questa app). <br><br> Cancellare i dati dell'app. <br><br> Assicurarsi che la versione dell'app sia aggiornata. <br><br> Assicurarsi che la versione dell'app Portale aziendale sia aggiornata.
**Connessione a Internet richiesta**: è necessaria una connessione a Internet per verificare se è possibile usare questa app. | Il dispositivo non è connesso a Internet. | Connettere il dispositivo a una rete Wi-Fi o dati.
**Dispositivo non conforme**: questa app non può essere usata perché si sta usando un dispositivo rooted. Per assistenza contattare l'amministratore IT. | Intune ha rilevato che l'utente sta usando un dispositivo rooted. | Ripristinare le impostazioni predefinite del dispositivo.
**L'account non è configurato**: questa app deve essere gestita da Microsoft Intune, ma l'account non è stato configurato. Per assistenza contattare l'amministratore IT. | L'account utente non ha una licenza Intune A Direct. | Verificare che all'account dell'utente sia assegnata una licenza di Intune nel [portale di Office](http://portal.office.com).
**Unable to register the app**: questa app deve essere gestita da Microsoft Intune, ma non è possibile effettuare la registrazione in questo momento. Per assistenza contattare l'amministratore IT. | Non è stato possibile registrare automaticamente l'app con il servizio MAM quando i criteri di protezione dell'applicazione sono obbligatori. | Cancellare i dati dell'app. <br><br> Inviare i log a Intune attraverso l'app Portale aziendale per o creare un ticket di supporto [qui](/how-to-get-support-for-microsoft-intune.md).





### <a name="see-also"></a>Vedere anche
- [Convalidare la configurazione dei criteri di gestione delle applicazioni mobili](../deploy-use/validate-mobile-application-management.md)
- [Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili con Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


