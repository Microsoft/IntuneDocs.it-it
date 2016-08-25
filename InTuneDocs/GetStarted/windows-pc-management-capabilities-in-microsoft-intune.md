---
title: "Funzionalità di gestione dei PC Windows | Microsoft Intune"
description: "Informazioni sulle funzionalità di Intune per gestire i PC Windows con il software client di Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a6caef9e0f4d6235ecf1a89c1765d6c8e6ce1a7b
ms.openlocfilehash: e5e3833a38434d4fe55cae554fc49f567b606ad8


---

# Funzionalità di gestione dei PC Windows (con il client PC Microsoft Intune)
Nella maggior parte dei casi i dispositivi vengono registrati con Microsoft Intune che offre un maggior numero di funzionalità rispetto al client PC Intune. Tuttavia è possibile anche gestire i PC usando il client PC Intune che fornisce le funzionalità seguenti:

-   **Gestione aggiornamenti software**: è possibile mantenere aggiornati i computer e stabilire quando applicare gli aggiornamenti.

-   **Criteri di Windows Firewall**: questa funzionalità garantisce che in nessun computer usato nell'azienda Windows Firewall sia inattivo o configurato in modo non corretto.

-   **Protezione antimalware**: Intune include Endpoint Protection, che consente di proteggere i computer dal malware.

-   **Assistenza remota**: Intune consente agli utenti di contattare il personale tecnico IT, che può fornire assistenza usando la funzionalità Desktop remoto inclusa con Intune (è necessario installare il software TeamViewer).

-   **Gestione delle licenze software:** è possibile tenere traccia del numero di licenze software disponibili e di quante licenze disponibili sono in uso.
-   **Distribuzione di app**: è possibile distribuire software ai PC gestiti. Alcune funzionalità di gestione di app non sono disponibili quando si gestiscono PC con il software client.


Intune supporta l'installazione del software client per PC su al massimo 7.000 dispositivi Windows.

## Requisiti del sistema operativo
Intune può gestire i PC con le versioni seguenti di Windows (sia 32 bit sia 64 bit):


-   **Windows Vista**: versioni Business, Enterprise e Ultimate

-   **Windows 7**: versioni Pro, Enterprise e Ultimate (senza Service Pack o con SP1)

-   **Windows 8**: versioni Pro ed Enterprise

-   **Windows 8.1**: versioni Pro ed Enterprise

- **Windows 10**: versioni Pro, Education ed Enterprise


## Requisiti hardware minimi
Di seguito sono riportati i requisiti hardware minimi per l'installazione del client PC Intune:

|Requisito|Dettagli|
|---------------|--------------------|
|Rete|Il client richiede che il computer abbia una connessione Internet.|
|Processore e memoria|Consultare i requisiti per il processore e la RAM specifici del sistema operativo del computer.|
|Spazio su disco|200 MB di spazio su disco prima dell'installazione del software client.|

## Altri requisiti
Di seguito sono riportati i requisiti software per l'installazione del client PC Intune:

|Requisito|Dettagli|
|---------------|--------------------|
|Autorizzazioni amministrative|L'account che installa il software client deve disporre delle autorizzazioni di amministratore locale per tale computer.|
|Windows Installer 3.1|Il computer deve avere almeno Windows Installer 3.1.|
|Rimuovere il software client incompatibile|Prima di installare il software client PC Intune è necessario disinstallare il seguente software client dal computer:<br /><br />-   Qualsiasi versione di Configuration Manager<br />-   Qualsiasi versione di Microsoft Systems Management Server (SMS)|

### Vedere anche
[Funzionalità di gestione dei dispositivi mobili in Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Aug16_HO3-->


