---
title: Risolvere i problemi di installazione del client
description: Risolvere i problemi comuni di installazione client.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 27f9d3172750d4db5b96d0477ecaeeafa1e59ed2
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="troubleshoot-client-setup-in-microsoft-intune"></a>Risolvere i problemi di installazione client in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare le seguenti informazioni per risolvere i problemi di installazione del client più frequenti. Se queste informazioni non consentono di risolvere il problema, vedere [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md) per trovare altri modi per ottenere assistenza.

## <a name="client-installation-fails"></a>L'istallazione del client ha esito negativo

-   Se nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) non vengono visualizzati avvisi relativi alla distribuzione del software client per il computer, verificare la connettività Internet e la configurazione proxy del computer e assicurarsi che il computer sia in grado di comunicare con l'URL del servizio, [https://manage.microsoft.com](https://manage.microsoft.com/). Quindi, riprovare l'installazione del software client.

-   È possibile attivare l'invio di un messaggio di posta elettronica a destinatari selezionati quando viene emesso un avviso di errore della distribuzione del software client configurando una regola di notifica nell'area di lavoro **Amministrazione** . Per altre informazioni, vedere [Ricevere notifiche tramite gli avvisi di Microsoft Intune](/intune-classic/deploy-use/get-notified-by-alerts).

-   Intune visualizza l'avviso critico **Errore distribuzione software client** se la distribuzione del software client ha esito negativo. L'avviso viene visualizzato nella pagina **Panoramica sistema** e nelle pagine **Avvisi** della [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/). Ecco come controllare gli avvisi:

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Avvisi** &gt; **Panoramica**.

2.  Nella pagina **Panoramica avvisi** , è possibile rivedere le seguenti informazioni:

    -   I tre avvisi principali, che possono essere ordinati in base a data, categoria o gravità

    -   Il numero totale di avvisi attivi

3.  Fare clic su **Tutti gli avvisi** per visualizzare le informazioni seguenti nella pagina **Avvisi** . Gli avvisi critici vengono visualizzati per primi:

    -   **Nome** : il nome del tipo di avviso che ha generato l'avviso.

    -   **Origine** : un collegamento all'origine dell'avviso.  Se la soglia di visualizzazione del tipo di avviso è impostata su **Tutto**, in questo collegamento verrà visualizzato un unico dispositivo interessato.  Se per la soglia di visualizzazione del tipo di avviso è stato impostato un valore, in questo collegamento verrà visualizzato l'elenco di tutti i dispositivi che sono interessati dall'avviso.

    -   **Ultimo aggiornamento** : indica l'ora dell'ultima modifica apportata all'avviso. Se un avviso è chiuso, viene visualizzata l'ora della chiusura.

    -   **Gravità** : indica la gravità dell'avviso

## <a name="computer-enrollment-package-doesnt-download"></a>Il download del pacchetto di registrazione per il computer ha esito negativo
**Problema:** durante il tentativo di registrazione di un computer si verifica quanto segue:
-  Il download del pacchetto di registrazione ha esito negativo
-  La finestra di dialogo del download viene visualizzata ma si verifica il timeout

**Risoluzione:** nel browser in uso per il download, per il periodo di esecuzione del download, verificare che siano abilitati i download e che i file crittografati possono essere salvati sul disco locale.

## <a name="client-installation-hangs-with-error-code-0x80040154"></a>L'installazione del client si blocca e visualizza il codice di errore 0x80040154
**Problema:**

-  L'installazione del client si blocca durante la registrazione

-  Impossibile registrare il dispositivo

-  Errore 0x80040154 in WindowsUpdate.log

L'errore potrebbe dipendere dall'assenza di aggiornamenti software critici sul PC.

**Soluzione:** Verificare che i criteri di aggiornamento del software consentano di installare gli aggiornamenti critici, come descritto in [Keep Windows PCs up to date with software updates in Microsoft Intune](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune) (Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune)


## <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Errori relativi a criteri di Microsoft Intune in policyplatform.log
Per i dispositivi Windows non MDM, gli errori dei criteri nel file policyplatform.log potrebbero derivare da impostazioni non predefinite nel Controllo dell'account utente di Windows sul dispositivo. Alcune impostazioni non predefinite del Controllo dell'account utente possono influire sulle installazioni client di Microsoft Intune e sull'esecuzione dei criteri.

### <a name="to-resolve-uac-issues"></a>Per risolvere i problemi relativi al Controllo dell'account utente

1.  Ritirare il computer come descritto in [Retire devices from Microsoft Intune management](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management) (Ritirare dispositivi dalla gestione di Microsoft Intune).

2.  Attendere 20 minuti che il software client venga rimosso.

    > [!NOTE]
    > Non provare a rimuovere il client da Programmi e funzionalità.

3.  Nel menu Start digitare **Controllo account utente** per aprire le impostazioni di Controllo dell'account utente.

4.  Spostare il dispositivo di scorrimento di notifica sull'impostazione predefinita.

## <a name="what-to-do-if-the-client-will-not-uninstall-from-the-microsoft-intune-administrator-console"></a>Cosa fare se il client non viene disinstallato dalla console di amministrazione di Microsoft Intune

### <a name="to-remove-the-client-software-by-using-the-microsoft-intune-command-line-tool"></a>Per rimuovere il software client usando lo strumento da riga di comando di Microsoft Intune

1.  Aprire un prompt dei comandi in modalità amministratore.

2.  Passare alla cartella *%programfiles%\Microsoft\OnlineManagement\Common*

3.  Eseguire il comando seguente: ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## <a name="client-installation-error-codes"></a>Codici di errore dell'installazione client
Nella tabella riportata di seguito vengono descritti i codici di errore visualizzati in **Avvisi** in caso di problemi di installazione del software client. Sono inclusi suggerimenti per la risoluzione del problema rappresentato da ciascun codice errore.

|Codice errore|Possibile problema|Soluzione suggerita|
|--------------|--------------------|------------------------|
|**0x80CF0437**|L'orologio del computer client non è impostato sull'ora corretta.|Assicurarsi che l'orologio e il fuso orario nel computer client siano impostati sull'ora e sul fuso orario corretti.|
|**0x80240438**, **0x80CF0438**, **0x80CF401B**|Impossibile connettersi al servizio Intune. Verificare le impostazioni proxy del client.|Verificare che la configurazione del proxy nel computer client sia supportata da Intune e che il computer client disponga di accesso a Internet. Per altre informazioni sulle configurazioni proxy supportate, vedere [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) (Proteggere i PC Windows con Endpoint Protection per Microsoft Intune).|
|**0x80CF402C**|Impossibile connettersi al servizio Intune. Verificare la connettività di rete.|Verificare che il computer disponga di connettività di rete. Controllare che il cavo di rete sia collegato o che la rete wireless sia operativa.|
|**0x80240438, 0x80CF0438**|Non sono configurate impostazioni proxy in Internet Explorer e nel sistema locale.|Controllare le impostazioni proxy del client e verificare che la configurazione proxy nel computer client sia supportata da Intune. Verificare anche che il computer client disponga dell'accesso a Internet. Per altre informazioni sulle configurazioni proxy supportate, vedere [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) (Proteggere i PC Windows con Endpoint Protection per Microsoft Intune).|
|**0x80043001**|Il pacchetto di registrazione non è aggiornato.|Scaricare e installare il pacchetto del software client più recente dall'area di lavoro **Amministrazione** . Per le istruzioni, vedere l'argomento [Installare il client PC Windows con Microsoft Intune](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune).|
|**0x80043004**|Sottoscrizione inesistente o disabilitata.|Verificare che l'account e la sottoscrizione a Intune siano ancora attivi. Per visualizzare le impostazioni dell'account, accedere al proprio account nell'[interfaccia di amministrazione di Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043002**|L'account è in modalità di manutenzione.|Quando l'account è in modalità di manutenzione, non è possibile registrare nuovi computer client. Per visualizzare le impostazioni dell'account, accedere al proprio account nell'[interfaccia di amministrazione di Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043003**|L'account è stato eliminato.|Verificare che l'account e la sottoscrizione a Intune siano ancora attivi. Per visualizzare le impostazioni dell'account, accedere al proprio account.|
|**0x80043005**|Il computer client è stato rimosso.|Attendere alcune ore, rimuovere le versioni precedenti del software client dal computer, quindi riprovare a installare il software client. Per altre informazioni, vedere la sezione **Cosa fare se il client non viene disinstallato dalla console di amministrazione di Microsoft Intune** precedente.|
|**0x80043006**|È stato raggiunto il numero massimo di postazioni consentito per l'account.|L'organizzazione deve acquistare ulteriori postazioni prima che sia possibile registrare più computer client nel servizio.|
|**0x80043007**|Impossibile trovare il file del certificato nella stessa cartella del programma di installazione.|Estrarre tutti i file prima di avviare l'installazione. Non rinominare o spostare eventuali file estratti: tutti i file devono trovarsi nella stessa cartella altrimenti l'installazione non riuscirà. Per altre informazioni, vedere [Install the Windows PC client with Microsoft Intune](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune) (Installare il client PC Windows con Microsoft Intune).|
|**0x8024D015**, **0x00240005**, **0x80070BC2**, **0x80070BC9**, **0x80CFD015**|È impossibile installare il software perché un riavvio del computer client è in sospeso.|Riavviare il computer, quindi riprovare a installare il software client.|
|**0x80070032**|Uno o più prerequisiti per l'installazione del software client non sono stati individuati nel computer client.|Assicurarsi che tutti gli aggiornamenti necessari siano installati nel computer client, quindi riprovare a installare il software client. Per altre informazioni sui prerequisiti per l'installazione del software client, vedere [Network infrastructure requirements for Microsoft Intune](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune) (Requisiti dell'infrastruttura di rete per Microsoft Intune).|
|**0x80043008**|Impossibile avviare il servizio Aggiornamenti di Microsoft Online Management.|Contattare il supporto tecnico, come descritto in [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Come ottenere supporto per Microsoft Intune).|
|**0x80043009**|Il computer client è già registrato al servizio.|È necessario ritirare il computer client prima di potersi registrare nuovamente al servizio. Per le istruzioni, vedere [Retire devices from Microsoft Intune management](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management) (Ritirare dispositivi dalla gestione di Microsoft Intune).|
|**0x8004300A**|L'errore (fase 21) si verifica quando il pacchetto di registrazione viene distribuito nell'oggetto Criteri di gruppo per l'installazione nell'ambito utente e non nell'ambito computer. |Assicurarsi che l'oggetto Criteri di gruppo sia assegnato correttamente tramite GPSI nell'ambito computer. Per visualizzare post di forum su questo argomento, vedere questo [forum TechNet](https://social.technet.microsoft.com/Forums/en-US/bb9fa71c-c132-4954-abb0-70be8acbd925/failed-to-install-windows-intune?forum=microsoftintuneprod).|
|**0x8004300B**|Impossibile eseguire l'installazione del software client perché la versione di Windows in esecuzione nel client non è supportata.|Intune non supporta la versione di Windows in esecuzione nel computer client. Per un elenco dei sistemi operativi supportati, vedere [Network infrastructure requirements for Microsoft Intune](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune) (Requisiti dell'infrastruttura di rete per Microsoft Intune).|
|**0xAB2**|Windows Installer non è in grado di accedere al runtime VBScript per un'azione personalizzata.|L'errore è causato da un'azione personalizzata basata sulle librerie a collegamento dinamico (DLL). Per la risoluzione dei problemi relativi alle DLL potrebbe essere necessario usare gli strumenti descritti in [Supporto tecnico Microsoft KB198038: Strumenti utili per pacchetto e problemi di distribuzione](http://go.microsoft.com/fwlink/?LinkID=234255).|
|**0x8004300f**|Non è possibile installare il software perché il client System Center Configuration Manager è già installato.|Rimuovere il client Configuration Manager, quindi ripetere l'installazione del software client.|
|**0x80043010**|Impossibile installare il software poiché il client Open Mobile Alliance Device Management (OMADM) è già installato.|Annullare la registrazione del client OMADM, quindi riprovare a installare il software del client.|
Se i problemi di installazione persistono, contattare il supporto tecnico, come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md). È necessario avere a disposizione il log di registrazione del computer client (disponibile in % *programfiles*% \Microsoft\OnlineManagement\Logs\Enrollment.log e in %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log), oltre al log di Windows Update (%*windir*%\windowsupdate.log) per mostrarli ai tecnici del supporto.

## <a name="what-to-do-if-endpoint-protection-is-not-uninstalled-when-you-uninstall-the-client"></a>Cosa fare se Endpoint Protection non viene disinstallato quando si disinstalla il client

A volte, l'agente di protezione host (Endpoint Protection) può rimanere dopo aver eseguito i comandi precedenti. In questo caso, eseguire questo comando da un prompt dei comandi con privilegi elevati:

    ```
    "C:\Program Files\Managed Defender\Setup.exe" /x /q /s
    ```


### <a name="next-steps"></a>Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
