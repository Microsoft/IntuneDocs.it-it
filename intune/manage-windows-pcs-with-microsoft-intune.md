---
title: Gestire i PC con il software client
titlesuffix: Microsoft Intune
description: Gestire i PC Windows installando il software client di Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic-keep
ms.openlocfilehash: 41f4a724a8450584a62629194e1a179372ec4b8e
ms.sourcegitcommit: 116be0eaa44fd5518ff34780d39569224ef4746b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36310556"
---
# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Gestire i PC Windows come computer tramite il client software di Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> È possibile usare Microsoft Intune per gestire i PC Windows [come dispositivi mobili con la soluzione di gestione dei dispositivi mobili (MDM)](windows-enroll.md) o come computer con il software client di Intune come descritto di seguito. Microsoft consiglia tuttavia ai clienti di [usare la soluzione di gestione MDM](windows-enroll.md) laddove possibile.

Intune offre alle organizzazioni una soluzione completa per la gestione dei dispositivi mobili. Intune consente di gestire i PC Windows come dispositivi mobili usando le funzionalità di gestione dei dispositivi moderni integrate nel sistema operativo Windows 10. Per soddisfare le esigenze di gestione dell'organizzazione, Intune consente anche di gestire i PC Windows come computer con il client del software Intune. Questo metodo di gestione usa le funzionalità di gestione dei computer tradizionali nel sistema operativo Windows legacy.

Il client software di Intune è ideale per i PC Windows che eseguono sistemi operativi legacy, come Windows 7, che non possono essere gestiti come dispositivi mobili. Il client software di Intune usa funzionalità di gestione come Criteri di gruppo per gestire i PC dal cloud.

Intune supporta la gestione di PC Windows come computer usando il client software per un massimo di 7.000 PC. Per le distribuzioni di dimensioni maggiori, gestire i PC Windows 10 come dispositivi mobili. Ogni versione di Intune e aggiornamento di Windows 10 include funzionalità di gestione basate sull'architettura di gestione dei dispositivi mobili. È consigliabile passare alla gestione di Windows 10 come dispositivi mobili per l'organizzazione.


> [!NOTE]
> È possibile gestire i dispositivi con Windows 8.1 e versioni successive come PC usando il software client di Intune oppure come dispositivi mobili. Non è possibile usare entrambi i metodi nello stesso dispositivo. Valutare con attenzione lo scenario prima di decidere di gestire i PC con il software client di Intune. Le informazioni in questo argomento riguardano esclusivamente la gestione dei dispositivi come PC con il software client di Intune.

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

## <a name="deploying-the-intune-software-client"></a>Distribuzione del client software di Intune
L'amministratore di Intune può rendere disponibile il client software di Intune agli utenti in diversi modi. Per ulteriori indicazioni, vedere [Installare il client software di Intune nei PC Windows](install-the-windows-pc-client-with-microsoft-intune.md).

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Funzionalità di gestione dei computer con il software client di Intune
Nella maggior parte dei casi i dispositivi vengono registrati con Microsoft Intune che offre un maggior numero di funzionalità. Tuttavia è possibile anche gestire i PC usando il client software di Intune che fornisce le funzionalità seguenti:

-   **[Gestione aggiornamenti software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)**: è possibile mantenere aggiornati i PC e stabilire quando applicare gli aggiornamenti.

-   **[Criteri di Windows Firewall](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)**: questa funzionalità garantisce che in nessun PC usato nell'azienda Windows Firewall sia inattivo o configurato in modo non corretto.

-   **[Protezione antimalware](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)**: Intune include Endpoint Protection, che consente di proteggere i PC dal malware.

-   **[Assistenza remota](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)**: Intune consente agli utenti di contattare il personale tecnico IT, che può fornire assistenza usando la funzionalità Desktop remoto inclusa in Intune (è necessario installare il software TeamViewer).

-   **[Gestione delle licenze software](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)**: è possibile tenere traccia del numero di licenze software disponibili e di quante licenze disponibili sono in uso.
-   **[Distribuzione di app](add-apps-for-windows-pcs-in-microsoft-intune.md)**: è possibile distribuire software nei PC gestiti. Alcune funzionalità di gestione di app non sono disponibili quando si gestiscono PC con il client software.

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Criteri e distribuzione di app per il software client Intune

Il client software di Intune supporta [funzionalità di gestione per la protezione dei PC](policies-to-protect-windows-pcs-in-microsoft-intune.md) mediante la gestione degli aggiornamenti software, Windows Firewall ed Endpoint Protection. Tuttavia ai PC gestiti con il client software di Intune non possono essere assegnati altri criteri di Intune, incluse le impostazioni dei criteri di **Windows** specifiche per la gestione dei dispositivi mobili.

Quando si usa il software client di Intune per gestire i PC Windows, è possibile usare solo i criteri visualizzati nella sezione **Gestione computer**.

Intune gestisce PC Windows tramite criteri in modo analogo a Oggetti Criteri di gruppo di Active Directory Domain Services (AD DS) di Windows Server. Se si gestiscono computer appartenenti a un dominio di Active Directory con Intune, [assicurarsi che i criteri di Intune non siano in conflitto con altri oggetti Criteri di gruppo](resolve-gpo-and-microsoft-intune-policy-conflicts.md) usati nell'organizzazione. Per altre informazioni, vedere [Criteri di gruppo per principianti](https://technet.microsoft.com/library/hh147307.aspx).

  ![Selezionare il modello per nuovi criteri relativi ai PC Windows](media/select-template-for-pc-policy.png)

Quando si distribuiscono le app è possibile usare il programma di installazione di Windows con estensione exe e msi.

  ![Selezionare la piattaforma e il percorso per i file del software client del PC](media/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Attività comuni per i PC Windows

È possibile usare la console di amministrazione di Intune per eseguire altre attività comuni di gestione dei computer nei PC Windows in cui è installato il client:
- [Use policies to simplify PC management](use-policies-to-simplify-windows-pc-management.md) (Usare i criteri per semplificare la gestione dei PC): descrive i criteri **Gestione computer** di Intune ed elenca le impostazioni per Microsoft Intune Center.

- [View hardware and software inventory for Windows PCs](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) (Visualizzare l'inventario hardware e software per PC Windows): spiega come creare un report contenente informazioni sulle funzionalità hardware dei PC e sulle applicazioni software in essi installate. Spiega inoltre come aggiornare l'inventario dei PC.
- [Retire a Windows PC](retire-a-windows-pc-with-microsoft-intune.md) (Ritirare un PC Windows): riporta i passaggi da eseguire per ritirare un PC Windows e descrive cosa succede dopo il ritiro.
- [Gestire il collegamento utente-dispositivo per PC Windows](manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md): spiega quando e come è necessario collegare un utente a un PC prima di distribuire software all'utente in questione.
- [Request and provide remote assistance for Windows PCs](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) (Richiedere e fornire assistenza remota per i PC Windows): descrive in che modo gli utenti di PC Intune ottengono assistenza remota, indica i prerequisiti e descrive l'installazione di TeamViewer.

Per altre informazioni sulle attività di gestione dei computer, vedere [Attività comuni di gestione di PC Windows con il software client di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Limitazioni della gestione con il software client di Intune

Alcune opzioni di gestione usate per gestire i PC come dispositivi mobili non possono essere usate per i PC gestiti con il software client di Intune:

-   Cancellazione completa (è disponibile la cancellazione selettiva)
-   Accesso condizionale

Nella console di amministrazione di Intune alcune sezioni, ad esempio **Aggiornamenti**, **Protezione** e **Licenze**, vengono visualizzate solo se i dispositivi sono stati registrati usando il software client di Intune.

  ![Elementi della console di amministrazione visualizzati solo per il client PC](media/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>Informazioni sulla risoluzione dei problemi

Il software client di Intune viene in genere eseguito in modalità non interattiva in background, senza richiedere interazione da parte dell'utente o procedure per la risoluzione dei problemi. Se è necessario risolvere i problemi di gestione dei PC, è possibile controllare i log. Il software client di Intune e i log corrispondenti vengono installati nella directory %Program Files%\Microsoft\OnlineManagement.

È anche possibile vedere [Che cos'è la registrazione dei dispositivi?](device-enrollment.md) per altre informazioni sulla registrazione di dispositivi con Microsoft Intune.
