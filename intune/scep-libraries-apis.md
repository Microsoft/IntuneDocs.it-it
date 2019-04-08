---
title: API per l'onboarding di autorità di certificazione di terze parti
titleSuffix: Microsoft Intune
description: Aggiungere o integrare la soluzione SCEP di GitHub per le autorità di certificazione di terze parti (CA) per rilasciare certificati SCEP ai dispositivi in Microsoft Intune. Questa soluzione include Java e API C# che consentono di convalidare, inviare notifiche di esito positivo e negativo a Intune e usare SSL Socket Factory durante la comunicazione con Intune. Visualizzano inoltre una panoramica delle operazioni da eseguire per testare la configurazione dell'autorità di certificazione SCEP.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bf5a9d509bd390561614f59fdce208e8e9f10dde
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799621"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>Usare le API per aggiungere a Intune autorità di certificazione di terze parti per SCEP

In Microsoft Intune è possibile aggiungere autorità di certificazione di terze parti (CA) e fare in modo che queste autorità emettano e convalidino i certificati usando il protocollo SCEP (Simple Certificate Enrollment Protocol). La sezione relativa all'[aggiunta delle autorità di certificazione di terze parti](certificate-authority-add-scep-overview.md) offre una panoramica di questa funzionalità e descrive le attività di amministrazione di Intune.

Esistono anche alcune attività per gli sviluppatori che usano una libreria open source pubblicata da Microsoft in GitHub.com. La libreria include un'API che:

- Convalida la password SCEP generata dinamicamente da Intune
- Notifica a Intune la creazione dei certificati per i dispositivi che inviano richieste SCEP

Usando questa API, il server SCEP di terze parti si integra con la soluzione di gestione SCEP di Intune per i dispositivi MDM. La libreria astrae aspetti come l'autenticazione, la posizione del servizio e l'API dei servizi OData di Intune dagli utenti.

## <a name="scep-management-solution"></a>Soluzione di gestione SCEP

![In che modo un'autorità di certificazione di terze parti SCEP si integra con Microsoft Intune](./media/scep-certificate-vendor-integration.png)

Con Intune gli amministratori creano i profili SCEP e quindi li assegnano ai dispositivi MDM. I profili SCEP includono alcuni parametri, ad esempio:

- L'URL del server SCEP
- Il certificato radice trusted dell'autorità di certificazione
- Gli attributi del certificato e altro ancora

Il profilo SCEP viene assegnato ai dispositivi che eseguono l'archiviazione con Intune e sono configurati con questi parametri. In Intune viene creata una password di verifica SCEP generata dinamicamente, che viene assegnata al dispositivo.

Questa verifica contiene:

- La password di verifica generata dinamicamente
- Le informazioni dettagliate sui parametri previsti nella richiesta di firma del certificato inviata dal dispositivo al server SCEP
- L'ora di scadenza della verifica

Intune esegue la crittografia di queste informazioni, firma il BLOB crittografato e quindi inserisce questi dettagli nella password di verifica SCEP.

I dispositivi che contattano il server SCEP per richiedere un certificato specificano questa password di verifica SCEP. Il server SCEP invia a Intune per la convalida la richiesta di firma del certificato e la password di verifica SCEP crittografata.  La password di verifica e la richiesta di firma del certificato devono superare la convalida perché il server SCEP invii un certificato al dispositivo. Quando una verifica SCEP viene convalidata, vengono eseguiti questi controlli:


- Convalida la firma del BLOB crittografato
- Conferma che la richiesta di verifica non è ancora scaduta
- Verifica che il profilo sia ancora assegnato al dispositivo
- Verifica che le proprietà del certificato richieste dal dispositivo in CSR corrispondano ai valori previsti

La soluzione di gestione di SCEP include anche la creazione di report. Un amministratore può ottenere informazioni sullo stato della distribuzione del profilo SCEP e sui certificati rilasciati ai dispositivi.

## <a name="integrate-with-intune"></a>Integrazione con Intune

Il codice per la libreria da integrare con il protocollo SCEP di Intune è disponibile per il download nel [repository GitHub Microsoft/Intune-Resource-Access](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation).

L'integrazione della libreria nei prodotti prevede i passaggi seguenti. Questi passaggi richiedono familiarità con l'uso dei repository GitHub e la creazione di soluzioni e progetti in Visual Studio.

1. Registrarsi per ricevere notifiche dal repository
2. Clonare o scaricare il repository
3. Andare all'implementazione della libreria necessaria nella cartella `\src\CsrValidation` (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
4. Compilare la libreria usando le istruzioni del file Leggimi
5. Includere la libreria del progetto che compila il server SCEP
6. Completare le attività seguenti nel server SCEP:

    - Consentire all'amministratore di configurare [l'identificatore applicazione Azure, la chiave applicazione Azure e l'ID tenant](#onboard-scep-server-in-azure) (in questo articolo) usati dalla libreria per l'autenticazione. Gli amministratori devono essere autorizzati ad aggiornare la chiave dell'applicazione Azure.
    - Identificare le richieste SCEP che includono una password SCEP generata da Intune
    - Usare la libreria di **API di richiesta di convalida** per convalidare le password SCEP generate da Intune
    - Usare le API di notifica della libreria per notificare a Intune i certificati emessi per le richieste SCEP che usano password SCEP generate da Intune. Notificare anche a Intune eventuali errori che possono verificarsi durante l'elaborazione di tali richieste SCEP.
    - Verificare che il server registri informazioni sufficienti per consentire agli amministratori di risolvere i problemi

7. Completare i [test di integrazione](#integration-testing) (in questo articolo) e risolvere eventuali problemi
8. Offrire ai clienti materiale sussidiario che spieghi:

    - In che modo deve essere eseguito l'onboarding del server SCEP nel portale di Azure
    - In che modo si ottengono l'identificatore applicazione Azure e la chiave applicazione Azure necessari per configurare la libreria

### <a name="onboard-scep-server-in-azure"></a>Eseguire l'onboarding del server SCEP in Azure

Per eseguire l'autenticazione per Intune, il server SCEP richiede un ID applicazione Azure, una chiave applicazione Azure e un ID tenant. Il server SCEP deve anche essere autorizzato ad accedere all'API di Intune.

Per ottenere questi dati, l'amministratore del server SCEP accede al portale di Azure, registra l'applicazione, assegna all'applicazione l'autorizzazione per la **convalida della richiesta di verifica API/SCEP di Microsoft Intune**, crea una chiave per l'applicazione e quindi scarica l'ID dell'applicazione, la relativa chiave e l'ID tenant.

Per informazioni sulla registrazione delle applicazioni e su come ottenere ID e chiavi, vedere [Usare il portale per creare un'applicazione Azure Active Directory e un'entità servizio che possano accedere alle risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

### <a name="java-library-api"></a>API della libreria Java

La libreria Java viene implementata come un progetto Maven che esegue il pull delle proprie dipendenze mentre viene compilato. L'API viene implementata sotto lo spazio dei nomi `com.microsoft.intune.scepvalidation` dalla classe `IntuneScepServiceClient`.

#### <a name="intunescepserviceclient-class"></a>Classe IntuneScepServiceClient

La classe `IntuneScepServiceClient` include i metodi usati dal servizio di SCEP per convalidare le password SCEP, per notificare a Intune i certificati creati e per indicare eventuali errori.

##### <a name="intunescepserviceclient-constructor"></a>Costruttore IntuneScepServiceClient

Firma:

```java
IntuneScepServiceClient(
    Properties configProperties)
```

Descrizione:

Crea e configura un oggetto `IntuneScepServiceClient`.

Parametri:

    - configProperties    Properties object containing client configuration information

La configurazione deve includere le proprietà seguenti:

    - AAD_APP_ID="The Azure Application Id obtained during the onboarding process"
    - AAD_APP_KEY="The Azure Application Key obtained during the onboarding process"
    - TENANT="The Tenant Id obtained during the onboarding process"
    - PROVIDER_NAME_AND_VERSION="Information used to identify your product and its version"
    
Se la soluzione richiede un proxy con autenticazione o senza autenticazione, è possibile aggiungere le proprietà seguenti:

    - PROXY_HOST="L'host che ospita il proxy."
    - PROXY_PORT="La porta su cui il proxy è in ascolto."
    - PROXY_USER="Il nome utente da utilizzare se il proxy usa l'autenticazione di base."
    - PROXY_PASS="La password da utilizzare se il proxy usa l'autenticazione di base."

Genera:

    - IllegalArgumentException    Thrown if the constructor is executed without a proper property object.

> [!IMPORTANT]
> È opportuno creare un'istanza di questa classe e usarla per elaborare più richieste SCEP. In questo modo si riduce il sovraccarico, poiché i token di autenticazione e le informazioni sulla posizione del servizio vengono memorizzati nella cache.

**Note sulla sicurezza**  
Il responsabile dell'implementazione del server SCEP deve proteggere da manomissioni e divulgazione i dati immessi nelle proprietà di configurazione persistenti nella risorsa di archiviazione. È consigliabile usare la crittografia e gli elenchi di controllo di accesso appropriati per proteggere le informazioni.

##### <a name="validaterequest-method"></a>Metodo ValidateRequest

Firma:

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

Descrizione:

Convalida una richiesta di certificato SCEP.

Parametri:

    - transactionId         The SCEP Transaction Id
    - certificateRequest    DER-encoded PKCS #10 Certificate Request Base64 encoded as a string

Genera:

    - IllegalArgumentException      Thrown if called with a parameter that is not valid
    - IntuneScepServiceException    Thrown if it is found that the certificate request is not valid
    - Exception                     Thrown if an un-expected error is encountered

> [!IMPORTANT]
> Le eccezioni generate da questo metodo devono essere registrate dal server. Si noti che le proprietà `IntuneScepServiceException` contengono informazioni dettagliate sulle cause della mancata convalida della richiesta di certificato.

**Note sulla sicurezza**  

  - Se questo metodo genera un'eccezione, il server SCEP **non deve** emettere un certificato per il client.
  - Gli errori di convalida della richiesta del certificato SCEP possono indicare un problema nell'infrastruttura di Intune. Oppure, indicare che un utente malintenzionato sta cercando di ottenere un certificato.

##### <a name="sendsuccessnotification-method"></a>Metodo SendSuccessNotification

Firma:

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

Descrizione:

Indica a Intune che un certificato viene creato come parte dell'elaborazione di una richiesta SCEP.

Parametri:

    - transactionId           The SCEP Transaction Id
    - certificateRequest      DER-encoded PKCS #10 Certificate Request Base64 encoded as a string
    - certThumprint           Thumbprint of the provisioned certificate
    - certSerialNumber        Serial number of the provisioned certificate
    - certExpirationDate      Expiration date of the provisioned certificate. The date time string should be formatted as web UTC time (YYYY-MM-DDThh:mm:ss.sssTZD) ISO 8601.
    - certIssuingAuthority    Name of the authority that issued the certificate

Genera:

    - IllegalArgumentException      Thrown if called with a parameter that is not valid
    - IntuneScepServiceException    Thrown if it is found that the certificate request is not valid
    - Exception                     Thrown if an un-expected error is encountered

> [!IMPORTANT]
> Le eccezioni generate da questo metodo devono essere registrate dal server. Si noti che le proprietà `IntuneScepServiceException` contengono informazioni dettagliate sulle cause della mancata convalida della richiesta di certificato.

**Note sulla sicurezza**

  - Se questo metodo genera un'eccezione, il server SCEP **non deve** emettere un certificato per il client.
  - Gli errori di convalida della richiesta del certificato SCEP possono indicare un problema nell'infrastruttura di Intune. Oppure, indicare che un utente malintenzionato sta cercando di ottenere un certificato.

##### <a name="sendfailurenotification-method"></a>Metodo SendFailureNotification

Firma:

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

Descrizione:

Notifica a Intune che si è verificato un errore durante l'elaborazione di una richiesta SCEP. Questo metodo non deve essere richiamato per le eccezioni generate dai metodi di questa classe.

Parametri:

    - transactionId         The SCEP Transaction Id
    - certificateRequest    DER-encoded PKCS #10 Certificate Request Base64 encoded as a string
    - hResult               Win32 error code that best describes the error that was encountered. See [Win32 Error Codes](https://msdn.microsoft.com/library/cc231199.aspx)
    - errorDescription      Description of the error encountered

Genera:

    - IllegalArgumentException      Thrown if called with a parameter that is not valid
    - IntuneScepServiceException    Thrown if it is found that the certificate request is not valid
    - Exception                     Thrown if an un-expected error is encountered

> [!IMPORTANT]
> Le eccezioni generate da questo metodo devono essere registrate dal server. Si noti che le proprietà `IntuneScepServiceException` contengono informazioni dettagliate sulle cause della mancata convalida della richiesta di certificato.

**Note sulla sicurezza**

  - Se questo metodo genera un'eccezione, il server SCEP **non deve** emettere un certificato per il client.
  - Gli errori di convalida della richiesta del certificato SCEP possono indicare un problema nell'infrastruttura di Intune. Oppure, indicare che un utente malintenzionato sta cercando di ottenere un certificato.

##### <a name="setsslsocketfactory-method"></a>Metodo SetSslSocketFactory

Firma:

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

Descrizione:

Usare questo metodo per indicare al client che deve usare l'istanza di SSL Socket Factory specificata (anziché il valore predefinito) quando comunica con Intune.

Parametri:

    - factory    The SSL socket factory that the client should use for HTTPS requests

Genera:

    - IllegalArgumentException    Thrown if called with a parameter that is not valid

> [!NOTE]
> L'istanza di SSL Socket Factory deve essere impostata prima di eseguire gli altri metodi di questa classe.

## <a name="integration-testing"></a>Test dell'integrazione

La convalida e la verifica che la soluzione è integrata correttamente con Intune sono indispensabili. Di seguito è riportata una panoramica dei passaggi:

1. Configurare un [account di prova di Intune](account-sign-up.md).
2. Eseguire l'onboarding del [server SCEP nel portale di Azure](#onboard-scep-server-in-azure) (in questo articolo).
3. [Configurare il server SCEP](certificates-scep-configure.md) con gli ID e la chiave creati durante l'onboarding del server SCEP.
4. [Registrare i dispositivi](device-enrollment.md) per testare gli scenari nella [matrice di test dello scenario](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
5. [Creare di un profilo certificato radice trusted](certificates-scep-configure.md) per l'autorità di certificazione.
6. Creare profili SCEP per testare gli scenari indicati nella [matrice di test dello scenario](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
7. [Assegnare i profili](device-profile-assign.md) agli utenti che hanno registrato i propri dispositivi.
8. Attendere che i dispositivi si sincronizzino con Intune. Oppure [sincronizzare manualmente i dispositivi](device-sync.md).
9. Verificare il certificato radice trusted e i [profili SCEP vengano distribuiti ai dispositivi](device-profile-monitor.md).
10. Verificare che il certificato radice trusted sia installato in tutti i dispositivi.
11. Verificare che i certificati SCEP per i profili assegnati siano installati in tutti i dispositivi.
12. Verificare che le proprietà dei certificati installati corrispondano alle proprietà impostate nel profilo SCEP.
13. Verificare che i certificati rilasciati siano indicati correttamente nella console di Intune

## <a name="see-also"></a>Vedere anche

- [Add partner certification authority in Intune using SCEP](certificate-authority-add-scep-overview.md) (Aggiungere l'autorità di autenticazione partner in Intune con SCEP)
- [Configurare Intune](setup-steps.md)
- [Registrazione dei dispositivi](device-enrollment.md)
- [Creare un profilo certificato SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) (il programma di installazione del server o connettore NDES di Microsoft non viene usato per questo scenario)
