---
title: Come configurare i certificati con Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come usare Intune per creare e assegnare certificati che consentono di proteggere Wi-Fi, VPN e altre connessioni.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 364534ad788466f8b268b4091decee5326b94163
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-configure-certificates-in-microsoft-intune"></a>Come configurare i certificati in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Quando si concede agli utenti l'accesso alle risorse aziendali tramite profili VPN, Wi-Fi o di posta elettronica, è possibile proteggere tale accesso con un certificato installato in ogni dispositivo utente. Di seguito è indicato il flusso di lavoro generale:

1. Assicurarsi di disporre dell'infrastruttura di certificazione corretta. È possibile usare [certificati SCEP](configure-certificate-infrastructure-for-scep.md) e [certificati PKCS](configure-certificate-infrastructure-for-pfx.md).
2. Installare un certificato radice o un certificato dell'autorità di certificazione (CA) intermedio in ogni dispositivo, in modo che il dispositivo riconosca la legittimità dell'autorità di certificazione. A tale scopo, creare e assegnare un **profilo certificato attendibile**. Quando si assegna questo profilo, i dispositivi da gestire con Intune richiederanno e riceveranno il certificato radice. È necessario creare un profilo separato per ogni piattaforma. I profili certificato attendibile sono disponibili per le piattaforme seguenti:
    - iOS 8.0 e versioni successive
    - macOS 10.9 e versioni successive
    - Android 4.0 e versioni successive <!--Android for Work --->
    - Windows 8.1 e versioni successive
    - Windows Phone 8.1 e versioni successive
    - Windows 10 e versioni successive
3. Creare i profili certificato in modo che i dispositivi richiedano un certificato da usare per l'autenticazione dell'accesso a VPN, Wi-Fi e posta elettronica. È possibile creare e distribuire un profilo certificato **PKCS** o **SCEP** per i dispositivi che eseguono queste piattaforme:
    - iOS 8.0 e versioni successive
    - Android 4.0 e versioni successive
    - Android for Work
    - Windows 10 (per dispositivi desktop e mobili) e versioni successive

    È possibile usare solo un profilo certificato SCEP su queste piattaforme:

-     macOS 10.9 e versioni successive
-     Windows Phone 8.1 e versioni successive

È necessario creare un profilo separato per ogni piattaforma dei dispositivi. Quando si crea il profilo, questo viene associato al profilo del certificato radice attendibile già creato.

### <a name="further-considerations"></a>Altre considerazioni

- Se non è presente un'autorità di certificazione globale (enterprise), è necessario crearla.
- Se, in base alle piattaforme dei dispositivi, si decide di usare il profilo Simplified Certificate Enrollment Protocol (SCEP), è necessario anche configurare un server del servizio Registrazione dispositivi di rete (NDES).
- Se si prevede di usare i profili SCEP o PKCS, è necessario scaricare e configurare Connettore di certificati di Microsoft Intune.

## <a name="before-you-start"></a>Prima di iniziare


### <a name="if-you-want-to-use-scep-certificates"></a>Se si sceglie di usare i certificati SCEP

Completare i prerequisiti necessari in [Infrastruttura di certificazione per SCEP](/intune-azure/configure-devices/configure-certificate-infrastructure-for-scep).

### <a name="if-you-want-to-use-pkcs-certificates"></a>Se si sceglie di usare i certificati PKCS

Completare i prerequisiti necessari in [Certificate infrastructure for PKCS](/intune-azure/configure-devices/configure-certificate-infrastructure-for-pfx) (Infrastruttura di certificazione per PKCS).

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>Attività 1: esportare il certificato CA radice attendibile
Esportare il certificato dell'Autorità di certificazione radice disponibile nell'elenco locale come file con estensione **cer** dalla CA emittente o da qualsiasi dispositivo che consideri attendibile la CA emittente. Non esportare la chiave privata.

Il certificato viene importato quando si configura un profilo certificato attendibile.

## <a name="task-2-create-trusted-certificate-profiles"></a>Attività 2: creare profili certificato attendibile
È necessario creare un profilo certificato attendibile prima di creare un profilo certificato SCEP o PKCS. Sono necessari un profilo certificato attendibile e un profilo SCEP o PKCS per ogni piattaforma del dispositivo.

### <a name="to-create-a-trusted-certificate-profile"></a>Per creare un profilo certificato attendibile

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo certificato attendibile.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo per questo certificato attendibile. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Certificato attendibile**.
7. Passare al certificato salvato nell'attività 1, quindi fare clic su **OK**.
8. Solo per i dispositivi Windows 8.1 e Windows 10, selezionare l'**Archivio di destinazione** per il certificato attendibile da:
    - **Archivio certificati computer - Radice**
    - **Archivio certificati computer - Intermedio**
    - **Archivio certificati utente - Intermedio**
8. Al termine, scegliere **OK**, tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md).


> [!Note]
> I dispositivi Android visualizzano un avviso che indica che altri produttori hanno installato un certificato attendibile.

## <a name="task-3-create-scep-or-pkcs-certificate-profiles"></a>Attività 3: creare profili certificato SCEP o PKCS
Dopo aver creato un profilo certificato attendibile, creare i profili certificato SCEP o PKCS per ogni piattaforma che si vuole usare. Quando si crea un profilo certificato SCEP, è necessario specificarne uno attendibile per la stessa piattaforma. In questo modo i due profili certificato risultano collegati, anche se è ancora necessario assegnarli separatamente.

### <a name="to-create-an-scep-certificate-profile"></a>Per creare un profilo certificato SCEP

1. Nel portale di Azure selezionare il carico di lavoro **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo certificato SCEP.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo per questo certificato SCEP. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Certificato SCEP**.
7. Nel pannello **Certificato SCEP** è possibile configurare le impostazioni seguenti:
    - **Periodo di validità del certificato**: se il comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** è stato eseguito nella CA emittente, che consente un periodo di validità personalizzato, è possibile specificare la quantità di tempo rimanente prima della scadenza del certificato.<br>È possibile specificare un valore inferiore, ma non superiore rispetto al periodo di validità nel modello di certificato indicato. Ad esempio, se il periodo di validità del certificato nel modello di certificato è di due anni, è possibile specificare un valore di un anno ma non un valore di cinque anni. Inoltre, il valore deve essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente. 
    - **Provider di archiviazione chiavi (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): specificare dove verrà archiviata la chiave per il certificato. Scegliere tra uno dei seguenti valori:
        - **Registra nel provider di archiviazione chiavi Trusted Platform Module (TPM) se presente, altrimenti nel provider di archiviazione chiavi software**
        - **Registra nel provider di archiviazione chiavi Trusted Platform Module (TPM) oppure genera errore**
        - **Registra in Passport oppure genera errore (Windows 10 e versioni successive)**
        - **Registra nel provider di archiviazione chiavi software**
    - **Formato nome soggetto**: dall'elenco, selezionare in che modo Intune crea automaticamente il nome soggetto nella richiesta certificato. Se il certificato è per un utente, è anche possibile includere l'indirizzo di posta elettronica dell'utente nel nome del soggetto. È possibile scegliere tra:
        - **Non configurato**
        - **Nome comune**
        - **Nome comune incluso l'indirizzo di posta elettronica**
        - **Nome comune come indirizzo di posta elettronica**
    - **Nome alternativo soggetto**: specificare in che modo Intune crea automaticamente i valori per il nome alternativo soggetto (SAN) nella richiesta certificato. Ad esempio, se si seleziona un tipo di certificato utente, è possibile includere il nome dell'entità utente (UPN) nel nome alternativo oggetto. Se il certificato client verrà usato per eseguire l'autenticazione in un server dei criteri di rete, è necessario impostare il nome alternativo oggetto sul nome dell'entità utente. 
    - **Utilizzo chiave**: specificare le opzioni d'uso della chiave per il certificato. È possibile scegliere una delle opzioni seguenti: 
        - **Crittografia chiave:** consentire lo scambio di chiavi solo quando la chiave viene crittografata. 
        - **Firma digitale:** consentire lo scambio di chiavi soltanto se una firma digitale consente di proteggere la chiave. 
    - **Dimensioni chiave (bit)**: selezionare il numero di bit che saranno contenuti nella chiave. 
    - **Algoritmo hash** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): selezionare uno dei tipi di algoritmo hash disponibili da usare con il certificato. Selezionare il livello di sicurezza più avanzato supportato dai dispositivi che verranno connessi. 
    - **Certificato radice**: scegliere un profilo del certificato radice della CA già configurato e assegnato all'utente o al dispositivo. Questo certificato CA deve essere il certificato radice per l'autorità di certificazione che rilascerà il certificato che si sta configurando in questo profilo certificato. 
    - **Utilizzo chiave esteso**: scegliere **Aggiungi** per aggiungere valori per lo scopo designato del certificato. Nella maggior parte dei casi il certificato richiederà l' **Autenticazione Client** in modo che l'utente o il dispositivo possa eseguire l'autenticazione a un server. È comunque possibile aggiungere altri utilizzi di chiavi secondo necessità. 
    - **Impostazioni di registrazione**
        - **Soglia di rinnovo (%)**: specificare la percentuale di durata residua del certificato prima che il dispositivo ne richieda il rinnovo.
        - **URL server SCEP**: specificare uno o più URL per i server NDES che emetteranno certificati tramite SCEP. 
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.

Seguire le istruzioni nella pagina di configurazione del profilo per configurare le impostazioni del profilo di certificato SCEP.
>[!Note]
> Solo per dispositivi iOS: in Formato nome soggetto selezionare Personalizzato per immettere un formato personalizzato del nome soggetto.
> Le due variabili attualmente supportate per il nome personalizzato sono **CN (Nome comune)** ed **E (Posta elettronica)**. Usando una combinazione di queste stringhe statiche e variabili, è possibile creare un formato del nome soggetto personalizzato, come il seguente: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US** In questo esempio è stato creato un formato del nome soggetto che, oltre alle variabili CN ed E, usa stringhe per i valori Organizational Unit, Organization, Location, State e Country. [Questo argomento](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) mostra la funzione **CertStrToName** e le relative stringhe supportate.


### <a name="to-create-a-pkcs-certificate-profile"></a>Per creare un profilo certificato PKCS

Nel portale di Azure selezionare il carico di lavoro **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili fare clic su **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo certificato PKCS.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo per questo certificato PKCS:
    - **Android**
    - **iOS**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Certificato PKCS**.
7. Nel pannello **Certificato PKCS** è possibile configurare le impostazioni seguenti:
    - **Soglia di rinnovo (%)**: specificare la percentuale di durata residua del certificato prima che il dispositivo ne richieda il rinnovo.
    - **Periodo di validità del certificato**: se il comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** è stato eseguito nella CA emittente, che consente un periodo di validità personalizzato, è possibile specificare la quantità di tempo rimanente prima della scadenza del certificato.<br>È possibile specificare un valore inferiore, ma non superiore rispetto al periodo di validità nel modello di certificato indicato. Ad esempio, se il periodo di validità del certificato nel modello di certificato è di due anni, è possibile specificare un valore di un anno ma non un valore di cinque anni. Inoltre, il valore deve essere inferiore rispetto al periodo di validità rimanente del certificato della CA emittente.
    - **Provider di archiviazione chiavi (KSP)** (Windows 10) -
    - **Autorità di certificazione** -
    - **Nome dell'autorità di certificazione** -
    - **Nome modello di certificato**: immettere il nome di un modello di certificato configurato per essere usato dal servizio Registrazione dispositivi di rete e che è stato aggiunto a una CA emittente.
    Assicurarsi che il nome corrisponda esattamente a uno dei modelli del certificato elencati nel registro di sistema del server che esegue il servizio Registrazione dispositivi di rete. Accertarsi di specificare il nome del modello del certificato e non il nome visualizzato del modello del certificato. 
    Per trovare i nomi dei modelli di certificato, individuare la seguente chiave: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. I modelli di certificato verranno visualizzati come i valori per **EncryptionTemplate**, **GeneralPurposeTemplate**e **SignatureTemplate**. Per impostazione predefinita, il valore per i tre modelli di certificato è IPSECIntermediateOffline, che è associato al nome visualizzato del modello **IPSec (Offline request)**. 
    - **Formato nome soggetto**: dall'elenco, selezionare in che modo Intune crea automaticamente il nome soggetto nella richiesta certificato. Se il certificato è per un utente, è anche possibile includere l'indirizzo di posta elettronica dell'utente nel nome del soggetto. È possibile scegliere tra:
        - **Non configurato**
        - **Nome comune**
        - **Nome comune incluso l'indirizzo di posta elettronica**
        - **Nome comune come indirizzo di posta elettronica**
    - **Nome alternativo soggetto**: specificare in che modo Intune crea automaticamente i valori per il nome alternativo soggetto (SAN) nella richiesta certificato. Ad esempio, se si seleziona un tipo di certificato utente, è possibile includere il nome dell'entità utente (UPN) nel nome alternativo oggetto. Se il certificato client verrà usato per eseguire l'autenticazione in un server dei criteri di rete, è necessario impostare il nome alternativo oggetto sul nome dell'entità utente.
    - **Utilizzo chiave esteso** (Android): scegliere **Aggiungi** per aggiungere valori per lo scopo designato del certificato. Nella maggior parte dei casi il certificato richiederà l' **Autenticazione Client** in modo che l'utente o il dispositivo possa eseguire l'autenticazione a un server. È comunque possibile aggiungere altri utilizzi di chiavi secondo necessità. 
    - **Certificato radice** (Android): scegliere un profilo del certificato radice della CA già configurato e assegnato all'utente o al dispositivo. Questo certificato CA deve essere il certificato radice per l'autorità di certificazione che rilascerà il certificato che si sta configurando in questo profilo certificato.
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="task-4-assign-certificate-profiles"></a>Attività 4: assegnare i profili certificato

Prima di assegnare i profili certificato ai gruppi, considerare quanto segue:

- Quando si assegnano i profili certificato ai gruppi, il file del certificato dal profilo certificato CA attendibile viene installato nel dispositivo. Il dispositivo usa il profilo certificato SCEP o PKCS per creare una richiesta di certificato dal dispositivo.
- I profili certificato vengono installati solo nei dispositivi che eseguono la piattaforma usata durante la creazione del profilo.
- È possibile distribuire i profili certificato alle raccolte di utenti o di dispositivi.
- Per pubblicare rapidamente un certificato in un dispositivo dopo la registrazione del dispositivo, distribuire il profilo certificato a un gruppo di utenti piuttosto che di dispositivi. Se si distribuisce a un gruppo di dispositivi, è necessario eseguire una registrazione completa del dispositivo prima che questo riceva i criteri.
- Anche se si distribuisce ogni profilo separatamente, è necessario distribuire anche la CA radice attendibile e il profilo SCEP o PKCS. In caso contrario, i criteri di certificato SCEP o PKCS avranno esito negativo.

## <a name="next-steps"></a>Passaggi successivi
Vedere [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md) per informazioni generali sull'assegnazione dei profili di dispositivo.

