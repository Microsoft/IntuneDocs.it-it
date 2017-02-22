---
title: Gestire i PC con il software client | Documentazione Microsoft
description: Gestire i PC Windows installando il software client di Intune.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 45c32cf08e4d6fd570af287ed64411edc9d9b394
ms.openlocfilehash: 21e83b68bb68384a8916db8d7f779cddde18a8a6


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Gestire i PC Windows con il software client per PC di Intune
Invece di [registrare i PC Windows come dispositivi mobili](set-up-windows-device-management-with-microsoft-intune.md), è possibile registrare e gestire i PC Windows installando il software client di Intune.

Intune gestisce i PC Windows tramite criteri con modalità analoghe a quelle degli oggetti Criteri di gruppo di Servizi di dominio Active Directory di Windows Server. Se si gestiscono computer appartenenti a un dominio di Active Directory con Intune, [assicurarsi che i criteri di Intune non siano in conflitto con oggetti Criteri di gruppo](resolve-gpo-and-microsoft-intune-policy-conflicts.md) attivati per l'organizzazione. Per altre informazioni, vedere [Oggetti Criteri di gruppo](https://technet.microsoft.com/library/hh147307.aspx).

Mentre il client software di Intune supporta le [funzionalità di gestione che consentono di proteggere i PC](policies-to-protect-windows-pcs-in-microsoft-intune.md) mediante la gestione degli aggiornamenti software, di Windows Firewall e di Endpoint Protection, ai PC gestiti con il client software di Intune non possono essere assegnati altri criteri di Intune, incluse le impostazioni dei criteri di **Windows** specifiche della gestione dei dispositivi mobili. 

Quando si usa il client del software Intune per gestire i PC Windows, è possibile usare solo i criteri visualizzati nella sezione**Gestione computer**.

  ![Selezionare il modello per nuovi criteri relativi ai PC Windows](../media/select-template-for-pc-policy.png)

Per descrizioni dettagliate dei criteri che è possibile impostare, vedere:

- [Usare i criteri per proteggere i PC Windows che eseguono il software client di Intune](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)
- [Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)
- [Proteggere i PC Windows con criteri di Windows Firewall in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)
- [Proteggere i PC Windows con Endpoint Protection per Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

Quando si distribuiscono le app è possibile anche usare il programma di installazione di Windows con estensione exe e msi.

  ![Selezionare la piattaforma e il percorso per i file del software client del PC](../media/select-platform-of-software-files-for-pc-agent.png)

> [!NOTE]
> È possibile gestire i dispositivi con Windows 8.1 o versioni successive come PC usando il client di Intune oppure come dispositivi mobili usando la funzionalità di gestione dei dispositivi mobili (MDM). Non è possibile usare contemporaneamente entrambi i metodi, quindi valutare attentamente la decisione prima di gestire i PC usando il client software di Intune. Le informazioni in questo argomento riguardano esclusivamente la gestione dei dispositivi come PC eseguendo il client software di Intune.

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
|Sistema operativo | Il dispositivo Windows deve eseguire Windows Vista o una versione successiva. </br></br>**Le edizioni Home non sono supportate**|
|Autorizzazioni amministrative|L'account che installa il software client deve avere le autorizzazioni di amministratore locale per il dispositivo specificato.|
|Windows Installer 3.1|Il computer deve avere almeno Windows Installer 3.1.<br /><br />Per visualizzare la versione di Windows Installer in un computer:<br /><br />  Nel PC fare clic con il pulsante destro del mouse su **%windir%\System32\msiexec.exe** e quindi scegliere **Proprietà**.<br /><br />È possibile scaricare la versione più recente di Windows Installer da [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) dal sito Web Microsoft Developer Network.|
|Rimuovere il software client incompatibile|Prima di installare il software client di Intune, è necessario disinstallare dal PC eventuale software client di Configuration Manager, Operations Manager, Operations Management Suite e Service Manager.|

## <a name="computer-management-capabilities-with-the-intune-software-client"></a>Funzionalità di gestione dei computer con il client software di Intune

Dopo aver installato il software client di Intune, le funzionalità di gestione includono: 

- [Gestione delle applicazioni](deploy-apps-in-microsoft-intune.md)

- [Monitoraggio in tempo reale ed Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)

 > [!NOTE]
 > Endpoint Protection equivale a Windows Defender. Endpoint Protection si applica a Windows 7 e Windows 8. Per Windows 10 e versioni successive, il nome del prodotto è diventato Windows Defender.

- [Gestione delle impostazioni di Windows Firewall](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventario hardware e software, controllo remoto (tramite le richieste di assistenza remota)

- [Impostazioni degli aggiornamenti software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- Report sulle impostazioni di conformità

Nella console di amministrazione di Intune alcune sezioni, ad esempio "Aggiornamenti", "Protezione" e "Licenze", vengono visualizzate solo se i dispositivi sono stati registrati usando il client software di Intune.

  ![Elementi della console di amministrazione visualizzati solo per il client PC](../media/admin-console-settings-only-for-pc-agent.png)

È possibile anche usare la console di amministrazione di Intune per eseguire altre [attività comuni di gestione dei computer](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) nei PC Windows in cui è installato il client:

-   Visualizzare le informazioni sull'inventario hardware e software per i computer gestiti

-   Riavviare in remoto un computer

-   Disattivare un computer per disinstallare il client software e rimuoverlo dalla gestione con Intune

-   Collegare gli utenti a computer gestiti specifici

-   Rispondere alle richieste di assistenza remota

## <a name="management-limitations-of-the-intune-software-client"></a>Limitazioni alla gestione del client software di Intune

Alcune opzioni di gestione che possono essere usate per gestire i PC come dispositivi mobili, non possono essere usate per i PC gestiti con il client software di Intune:

-   Cancellazione completa (è disponibile la cancellazione selettiva)

-   Accesso condizionale

## <a name="help-with-troubleshooting"></a>Informazioni sulla risoluzione dei problemi

L'agente client di Intune viene eseguito in genere in modalità non interattiva in background senza la necessità di interazione da parte dell'utente o di procedure per la risoluzione dei problemi. Se è necessario risolvere i problemi di gestione dei PC, è possibile controllare i log. Il client software di Intune e i log corrispondenti vengono installati nella directory %Program Files%\Microsoft\OnlineManagement.

È possibile anche esaminare [Risolvere i problemi di installazione client in Microsoft Intune](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune) per verificare la presenza di eventuali problemi e le risoluzioni o le soluzioni alternative possibili.



<!--HONumber=Feb17_HO2-->


