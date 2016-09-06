---
title: Gestire i PC con il software client | Microsoft Intune
description: Gestire i PC Windows installando il software client di Intune.
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cf471320f122eea7804ff6cd6cad208f8cd5a692
ms.openlocfilehash: f264dc3740ce9b117fcc01c39792904a2dc6e7ab


---

# Gestire i PC Windows con il software client per PC di Intune
Invece di [registrare i PC Windows come dispositivi mobili](set-up-windows-device-management-with-microsoft-intune.md), è possibile registrare e gestire i PC Windows installando il software client di Intune.

Intune gestisce PC Windows tramite criteri in modo analogo a Oggetti Criteri di gruppo di Servizi di dominio Active Directory di Windows Server. Se si gestiscono computer appartenenti a un dominio di Active Directory con Intune, è necessario [assicurarsi che i criteri di Intune non siano in conflitto con Oggetti Criteri di gruppo](resolve-gpo-and-microsoft-intune-policy-conflicts.md) attivati per l'organizzazione.

Mentre il client software di Intune supporta le [funzionalità di gestione che consentono di proteggere i PC](policies-to-protect-windows-pcs-in-microsoft-intune.md) mediante la gestione degli aggiornamenti software, di Windows Firewall e di Endpoint Protection, i PC gestiti con il client di Intune non possono essere assegnati ad altri criteri di Intune, incluse le impostazioni dei criteri di **Windows** specifiche della gestione dei dispositivi mobili.

> [!NOTE]
> I dispositivi che eseguono Windows 8.1 o versioni successive possono essere gestiti con il client di Intune o possono essere registrati come dispositivi mobili. Le informazioni riportate di seguito si applicano ai computer che eseguono il client di Intune. L'installazione del client per PC di Intune e la registrazione del dispositivo Windows per la gestione di dispositivi mobili non sono supportate.

## Requisiti per la gestione del client per PC di Intune

**Hardware**: di seguito sono riportati i requisiti hardware minimi per installare il client Intune:

|Requisito|Altre informazioni|
|---------------|--------------------|
|Rete|Il client richiede che il computer abbia una connessione Internet.|
|Processore e memoria|Consultare i requisiti per il processore e la RAM specifici del sistema operativo del computer.|
|Spazio su disco|200 MB di spazio su disco prima dell'installazione del software client.|

**Software**: di seguito sono elencati i requisiti software per l'installazione del client:

|Requisito|Altre informazioni|
|---------------|--------------------|
|Sistema operativo | Il dispositivo Windows deve eseguire Windows 7 o una versione successiva. |
|Autorizzazioni amministrative|L'account che installa il software client deve avere le autorizzazioni di amministratore locale per il dispositivo specificato.|
|Windows Installer 3.1|Il computer deve avere almeno Windows Installer 3.1.<br /><br />Per visualizzare la versione di Windows Installer in un computer:<br /><br />- Nel computer fare clic con il pulsante destro del mouse su **%windir%\System32\msiexec.exe**, quindi scegliere **Proprietà**.<br /><br />È possibile scaricare la versione più recente di Windows Installer da [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) dal sito Web Microsoft Developer Network.|
|Rimuovere il software client incompatibile|Prima di installare il software client di Intune, è necessario disinstallare dal PC eventuale software client di Gestione configurazione o di System Management Server.|

## Installare il client computer di Intune
Il software client di Intune può essere installato in uno dei modi seguenti:

-  È possibile [distribuire manualmente il software client di Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software). In questo tipo di distribuzione, un amministratore scarica il software client di Intune e lo installa manualmente in ogni computer.

  Per scaricare il software client di Intune, aprire la [console di amministrazione di Intune](https://manage.microsoft.com), scegliere **Amministrazione** > **Download software client** e quindi fare clic su **Scarica software client**.

-  Usare gli stessi file scaricati per installare manualmente il software client di Intune e [distribuirlo in computer appartenenti a un dominio tramite oggetti Criteri di gruppo di Active Directory](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy).

-  Distribuire il software client di Intune nei computer durante la [distribuzione di un sistema operativo](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image).

-  Inviare istruzioni agli utenti con l'URL per il portale aziendale di Intune, [https://portal.manage.microsoft.com](http://go.microsoft.com/fwlink/?LinkId=825632). Quando gli utenti aprono il portale aziendale, viene loro richiesto di registrare i propri PC scaricando ed eseguendo il software client di Intune.

## Gestione di computer con il client computer di Intune
Dopo l'installazione, il software client di Intune consente di usare diverse funzionalità di gestione dei computer tra cui: [gestione delle applicazioni](deploy-apps-in-microsoft-intune.md), Endpoint Protection, inventario hardware e software, controllo remoto (tramite richieste di assistenza remota), aggiornamenti software e creazione di report per le impostazioni di conformità.

Diverse attività di gestione dei computer abilitata dal client computer vengono gestite tramite i criteri di Intune, ad esempio:

-   Configurazione delle [impostazioni di Windows Firewall](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) nei computer gestiti.

-   Configurazione delle [impostazioni di aggiornamento software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) per i computer gestiti per la ricerca e il download degli aggiornamenti software richiesti.

-   Protezione dei computer gestiti da minacce potenziali e software dannoso tramite la gestione del [monitoraggio in tempo reale e di Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).

![Modello di criteri per PC Windows](../media/pc_policy_template.png)

Oltre alle azioni dell'agente client di Intune eseguite localmente nei singoli computer, è anche possibile usare la console di amministrazione di Intune per eseguire altre [attività comuni di gestione dei computer](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) nei PC Windows in cui è installato il client per:

-   Visualizzare le informazioni sull'inventario hardware e software per i computer gestiti

-   Riavviare in remoto un computer

-   Disattivare un computer per disinstallare il software client e rimuoverlo dalla gestione con Intune

-   Collegare gli utenti a computer gestiti specifici

-   Rispondere alle richieste di assistenza remota

L'agente client di Intune viene eseguito in genere in modalità non interattiva in background senza la necessità di interazione da parte dell'utente o di procedure per la risoluzione dei problemi. Se tuttavia fosse necessario risolvere alcuni problemi di gestione dei computer, sono disponibili alcune [risorse a ciò destinate](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).



<!--HONumber=Aug16_HO4-->


