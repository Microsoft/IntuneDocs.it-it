---
title: Specificare i numeri IMEI | Microsoft Intune
description: Microsoft Intune consente agli amministratori di importare i numeri IMEI (International Mobile Equipment Identity) per le piattaforme per dispositivi mobili in modo da facilitare l&quot;identificazione dei dispositivi mobili aziendali
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: 040413b59c81c20cf579660a83acebc494c0a1b9


---

# <a name="specify-corporateowned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Specificare i dispositivi aziendali con i numeri IMEI (International Mobile Equipment Identity)
Microsoft Intune consente agli amministratori di identificare i dispositivi mobili aziendali tramite l'importazione dei numeri IMEI per le piattaforme per dispositivi mobili. Dopo la registrazione dei dispositivi in Intune, è possibile visualizzare i dispositivi con numeri IMEI importati in **Gruppi** > **Panoramica** > **Tutti i dispositivi**. **Gruppo di dispositivi** elenca i dispositivi con numeri IMEI importati come dispositivi di tipo **Aziendale** nella colonna **Proprietà**.

1. Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) scegliere **Gruppi** &gt; **Tutti i dispositivi** &gt; **Dispositivi aziendali preregistrati** &gt; ** Per IMEI (tutte le piattaforme)** e quindi scegliere **Aggiungi dispositivi....**. È possibile aggiungere dispositivi in due modi:

    -   **Caricando un file con estensione csv contenente i numeri di serie**: creare un elenco delimitato da virgole (con estensione csv) composto da due colonne senza intestazione e limitato a 5.000 dispositivi o a 5 MB per ogni file con estensione csv.

        |||
        |-|-|
        |&lt;IMEI n. 1&gt;|&lt;Dettagli sul dispositivo 1&gt;|
        |&lt;IMEI n. 2&gt;|&lt;Dettagli sul dispositivo 2&gt;|
        Il file con estensione CSV quando viene visualizzato in un editor di testo viene visualizzato come:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Aggiungendo manualmente i dettagli dei dispositivi**: immettere il numero IMEI e i dettagli per un massimo di quindici dispositivi.

   I *dettagli* sono destinati all'uso amministrativo, in modo che sia possibile identificare il numero IMEI associato a ciascun dispositivo. Queste informazioni non vengono inviate al dispositivo, ma verranno visualizzate nella console di Intune.

2.   Scegliere **Avanti**.
3.  Nel riquadro **Verifica dispositivi** è possibile verificare i numeri IMEI dei dispositivi importati. È anche possibile decidere se sovrascrivere i **Dettagli** relativi ai numeri IMEI in corso di reimportazione. È possibile deselezionare la casella **Sovrascrivi** per mantenere i dettagli correnti. Scegliere **Fine** per importare i numeri IMEI.
4.  I numeri IMEI e le descrizioni importati vengono aggiunti all'elenco **Per IMEI (tutte le piattaforme)**.

Quando un dispositivo con un numero IMEI viene registrato in Intune, in genere quando un utente installa l'app Portale aziendale e completa il processo di registrazione, il dispositivo viene contrassegnato come di proprietà dell'azienda e viene visualizzato come registrato nel gruppo **IMEI Devices** (Dispositivi IMEI).



<!--HONumber=Nov16_HO2-->


