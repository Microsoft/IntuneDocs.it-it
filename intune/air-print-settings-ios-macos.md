---
title: Impostazioni di AirPrint di Intune per dispositivi iOS e macOS
titlesuffix: Microsoft Intune
description: Informazioni su come usare Microsoft Intune per connettere automaticamente i dispositivi iOS e macOS a stampanti compatibili con AirPrint.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9e2781743618c213fc57e21026480f7f30535c67
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="airprint-settings-for-ios-and-macos-devices"></a>Impostazioni di AirPrint per dispositivi iOS e macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare queste impostazioni per configurare i dispositivi iOS o macOS in modo che si connettano automaticamente a stampanti compatibili con AirPrint in rete. Per procedere, sono necessari l'indirizzo IP e il percorso risorsa delle stampanti.

## <a name="find-airprint-printer-information"></a>Trovare le informazioni sulla stampante AirPrint

Seguire questa procedura per aggiungere le informazioni AirPrint al payload AirPrint in modo che gli utenti dei dispositivi iOS possano stampare su stampanti AirPrint note.

1. In un dispositivo Mac connesso alla stessa rete locale (subnet) delle stampanti Airprint aprire Terminale (da **/Applicazioni/Utilità**)
2. In Terminale digitare **ippfind** e premere INVIO.
3. Prendere nota delle informazioni sulla stampante restituite dal comando, ad esempio: **ipp://myprinter.local.:631/ipp/port1**. La prima parte delle informazioni specifica il nome della stampante mentre l'ultima indica il percorso della risorsa.
4. In Terminale digitare **ping myprinter.local** e premere INVIO.
5. Prendere nota delle informazioni sull'indirizzo IP restituite dal comando, ad esempio, **PING myprinter.local (10.50.25.21)**.
6. Infine, usare l'indirizzo IP e il percorso della risorsa nelle impostazioni del payload AirPrint. Ad esempio, un indirizzo IP potrebbe essere **10.50.25.21** mentre un percorso della risorse potrebbe essere **/ipp/port1**.

## <a name="configure-an-airprint-profile"></a>Configurare un profilo AirPrint

1. Da [Intune nel portale di Azure](https://portal.azure.com) passare a [**Funzionalità del dispositivo** nell'area di configurazione del dispositivo](device-features-configure.md). 
1. Nel riquadro **Funzionalità del dispositivo** scegliere **AirPrint**.
2. Nel riquadro **AirPrint** immettere **Indirizzo IP** e **Percorso risorsa** per aggiungere una destinazione AirPrint e fare clic su **Aggiungi**.
3. Aggiungere tutte le destinazioni necessarie. Al termine, scegliere **OK**.

È anche possibile importare un elenco di stampanti da un file con valori delimitati da virgole (csv) oppure esportarlo.


## <a name="next-steps"></a>Passaggi successivi

È ora possibile assegnare il profilo del dispositivo ai gruppi selezionati. Per informazioni dettagliate, vedere [How to assign device profiles](device-profile-assign.md) (Come assegnare profili di dispositivo).