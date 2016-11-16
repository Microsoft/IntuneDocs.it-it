---

title: Installare il software client per PC | Microsoft Intune
description: Usare questa guida per far gestire i computer Windows dal software client di Microsoft Intune.
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 738b6bedcefbfd8bf0fa7bde5b86c79293af527e
ms.openlocfilehash: 7d239a80ed68d39b2a7179a45178ba6ae11c5423


---

# <a name="install-the-intune-software-client-on-windows-pcs"></a>Installare il client software di Intune nei PC Windows
È possibile registrare i PC Windows installando il software client di Intune. Il software client di Intune può essere installato nei modi seguenti:

- Installazione manuale
- Installazione con Criteri di gruppo
- Inclusione in un'immagine disco
- Installazione da parte dell'utente

Il client software Intune scaricato inizialmente contiene il software minimo necessario per registrare il PC nella gestione di Intune. Dopo la registrazione di un PC, il client software Intune scarica il software client completo necessario per la gestione del PC.

Questa serie di download di riduce al minimo il tempo necessario per la registrazione iniziale del PC in Intune. Garantisce anche che il client disponga del software più aggiornato dopo il completamento del secondo download.

## <a name="download-the-intune-client-software"></a>Download del software client di Intune

Tutti i metodi, salvo quelli in cui l'utente installa il software client di Intune autonomamente, richiedono il download del software per la sua distribuzione.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Amministrazione** &gt; **Download software client**.

  ![Scaricare il client PC Intune](../media/pc-sa-client-download.png)

2.  Nella pagina **Download software client** fare clic su **Scarica software client**. Salvare il pacchetto **Microsoft_Intune_Setup.zip** contenente il software in un percorso protetto della rete locale.

    > [!NOTE]
    > Il pacchetto di installazione del software client di Intune contiene le informazioni sull'account dell'utente. Se utenti non autorizzati ottengono l'accesso al pacchetto di installazione, possono registrare computer nell'account rappresentato dal certificato incorporato ed eventualmente ottenere l'accesso alle risorse aziendali.

3.  Estrarre il contenuto del pacchetto di installazione in un percorso sicuro nella rete locale.

    > [!IMPORTANT]
    > Non rinominare o rimuovere il file **ACCOUNTCERT** estratto, altrimenti l'installazione del software client non riuscirà.

## <a name="deploy-the-client-software-manually"></a>Distribuire manualmente il software client

In un computer, passare alla cartella in cui si trovano i file di installazione del software client. Quindi eseguire **Microsoft_Intune_Setup.exe** per installare il software client.

    > [!NOTE]
    > The status of the installation is displayed when you hover over the icon in the taskbar on the client computer.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Distribuire il software client usando Criteri di gruppo

1.  Nella cartella che contiene i file **Microsoft_Intune_Setup.exe** e **MicrosoftIntune.accountcert** eseguire questo comando per estrarre i programmi di installazione basati su Windows Installer per i computer a 32 e 64 bit:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Copiare i file **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** e **MicrosoftIntune.accountcert** in un percorso di rete accessibile a tutti i computer in cui verrà installato il software client.

    > [!IMPORTANT]
    > Non separare o rinominare i file altrimenti l'installazione del software client non riuscirà.

3.  Usare Criteri di gruppo per distribuire il software nei computer della rete.

    Per altre informazioni sull'utilizzo di Criteri di gruppo per distribuire automaticamente il software, vedere la documentazione di Windows Server.

## <a name="deploy-the-client-software-as-part-of-an-image"></a>Installare il software client come parte di un'immagine
Il software client di Intune può essere distribuito nei computer come parte di un'immagine del sistema operativo, usando come traccia la seguente procedura:

1.  Copiare i file di installazione client **Microsoft_Intune_Setup.exe** e **MicrosoftIntune.accountcert** nella cartella **%Systemdrive%\Temp\Microsoft_Intune_Setup** del computer di riferimento.

2.  Creare la voce del Registro di sistema **WindowsIntuneEnrollPending** aggiungendo il comando seguente allo script **SetupComplete.cmd** :

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  Aggiungere il comando seguente a **setupcomplete.cmd** per eseguire il pacchetto di registrazione con l'argomento della riga di comando /PrepareEnroll:

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > Lo script **SetupComplete.cmd** consente a Installazione di Windows di modificare il sistema prima che un utente effettui l'accesso. Al termine dell'esecuzione del programma Installazione di Windows, l'argomento della riga di comando **/PrepareEnroll** predispone un computer di destinazione per la registrazione automatica in Intune.

4.  Inserire **SetupComplete.cmd** nella cartella **%Windir%\Setup\Scripts** del computer di riferimento.

5.  Acquisire un'immagine del computer di riferimento e distribuirla nei computer di destinazione.

Dopo aver riavviato il computer di destinazione una volta eseguito il programma Installazione di Windows, verrà creata la chiave del Registro di sistema **WindowsIntuneEnrollPending** . Il pacchetto di registrazione verifica se il computer è registrato. Se il computer è registrato, non verrà intrapresa alcuna azione. Se il computer non è registrato, il pacchetto creerà un'attività di registrazione automatica in Microsoft Intune.

L'attività di registrazione automatica, eseguita al successivo orario pianificato, verifica l'esistenza del valore del Registro di sistema **WindowsIntuneEnrollPending** e tenta di registrare il PC di destinazione in Intune. Se il tentativo non riesce a causa di un errore, la registrazione verrà ripetuta al momento della successiva esecuzione dell'attività. I tentativi continuano per un mese.

L'attività di registrazione automatica, il valore del Registro di sistema **WindowsIntuneEnrollPending** e il certificato dell'account vengono eliminati dal computer di destinazione al completamento della registrazione o dopo un mese, a seconda di quale condizione si verifica per prima.

## <a name="instruct-users-to-selfenroll"></a>Istruire gli utenti per la registrazione automatica

Gli utenti possono installare il software client Intune visitando il [sito Web del portale aziendale](http://portal.manage.microsoft.com). Se il portale Web rileva che il dispositivo è un PC Windows, verrà chiesto agli utenti di registrare il PC scaricando il client software di Intune. Dopo il download del software, gli utenti possono installarlo per attivare la gestione dei PC.

![Portale di Intune che richiede di scaricare il client software di Intune](../media/software-client-download.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>Controllare e convalidare la distribuzione del client
Usare una delle seguenti procedure per controllare e convalidare la distribuzione del client.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>Per verificare l'installazione del software client dalla console di amministrazione di Microsoft Intune

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i computer**.

2.  Trovare i computer gestiti che comunicano con Intune o cercare un computer gestito specifico, digitando il nome intero o parte di esso nella casella **Cerca dispositivi**.

3.  Verificare lo stato del computer nel riquadro inferiore della console. Risolvere gli eventuali errori.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>Per creare un report di inventario dei computer al fine di visualizzare tutti i computer registrati

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Report** &gt; **Report inventario computer**.

2.  Nella pagina **Crea nuovo report** lasciare i valori predefiniti in tutti i campi (salvo se si prevede di applicare filtri) e fare clic su **Visualizza report**.

3.  In una nuova finestra viene aperta la pagina **Report inventario computer** che consente di visualizzare tutti i computer che sono stati registrati in Intune.

    > [!TIP]
    > Fare clic su un'intestazione di colonna nel report per ordinare l'elenco in base al contenuto della colonna.


### <a name="see-also"></a>Vedere anche
[Gestire i PC Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
[Risolvere i problemi di installazione client](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)



<!--HONumber=Nov16_HO1-->


