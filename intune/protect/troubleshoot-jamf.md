---
title: Risoluzione dei problemi relativi all'integrazione di JAMF Pro con Microsoft Intune
titleSuffix: Microsoft Intune
description: Suggerimenti per la risoluzione di alcuni dei problemi più comuni quando si integrano i dispositivi JAMF Pro per Mac con Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44733eb369e520d2d5f0ff548d4f1921abcb8758
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503575"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>Risolvere i problemi di integrazione di JAMF Pro con Microsoft Intune

Questo articolo aiuta gli amministratori di Intune a comprendere e risolvere i problemi relativi all'integrazione di JAMF Pro per macOS con Intune.

> [!TIP]  
> Gran parte delle informazioni contenute in questo articolo sono emerse in origine in [risoluzione dei problemi quando si integra JAMF con Microsoft Intune](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune) in support.Microsoft.com.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare la risoluzione dei problemi, raccogliere alcune informazioni di base per chiarire il problema e ridurre il tempo necessario per trovare una soluzione. Ad esempio, quando si verifica un problema relativo all'integrazione di JAMF-Intune, verificare sempre che siano stati soddisfatti tutti i prerequisiti. Prima di iniziare la risoluzione dei problemi, esaminare le considerazioni seguenti:

- Esaminare i prerequisiti di [integrare JAMF Pro con Intune](conditional-access-integrate-jamf.md#prerequisites).
- Tutti gli utenti devono avere le licenze Microsoft Intune e Microsoft AAD Premium P1 
- È necessario disporre di un account utente con autorizzazioni di integrazione Microsoft Intune nella console di JAMF Pro.
- È necessario disporre di un account utente con autorizzazioni di amministratore globale in Azure.


Quando si esamina l'integrazione di JAMF Pro con Intune, tenere presenti le informazioni seguenti: 
- Qual è il messaggio di errore esatto?
- Dove viene visualizzato il messaggio di errore?
- Quando è iniziato il problema?  L'integrazione di JAMF Pro con Intune ha sempre funzionato?
- Quanti utenti sono interessati? Tutti gli utenti sono interessati o solo alcuni?
- Quanti dispositivi sono interessati? Tutti i dispositivi sono interessati o solo alcuni?
 

## <a name="common-problems"></a>Problemi comuni 

Le informazioni seguenti consentono di identificare e risolvere i problemi comuni per i dispositivi dopo aver configurato l'integrazione di Intune e JAMF Pro.  

| Problema   | Altre informazioni                  |
|-----------------|--------------------------|
| **I dispositivi vengono contrassegnati come non risponde in JAMF Pro**  | [I dispositivi non riescono ad archiviare con JAMF Pro o con Azure AD](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **La richiesta di accesso Keychain ai dispositivi Mac quando si apre un dispositivo dell'app non riesce a registrarsi**  | [Agli utenti viene richiesto di immettere la password per consentire alle app di registrarsi con Azure ad](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app). |
| **La registrazione dei dispositivi non riesce**  | Potrebbero essere valide le cause seguenti: <br> **-** [ ***cause 1*** : le autorizzazioni per l'app JAMF Pro in Azure non sono corrette](#cause-1) <br> **-** [ ***causa 2*** -si è verificato un problema per il *connettore MacOS nativo di JAMF* in Azure ad](#cause-2) <br> **-** [ ***cause 3*** -l'utente non dispone di una licenza di Intune o JAMF valida](#cause-3) <br> **-** [ ***motivo 4*** -l'utente non ha usato JAMF self service per avviare l'app portale aziendale](#cause-4) <br> **-** [ ***cause 5*** : l'integrazione di Intune è disattivata](#cause-5) <br> **-** [ ***motivo 6*** : il dispositivo è stato registrato in precedenza in Intune o l'utente ha tentato di registrare il dispositivo più volte](#cause-6) <br> **-** [ ***cause 7*** -JamfAAD richiede l'accesso a una "chiave di Microsoft workplace join" dal Keychain degli utenti](#cause-7) |
|  **Il dispositivo Mac Mostra la conformità in Intune ma non è conforme in Azure** | [Problemi di registrazione del dispositivo](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Le voci duplicate vengono visualizzate nella console di Intune per i dispositivi Mac registrati con JAMF** | [Più registrazioni per lo stesso dispositivo](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **I criteri di conformità non sono in grado di valutare il dispositivo** | [Il criterio è destinato ai gruppi di dispositivi](#compliance-policy-fails-to-evaluate-the-device) |
| **Non è stato possibile recuperare il token di accesso per l'API Microsoft Graph** | Potrebbero essere valide le cause seguenti: <br> -[le autorizzazioni per l'app JAMF Pro in Azure](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) <br> - [licenza scaduta per JAMF o Intune](#a-license-required-for-jamf-intune-integration-has-expired) <br> porte **-** [non aperte](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>I dispositivi vengono contrassegnati come non risponde in JAMF Pro  

**Causa**: di seguito sono riportate le cause comuni dei dispositivi contrassegnati come non *risponde* da JAMF Pro:

- Il dispositivo non riesce ad archiviare con JAMF Pro.  
  JAMF Pro prevede che i dispositivi vengano verificati ogni 15 minuti. I dispositivi vengono contrassegnati come non risponde da JAMF se non riescono a archiviare in un periodo di 24 ore.  

- Il dispositivo non riesce ad archiviare con Azure AD.  
  Con la registrazione corretta per Azure AD, i dispositivi macOS ricevono un token di Azure:
  - Questo token viene aggiornato ogni 12 ore.   
  - Quando l'aggiornamento del token ha esito negativo per 24 ore o più, JAMF Pro contrassegna il dispositivo come non risponde.  
  - Se il token di Azure scade, agli utenti viene richiesto di accedere ad Azure per ottenere un nuovo token. Un token di aggiornamento per l'accesso ad Azure viene generato ogni sette giorni.

**Risoluzione**  
Dopo che un dispositivo è stato contrassegnato come non *risponde* da JAMF Pro, l'utente registrato del dispositivo deve eseguire l'accesso per correggere lo stato non reattivo. Deve essere l'utente che ha aggiunto il lavoro all'account perché ha l'identità di Intune nel keychain di accesso.



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>I dispositivi Mac richiedono l'accesso Keychain quando si apre un'app  

Dopo aver configurato l'integrazione di Intune e JAMF Pro e aver distribuito i criteri di accesso condizionale, gli utenti dei dispositivi gestiti con JAMF Pro riceveranno una password per l'apertura di Microsoft Office applicazioni 365, ad esempio i team, Outlook e altre app che richiedono Azure Autenticazione AD. 

Ad esempio, quando si apre Microsoft teams viene visualizzato un messaggio di richiesta con testo simile all'esempio seguente:

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**Motivo**: queste richieste vengono generate da JAMF Pro per ogni app applicabile che richiede la registrazione Azure ad. 

**Risoluzione**   
Al prompt, l'utente deve specificare la password del dispositivo per accedere Azure AD. Le opzioni includono:
- **Nega** : non eseguire l'accesso e non usare l'app.
- **Consenti** -un accesso una volta. Alla successiva apertura dell'app, viene richiesto di nuovo l'accesso.
- **Consenti sempre** : le credenziali di accesso vengono memorizzate nella cache per l'applicazione. Alla successiva apertura dell'app, non richiede l'accesso.  

Se si seleziona *Consenti sempre* per un'app, l'app viene approvata per l'accesso futuro. Le app aggiuntive richiedono l'autenticazione fino a quando non vengono impostate come *Consenti sempre*. Le credenziali memorizzate nella cache per un'app non possono essere usate da un'altra app.  

### <a name="devices-fail-to-register"></a>La registrazione dei dispositivi non riesce  

Per i dispositivi Mac che non riescono a eseguire la registrazione, sono diverse le cause più comuni.  

#### <a name="cause-1"></a>Causa 1  

**L'applicazione JAMF Pro Enterprise in Azure ha l'autorizzazione errata o ha più di un'autorizzazione**  

  Quando si crea l'app in Azure, è necessario rimuovere tutte le autorizzazioni predefinite dell'API e quindi assegnare a Intune un'unica autorizzazione di *update_device_attributes*. 

  **Risoluzione**  
  Esaminare e, se necessario, correggere le autorizzazioni per l'app JAMF creata in Azure AD. Vedere la procedura per [creare un'applicazione per JAMF in Azure ad](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory). 

#### <a name="cause-2"></a>Causa 2  

**L'app del **connettore MacOS nativa di JAMF** non è stata creata nel tenant di Azure ad o il consenso per il connettore è stato firmato da un account che non dispone dei diritti di amministratore globale**  

  **Risoluzione**  
  Vedere la sezione *configurazione dell'integrazione di Intune per MacOS* in [integrazione con Microsoft Intune](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html) in docs.JAMF.com. 

#### <a name="cause-3"></a>Causa 3

**L'utente non dispone di una licenza valida di Intune o JAMF**  

  La mancanza di una licenza valida può causare l'errore seguente, che indica che la licenza JAMF è scaduta:  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **Risoluzione**
  - Licenza di JAMF: contattare JAMF per assistenza per ottenere una nuova licenza per JAMF.  
  - Licenza di Intune: assegnare all'utente una licenza valida o contattare Microsoft o il proprio partner per informazioni su come ottenere una licenza corrente.

#### <a name="cause-4"></a>Causa 4  

**L'utente non ha usato *JAMF self service* per avviare l'app portale aziendale**

Per la registrazione e la registrazione di un dispositivo con Intune tramite JAMF, l'utente deve usare JAMF self service per aprire il Portale aziendale Intune. Se l'utente apre manualmente il portale aziendale, il dispositivo esegue la registrazione e la registrazione senza la connessione a JAMF.  

Per determinare il servizio usato dal dispositivo per la registrazione e la registrazione, esaminare l'app Portale aziendale sul dispositivo. Quando viene registrato tramite JAMF, è necessario ricevere una notifica per aprire l'app self-service per apportare modifiche.

Nell'app Portale aziendale, l'utente potrebbe visualizzare **`Not registered`** e una voce simile a quella dell'esempio seguente potrebbe apparire nei log del portale aziendale:  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**Risoluzione**  
Per modificare l'origine di registrazione da Intune a JAMF:
1. [Annullare la registrazione del dispositivo macOS da Intune](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos). Per evitare ulteriori complicazioni per i dispositivi che non vengono rimossi completamente da Intune, vedere la [*causa 6*](#cause-6) in questo elenco di cause.  

2. Nel dispositivo usare JAMF self service per aprire l'app Portale aziendale e quindi registrare il dispositivo in Intune. Questa attività richiede che sia stato [usato JAMF per distribuire l'app portale aziendale per MacOS](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)e che sia stato [creato un criterio in JAMF Pro che registra il dispositivo degli utenti con Azure ad](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory).  

3. Quando si apre il portale, nella prima schermata viene visualizzato un messaggio in cui viene richiesto di eseguire l'accesso. Usare l'account aziendale o dell'istituto di istruzione  

4. Il portale aziendale verifica le informazioni sull'account e visualizza gli stati relativi a Registrazione del dispositivo e Conformità del dispositivo. Triangoli gialli evidenziano le azioni da eseguire per proteggere il dispositivo macOS per l'istituto di istruzione o il lavoro. Fare clic su Inizia per iniziare la registrazione.  

5. Se richiesto, digitare le informazioni di accesso del computer.  
     
Potrebbero occorrere alcuni minuti per registrare il dispositivo per la gestione. Durante l'attesa è possibile eseguire altre operazioni sul computer. Al termine della configurazione dell'accesso aziendale viene visualizzato un messaggio relativo al completamento dell'operazione.

#### <a name="cause-5"></a>Causa 5  

**L'integrazione di Intune è disattivata**

Se l'integrazione di Intune è disattivata, gli utenti ricevono una finestra popup nel Portale aziendale con il messaggio seguente quando tentano di registrare un dispositivo:  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

Il server JAMF Pro invia un impulso ai server Intune quando l'integrazione è disattivata e indica a Intune che l'integrazione è disabilitata. 

**Risoluzione**  
Abilitare nuovamente l'integrazione di Intune in JAMF Pro. Vedere [Configurare l'integrazione di Microsoft Intune in Jamf Pro](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro).


#### <a name="cause-6"></a>Causa 6  

**Il dispositivo è stato registrato in precedenza in Intune o l'utente ha tentato di registrare il dispositivo più volte**

Se viene annullata la registrazione di un dispositivo da JAMF ma non è stato rimosso correttamente da Intune o vengono eseguiti diversi tentativi di registrazione, è possibile visualizzare più istanze dello stesso dispositivo nel portale. Questo causa la mancata registrazione di JAMF.

**Risoluzione**  
1. Nel Mac avviare il **terminale**.
2. Eseguire **sudo JAMF removemdmprofile**.
3. Eseguire **sudo JAMF removeFramework**.
4. Nel server JAMF Pro eliminare il record di inventario del computer.
5. Eliminare il dispositivo da AzureAD.
6. Se presenti, eliminare i file seguenti nel dispositivo:
   - Supporto di/Libreria/Application/com. Microsoft. file companyportal. UserContext. info
   - Supporto di/Libreria/Application/com. Microsoft. file companyportal
   - Supporto di/Libreria/Application/com. jamfsoftware. selfservice. Mac
   - Applicazione/Library/Saved
   - Stato/com. jamfsoftware. selfservice. Mac. savedState verrà
   - Stato dell'applicazione/Library/Saved/com. Microsoft. file companyportal. savedState verrà
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Utenti/<username>/Library/Cookies/com.microsoft.CompanyPortal.binarycookies
   - /Utenti/<username>/Library/Cookies/com.jamf.management.jamfAAD.binarycookies
   - com. Microsoft. file companyportal
   - com. Microsoft. file companyportal. HockeySDK
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Chiave di trasporto della sessione Microsoft (chiavi pubbliche e private)
   - Chiave di Workplace Join Microsoft (chiavi pubbliche e private)
7. Rimuovere qualsiasi elemento dal Keychain sul dispositivo che fa riferimento a *Microsoft*, *Intune*o *Portale aziendale*, inclusi i certificati DeviceLogin.Microsoft.com. Rimuovere i riferimenti *JAMF* ad eccezione di JAMF Public e private key. 
   > [!IMPORTANT]  
   > Se si rimuove la chiave pubblica e privata, la registrazione del dispositivo non viene interrotta.

8. Eliminare le voci seguenti:  
   - Kind: password dell'applicazione; Account: com. Microsoft. workplacejoin. identificazione personale
   - Kind: password dell'applicazione; Account: com. Microsoft. workplacejoin. registeredUserPrincipalName
   - Kind: certificate; Rilasciato da: MS-Organization-Access
   - Kind: preferenza di identità; Nome (se presente, URL STS ADFS): https://adfs\<DNSName>.com/adfs/ls
   - Kind: preferenza di identità; Nome: https://enterpriseregistration.windows.net
   - Kind: preferenza di identità; Nome: https://enterpriseregistration.windows.net/  
9. Riavviare il dispositivo Mac.
10. Disinstallare Portale aziendale dal dispositivo.
11. Passare a portal.manage.microsoft.com ed eliminare tutte le istanze del dispositivo Mac. Attendere almeno 30 minuti prima di andare al passaggio successivo.
12. Registrare nuovamente il dispositivo in JAMF Pro.
13. Riaprire self-service e avviare i criteri di registrazione.


#### <a name="cause-7"></a>Causa 7  

**JamfAAD richiede l'accesso a una "chiave di Microsoft Workplace Join" dal Keychain degli utenti**

Durante la registrazione, l'utente di un dispositivo macOS riceve la richiesta seguente per consentire l'accesso JamfAAD a una chiave dal Keychain: 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**Risoluzione**  
Per registrare correttamente il dispositivo con Azure AD, JAMF richiede all'utente di fornire la password dell'account e selezionare **Consenti**.

Questa richiesta è simile alla richiesta di conferma per i [dispositivi Mac per l'accesso Keychain quando si apre un'app](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app), più indietro in questo articolo.  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>Il dispositivo Mac Mostra la conformità in Intune ma non è conforme in Azure  

**Motivo**: le condizioni seguenti possono causare la visualizzazione di un dispositivo come conforme in Intune ma non come conforme in Azure:  
- Il dispositivo non è registrato correttamente.  
- Il dispositivo è stato registrato più volte senza la pulizia necessaria.

**Risoluzione**  
Per risolvere questo problema, seguire la [*risoluzione per la*](#cause-6) *mancata registrazione dei dispositivi*, più indietro in questo articolo. 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Le voci duplicate vengono visualizzate nella console di Intune per i dispositivi Mac registrati con JAMF  
 
**Motivo**: un dispositivo viene registrato più volte con Intune, in genere registrato nuovamente dopo essere stato rimosso da Intune.  

Quando un dispositivo viene rimosso dall'integrazione di Intune e JAMF Pro, è possibile che alcuni dati rimangano indietro, che possono causare registrazioni successive per la creazione di voci duplicate.  

**Risoluzione**  
Per risolvere questo problema, seguire la [*risoluzione per la*](#cause-6) *mancata registrazione dei dispositivi*, più indietro in questo articolo. 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>I criteri di conformità non sono in grado di valutare il dispositivo  

**Motivo**: l'integrazione di Jamf con Intune non supporta i criteri di conformità che fanno riferimento a gruppi di dispositivi. 

**Risoluzione**  
Modificare i criteri di conformità per i dispositivi macOS da assegnare ai gruppi di utenti. 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Non è stato possibile recuperare il token di accesso per l'API Microsoft Graph

Viene visualizzato l'errore seguente:

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

L'origine di questo errore può essere una delle seguenti cause: 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Si è verificato un problema di autorizzazione con l'applicazione JAMF Pro in Azure

Durante la registrazione dell'app JAMF Pro in Azure, si è verificata una delle condizioni seguenti:  
- L'app ha ricevuto più di un'autorizzazione.
- Il **consenso dell'amministratore di concessione per *\<l'opzione della > aziendale***  non è stato selezionato.  

**Risoluzione**  
Per la [registrazione dei dispositivi non è possibile eseguire la registrazione](#devices-fail-to-register), più indietro in questo articolo.

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Una licenza necessaria per l'integrazione di JAMF-Intune è scaduta

**Soluzione**: vedere la risoluzione della [mancata registrazione dei dispositivi](#devices-fail-to-register). 

#### <a name="the-required-ports-arent-open-on-your-network"></a>Le porte richieste non sono aperte sulla rete

**Risoluzione**: esaminare le informazioni per le porte di rete in [prerequisiti](conditional-access-integrate-jamf.md#prerequisites) per l'integrazione di JAMF Pro con Intune.


## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sull' [integrazione di JAMF Pro con Intune](conditional-access-integrate-jamf.md)