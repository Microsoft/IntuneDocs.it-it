---
title: Il dispositivo Android sembra essere crittografato | Microsoft Docs
description: Risolvere lo stato della crittografia nell'app Portale aziendale e Microsoft Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: caae22e59e8adb6952e9a69ff03c575ae4467b2d
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238984"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>Dispositivo crittografato, ma le app dicono altrimenti

Se Portale aziendale o l'app Microsoft Intune affermano che il dispositivo non è crittografato, ma si è certi che sia, provare i passaggi descritti in questo articolo.  

## <a name="add-a-startup-pin"></a>Aggiungere un PIN di avvio

Alcuni dispositivi Android richiedono la creazione di un PIN di avvio per assicurarsi che il dispositivo sia sicuro. Il percorso di questa impostazione sarà nell'app **Impostazioni** del dispositivo. Il nome e il percorso dell'impostazione possono variare. Ad esempio, in Samsung Galaxy S7, l'impostazione viene definita **avvio protetto**. Per abilitarla e creare un codice di accesso, passare a **Impostazioni** > **schermata di blocco e sicurezza** > **avvio protetto**.  

## <a name="encrypt-the-entire-device"></a>Crittografare l'intero dispositivo

Questa sezione si applica solo all'app Portale aziendale. Alcuni dispositivi consentono di scegliere se crittografare l'intero dispositivo o solo lo spazio usato. Scegliere l'opzione per crittografare l'intero dispositivo. Se si è scelto di crittografare solo lo spazio utilizzato:

1. [Rimuovere il dispositivo dal Portale aziendale](unenroll-your-device-from-intune-android.md).
2. Decrittografare lo spazio usato.  
3. Crittografare l'intero dispositivo.  
4. Registrare nuovamente il dispositivo.  

## <a name="downgrade-your-version-of-android"></a>Effettuare il downgrade della versione di Android

Questa sezione si applica solo all'app Portale aziendale. Se il dispositivo offre la possibilità di effettuare il downgrade ad Android 6.0 e versioni successive, procedere in tal senso. Il tentativo di effettuare il downgrade del dispositivo potrebbe comportare dei rischi di perdita di dati. In caso contrario, è consigliabile contattare il supporto tecnico dell'azienda per risolvere il problema. Le informazioni di contatto del supporto tecnico dell'azienda, sono disponibili nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="specific-manufacturer-issues"></a>Problemi di produttori specifici

Alcuni dispositivi Android con la versione 7.0 o successive crittografano i dati in modi non coerenti con determinati standard della piattaforma Android. Questi metodi di crittografia mettono a rischio le informazioni sul dispositivo. Di conseguenza, questi dispositivi non sono supportati.

Per un elenco non esaustivo di dispositivi Android supportati, vedere l'articolo [sistemi operativi e browser supportati in Intune](https://docs.microsoft.com/intune/supported-devices-browsers#supported-samsung-knox-standard-devices). Se il dispositivo non è elencato, consultare il produttore del dispositivo o contattare il personale di supporto.

> [!Note]
> Microsoft collabora con i produttori per risolvere i problemi rilevati durante i test o segnalati dagli utenti. Questo articolo verrà aggiornato quando saranno disponibili nuove informazioni.

## <a name="update-devices"></a>Aggiornare i dispositivi

Se il dispositivo non è stato aggiornato alla versione più recente di Android, passare all'app **Impostazioni** del dispositivo e selezionare **Aggiorna**.  

## <a name="next-steps"></a>Passaggi successivi

Serve ancora assistenza? Contattare il supporto tecnico aziendale (accedere al [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per informazioni sul contatto) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.  
