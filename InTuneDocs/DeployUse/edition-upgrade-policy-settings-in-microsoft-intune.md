---
title: Impostazioni dei criteri di aggiornamento dell'edizione Windows | Microsoft Intune
description: "Informazioni su come aggiornare automaticamente i dispositivi Windows 10 alla versione più recente con Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06a9c78300d7ff384299957102114c69c43a1ad5
ms.openlocfilehash: 45130e3e12968d9df579a7a9d0cade0343b7c165


---

# Impostazioni dei criteri di aggiornamento dell'edizione Windows in Microsoft Intune
I **Criteri di aggiornamento edizione** Microsoft Intune consentono di aggiornare automaticamente i dispositivi che usano una delle versioni seguenti di Windows 10 a un'edizione più recente:
* Windows 10 Desktop
* Windows 10 Holographic
* Windows 10 Mobile

## Prima di iniziare
Prima di iniziare l'aggiornamento dei dispositivi alla versione più recente, è necessario uno degli elementi seguenti:
* Un codice Product Key valido per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio le edizioni Windows 10 Desktop. È possibile usare codici ad attivazione multipla o chiavi del server di gestione delle chiavi.
**O** un file di licenza di Microsoft che contiene le informazioni sulle licenze per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio per le edizioni Windows 10 Mobile e Windows 10 Holographic.
* I dispositivi Windows 10 da usare come destinazione devono essere registrati in Microsoft Intune. Non è possibile usare criteri di aggiornamento dell'edizione con PC che eseguono il software client per PC di Intune.

## Impostazioni dei criteri di aggiornamento dell'edizione

|Nome impostazione|Dettagli|
|-|-|
|**Nome**|Immettere un nome per i criteri di aggiornamento dell'edizione.|
|**Descrizione**|Immettere facoltativamente una descrizione per i criteri che consenta di identificarli nella console di Intune.
|**Edizione di aggiornamento**|Dall'elenco a discesa selezionare la versione di Windows 10 Desktop, Windows 10 Holographic o Windows 10 Mobile a cui aggiornare i dispositivi specificati.
|**Codice Product Key**|Specificare il codice Product Key ottenuto da Microsoft che può essere usato per aggiornare tutti i dispositivi Windows 10 Desktop di destinazione.<br>Dopo aver creato criteri che contengono un codice Product Key, non è possibile modificare il codice Product Key in un secondo momento, perché il codice viene nascosto per motivi di sicurezza. Per modificare il codice Product Key, è necessario immettere nuovamente l'intero codice.
|**File di licenza**|Scegliere **Sfoglia** per selezionare il file di licenza ottenuto da Microsoft che contiene informazioni sulla licenza per l'edizione Windows Holographic o Windows 10 Mobile in base alla quale si vuole aggiornare i dispositivi di destinazione.

### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Aug16_HO5-->


