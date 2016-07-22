---
title: "Funzionalità di gestione dei PC Windows | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 665e4a1aa7ee22db91b47660a179384f7c3e4393
ms.openlocfilehash: 9e7a2f5cb2afdeca737c0c8b1b91418352ad5539


---

# Funzionalità di gestione dei PC Windows (con il client PC Microsoft Intune)
Nella maggior parte dei casi i dispositivi vengono registrati con Microsoft Intune che offre un maggior numero di funzionalità rispetto al client PC Intune. Tuttavia è possibile anche gestire i PC usando il client PC Intune che fornisce le funzionalità seguenti:

-   **Gestisci aggiornamenti software**: è possibile mantenere aggiornati i computer e gestire la pianificazione degli aggiornamenti.

-   **Criteri di Windows Firewall**: questa funzionalità garantisce che in nessun computer usato dall'azienda Windows Firewall sia inattivo o configurato in modo non corretto.

-   **Protezione antimalware**: Intune include Endpoint Protection, che consente di proteggere i computer dal malware.

-   **Assistenza remota**: Intune consente agli utenti di contattare il personale tecnico IT che può fornire assistenza usando la funzionalità Desktop remoto inclusa con Intune <!--- (requires TeamViewer software)--->.

-   **Gestione delle licenze software:** è possibile tenere traccia del numero di licenze software disponibili e di quante licenze disponibili sono in uso.
-   **Distribuzione di app**: è possibile distribuire software ai PC gestiti. Alcune funzionalità di gestione di app non sono disponibili quando si gestiscono PC con il software client.


Intune supporta l'installazione del software client per PC su al massimo 7.000 dispositivi Windows.

## Requisiti del sistema operativo
Intune può gestire i PC con le seguenti versioni di Windows (sia x86 sia x64):


-   **Windows Vista**: versioni Business, Enterprise e Ultimate.

-   **Windows 7**: versioni Pro, Enterprise e Ultimate (senza Service Pack o con SP1).

-   **Windows 8**: versioni Pro ed Enterprise.

-   **Windows 8.1**: versioni Pro ed Enterprise.

- **Windows 10**: versioni Home, Pro, Education ed Enterprise.


## Requisiti hardware minimi
Di seguito sono riportati i requisiti hardware minimi per installare il client PC Intune:

|Requisito|Dettagli|
|---------------|--------------------|
|Rete|Il client richiede che il computer abbia una connessione Internet.|
|Processore e memoria|Consultare i requisiti per il processore e la RAM specifici del sistema operativo del computer.|
|Spazio su disco|200 MB di spazio su disco prima dell'installazione del software client.|

## Altri requisiti
Di seguito sono elencati i requisiti software per installare il client PC Intune:

|Requisito|Dettagli|
|---------------|--------------------|
|Autorizzazioni amministrative|L'account che installa il software client deve avere le autorizzazioni di amministratore locale per quel computer.|
|Windows Installer 3.1|Il computer deve avere installato almeno Windows Installer 3.1.|
|Rimuovere il software client incompatibile|Prima di installare il software client PC Intune è necessario disinstallare il seguente software client dal computer:<br /><br />-   Qualsiasi versione di Configuration Manager<br />-   Qualsiasi versione di Microsoft Systems Management Server (SMS)|

### Vedere anche
[Funzionalità di gestione dei dispositivi mobili in Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


