---
title: Registrare dispositivi con Windows AutoPilot
titleSuffix: Microsoft Intune
description: Informazioni su come registrare dispositivi Windows 10 con Windows AutoPilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 2ef7ebf495511e1d5c04aa8a9c459ba48f3dbb42
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180856"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>Registrare dispositivi Windows con Windows AutoPilot  
Windows AutoPilot semplifica la registrazione dei dispositivi. La compilazione e la gestione di immagini del sistema operativo personalizzate sono processi che richiedono molto tempo. Richiede tempo anche l'applicazione di queste immagini personalizzate del sistema operativo ai nuovi dispositivi per prepararli per l'uso prima della consegna agli utenti finali. Con Microsoft Intune e AutoPilot è possibile assegnare i nuovi dispositivi agli utenti finali senza la necessità di compilare, gestire e applicare le immagini del sistema operativo personalizzate ai dispositivi. Quando si usa Intune per gestire i dispositivi AutoPilot, è possibile gestire criteri, profili, applicazioni e così via sui dispositivi che sono stati registrati. Per una panoramica di vantaggi, scenari e prerequisiti, vedere [Panoramica di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Prerequisiti
- [La registrazione automatica di Windows deve essere abilitata](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [sottoscrizione di Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Come ottenere il file con estensione csv da importare in Intune

Vedere il cmdlet PowerShell per altre informazioni su come usarlo.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo/1.3/Content/Get-WindowsAutoPilotInfo.ps1)

## <a name="add-devices"></a>Aggiungere dispositivi

È possibile aggiungere i dispositivi di Windows AutoPilot importando un file CSV con le informazioni.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi** > **Importa**.

    ![Screenshot dei dispositivi di Windows Autopilot](media/enrollment-autopilot/autopilot-import-device.png)

2. In **Aggiungi dispositivi di Windows AutoPilot** passare a un file con estensione csv che elenca i dispositivi che si vuole aggiungere. Il file deve elencare i numeri di serie, gli ID prodotto Windows, gli hash hardware e facoltativamente gli ID ordine dei dispositivi.

    ![Screenshot dell'aggiunta dei dispositivi di Windows Autopilot](media/enrollment-autopilot/autopilot-import-device2.png)

3. Scegliere **Importa** per avviare l'importazione delle informazioni sui dispositivi. L'importazione può richiedere alcuni minuti.

4. Al termine dell'importazione scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi** > **Windows AutoPilot** > **Sincronizza**. Viene visualizzato un messaggio che informa che è in corso la sincronizzazione. Il processo potrebbe richiedere alcuni minuti, a seconda di quanti dispositivi sono in corso di sincronizzazione.

5. Aggiornare la vista per visualizzare i nuovi dispositivi.

## <a name="create-an-autopilot-device-group"></a>Creare un gruppo di dispositivi Autopilot

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Gruppi** > **Nuovo gruppo**.
2. Nel pannello **Gruppo**:
    1. In **Tipo gruppo** scegliere **sicurezza**.
    2. Immettere un **Nome gruppo** e una **Descrizione gruppo**.
    3. In **Tipo di appartenenza** scegliere **Assegnato** o **Dispositivo dinamico**.
3. Se nel passaggio precedente si è scelto **Assegnato** come **Tipo di appartenenza**, nella scheda **Gruppo** scegliere **Membri** e aggiungere i dispositivi AutoPilot al gruppo.
    I dispositivi Autopilot che non sono ancora registrati sono dispositivi il cui nome è uguale al numero di serie del dispositivo stesso.
4. Se nel passaggio precedente si è scelto **Dispositivi dinamici** come **Tipo di appartenenza**, nella scheda **Gruppo** scegliere **Membri dispositivo dinamico** e digitare uno dei codici seguenti nella casella **Regola avanzata**.
    - Se si vuole creare un gruppo che includa tutti i dispositivi AutoPilot, digitare `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Se si vuole creare un gruppo che includa tutti i dispositivi AutoPilot con un ID ordine specifico, digitare `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Se si vuole creare un gruppo che includa tutti i dispositivi AutoPilot con un ID ordine d'acquisto specifico, digitare `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Dopo aver aggiunto il codice **Regola avanzata** scegliere **Salva**.
5. Scegliere **Crea**.  

## <a name="create-an-autopilot-deployment-profile"></a>Creare un profilo di distribuzione Autopilot
I profili di distribuzione AutoPilot vengono usati per configurare i dispositivi AutoPilot.
1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo**.
2. Specificare un **Nome** e una **Descrizione** facoltativa.
3. Se si vuole che tutti i dispositivi nei gruppi assegnati vengano automaticamente converti in Autopilot, impostare **Converti tutti i dispositivi interessati in Autopilot** su **Sì**. Tutti i dispositivi non Autopilot nei gruppi assegnati verranno registrati con il servizio di distribuzione di Autopilot. L'elaborazione della registrazione può richiedere fino a 48 ore. Quando la registrazione viene annullata e il dispositivo viene reimpostato, Autopilot eseguirà la registrazione. Dopo che un dispositivo è stato registrato in questo modo, se si disabilita o rimuove l'assegnazione del profilo, il dispositivo non verrà rimosso dal servizio di distribuzione di Autopilot. È invece necessario [rimuovere direttamente il dispositivo](enrollment-autopilot.md#delete-autopilot-devices).
4. In **Modalità di distribuzione**, scegliere una di queste due opzioni:
    - **Definita dall'utente**: i dispositivi con questo profilo sono associati all'utente che esegue la registrazione del dispositivo. Le credenziali dell'utente sono necessarie per effettuare la registrazione del dispositivo.
    - **Distribuzione automatica (anteprima)** (richiede la [Windows 10 Insider Preview Build 17672](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente): i dispositivi con questo profilo non sono associati all'utente che esegue la registrazione del dispositivo. Le credenziali dell'utente non sono necessarie per effettuare la registrazione del dispositivo.
5. Nella casella **Join to Azure AD as** (Connetti ad Azure AD come) scegliere **Aggiunto ad Azure AD**.
6. Scegliere **Out-of-box experience (OOBE)** (Configurazione guidata), configurare le opzioni seguenti e scegliere **Salva**:
    - **Lingua (area geografica)***: scegliere la lingua da usare per il dispositivo. Questa opzione è disponibile solo se si è scelta l'opzione **Distribuzione automatica** in **Modalità di distribuzione**.
    - **Configura automaticamente la tastiera***: se è selezionata una **Lingua (area geografica)**, scegliere **Sì** per ignorare la pagina di selezione della tastiera. Questa opzione è disponibile solo se si è scelta l'opzione **Distribuzione automatica** in **Modalità di distribuzione**.
    - **Contratto di licenza con l'utente finale** (Windows 10, versione 1709 o successive): scegliere se si vuole visualizzare il contratto di licenza per gli utenti.
    - **Impostazioni privacy**: scegliere se si vuole visualizzare le impostazioni di privacy per gli utenti.
    - **Nascondi le opzioni di cambio di account (solo Windows Insider)**: scegliere **Nascondi** per impedire che le opzioni dell'account vengano visualizzate nella pagina di accesso aziendale e nella pagina degli errori di dominio. Per questa opzione è necessario [configurare le informazioni personalizzate distintive dell'azienda in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo di account utente**: scegliere il tipo di account utente (**Amministratore** o **Standard**).
    - **Applica il modello di nome computer (solo Windows Insider)**: scegliere **Sì** per creare un modello da usare per assegnare il nome a un dispositivo durante la registrazione. I nomi non devono superare i 15 caratteri e possono contenere lettere, numeri e trattini. I nomi non possono contenere solo numeri. Usare la [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) per aggiungere un numero di serie specifico per l'hardware. In alternativa, usare la [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) per aggiungere una stringa casuale di numeri, dove x corrisponde al numero di cifre da aggiungere. 

6. Scegliere **Crea** per creare il profilo. Il profilo di distribuzione di Autopilot è ora disponibile per l'assegnazione ai dispositivi.

*Sia **Lingua (area geografica)** che **Configura automaticamente la tastiera** sono disponibili solo se è stata scelta l'opzione **Distribuzione automatica (anteprima)** per **Modalità di distribuzione** (richiede la [Windows 10 Insider Preview Build 17672](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente).


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Assegnare un profilo di distribuzione di Autopilot a un gruppo di dispositivi

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > scegliere un profilo.
2. Nel pannello del profilo specifico, scegliere **Assegnazioni**. 
3. Scegliere **Selezione gruppi**, quindi nel pannello **Selezione gruppi** scegliere il o i gruppi di utenti ai quali assegnare il profilo e scegliere **Seleziona**.

## <a name="edit-an-autopilot-deployment-profile"></a>Modificare un profilo di distribuzione di AutoPilot
Dopo aver creato un profilo di distribuzione di AutoPilot, è possibile modificare alcune parti del profilo di distribuzione.   

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo**.
2. In **Registrazione Windows** nella sezione **Windows AutoPilot** scegliere **Profili di distribuzione**.
3. Selezionare il profilo da modificare.
4. Fare clic su **Proprietà** a sinistra per modificare il nome o la descrizione del profilo di distribuzione. Fare clic su **Salva** dopo aver apportato le modifiche.
5. Fare clic su **Impostazioni** per apportare modifiche alle impostazioni della configurazione guidata. Fare clic su **Salva** dopo aver apportato le modifiche.

> [!NOTE]
> Le modifiche al profilo vengono applicate ai dispositivi assegnati al profilo. Il profilo aggiornato non verrà tuttavia applicato a un dispositivo già registrato in Intune finché non saranno state completate la reimpostazione e la nuova registrazione del dispositivo.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Avvisi per dispositivi non assegnati Windows AutoPilot <!-- 163236 -->  

Gli avvisi indicheranno quanti dispositivi con il programma Autopilot non hanno profili di distribuzione di Autopilot. Usare le informazioni contenute nell'avviso per creare i profili e assegnarli ai dispositivi non assegnati. Selezionando l'avviso, verrà visualizzato un elenco completo di dispositivi Windows AutoPilot e le relative informazioni dettagliate.


Per visualizzare gli avvisi per i dispositivi non assegnati, in [Intune nel portale di Azure](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Panoramica** > **Dispositivi non assegnati**.  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Assegnare un utente a un dispositivo Autopilot specifico

È possibile assegnare un utente a un dispositivo Autopilot specifico. Questa assegnazione precompila un utente di Azure Active Directory nella pagina di accesso [distintiva dell'azienda](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) durante l'installazione di Windows. Consente inoltre di definire il nome di un messaggio di saluto personalizzato. Questa informazione non viene precompilata nella pagina di accesso di Windows né la modifica. Solo gli utenti con licenza di Intune possono essere assegnati con questa procedura.

Prerequisiti: il portale aziendale di Azure Active Directory deve essere configurato e deve essere presente la [Windows 10 Insider Preview Build](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente.

1. In [Intune nel portale di Azure](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi** > scegliere il dispositivo > **Assegna utente**.

    ![Screenshot di Assegna utente](media/enrollment-autopilot/assign-user.png)

2. Scegliere un utente di Azure con licenza per Intune e scegliere **Seleziona**.

    ![Screenshot di selezione utente](media/enrollment-autopilot/select-user.png)

3. Nella casella **Nome descrittivo** digitare un nome o accettare il valore predefinito. Questa stringa è il nome descrittivo visualizzato quando l'utente esegue l'accesso durante l'installazione di Windows.

    ![Screenshot di nome descrittivo](media/enrollment-autopilot/friendly-name.png)

4. Scegliere **OK**.


## <a name="delete-autopilot-devices"></a>Eliminare dispositivi di AutoPilot

È possibile eliminare i dispositivi di Windows AutoPilot non registrati.

1. Se i dispositivi sono registrati in Intune, è necessario prima [eliminarli dal portale di Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi**.

3. In **Dispositivi di Windows AutoPilot** scegliere i dispositivi che si vuole eliminare e quindi scegliere **Elimina**.

4. Confermare l'eliminazione scegliendo **Sì**. L'eliminazione può richiedere alcuni minuti.

## <a name="using-autopilot-in-other-portals"></a>Uso di AutoPilot in altri portali
Se non si è interessati alla gestione di dispositivi mobili, è possibile usare AutoPilot in altri portali. Nonostante sia possibile l'uso di altri portali, è consigliabile usare solo Intune per gestire le distribuzioni AutoPilot. Quando si usano Intune e un altro portale, Intune non riesce a:  

- Visualizzare le modifiche apportate ai profili creati in Intune ma modificati in un altro portale
- Sincronizzare i profili creati in un altro portale
- Visualizzare le modifiche apportate alle assegnazioni dei profili eseguite in un altro portale
- Sincronizzare le assegnazioni dei profili eseguite in un altro portale
- Visualizzare le modifiche dell'elenco dei dispositivi apportate in un altro portale

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot per dispositivi esistenti

È possibile raggruppare dispositivi Windows in base all'ID correlatore quando vengono registrati usando [AutoPilot per i dispositivi esistenti](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) tramite Configuration Manager. L'ID correlatore è un parametro del file di configurazione di Autopilot. L'[attributo del dispositivo Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) viene impostato automaticamente su "OfflineAutopilotprofile-\<ID correlatore\>". In questo modo sarà possibile creare gruppi dinamici di Azure AD arbitrari in base all'ID correlatore tramite l'attributo enrollmentprofileName.

>[!WARNING] 
> Dato che l'ID correlatore non è già elencato in Intune, il dispositivo può riportare qualsiasi ID correlatore desiderato. Se l'utente crea un ID correlatore corrispondente a un nome di profilo di AutoPilot o di Apple DEP, il dispositivo verrà aggiunto a un gruppo di dispositivi di Azure AD dinamico in base all'attributo enrollmentProfileName. Per evitare questo conflitto:
> - Creare sempre le regole di gruppo dinamico corrispondenti in base all'*intero* valore di enrollmentProfileName.
> - Non iniziare mai con "OfflineAutopilotprofile-" i nomi di profili AutoPilot o Apple DEP.

## <a name="next-steps"></a>Passaggi successivi
Dopo aver configurato Windows AutoPilot per i dispositivi Windows 10 registrati, scoprire come gestire i dispositivi. Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](https://docs.microsoft.com/intune/device-management).
