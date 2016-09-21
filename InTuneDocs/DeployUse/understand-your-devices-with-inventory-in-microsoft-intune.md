---
title: Informazioni sui dispositivi con inventario | Microsoft Intune
description: Usare Intune per visualizzare informazioni sull'hardware dei dispositivi gestiti.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 18ef1ca18244b202a35fc8fc23fc994105b7b47e
ms.openlocfilehash: ff55533499494488cd4cd692c6e36fe547ade3e4


---

# Informazioni sui dispositivi con inventario in Microsoft Intune
Microsoft Intune consente di visualizzare l'inventario dei dispositivi registrati e dei PC Windows che eseguono il software client di Intune.
Intune in genere raccoglie l'inventario dei dispositivi gestiti ogni 7 giorni. Per questo motivo, può esserci un ritardo prima che i report mostrino i risultati delle eventuali ultime modifiche ai dispositivi, ad esempio, una modifica al nome del dispositivo o allo spazio di archiviazione gratuito.

## Inventario raccolto dai dispositivi registrati
Per visualizzare l'inventario raccolto dai dispositivi mobili, eseguire i [Report inventario dispositivi mobili](understand-microsoft-intune-operations-by-using-reports.md). Intune raccoglie l'inventario seguente dai dispositivi registrati:

|Proprietà|Raccolta da|
|------------|-----------------------|
|**Nome**|Tutti i dispositivi|
|**Sistema operativo**|Tutti i dispositivi|
|**Produttore**|Tutti i dispositivi|
|**Modello**|Tutti i dispositivi|
|**Canale di gestione**|Tutti i dispositivi|
|**AAD registrato**|Tutti i dispositivi tranne Mac OS X|
|**Conforme**|Tutti i dispositivi|
|**Attivato da EAS**|Tutti i dispositivi tranne Mac OS X|
|**ID di attivazione EAS**|Tutti i dispositivi tranne Mac OS X|
|**Ora di attivazione EAS**|Tutti i dispositivi tranne Mac OS X|
|**Stato gestione**|Tutti i dispositivi|
|**Indirizzo E-mail**|Tutti i dispositivi|
|**ID Exchange ActiveSync**|Tutti i dispositivi|
|**Dispositivo jailbroken o rooted**|Solo dispositivi iOS e Android|
|**ID univoco del dispositivo**|Tutti i dispositivi eccetto Exchange ActiveSync|
|**Numero di serie**|Dispositivi iOS, Mac OS X, Android, Windows 8.1 e Windows 10|
|**Spazio di archiviazione totale**|Dispositivi iOS, Mac OS X, Windows 8.1 e Windows 10|
|**Spazio di archiviazione disponibile**|Dispositivi iOS, Mac OS X, Windows 8.1 e Windows 10|
|**Numero di telefono**<br>I telefoni classificati come "aziendali" sono ora identificati con il loro numero di telefono completo quando, ad esempio, si esegue un report inventario dei dispositivi mobili. I numeri di telefono BYOD continuano a essere mascherati con &#42;, mostrando solo le ultime quattro cifre.|Dispositivi iOS, Android e Windows Phone|
|**IMEI**|Dispositivi Exchange ActiveSync, iOS, Android e Windows Phone|
|**MEID**<br>Identificativo di apparecchiatura mobile|Solo dispositivi iOS|
|**MAC Wi-Fi**|Tutti i dispositivi eccetto Exchange ActiveSync|
|**Gestore sottoscrizione**|Solo dispositivi iOS e Android|
|**Tecnologia cellulare**|Solo dispositivi iOS e Android|
|**Sotto la supervisione**|Solo dispositivi iOS|
|**Stato blocco attivazione**|Solo dispositivi iOS|
|**Data registrazione**|Tutti i dispositivi|
|**Ultimo aggiornamento**|Tutti i dispositivi|
|**Ethernet MAC**|Solo dispositivi Mac OS X|
|**Blocco attivazione abilitato**|Solo dispositivi iOS|
|**Crittografia abilitata**|Tutti i dispositivi|

## Inventario raccolto da PC Windows
> [!IMPORTANT]
> Questa sezione si applica solo ai PC Windows che eseguono il software client di PC Windows con Intune.

Per visualizzare l'inventario raccolto dai PC Windows, eseguire [Report inventario computer](understand-microsoft-intune-operations-by-using-reports.md). Intune raccoglie l'inventario seguente dai PC Windows:

-   **Nome**

-   **Tipo chassis**

-   **Produttore**

-   **Modello**

-   **Sistema operativo**

-   **Versione TPM**

-   **Spazio totale su disco**

-   **Spazio su disco utilizzato**

-   **Spazio disco disponibile**

-   **Nome disco SO**

-   **Spazio su disco SO**

-   **Spazio libero su disco SO**

-   **Memoria fisica**

-   **Nome processore**

-   **Architettura del processore**

-   **Velocità CPU**

-   **Indirizzo IP**

-   **Numero di serie**

-   **Ultimo utente che ha eseguito l'accesso**

-   **Utente assegnato**

-   **Ultimo aggiornamento**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->



<!--HONumber=Aug16_HO5-->


