---
title: Installare il software client per PC
description: Usare questa guida per far gestire i computer Windows dal software client di Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
ms.date: 07/13/2017
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4dd9fc00475c8a8eea28bef2150f25639ac38e15
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572607"
---
# <a name="install-the-intune-software-client-on-windows-pcs"></a>Installare il client software di Intune nei PC Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> È possibile usare Microsoft Intune per gestire i PC Windows [come dispositivi mobili con la soluzione di gestione dei dispositivi mobili (MDM)](windows-enroll.md) o come computer con il software client di Intune come descritto di seguito. Microsoft consiglia tuttavia ai clienti di [usare la soluzione di gestione MDM](windows-enroll.md) laddove possibile. Per altre informazioni, vedere [Confrontare la gestione dei PC Windows come computer o come dispositivi mobili](pc-management-comparison.md). 


È possibile registrare i PC Windows installando il software client di Intune. Il software client di Intune può essere installato usando i metodi seguenti:

- Dall'amministratore IT usando uno di questi metodi: installazione manuale, Criteri di gruppo o installazione inclusa in un'immagine disco

- Dagli utenti finali, che installano manualmente il software client

Il software client Intune contiene il software minimo necessario per registrare il PC nella gestione di Intune. Dopo la registrazione di un PC, il software client di Intune scarica il software client completo necessario per la gestione del PC.

Questa serie di download limita l'impatto sulla larghezza di banda della rete e riduce al minimo il tempo necessario per la registrazione iniziale del PC in Intune. Garantisce anche che il client disponga del software più aggiornato dopo il completamento del secondo download.

Una licenza Intune consente l'installazione del software client Intune in cinque PC.

## <a name="download-the-intune-client-software"></a>Download del software client di Intune

Tutti i metodi, salvo quelli in cui l'utente installa il software client di Intune autonomamente, richiedono che gli amministratori IT scarichino prima di tutto il software per poterlo distribuire successivamente agli utenti finali.

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Amministrazione** &gt; **Download software client**.

   ![Scaricare il client PC Intune](./media/https://docs.microsoft.com/intune/media/install-the-windows-pc-client/pc-sa-client-download.png)

2. Nella pagina **Download software client** fare clic su **Scarica software client**. Salvare il pacchetto **Microsoft_Intune_Setup.zip** contenente il software in un percorso protetto della rete locale.

   Il pacchetto di installazione del software client di Intune contiene informazioni univoche e specifiche sull'account, disponibili tramite un certificato incorporato. Se utenti non autorizzati ottengono l'accesso al pacchetto di installazione, possono registrare PC nell'account rappresentato dal certificato incorporato ed eventualmente ottenere l'accesso alle risorse aziendali.

3. Estrarre il contenuto del pacchetto di installazione in un percorso sicuro nella rete locale.

    > [!IMPORTANT]
    > Non rinominare o rimuovere il file **ACCOUNTCERT** estratto, altrimenti l'installazione del software client avrà esito negativo.

## <a name="deploy-the-client-software-manually"></a>Distribuire manualmente il software client

Nei computer in cui verrà installato il software client passare alla cartella in cui si trovano i file di installazione del software client. Quindi eseguire **Microsoft_Intune_Setup.exe** per installare il software client.

> [!NOTE]
> Lo stato dell'installazione viene visualizzato quando si passa il mouse sull'icona nella barra delle applicazioni del computer client.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Distribuire il software client usando Criteri di gruppo

1. Nella cartella che contiene i file **Microsoft_Intune_Setup.exe** e **MicrosoftIntune.accountcert** eseguire questo comando per estrarre i programmi di installazione basati su Windows Installer per i computer a 32 e 64 bit:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2. Copiare i file **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** e **MicrosoftIntune.accountcert** in un percorso di rete accessibile a tutti i computer in cui verrà installato il software client.

    > [!IMPORTANT]
    > Non separare o rinominare i file altrimenti l'installazione del software client non riuscirà.

3. Usare Criteri di gruppo per distribuire il software nei computer della rete.

    Per altre informazioni sull'uso di Criteri di gruppo per distribuire automaticamente il software, vedere [Criteri di gruppo per principianti](https://technet.microsoft.com/library/hh147307.aspx).

## <a name="deploy-the-client-software-as-part-of-an-image"></a>Installare il software client come parte di un'immagine
Il software client di Intune può essere distribuito nei computer come parte di un'immagine del sistema operativo, usando come traccia la seguente procedura:

1. Copiare i file di installazione client **Microsoft_Intune_Setup.exe** e **MicrosoftIntune.accountcert** nella cartella **%Systemdrive%\Temp\Microsoft_Intune_Setup** del computer di riferimento.

2. Creare la voce del Registro di sistema **WindowsIntuneEnrollPending** aggiungendo il comando seguente allo script **SetupComplete.cmd** :

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3. Aggiungere il comando seguente a **setupcomplete.cmd** per eseguire il pacchetto di registrazione con l'argomento della riga di comando /PrepareEnroll:

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > Lo script **SetupComplete.cmd** consente a Installazione di Windows di modificare il sistema prima che un utente effettui l'accesso. Al termine dell'esecuzione del programma Installazione di Windows, l'argomento della riga di comando **/PrepareEnroll** predispone un computer di destinazione per la registrazione automatica in Intune.

4. Inserire **SetupComplete.cmd** nella cartella **%Windir%\Setup\Scripts** del computer di riferimento.

5. Acquisire un'immagine del computer di riferimento e distribuirla nei computer di destinazione.

    Dopo aver riavviato il computer di destinazione una volta eseguito il programma Installazione di Windows, verrà creata la chiave del Registro di sistema **WindowsIntuneEnrollPending** . Il pacchetto di registrazione verifica se il computer è registrato. Se il computer è registrato, non verrà intrapresa alcuna azione. Se il computer non è registrato, il pacchetto creerà un'attività di registrazione automatica in Microsoft Intune.

    L'attività di registrazione automatica, eseguita al successivo orario pianificato, verifica l'esistenza del valore del Registro di sistema **WindowsIntuneEnrollPending** e tenta di registrare il PC di destinazione in Intune. Se il tentativo non riesce a causa di un errore, la registrazione verrà ripetuta al momento della successiva esecuzione dell'attività. I tentativi continuano per un mese.

    L'attività di registrazione automatica, il valore del Registro di sistema **WindowsIntuneEnrollPending** e il certificato dell'account vengono eliminati dal computer di destinazione al completamento della registrazione o dopo un mese, a seconda di quale condizione si verifica per prima.

## <a name="instruct-users-to-self-enroll"></a>Istruire gli utenti per la registrazione automatica

Per installare il software client di Intune, gli utenti possono visitare il [sito Web del portale aziendale](https://portal.manage.microsoft.com). Le informazioni specifiche visibili agli utenti nel portale Web variano in base all'autorità di gestione dei dispositivi mobili (MDM) dell'account e a piattaforma e versione del PC dell'utente.

Se agli utenti non è stata assegnata una licenza di Intune o se l'autorità MDM dell'organizzazione non è stata impostata su Intune, gli utenti non visualizzeranno alcuna opzione per la registrazione.

Se agli utenti è stata assegnata una licenza di Intune e l'autorità MDM dell'organizzazione è stata impostata su Intune:

- Per gli utenti dei PC Windows 7 o Windows 8 viene visualizzata SOLO l'opzione che consente di eseguire la registrazione a Intune scaricando e installando il software client per PC esclusivo per la propria organizzazione.

- Per gli utenti dei PC Windows 8.1 o Windows 10 sono disponibili due opzioni di registrazione:

  - **Registrare il PC come dispositivo mobile**: gli utenti scelgono il pulsante **Informazioni sull'iscrizione** e visualizzano le istruzioni per registrare il PC come dispositivo mobile. Il pulsante viene visualizzato in primo piano, poiché la registrazione MDM è l'opzione predefinita e preferita per la registrazione. Tuttavia, l'opzione MDM non è pertinente in questo argomento, che riguarda solo l'installazione del software client.
  - **Registrare il PC usando il software client di Intune**: è necessario indicare agli utenti di selezionare il collegamento **Fare clic qui per scaricare**, che li guida nell'installazione del software client.

Nella tabella seguente sono riepilogate le opzioni.

  ![Opzioni di registrazione predefinite per piattaforma](./media/install-the-windows-pc-client/default-enrollment-options-table.png)

Le schermate seguenti illustrano ciò che gli utenti vedono quando registrano i propri dispositivi usando il client software.

Per prima cosa gli utenti devono identificare o registrare il dispositivo.

  ![identificare o registrare il dispositivo](./media/install-the-windows-pc-client/identify-device-or-enroll.png)

Per fare in modo che gli utenti installino il software client per PC, è necessario indicare loro di selezionare il collegamento **Fare clic qui per scaricare**, che consente agli utenti di scaricare il software client per PC e li guida nel processo di installazione. Il pulsante **Informazioni sull'iscrizione** porta gli utenti alla documentazione che spiega come iscriversi usando la registrazione MDM, che non è pertinente in queste istruzioni relative al software client.

  ![scegliere il collegamento Fare clic qui per scaricare](./media/install-the-windows-pc-client/enroll-your-windows-device.png)

Quando gli utenti fanno clic sul collegamento vedono il pulsante **Scarica software**, che selezionano per avviare l'installazione del software client per PC.

  ![scegliere il pulsante Scarica software](./media/install-the-windows-pc-client/download-pc-client-software.png)

Agli utenti viene quindi chiesto di accedere con le proprie credenziali aziendali.

  ![Accedere con le proprie credenziali](./media/install-the-windows-pc-client/sign-in-to-intune.png)

Gli utenti accedono alla pagina di benvenuto per l'installazione.

  ![Pagina di benvenuto per l'installazione client per PC](./media/install-the-windows-pc-client/welcome-to-pc-agent-install-wizard.png)

Gli utenti scelgono **Avanti** e viene avviata l'installazione.

  ![Pagina di benvenuto per l'installazione client per PC](./media/install-the-windows-pc-client/welcome-to-pc-agent-install-wizard.png)

Al termine dell'installazione gli utenti scelgono **Fine**.

  ![Completare l'installazione client per PC](./media/install-the-windows-pc-client/completed-the-setup-wizard.png)

Se gli utenti tentano di registrare il proprio PC come dispositivo mobile dopo averlo già registrato con il software client per PC di Intune, apparirà la seguente schermata di errore.

  ![Schermata visualizzata se il PC è già registrato](./media/install-the-windows-pc-client/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>Controllare e convalidare la distribuzione del client
Usare una delle seguenti procedure per controllare e convalidare la distribuzione del client.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>Per verificare l'installazione del software client dalla console di amministrazione di Microsoft Intune

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i computer**.

2. Trovare i computer gestiti che comunicano con Intune o cercare un computer gestito specifico, digitando il nome intero o parte di esso nella casella **Cerca dispositivi**.

3. Verificare lo stato del computer nel riquadro inferiore della console. Risolvere gli eventuali errori.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>Per creare un report di inventario dei computer al fine di visualizzare tutti i computer registrati

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Report** &gt; **Report inventario computer**.

2. Nella pagina **Crea nuovo report** lasciare i valori predefiniti in tutti i campi (salvo se si prevede di applicare filtri) e fare clic su **Visualizza report**.

3. In una nuova finestra viene aperta la pagina **Report inventario computer** che consente di visualizzare tutti i computer che sono stati registrati in Intune.

    > [!TIP]
    > Fare clic su un'intestazione di colonna nel report per ordinare l'elenco in base al contenuto della colonna.

## <a name="uninstall-the-windows-client-software"></a>Disinstallare il software client Windows

È possibile annullare la registrazione di un software client Windows in due modi:

- Dalla console di amministrazione di Intune (metodo consigliato)
- Da un prompt dei comandi nel client

### <a name="unenroll-by-using-the-intune-admin-console"></a>Annullare la registrazione usando la console di amministrazione di Intune

Per annullare la registrazione del software client usando la console di amministrazione di Intune, passare a **Gruppi** > **Tutti i computer** > **Dispositivi**. Fare clic con il pulsante destro del mouse sul client e selezionare **Disattiva/Cancella**.

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>Annullare la registrazione usando un prompt dei comandi nel client

Usando un prompt dei comandi con privilegi elevati, eseguire uno dei comandi seguenti.

**Metodo 1**:

    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune

**Metodo 2** Si noti che tutti gli agenti sono installati in ogni SKU di Windows:

    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall
    wmic product where name="Microsoft Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall
    wmic product where name="Microsoft Policy Platform" call uninstall
    wmic product where name="Microsoft Security Client" call uninstall
    wmic product where name="Microsoft Online Management Client" call uninstall
    wmic product where name="Microsoft Online Management Client Service" call uninstall
    wmic product where name="Microsoft Easy Assist v2" call uninstall
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Microsoft Intune Center" call uninstall
    wmic product where name="Microsoft Online Management Update Manager" call uninstall
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall
    wmic product where name="Microsoft Intune" call uninstall
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall
    wmic product where name="Windows Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Windows Online Management Policy Agent" call uninstall
    wmic product where name="Windows Policy Platform" call uninstall
    wmic product where name="Windows Security Client" call uninstall
    wmic product where name="Windows Online Management Client" call uninstall
    wmic product where name="Windows Online Management Client Service" call uninstall
    wmic product where name="Windows Easy Assist v2" call uninstall
    wmic product where name="Windows Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Windows Intune Center" call uninstall
    wmic product where name="Windows Online Management Update Manager" call uninstall
    wmic product where name="Windows Online Management Agent Installer" call uninstall
    wmic product where name="Windows Intune" call uninstall

> [!TIP]
> L'annullamento della registrazione del client lascerà un record lato server non aggiornato per il client interessato. Poiché il processo di annullamento della registrazione è asincrono e sono presenti nove agenti da disinstallare, è possibile che siano necessari fino a 30 minuti per il completamento.

### <a name="check-the-unenrollment-status"></a>Controllare lo stato di annullamento della registrazione

Controllare "%ProgramFiles%\Microsoft\OnlineManagement" e verificare che a sinistra siano visibili soltanto le directory seguenti:

- AgentInstaller
- Logs
- Aggiornamenti
- Comune

### <a name="remove-the-onlinemanagement-folder"></a>Rimuovere la cartella OnlineManagement

Il processo di annullamento della registrazione non rimuove la cartella OnlineManagement. Attendere 30 minuti dopo la disinstallazione ed eseguire il comando seguente. Se il comando viene eseguito troppo presto, la disinstallazione potrebbe rimanere in uno stato sconosciuto. Per rimuovere la cartella, avviare un prompt con privilegi elevati ed eseguire:

    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".

### <a name="next-steps"></a>Passaggi successivi
[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
