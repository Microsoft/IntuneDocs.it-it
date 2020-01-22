---
title: Registrare dispositivi con Windows AutoPilot
titleSuffix: Microsoft Intune
description: Informazioni su come registrare dispositivi Windows 10 con Windows AutoPilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb98ee2974cefeebb90689207388d5fe9229dad2
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036653"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Registrare dispositivi Windows in Intune con Windows AutoPilot  
Windows AutoPilot semplifica la registrazione dei dispositivi in Intune. La compilazione e la gestione di immagini del sistema operativo personalizzate sono processi che richiedono molto tempo. Richiede tempo anche l'applicazione di queste immagini personalizzate del sistema operativo ai nuovi dispositivi per prepararli per l'uso prima della consegna agli utenti finali. Con Microsoft Intune e AutoPilot è possibile assegnare i nuovi dispositivi agli utenti finali senza la necessità di compilare, gestire e applicare le immagini del sistema operativo personalizzate ai dispositivi. Quando si usa Intune per gestire i dispositivi AutoPilot, è possibile gestire criteri, profili, applicazioni e così via sui dispositivi che sono stati registrati. Per una panoramica di vantaggi, scenari e prerequisiti, vedere [Panoramica di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

Esistono quattro tipi di distribuzione Autopilot:
- [Modalità di distribuzione automatica](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) per chioschi multimediali, segnaletica digitale o un dispositivo condiviso
- [White Glove](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) consente ai partner o al personale IT di eseguire il pre-provisioning di un PC Windows 10 in modo che sia completamente configurato e pronto per le attività aziendali [Autopilot per i dispositivi esistenti](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) consente di distribuire facilmente la versione più recente di Windows 10 nei dispositivi esistenti
- [Modalità Definita dall'utente](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) per utenti tradizionali. 


## <a name="prerequisites"></a>Prerequisiti
- [Sottoscrizione di Intune](../fundamentals/licenses.md)
- [La registrazione automatica di Windows deve essere abilitata](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Sottoscrizione di Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Come ottenere il file con estensione csv da importare in Intune

Per altre informazioni, vedere il cmdlet di PowerShell seguente.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Aggiungere dispositivi

È possibile aggiungere i dispositivi di Windows AutoPilot importando un file CSV con le informazioni.

1. Nell'[Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **Windows** > **Registrazione Windows** > **Dispositivi** (in **Programma di distribuzione di Windows AutoPilot** > **Importa**).

    ![Screenshot dei dispositivi di Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device.png)

2. In **Aggiungi dispositivi di Windows AutoPilot** passare a un file con estensione csv che elenca i dispositivi che si vuole aggiungere. Il file CSV deve elencare i numeri di serie, gli ID prodotto Windows, gli hash hardware, i tag dei gruppi dei dispositivi e facoltativamente l'utente assegnato. È possibile avere fino a 500 righe nell'elenco. Per dettagli su come ottenere informazioni sul dispositivo, vedere [Aggiunta di dispositivi a Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/add-devices#device-identification). Usare l'intestazione e il formato di riga indicati di seguito:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Screenshot dell'aggiunta dei dispositivi di Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > Quando si usa il caricamento CSV per assegnare un utente, assicurarsi di assegnare UPN validi. Se si assegna un UPN non valido (nome utente errato), il dispositivo potrebbe risultare inaccessibile fino a quando non si rimuove l'assegnazione non valida. Durante il caricamento CSV, l'unica convalida eseguita sulla colonna **Utente assegnato** consiste nel verificare la validità del nome di dominio. Non è possibile eseguire la convalida dei singoli UPN per assicurarsi che si stia assegnando un utente esistente o corretto.

3. Scegliere **Importa** per avviare l'importazione delle informazioni sui dispositivi. L'importazione può richiedere alcuni minuti.

4. Al termine dell'importazione, scegliere **Dispositivi** > **Windows** > **Registrazione Windows** > **Dispositivi** (in **Programma di distribuzione di Windows AutoPilot** > **Sincronizza**). Viene visualizzato un messaggio che informa che è in corso la sincronizzazione. Il processo potrebbe richiedere alcuni minuti, a seconda di quanti dispositivi sono in corso di sincronizzazione.

5. Aggiornare la vista per visualizzare i nuovi dispositivi.

## <a name="create-an-autopilot-device-group"></a>Creare un gruppo di dispositivi Autopilot

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Gruppi** > **Nuovo gruppo**.
2. Nel pannello **Gruppo**:
    1. In **Tipo gruppo** scegliere **sicurezza**.
    2. Immettere un **Nome gruppo** e una **Descrizione gruppo**.
    3. In **Tipo di appartenenza** scegliere **Assegnato** o **Dispositivo dinamico**.
3. Se nel passaggio precedente si è scelto **Assegnato** come **Tipo di appartenenza**, nella scheda **Gruppo** scegliere **Membri** e aggiungere i dispositivi AutoPilot al gruppo.
    I dispositivi Autopilot che non sono ancora registrati sono dispositivi il cui nome è uguale al numero di serie del dispositivo stesso.
4. Se nel passaggio precedente si è scelto **Dispositivi dinamici** come **Tipo di appartenenza**, nella scheda **Gruppo** scegliere **Membri dispositivo dinamico** e digitare uno dei codici seguenti nella casella **Regola avanzata**. Queste regole eseguono la raccolta dei soli dispositivi Autopilot perché hanno come destinazione attributi in possesso solo dei dispositivi Autopilot. La creazione di un gruppo basato su attributi non Autopilot non garantirà che i dispositivi inclusi nel gruppo siano effettivamente registrati in Autopilot.
    - Se si vuole creare un gruppo che includa tutti i dispositivi AutoPilot, digitare: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Il campo del tag del gruppo di Intune è associato all'attributo OrderID nei dispositivi Azure AD. Se si vuole creare un gruppo che includa tutti i dispositivi Autopilot con un tag di gruppo (l'ID ordine del dispositivo di Azure AD) specifico, è necessario digitare: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Se si vuole creare un gruppo che includa tutti i dispositivi AutoPilot con un ID ordine d'acquisto specifico, digitare `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Dopo aver aggiunto il codice **Regola avanzata** scegliere **Salva**.
5. Scegliere **Crea**.  

## <a name="create-an-autopilot-deployment-profile"></a>Creare un profilo di distribuzione Autopilot
I profili di distribuzione AutoPilot vengono usati per configurare i dispositivi AutoPilot. È possibile creare fino a 350 profili per ogni tenant.
1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **Windows** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo**.
2. Nella pagina **Informazioni di base** specificare un **Nome** e una **Descrizione** facoltativa.

    ![Screenshot della pagina Informazioni di base](./media/enrollment-autopilot/create-profile-basics.png)

3. Se si vuole che tutti i dispositivi nei gruppi assegnati vengano automaticamente converti in Autopilot, impostare **Converti tutti i dispositivi interessati in Autopilot** su **Sì**. Tutti i dispositivi di proprietà dell'azienda non Autopilot nei gruppi assegnati verranno registrati con il servizio di distribuzione Autopilot. I dispositivi di proprietà personale non verranno convertiti in Autopilot. L'elaborazione della registrazione può richiedere fino a 48 ore. Quando la registrazione viene annullata e il dispositivo viene reimpostato, Autopilot eseguirà la registrazione. Dopo che un dispositivo è stato registrato in questo modo, se si disabilita o rimuove l'assegnazione del profilo, il dispositivo non verrà rimosso dal servizio di distribuzione di Autopilot. È invece necessario [rimuovere direttamente il dispositivo](enrollment-autopilot.md#delete-autopilot-devices).
4. Selezionare **Avanti**.
5. Nella pagina **Configurazione guidata** per **Modalità di distribuzione** scegliere una di queste due opzioni:
    - **Definita dall'utente**: I dispositivi con questo profilo sono associati all'utente che esegue la registrazione del dispositivo. Le credenziali dell'utente sono necessarie per effettuare la registrazione del dispositivo.
    - **Distribuzione automatica (anteprima)** (richiede Windows 10 versione 1809 o successive): i dispositivi con questo profilo non sono associati all'utente che esegue la registrazione del dispositivo. Le credenziali dell'utente non sono necessarie per effettuare la registrazione del dispositivo. Quando a un dispositivo non è associato alcun utente, i criteri di conformità basati sull'utente non sono applicabili. Quando si usa la modalità di distribuzione automatica, verranno applicati solo i criteri di conformità destinati al dispositivo.

    ![Screenshot della pagina Configurazione guidata](./media/enrollment-autopilot/create-profile-outofbox.png)

6. Nella casella **Join to Azure AD as** (Connetti ad Azure AD come) scegliere **Aggiunto ad Azure AD**.
7. Configurare le opzioni seguenti:
    - **Contratto di licenza con l'utente finale**: (Windows 10, versione 1709 o successive): scegliere se si vuole visualizzare il contratto di licenza per gli utenti.
    - **Impostazioni di privacy**: scegliere se si vuole visualizzare le impostazioni di privacy per gli utenti.
    >[!IMPORTANT]
    >Il valore predefinito per l'impostazione Dati di diagnostica varia in base alle versioni di Windows. Per i dispositivi che eseguono Windows 10, versione 1903, il valore predefinito è impostato su Completa durante l'esperienza predefinita. Per altre informazioni, vedere i [dati di diagnostica di Windows](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - **Nascondi le opzioni di cambio di account (richiede Windows 10 versione 1809 o successiva)** : scegliere **Nascondi** per impedire che le opzioni dell'account vengano visualizzate nella pagina di accesso aziendale e nella pagina degli errori di dominio. Per questa opzione è necessario [configurare le informazioni personalizzate distintive dell'azienda in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo di account utente**: scegliere il tipo di account utente (**Amministratore** o **Standard**). Per consentire all'utente che aggiunge il dispositivo di essere un amministratore locale, aggiungerlo al gruppo di amministratori locale. L'utente non viene abilitato come amministratore predefinito nel dispositivo.
    - **Consenti modalità " White Glove" per OOBE**  (richiede Windows 10, versione 1903 o successive; [requisiti fisici aggiuntivi](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): scegliere **Sì** per consentire il supporto per la modalità "White Glove".
    - **Applica il modello di nome di dispositivo** (richiede Windows 10 versione 1809 o successive e un tipo di join per Azure AD): scegliere **Sì** per creare un modello da usare per assegnare il nome a un dispositivo durante la registrazione. I nomi non devono superare i 15 caratteri e possono contenere lettere, numeri e trattini. I nomi non possono contenere solo numeri. Usare la [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) per aggiungere un numero di serie specifico per l'hardware. In alternativa, usare la [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) per aggiungere una stringa casuale di numeri, dove x corrisponde al numero di cifre da aggiungere. È possibile specificare solo un prefisso per dispositivi ibridi in un [profilo di aggiunta a un dominio](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile). 
    - **Lingua (area geografica)** \*: scegliere la lingua da usare per il dispositivo. Questa opzione è disponibile solo se si è scelta l'opzione **Distribuzione automatica** in **Modalità di distribuzione**.
    - **Configura automaticamente la tastiera**\*: se è selezionata una **Lingua (area geografica)** , scegliere **Sì** per ignorare la pagina di selezione della tastiera. Questa opzione è disponibile solo se si è scelta l'opzione **Distribuzione automatica** in **Modalità di distribuzione**.
8. Selezionare **Avanti**.
9. Nella pagina **Tag di ambito** aggiungere i tag di ambito da applicare a questo profilo (facoltativo). Per altre informazioni sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).
10. Selezionare **Avanti**.
11. Nella pagina **Assegnazioni** scegliere **Gruppi selezionati** per **Assegna a**.

    ![Screenshot della pagina Assegnazioni](./media/enrollment-autopilot/create-profile-assignments.png)

12. Scegliere **Selezionare i gruppi da includere** e scegliere i gruppi da includere in questo profilo.
13. Se si vogliono escludere determinati gruppi, scegliere **Selezionare i gruppi da escludere** e scegliere i gruppi da escludere.
14. Selezionare **Avanti**.
15. Nella pagina **Rivedi e crea** scegliere **Crea** per creare il profilo.

    ![Screenshot della pagina Rivedi](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune verificherà periodicamente la presenza di nuovi dispositivi nei gruppi assegnati e quindi avvierà il processo di assegnazione dei profili a quei dispositivi. Questo processo può richiedere alcuni minuti. Prima di distribuire un dispositivo, assicurarsi che questo processo sia stato completato.  In **Dispositivi** > **Windows** > **Registrazione Windows** > **Dispostivi** (in **Programma di distribuzione di Windows AutoPilot** è possibile verificare che lo stato del profilo passi da "Non assegnato" ad "Assegnazione" e infine ad "Assegnato".

## <a name="edit-an-autopilot-deployment-profile"></a>Modificare un profilo di distribuzione di AutoPilot
Dopo aver creato un profilo di distribuzione di AutoPilot, è possibile modificare alcune parti del profilo di distribuzione.   

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **Windows** > **Registrazione Windows** > **Profili di distribuzione**.
2. Selezionare il profilo da modificare.
3. Selezionare **Proprietà** a sinistra per modificare il nome o la descrizione del profilo di distribuzione. Fare clic su **Salva** dopo aver apportato le modifiche.
5. Fare clic su **Impostazioni** per apportare modifiche alle impostazioni della configurazione guidata. Fare clic su **Salva** dopo aver apportato le modifiche.

> [!NOTE]
> Le modifiche al profilo vengono applicate ai dispositivi assegnati al profilo. Il profilo aggiornato non verrà tuttavia applicato a un dispositivo già registrato in Intune finché non saranno state completate la reimpostazione e la nuova registrazione del dispositivo.

## <a name="edit-autopilot-device-attributes"></a>Modificare gli attributi dei dispositivi Autopilot
Dopo aver caricato un dispositivo Autopilot, è possibile modificarne alcuni attributi.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selezionare **Dispositivi** > **Windows** > **Registrazione Windows** > **Dispositivi** (in **Programma di distribuzione di Windows AutoPilot**).
2. Selezionare il dispositivo da modificare.
3. Nel riquadro a destra della schermata è possibile modificare il nome del dispositivo, il tag di gruppo o il nome descrittivo (se è stato assegnato un utente).
4. Selezionare **Salva**.

> [!NOTE]
> I nomi dei dispositivi possono essere configurati per tutti i dispositivi, ma vengono ignorati nelle distribuzioni aggiunte ad Azure AD ibrido. Il nome del dispositivo deriva comunque dal profilo di aggiunta al dominio per i dispositivi di Azure AD ibrido.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Avvisi per dispositivi non assegnati Windows AutoPilot  <!-- 163236 -->  

Gli avvisi indicheranno quanti dispositivi con il programma Autopilot non hanno profili di distribuzione di Autopilot. Usare le informazioni contenute nell'avviso per creare i profili e assegnarli ai dispositivi non assegnati. Selezionando l'avviso, verrà visualizzato un elenco completo di dispositivi Windows AutoPilot e le relative informazioni dettagliate.

Per visualizzare gli avvisi per i dispositivi non assegnati, nella [interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), scegliere **Dispositivi** > **Panoramica** > **Avvisi per la registrazione** > **Dispositivi non assegnati**.  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Assegnare un utente a un dispositivo Autopilot specifico

È possibile assegnare un utente a un dispositivo Autopilot specifico. Questa assegnazione precompila un utente di Azure Active Directory nella pagina di accesso [distintiva dell'azienda](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) durante l'installazione di Windows. Consente inoltre di definire il nome di un messaggio di saluto personalizzato. Questa informazione non viene precompilata nella pagina di accesso di Windows né la modifica. Solo gli utenti con licenza di Intune possono essere assegnati con questa procedura.

Prerequisiti: il portale aziendale di Azure Active Directory deve essere configurato; Windows 10 versione 1809 o successiva.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), scegliere **Dispositivi** > **Windows** > **Registrazione Windows** > **Dispositivi** (in **Programma di distribuzione di Windows AutoPilot** > scegliere il dispositivo > **Assegna utente**.

    ![Screenshot di Assegna utente](./media/enrollment-autopilot/assign-user.png)

2. Scegliere un utente di Azure con licenza per Intune e scegliere **Seleziona**.

    ![Screenshot di selezione utente](./media/enrollment-autopilot/select-user.png)

3. Nella casella **Nome descrittivo** digitare un nome o accettare il valore predefinito. Questa stringa è il nome descrittivo visualizzato quando l'utente esegue l'accesso durante l'installazione di Windows.

    ![Screenshot di nome descrittivo](./media/enrollment-autopilot/friendly-name.png)

4. Scegliere **OK**.


## <a name="delete-autopilot-devices"></a>Eliminare dispositivi di AutoPilot

È possibile eliminare i dispositivi di Windows Autopilot non registrati in Intune:

- Eliminare i dispositivi da Windows Autopilot in **Dispositivi** > **Windows** > **Registrazione Windows** > **Dispositivi** (in **Programma di distribuzione di Windows AutoPilot**). Scegliere i dispositivi da eliminare, quindi scegliere **Elimina**. L'eliminazione dei dispositivi di Windows Autopilot richiede alcuni minuti.

La rimozione completa di un dispositivo dal tenant richiede l'eliminazione dei record relativi a dispositivi di Intune, dispositivi di Azure Active Directory e dispositivi di Windows Autopilot. Queste operazioni possono essere eseguite in Intune:

1. Se i dispositivi sono registrati in Intune, è necessario prima [eliminarli dal pannello Tutti i dispositivi di Intune](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Eliminare i dispositivi di Azure Active Directory tramite **Dispositivi** > **Dispositivi di Azure AD**.

3. Eliminare i dispositivi da Windows Autopilot in **Dispositivi** > **Windows** > **Registrazione Windows** > **Dispositivi** (in **Programma di distribuzione di Windows AutoPilot**). Scegliere i dispositivi da eliminare, quindi scegliere **Elimina**. L'eliminazione dei dispositivi di Windows Autopilot richiede alcuni minuti.

## <a name="using-autopilot-in-other-portals"></a>Uso di AutoPilot in altri portali
Se non si è interessati alla gestione di dispositivi mobili, è possibile usare AutoPilot in altri portali. Nonostante sia possibile l'uso di altri portali, è consigliabile usare solo Intune per gestire le distribuzioni AutoPilot. Quando si usano Intune e un altro portale, Intune non riesce a:  

- Visualizzare le modifiche apportate ai profili creati in Intune ma modificati in un altro portale
- Sincronizzare i profili creati in un altro portale
- Visualizzare le modifiche apportate alle assegnazioni dei profili eseguite in un altro portale
- Sincronizzare le assegnazioni dei profili eseguite in un altro portale
- Visualizzare le modifiche dell'elenco dei dispositivi apportate in un altro portale

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot per dispositivi esistenti

È possibile raggruppare dispositivi Windows in base all'ID correlatore quando vengono registrati usando [AutoPilot per i dispositivi esistenti](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) tramite Configuration Manager. L'ID correlatore è un parametro del file di configurazione di Autopilot. L'[attributo del dispositivo Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) viene impostato automaticamente su "OfflineAutopilotprofile-\<ID correlatore\>". In questo modo sarà possibile creare gruppi dinamici di Azure AD arbitrari in base all'ID correlatore tramite l'attributo enrollmentprofileName.

>[!WARNING] 
> Dato che l'ID correlatore non è già elencato in Intune, il dispositivo può riportare qualsiasi ID correlatore desiderato. Se l'utente crea un ID correlatore corrispondente a un nome di profilo di AutoPilot o di Apple DEP, il dispositivo verrà aggiunto a un gruppo di dispositivi di Azure AD dinamico in base all'attributo enrollmentProfileName. Per evitare questo conflitto:
> - Creare sempre le regole di gruppo dinamico corrispondenti in base all'*intero* valore di enrollmentProfileName.
> - Non iniziare mai con "OfflineAutopilotprofile-" i nomi di profili AutoPilot o Apple DEP.

## <a name="next-steps"></a>Passaggi successivi
Dopo aver configurato Windows AutoPilot per i dispositivi Windows 10 registrati, scoprire come gestire i dispositivi. Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](../remote-actions/device-management.md).
