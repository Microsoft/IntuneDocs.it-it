---
title: Usare un'autorità di certificazione di terze parti con SCEP in Microsoft Intune - Azure | Microsoft Docs
description: In Microsoft Intune è possibile aggiungere un fornitore o un'autorità di certificazione (CA, Certificate Authority) di terze parti per rilasciare certificati ai dispositivi mobili tramite il protocollo SCEP. In questa panoramica, un'applicazione Azure Active Directory (Azure AD) concede a Microsoft Intune le autorizzazioni necessarie per convalidare certificati. Per rilasciare certificati, usare quindi l'ID applicazione, la chiave di autenticazione e l'ID tenant dell'applicazione AAD nella configurazione del server SCEP.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 772c800e75f52d9826992bf0adfbfdcf3faba107
ms.sourcegitcommit: a13d1eafc979a9cfeb4adbdea861e2784c2b1068
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2018
ms.locfileid: "46329981"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Aggiungere un'autorità di certificazione partner in Intune tramite SCEP

In Microsoft Intune è possibile aggiungere autorità di certificazione (CA) di terze parti. Tali CA possono distribuire certificati ai dispositivi mobili tramite il protocollo SCEP (Simple Certificate Enrollment Protocol). Questa funzionalità consente di rilasciare nuovi certificati e di rinnovare certificati esistenti nei dispositivi Windows, iOS, Android e macOS.

Questa funzionalità è costituita da due parti: uso di un'API open source e attività dell'amministratore di Intune.

**Parte 1: usare un'API open source**  
Microsoft ha creato un'API che si integra con Intune per la convalida dei certificati, l'invio di notifiche di esito positivo o negativo e l'uso di SSL, in particolare di SSL Socket Factory, per comunicare con Intune.

L'API è disponibile nel [repository GitHub pubblico dell'API SCEP di Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) per il download e l'uso all'interno di soluzioni. Usare questa API con server SCEP di terze parti per eseguire la convalida della richiesta di verifica personalizzata con Intune prima di recapitare un certificato a un dispositivo.

In [Integrate with Intune SCEP management solution](scep-libraries-apis.md) (Integrazione con la soluzione di gestione SCEP di Intune) sono disponibili informazioni dettagliate sull'uso dell'API e sui metodi di questa, nonché sul test della soluzione compilata.

**Parte 2: creare l'applicazione e il profilo**  
Tramite un'applicazione Azure Active Directory (Azure AD) è possibile delegare a Intune i diritti necessari per la gestione delle richieste SCEP provenienti dai dispositivi. L'applicazione Azure AD include valori relativi a ID applicazione e chiave di autenticazione usati all'interno della soluzione creata con l'API dallo sviluppatore. Gli amministratori possono quindi usare Intune per creare e distribuire i profili certificato SCEP. È anche possibile visualizzare report sullo stato della distribuzione per i dispositivi.

Questo articolo offre una panoramica di questa funzionalità, compresa la creazione dell'applicazione Azure AD, dal punto di vista di un amministratore.

## <a name="overview"></a>Panoramica

La procedura seguente offre una panoramica del rilascio di certificati SCEP in Intune:

1. In Intune, un amministratore crea un profilo certificato SCEP e quindi destina il profilo a utenti o dispositivi.
2. Il dispositivo accede a Intune.
3. Intune crea una richiesta di verifica SCEP univoca, aggiungendo anche informazioni per il controllo dell'integrità, ad esempio il soggetto e il nome alternativo del soggetto previsti.
4. Intune crittografa e firma sia le informazioni relative alla richiesta di verifica che quelle relative al controllo di integrità e quindi le invia al dispositivo con la richiesta SCEP.
5. Il dispositivo genera una richiesta di firma del certificato e una coppia di chiavi pubblica/privata nel dispositivo in base al profilo certificato SCEP di cui viene eseguito il push da Intune.
6. La richiesta di firma del certificato e la richiesta di verifica crittografata/firmata vengono inviate all'endpoint server SCEP di terze parti.
7. Il server SCEP invia la richiesta di firma del certificato e la richiesta di verifica a Intune. Intune quindi convalida la firma, decrittografa il payload e confronta la richiesta di firma del certificato con le informazioni del controllo di integrità.
8. Intune invia una risposta al server SCEP, indicando se la convalida della richiesta di verifica è riuscita o meno.  
9. Se tale convalida ha esito positivo, il server SCEP rilascia il certificato al dispositivo.

Il diagramma seguente illustra il flusso dettagliato dell'integrazione SCEP di terze parti in Intune:

![In che modo un'autorità di certificazione di terze parti SCEP si integra con Microsoft Intune](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurare l'integrazione di un'autorità di certificazione di terze parti

### <a name="validate-third-party-certification-authority"></a>Convalidare l'autorità di certificazione di terze parti

Prima di integrare le autorità di certificazione di terze parti con Intune, verificare che l'autorità di certificazione in uso supporti Intune. In [Partner autorità di certificazione di terze parti](#third-party-certification-authority-partners) (in questo articolo) è disponibile un elenco. Per altre informazioni, è anche possibile vedere il materiale sussidiario dell'autorità di certificazione in uso. L'autorità di certificazione può includere istruzioni di configurazione specifiche per l'implementazione.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorizzare la comunicazione tra l'autorità di certificazione e Intune

Per consentire a un server SCEP di terze parti di eseguire la convalida della richiesta di verifica personalizzata con Intune, creare un'app in Azure AD. Questa app delega a Intune i diritti necessari per convalidare le richieste SCEP.

Assicurarsi di avere le autorizzazioni necessarie per registrare un'app di Azure AD. In [Autorizzazioni necessarie](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) sono elencati i passaggi.

**Passaggio 1: Creare un'applicazione Azure AD** 

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Azure Active Directory** > **Registrazioni per l'app** > **Registrazione nuova applicazione**.
3. Immettere un nome e un URL di accesso. Come tipo di applicazione selezionare **App Web/API**.
4. Selezionare **Crea**.

[Integrate applications with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) (Integrare applicazioni con Azure Active Directory) include materiale sussidiario sulla creazione di un'app,con suggerimenti per l'URL e il nome.

**Passaggio 2: Concedere autorizzazioni**

Dopo aver creato l'applicazione, concedere all'API Microsoft Intune le autorizzazioni necessarie:

1. Nell'app di Azure AD aprire **Impostazioni** > **Autorizzazioni necessarie**.  
2. Selezionare **Aggiungi** > **Selezionare un'API** > selezionare **Microsoft Intune API**  (API Microsoft Intune)  > **Seleziona**.
3. In **Selezionare le autorizzazioni** scegliere **SCEP challenge validation** (Convalida richiesta di verifica SCEP)  > **Seleziona**.
4. Selezionare **Fatto** per salvare le modifiche.

**Passaggio 3: Ottenere l'ID applicazione e la chiave di autenticazione**

Ottenere quindi i valori relativi all'ID e alla chiave dell'applicazione Azure AD. Sono necessari i valori seguenti:

- ID applicazione
- Chiave di autenticazione
- ID tenant

**Per ottenere l'ID applicazione e la chiave di autenticazione**:

1. In Azure AD, selezionare la nuova applicazione (**Registrazioni per l'app**).
2. Copiare l'**ID applicazione** e archiviarlo nel codice dell'applicazione.
3. Generare quindi una chiave di autenticazione. Nell'app di Azure AD, aprire **Impostazioni** > **Chiavi**.
4. In **Password** immettere una descrizione e scegliere la durata della chiave. **Salvare** le modifiche. Copiare e salvare il valore visualizzato.

    > [!IMPORTANT]
    > Copiare e salvare la chiave immediatamente, perché non verrà più visualizzata. Il valore di questa chiave è necessario per l'implementazione dell'autorità di certificazione di terze parti. Assicurarsi di rivedere il materiale sussidiario per informazioni sulla configurazione dell'ID applicazione, della chiave di autenticazione e dell'ID tenant.

L'**ID tenant** è il testo del dominio che segue il simbolo @ nell'account. Se ad esempio l'account è `admin@name.onmicrosoft.com`, l'ID tenant è **name.onmicrosoft.com**.

In [Ottenere l'ID applicazione e la chiave di autenticazione](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key) sono elencati i passaggi necessari per ottenere questi valori e sono disponibili altri dettagli sulle app di Azure AD.

### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurare e distribuire un profilo certificato SCEP
L'amministratore deve creare un profilo certificato SCEP da destinare a utenti o a dispositivi e quindi deve assegnare il profilo.

- [Creare un profilo certificato SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [Assegnare il profilo certificato](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Rimozione di certificati

Quando si cancella un dispositivo o se ne annulla la registrazione, i certificati vengono rimossi, ma non vengono revocati.

## <a name="third-party-certification-authority-partners"></a>Partner autorità di certificazione di terze parti
Intune è supportato dalle autorità di certificazione di terze parti seguenti:

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)
- [Versione open source GitHub EJBCA](https://github.com/agerbergt/intune-ejbca-connector)

Le autorità di certificazione di terze parti interessate a integrare il proprio prodotto con Intune possono vedere il materiale sussidiario sull'API:

- [Repository GitHub dell'API SCEP di Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Materiale sussidiario dell'API SCEP di Intune per le autorità di certificazione di terze parti](scep-libraries-apis.md)

## <a name="see-also"></a>Vedere anche

- [Configurare i profili certificato](certificates-scep-configure.md)
- [Repository GitHub dell'API SCEP di Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Materiale sussidiario dell'API SCEP di Intune per le autorità di certificazione di terze parti](scep-libraries-apis.md)
