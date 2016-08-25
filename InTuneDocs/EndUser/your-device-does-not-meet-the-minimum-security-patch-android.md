---
title: Il dispositivo non soddisfa la patch di protezione minima | Microsoft Intune
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b3e5994c-d215-4c72-8915-349bd0b2504d
ms.sourcegitcommit: b76c04545b9b26a0e2470b95a3f5ac0a81b07817
ms.openlocfilehash: a4788340b36c7d04ff1a62844aea7dba06079a2b


---

# Il dispositivo non soddisfa la patch di protezione minima

Se un messaggio indica che il livello minimo della patch di protezione per Android non è configurato, è necessario installare almeno la patch di protezione minima o una versione più recente. L'amministratore IT richiede l'installazione per proteggere i dati aziendali nel dispositivo Android.

La posizione del livello attuale della patch di protezione può essere diversa, in base al tipo di dispositivo Android in uso. È necessario sapere se il dispositivo è di tipo Samsung Knox o è un altro tipo di dispositivo Android. Per sapere se il dispositivo è di tipo Samsung Knox, passare a **Impostazioni** > **Informazioni sul telefono**. Se la parola "Knox" non appare, significa che non si sta usando un dispositivo Samsung Knox.

**Per determinare la versione più recente del software nel dispositivo:**

- Dispositivi non Samsung Knox: provare a passare a **Impostazioni** > **Informazioni** > **Informazioni software** > **Altro**, quindi vedere in **Livello minimo di patch di protezione per Android**. I nomi di menu e i percorsi possono essere leggermente diversi per i vari dispositivi Android.

- Dispositivi Samsung Knox: passare a **Impostazioni** > **Informazioni sul telefono** > **Security software version** (Versione software di protezione).

**Per installare la patch di protezione richiesta:**

- Dispositivi non Samsung Knox: passare a **Impostazioni** > **Informazioni** > **Aggiornamenti software**. 

- Dispositivi Samsung Knox: passare a **Impostazioni** > **Aggiornamenti del sistema** > **Check for new system update** (Controlla nuovi aggiornamenti del sistema).

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

### Vedere anche
[Uso del dispositivo Android con Intune](using-your-android-device-with-intune.md)



<!--HONumber=Jun16_HO3-->


