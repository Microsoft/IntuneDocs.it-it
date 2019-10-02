---
title: Usare i profili di certificato SCEP con Microsoft Intune - Azure | Microsoft Docs
description: Creare e assegnare profili di certificato SCEP (Simple Certificate Enrollment Protocol) con Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e6b9f7d6aeda219af0f0cf3d0f5c34a3f03d258
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722891"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Creare e assegnare profili di certificato SCEP in Intune

Dopo aver [configurato l'infrastruttura](certificates-scep-configure.md) per supportare i certificati SCEP (Simple Certificate Enrollment Protocol), è possibile creare e quindi assegnare profili di certificato SCEP a utenti e dispositivi in Intune.

> [!IMPORTANT]  
> Prima di creare profili di certificato SCEP, i dispositivi che useranno un profilo di certificato SCEP devono considerare attendibile l'autorità di certificazione (CA) radice attendibile. Usare un *profilo di certificato attendibile* in Intune per eseguire il provisioning del certificato CA radice attendibile per utenti e dispositivi. Per informazioni sul profilo di certificato attendibile, vedere [Esportare il certificato CA radice attendibile](certificates-configure.md#export-the-trusted-root-ca-certificate) e [Creare profili di certificato attendibili](certificates-configure.md#create-trusted-certificate-profiles) in *Usare i certificati per l'autenticazione in Microsoft Intune*.


## <a name="create-a-scep-certificate-profile"></a>Creare un profilo certificato SCEP

1. Accedere al [portale di Intune](https://aka.ms/intuneportal).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere **Nome** e **Descrizione** per il profilo certificato SCEP.
4. Nell'elenco a discesa **Piattaforma** selezionare una [piattaforma di dispositivo supportata](certificates-configure.md#supported-platforms-and-certificate-profiles) per questo certificato SCEP. 
5. Nell'elenco a discesa **Tipo di profilo** selezionare **Certificato SCEP**.  
   
   Per la piattaforma **Android Enterprise**, *Tipo di profilo* è suddiviso in due categorie: *Solo proprietario del dispositivo* e *Solo profilo di lavoro*. Assicurarsi di selezionare il profilo di certificato SCEP corretto per i dispositivi gestiti.  

   I profili di certificato SCEP per il profilo *Solo proprietario del dispositivo* presentano le limitazioni seguenti:  

   1. Le variabili seguenti non sono supportate:  

      - CN={{OnPrem_Distinguished_Name}}  
      - CN={{onPremisesSamAccountName}}  

   2. In Monitoraggio la generazione di report per i certificati non è disponibile per i profili di certificato SCEP del proprietario del dispositivo.
   
   3. La revoca dei certificati sottoposti a provisioning dai profili di certificato SCEP per il proprietario del dispositivo non è supportata con Intune, ma può essere gestita attraverso un processo esterno o direttamente con l'autorità di certificazione.

6. Selezionare **Impostazioni** e quindi completare le configurazioni seguenti:

   - **Tipo di certificato**:   
     *(Si applica a:  Android, Android Enterprise, iOS, macOS, Windows 8.1 e versioni successive, Windows 10 e versioni successive.)*  

      Selezionare un tipo a seconda del modo in cui verrà usato il profilo di certificato:
      - **Utente**: i certificati di tipo *Utente* possono contenere attributi sia relativi agli utenti che ai dispositivi nel soggetto e nel nome alternativo del soggetto del certificato.  
      - **Dispositivo**:  I certificati di tipo *Dispositivo* possono contenere solo attributi relativi ai dispositivi nel soggetto e nel nome alternativo del soggetto del certificato.  
      
        Usare il tipo **Dispositivo** per scenari quali i dispositivi senza utente, ad esempio i chioschi multimediali, o per i dispositivi Windows. Nei dispositivi Windows il certificato viene inserito nell'archivio certificati Computer locale.  

   - **Formato nome soggetto**:  
     selezionare come Intune crea automaticamente il nome del soggetto nella richiesta di certificato. Le opzioni per il formato del nome soggetto dipendono dal tipo di certificato selezionato, ovvero **Utente** o **Dispositivo**.  

     > [!NOTE]  
     > L'uso di SCEP per ottenere certificati presenta un [problema noto](#avoid-certificate-signing-requests-with-escaped-special-characters) quando il nome del soggetto nella richiesta di firma del certificato risultante include uno dei caratteri seguenti come carattere di escape (preceduto da una barra rovesciata \\):
     > - \+
     > - ;
     > - ,
     > - =

     - **Tipo di certificato utente**  
       Le opzioni di formato per *Formato nome soggetto* includono:  
       - **Non configurato**
       - **Nome comune**
       - **Nome comune incluso l'indirizzo di posta elettronica**
       - **Nome comune come indirizzo di posta elettronica**
       - **IMEI (International Mobile Equipment Identity)**
       - **Numero di serie**
       - **Personalizzato**: quando si seleziona questa opzione, viene visualizzata anche una casella di testo **Personalizzato**. Usare questo campo per immettere un formato di nome soggetto personalizzato, incluse le variabili. Il formato personalizzato supporta due variabili: **CN (Nome comune)** ed **E (Posta elettronica)** . **CN (Nome comune)** può essere impostata su una delle variabili seguenti:

         - **CN={{UserName}}** : nome dell'entità utente (UPN) dell'utente, ad esempio janedoe@contoso.com.
         - **CN={{AAD_Device_ID}}** : ID assegnato quando si registra un dispositivo in Azure Active Directory (AD). Questo ID è in genere usato per l'autenticazione con Azure AD.
         - **CN={{SERIALNUMBER}}** : numero di serie (SN) univoco usato in genere dal produttore per identificare un dispositivo.
         - **CN={{IMEINumber}}** : numero IMEI (International Mobile Equipment Identity) univoco usato per identificare un telefono cellulare.
         - **CN={{OnPrem_Distinguished_Name}}** : sequenza di nomi distinti relativi separati da virgola, ad esempio *CN=Giorgia Fanucci,OU=UserAccounts,DC=corp,DC=contoso,DC=com*.

           Per usare la variabile *{{OnPrem_Distinguished_Name}}* , assicurarsi di sincronizzare l'attributo utente *onpremisesdistinguishedname* usando [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

         - **CN={{onPremisesSamAccountName}}** : gli amministratori possono sincronizzare l'attributo samAccountName da Active Directory ad Azure AD usando Azure AD Connect in un attributo denominato *onPremisesSamAccountName*. Intune può sostituire tale variabile come parte di una richiesta di emissione di certificati nel soggetto di un certificato. L'attributo samAccountName è il nome di accesso utente usato per supportare i client e i server da una versione precedente di Windows (precedente a Windows 2000). Il formato del nome di accesso dell'utente è: *NomeDomino\utenteTest* o solo *utenteTest*.

            Per usare la variabile *{{onPremisesSamAccountName}}* , assicurarsi di sincronizzare l'attributo utente *onPremisesSamAccountName* usando [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

         Usando una combinazione di una o più variabili e stringhe statiche, è possibile creare un formato di nome soggetto personalizzato, ad esempio:  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
            
        Questo esempio include un formato di nome soggetto che usa le variabili CN ed E, oltre a stringhe per i valori di unità organizzativa (OU), organizzazione (O), località (L), stato (S) e paese (C). L'argomento [Funzione CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) visualizza questa funzione e le relative stringhe supportate.

      - **Tipo di certificato dispositivo**  
        Le opzioni di formato per il formato del nome soggetto includono le variabili seguenti: 
        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}** *(applicabile solo per Windows e i dispositivi aggiunti a un dominio)*
        - **{{MEID}}**
        
        È possibile specificare queste variabili, seguite dal testo per la variabile, nella casella di testo. Ad esempio, il nome comune per un dispositivo denominato *Dispositivo1* può essere aggiunto come **CN={{DeviceName}}Dispositivo1**.

        > [!IMPORTANT]  
        > - Quando si specifica una variabile, racchiudere il nome della variabile tra parentesi graffe { }, come illustrato nell'esempio, per evitare un errore.  
        > - Le proprietà del dispositivo usate nel *soggetto* o nel *nome alternativo del soggetto* di un certificato del dispositivo, ad esempio **IMEI**, **SerialNumber** e **FullyQualifiedDomainName**, sono proprietà soggette a spoofing da parte di un utente con accesso al dispositivo.
        > - Un dispositivo deve supportare tutte le variabili specificate in un profilo di certificato, affinché tale profilo possa essere installato nel dispositivo.  Ad esempio, se si usa **{{IMEI}}** nel nome del soggetto di un profilo SCEP e il profilo viene assegnato a un dispositivo che non ha un numero IMEI, l'installazione del profilo avrà esito negativo.  
 


   - **Nome alternativo soggetto**:  
     specificare in che modo Intune crea automaticamente il nome alternativo del soggetto nella richiesta di certificato. Le opzioni per il nome alternativo del soggetto dipendono dal tipo di certificato selezionato, ovvero **Utente** o **Dispositivo**.  

      - **Tipo di certificato utente**  
        Selezionare uno degli attributi disponibili:  
        - **Indirizzo di posta elettronica**
        - **Nome dell'entità utente (UPN)** 

        Ad esempio, i certificati di tipo Utente possono includere il nome dell'entità utente (UPN) nel nome alternativo del soggetto. Se un certificato client viene usato per eseguire l'autenticazione in un server dei criteri di rete, impostare il nome alternativo del soggetto sul nome dell'entità utente.

      - **Tipo di certificato dispositivo**  
        Usare l'elenco a discesa **Attributo** e selezionare un attributo, assegnare un **Valore** e selezionare **Aggiungi** per aggiungerlo al profilo di certificato. È possibile aggiungere più valori selezionando attributi aggiuntivi.  

        Gli attributi disponibili includono:
        - **Indirizzo di posta elettronica**
        - **Nome dell'entità utente (UPN)**
        - **DNS**

        Con il tipo di certificato *Dispositivo*, per il valore è possibile usare le variabili del certificato del dispositivo seguenti:  

        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        Per specificare un valore per un attributo, includere il nome della variabile tra parentesi graffe, seguito dal testo per la variabile. Ad esempio, è possibile aggiungere il valore per l'attributo DNS **{{AzureADDeviceId}}.dominio.com** dove *.dominio.com* è il testo. Per un utente denominato *Utente1*, un indirizzo di posta elettronica potrebbe comparire come {{FullyQualifiedDomainName}}User1@Contoso.com.  

        > [!IMPORTANT]  
        > - Quando si usa una variabile di un certificato del dispositivo, racchiuderla tra parentesi graffe { }.  
        > - Non usare parentesi graffe **{ }** , simboli di pipe **|** e punti e virgola **;** , nel testo che segue la variabile.  
        > - Le proprietà del dispositivo usate nel *soggetto* o nel *nome alternativo del soggetto* di un certificato del dispositivo, ad esempio **IMEI**, **SerialNumber** e **FullyQualifiedDomainName**, sono proprietà soggette a spoofing da parte di un utente con accesso al dispositivo.  
        > - Un dispositivo deve supportare tutte le variabili specificate in un profilo di certificato, affinché tale profilo possa essere installato nel dispositivo.  Ad esempio, se si usa **{{IMEI}}** nel nome alternativo del soggetto di un profilo SCEP e il profilo viene assegnato a un dispositivo che non ha un numero IMEI, l'installazione del profilo avrà esito negativo.

   - **Periodo di validità del certificato**:  
     È possibile immettere un valore inferiore, ma non superiore, al periodo di validità presente nel modello di certificato. Se il modello di certificato è stato configurato per [supportare un valore personalizzato che è possibile impostare dalla console di Intune](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template), usare questa impostazione per specificare la quantità di tempo rimanente prima della scadenza del certificato.  

     Se ad esempio il periodo di validità del certificato nel modello di certificato è di due anni, è possibile immettere un valore di un anno ma non un valore di cinque anni. Inoltre, il valore deve essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente.

   - **Provider di archiviazione chiavi (KSP)** :  
     *(Si applica a:  Windows 8.1 e versioni successive e Windows 10 e versioni successive)*  
     
     Specificare dove viene archiviata la chiave per il certificato. Scegliere uno dei valori seguenti:  
     - **Registra nel provider di archiviazione chiavi Trusted Platform Module (TPM) se presente, altrimenti nel provider di archiviazione chiavi software**
     - **Registra nel provider di archiviazione chiavi Trusted Platform Module (TPM) oppure genera errore**
     - **Registra in Passport oppure genera errore (Windows 10 e versioni successive)**
     - **Registra nel provider di archiviazione chiavi software**

   - **Utilizzo chiavi**:  
     selezionare le opzioni di utilizzo delle chiavi per il certificato:

     - **Firma digitale**: consentire lo scambio di chiavi solo se viene usata una firma digitale per proteggere la chiave.
     - **Crittografia chiave**: consentire lo scambio di chiavi solo quando la chiave è crittografata.  

   - **Dimensioni chiave (bit)** :  
     selezionare il numero di bit contenuti nella chiave.  

   - **Algoritmo hash**:  
     *(Si applica ad Android, Android Enterprise, Windows Phone 8.1, Windows 8.1 e versioni successive e Windows 10 e versioni successive)*  

     selezionare uno dei tipi di algoritmo hash disponibili da usare con questo certificato. Selezionare il livello di sicurezza più avanzato supportato dai dispositivi che verranno connessi.

   - **Certificato radice**:  
     Selezionare il *profilo certificato attendibile* configurato in precedenza e assegnato a utenti e dispositivi applicabili per questo profilo di certificato SCEP. Il profilo di certificato attendibile viene usato per eseguire il provisioning di utenti e dispositivi con il certificato CA radice attendibile. Per informazioni sul profilo di certificato attendibile, vedere [Esportare il certificato CA radice attendibile](certificates-configure.md#export-the-trusted-root-ca-certificate) e [Creare profili di certificato attendibili](certificates-configure.md#create-trusted-certificate-profiles) in *Usare i certificati per l'autenticazione in Intune*. Se sono disponibili un'autorità di certificazione radice e un'autorità di certificazione emittente, selezionare il profilo del certificato radice attendibile associato all'autorità di certificazione emittente.

   - **Utilizzo chiavi avanzato**:  
     aggiungere valori per lo scopo designato del certificato. Nella maggior parte dei casi il certificato richiede l'*autenticazione client* in modo che l'utente o il dispositivo possa eseguire l'autenticazione in un server. È possibile aggiungere altri utilizzi di chiavi in base alle esigenze.

   - **Soglia di rinnovo (%)** :  
     immettere la percentuale di durata residua del certificato prima che il dispositivo richieda il rinnovo del certificato. Se si immette 20, ad esempio, il rinnovo del certificato verrà tentato quando il certificato risulta scaduto all'80% e verranno eseguiti ulteriori tentativi fino al completamento del rinnovo. Il rinnovo genera un nuovo certificato, che comporta una nuova coppia di chiavi pubblica/privata.

   - **URL server SCEP**:  
     specificare uno o più URL per i server del servizio Registrazione dispositivi di rete che emettono certificati tramite SCEP. Ad esempio, immettere *https://ndes.contoso.com/certsrv/mscep/mscep.dll* . È possibile aggiungere altri URL di SCEP per il bilanciamento del carico, se necessario, perché viene eseguito il push degli URL in modo casuale nel dispositivo con il profilo. Se uno dei server SCEP non è disponibile, la richiesta SCEP avrà esito negativo ed è possibile che nelle successive archiviazioni del dispositivo la richiesta del certificato venga effettuata sullo stesso server non attivo.

7. Selezionare **OK** e quindi **Crea**. Il profilo viene creato e visualizzato nell'elenco *Configurazione del dispositivo - Profili*.

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>Evitare le richieste di firma del certificato con caratteri speciali di escape
Esiste un problema noto per le richieste di certificati SCEP che includono un nome soggetto con uno o più dei caratteri speciali seguenti come carattere di escape. I nomi di soggetto che includono uno dei caratteri speciali come carattere di escape generano una richiesta di firma del certificato con un nome soggetto errato che a sua volta determina l'esito negativo della convalida della richiesta di verifica SCEP di Intune e la mancata emissione del certificato.  

I caratteri speciali sono:
- \+
- ,
- ;
- =

Quando il nome del soggetto include uno dei caratteri speciali, usare una delle opzioni seguenti per ovviare a questa limitazione:  
- Racchiudere tra virgolette il valore CN contenente il carattere speciale.  
- Rimuovere il carattere speciale dal valore CN.  

**Ad esempio**, si supponga di avere un nome soggetto visualizzato come *Test user (TestCompany, LLC)* .  Una richiesta di firma del certificato che includa un CN con la virgola tra *TestCompany* e *LLC* presenta un problema.  È possibile evitare il problema racchiudendo l'intero CN tra virgolette oppure rimuovendo la virgola tra *TestCompany* e *LLC*:
- **Aggiungere le virgolette**: *CN=* "Test User (TestCompany, LLC)",OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **Rimuovere la virgola**: *CN=Test User (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 I tentativi di escape della virgola tramite l'uso di una barra rovesciata, tuttavia, non riusciranno con un errore nei log CRP:  
- **Escape della virgola**: *CN=Test User (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

L'errore è simile al seguente: 

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>Assegnare il profilo certificato
La procedura per assegnare i profili di certificato SCEP è uguale a quella per la [distribuzione dei profili di dispositivo](../configuration/device-profile-assign.md) per altri scopi. Tuttavia, tenere presente quanto segue prima di continuare:

- Quando si assegnano profili di certificato SCEP a gruppi, il file del certificato CA radice attendibile (specificato nel *profilo di certificato attendibile*) viene installato nel dispositivo. Il dispositivo usa il profilo di certificato SCEP per creare una richiesta di certificato per tale certificato CA radice attendibile.  

- Il profilo di certificato SCEP viene installato solo nei dispositivi che eseguono la piattaforma specificata al momento della creazione del profilo di certificato.

- È possibile assegnare profili certificato alle raccolte di utenti o di dispositivi.

- Per pubblicare rapidamente un certificato in un dispositivo dopo la registrazione del dispositivo, assegnare il profilo certificato a un gruppo di utenti invece che a un gruppo di dispositivi. Se si assegna il profilo certificato a un gruppo di dispositivi, è necessario eseguire una registrazione completa dei dispositivi prima che questi ricevano i criteri.  

- Se si usa la co-gestione per Intune e Configuration Manager, in Configuration Manager [impostare il dispositivo di scorrimento del carico di lavoro](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads) per Criteri di accesso alle risorse su **Intune** o **Intune pilota**. Questa impostazione consente ai client Windows 10 di avviare il processo di richiesta del certificato.

- Anche se si creano e si assegnano separatamente il profilo di certificato attendibile e il profilo di certificato SCEP, è necessario assegnare entrambi. Se non sono entrambi installati in un dispositivo, i criteri per i certificati SCEP hanno esito negativo. Assicurarsi che tutti i profili di certificati radice attendibili vengano anche distribuiti negli stessi gruppi del profilo SCEP.


> [!NOTE]
> Nei dispositivi iOS, quando un profilo certificato SCEP viene associato a un profilo aggiuntivo, ad esempio un profilo Wi-Fi o VPN, il dispositivo riceve un certificato per ognuno di questi profili aggiuntivi. Ne risulta che il dispositivo iOS riceve più certificati dalla richiesta di certificato SCEP.  Se si desidera un solo certificato, è necessario usare i certificati PKCS invece dei certificati SCEP.  Ciò è dovuto a differenze nella modalità di recapito dei certificati SCEP e PKCS ai dispositivi.


## <a name="next-steps"></a>Passaggi successivi  

[Assegnare profili](../configuration/device-profile-assign.md)  
