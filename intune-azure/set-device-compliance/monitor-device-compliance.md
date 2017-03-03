---
title: "Come monitorare la conformità del dispositivo | Anteprima di Intune in Azure | Documentazione Microsoft"
description: "Anteprima di Intune in Azure: Come monitorare la conformità del dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: eb27002f449b3bbebb2a9b4ed780350c71eda881


---
# <a name="how-to-monitor-compliance-in-intune-azure-preview"></a>Come monitorare la conformità in anteprima di Intune in Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

È possibile visualizzare il riepilogo dello stato dei **profili di conformità** nel pannello **Panoramica**.
È possibile fare clic in modo interattivo nei grafici per eseguire il drill-down e accedere ad altri dettagli. Se sono disponibili più profili di conformità configurati, è possibile visualizzare anche lo stato per ogni criterio passando al pannello specifico e scegliendo **Report** nella sezione **Gestisci**.  Di seguito sono elencati i dettagli dei report disponibili per l'anteprima.

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

È possibile eseguire il drill-down di ogni impostazione per visualizzare altre informazioni sui profili per cui sono state abilitate queste impostazioni ed è stato configurato il valore dell'impostazione.



<!--HONumber=Feb17_HO1-->


