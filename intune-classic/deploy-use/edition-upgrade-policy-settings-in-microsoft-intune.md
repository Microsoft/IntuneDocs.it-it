---
title: Impostazioni dei criteri di aggiornamento dell'edizione di Windows
description: Informazioni su come aggiornare automaticamente i dispositivi Windows 10 a una versione più recente con Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 04/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99c0ef47ad8f143ef9bd1d6dbfff9c94fb154007
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="windows-edition-upgrade-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di aggiornamento dell'edizione Windows in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

I **criteri di aggiornamento edizione** di Microsoft Intune consentono di aggiornare automaticamente i dispositivi che usano una delle versioni seguenti di Windows 10 a una versione più recente:
* Windows 10 Desktop
* Windows 10 Holographic
* Windows 10 Mobile

Sono supportati i seguenti percorsi di aggiornamento:
- Da Windows 10 Pro a Windows 10 Enterprise
- Da Windows 10 Home a Windows 10 Education
- Da Windows 10 Mobile a Windows 10 Mobile Enterprise
- Da Windows 10 Holographic Pro a Windows 10 Holographic Enterprise

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare l'aggiornamento dei dispositivi alla versione più recente, è necessario uno degli elementi seguenti:
* Un codice Product Key valido per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio le edizioni Windows 10 Desktop. È possibile usare codici ad attivazione multipla o chiavi del server di gestione delle chiavi.
**O** un file di licenza di Microsoft che contiene le informazioni sulle licenze per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio per le edizioni Windows 10 Mobile e Windows 10 Holographic.
* I dispositivi Windows 10 da usare come destinazione devono essere registrati in Microsoft Intune. Non è possibile usare criteri di aggiornamento dell'edizione con PC che eseguono il software client per PC di Intune.

## <a name="edition-upgrade-policy-settings"></a>Impostazioni dei criteri di aggiornamento dell'edizione

|Nome impostazione|Dettagli|
|-|-|
|**Nome**|Immettere un nome per i criteri di aggiornamento dell'edizione.|
|**Descrizione**|Immettere facoltativamente una descrizione per i criteri che consenta di identificarli nella console di Intune.
|**Edizione di aggiornamento**|Dall'elenco a discesa selezionare la versione di Windows 10 Desktop, Windows 10 Holographic o Windows 10 Mobile a cui aggiornare i dispositivi specificati.
|**Codice Product Key**|Specificare il codice Product Key ottenuto da Microsoft che può essere usato per aggiornare tutti i dispositivi Windows 10 Desktop di destinazione.<br>Dopo aver creato criteri che contengono un codice Product Key, non è possibile modificare il codice Product Key in un secondo momento, perché il codice viene nascosto per motivi di sicurezza. Per modificare il codice Product Key, è necessario immettere nuovamente l'intero codice.
|**File di licenza**|Scegliere **Sfoglia** per selezionare il file di licenza ottenuto da Microsoft che contiene informazioni sulla licenza per l'edizione Windows Holographic o Windows 10 Mobile in base alla quale si vuole aggiornare i dispositivi di destinazione.

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
