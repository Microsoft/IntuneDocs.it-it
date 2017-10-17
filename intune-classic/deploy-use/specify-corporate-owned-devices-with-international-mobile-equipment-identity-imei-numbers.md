---
title: Specificare i numeri IMEI
description: Microsoft Intune consente agli amministratori di importare i numeri IMEI (International Mobile Equipment Identity) per le piattaforme per dispositivi mobili in modo da facilitare l'identificazione dei dispositivi mobili aziendali
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9038670a4c0b4bf52868ba739336dd35366eed2f
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Specificare i dispositivi aziendali con i numeri IMEI (International Mobile Equipment Identity)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune consente agli amministratori di identificare i dispositivi mobili aziendali tramite l'importazione dei numeri IMEI per le piattaforme per dispositivi mobili. Dopo la registrazione dei dispositivi in Intune, è possibile visualizzare i dispositivi con numeri IMEI importati in **Gruppi** > **Panoramica** > **Tutti i dispositivi**. **Gruppo di dispositivi** elenca i dispositivi con numeri IMEI importati come dispositivi di tipo **Aziendale** nella colonna **Proprietà**.

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Gruppi** &gt; **Tutti i dispositivi** &gt; **Dispositivi aziendali preregistrati** &gt;  **Per IMEI (tutte le piattaforme)** e quindi scegliere **Aggiungi dispositivi....**. È possibile aggiungere dispositivi in due modi:

    -   **Caricando un file con estensione csv contenente i numeri di serie**: creare un elenco delimitato da virgole (con estensione csv) composto da due colonne senza intestazione e limitato a 5.000 dispositivi o a 5 MB per ogni file con estensione csv. Il campo dei dettagli è limitato a 128 caratteri. 

        |||
        |-|-|
        |&lt;IMEI n. 1&gt;|&lt;Dettagli sul dispositivo 1&gt;|
        |&lt;IMEI n. 2&gt;|&lt;Dettagli sul dispositivo 2&gt;|
        Il file con estensione CSV quando viene visualizzato in un editor di testo viene visualizzato come:

        ```
        01234567890123,device details
        02234567890123,device details
        ```

    -   **Aggiungendo manualmente i dettagli dei dispositivi**: immettere il numero IMEI e i dettagli per un massimo di quindici dispositivi.

   Il campo *Dettagli* è destinato all'uso amministrativo. È possibile specificare i dettagli per facilitare l'identificazione del dispositivo nell'elenco dei dispositivi di proprietà dell'azienda indicati in ordine di ID hardware. Queste informazioni non vengono inviate al dispositivo, ma verranno visualizzate nella console di Intune.

2.   Scegliere **Avanti**.
3.  Nel riquadro **Verifica dispositivi** è possibile verificare i numeri IMEI dei dispositivi importati. È anche possibile decidere se sovrascrivere i **Dettagli** relativi ai numeri IMEI in corso di reimportazione. È possibile deselezionare la casella **Sovrascrivi** per mantenere i dettagli correnti. Scegliere **Fine** per importare i numeri IMEI.
4.  I numeri IMEI e le descrizioni importati vengono aggiunti all'elenco **Per IMEI (tutte le piattaforme)**.

> [!IMPORTANT]
> Se si stanno importando i numeri IMEI per i dispositivi Android, tenere presente che alcuni dispositivi Android possono avere più numeri IMEI. Se si importa un numero IMEI che non corrisponde al numero IMEI specificato in Intune dal dispositivo, il dispositivo verrà classificato come dispositivo personale anziché come dispositivo aziendale.

Quando un dispositivo con un numero IMEI viene registrato in Intune, in genere quando un utente installa l'app Portale aziendale e completa il processo di registrazione, il dispositivo viene contrassegnato come di proprietà dell'azienda e viene visualizzato come registrato nel gruppo **IMEI Devices** (Dispositivi IMEI).

>[!NOTE]
> Quando verrà eseguita la migrazione dell'organizzazione nel nuovo portale di Azure, questa funzionalità subirà delle modifiche. Nella console di amministrazione di Intune esistente, gli amministratori possono accettare i dettagli associati da un file CSV caricato e sovrascrivere i dettagli esistenti per i singoli identificatori hardware. Nel nuovo portale di Azure sarà possibile sovrascrivere automaticamente i dettagli per tutti gli identificatori hardware o ignorare tutti i nuovi dettagli per gli identificatori esistenti.

Per specifiche dettagliate sui codici IMEI, vedere [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).
