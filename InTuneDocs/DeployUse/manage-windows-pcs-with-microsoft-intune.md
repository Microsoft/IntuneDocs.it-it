---
title: Gestire i PC Windows con Intune | Microsoft Intune
description: 
keywords: 
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0335b80afa8e330263baad054f0e902f019f75bb
ms.openlocfilehash: 92f4ddde3336fd4cf07c701596f5ebe4c0aeb49f


---

# Gestire i PC Windows con Microsoft Intune
Oltre che per registrare dispositivi, è possibile usare Intune anche per gestire i PC Windows che eseguono sistemi operativi supportati tramite il software client per PC Windows di Intune. I requisiti hardware e software per eseguire il client sono minimi: in pratica è supportato qualsiasi sistema in grado di eseguire Windows 7 o versioni successive.  Il software client può anche essere installato facilmente in computer appartenenti a un dominio (in qualsiasi dominio) o in computer non appartenenti a un dominio.

Intune gestisce PC Windows tramite criteri in modo analogo a Oggetti Criteri di gruppo di Servizi di dominio Active Directory di Windows Server. Se si gestiscono computer appartenenti a un dominio di Active Directory con Intune, è necessario [assicurarsi che i criteri di Intune non siano in conflitto con Oggetti Criteri di gruppo](resolve-gpo-and-microsoft-intune-policy-conflicts.md) attivati per l'organizzazione.

> [!NOTE]
> Microsoft Intune come servizio autonomo offre queste funzionalità per la gestione dei computer. I dispositivi che eseguono Windows 8.1 possono essere gestiti con il client di Intune o possono essere registrati come dispositivi mobili. Le informazioni riportate di seguito si applicano ai computer che eseguono il client di Intune.

## Requisiti per la gestione dei PC con Intune

**Hardware**: di seguito sono riportati i requisiti hardware minimi per installare il client Intune:

|Requisito|Altre informazioni|
|---------------|--------------------|
|Rete|Il client richiede che il computer abbia una connessione Internet.|
|Processore e memoria|Consultare i requisiti per il processore e la RAM specifici del sistema operativo del computer.|
|Spazio su disco|200 MB di spazio su disco prima dell'installazione del software client.|

**Software**: di seguito sono elencati i requisiti software per l'installazione del client:

|Requisito|Altre informazioni|
|---------------|--------------------|
|Autorizzazioni amministrative|L'account che installa il software client deve avere le autorizzazioni di amministratore locale per quel computer.|
|Windows Installer 3.1|Il computer deve avere almeno Windows Installer 3.1.<br /><br />Per visualizzare la versione di Windows Installer in un computer:<br /><br />- Nel computer fare clic con il pulsante destro del mouse su **%windir%\System32\msiexec.exe**, quindi scegliere **Proprietà**.<br /><br />È possibile scaricare la versione più recente di Windows Installer da [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) dal sito Web Microsoft Developer Network.|
|Rimuovere il software client incompatibile|Prima di installare il software client di Intune, è necessario disinstallare dal PC eventuale software client di Gestione configurazione o di System Management Server.|

## Installare il client computer di Intune
Il primo passaggio per la gestione di PC Windows con Intune consiste nell'installare il client. Il software client può essere installato quando il PC viene registrato per la gestione dal servizio Intune in uno dei modi seguenti:

-   È possibile [distribuire manualmente il software client di Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software). In questo tipo di distribuzione, un amministratore scarica il software client di Intune e lo installa manualmente in ogni computer.

    Per scaricare il software client di Intune, aprire la console di amministrazione di Intune e nell'area Download software client scaricare il pacchetto del software client. Una volta installato il software client, Intune installa automaticamente il software aggiuntivo necessario per gestire il computer.

-   È possibile usare gli stessi file scaricati per installare manualmente il client Intune e [distribuirlo in computer appartenenti a un dominio tramite oggetti Criteri di gruppo di Active Directory](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy).

-   [Gli utenti possono registrare automaticamente il proprio computer](install-the-windows-pc-client-with-microsoft-intune.md#how-users-can-self-enroll-their-computers) tramite il portale aziendale di Intune. Ogni computer registrato viene quindi collegato automaticamente all'account utente usato per installare il software client di Intune.

-   È anche possibile, infine, distribuire il software client di Intune nei computer nell'ambito di una [distribuzione del sistema operativo](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image).

## Gestione di computer con il client computer di Intune
Dopo l'installazione, il software client di Intune consente di usare diverse funzionalità di gestione dei computer tra cui: [gestione delle applicazioni](deploy-apps-in-microsoft-intune.md), Endpoint Protection, inventario hardware e software, controllo remoto (tramite richieste di assistenza remota), aggiornamenti software e creazione di report per le impostazioni di conformità.

Diverse attività di gestione dei computer abilitata dal client computer vengono gestite tramite i criteri di Intune, ad esempio:

-   Configurazione delle [impostazioni di Windows Firewall](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) nei computer gestiti.

-   Configurazione delle [impostazioni di aggiornamento software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) per i computer gestiti per la ricerca e il download degli aggiornamenti software richiesti.

-   Protezione dei computer gestiti da minacce potenziali e software dannoso tramite la gestione del [monitoraggio in tempo reale e di Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).

Oltre alle azioni dell'agente client di Intune eseguite localmente nei singoli computer, è anche possibile usare la console di amministrazione di Intune per eseguire altre [attività comuni di gestione dei computer](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) nei PC Windows in cui è installato il client per:

-   Visualizzare le informazioni sull'inventario hardware e software per i computer gestiti

-   Riavviare in remoto un computer

-   Disattivare un computer per disinstallare il software client e rimuoverlo dalla gestione con Intune

-   Collegare gli utenti a computer gestiti specifici

-   Rispondere alle richieste di assistenza remota

L'agente client di Intune viene eseguito in genere in modalità non interattiva in background senza la necessità di interazione da parte dell'utente o di procedure per la risoluzione dei problemi. Se tuttavia fosse necessario risolvere alcuni problemi di gestione dei computer, sono disponibili alcune [risorse a ciò destinate](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).



<!--HONumber=Jun16_HO4-->


