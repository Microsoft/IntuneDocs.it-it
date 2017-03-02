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
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 2e7062169ceb855f03a13d1afb4b4de41af593ac
ms.openlocfilehash: 10ba007095182c9cb07710656ba5f275e254d92e
ms.lasthandoff: 02/15/2017


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Gestire i PC Windows con il software client per PC di Intune
La [registrazione dei PC Windows come dispositivi mobili](set-up-windows-device-management-with-microsoft-intune.md) è il metodo preferito di registrazione dei PC Windows in Intune; in alternativa è possibile scegliere di registrare e gestire i PC Windows installando il software client di Intune, come descritto in questo argomento.

Intune gestisce i PC Windows tramite criteri con modalità analoghe a quelle degli oggetti Criteri di gruppo di Servizi di dominio Active Directory di Windows Server. Se si gestiscono computer appartenenti a un dominio di Active Directory con Intune, [assicurarsi che i criteri di Intune non siano in conflitto con oggetti Criteri di gruppo](resolve-gpo-and-microsoft-intune-policy-conflicts.md) attivati per l'organizzazione. Per altre informazioni, vedere [Oggetti Criteri di gruppo](https://technet.microsoft.com/library/hh147307.aspx).

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Criteri e distribuzione di app per il software client Intune

Il client software di Intune supporta [funzionalità di gestione per la protezione dei PC](policies-to-protect-windows-pcs-in-microsoft-intune.md) mediante la gestione degli aggiornamenti software, Windows Firewall ed Endpoint Protection. Tuttavia ai PC gestiti con il client software di Intune non possono essere assegnati altri criteri di Intune, incluse le impostazioni dei criteri di **Windows** specifiche per la gestione dei dispositivi mobili. 

Quando si usa il software client di Intune per gestire i PC Windows, è possibile usare solo i criteri visualizzati nella sezione **Gestione computer**.

  ![Selezionare il modello per nuovi criteri relativi ai PC Windows](../media/select-template-for-pc-policy.png)

Per descrizioni dettagliate dei criteri che è possibile impostare, vedere:

- [Usare i criteri per proteggere i PC Windows che eseguono il software client di Intune](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)
- [Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)
- [Proteggere i PC Windows con criteri di Windows Firewall in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)
- [Proteggere i PC Windows con Endpoint Protection per Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

Quando si distribuiscono le app è possibile anche usare il programma di installazione di Windows con estensione exe e msi.

  ![Selezionare la piattaforma e il percorso per i file del software client del PC](../media/select-platform-of-software-files-for-pc-agent.png)

> [!NOTE]
> È possibile gestire i dispositivi con Windows 8.1 o versioni successive come PC usando il software client di Intune oppure come dispositivi mobili usando la funzionalità di gestione dei dispositivi mobili (MDM). Non è possibile usare contemporaneamente entrambi i metodi. Valutare attentamente la decisione prima di scegliere di gestire i PC usando il software client di Intune. Le informazioni in questo argomento riguardano esclusivamente la gestione dei dispositivi come PC con il software client di Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Requisiti per la gestione del client per PC di Intune

**Hardware**: di seguito sono riportati i requisiti hardware minimi per l'installazione del software client di Intune:

|Requisito|Altre informazioni|
|---------------|--------------------|
|Rete|Il client richiede che il computer abbia una connessione Internet.|
|Processore e memoria|Consultare i requisiti per il processore e la RAM specifici del sistema operativo del computer.|
|Spazio su disco|200 MB di spazio su disco prima dell'installazione del software client.|

**Software**: di seguito sono elencati i requisiti software per l'installazione del software client:

|Requisito|Altre informazioni|
|---------------|--------------------|
|Sistema operativo | Il dispositivo Windows deve eseguire Windows Vista o una versione successiva. </br></br>**Le edizioni Home non sono supportate**|
|Autorizzazioni amministrative|L'account che installa il software client deve avere le autorizzazioni di amministratore locale per il dispositivo specificato.|
|Windows Installer 3.1|Il computer deve avere almeno Windows Installer 3.1.<br /><br />Per visualizzare la versione di Windows Installer in un computer:<br /><br />  Nel PC fare clic con il pulsante destro del mouse su **%windir%\System32\msiexec.exe** e quindi scegliere **Proprietà**.<br /><br />È possibile scaricare la versione più recente di Windows Installer da [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) dal sito Web Microsoft Developer Network.|
|Rimuovere il software client incompatibile|Prima di installare il software client di Intune, è necessario disinstallare dal PC eventuale software client di Configuration Manager, Operations Manager, Operations Management Suite e Service Manager.|

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Funzionalità di gestione dei computer con il software client di Intune

Dopo aver installato il software client di Intune, le funzionalità di gestione includono: 

- [Gestione delle applicazioni](deploy-apps-in-microsoft-intune.md)

- [Monitoraggio in tempo reale ed Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) - Endpoint Protection equivale a Windows Defender. Endpoint Protection si applica a Windows 7 e Windows 8. Per Windows 10 e versioni successive, il nome del prodotto è diventato Windows Defender.

- [Gestione delle impostazioni di Windows Firewall](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventario hardware e software, controllo remoto (tramite le richieste di assistenza remota)

- [Impostazioni degli aggiornamenti software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- Report sulle impostazioni di conformità

Nella console di amministrazione di Intune alcune sezioni, ad esempio "Aggiornamenti", "Protezione" e "Licenze", vengono visualizzate solo se i dispositivi sono stati registrati usando il client software di Intune.

  ![Elementi della console di amministrazione visualizzati solo per il client PC](../media/admin-console-settings-only-for-pc-agent.png)

È possibile usare la console di amministrazione di Intune anche per eseguire altre attività comuni di gestione dei computer nei PC Windows in cui è installato il client:

-   Visualizzare le informazioni sull'inventario hardware e software per i computer gestiti
-   Riavviare in remoto un computer
-   Disattivare un computer per disinstallare il software client e rimuoverlo dalla gestione con Intune
-   Collegare gli utenti a computer gestiti specifici
-   Rispondere alle richieste di assistenza remota

Per altre informazioni sulle attività di gestione dei computer, vedere [Attività comuni di gestione di PC Windows con il software client di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Limitazioni della gestione con il software client di Intune

Alcune opzioni di gestione usate per gestire i PC come dispositivi mobili non possono essere usate per i PC gestiti con il software client di Intune:

-   Cancellazione completa (è disponibile la cancellazione selettiva)

-   Accesso condizionale

## <a name="help-with-troubleshooting"></a>Informazioni sulla risoluzione dei problemi

Il software client di Intune viene in genere eseguito in modalità non interattiva in background, senza richiedere interazione da parte dell'utente o procedure per la risoluzione dei problemi. Se è necessario risolvere i problemi di gestione dei PC, è possibile controllare i log. Il software client di Intune e i log corrispondenti vengono installati nella directory %Program Files%\Microsoft\OnlineManagement.

È possibile anche esaminare [Risolvere i problemi di installazione client in Microsoft Intune](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune) per verificare la presenza di eventuali problemi e le risoluzioni o le soluzioni alternative possibili.

