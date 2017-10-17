---
title: Configurare la gestione per Android
description: Abilitare la gestione di dispositivi mobili (MDM) per i dispositivi Android e KNOX Standard con Microsoft Intune.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5826cd29bf07a3f1cf9b91ec75f0e0bb46050d60
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="set-up-android-device-management"></a>Configurare la gestione dei dispositivi Android

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In qualità di amministratore di Intune, è possibile abilitare la gestione di dispositivi Android dal portale aziendale, inclusi i dispositivi Samsung KNOX Standard. Gli utenti possono quindi registrare i propri dispositivi usando l'app Portale aziendale disponibile da Google Play.

Per impostazione predefinita, tutti i dispositivi Android sono autorizzati alla registrazione in Intune. Per impedire la registrazione dei dispositivi Android, accedere al [portale di amministrazione di Microsoft Intune](https://manage.microsoft.com) con le credenziali di amministratore. Scegliere **Amministrazione** > **Gestione dei dispositivi mobili** > **Regole di registrazione** e deselezionare la casella **Consenti dispositivi Android**.

1.  **Configurare Intune**<br>
    Se non è stato già fatto, preparare la gestione di dispositivi mobili (MDM) [impostando l'autorità di gestione di dispositivi mobili](prerequisites-for-enrollment.md#step-2-set-mdm-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2.  **Registrazione Android abilitata**<br>
    Non sono necessarie altre configurazioni nella console di Intune per abilitare la registrazione dei dispositivi mobili Android.

3.  **Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali.**

    Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Android in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android). Il processo di registrazione indica agli utenti cosa possono aspettarsi e i dati visibili o meno agli amministratori IT nei propri dispositivi.

    Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:
  - [Informazioni sull'uso di Microsoft Intune per gli utenti finali](/intune/end-user-educate)
  - [End user guidance for Android devices](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune) (Linee guida per utenti finali relative a dispositivi Android)

A causa dell'assenza di Google Play Store in Cina, i dispositivi Android devono ottenere il portale aziendale dai marketplace di app cinesi. L'app Portale aziendale per Android sarà disponibile per il download negli store seguenti:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

L'app Portale aziendale per Android usa i servizi Google Play per comunicare con il servizio Microsoft Intune. Dato che i servizi Google Play non sono ancora disponibili in Cina, per completare qualsiasi attività tra le seguenti possono essere richieste fino a 8 ore. 

|Console di amministrazione di Intune| App Portale aziendale di Intune per Android |Sito Web del portale aziendale di Intune|   
|---|---|---|
|Cancellazione completa| Rimozione di un dispositivo remoto| Rimozione di un dispositivo (locale e remoto)|
|Cancellazione selettiva| Reimpostazione del dispositivo| Reimpostazione del dispositivo|
|Distribuzioni di app nuove o aggiornate| Installazione delle app line-of-business disponibili| Reimpostazione del passcode del dispositivo|
|Blocco remoto|||
|Reimpostazione del passcode|||

### <a name="see-also"></a>Vedere anche
[Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md)
