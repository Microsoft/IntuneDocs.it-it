---
title: Autenticazione OAuth del data warehouse di Intune
titleSuffix: Microsoft Intune
description: Questo argomento descrive l'autenticazione OAuth del data warehouse per Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/31/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9d3cd7dfb28d26451da95861fe9a3011c2556b1
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454044"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Autenticazione OAuth del data warehouse di Intune

È possibile configurare un'applicazione con Azure Active Directory (Azure AD) ed eseguirne l'autenticazione nel data warehouse di Intune. Questo processo è utile per i siti Web, le app e i processi in background in cui l'applicazione non deve avere accesso alle credenziali utente. Usando la procedura seguente, si autorizza l'applicazione con Azure AD mediante OAuth 2.0.

## <a name="authorization"></a>Authorization

In Azure Active Directory (Azure AD) si utilizza OAuth 2.0 per consentire all'utente di autorizzare l'accesso ad applicazioni Web e API Web nel proprio tenant di Azure AD. Questa guida illustra come eseguire l'autenticazione dell'applicazione tramite C#. Il flusso del codice di autorizzazione OAuth 2.0 è descritto nella sezione 4.1 della specifica OAuth 2.0. Per altre informazioni, vedere [Autorizzare l'accesso alle applicazioni Web tramite OAuth 2.0 e Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).


## <a name="azure-keyvault"></a>Azure Key Vault

Il processo seguente usa un metodo privato per elaborare e convertire una chiave dell'app. Questo metodo privato è denominato SecureString. In alternativa, è possibile usare Azure Key Vault per archiviare la chiave dell'app. Per altre informazioni, vedere [Key Vault](https://azure.microsoft.com/services/key-vault/).

## <a name="create-a-web-app"></a>Creare un'app Web

In questa sezione vengono forniti i dettagli sull'app Web che si vuole punti a Intune. Un'app Web è un'applicazione client-server. Il server fornisce l'app Web che include interfaccia utente, contenuto e funzionalità. Questo tipo di app viene gestito separatamente sul Web. Usare Intune per concedere a un'app Web di accedere a Intune. Il flusso di dati viene avviato dall'app Web. 

1.  Accedere al [portale di Azure](https://portal.azure.com).
2.  Usare il campo **Cerca risorse, servizi e documentazione** nella parte superiore del portale di Azure per cercare **Azure Active Directory**.
3.  Nel menu a discesa selezionare **Azure Active Directory** in **Servizi**.
4.  Selezionare **Registrazioni per l'app**.
5.  Fare clic su **Registrazione nuova applicazione** per visualizzare il pannello **Crea**.
6.  Nel pannello **Crea** aggiungere i dettagli dell'app:

    - Un nome per l'app, ad esempio *Aut solo app Intune*.
    - Il **tipo di applicazione**. Scegliere **App/API Web** per aggiungere un'app che rappresenti un'applicazione Web, un'API Web o entrambe.
    - **URL di accesso** dell'applicazione. Questo è il percorso a cui accedono automaticamente gli utenti durante il processo di autenticazione. Viene loro richiesto di dimostrare la loro identità. Per altre informazioni, vedere [Informazioni sull'accesso alle applicazioni e Single Sign-On con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

7.  Nella parte inferiore del pannello **Crea** fare clic su **Crea**.

    >[!NOTE] 
    > Copiare l'**ID applicazione** dal pannello **App registrata** per usarlo in seguito.

## <a name="create-a-key"></a>Creare una chiave

In questa sezione Azure AD genera un valore di chiave per l'app.

1.  Nel pannello **Registrazioni per l'app** selezionare l'app appena creata per visualizzare il pannello dell'app.
2.  Selezionare **Impostazioni** nella parte superiore del pannello per visualizzare il pannello **Impostazioni**.
3.  Selezionare **Chiavi** nel pannello **Impostazioni**.
4.  Aggiungere la **descrizione** della chiave, una durata in **Scadenza** e un **valore** per la chiave.
5.  Fare clic su **Salva** per salvare e aggiornare le chiavi dell'applicazione.
6.  È necessario copiare il valore di chiave generato (con codifica base64).

    >[!NOTE] 
    > Il valore della chiave scompare dopo la chiusura del pannello **Chiavi**. Non è possibile recuperare la chiave da questo pannello in un secondo momento. Copiarla per poterla usare in seguito.

## <a name="grant-application-permissions"></a>Concedere le autorizzazioni per le applicazioni

In questa sezione vengono concesse le autorizzazioni per le applicazioni.

1.  Selezionare **Autorizzazioni necessarie** nel pannello **Impostazioni**.
2.  Fare clic su **Aggiungi**.
3.  Selezionare **Aggiungi API** per visualizzare il pannello **Selezionare un'API**.
4.  Selezionare **API di Microsoft Intune (MicrosoftIntuneAPI)** e quindi fare clic su **Seleziona** nel pannello **Selezionare un'API**. Viene selezionato il passaggio **Selezionare le autorizzazioni** e viene visualizzato il pannello **Abilita accesso**.
5.  Scegliere l'opzione **Get data warehouse information from Microsoft Intune** (Ottieni informazioni sul data warehouse da Microsoft Intune) nella sezione **Autorizzazioni applicazione**.
6.  Fare clic su **Seleziona** nel pannello **Abilita accesso**.
7.  Fare clic su **Fine** nel pannello **Aggiungi accesso all'API**.
8.  Fare clic su **Concedi autorizzazioni** nel pannello **Autorizzazioni necessarie** e fare clic su **Sì** quando richiesto per aggiornare le eventuali autorizzazioni esistenti già concesse all'applicazione.

## <a name="generate-token"></a>Genera token

Usare Visual Studio per creare un progetto di app console (.NET Framework) che supporta .NET Framework e usa C# come linguaggio di programmazione.

1.  Selezionare **File** > **Nuovo** > **Progetto** per visualizzare la finestra di dialogo **Nuovo progetto**.
2.  A sinistra, selezionare **Visual C#** per visualizzare tutti i progetti .NET Framework.
3.  Selezionare **App console (.NET Framework)** , aggiungere un nome di app e quindi fare clic su **OK** per creare l'app.
4.  In **Esplora soluzioni** selezionare **Program.cs** per visualizzare il codice.
5.  In Esplora soluzioni aggiungere un riferimento all'assembly `System.Configuration`.
6.  Nel menu a comparsa selezionare **Aggiungi** > **Nuovo elemento**. Viene visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.
7.  A sinistra, in **Visual C#** selezionare **Codice**.
8.  Selezionare **Classe**, modificare il nome della classe in *IntuneDataWarehouseClass.cs* e fare clic su **Aggiungi**.
9.  Aggiungere il codice seguente all'interno del metodo <code>Main</code>:

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

10. Aggiungere ulteriori spazi dei nomi aggiungendo il codice seguente nella parte superiore del file di codice:

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

11. Dopo il metodo <code>Main</code> aggiungere il metodo privato seguente per elaborare e convertire la chiave dell'app:

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

12. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Riferimenti** e quindi scegliere **Gestisci pacchetti NuGet**.
13. Cercare *Microsoft.IdentityModel.Clients.ActiveDirectory* e installare il pacchetto Microsoft NuGet correlato.
14. In **Esplora soluzioni** selezionare e aprire il file *App.config*.
15. Aggiungere la sezione <code>appSettings</code> in modo da ottenere il codice XML seguente:

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

16. Aggiornare i valori <code>appId</code>, <code>appKey</code> e <code>tenantDomain</code> in modo che corrispondano ai valori specifici correlati all'app.
17. Compilare l'app.

    >[!NOTE] 
    > Per visualizzare codice di implementazione aggiuntivo, vedere l'[esempio di codice Intune-Data-Warehouse](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp ).

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su Azure Key Vault, vedere [Cos'è Azure Key Vault?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis).

