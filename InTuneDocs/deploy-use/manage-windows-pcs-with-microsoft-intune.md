---
title: Gestire i PC con il software client | Documentazione Microsoft
description: Gestire i PC Windows installando il software client di Intune.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3d2f3a7233ea7a5127baf5a08be1ccb41f717244
ms.openlocfilehash: 4344251ede6d8cc338d84782d224d87fd78d5bd8


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Gestire i PC Windows con il software client per PC di Intune
Invece di [registrare i PC Windows come dispositivi mobili](set-up-windows-device-management-with-microsoft-intune.md), è possibile registrare e gestire i PC Windows installando il software client di Intune.

Intune gestisce i PC Windows tramite criteri con modalità analoghe a quelle degli oggetti Criteri di gruppo di Servizi di dominio Active Directory di Windows Server. Se si gestiscono computer appartenenti a un dominio di Active Directory con Intune, [assicurarsi che i criteri di Intune non siano in conflitto con oggetti Criteri di gruppo](resolve-gpo-and-microsoft-intune-policy-conflicts.md) attivati per l'organizzazione.

Mentre il client software di Intune supporta le [funzionalità di gestione che consentono di proteggere i PC](policies-to-protect-windows-pcs-in-microsoft-intune.md) mediante la gestione degli aggiornamenti software, di Windows Firewall e di Endpoint Protection, ai PC gestiti con il client software di Intune non possono essere assegnati altri criteri di Intune, incluse le impostazioni dei criteri di **Windows** specifiche della gestione dei dispositivi mobili.

> [!NOTE]
> È possibile gestire i dispositivi con Windows 8.1 o versioni successive come PC usando il client di Intune oppure come dispositivi mobili usando la funzionalità di gestione dei dispositivi mobili (MDM). Non è possibile usare entrambi i metodi insieme. Le informazioni in questo argomento riguardano esclusivamente la gestione dei dispositivi come PC eseguendo il client software di Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Requisiti per la gestione del client per PC di Intune

**Hardware**: di seguito sono riportati i requisiti hardware minimi per installare il client Intune:

|Requisito|Altre informazioni|
|---------------|--------------------|
|Rete|Il client richiede che il computer abbia una connessione Internet.|
|Processore e memoria|Consultare i requisiti per il processore e la RAM specifici del sistema operativo del computer.|
|Spazio su disco|200 MB di spazio su disco prima dell'installazione del software client.|

**Software**: di seguito sono elencati i requisiti software per l'installazione del client:

|Requisito|Altre informazioni|
|---------------|--------------------|
|Sistema operativo | Il dispositivo Windows deve eseguire Windows Vista o una versione successiva. Le edizioni Home non sono supportate.|
|Autorizzazioni amministrative|L'account che installa il software client deve avere le autorizzazioni di amministratore locale per il dispositivo specificato.|
|Windows Installer 3.1|Il computer deve avere almeno Windows Installer 3.1.<br /><br />Per visualizzare la versione di Windows Installer in un computer:<br /><br />  Nel PC fare clic con il pulsante destro del mouse su **%windir%\System32\msiexec.exe** e quindi scegliere **Proprietà**.<br /><br />È possibile scaricare la versione più recente di Windows Installer da [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) dal sito Web Microsoft Developer Network.|
|Rimuovere il software client incompatibile|Prima di installare il software client di Intune, è necessario disinstallare dal PC eventuale software client di Configuration Manager, Operations Manager, Operations Management Suite e Service Manager.|

## <a name="computer-management-with-the-intune-computer-client"></a>Gestione di computer con il client computer di Intune
Dopo aver installato il software client di Intune, le funzionalità di gestione includono: 

- [Gestione delle applicazioni](deploy-apps-in-microsoft-intune.md)

- [Monitoraggio in tempo reale ed Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)

- [Gestione delle impostazioni di Windows Firewall](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventario hardware e software, controllo remoto (tramite le richieste di assistenza remota)

- [Impostazioni degli aggiornamenti software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- Report sulle impostazioni di conformità

Alcune opzioni di gestione disponibili per i PC gestiti come dispositivi mobili non sono disponibili per i PC gestiti dal client software, incluse:

-   Cancellazione completa (è disponibile la cancellazione selettiva)

-   Accesso condizionale

-   Criteri di Windows diversi dai criteri **Gestione computer**

  ![Modello di criteri per PC Windows](../media/pc_policy_template.png)

Oltre alle azioni dell'agente client di Intune eseguite localmente nei singoli computer, è anche possibile usare la console di amministrazione di Intune per eseguire altre [attività comuni di gestione dei computer](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) nei PC Windows in cui è installato il client per:

-   Visualizzare le informazioni sull'inventario hardware e software per i computer gestiti

-   Riavviare in remoto un computer

-   Disattivare un computer per disinstallare il software client e rimuoverlo dalla gestione con Intune

-   Collegare gli utenti a computer gestiti specifici

-   Rispondere alle richieste di assistenza remota

L'agente client di Intune viene eseguito in genere in modalità non interattiva in background senza la necessità di interazione da parte dell'utente o di procedure per la risoluzione dei problemi. Se tuttavia fosse necessario risolvere alcuni problemi di gestione dei computer, sono disponibili alcune [risorse a ciò destinate](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).



<!--HONumber=Dec16_HO3-->


