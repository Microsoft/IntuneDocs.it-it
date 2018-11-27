---
title: Monitorare la conformità dei dispositivi
titlesuffix: Microsoft Intune
description: Informazioni su come monitorare la conformità dei dispositivi."
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b6c86b8f365f5ac3e65e91725e9fcd29ccd9ef58
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187023"
---
# <a name="monitor-device-compliance-in-intune"></a>Monitorare la conformità dei dispositivi in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile visualizzare il riepilogo dello stato dei **profili di conformità** nel pannello **Panoramica**.
È possibile fare clic in modo interattivo nei grafici per eseguire il drill-down e accedere ad altri dettagli. Se sono configurati più profili di conformità è possibile visualizzarne lo stato nel pannello dei criteri in **Gestisci** > **Report**.

##  <a name="device-compliance"></a>Conformità del dispositivo

La visualizzazione di riepilogo del report di conformità dei dispositivi elenca le informazioni aggregate sul numero di dispositivi che si trovano in uno degli stati seguenti:

- **Conforme**: il dispositivo è stato valutato di recente e risulta conforme alle impostazioni del profilo di conformità specificato.
- **Non conforme**: il dispositivo è stato valutato e definito non conforme.  Se è stato specificato un periodo di tolleranza nel profilo, il periodo è scaduto generando uno stato non conforme del dispositivo.
- **Periodo di grazia**: il dispositivo è stato valutato e definito non conforme. Tuttavia il periodo di tolleranza si applica ancora prima che il dispositivo venga contrassegnato come non conforme.

È possibile eseguire il drill-down di ogni sezione per visualizzare altri dettagli su singoli dispositivi e utenti.

## <a name="setting-compliance"></a>Conformità delle impostazioni

Il report sulla conformità delle impostazioni visualizza dettagli per ogni impostazione di conformità, ad esempio:

- Il numero di dispositivi non conformi con l'impostazione.
- La piattaforma a cui viene applicata l'impostazione.

È possibile eseguire il drill-down di ogni impostazione per visualizzare altre informazioni sui profili per cui sono state abilitate queste impostazioni e sul valore dell'impostazione.
