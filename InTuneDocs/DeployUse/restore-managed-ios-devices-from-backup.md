---
title: Ripristinare dispositivi iOS gestiti da Intune da backup | Microsoft Intune
description: Offrire indicazioni agli utenti finali su come registrare nuovamente i propri dispositivi dopo il ripristino da backup.
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 612b0954a81de1ee8d4a1e96c7440239437dec14
ms.openlocfilehash: 5fc4423f8fd0c5829be5fe6c96949e126991e430


---

# Ripristinare dispositivi iOS gestiti da Intune da backup

In alcuni casi è necessario ripristinare un dispositivo iOS da backup, ad esempio quando si prende possesso di un nuovo dispositivo. In questo argomento vengono illustrati i passaggi aggiuntivi che potrebbe essere necessario eseguire per impostare la gestione di Intune dopo il ripristino del dispositivo.

## Ripristino di backup nello stesso dispositivo

Se il backup viene ripristinato nello stesso dispositivo, verrà ripristinato anche lo stato di registrazione del dispositivo. Non sono necessarie altre azioni.

## Ripristino di backup in dispositivi diversi

Se il backup viene ripristinato in un dispositivo diverso, lo stato della registrazione non viene automaticamente ripristinato nel nuovo dispositivo. Gli utenti devono attenersi alla procedura di registrazione standard nell'app Portale aziendale versione 2.1.22 o successive per [registrare il dispositivo iOS in Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).

> [!NOTE]
> Se agli utenti finali sono destinati criteri di accesso condizionale, gli utenti potranno accedere alla posta elettronica aziendale solo dopo la nuova registrazione.

> [!TIP]
> Un esempio di comunicazione per gli utenti potrebbe essere il seguente: Per registrarsi nel nuovo dispositivo, verificare che la versione dell'app Portale aziendale corrisponda alla versione 2.1.22 o successiva. Per controllare la versione, aprire l'app Portale aziendale, toccare il pulsante Menu in alto a destra e quindi toccare Info. Se è installata una versione precedente, chiudere l'app Portale aziendale e aprire App Store. Toccare il pulsante Aggiornamenti nell'angolo inferiore destro, quindi toccare il pulsante Aggiorna accanto alla voce Portale aziendale nell'elenco. Al termine dell'aggiornamento, avviare l'app Portale aziendale e [registrare il dispositivo iOS in Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).



<!--HONumber=Oct16_HO2-->


