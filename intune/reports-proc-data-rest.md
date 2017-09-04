---
title: Recuperare dati dall'API data warehouse con un client REST
description: Recuperare i dati dal data warehouse di Intune tramite un'API RESTful.
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1bbb0e8ba84e221df3a434da79c513939267648b
ms.sourcegitcommit: b8ef9d8387b4d9b2ea4e6ce937635304771e6532
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/11/2017
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>Recuperare dati dall'API data warehouse di Intune con un client REST

È possibile accedere al modello di dati data warehouse di Intune tramite endpoint RESTful. Per ottenere l'accesso ai dati, è necessario autorizzare il client con Microsoft Azure Active Directory (Azure AD) tramite OAuth 2.0. Per abilitare l'accesso, configurare prima di tutto un'app nativa in Azure e concedere le autorizzazioni all'API Microsoft Intune. Il client locale ottiene l'autorizzazione e può quindi comunicare con gli endpoint del data warehouse tramite l'app nativa.

I passaggi per configurare un client per recuperare i dati dall'API data warehouse richiedono le operazioni seguenti:

1. Creare un'app client come app nativa in Azure
3. Concedere all'app client l'accesso all'API Microsoft Intune
3. Creare un client REST locale per ottenere i dati

Usare la procedura seguente per informazioni su come autorizzare e usare Postman come client. Postman è uno strumento di uso comune per risoluzione dei problemi e lo sviluppo di client REST da usare con le API. Per altre informazioni su Postman, vedere il sito di [Postman](https://www.getpostman.com). Questo argomento include anche un esempio di codice C#. Nell'esempio viene illustrato come autorizzare un client e ottenere dati dall'API.

## <a name="create-a-native-app-in-azure"></a>Creare un'app nativa in Azure

Creare un'app nativa in Azure. Questa app nativa è l'app client. Il client in esecuzione nel computer locale fa riferimento all'API data warehouse di Intune quando il client locale richiede le credenziali. 

1. Accedere al portale di Azure per il tenant. Scegliere **Azure Active Directory** > **Registrazioni per l'app** per aprire il pannello **Registrazioni per l'app**.
2. Fare clic su **Registrazione nuova app**.
3. Digitare i dettagli dell'app.
    1.  Digitare un nome descrittivo, ad esempio Client data warehouse Intune, per il **Nome**.
    2.  Selezionare **Nativo** per il **Tipo di applicazione**.
    3.  Digitare l'URL per l'**URL di accesso**. L'URL di accesso dipenderà dallo scenario specifico, tuttavia se si intende usare Postman, digitare `https://www.getpostman.com/oauth2/callback`. Usare il callback per il passaggio di autenticazione client per eseguire l'autenticazione ad Azure AD.
4.  Scegliere **Crea**.

     ![API data warehouse di Intune](media\reports-get_rest_data_client_overview.png)

5. Prendere nota dell'**ID applicazione** di questa app in quanto verrà usato nella sezione successiva.
6. Se si intende usare Postman, aggiungere una chiave. La chiave viene usata come segreto client con l'autenticazione ad Azure AD. Per aggiungere una chiave:
    1.  Fare clic su **Chiavi** in **Accesso all'API** nel pannello Impostazioni per l'app.
    2.  Digitare un nome della chiave, ad esempio Segreto client, per la **Descrizione**.
    3.  Selezionare **1 anno** per la Durata.
    4.  Fare clic su **Save**. 
    5.  Copiare il valore della chiave. Non sarà possibile recuperare la chiave dopo aver chiuso il pannello **Impostazioni** per le chiavi.

## <a name="grant-the-native-app-access-to-the-microsoft-intune-api"></a>Concedere all'app nativa l'accesso all'API Microsoft Intune

È ora disponibile un'app definita in Azure. Concedere all'app nativa l'accesso all'API Microsoft Intune.

1.  Fare clic sull'app nativa. Il nome assegnato all'app è simile a Client data warehouse Intune.
2.  Nel pannello **Impostazioni** fare clic su **Autorizzazioni necessarie**.
3.  Fare clic su **Aggiungi** nel pannello **Autorizzazioni necessarie**.
4.  Fare clic su **Selezionare un'API**.
5.  Cercare il nome dell'app Web. È denominata **API Microsoft Intune**.
6.  Fare clic su app nell'elenco.
7.  Fare clic su **Seleziona**.
8.  Selezionare la casella **Autorizzazioni delegate** per aggiungere **Ottenere informazioni sul data warehouse da Microsoft Intune**.

    ![Abilitazione dell'accesso](media\reports-get_rest_data_client_access.png)

9.  Fare clic su **Seleziona**.
10.  Fare clic su **Fine**.
11.  Facoltativamente, fare clic su **Concedi autorizzazioni** nel pannello Autorizzazioni necessarie. In questo modo si concederà l'accesso a tutti gli account nella directory corrente evitando la visualizzazione della finestra di dialogo di consenso per ogni utente nel tenant. Per altre informazioni, vedere [Integrazione di applicazioni con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).
12.  Fare clic su **Sì**.

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>Recuperare dati dall'API Microsoft Intune con Postman

È possibile usare l'API data warehouse di Intune con un client REST generico come ad esempio Postman. Postman può fornire informazioni dettagliate sulle funzionalità dell'API, sul modello di dati OData sottostante e risolvere i problemi di connessione alle risorse dell'API. In questa sezione è possibile trovare informazioni sulla generazione di un token Auth2.0 per il client locale. Il token servirà al client per eseguire l'autenticazione con Azure AD e accedere alle risorse dell'API.

### <a name="information-you-will-need-to-make-the-call"></a>Informazioni necessarie per effettuare la chiamata

Per effettuare una chiamata REST con Postman sono necessarie le informazioni seguenti:

| Attributo        | Descrizione                                                                                                                                                                          | Esempio                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| URL callback     | Impostare questo URL come URL callback nella pagina delle impostazioni dell'app.                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| Nome token       | Stringa usata per passare le credenziali all'app Azure. Il processo genera il token in modo da poter effettuare una chiamata all'API data warehouse.                          | Bearer                                                                                        |
| URL autenticazione         | È l'URL usato per l'autenticazione. | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com |
| URL token di accesso | È l'URL usato per concedere il token.                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| ID client        | Viene creato e annotato quando si crea l'app nativa in Azure.                                                                                               | 4184c61a-e324-4f51-83d7-022b6a81b991                                                          |
| Chiave privata client    | Viene creato e annotato quando si aggiunge una chiave all'app client in Azure.                                                                                              | JZoRZGPmN9xwsUnfX9UW877dkV5Fn/qQClhr7SuyMUQ=                                                  |
| Ambito (facoltativo) | Vuoto                                                                                                                                                                               | È possibile lasciare vuoto il campo.                                                                     |
| Tipo di concessione       | Il token è un codice di autorizzazione.                                                                                                                                                  | Codice di autorizzazione                                                                            |

È necessario l'endpoint. In questo esempio verranno recuperati dati dall'entità **dates**. Il formato dell'entità **dates** è il seguente: `https://fef.{aus}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`. Verrà usato l'URL di gestione del tenant. L'URL di gestione del tenant viene usato durante la creazione dell'app Web.

### <a name="make-the-rest-call"></a>Effettuare la chiamata REST

Per ottenere un nuovo token di accesso per Postman, è necessario aggiungere l'URL di autorizzazione di Azure AD, l'ID client e il segreto client. Postman caricherà la pagina di autorizzazione in cui verranno specificate le credenziali.

#### <a name="add-the-information-used-to-request-the-token"></a>Aggiungere le informazioni usate per richiedere il token

1.  Scaricare Postman se non è stato già installato. Per scaricare Postman, vedere [www.getpostman](https://www.getpostman.com).
2.  Aprire Postman. Scegliere l'operazione HTTP **GET**.
3.  Incollare l'URL dell'endpoint nell'indirizzo. Sarà simile al seguente:  

    `https://fef.msua06.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4.  Scegliere la scheda **Autorizzazione** e selezionare **OAuth 2.0** dall'elenco **Tipo**.
5.  Fare clic su **Ottieni nuovo token di accesso**.
6.  Verificare di avere già aggiunto l'URL callback all'app in Azure. L'URL callback è `https://www.getpostman.com/oauth2/callback`.
7.  Immettere Bearer per il **Nome token**.
8.  Aggiungere l'**URL autenticazione**. Sarà simile al seguente:  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com`
9.  Aggiungere l'**URL token di accesso**. Sarà simile al seguente:  

     `https://login.microsoftonline.com/common/oauth2/token`

10. Aggiungere l'**ID client** dell'app nativa creata in Azure e denominata `Intune Data Warehouse Client`. Sarà simile al seguente:  

     `4184c61a-e324-4f51-83d7-022b6a81b991`

11. Aggiungere il **Segreto client** definito come chiave durante la creazione dell'app nativa in Azure. Sarà simile al seguente: 

     `F360R69M0MS72OB6YAqTyXO9MsXZx/OJTgAE2HB4k2k=`

12. Selezionare **Codice di autorizzazione** e Richiedi token di accesso in locale.

13. Fare clic su **Richiedi token**.

    ![Informazioni per il token](media\reports-postman_getnewtoken.png)

14. Digitare le credenziali nella pagina di autorizzazione di Azure AD. L'elenco di token esistenti in Postman contiene ora il token denominato `Bearer`.
16. Scegliere il token. Selezionare **Intestazione** per aggiungere il token.
17. Fare clic su **Usa token**. L'elenco di intestazioni contiene il nuovo valore della chiave di autorizzazione e il valore `Bearer <your-authorization-token>`.

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>Inviare la chiamata all'endpoint con Postman

1.  Fare clic su **Invia**.
2.  I dati restituiti vengono visualizzati nel corpo della risposta di Postman.

    ![Postman 200OK](media\reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>Creare un client REST (C#) per recuperare dati dal data warehouse di Intune

L'esempio seguente contiene un semplice client REST. Il codice usa la classe **httpClient** della libreria .Net. Quando il client ottiene le credenziali per Azure AD, il client crea una chiamata GET REST per recuperare l'entità dates dall'API data warehouse.

> [!Note]  
> È possibile accedere all'[esempio di codice seguente su GitHub](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs). Fare riferimento al repository GitHub per le modifiche e gli aggiornamenti più recenti per l'esempio.

1.  Aprire **Microsoft Visual Studio**.
2.  Scegliere **File** > **Nuovo progetto**. Espandere **Visual C#** e scegliere **App console (.NET Framework)**. 
3.  Assegnare al progetto il nome ` IntuneDataWarehouseSamples`, scegliere il percorso in cui si vuole salvare il progetto e quindi fare clic su **OK**.
3.  Fare clic con il pulsante destro del mouse sul nome della soluzione in Esplora soluzioni e quindi scegliere **Gestisci pacchetti NuGet per la soluzione**. Fare clic su **Sfoglia** e quindi digitare 'Microsoft.IdentityModel.Clients.ActiveDirectory' nella casella di ricerca.
4. Scegliere il pacchetto, selezionare il progetto **IntuneDataWarehouseSamples** in Gestisci pacchetti per la soluzione e quindi fare clic su **Installa**. 
5. Fare clic su **Accetto** per accettare la licenza del pacchetto NuGet.
6. Aprire `Program.cs` da Esplora soluzioni.

    ![Progetto in Visual Studio](media\reports-get_rest_data_in.png)

7.  Sostituire il codice in Program.cs con il codice seguente:  
    ```csharp
namespace IntuneDataWarehouseSamples
{
    using System;
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;

    class Program
    {
     static void Main(string[] args)
  {
   /**
    * TODO: Replace the below values with your own.
    * emailAddress - The email address of the user that you will authenticate as.
    *
    * password  - The password for the above email address.
    *    This is inline only for simplicity in this sample. We do not 
    *    recommend storing passwords in plaintext.
    *
    * applicationId - The application ID of the native app that was created in AAD.
    *
    * warehouseUrl   - The data warehouse URL for your tenant. This can be found in 
    *      the Azure portal.
    * 
    * collectionName - The name of the warehouse entity collection you would like to 
    *      access.
    */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
    resource: "https://api.manage.microsoft.com/",
    clientId: applicationId,
    userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
  }
    }
    ```

8.  Aggiornare gli elementi `TODO` nell'esempio di codice.
9.  Premere **CTRL+F5** per compilare ed eseguire il client Intune.DataWarehouseAPIClient in modalità Debug.

    ![Entità Date recuperata in formato JSON.](media\reports-get_rest_data_output.png)

10.  Rivedere l'output della console. L'output contiene i dati in formato JSON estratti dall'entità **dates** nel tenant Intune.

## <a name="next-steps"></a>Passaggi successivi

È possibile trovare informazioni dettagliate sull'autorizzazione, la struttura URL dell'API e gli endpoint OData in [Usare l'API data warehouse di Intune](reports-api-url.md). 

È anche possibile fare riferimento al modello di dati del data warehouse di Intune per trovare le entità di dati contenute nell'API. Per altre informazioni, vedere [Usare il modello di dati dell'API data warehouse di Intune](reports-ref-data-model.md).