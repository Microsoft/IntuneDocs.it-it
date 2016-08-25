---
title: Impostazioni dei criteri di aggiornamento dell'edizione Windows | Microsoft Intune
description: "Informazioni su come aggiornare automaticamente i dispositivi Windows 10 alla versione più recente con Intune."
keywords: 
author: robstackmsft
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a409d36c1c5fcfd3d81ce0cbdf1f69af4747157a
ms.openlocfilehash: 94ce40589180ebafcacfb497bc4de9f3458f4ca3


---

# Impostazioni dei criteri di aggiornamento dell'edizione Windows in Microsoft Intune
I **Criteri di aggiornamento edizione** Microsoft Intune consentono di aggiornare automaticamente i dispositivi che usano una delle versioni seguenti di Windows 10 a un'edizione più recente:
* Windows 10 Desktop
* Windows 10 Holographic

## Prima di iniziare
Prima di iniziare l'aggiornamento dei dispositivi alla versione più recente, è necessario uno degli elementi seguenti:
* Un codice Product Key valido per installare la versione nuova di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio le edizioni Windows 10 Desktop.
* Un file di licenza di Microsoft che contiene le informazioni sulle licenze per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio per le edizioni Windows 10 Mobile e Windows 10 Holographic.
* I dispositivi Windows 10 da usare come destinazione devono essere registrati in Microsoft Intune.

## Impostazioni dei criteri di aggiornamento dell'edizione

|Nome impostazione|Dettagli|
|-|-|
|**Nome**|Immettere un nome per i criteri di aggiornamento dell'edizione.|
|**Descrizione**|Immettere facoltativamente una descrizione per i criteri che consenta di identificarli nella console di Intune.
|**Edizione di aggiornamento**|Dall'elenco a discesa selezionare la versione di Windows 10 Desktop, Windows 10 Holographic o Windows 10 Mobile a cui aggiornare i dispositivi specificati.
|**Codice Product Key**|Specificare il codice Product Key ottenuto da Microsoft che può essere usato per aggiornare tutti i dispositivi Desktop Windows 10 di destinazione.<br>Dopo aver creato criteri che contengono un codice Product Key, non è possibile modificare il codice Product Key in un secondo momento, perché il codice viene nascosto per motivi di sicurezza. Per modificare il codice Product Key, è necessario immettere nuovamente l'intero codice.
|**File di licenza**|Fare clic su **Sfoglia** per selezionare il file di licenza ottenuto da Microsoft che contiene informazioni sulla licenza per l'edizione Windows Holographic o Windows 10 Mobile alla quale si vogliono aggiornare i dispositivi di destinazione.

### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


<!--HONumber=Jul16_HO3-->


