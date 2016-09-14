---
title: Scegliere come gestire i dispositivi | Microsoft Intune
description: Informazioni sui diversi modi per registrare e gestire i dispositivi.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e3f27837195e5fdf58b9c13f38b0e5c0ad90d971
ms.openlocfilehash: 86b33ff528a2922e62c4c726bc8ce5f6bdbcfa38


---

# Scegliere come gestire i dispositivi

Per sfruttare i vantaggi delle funzionalità di Intune, ad esempio la distribuzione di app e il controllo delle impostazioni del dispositivo, i dispositivi devono essere *gestiti*. La modalità di gestione dei dispositivi dipende dalle funzionalità di Intune che si vuole usare.
Questo argomento fornisce indicazioni per scegliere quale metodo soddisfa le proprie esigenze.

Per gestire i dispositivi che eseguono iOS, Mac OS X, Android o Windows Phone, è necessario *registrarli*.

Per gestire i PC Windows, sono disponibili due opzioni:

1. Registrare il dispositivo **o**
2. Installare il *client software di Intune*.

## Scegliere il metodo da usare
Per decidere come gestire i propri dispositivi, usare questo flusso decisionale.

![Flusso decisionale per la scelta del metodo di gestione dei dispositivi.](./media/choose-manage-method.png)

Registrare i PC Windows per ottenere la maggior parte delle funzionalità. Tuttavia, il client software di Intune può risultare più adatto alle proprie esigenze quando:

- Il PC esegue Windows 7
- Si vuole gestire gli aggiornamenti software Windows e l'utilizzo delle licenze
- Si vuole gestire i malware con Endpoint Protection e Windows Firewall
- Si vuole fornire assistenza remota agli utenti tramite il software TeamViewer


Per un elenco dettagliato delle funzionalità di gestione che si ottengono con ogni metodo, vedere [Mobile device management capabilities](mobile-device-management-capabilities-in-microsoft-intune.md) (Funzionalità di gestione dei dispositivi mobili) e [Funzionalità del client software per PC di Intune](windows-pc-management-capabilities-in-microsoft-intune.md).
Per informazioni sui dispositivi e i PC supportati da Intune, vedere [Dispositivi mobili e computer supportati](/intune/get-started/supported-mobile-devices-and-computers)


## Gestione di Exchange ActiveSync
Oltre alla registrazione di un dispositivo o all'installazione del client software di Intune, è inoltre possibile gestire i dispositivi tramite [Exchange ActiveSync](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune). Questo metodo comporta l'installazione di On-Premises Connector o l'uso di Service to Service Connector incorporato per connettersi a Exchange Server.
Anche se si tratta di un'ulteriore opzione per la gestione dei dispositivi, fornisce un set limitato di funzionalità di gestione rispetto agli altri metodi.


## Passaggi successivi

- [Scegliere come registrare i dispositivi mobili](/intune/get-started/choose-how-to-enroll-devices1)
- [Gestire i PC Windows con il software client per PC di Intune](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)



- [Gestione dei dispositivi mobili con Exchange ActiveSync e Microsoft Intune](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).




<!--HONumber=Aug16_HO5-->


