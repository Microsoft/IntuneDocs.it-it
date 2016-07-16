---
title: Impostazioni dei criteri di aggiornamento dell'edizione Windows | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8e911193075d2a621ef94f2917b2126501ea2100
ms.openlocfilehash: e468ff102b45bf0c23fd76d8d15c44978861ae8a


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


<!--HONumber=Jun16_HO4-->


