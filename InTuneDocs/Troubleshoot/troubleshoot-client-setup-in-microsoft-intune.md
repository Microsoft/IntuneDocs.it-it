---
title: Risolvere i problemi di installazione client | Microsoft Intune
description: Risolvere i problemi comuni di installazione client.
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c1e215320168c659d5f838355f6350111d6979b0
ms.openlocfilehash: a1f9432e8789a40ec65c64cb958414b97c548f06


---

# Risolvere i problemi di installazione client in Microsoft Intune
Usare le seguenti informazioni per risolvere i problemi di installazione del client più frequenti. Se queste informazioni non consentono di risolvere il problema, vedere [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md) per trovare altri modi per ottenere assistenza.

## L'istallazione del client ha esito negativo

-   Se nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) non vengono visualizzati avvisi relativi alla distribuzione del software client per il computer, verificare la connettività Internet e la configurazione proxy del computer e assicurarsi che il computer sia in grado di comunicare con l'URL del servizio, [https://manage.microsoft.com](https://manage.microsoft.com/). Quindi, riprovare l'installazione del software client.

-   È possibile attivare l'invio di un messaggio di posta elettronica a destinatari selezionati quando viene emesso un avviso di errore della distribuzione del software client configurando una regola di notifica nell'area di lavoro **Amministrazione** . Per altre informazioni, vedere [Ricevere notifiche tramite gli avvisi di Microsoft Intune](/intune/deploy-use/get-notified-by-alerts).

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

## Il download del pacchetto di registrazione per il computer ha esito negativo
**Problema:** durante il tentativo di registrazione di un computer si verifica quanto segue:
-  Il download del pacchetto di registrazione ha esito negativo
-  La finestra di dialogo del download viene visualizzata ma si verifica il timeout

**Risoluzione:** nel browser in uso per il download, per il periodo di esecuzione del download, verificare che siano abilitati i download e che i file crittografati possono essere salvati sul disco locale.

## L'installazione del client si blocca e visualizza il codice di errore 0x80040154
**Problema:**

-  L'installazione del client si blocca durante la registrazione

-  Impossibile registrare il dispositivo

-  Errore 0x80040154 in WindowsUpdate.log

L'errore potrebbe dipendere dall'assenza di aggiornamenti software critici sul PC.

**Soluzione:** Verificare che i criteri di aggiornamento del software consentano di installare gli aggiornamenti critici, come descritto in [Keep Windows PCs up to date with software updates in Microsoft Intune](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune) (Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune)


## Errori relativi a criteri di Microsoft Intune in policyplatform.log
Per i dispositivi Windows non MDM, gli errori dei criteri nel file policyplatform.log potrebbero derivare da impostazioni non predefinite nel Controllo dell'account utente di Windows sul dispositivo. Alcune impostazioni non predefinite del Controllo dell'account utente possono influire sulle installazioni client di Microsoft Intune e sull'esecuzione dei criteri.

### Per risolvere i problemi relativi al Controllo dell'account utente

1.  Ritirare il computer come descritto in [Retire devices from Microsoft Intune management](/intune/deploy-use/retire-devices-from-microsoft-intune-management) (Ritirare dispositivi dalla gestione di Microsoft Intune).

2.  Attendere 20 minuti che il software client venga rimosso.

    > [!NOTE]
    > Non provare a rimuovere il client da Programmi e funzionalità.

3.  Nel menu Start digitare **Controllo account utente** per aprire le impostazioni di Controllo dell'account utente.

4.  Spostare il dispositivo di scorrimento di notifica sull'impostazione predefinita.

## Cosa fare se il client non viene disinstallato dalla console di amministrazione di Microsoft Intune

### Per rimuovere il software client usando lo strumento da riga di comando di Microsoft Intune

1.  Aprire un prompt dei comandi in modalità amministratore.

2.  Passare alla cartella *%programfiles%\Microsoft\OnlineManagement\Common*

3.  Esegui il comando seguente ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## Codici di errore dell'installazione client
Nella tabella riportata di seguito vengono descritti i codici di errore visualizzati in **Avvisi** in caso di problemi di installazione del software client. Sono inclusi suggerimenti per la risoluzione del problema rappresentato da ciascun codice errore.

|Codice errore|Possibile problema|Soluzione suggerita|
|--------------|--------------------|------------------------|
|**0x80CF0437**|L'orologio del computer client non è impostato sull'ora corretta.|Assicurarsi che l'orologio e il fuso orario nel computer client siano impostati sull'ora e sul fuso orario corretti.|
|**0x80240438**, **0x80CF0438**, **0x80CF401B**|Impossibile connettersi al servizio Intune. Verificare le impostazioni proxy del client.|Verificare che la configurazione del proxy nel computer client sia supportata da Intune e che il computer client disponga di accesso a Internet. Per altre informazioni sulle configurazioni proxy supportate, vedere [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) (Proteggere i PC Windows con Endpoint Protection per Microsoft Intune).|
|**0x80CF402C**|Impossibile connettersi al servizio Intune. Verificare la connettività di rete.|Verificare che il computer disponga di connettività di rete. Controllare che il cavo di rete sia collegato o che la rete wireless sia operativa.|
|**0x80240438, 0x80CF0438**|Non sono configurate impostazioni proxy in Internet Explorer e nel sistema locale.|Controllare le impostazioni proxy del client e verificare che la configurazione proxy nel computer client sia supportata da Intune. Verificare anche che il computer client disponga dell'accesso a Internet. Per altre informazioni sulle configurazioni proxy supportate, vedere [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) (Proteggere i PC Windows con Endpoint Protection per Microsoft Intune).|
|**0x80043001**|Il pacchetto di registrazione non è aggiornato.|Scaricare e installare il pacchetto del software client più recente dall'area di lavoro **Amministrazione** . Per le istruzioni, vedere l'argomento [Installare il client PC Windows con Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).|
|**0x80043004**|Sottoscrizione inesistente o disabilitata.|Verificare che l'account e la sottoscrizione a Intune siano ancora attivi. Per visualizzare le impostazioni dell'account, accedere al proprio account nell'[interfaccia di amministrazione di Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043002**|L'account è in modalità di manutenzione.|Quando l'account è in modalità di manutenzione, non è possibile registrare nuovi computer client. Per visualizzare le impostazioni dell'account, accedere al proprio account nell'[interfaccia di amministrazione di Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043003**|L'account è stato eliminato.|Verificare che l'account e la sottoscrizione a Intune siano ancora attivi. Per visualizzare le impostazioni dell'account, accedere al proprio account.|
|**0x80043005**|Il computer client è stato rimosso.|Attendere alcune ore, rimuovere le versioni precedenti del software client dal computer, quindi riprovare a installare il software client. Per altre informazioni, vedere la sezione **Cosa fare se il client non viene disinstallato dalla console di amministrazione di Microsoft Intune** precedente.|
|**0x80043006**|È stato raggiunto il numero massimo di postazioni consentito per l'account.|L'organizzazione deve acquistare ulteriori postazioni prima che sia possibile registrare più computer client nel servizio.|
|**0x80043007**|Impossibile trovare il file del certificato nella stessa cartella del programma di installazione.|Estrarre tutti i file prima di avviare l'installazione. Non rinominare o spostare eventuali file estratti: tutti i file devono trovarsi nella stessa cartella altrimenti l'installazione non riuscirà. Per altre informazioni, vedere [Install the Windows PC client with Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune) (Installare il client PC Windows con Microsoft Intune).|
|**0x8024D015**, **0x00240005**, **0x80070BC2**, **0x80070BC9**, **0x80CFD015**|È impossibile installare il software perché un riavvio del computer client è in sospeso.|Riavviare il computer, quindi riprovare a installare il software client.|
|**0x80070032**|Uno o più prerequisiti per l'installazione del software client non sono stati individuati nel computer client.|Assicurarsi che tutti gli aggiornamenti necessari siano installati nel computer client, quindi riprovare a installare il software client. Per altre informazioni sui prerequisiti per l'installazione del software client, vedere [Network infrastructure requirements for Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune) (Requisiti dell'infrastruttura di rete per Microsoft Intune).|
|**0x80043008**|Impossibile avviare il servizio Aggiornamenti di Microsoft Online Management.|Contattare il supporto tecnico, come descritto in [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Come ottenere supporto per Microsoft Intune).|
|**0x80043009**|Il computer client è già registrato al servizio.|È necessario ritirare il computer client prima di potersi registrare nuovamente al servizio. Per le istruzioni, vedere [Retire devices from Microsoft Intune management](/intune/deploy-use/retire-devices-from-microsoft-intune-management) (Ritirare dispositivi dalla gestione di Microsoft Intune).|
|**0x8004300B**|Impossibile eseguire l'installazione del software client perché la versione di Windows in esecuzione nel client non è supportata.|Intune non supporta la versione di Windows in esecuzione nel computer client. Per un elenco dei sistemi operativi supportati, vedere [Network infrastructure requirements for Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune) (Requisiti dell'infrastruttura di rete per Microsoft Intune).|
|**0xAB2**|Windows Installer non è in grado di accedere al runtime VBScript per un'azione personalizzata.|L'errore è causato da un'azione personalizzata basata sulle librerie a collegamento dinamico (DLL). Nella risoluzione dei problemi relativi alle DLL, potrebbe essere necessario l'utilizzo degli strumenti descritti in [Supporto Tecnico Microsoft KB198038: Strumenti utili per pacchetti e problemi di distribuzione](http://go.microsoft.com/fwlink/?LinkID=234255).|
|**0x8004300f**|Non è possibile installare il software perché il client System Center Configuration Manager è già installato.|Rimuovere il client Configuration Manager, quindi ripetere l'installazione del software client.|
|**0x80043010**|Impossibile installare il software poiché il client Open Mobile Alliance Device Management (OMADM) è già installato.|Annullare la registrazione del client OMADM, quindi riprovare a installare il software del client.|
Se i problemi di installazione persistono, contattare il supporto tecnico, come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md). È necessario avere a disposizione il log di registrazione del computer client (disponibile in % *programfiles*% \Microsoft\OnlineManagement\Logs\Enrollment.log e in %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log), oltre al log di Windows Update (%*windir*%\windowsupdate.log) per mostrarli ai tecnici del supporto.

### Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Jul16_HO3-->


