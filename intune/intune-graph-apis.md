---
title: Come usare Azure AD per accedere alle API di Intune in Microsoft Graph
titlesuffix: Microsoft Intune
description: Descrive i passaggi necessari per consentire alle app di usare Azure AD per accedere alle API di Intune in Microsoft Graph.
keywords: intune graphapi c# powershell ruoli di autorizzazione
author: dougeby
manager: dougeby
ms.author: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5129484a3cfea873be4009849b5989f9c2acd888
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187448"
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>Come usare Azure AD per accedere alle API di Intune in Microsoft Graph

L'[API Microsoft Graph](https://developer.microsoft.com/graph/) ora supporta Microsoft Intune con API e ruoli di autorizzazione specifici.  L'API Microsoft Graph usa Azure Active Directory (Azure AD) per l'autenticazione e il controllo di accesso.  
L'accesso alle API di Intune in Microsoft Graph richiede:

- Un ID applicazione con:

    - Autorizzazione per chiamare Azure AD e le API Microsoft Graph.
    - Ambiti di autorizzazione appropriati per le specifiche attività dell'applicazione.

- Credenziali utente con:

    - Autorizzazione per l'accesso al tenant di Azure AD associato all'applicazione.
    - Autorizzazioni di ruolo necessarie per supportare gli ambiti di autorizzazione dell'applicazione.

- L'utente finale deve concedere all'app l'autorizzazione per l'esecuzione delle attività dell'applicazione per il tenant di Azure.

Questo articolo:

- Illustra come registrare un'applicazione con l'accesso all'API Microsoft Graph e i ruoli di autorizzazione appropriati.

- Descrive i ruoli di autorizzazione dell'API di Intune.

- Include esempi di autenticazione dell'API di Intune per C# e PowerShell.

- Descrive come supportare più tenant.

Per altre informazioni, vedere:

- [Autorizzare l'accesso alle applicazioni Web tramite OAuth 2.0 e Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Introduzione all'autenticazione di Azure AD](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth)
- [Integrazione di applicazioni con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [Informazioni su OAuth 2.0](https://oauth.net/2/)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>Registrare le app per l'uso dell'API Microsoft Graph

Per registrare un'app per l'uso dell'API Microsoft Graph:

1.  Accedere al [portale di Azure](https://portal.azure.com) con credenziali amministrative.

    A seconda delle esigenze, è possibile usare:
    - L'account amministratore del tenant.
    - Un account utente del tenant con l'impostazione **Gli utenti possono registrare applicazioni** abilitata.

2.  Dal menu scegliere **Azure Active Directory** &gt; **Registrazioni per l'app**.

    <img src="./media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3.  Scegliere **Registrazione nuova applicazione** per creare una nuova applicazione oppure scegliere un'applicazione esistente.  Se si sceglie un'applicazione esistente, ignorare il passaggio successivo.

4.  Nel pannello **Crea** specificare quanto segue:

    1.  Il **nome** per l'applicazione (visualizzato quando gli utenti eseguono l'accesso).

    2.  I valori **Tipo di applicazione** e **URI di reindirizzamento**.

        Questi elementi variano in base ai requisiti. Se ad esempio si usa Azure AD [Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL), impostare **Tipo di applicazione** su `Native` e **URI di reindirizzamento** su `urn:ietf:wg:oauth:2.0:oob`.

        <img src="media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        Per altre informazioni, vedere [Scenari di autenticazione per Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

5.  Nel pannello dell'applicazione:

    1.  Prendere nota del valore **ID applicazione**.

    2.  Scegliere **Impostazioni** &gt; **Accesso all'API** &gt; **Autorizzazioni necessarie**.

    <img src="media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6.  Dal pannello **Autorizzazioni necessarie** scegliere **Aggiungi** &gt; **Aggiungi accesso all'API** &gt; **Selezionare un'API**.

    <img src="media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7.  Dal pannello **Selezionare un'API** scegliere **Microsoft Graph** &gt; **Seleziona**.  Verrà aperto il pannello **Abilita accesso**, in cui sono elencati gli ambiti di autorizzazione disponibili per l'applicazione.

    <img src="media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    Scegliere i ruoli necessari per l'app inserendo un segno di spunta a sinistra dei nomi corrispondenti.  Per informazioni sugli specifici ambiti di autorizzazione di Intune, vedere [Ambiti di autorizzazione di Intune](#intune-permission-scopes).  Per informazioni sugli altri ambiti di autorizzazione dell'API Graph, vedere [Informazioni di riferimento sulle autorizzazioni di Microsoft Graph](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).

    Per ottenere risultati ottimali, scegliere il minor numero di ruoli necessario per implementare l'applicazione.

    Al termine, scegliere **Seleziona** e **Fine** per salvare le modifiche.

A questo punto, è inoltre possibile:

- Scegliere di concedere a tutti gli account del tenant l'autorizzazione per usare l'app senza specificare credenziali.  

    A tale scopo, scegliere **Concedi autorizzazioni** e accettare la richiesta di conferma.

    Quando si esegue l'applicazione per la prima volta, viene richiesto di concedere all'app l'autorizzazione per l'esecuzione dei ruoli selezionati.

    <img src="media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- Rendere disponibile l'app agli utenti all'esterno del tenant.  In genere, questa operazione è necessaria solo per i partner che supportano più tenant o organizzazioni.  

    A tale scopo, procedere nel seguente modo:

  1. Scegliere **Manifesto** nel pannello dell'applicazione, in modo da aprire il pannello **Modifica manifesto**.

     <img src="media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. Modificare il valore dell'impostazione `availableToOtherTenants` in `true`.

  3. Salvare le modifiche.

## <a name="intune-permission-scopes"></a>Ambiti di autorizzazione di Intune

Azure AD e Microsoft Graph usano ambiti di autorizzazione per controllare l'accesso alle risorse aziendali.  

Gli ambiti di autorizzazione (anche denominati _ambiti OAuth_) controllano l'accesso alle specifiche entità di Intune e alle relative proprietà. In questa sezione sono riepilogati gli ambiti di autorizzazione per le funzionalità dell'API di Intune.

Per altre informazioni, vedere:
- [Autenticazione di Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [Ambiti di autorizzazione dell'applicazione](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

Quando si concede l'autorizzazione a Microsoft Graph, è possibile specificare i seguenti ambiti per controllare l'accesso alle funzionalità di Intune. Nella tabella seguente sono riepilogati gli ambiti di autorizzazione dell'API di Intune.  La prima colonna indica il nome della funzionalità, così com'è visualizzato nel portale di Azure, e la seconda colonna specifica il nome dell'ambito di autorizzazione.

Impostazione _Abilita accesso_ | Nome ambito
:--|:--
__Perform user-impacting remote actions on Microsoft Intune devices__ (Eseguire azioni remote che influiscono sull'utente nei dispositivi di Microsoft Intune) | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__Read and write Microsoft Intune devices__ (Leggere e scrivere i dispositivi di Microsoft Intune) | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Read Microsoft Intune devices__ (Leggere i dispositivi di Microsoft Intune) | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Read and write Microsoft Intune RBAC settings__ (Leggere e scrivere le impostazioni di controllo degli accessi in base al ruolo di Microsoft Intune) | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Read Microsoft Intune RBAC settings__ (Leggere le impostazioni di controllo degli accessi in base al ruolo di Microsoft Intune) | [DeviceManagementRBAC.Read.All](#rac=ro)
__Read and write Microsoft Intune apps__ (Leggere e scrivere le app di Microsoft Intune) | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Read Microsoft Intune apps__ (Leggere le app di Microsoft Intune) | [DeviceManagementApps.Read.All](#app-ro)
__Read and write Microsoft Intune Device Configuration and Policies__ (Leggere e scrivere la configurazione e i criteri dei dispositivi di Microsoft Intune) | [DeviceManagementConfiguration.ReadWrite.All](#cfg-rw)
__Read Microsoft Intune Device Configuration and Policies__ (Leggere la configurazione e i criteri dei dispositivi di Microsoft Intune) | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Read and write Microsoft Intune configuration__ (Leggere e scrivere la configurazione di Microsoft Intune) | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Read Microsoft Intune configuration__ (Leggere la configurazione di Microsoft Intune) | [DeviceManagementServiceConfig.Read.All](#svc-ra)

La tabella elenca le impostazioni nell'ordine in cui sono visualizzate nel portale di Azure. Nelle sezioni seguenti vengono descritti gli ambiti in ordine alfabetico.

Attualmente, tutti gli ambiti di autorizzazione di Intune richiedono l'accesso con privilegi di amministratore.  Ciò significa che sono necessarie credenziali corrispondenti per l'esecuzione di app o script che accedono alle risorse dell'API di Intune.

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- Impostazione **Abilita accesso**: __Leggere le app di Microsoft Intune__

- Consente l'accesso in lettura alle proprietà e allo stato delle entità seguenti:
    - App client
    - Categorie di app per dispositivi mobili
    - Criteri di protezione delle app
    - Configurazioni delle app

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- Impostazione **Abilita accesso**: __Leggere e scrivere le app di Microsoft Intune__

- Consente le stesse operazioni di __DeviceManagementApps.Read.All__

- Consente inoltre modifiche alle entità seguenti:

    - App client
    - Categorie di app per dispositivi mobili
    - Criteri di protezione delle app
    - Configurazioni delle app

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- Impostazione **Abilita accesso**: __Leggere la configurazione e i criteri dei dispositivi di Microsoft Intune__

- Consente l'accesso in lettura alle proprietà e allo stato delle entità seguenti:
    - Configurazione dei dispositivi
    - Criteri di conformità dei dispositivi
    - Messaggi di notifica

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- Impostazione **Abilita accesso**: __Leggere e scrivere la configurazione e i criteri dei dispositivi di Microsoft Intune__

- Consente le stesse operazioni di __DeviceManagementConfiguration.Read.All__

- Le app possono inoltre creare, assegnare, eliminare e modificare le entità seguenti:
    - Configurazione dei dispositivi
    - Criteri di conformità dei dispositivi
    - Messaggi di notifica

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- Impostazione **Abilita accesso**: __Eseguire azioni remote che influiscono sull'utente nei dispositivi di Microsoft Intune__

- Consente le seguenti azioni remote in un dispositivo gestito:
    - Ritiro
    - Cancellazione
    - Reimpostazione/recupero del passcode
    - Blocco remoto
    - Abilitazione o disabilitazione della modalità di dispositivo perso
    - Pulizia del PC
    - Riavviare
    - Eliminazione di un utente da un dispositivo condiviso

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- Impostazione **Abilita accesso**: __Leggere i dispositivi di Microsoft Intune__

- Consente l'accesso in lettura alle proprietà e allo stato delle entità seguenti:
    - Dispositivo gestito
    - Categoria di dispositivi
    - App rilevata
    - Azioni remote
    - Informazioni sul malware

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- Impostazione **Abilita accesso**: __Leggere e scrivere i dispositivi di Microsoft Intune__

- Consente le stesse operazioni di __DeviceManagementManagedDevices.Read.All__

- Le app possono inoltre creare, eliminare e modificare le entità seguenti:
    - Dispositivo gestito
    - Categoria di dispositivi

- Sono inoltre consentite le azioni remote seguenti:
    - Individuazione dei dispositivi
    - Bypass del blocco attivazione
    - Richiesta di assistenza remota

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- Impostazione **Abilita accesso**: __Leggere le impostazioni di controllo degli accessi in base al ruolo di Microsoft Intune__

- Consente l'accesso in lettura alle proprietà e allo stato delle entità seguenti:
    - Assegnazioni di ruolo
    - Definizioni di ruolo
    - Operazioni su risorse

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- Impostazione **Abilita accesso**: __Leggere e scrivere le impostazioni di controllo degli accessi in base al ruolo di Microsoft Intune__

- Consente le stesse operazioni di __DeviceManagementRBAC.Read.All__

- Le app possono inoltre creare, assegnare, eliminare e modificare le entità seguenti:
    - Assegnazioni di ruolo
    - Definizioni di ruolo

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- Impostazione **Abilita accesso**: __Leggere la configurazione di Microsoft Intune__

- Consente l'accesso in lettura alle proprietà e allo stato delle entità seguenti:
    - Registrazione del dispositivo
    - Certificato Apple Push Notification Service
    - Programma di registrazione del dispositivo mobile di Apple:
    - Volume Purchase Program di Apple
    - Exchange Connector
    - Termini e condizioni
    - Gestione delle spese per telecomunicazioni
    - Infrastruttura a chiave pubblica (PKI) cloud
    - Personalizzazione
    - Mobile Threat Defense

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- Impostazione **Abilita accesso**: __Leggere e scrivere la configurazione di Microsoft Intune__

- Consente le stesse operazioni di DeviceManagementServiceConfig.Read.All_

- Le app possono inoltre configurare le funzionalità di Intune seguenti:
    - Registrazione del dispositivo
    - Certificato Apple Push Notification Service
    - Programma di registrazione del dispositivo mobile di Apple:
    - Volume Purchase Program di Apple
    - Exchange Connector
    - Termini e condizioni
    - Gestione delle spese per telecomunicazioni
    - Infrastruttura a chiave pubblica (PKI) cloud
    - Personalizzazione
    - Mobile Threat Defense

## <a name="azure-ad-authentication-examples"></a>Esempi di autenticazione di AD Azure

In questa sezione viene illustrato come incorporare Azure AD nei progetti C# e PowerShell.

In ogni esempio sarà necessario specificare un ID applicazione che disponga almeno dell'ambito di autorizzazione `DeviceManagementManagedDevices.Read.All` (descritto in precedenza).

Quando si testa un esempio, potrebbero essere visualizzati errori di stato HTTP 403 (Accesso negato) simili al seguente:

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

In questo caso, verificare quanto segue:

- L'ID applicazione è stato aggiornato a un ID autorizzato a usare l'API Microsoft Graph e l'ambito di autorizzazione `DeviceManagementManagedDevices.Read.All`.

- Le credenziali del tenant supportano le funzioni amministrative.

- Il codice è simile agli esempi visualizzati.


### <a name="authenticate-azure-ad-in-c"></a>Autenticare Azure AD in C\#

In questo esempio viene illustrato come usare C# per recuperare un elenco di dispositivi associati all'account di Intune.

1.  Avviare Visual Studio e quindi creare un nuovo progetto App console (.NET Framework) di Visual C#.

2.  Immettere un nome per il progetto e specificare gli altri dettagli in base alle esigenze.

    <img src="media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3.  Usare Esplora soluzioni per aggiungere il pacchetto NuGet Microsoft ADAL al progetto.

    1.  Fare clic con il pulsante destro del mouse in Esplora soluzioni.
    2.  Scegliere **Gestisci pacchetti NuGet...** &gt; **Sfoglia**.
    3.  Selezionare `Microsoft.IdentityModel.Clients.ActiveDirectory` e quindi scegliere **Installa**.

    <img src="media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4.  Aggiungere le istruzioni seguenti all'inizio di **Program.cs**:

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5.  Aggiungere un metodo per creare l'intestazione dell'autorizzazione:

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    Ricordare di modificare il valore di `application_ID` in modo che corrisponda a un ID che disponga almeno dell'ambito di autorizzazione `DeviceManagementManagedDevices.Read.All`, come descritto in precedenza.

6. Aggiungere un metodo per recuperare l'elenco dei dispositivi:

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7.  Aggiornare **Main** in modo da eseguire la chiamata di **GetMyManagedDevices**:

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8.  Compilare ed eseguire il programma.  

Quando si esegue il programma per la prima volta, verranno visualizzate due richieste.  La prima richiede le credenziali e la seconda concede le autorizzazioni per la richiesta `managedDevices`.  

Per riferimento, ecco il programma completato:

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Autenticare Azure AD (PowerShell)

Il seguente script di PowerShell usa il modulo Azure AD PowerShell per l'autenticazione.  Per altre informazioni, vedere [Azure Active Directory PowerShell versione 2](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) e gli [esempi di Intune PowerShell](https://github.com/microsoftgraph/powershell-intune-samples).

In questo esempio, aggiornare il valore di `$clientID` in modo che corrisponda un ID applicazione valido.

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>Supportare più tenant e partner

Se l'organizzazione supporta altre organizzazioni con specifici tenant di Azure Active Directory, è possibile consentire ai clienti di usare l'applicazione con i rispettivi tenant.

A tale scopo, procedere nel seguente modo:

1.  Verificare che l'account del cliente esista nel tenant di Azure AD di destinazione.

2.  Verificare che l'account del tenant consenta agli utenti di registrare applicazioni (vedere **Impostazioni utente**).

3.  Stabilire una relazione tra ogni tenant.  

    A tale scopo:

    a. Usare il [Centro per i partner Microsoft](https://partnercenter.microsoft.com/) per definire una relazione con il cliente e il relativo indirizzo di posta elettronica.

    b. Invitare l'utente come guest nel tenant.

Per invitare l'utente come guest nel tenant:

1.  Scegliere **Aggiungi un utente guest** dal pannello **Attività rapide**.

    <img src="media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2.  Immettere l'indirizzo di posta elettronica del cliente e, facoltativamente, aggiungere un messaggio personalizzato per l'invito.

    <img src="media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3.  Scegliere **Invita**.

Verrà inviato un invito all'utente.

   <img src="media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   L'utente dovrà scegliere il collegamento **Guida introduttiva** per accettare l'invito.

Quando è stata stabilita la relazione (o è stato accettato l'invito), aggiungere l'account utente a **Ruolo della directory**.

Ricordare di aggiungere l'utente ad altri ruoli in base alle esigenze. Ad esempio, per consentire all'utente di gestire le impostazioni di Intune, l'utente deve essere un **amministratore globale** o un **amministratore del servizio Intune**.

Inoltre:

- Usare https://portal.office.com per assegnare una licenza di Intune all'account utente.

- Aggiornare il codice dell'applicazione per eseguire l'autenticazione nel dominio del tenant di Azure AD del cliente, anziché nel proprio.

    Se ad esempio il dominio del proprio tenant è `contosopartner.onmicrosoft.com` e il dominio del tenant del cliente è `northwind.onmicrosoft.com`, sarà necessario aggiornare il codice per l'autenticazione nel tenant del cliente.

    A tale scopo, in un'applicazione C# basata sull'esempio precedente, sarà necessario modificare il valore della variabile `authority`:

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    su

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
