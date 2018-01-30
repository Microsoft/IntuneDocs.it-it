---
title: "Come monitorare la conformità dei dispositivi"
titlesuffix: Azure portal
description: "Informazioni su come monitorare la conformità dei dispositivi.\""
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9cd8bb0486164dd9dfe020261da9079ea5a68633
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-monitor-device-compliance-in-intune"></a>Come monitorare la conformità dei dispositivi in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

È possibile visualizzare il riepilogo dello stato dei **profili di conformità** nel pannello **Panoramica**.
È possibile fare clic in modo interattivo nei grafici per eseguire il drill-down e accedere ad altri dettagli. Se sono disponibili più profili di conformità configurati, è possibile visualizzare anche lo stato per ogni criterio passando al pannello specifico e scegliendo **Report** nella sezione **Gestisci**.  Di seguito sono elencati i dettagli dei report disponibili.

##  <a name="device-compliance"></a>Conformità del dispositivo

La visualizzazione di riepilogo del report sulla conformità dei dispositivi inizia illustrando le informazioni aggregate sul numero di dispositivi che stanno segnalando uno dei seguenti valori:

- **Conforme**: la conformità del dispositivo è stata valutata recentemente e il dispositivo è stato definito compatibile con le impostazioni del profilo di conformità specificato.
- **Non conforme**: il dispositivo è stato valutato e definito non conforme.  Se è stato specificato un periodo di tolleranza nel profilo, il periodo è scaduto generando uno stato non conforme del dispositivo.
- **Periodo di grazia**: il dispositivo è stato valutato e definito non conforme. Tuttavia, il periodo di tolleranza si applica ancora prima che il dispositivo venga contrassegnato effettivamente come non conforme.

È possibile eseguire il drill-down di ogni sezione per visualizzare altri dettagli su singoli dispositivi e utenti.

## <a name="setting-compliance"></a>Conformità delle impostazioni

Il report sulla conformità delle impostazioni fornisce i dettagli per ogni impostazione di conformità, ad esempio:

- Il numero di dispositivi non conformi con l'impostazione.
- La piattaforma a cui viene applicata l'impostazione.

È possibile eseguire il drill-down di ogni impostazione per visualizzare altre informazioni sui profili per cui sono state abilitate queste impostazioni e sul valore dell'impostazione.
