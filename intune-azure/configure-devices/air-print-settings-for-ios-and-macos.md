---
title: Impostazioni di AirPrint di Intune per dispositivi iOS e macOS
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come usare Intune per connettere automaticamente i dispositivi iOS e macOS a stampanti compatibili con AirPrint.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 4/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: a0f60cad9a5e679c83572375c3dd83bc7aeebd93
ms.lasthandoff: 04/19/2017


---

# <a name="airprint-settings-for-ios-and-macos-devices"></a>Impostazioni di AirPrint per dispositivi iOS e macOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Usare queste impostazioni per configurare i dispositivi iOS o macOS in modo che si connettano automaticamente a stampanti compatibili con AirPrint in rete. Sono necessari l'indirizzo IP e il percorso risorsa delle stampanti.

## <a name="find-airprint-printer-information"></a>Trovare le informazioni sulla stampante AirPrint

Seguire questa procedura per aggiungere le informazioni AirPrint al payload AirPrint in modo che gli utenti dei dispositivi iOS possano stampare su stampanti AirPrint note.

1. In un dispositivo Mac connesso alla stessa rete locale (subnet) delle stampanti Airprint aprire Terminale (da **/Applicazioni/Utilità**)
2. In Terminale digitare **ippfind** e premere INVIO.
3. Prendere nota delle informazioni sulla stampante restituite dal comando, ad esempio: **ipp://myprinter.local.:631/ipp/port1**. La prima parte delle informazioni specifica il nome della stampante mentre l'ultima indica il percorso della risorsa.
4. In Terminale digitare **ping myprinter.local** e premere INVIO.
5. Prendere nota delle informazioni sull'indirizzo IP restituite dal comando, ad esempio, **PING myprinter.local (10.50.25.21)**.
6. Infine, usare l'indirizzo IP e il percorso della risorsa nelle impostazioni del payload AirPrint. Ad esempio, un indirizzo IP potrebbe essere **10.50.25.21** mentre un percorso della risorse potrebbe essere **/ipp/port1**.

## <a name="configure-an-airprint-profile"></a>Configurare un profilo AirPrint

1. Nel pannello **Funzionalità del dispositivo** scegliere **AirPrint**.
2. Nel pannello **AirPrint** immettere l'**indirizzo IP** e il **percorso della risorsa** per aggiungere una destinazione AirPrint e fare clic su **Aggiungi**.
3. Aggiungere tutte le destinazioni necessarie. Al termine scegliere **OK**.

È anche possibile importare un elenco di stampanti da un file con valori delimitati da virgole (csv) oppure esportarlo.

