---
# required metadata

title: Il computer è già registrato | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8d3a40f5-99e9-48dc-9706-f7a3a23e5704

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Il computer è già iscritto
Questa pagina viene visualizzata perché è stata eseguita l'installazione per il software client di Intune. Il software è però già installato nel computer, di conseguenza l'installazione non può continuare.

Il problema può dipendere dalle cause seguenti:

-   Il software client è stato installato in precedenza ed è stata eseguito di nuovo il programma di installazione.

-   Il programma di installazione è stato eseguito nel computer dopo che un amministratore IT ha ritirato il dispositivo da Intune. Dopo il ritiro del dispositivo, potrebbe essere necessario attendere diverse ore prima che il software client venga rimosso dal computer.

-   Il programma di installazione ha rilevato un'installazione recente non riuscita o una rimozione non riuscita del software client.

## Componenti installati nel computer dal programma di installazione
Viene installato il client di Intune. Al termine dell'installazione, il software client continua a essere eseguito in background per consentire la configurazione del computer per l'uso con Intune. Questo processo può richiedere molto tempo e include le operazioni seguenti:

-   Registrazione del computer con Intune

-   Invio dell'inventario sull'hardware del computer e sul software installato

-   Configurazione dei criteri di Intune, inclusa l'installazione di Endpoint Protection (se configurato)

-   Installazione di Intune Center

Una volta installato Intune, è possibile usarlo per accedere al portale aziendale per collegare il computer al proprio account aziendale.

## Microsoft Intune Center
Intune Center viene installato come un'app nel computer dopo che è stato installato correttamente il software ed è stata completata la registrazione del computer con Intune. È possibile usare Intune Center per:

-   **Ottenere applicazioni dal portale aziendale** : consente di individuare e installare le app distribuite dall'amministratore IT. Quando si accede al portale aziendale per la prima volta da un computer appena registrato, viene visualizzata l'opzione per collegare l'account aziendale al computer.

-   **Verificare gli aggiornamenti software**: consente di cercare gli aggiornamenti software distribuiti dall'amministratore di Intune.

-   **Avviare un'analisi di Endpoint Protection del computer** : è possibile avviare un'analisi per individuare la presenza di software dannoso nel computer.

-   **Richiedere assistenza remota** : questa opzione è disponibile solo quando l'assistenza remota è supportata dal sistema operativo del computer.

## Verificare l'installazione o la rimozione del software client
**Per verificare l'installazione del client**
L'installazione del client di Intune è completa quando nel computer sono disponibili le app seguenti:

-   **Intune Center**

-   **Intune Endpoint Protection** (se Endpoint Protection è stato abilitato dall'amministratore IT)

Se si ha familiarità con Gestione attività, è possibile cercare il servizio client di Intune, che deve essere in esecuzione:

-   **OmcSvc**

**Per verificare la rimozione del client**
In seguito alla disinstallazione del client di Intune da un computer, vengono rimosse le app installate durante l'installazione del client, incluso Intune Center.

Viene rimosso anche il servizio client di Intune **OmcSvc**.

## Come rimuovere il software client dal computer
Per impostazione predefinita, alcune ore dopo che l'amministratore IT ha ritirato il computer dalla console di amministrazione di Intune, il software client di Intune verrà disinstallato.

Per disinstallare manualmente il software client di Intune da un computer, è possibile usare la procedura seguente per forzare la disinstallazione:

1.  Nel computer aprire un prompt dei comandi in modalità amministratore.

2.  Passare alla cartella **%programfiles%\Microsoft\OnlineManagement\Common**

3.  Eseguire il comando seguente: **ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune**

In questo modo verrà pianificata la rimozione del software client.



<!--HONumber=May16_HO1-->


