---
title: Risolvere i problemi di registrazione dei dispositivi
titleSuffix: Microsoft Intune
description: Suggerimenti per la risoluzione dei problemi di registrazione dei dispositivi in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b995841152ee7290e41eed7988ff2b52b6bc66c
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375229"
---
# <a name="troubleshoot-device-enrollment-in-microsoft-intune"></a>Risolvere i problemi di registrazione dei dispositivi in Microsoft Intune

Questo articolo contiene suggerimenti per la risoluzione dei problemi di [registrazione dei dispositivi](device-enrollment.md). Se queste informazioni non consentono di risolvere il problema, vedere [Come ottenere supporto per Microsoft Intune](get-support.md) per trovare altri modi per ottenere assistenza.


## <a name="initial-troubleshooting-steps"></a>Procedure iniziali per la risoluzione dei problemi

Prima di iniziare la risoluzione dei problemi, verificare di aver configurato Intune correttamente per consentire la registrazione. Per informazioni su tali requisiti di configurazione, vedere:

- [Prepararsi alla registrazione dei dispositivi in Microsoft Intune](setup-steps.md)
- [Configurare la gestione dei dispositivi iOS e Mac](ios-enroll.md)
- [Configurare la gestione dei dispositivi Windows](windows-enroll.md)
- [Configurare la gestione dei dispositivi Android](android-enroll.md) - Non sono necessari passaggi aggiuntivi

È anche possibile assicurarsi che la data e l'ora nel dispositivo dell'utente siano impostate correttamente:

1. Riavviare il dispositivo.
2. Assicurarsi che la data e l'ora siano impostate su standard GMT (+ o - 12 ore) per il fuso orario dell'utente finale.
3. Disinstallare e reinstallare il portale aziendale di Intune (se applicabile).

Gli utenti dei dispositivi gestiti possono raccogliere log di registrazione e diagnostica da sottoporre all'analisi dell'amministratore. Le istruzioni per raccogliere i log sono disponibili nell'articolo:

- [Inviare gli errori di registrazione all'amministratore IT](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [Inviare gli errori all'amministratore IT](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>Problemi di registrazione generali
Questi problemi possono verificarsi in tutte le piattaforme di dispositivi.

### <a name="device-cap-reached"></a>Numero massimo dispositivi raggiunto
**Problema:** durante la registrazione viene visualizzato un errore, ad esempio **Portale aziendale temporaneamente non disponibile**, e DMPdownloader.log in Gestione configurazione contiene l'errore **Numero massimo dispositivi raggiunto**.

**Risoluzione:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>Verificare il numero di dispositivi registrati e consentiti.

Verificare che all'utente non siano assegnati più dispositivi rispetto al numero massimo seguendo questa procedura:

1. In Intune scegliere **Registrazione del dispositivo** > **Restrizioni registrazione** > **Restrizione sul limite di dispositivi**. Prendere nota del valore nella colonna **Limite di dispositivi**.

2. In Intune scegliere **Utenti** > **Tutti gli utenti** > selezionare l'utente > **Dispositivi**. Prendere nota del numero di dispositivi.

3. Se il numero di dispositivi registrati per l'utente ha già raggiunto la restrizione sul limite di dispositivi, non è possibile registrarne altri, a meno che:
    - [I dispositivi esistenti vengano rimossi](devices-wipe.md), o
    - Si aumenti il limite di dispositivi[ impostando le restrizioni del dispositivo](enrollment-restrictions-set.md).

Per evitare di raggiungere i limiti dei dispositivi, assicurarsi di rimuovere i record dei dispositivi non aggiornati.

> [!NOTE]
> 
> È possibile evitare il limite di registrazione usando l'account del manager di registrazione dispositivi, come descritto in [Registrare i dispositivi di proprietà dell'azienda con il manager di registrazione dispositivi in Microsoft Intune](device-enrollment-manager-enroll.md).
> 
> Un account utente che viene aggiunto all'account Manager di registrazione dispositivi non sarà in grado di completare la registrazione quando vengono applicati i criteri di accesso condizionale per l'accesso utente specifico.

### <a name="company-portal-temporarily-unavailable"></a>Portale aziendale temporaneamente non disponibile
**Problema:** nel dispositivo viene visualizzato l'errore **Portale aziendale temporaneamente non disponibile**.

**Risoluzione:**

1. Rimuovere l'app Portale aziendale di Intune dal dispositivo.

2. Aprire il browser nel dispositivo, passare a [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) e tentare di eseguire un accesso utente.

3. Se non è possibile accedere, provare a usare un'altra rete.

4. Se il problema persiste, verificare che le credenziali dell'utente siano sincronizzate correttamente con Azure Active Directory.

5. Se l'utente accede correttamente, un dispositivo iOS richiede in genere di installare l'app Portale aziendale di Intune ed eseguire la registrazione. In un dispositivo Android è necessario installare manualmente l'app Portale aziendale di Intune e quindi ripetere il tentativo di registrazione.

### <a name="mdm-authority-not-defined"></a>Autorità MDM non definita
**Problema:** viene visualizzato l'errore **Autorità MDM non definita**.

**Risoluzione:**

1. Verificare che l'autorità MDM sia stata [impostata in modo appropriato](mdm-authority-set.md).
    
2. Verificare che le credenziali dell'utente siano sincronizzate correttamente con Azure Active Directory. È possibile verificare che il nome dell'UPN dell'utente corrisponda alle informazioni di Active Directory nell'interfaccia di amministrazione di Microsoft 365.
    Se il nome dell'entità utente non corrisponde alle informazioni di Active Directory:

    1. Disattivare DirSync sul server locale.

    2. Eliminare l'utente non corrispondente dall'elenco utenti del **portale per gli account di Intune** .

    3. Attendere circa un'ora per consentire al servizio di Azure rimuovere i dati errati.

    4. Attivare nuovamente DirSync e controllare se l'utente è ora sincronizzato correttamente.

3. In uno scenario in cui si usa System Center Configuration Manager con Intune, verificare che l'utente disponga di un ID utente cloud valido:

    1. Aprire SQL Management Studio.

    2. Connettersi al database appropriato.

    3. Aprire la cartella del database, quindi individuare e aprire la cartella **CM_DBName**, dove DBName è il nome del database del cliente.

    4. Nella parte superiore fare clic su **Nuova query** ed eseguire le query seguenti:

        - Per visualizzare tutti gli utenti: `select * from [CM_ DBName].[dbo].[User_DISC]`

        - Per visualizzare utenti specifici, usare la query seguente, in cui %testuser1% è un segnaposto per username@domain.com per l'utente che si vuole cercare: `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        Dopo aver scritto la query, fare clic su **!Execute**.
        Dopo che sono stati restituiti i risultati, cercare l'ID clouduser.  Se non viene trovato alcun ID, l'utente non dispone di una licenza per usare Intune.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Non è possibile creare criteri o registrare dispositivi se il nome della società contiene caratteri speciali
**Problema:** non è possibile creare criteri o registrare dispositivi.

**Risoluzione:** nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/) rimuovere i caratteri speciali dal nome della società e salvare le informazioni aziendali.

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Non è possibile accedere o registrare dispositivi quando si hanno più domini verificati
**Problema:** questo problema può verificarsi quando si aggiunge un secondo dominio verificato ad AD FS. Gli utenti con il suffisso del nome dell'entità utente (UPN) del secondo dominio potrebbero non essere in grado di accedere ai portali o di registrare dispositivi.


<strong>Risoluzione:</strong> i clienti di Microsoft Office 365 devono distribuire un'istanza separata di Active Directory Federation Services (AD FS) 2.0 per ogni suffisso se:
- Usano l'accesso single sign-on (SSO) tramite AD FS 2.0
- Hanno più domini di primo livello per i suffissi UPN degli utenti all'interno dell'organizzazione (ad esempio, @contoso.com o @fabrikam.com).


Un [rollup per AD FS 2.0](http://support.microsoft.com/kb/2607496) interagisce con l'opzione <strong>SupportMultipleDomain</strong> per consentire al server AD FS di supportare questo scenario senza richiedere la presenza di altri server AD FS 2.0. Per altre informazioni, vedere [questo blog](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/).


## <a name="android-issues"></a>Problemi di Android

### <a name="android-enrollment-errors"></a>Errori di registrazione di Android

La tabella seguente elenca gli errori che potrebbero verificarsi quando gli utenti finali registrano i dispositivi Android in Intune.

|Messaggio di errore|Problema|Soluzione|
|---|---|---|
|**L'amministratore IT deve assegnare la licenza per l'accesso**<br>L'amministratore IT non ha concesso l'accesso per l'uso di questa app. Contattare l'amministratore IT per richiedere assistenza o riprovare più tardi.|Il dispositivo non può essere registrato perché l'account dell'utente non ha la licenza necessaria.|Per poter registrare i dispositivi, è necessario che agli utenti venga assegnata la licenza necessaria. Questo messaggio indica che l'utente ha il tipo di licenza errato per l'autorità di gestione dei dispositivi mobili. Ad esempio, verrà visualizzato questo errore se entrambi gli elementi seguenti sono veri:<ol><li>Intune è stato impostato come l'autorità di gestione dei dispositivi mobili</li><li>Utilizzano la licenza di System Center 2012 R2 Configuration Manager.</li></ol>Per altre informazioni, vedere [Assign Intune licenses to your user accounts](/intune/licenses-assign) (Assegnare licenze di Intune agli account utente).|
|**L'amministratore IT deve impostare l'autorità MDM**<br>L'amministratore IT non ha impostato un'autorità MDM. Contattare l'amministratore IT per richiedere assistenza o riprovare più tardi.|L'autorità di gestione dei dispositivi mobili non è stata definita.|L'autorità di gestione dei dispositivi mobili non è stata impostata in Intune. Vedere le informazioni su come [impostare l'autorità di gestione dei dispositivi mobili](/intune/mdm-authority-set).|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>I dispositivi non riescono a collegarsi al servizio Intune e vengono visualizzati come "Non integro" nella console di amministrazione di Intune
**Problema:** alcuni dispositivi Samsung che eseguono Android versioni 4.4.x e 5.x potrebbero non riuscire più a collegarsi al servizio Intune. Se i dispositivi non si collegano:

- Non possono ricevere criteri, app e comandi remoti dal servizio Intune.
- Visualizzano lo stato di gestione **Non integro** nella console di amministrazione.
- Gli utenti protetti da criteri di accesso condizionale potrebbero perdere l'accesso alle risorse aziendali.

Il software Samsung Smart Manager, fornito in alcuni dispositivi Samsung, può disattivare il Portale aziendale Intune e i relativi componenti. Quando il portale aziendale è in stato disattivato, non può essere eseguito in background e non può contattare il servizio Intune.

**Soluzione 1:**

Comunicare agli utenti di avviare manualmente l'app Portale aziendale. Dopo il riavvio dell'app il dispositivo può collegarsi al servizio Intune.

> [!IMPORTANT]
> L'apertura manuale dell'app Portale aziendale è una soluzione temporanea, perché Samsung Smart Manager potrebbe disattivare nuovamente l'app Portale aziendale.

**Soluzione 2:**

Indicare agli utenti di provare a eseguire l'aggiornamento ad Android 6.0. Il problema della disattivazione non si verifica nei dispositivi Android 6.0. Per controllare se è disponibile un aggiornamento, passare a **Impostazioni** > **Info sul dispositivo** > **Scarica aggiornamenti manualmente** > seguire le istruzioni.

**Soluzione 3:**

Se la soluzione 2 non funziona, chiedere agli utenti di eseguire questa procedura per fare in modo che Smart Manager escluda l'app Portale aziendale:

1. Avviare l'app Smart Manager nel dispositivo.

   ![Selezionare l'icona Smart Manager nel dispositivo](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. Scegliere il riquadro **Batteria**.

   ![Selezionare il riquadro Batteria](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. In **Risparmio energetico app** o **Ottimizzazione app** selezionare **Dettaglio**.

   ![Selezionare Dettaglio in Risparmio energetico app o Ottimizzazione app](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. Scegliere **Portale aziendale** nell'elenco delle app.

   ![Selezionare Portale aziendale nell'elenco delle app](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. Scegliere **Disattiva**.

   ![Selezionare Disattiva nella finestra di dialogo Ottimizzazione app](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. In **Risparmio energetico app** o **Ottimizzazione app** verificare che l'app Portale aziendale sia disattivata.

   ![Verificare che l'app Portale aziendale sia disattivata](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Installazione profilo non riuscita
**Problema:** in un dispositivo Android un messaggio indica che **si è verificato un errore di installazione del profilo**.

**Risoluzione:**

1. Verificare che all'utente sia assegnata una licenza appropriata per la versione del servizio Intune in uso.

2. Verificare che il dispositivo non sia già registrato con un altro provider MDM.

3. Verificare che sul dispositivo non sia già installato un profilo di gestione.

4. Verificare che Chrome per Android sia configurato come browser predefinito e che i cookie siano abilitati.

### <a name="android-certificate-issues"></a>Problemi relativi ai certificati di Android

**Problema**: viene visualizzato il messaggio seguente nel dispositivo: *Non è possibile accedere perché un certificato necessario non è presente nel dispositivo.*

**Soluzione 1**:

L'utente potrebbe essere in grado di recuperare il certificato mancante seguendo le istruzioni in [Manca un certificato necessario per il dispositivo](/intune-user-help/your-device-is-missing-a-required-certificate-android). Se l'errore persiste, provare la soluzione 2.

**Soluzione 2**:

Dopo aver immesso le credenziali aziendali ed essere stati reindirizzati per l'accesso federato, gli utenti potrebbero riscontrare l'errore di certificato mancante. In questo caso, l'errore può significare che manca un certificato intermedio nel server Active Directory Federation Services (ADFS)

L'errore di certificato si verifica perché i dispositivi Android richiedono certificati intermedi da includere in un [messaggio Hello del server SSL](https://technet.microsoft.com/library/cc783349.aspx). Attualmente, un'installazione predefinita con server AD FS o server proxy WAP - AD FS invia solo il certificato SSL del servizio AD FS nella risposta Hello del server SSL a un messaggio Hello del client SSL.

Per risolvere il problema, importare i certificati nei certificati personali del computer sul server ADFS o proxy, come indicato di seguito:

1. Nei server ADFS e proxy fare clic con il pulsante destro del mouse su **Start** > **Esegui** > **certlm.msc** per avviare la console Gestione certificati del computer locale.
2. Espandere **Personale** e scegliere **Certificati**.
3. Cercare il certificato per la comunicazione del servizio ADFS (un certificato firmato pubblicamente) e fare doppio clic per visualizzare le relative proprietà.
4. Scegliere la scheda **Percorso certificazione** per visualizzare il o i certificati padre del certificato.
5. Per ogni certificato padre, scegliere **Visualizza certificato**.
6. Scegliere **Dettagli** > **Copia su file...** .
7. Seguire le istruzioni della procedura guidata per esportare o salvare la chiave pubblica del certificato padre nel percorso file desiderato.
8. Fare clic con il pulsante destro del mouse su **Certificati** > **Tutte le attività** > **Importa**.
9. Seguire le indicazioni della procedura guidata per importare i certificati padre in **Computer locale\Personale\Certificati**.
10. Riavviare i server ADFS.
11. Ripetere i passaggi precedenti in tutti i server ADFS e proxy.

Per verificare che l'installazione del certificato sia corretta, è possibile usare lo strumento di diagnostica disponibile in [https://www.digicert.com/help/](https://www.digicert.com/help/). Nella casella **Indirizzo server** immettere il nome di dominio completo del server AD FS (ad esempio: sts.contso.com) e fare clic su **Controllo server**.

**Per convalidare la corretta installazione del certificato**:

I passaggi seguenti descrivono solo uno dei numerosi metodi e strumenti che è possibile usare per convalidare la corretta installazione del certificato.

1. Andare allo [strumento Digicert gratuito](ttps://www.digicert.com/help/).
2. Immettere il nome di dominio completo del server ADFS (ad esempio, sts.contoso.com) e selezionare **CHECK SERVER** (Controllo server)

Se il certificato del server è installato correttamente, nei risultati vengono visualizzati tutti i segni di spunta. Se si verifica il problema sopra riportato, viene visualizzata una X rossa nelle sezioni "Certificate Name Matches" e "SSL Certificate is correctly Installed" del report.


## <a name="ios-issues"></a>Problemi di iOS

### <a name="ios-enrollment-errors"></a>Errori di registrazione per iOS
La tabella seguente elenca gli errori che potrebbero verificarsi quando gli utenti finali registrano i dispositivi iOS in Intune.

|Messaggio di errore|Problema|Soluzione|
|-------------|-----|----------|
|NoEnrollmentPolicy|Non sono stati trovati criteri di registrazione|Verificare che siano stati configurati tutti i prerequisiti di registrazione, ad esempio il certificato APNS (Apple Push Notification Service), e che sia abilitato "iOS come piattaforma". Per le istruzioni, vedere [Configurare la gestione dei dispositivi iOS e Mac](ios-enroll.md).|
|DeviceCapReached|Sono già stati registrati troppi dispositivi mobili.|L'utente deve rimuovere dal Portale aziendale uno dei dispositivi mobili attualmente registrati prima di poterne registrare un altro. Vedere le istruzioni relative al tipo di dispositivo in uso: [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios), [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|Si è verificato un problema con il certificato che consente al dispositivo mobile di comunicare con la rete aziendale.<br /><br />|Apple Push Notification Service (APNS) offre un canale per contattare i dispositivi iOS registrati. La registrazione avrà esito negativo e verrà visualizzato questo messaggio se:<ul><li>Non sono stati completati i passaggi per ottenere un certificato del servizio APN oppure</li><li>Il certificato del servizio APN è scaduto.</li></ul>Esaminare le informazioni sulla configurazione degli utenti in [Sincronizzare Active Directory e aggiungere utenti a Intune](users-add.md) e [Organizzazione di utenti e dispositivi](groups-add.md).|
|AccountNotOnboarded|Si è verificato un problema con il certificato che consente al dispositivo mobile di comunicare con la rete aziendale.<br /><br />|Apple Push Notification Service (APNS) offre un canale per contattare i dispositivi iOS registrati. La registrazione avrà esito negativo e verrà visualizzato questo messaggio se:<ul><li>Non sono stati completati i passaggi per ottenere un certificato del servizio APN oppure</li><li>Il certificato del servizio APN è scaduto.</li></ul>Per altre informazioni, vedere [Configurare la gestione dei dispositivi iOS e Mac con Microsoft Intune](ios-enroll.md).|
|DeviceTypeNotSupported|È possibile che l'utente abbia cercato di eseguire la registrazione con un dispositivo non iOS. Il tipo di dispositivo mobile che si sta provando a registrare non è supportato.<br /><br />Verificare che il dispositivo esegua iOS 8.0 o versione successiva.<br /><br />|Verificare che nel dispositivo dell'utente sia in esecuzione iOS 8.0 o versione successiva.|
|UserLicenseTypeInvalid|Il dispositivo non può essere registrato perché l'account utente non è ancora membro di un gruppo di utenti richiesto.<br /><br />|Per poter registrare i loro dispositivi, gli utenti devono essere membri del gruppo di utenti appropriato. Questo messaggio indica che l'utente ha il tipo di licenza errato per l'autorità di gestione dei dispositivi mobili. Ad esempio, verrà visualizzato questo errore se entrambi gli elementi seguenti sono veri:<ol><li>Intune è stato impostato come l'autorità di gestione dei dispositivi mobili</li><li>Utilizzano la licenza di System Center 2012 R2 Configuration Manager.</li></ol>Rivedere gli articoli seguenti per altre informazioni:<br /><br />Vedere l'articolo [Configurare la gestione dei dispositivi iOS e Mac con Microsoft Intune](ios-enroll.md) e le informazioni sulla configurazione degli utenti in [Sincronizzare Active Directory e aggiungere utenti a Intune](users-add.md) e [Organizzazione di utenti e dispositivi](groups-add.md).|
|MdmAuthorityNotDefined|L'autorità di gestione dei dispositivi mobili non è stata definita.<br /><br />|L'autorità di gestione dei dispositivi mobili non è stata impostata in Intune.<br /><br />Rivedere il primo punto del "Passaggio 6: Registrare dispositivi mobili e installare un'app" in [Iniziare con una versione di valutazione gratuita di 30 giorni di Microsoft Intune](free-trial-sign-up.md).|

### <a name="devices-are-inactive-or-the-admin-console-cant-communicate-with-them"></a>I dispositivi sono inattivi o la console di amministrazione non è in grado di comunicare con i dispositivi
**Problema:** i dispositivi iOS non si collegano al servizio Intune. È necessario che i dispositivi si colleghino regolarmente al servizio per mantenere l'accesso alle risorse aziendali protette. Se i dispositivi non si collegano:

- Non possono ricevere criteri, app e comandi remoti dal servizio Intune.
- Visualizzano lo stato di gestione **Non integro** nella console di amministrazione.
- Gli utenti protetti da criteri di accesso condizionale potrebbero perdere l'accesso alle risorse aziendali.

**Risoluzione:** comunicare le risoluzioni seguenti agli utenti finali per consentire loro di ripristinare l'accesso alle risorse aziendali.

Quando gli utenti avviano l'app Portale aziendale iOS, l'app può indicare se il dispositivo ha perso il collegamento con Intune. Se viene rilevata la mancanza di collegamento, l'app tenta automaticamente di eseguire la sincronizzazione con Intune per ristabilire il collegamento e agli utenti viene visualizzata la notifica inline **Tentativo di sincronizzazione…** .

  ![Notifica Tentativo di sincronizzazione](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

Se la sincronizzazione ha esito positivo, viene visualizzata la notifica inline **La sincronizzazione è riuscita** nell'app Portale aziendale iOS che indica che il dispositivo funziona correttamente.

  ![Notifica La sincronizzazione è riuscita](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

Se la sincronizzazione non viene eseguita, viene visualizzata la notifica inline **Non è possibile eseguire la sincronizzazione** nell'app Portale aziendale iOS.

  ![Notifica Non è possibile eseguire la sincronizzazione](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

Per risolvere il problema, è necessario che gli utenti selezionino il pulsante **Configura** a destra della notifica **Non è possibile eseguire la sincronizzazione**. Il pulsante Configura visualizza la schermata Configurazione dell'accesso aziendale con istruzioni per la registrazione del dispositivo.

  ![Schermata di configurazione dell'accesso aziendale](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

Dopo aver eseguito la registrazione, vengono ripristinati il corretto funzionamento dei dispositivi e l'accesso alle risorse aziendali.

### <a name="verify-ws-trust-13-is-enabled"></a>Verificare che WS-Trust 1.3 sia abilitato
**Problema** I dispositivi iOS Device Enrollment Program (DEP) non possono essere registrati

La registrazione dei dispositivi DEP con affinità utente richiede un endpoint WS-Trust 1.3 Username/Mixed per essere abilitato a richiedere token utente. Active Directory abilita questo endpoint per impostazione predefinita. Per ottenere un elenco di endpoint abilitati, usare il cmdlet Get-AdfsEndpoint di PowerShell e cercare l'endpoint trust/13/UsernameMixed. Ad esempio:

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

Per altre informazioni, vedere la [documentazione di Get-AdfsEndpoint](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

Per altre informazioni, vedere [Procedure consigliate per la protezione di Active Directory Federation Services](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs). Per informazioni su come determinare se WS-Trust 1.3 Username/Mixed è abilitato nel provider di identità WS-Federation:
- Contattare il supporto tecnico Microsoft se si usa AD FS
- Contattare il fornitore di identità di terze parti.


### <a name="profile-installation-failed"></a>Installazione profilo non riuscita
**Problema:** in un dispositivo iOS un messaggio indica che **si è verificato un errore di installazione del profilo**.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Risoluzione dell'errore di installazione del profilo

1. Verificare che all'utente sia assegnata una licenza appropriata per la versione del servizio Intune in uso.

2. Verificare che il dispositivo non sia già registrato con un altro provider MDM.

3. Verificare che sul dispositivo non sia già installato un profilo di gestione.

4. Passare a [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) e provare a installare il profilo quando richiesto.

5. Verificare che Safari per iOS sia configurato come browser predefinito e che i cookie siano abilitati.

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>Il dispositivo iOS registrato non viene visualizzato nella console quando si usa System Center Configuration Manager con Intune
**Problema:** l'utente registra il dispositivo iOS, ma non viene visualizzato nella console di amministrazione di Configuration Manager. Il dispositivo non indica che è stato registrato. Cause possibili:

- Microsoft Intune Connector nel sito di Configuration Manager non comunica con il servizio Intune.
- Il componente di gestione dei dati di individuazione (ddm) o il componente Gestione stati (statmgr) non elabora i messaggi dal servizio di Intune.
- È possibile che il certificato MDM sia stato scaricato da un account e usato con un altro account.


**Risoluzione:** esaminare i file di log seguenti per individuare possibili errori:

- dmpdownloader.log
- ddm.log
- statmgr.log

Presto verranno aggiunti esempi su cosa cercare in questi file di log.


### <a name="users-ios-device-is-stuck-on-an-enrollment-screen-for-more-than-10-minutes"></a>Il dispositivo iOS dell'utente è bloccato in una schermata di registrazione da più di 10 minuti

**Problema**: la registrazione di un dispositivo potrebbe rimanere bloccata in una delle due schermate seguenti:
- Attesa della configurazione finale da "Microsoft"
- App Guided Access non disponibile. Contattare l'amministratore.

Questo problema può verificarsi se:
- Si verifica un'interruzione temporanea dei servizi Apple oppure
- La configurazione della registrazione di iOS prevede l'uso di token VPP, come illustrato nella tabella, ma c'è un problema con il token VPP.

| Impostazioni di registrazione | Valore |
| ---- | ---- |
| Piattaforma | iOS |
| Affinità utente | Registra con affinità utente |
|Autenticazione tramite il portale aziendale anziché con l'assistente alla configurazione di Apple | Sì |
| Installa il Portale aziendale con VPP | Usare il token: indirizzo del token |
| Eseguire il portale aziendale nella modalità app singola fino all'autenticazione | Sì |

**Risoluzione**: per risolvere il problema, è necessario:
1. Determinare se è presente un problema con il token VPP e risolverlo.
2. Identificare i dispositivi bloccati.
3. Cancellare i dati dei dispositivi interessati.
4. Chiedere all'utente di riavviare il processo di registrazione.

#### <a name="determine-if-theres-something-wrong-with-the-vpp-token"></a>Determinare se è presente un problema con il token VPP
1. Passare a **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP** > nome del token > **Profili** > nome del profilo > **Gestisci** > **Proprietà**.
2. Esaminare le proprietà per controllare se vengono visualizzati errori simili al seguente:
    - Il token è scaduto.
    - Il token non rientra tra le licenze di Portale aziendale.
    - Il token viene utilizzato da un altro servizio.
    - Il token viene utilizzato da un altro tenant.
    - Il token è stato eliminato.
3. Risolvere i problemi del token.

#### <a name="identify-which-devices-are-blocked-by-the-vpp-token"></a>Identificare i dispositivi bloccati dal token VPP
1. Passare a **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP** > nome del token > **Dispositivi**.
2. Filtrare la colonna dello **stato del profilo** in base a **Bloccato**.
3. Prendere nota dei numeri di serie dei dispositivi con stato **Bloccato**.

#### <a name="remotely-wipe-the-blocked-devices"></a>Cancellare in remoto i dati dei dispositivi bloccati
Dopo aver risolto i problemi del token VPP, è necessario cancellare i dati dei dispositivi che sono bloccati.
1. Passare a **Intune** > **Dispositivi** > **Tutti i dispositivi** > **Colonne**  >  **Numero di serie** > **Applica**. 
2. Selezionare ogni dispositivo bloccato nell'elenco **Tutti i dispositivi** e quindi scegliere **Cancella** > **Sì**.

#### <a name="tell-the-users-to-restart-the-enrollment-process"></a>Chiedere agli utenti di riavviare il processo di registrazione
Dopo aver cancellato i dispositivi bloccati, chiedere agli utenti di riavviare il processo di registrazione.

## <a name="macos-issues"></a>Problemi relativi a macOS

### <a name="macos-enrollment-errors"></a>Errori di registrazione per macOS
**Messaggio di errore 1:** *Si sta usando una macchina virtuale. Assicurarsi che la macchina virtuale sia stata configurata completamente, inclusi il numero di serie e il modello. Se questa non è una macchina virtuale, contattare il supporto tecnico.*  

**Messaggio di errore 2:** *We’re having trouble getting your device managed. This problem could be caused if you're using a virtual machine, have a restricted serial number, or if this device is already assigned to someone else. Learn how to resolve these problems or contact your company support. (Si sono verificati problemi nella configurazione del dispositivo come gestito. Il problema potrebbe essere dovuto all'uso di una macchina virtuale, alla presenza di un numero di serie con restrizioni o al fatto che il dispositivo sia già assegnato a un altro utente. Informazioni su come risolvere questi problemi o contattare il supporto tecnico aziendale.)*

**Problema:** questo messaggio potrebbe essere il risultato di uno qualsiasi dei motivi seguenti:  
* Una macchina di virtuale macOS non è configurata correttamente  
* Sono state abilitate restrizioni del dispositivo che richiedono che esso sia di proprietà dell'azienda o abbia un numero di serie registrato in Intune  
* Il dispositivo è già stato registrato ed è ancora assegnato a un altro utente in Intune  

**Risoluzione:** per prima cosa verificare con l'utente quali problemi interessano il dispositivo. Eseguire quindi la più pertinente tra le soluzioni indicate di seguito:
* Se l'utente sta registrando una macchina virtuale per il test, verificare che sia stata completamente configurata in modo che Intune possa riconoscerne il numero di serie e il modello hardware. Altre informazioni su come [configurare le macchine virtuali](macos-enroll.md#enroll-virtual-macos-machines-for-testing) in Intune.  
* Se l'organizzazione ha attivato restrizioni di registrazione che bloccano i dispositivi macOS personali, è necessario procedere manualmente per [aggiungere il numero di serie del dispositivo personale](corporate-identifiers-add.md#manually-enter-corporate-identifiers) a Intune.  
* Se il dispositivo è ancora assegnato a un altro utente in Intune, il proprietario precedente non ha usato l'app Portale aziendale per rimuoverlo o ripristinarlo. Per pulire il record del dispositivo non aggiornato da Intune:  

    1. Andare a [Intune nel portale di Azure](https://portal.manage.microsoft.com) e accedere con le proprie credenziali amministrative.
    2. Andare a Intune > **Dispositivi** > **Tutti i dispositivi**.  
    3. Trovare il dispositivo che presenta il problema di registrazione. Eseguire la ricerca in base al nome del dispositivo o all'indirizzo MAC/HW per limitare i risultati.
    4. Selezionare il dispositivo > **Elimina**. Eliminare tutte le altre voci associate al dispositivo.  

## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>Problemi durante l'uso di System Center Configuration Manager con Intune
### <a name="mobile-devices-disappear"></a>I dispositivi mobili scompaiono
**Problema:** dopo la registrazione in Configuration Manager, il dispositivo mobile viene eliminato dalla raccolta. Tuttavia, il dispositivo ha ancora il profilo di gestione ed è elencato nel Gateway CSS.

**Risoluzione:** questo problema può verificarsi perché:
- È presente un processo personalizzato che rimuove i dispositivi non appartenenti a un dominio oppure 
- L'utente ha ritirato il dispositivo dalla sottoscrizione.
Per convalidare e verificare quale processo o account utente ha rimosso il dispositivo dalla console di Configuration Manager, attenersi alla procedura seguente.

#### <a name="check-how-device-was-removed"></a>Controllare in che modo è stato rimosso il dispositivo

1. Nella console di amministrazione di Configuration Manager selezionare **Monitoraggio** &gt; **Stato del sistema** &gt; **Query messaggi di stato**.

2. Fare clic con il pulsante destro del mouse su **Risorse dei membri raccolta eliminate manualmente** e scegliere **Mostra messaggi**.

3. Selezionare una data e un'ora appropriate o le ultime 12 ore.

4. Trovare il dispositivo in questione ed esaminare in che modo è stato rimosso. L'esempio seguente mostra che l'account SCCMInstall ha eliminato il dispositivo tramite un'applicazione sconosciuta.

    ![Schermata per la diagnosi dell'eliminazione del dispositivo](./media/troubleshoot-device-enrollment-in-intune/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5. Verificare che in Configuration Manager non sia presente un'attività pianificata, uno script o un altro processo che potrebbe eliminare automaticamente dispositivi mobili o non appartenenti a un dominio oppure dispositivi correlati.

### <a name="other-ios-enrollment-errors"></a>Altri errori di registrazione di iOS
Un elenco degli errori di registrazione di iOS è disponibile nella documentazione in [Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune) (Risoluzione dei problemi di registrazione dei dispositivi iOS in Microsoft Intune).

## <a name="pc-issues"></a>Problemi relativi al PC

|Messaggio di errore|Problema|Soluzione|
|---|---|---|
|**L'amministratore IT deve assegnare la licenza per l'accesso**<br>L'amministratore IT non ha concesso l'accesso per l'uso di questa app. Contattare l'amministratore IT per richiedere assistenza o riprovare più tardi.|Il dispositivo non può essere registrato perché l'account dell'utente non ha la licenza necessaria.|Per poter registrare i dispositivi, è necessario che agli utenti venga assegnata la licenza necessaria. Questo messaggio indica che l'utente ha il tipo di licenza errato per l'autorità di gestione dei dispositivi mobili. Ad esempio, verrà visualizzato questo errore se entrambi gli elementi seguenti sono veri: <ol><li>Intune è stato impostato come l'autorità di gestione dei dispositivi mobili</li><li>Utilizzano la licenza di System Center 2012 R2 Configuration Manager.</li></ol>Vedere le informazioni su [come assegnare le licenze di Intune agli account utente](https://docs.microsoft.com/intune/licenses-assign).|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>The machine is already enrolled (Il computer è già registrato) - Errore hr 0x8007064c
**Problema:** la registrazione non riesce e genera l'errore **The machine is already enrolled** (Il computer è già registrato). Il log di registrazione visualizza l'errore **hr 0x8007064c**.

Questo errore può verificarsi perché il computer:
- È stato registrato in precedenza oppure
- Contiene l'immagine clonata di un computer che era già registrato.
Il certificato dell'account precedente è ancora presente nel computer.

**Risoluzione:**

1. Dal menu **Start** digitare **Esegui** -> **MMC**.
1. Scegliere **File** > **Aggiungi o rimuovi snap-in**.
1. Fare doppio clic su **Certificati**, scegliere **Account del computer** > **Avanti** e selezionare **Computer locale**.
1. Fare doppio clic su **Certificati (computer locale)** e scegliere **Certificati personali**.
1. Cercare il certificato Intune rilasciato da Sc_Online_Issuing e, se presente, eliminarlo.
1. Se presente, eliminare la chiave del Registro di sistema **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** e tutte le sottochiavi.
1. Provare a eseguire nuovamente la registrazione.
1. Se la registrazione del PC ancora non riesce, cercare la chiave seguente e, se presente, eliminarla: **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.
1. Provare a eseguire nuovamente la registrazione.

    > [!IMPORTANT]
    > Questa sezione, metodo o attività contiene procedure che spiegano come modificare il Registro di sistema. L'errata modifica del Registro di sistema può tuttavia causare problemi gravi. Verificare quindi di attenersi attentamente alla procedura. Per una maggiore protezione, eseguire il backup del Registro di sistema prima di modificarlo. In caso di problemi, sarà quindi possibile ripristinare il Registro di sistema.
    > Per altre informazioni su come eseguire il backup e il ripristino del Registro di sistema, leggere [Come eseguire il backup e il ripristino del Registro di sistema in Windows](https://support.microsoft.com/kb/322756)

## <a name="general-enrollment-error-codes"></a>Codici degli errori di registrazione generali

|Codice errore|Possibile problema|Soluzione suggerita|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |L'orologio del computer client non è impostato sull'ora corretta.|Assicurarsi che l'orologio e il fuso orario nel computer client siano impostati sull'ora e sul fuso orario corretti.|
|0x80240438, 0x80CF0438, 0x80CF402C|Impossibile connettersi al servizio Intune. Verificare le impostazioni proxy del client.|Verificare che Intune supporti la configurazione del proxy nel computer client. Verificare che il computer sia dotato dell'accesso a Internet.|
|0x80240438, 0x80CF0438|Non sono configurate impostazioni proxy in Internet Explorer e nel sistema locale.|Impossibile connettersi al servizio Intune. Verificare le impostazioni proxy del client. Verificare che Intune supporti la configurazione del proxy nel computer client. Verificare che il computer sia dotato dell'accesso a Internet.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|Il pacchetto di registrazione non è aggiornato.|Scaricare e installare il pacchetto del software client più recente dall'area di lavoro Amministrazione.|
|0x80043002, 0x80CF3002|L'account è in modalità di manutenzione.|Quando l'account è in modalità di manutenzione, non è possibile registrare nuovi computer client. Per visualizzare le impostazioni dell'account, accedere al proprio account.|
|0x80043003, 0x80CF3003|L'account è stato eliminato.|Verificare che l'account e la sottoscrizione a Intune siano ancora attivi. Per visualizzare le impostazioni dell'account, accedere al proprio account.|
|0x80043005, 0x80CF3005|Il computer client è stato rimosso.|Attendere alcune ore, rimuovere le versioni precedenti del software client dal computer, quindi riprovare a installare il software client.|
|0x80043006, 0x80CF3006|È stato raggiunto il numero massimo di postazioni consentito per l'account.|L'organizzazione deve acquistare ulteriori postazioni prima che sia possibile registrare più computer client nel servizio.|
|0x80043007, 0x80CF3007|Impossibile trovare il file del certificato nella stessa cartella del programma di installazione.|Estrarre tutti i file prima di avviare l'installazione. Non rinominare o spostare alcun file estratto: tutti i file devono trovarsi nella stessa cartella altrimenti l'installazione non riuscirà.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|È impossibile installare il software perché un riavvio del computer client è in sospeso.|Riavviare il computer, quindi riprovare a installare il software client.|
|0x80070032|Uno o più prerequisiti per l'installazione del software client non sono stati individuati nel computer client.|Assicurarsi che tutti gli aggiornamenti necessari siano installati nel computer client, quindi riprovare a installare il software client.|
|0x80043008, 0x80CF3008|Impossibile avviare il servizio Microsoft Online Management Updates.|Contattare il supporto tecnico di Microsoft, come descritto in [Come ottenere supporto per Microsoft Intune](get-support.md).|
|0x80043009, 0x80CF3009|Il computer client è già registrato al servizio.|È necessario ritirare il computer client prima di potersi registrare nuovamente al servizio.|
|0x8004300B, 0x80CF300B|È impossibile eseguire l'installazione del software client perché la versione di Windows in esecuzione nel client non è supportata.|Intune non supporta la versione di Windows in esecuzione nel computer client.|
|0xAB2|Windows Installer non è in grado di accedere al runtime VBScript per un'azione personalizzata.|L'errore è causato da un'azione personalizzata basata sulle librerie a collegamento dinamico (DLL). Durante la risoluzione dei problemi del file DLL, potrebbe essere necessario usare gli strumenti descritti nell'[articolo del supporto tecnico Microsoft KB198038: Strumenti utili per i problemi relativi a pacchetti e distribuzione](https://support.microsoft.com/kb/198038).|
|0x80cf0440|La connessione all'endpoint del servizio è stata terminata.|L'account di valutazione o a pagamento è sospeso. Creare un nuovo account di prova o a pagamento ed eseguire nuovamente la registrazione.|




## <a name="next-steps"></a>Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](get-support.md).
