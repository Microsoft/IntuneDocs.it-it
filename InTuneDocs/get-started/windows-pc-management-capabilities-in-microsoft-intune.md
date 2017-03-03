---
title: "Funzionalità del client software per PC di Intune | Documentazione Microsoft"
description: "Informazioni sulle funzionalità di Intune per gestire i PC Windows con il client software di Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f268cf29461447306d0f5c3ca06d541d9a03a49d
ms.openlocfilehash: 36a20feed1756ea8dde2230db81099b6c5f8c7f6


---

# <a name="windows-pc-management-capabilities-when-you-use-the-intune-software-client"></a>Funzionalità di gestione di PC Windows quando si usa il client software di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Nella maggior parte dei casi i dispositivi vengono registrati con Microsoft Intune che offre un maggior numero di funzionalità. Tuttavia è possibile anche gestire i PC usando il client software di Intune che fornisce le funzionalità seguenti:

-   **[Gestione aggiornamenti software](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)**: è possibile mantenere aggiornati i PC e stabilire quando applicare gli aggiornamenti.

-   **[Criteri di Windows Firewall](/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)**: questa funzionalità garantisce che in nessun PC usato nell'azienda Windows Firewall sia inattivo o configurato in modo non corretto.

-   **[Protezione antimalware](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)**: Intune include Endpoint Protection, che consente di proteggere i PC dal malware.

-   **[Assistenza remota](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )**: Intune consente agli utenti di contattare il personale tecnico IT, che può fornire assistenza usando la funzionalità Desktop remoto inclusa in Intune (è necessario installare il software TeamViewer).

-   **[Gestione delle licenze software](/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)**: è possibile tenere traccia del numero di licenze software disponibili e di quante licenze disponibili sono in uso.
-   **[Distribuzione di app](/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)**: è possibile distribuire software nei PC gestiti. Alcune funzionalità di gestione di app non sono disponibili quando si gestiscono PC con il client software.


Intune supporta l'installazione del client software su un massimo di 7000 dispositivi Windows.

## <a name="operating-system-requirements"></a>Requisiti del sistema operativo
Intune può gestire i PC con le versioni seguenti di Windows (sia 32 bit sia 64 bit):


-   **Windows Vista**: versioni Business, Enterprise e Ultimate

-   **Windows 7**: versioni Pro, Enterprise e Ultimate (senza Service Pack o con SP1)

-   **Windows 8**: versioni Pro ed Enterprise

-   **Windows 8.1**: versioni Pro ed Enterprise

- **Windows 10**: versioni Pro, Education ed Enterprise


## <a name="minimum-hardware-requirements"></a>Requisiti hardware minimi
Di seguito sono riportati i requisiti hardware minimi per l'installazione del client software di Intune:

|Requisito|Dettagli|
|---------------|--------------------|
|Rete|Il client richiede che il computer abbia una connessione Internet.|
|Processore e memoria|Consultare i requisiti per il processore e la RAM specifici del sistema operativo del computer.|
|Spazio su disco|200 MB di spazio su disco prima dell'installazione del software client.|

## <a name="further-requirements"></a>Altri requisiti
Di seguito sono riportati i requisiti software minimi per l'installazione del client software di Intune:

|Requisito|Dettagli|
|---------------|--------------------|
|Autorizzazioni amministrative|L'account che installa il software client deve disporre delle autorizzazioni di amministratore locale per tale computer.|
|Windows Installer 3.1|Il computer deve avere almeno Windows Installer 3.1.|
|Rimuovere il software client incompatibile|Prima di installare il software client PC Intune è necessario disinstallare il seguente software client dal computer:<br /><br />-   Qualsiasi versione di Configuration Manager<br />-   Qualsiasi versione di Microsoft Systems Management Server (SMS)|

### <a name="see-also"></a>Vedere anche
[Funzionalità di gestione dei dispositivi registrati di Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


