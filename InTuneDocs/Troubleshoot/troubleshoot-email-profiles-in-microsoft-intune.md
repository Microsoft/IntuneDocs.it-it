---
title: Risolvere i problemi relativi ai profili di posta elettronica | Microsoft Intune
description: Problemi relativi ai profili di posta elettronica e procedure di risoluzione.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9915b275101e287498217c4f35e1c0e56d2425c2
ms.openlocfilehash: 9b699229489be2f09ea4c7a80e1e80f6ec7b106e


---

# Risolvere i problemi relativi ai profili di posta elettronica in Microsoft Intune
Di seguito vengono elencati alcuni problemi relativi ai profili di posta elettronica e le relative procedure di risoluzione.

Se queste informazioni non consentono di risolvere il problema, vedere [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md) per trovare altri modi per ottenere assistenza.


## Impossibile inviare immagini dall'account di posta elettronica
Gli utenti con account di posta elettronica configurati automaticamente non riescono a inviare le immagini dai propri dispositivi.
Questo errore si verifica quando l'opzione **Consenti l'invio di messaggi di posta elettronica da applicazioni di terze parti** non è abilitata.

### Soluzione Intune

1.  Aprire la console di amministrazione di Microsoft Intune, selezionare il carico di lavoro **Criterio** &gt; **Criteri di configurazione**.

2.  Selezionare il profilo di posta elettronica e scegliere **Modifica**.

3.  Selezionare **Consenti l'invio di messaggi di posta elettronica da applicazioni di terze parti**.

### Configuration Manager integrato con la soluzione Intune

1.  Nella console di Configuration Manager fare clic su &gt;**Asset e conformità**.

2.  Espandere **Panoramica** -&gt; **Impostazioni di conformità** -&gt;**Accesso risorse aziendali** e selezionare **Profili di posta elettronica**.

3.  Fare clic con il tasto destro del mouse sul profilo di posta elettronica e aprire **Proprietà**.

4.  Nella scheda **Impostazioni di sincronizzazione** selezionare **Consenti di inviare messaggi di posta elettronica da applicazioni di terze parti**.

## Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Jul16_HO4-->


