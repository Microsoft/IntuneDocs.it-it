---
title: Visualizzare l&quot;inventario software e hardware per PC Windows | Microsoft Intune
description: Come visualizzare informazioni sull&quot;hardware e il software di PC Windows gestiti con Intune.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 807599d4a6a979c88732ab969fdecb64552a83d5


---

# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Visualizzare l'inventario software e hardware per PC Windows

Intune raccoglie informazioni dettagliate sull'hardware e sul software dei computer gestiti. Le informazioni delle seguenti procedure consentono di:

-   Creare un report che riporta informazioni sulle funzionalità hardware dei computer gestiti.

-   Creare un report che elenca il software installato in ciascun computer.

-   Aggiornare un inventario di computer per garantire che i dati nel report sia correnti.

## <a name="to-display-information-about-computers-you-manage"></a>Per visualizzare informazioni sui computer gestiti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Report** &gt; **Report inventario computer**.

2.  Nella pagina **Crea nuovo report** , accettare i valori predefiniti oppure personalizzarli per filtrare i risultati che verranno restituiti nel report. Ad esempio, è possibile scegliere di visualizzare nel report solo i computer che eseguono Windows 8.1.

3.  Fare clic su **Visualizza rapporto** per aprire il **Report inventario computer** in una nuova finestra.

    È possibile ordinare il report in base a qualsiasi colonna, ad esempio **Nome**, **Tipo di chassis** o **Produttore** selezionando l'intestazione della colonna.

## <a name="to-display-software-installed-on-computers-you-manage"></a>Per visualizzare il software installato nei computer gestiti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Report** &gt; **Report software rilevato**.

2.  Nella pagina **Crea nuovo report** , accettare i valori predefiniti oppure personalizzarli per filtrare i risultati che verranno restituiti nel report. Ad esempio, è possibile scegliere di visualizzare nel report solo il software pubblicato da Microsoft.

3.  Scegliere **Visualizza rapporto** per aprire il **Report software rilevato** in una nuova finestra.

    È possibile ordinare il report in base a qualsiasi colonna, ad esempio **Nome**, **Autore** o **Categoria** selezionando ogni intestazione di colonna. È possibile espandere gli aggiornamenti nell'elenco per visualizzare maggiori dettagli, ad esempio i computer in cui gli aggiornamenti sono installati, scegliendo la freccia direzionale accanto alla voce dell'elenco.

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Per aggiornare l'inventario dei computer per accertarsi che sia aggiornato

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il computer di cui si vuole aggiornare l'inventario.

2.  Selezionare un computer oppure tenere premuto **CTRL** per selezionare più computer.

3.  Sulla barra delle applicazioni scegliere **Attività remote** &gt; **Aggiorna inventario**.

4.  Per visualizzare lo stato dell'attività, scegliere il collegamento **Attività remote** nell'angolo inferiore destro della pagina.

    Nella finestra di dialogo **Stato attività** sono elencate le attività remote correnti, il relativo stato, il nome del dispositivo e gli eventuali errori segnalati, nonché un collegamento per consultare le informazioni sulla risoluzione dei problemi.

### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


