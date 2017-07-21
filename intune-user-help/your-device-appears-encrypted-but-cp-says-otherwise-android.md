---
title: Il dispositivo Android sembra essere crittografato
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 07/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 370fbcf8bb424030eb7b7dbaba66fa943f08aa42
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Il dispositivo Android sembra essere crittografato, ma il portale aziendale indica il contrario

Quando si crittografa un dispositivo, si esegue la codifica delle informazioni in esso contenute tramite una chiave segreta nota solo all'utente. Questo impedisce l'accesso agli utenti non autorizzati. Molte organizzazioni richiedono agli utenti di crittografare i propri dispositivi Android prima di poter accedere ai file, alla posta elettronica o ai dati aziendali.

## <a name="common-issues"></a>Problemi comuni

Le versioni più recenti di Android, in particolare a partire dalla versione 7.0, richiedono un passcode di avvio per assicurarsi che il dispositivo sia completamente crittografato. Produttori di dispositivi diversi hanno descrizioni e posizioni variabili per il passcode di avvio. Nella maggior parte dei casi, questa impostazione è detta "avvio sicuro". 

## <a name="solutions"></a>Soluzioni

### <a name="add-a-startup-pin"></a>Aggiungere un PIN di avvio

Alcuni dispositivi Android richiedono la creazione di un PIN di avvio per assicurarsi che il dispositivo sia sicuro. Esistono molte versioni di Android da più produttori diversi. È possibile provare a risolvere il problema trovando la posizione in cui abilitare questa opzione nell'app delle impostazioni. Ad esempio, per abilitare l'avvio sicuro in un dispositivo Samsung Galaxy S7, passare a **Impostazioni** > **Blocco schermo e sicurezza** > **Avvio sicuro**.  

### <a name="downgrade-your-version-of-android"></a>Effettuare il downgrade della versione di Android

Se il dispositivo offre la possibilità di effettuare il downgrade a Android 6.0+, procedere in tal senso. Il tentativo di effettuare il downgrade del dispositivo potrebbe comportare dei rischi di perdita di dati. In caso contrario, è consigliabile contattare l'amministratore IT per risolvere il problema. Le informazioni di contatto per l'amministratore IT di riferimento sono disponibili nel [sito Web del portale aziendale](http://portal.manage.microsoft.com).

## <a name="specific-manufacturer-issues"></a>Problemi di produttori specifici

Alcuni dispositivi Android con la versione 7.0 o successive crittografano i dati in modi non coerenti con determinati standard della piattaforma Android. Questi dispositivi possono risultare crittografati anche se sono completamente nuovi. Intune riconosce che i metodi di crittografia di questi dispositivi mettono a rischio le informazioni del dispositivo. Questo rischio deriva principalmente da utenti malintenzionati che hanno accesso fisico al dispositivo.

> [!Note]
> Microsoft collabora con i produttori per risolvere i problemi rilevati durante i test o segnalati dagli utenti. Questo articolo verrà aggiornato quando saranno disponibili nuove informazioni. 

## <a name="known-devices"></a>Dispositivi noti

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Dispositivi noti che possono essere aggiornati per risolvere questo problema

I proprietari di uno dei dispositivi seguenti potrebbero sperimentare questo problema se il dispositivo non è stato aggiornato alla versione più recente di Android. Per installare gli aggiornamenti per questi dispositivi, passare a **Impostazioni** > **Updater**. 

- [Huawei Honor 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [Huawei P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Dispositivi noti che attualmente non possono essere aggiornati per risolvere questo problema

Non è possibile risolvere questo problema per i dispositivi seguenti. Potrebbe essere necessario usare un dispositivo diverso per accedere alle risorse aziendali. 

- [Huawei Mate 8](http://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [Huawei Mate 9](http://consumer.huawei.com/en/phones/mate9/)
- [Smartphone Xiaomi Mi](https://xiaomi-mi.com/mi-smartphones/)
