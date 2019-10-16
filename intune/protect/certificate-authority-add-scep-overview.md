---
title: Usare autorità di certificazione di terze parti con SCEP in Microsoft Intune - Azure | Microsoft Docs
description: In Microsoft Intune è possibile aggiungere un fornitore o un'autorità di certificazione (CA, Certificate Authority) di terze parti per rilasciare certificati ai dispositivi mobili tramite il protocollo SCEP. In questa panoramica, un'applicazione Azure Active Directory (Azure AD) concede a Microsoft Intune le autorizzazioni necessarie per convalidare certificati. Per rilasciare certificati, usare quindi l'ID applicazione, la chiave di autenticazione e l'ID tenant dell'applicazione AAD nella configurazione del server SCEP.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b82124fe8f6da7116c8333e293f219d7c667f9c
ms.sourcegitcommit: a2654f3642b43b29ab0e1cbb2dfa2b56aae18d0e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72310907"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Aggiungere un'autorità di certificazione partner in Intune tramite SCEP

Usare autorità di certificazione (CA) di terze parti con Intune. Le autorità di certificazione di terze parti possono effettuare il provisioning di dispositivi mobili con certificati nuovi o rinnovati usando il protocollo SCEP (Simple Certificate Enrollment Protocol) e possono supportare i dispositivi Windows, iOS, Android e macOS.

Questa funzionalità è costituita da due parti: uso di un'API open source e attività dell'amministratore di Intune.

**Parte 1: usare un'API open source**  
Microsoft ha creato un'API per l'integrazione con Intune. L'API consente di convalidare i certificati, inviare notifiche di esito positivo o negativo e usare SSL, in particolare SSL Socket Factory, per comunicare con Intune.

L'API è disponibile nel [repository GitHub pubblico dell'API SCEP di Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) per il download e l'uso all'interno di soluzioni. Usare questa API con server SCEP di terze parti per eseguire la convalida della richiesta di verifica personalizzata con Intune prima che SCEP esegua il provisioning di un certificato in un dispositivo.

In [Integrate with Intune SCEP management solution](scep-libraries-apis.md) (Integrazione con la soluzione di gestione SCEP di Intune) sono disponibili informazioni dettagliate sull'uso dell'API e sui metodi di questa, nonché sul test della soluzione compilata.

**Parte 2: creare l'applicazione e il profilo**  
Tramite un'applicazione Azure Active Directory (Azure AD) è possibile delegare a Intune i diritti necessari per la gestione delle richieste SCEP provenienti dai dispositivi. L'applicazione Azure AD include valori relativi a ID applicazione e chiave di autenticazione usati all'interno della soluzione creata con l'API dallo sviluppatore. Gli amministratori creano e distribuiscono quindi i profili dei certificati SCEP tramite Intune e possono visualizzare i report sullo stato di distribuzione nei dispositivi.

Questo articolo offre una panoramica di questa funzionalità, compresa la creazione dell'applicazione Azure AD, dal punto di vista di un amministratore.

## <a name="overview"></a>Panoramica

La procedura seguente offre una panoramica dell'uso di SCEP per i certificati in Intune:

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

![In che modo un'autorità di certificazione di terze parti SCEP si integra con Microsoft Intune](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurare l'integrazione di un'autorità di certificazione di terze parti

### <a name="validate-third-party-certification-authority"></a>Convalidare l'autorità di certificazione di terze parti

Prima di integrare le autorità di certificazione di terze parti con Intune, verificare che l'autorità di certificazione in uso supporti Intune. In [Partner autorità di certificazione di terze parti](#third-party-certification-authority-partners) (in questo articolo) è disponibile un elenco. Per altre informazioni, è anche possibile vedere il materiale sussidiario dell'autorità di certificazione in uso. L'autorità di certificazione può includere istruzioni di configurazione specifiche per l'implementazione.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorizzare la comunicazione tra l'autorità di certificazione e Intune

Per consentire a un server SCEP di terze parti di eseguire la convalida della richiesta di verifica personalizzata con Intune, creare un'app in Azure AD. Questa app delega a Intune i diritti necessari per convalidare le richieste SCEP.

Assicurarsi di avere le autorizzazioni necessarie per registrare un'app di Azure AD. Vedere [Autorizzazioni necessarie](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) nella documentazione di Azure AD.

#### <a name="create-an-application-in-azure-active-directory"></a>Creare un’applicazione in Azure Active Directory  

1. Nel [portale di Azure](https://portal.azure.com) passare ad **Azure Active Directory** > **Registrazioni app** e quindi selezionare **Nuova registrazione**.  

2. Nella pagina **Registra un'applicazione** specificare i dettagli seguenti:  
   - Nella sezione **Nome** immettere un nome significativo per l'applicazione.  
   - Per la sezione **Tipi di account supportati** selezionare **Account in qualsiasi directory organizzativa**.  
   - Per **URI di reindirizzamento** lasciare l'impostazione predefinita Web e quindi specificare l'URL di accesso per il server SCEP di terze parti.  

3. Selezionare **Registra** per creare l'applicazione e per aprire la pagina Panoramica per la nuova app.  

4. Nella pagina **Panoramica** dell'app copiare il valore **ID client applicazione** e annotarlo per usarlo in seguito. Questo valore sarà necessario in seguito.  

5. Nel riquadro di spostamento per l'app passare a **Certificates & secrets** (Certificati e segreti) in **Gestione**. Selezionare il pulsante **New client secret** (Nuovo segreto client). Immettere un valore in Descrizione, selezionare un'opzione per **Scadenza** e quindi scegliere **Aggiungi** per generare un *valore* per il segreto client. 
   > [!IMPORTANT]  
   > Prima di uscire da questa pagina, copiare il valore del segreto client e annotarlo per usarlo in seguito durante l'implementazione dell'autorità di certificazione di terze parti. Questo valore non viene più visualizzato. Assicurarsi di rivedere il materiale sussidiario per l'autorità di certificazione di terze parti per informazioni sulla configurazione dell'ID applicazione, della chiave di autenticazione e dell'ID tenant.  

6. Prendere nota dell'**ID tenant**. L'ID tenant è il testo del dominio che segue il simbolo @ nell'account. Se ad esempio l'account è *admin@name.onmicrosoft.com* , l'ID tenant è **name.onmicrosoft.com**.  

7. Nel riquadro di spostamento per l'app passare ad **Autorizzazioni API** in **Gestione** e quindi selezionare **Aggiungi un'autorizzazione**.  

8. Nella pagina **Richiedi le autorizzazioni dell'API** selezionare **Intune** e quindi selezionare **Autorizzazioni applicazione**. Selezionare la casella di controllo per **scep_challenge_provider** (convalida challenge SCEP).  

   Selezionare **Aggiungi autorizzazioni** per salvare questa configurazione.  

9. Rimanere nella pagina **Autorizzazioni API**, selezionare **Concedi consenso amministratore per Microsoft** e quindi selezionare **Sì**.  
   
   Il processo di registrazione dell'app in Azure AD è stato completato.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurare e distribuire un profilo certificato SCEP
L'amministratore deve creare un profilo certificato SCEP da destinare a utenti o a dispositivi e quindi deve assegnare il profilo.

- [Creare un profilo certificato SCEP](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [Assegnare il profilo certificato](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Rimozione di certificati

Quando si cancella un dispositivo o se ne annulla la registrazione, i certificati vengono rimossi, ma non vengono revocati.

## <a name="third-party-certification-authority-partners"></a>Partner autorità di certificazione di terze parti
Intune è supportato dalle autorità di certificazione di terze parti seguenti:

- [Entrust Datacard](https://info.entrustdatacard.com/pki-eval-tool)
- [Versione open source GitHub EJBCA](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Le autorità di certificazione di terze parti interessate a integrare il proprio prodotto con Intune possono vedere il materiale sussidiario sull'API:

- [Repository GitHub dell'API SCEP di Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Materiale sussidiario dell'API SCEP di Intune per le autorità di certificazione di terze parti](scep-libraries-apis.md)

## <a name="see-also"></a>Vedere anche

- [Configurare i profili certificato](certificates-scep-configure.md)
- [Repository GitHub dell'API SCEP di Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Materiale sussidiario dell'API SCEP di Intune per le autorità di certificazione di terze parti](scep-libraries-apis.md)
