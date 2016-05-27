---
# required metadata

title: Funzionalità di gestione dei PC Windows in Microsoft Intune | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Funzionalità di gestione dei PC Windows (con il client PC Microsoft Intune)
Nella maggior parte dei casi i dispositivi vengono registrati con Microsoft Intune che offre un maggior numero di funzionalità rispetto al client PC Intune. Tuttavia è possibile anche gestire i PC usando il client PC Intune che fornisce le funzionalità seguenti:

-   **Gestisci aggiornamenti software**: è possibile mantenere aggiornati i computer e gestire la pianificazione degli aggiornamenti.

-   **Criteri di Windows Firewall**: questa funzionalità garantisce che in nessun computer usato dall'azienda Windows Firewall sia inattivo o configurato in modo non corretto.

-   **Protezione antimalware**: Intune include Endpoint Protection, che consente di proteggere i computer dal malware.

-   **Assistenza remota**: Intune consente agli utenti di contattare il personale tecnico IT che può fornire assistenza usando la funzionalità Desktop remoto inclusa con Intune.

-   **Gestione delle licenze software:** è possibile tenere traccia del numero di licenze software disponibili e di quante licenze disponibili sono in uso.
-   **Distribuzione di app**: è possibile distribuire software ai PC gestiti. Alcune funzionalità di gestione di app non sono disponibili quando si gestiscono PC con il software client.


## Requisiti del sistema operativo
Intune può gestire i PC con le seguenti versioni di Windows (sia x86 sia x64):


-   **Windows Vista**: versioni Business, Enterprise e Ultimate.

-   **Windows 7**: versioni Professional, Enterprise e Ultimate (senza Service Pack o con SP1).

-   **Windows 8**: versioni Professional ed Enterprise.

-   **Windows 8.1**: versioni Professional ed Enterprise.


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
[Funzionalità di gestione dei dispositivi mobili in Microsoft Intune](/intune/understand/mobile-device-management-capabilties-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


