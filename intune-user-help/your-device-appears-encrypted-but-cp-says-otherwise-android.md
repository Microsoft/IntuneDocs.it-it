---
title: Il dispositivo Android sembra essere crittografato | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
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
ms.openlocfilehash: 55935b2f69f9573d8df5ea5ca32fb4587c652b26
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389476"
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Il dispositivo Android sembra essere crittografato, ma il portale aziendale indica il contrario

Quando si crittografa un dispositivo, si esegue la codifica delle informazioni in esso contenute tramite una chiave segreta nota solo all'utente. Questo impedisce l'accesso agli utenti non autorizzati. Molte organizzazioni richiedono agli utenti di crittografare i propri dispositivi Android prima di poter accedere ai file, alla posta elettronica o ai dati aziendali.

## <a name="common-issues"></a>Problemi comuni

Le versioni più recenti di Android, in particolare a partire dalla versione 7.0, richiedono un passcode di avvio per assicurarsi che il dispositivo sia completamente crittografato. Produttori di dispositivi diversi hanno descrizioni e posizioni variabili per il passcode di avvio. Nella maggior parte dei casi, questa impostazione è detta "avvio sicuro". 

## <a name="solutions"></a>Soluzioni

### <a name="add-a-startup-pin"></a>Aggiungere un PIN di avvio

Alcuni dispositivi Android richiedono la creazione di un PIN di avvio per assicurarsi che il dispositivo sia sicuro. Esistono molte versioni di Android da più produttori diversi. È possibile provare a risolvere il problema trovando la posizione in cui abilitare questa opzione nell'app delle impostazioni. Ad esempio, per abilitare l'avvio sicuro in un dispositivo Samsung Galaxy S7, passare a **Impostazioni** > **Blocco schermo e sicurezza** > **Avvio sicuro**.  

### <a name="encrypt-the-entire-device"></a>Crittografare l'intero dispositivo

Alcuni dispositivi consentono di scegliere se crittografare l'intero dispositivo o solo lo spazio usato. Scegliere l'opzione per crittografare l'intero dispositivo anziché solo lo spazio usato. Se è già stato crittografato solo lo spazio usato:

1. [Rimuovere il dispositivo dal Portale aziendale](unenroll-your-device-from-intune-android.md)
2. Decrittografare lo spazio usato
3. Crittografare l'intero dispositivo
4. Registrare nuovamente il dispositivo

### <a name="downgrade-your-version-of-android"></a>Effettuare il downgrade della versione di Android

Se il dispositivo offre la possibilità di effettuare il downgrade a Android 6.0+, procedere in tal senso. Il tentativo di effettuare il downgrade del dispositivo potrebbe comportare dei rischi di perdita di dati. In caso contrario, è consigliabile contattare il supporto tecnico dell'azienda per risolvere il problema. Le informazioni di contatto per il supporto tecnico dell'azienda sono disponibili nel [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).

## <a name="specific-manufacturer-issues"></a>Problemi di produttori specifici

Alcuni dispositivi Android con la versione 7.0 o successive crittografano i dati in modi non coerenti con determinati standard della piattaforma Android. Questi dispositivi possono risultare crittografati anche se sono completamente nuovi. Intune riconosce che i metodi di crittografia di questi dispositivi mettono a rischio le informazioni del dispositivo. Questo rischio deriva principalmente da utenti malintenzionati che hanno accesso fisico al dispositivo.

> [!Note]
> Microsoft collabora con i produttori per risolvere i problemi rilevati durante i test o segnalati dagli utenti. Questo articolo verrà aggiornato quando saranno disponibili nuove informazioni. 

## <a name="known-devices"></a>Dispositivi noti

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Dispositivi noti che possono essere aggiornati per risolvere questo problema

Se il dispositivo non è stato aggiornato alla versione più recente di Android, accedere al tuo dispositivo **le impostazioni** app e selezionare **Update**. Questi dispositivi potrebbero essere visualizzati come non conformi solo dopo aver aggiornato:  

- Huawei Honor 8
- Huawei P9

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Dispositivi noti che attualmente non possono essere aggiornati per risolvere questo problema
I dispositivi seguenti verranno sempre visualizzate crittografati e non possono essere utilizzati per accedere alle risorse aziendali. Per accedere alle risorse aziendali, è necessario usare un dispositivo diverso.  

- Huawei Mate 8
- Dispositivi OPPO
- Dispositivi Vivo
- Smartphone Xiaomi Mi
