---
title: Installare il software client per PC | Microsoft Intune
description: Usare questa guida per far gestire i computer Windows dal software client di Microsoft Intune.
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 13fa09a2b029818467062a5c589292c5f0bd0a58


---

# Installare il client software di Intune nei PC Windows
È possibile registrare i PC Windows installando il software client di Intune. Il software client di Intune può essere installato nei modi seguenti:

- Installazione manuale
- Installazione con Criteri di gruppo
- Inclusione in un'immagine disco
- Installazione da parte dell'utente

## Download del software client di Intune

Tutti i metodi, ad eccezione di quello in cui l'utente installa il software client di Intune autonomamente, rendono necessario il download del software per poterlo distribuire.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Amministrazione** &gt; **Download software client**

  ![Scaricare il client PC Intune](../media/pc-sa-client-download.png)

2.  Nella pagina **Download software client** fare clic su **Scarica software client** e salvare il pacchetto **Microsoft_Intune_Setup.zip** che contiene il software in un percorso sicuro nella rete.

    > [!NOTE]
    > Il pacchetto di installazione del software client di Intune contiene le informazioni sull'account dell'utente. Se utenti non autorizzati ottengono l'accesso al pacchetto di installazione, tali utenti possono registrare i computer nell'account rappresentato dal certificato incorporato.

3.  Estrarre il contenuto del pacchetto di installazione in un percorso sicuro nella rete locale.

    > [!IMPORTANT]
    > Non rinominare o rimuovere il file **ACCOUNTCERT** estratto, altrimenti l'installazione del software client non riuscirà.

## Distribuzione manuale

1.  Nel computer individuare la cartella che contiene i file di installazione del software client, quindi eseguire **Microsoft_Intune_Setup.exe** per installare il software client.

    > [!NOTE]
    > Lo stato dell'installazione viene visualizzato quando si passa il mouse sull'icona nella barra delle applicazioni del computer client.

## Distribuzione con Criteri di gruppo

1.  Nella cartella che contiene i file **Microsoft_Intune_Setup.exe** e **MicrosoftIntune.accountcert** eseguire questo comando per estrarre i programmi di installazione basati su Windows Installer per i computer a 32 e 64 bit:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Copiare i file **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** e **MicrosoftIntune.accountcert** in un percorso di rete a cui possono avere accesso tutti i computer in cui verrà installato il software client.

    > [!IMPORTANT]
    > Non separare o rinominare i file altrimenti l'installazione del software client non riuscirà.

3.  Usare Criteri di gruppo per distribuire il software nei computer della rete.

    Per altre informazioni sull'utilizzo di Criteri di gruppo per distribuire automaticamente il software, vedere la documentazione di Windows Server.

## Installazione come parte di un'immagine
Il software client di Intune può essere distribuito nei computer come parte di un'immagine del sistema operativo usando la seguente procedura di esempio come base:

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
    > Lo script **SetupComplete.cmd** consente a Installazione di Windows di apportare modifiche al sistema prima che un utente vi effettui l'accesso. Al termine dell'esecuzione del programma Installazione di Windows, l'argomento della riga di comando **/PrepareEnroll** predispone un computer di destinazione per la registrazione automatica in Intune.

4.  Inserire **SetupComplete.cmd** nella cartella **%Windir%\Setup\Scripts** del computer di riferimento.

5.  Acquisire un'immagine del computer di riferimento e distribuirla nei computer di destinazione.

Dopo aver riavviato il computer di destinazione una volta eseguito il programma Installazione di Windows, verrà creata la chiave del Registro di sistema **WindowsIntuneEnrollPending** . Il pacchetto di registrazione verificherà se il computer è iscritto. Se il computer è registrato, non verrà intrapresa alcuna azione. Se il computer non è registrato, il pacchetto creerà un'attività di registrazione automatica in Microsoft Intune.

L'attività di registrazione automatica, eseguita al successivo orario pianificato, verifica l'esistenza del valore del Registro di sistema **WindowsIntuneEnrollPending** e tenta di registrare il PC di destinazione in Intune. Se il tentativo non riesce a causa di un errore, la registrazione verrà ripetuta al momento della successiva esecuzione dell'attività. I tentativi continuano per un periodo di un mese.

L'attività di registrazione automatica, il valore del Registro di sistema **WindowsIntuneEnrollPending** e il certificato dell'account vengono eliminati dal computer di destinazione al completamento della registrazione o dopo un mese.

## Registrazione automatica da parte dell'utente

Gli utenti possono installare il software client di Intune passando a [http://portal.manage.microsoft.com](http://portal..manage.microsoft.com). Se il portale Web rileva che il dispositivo è un PC Windows, verrà chiesto di registrare il PC scaricando il client software di Intune. Dopo il download, gli utenti possono installare il software per la gestione dei PC.

![Portale di Intune che richiede di scaricare il client software di Intune](../media/software-client-download.png)

## Controllare e convalidare la distribuzione del client
Usare una delle seguenti procedure per controllare e convalidare la distribuzione del client.

### Per verificare l'installazione del software client dalla console di amministrazione di Microsoft Intune

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i computer**.

2.  Scorrere l'elenco dei computer per individuare quelli gestiti che comunicano con Intune oppure per cercare un computer gestito specifico, digitando tutto o parte del nome nella casella **Cerca dispositivi**.

3.  Verificare lo stato del computer nel riquadro inferiore della console e risolvere gli eventuali errori.

### Per creare un report di inventario dei computer al fine di visualizzare tutti i computer registrati

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Report** &gt; **Report inventario computer**.

2.  Nella pagina **Crea nuovo report** lasciare i valori predefiniti in tutti i campi (a meno che non si desideri applicare i filtri) e fare clic su **Visualizza report**.

3.  In una nuova finestra viene aperta la pagina **Report inventario computer** che consente di visualizzare tutti i computer che sono stati registrati in Intune.

    > [!TIP]
    > Fare clic su un'intestazione di colonna nel report per ordinare l'elenco in base al contenuto della colonna.


### Vedere anche
[Gestire i PC Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
[Risolvere i problemi di installazione client](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)



<!--HONumber=Sep16_HO4-->


