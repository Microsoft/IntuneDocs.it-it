---
title: Riavviare i dispositivi in remoto con Intune
titlesuffix: Microsoft Intune
description: Informazioni su come riavviare in remoto i dispositivi con l'azione di riavvio del dispositivo in Microsoft Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1bd5a01b8aac91c3bd6ea033d62d41e19aab65f8
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Riavviare i dispositivi in remoto con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Riavvia** causa il riavvio del dispositivo scelto. Il proprietario del dispositivo non viene avvisato automaticamente del riavvio, pertanto potrebbe perdere il lavoro.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità supportata in Windows 8.1 e versioni successive
- Windows Phone: funzionalità supportata in Windows Phone 8.1 e versioni successive
- iOS: funzionalità supportata

    > [!Note]  
    > Per eseguire questo comando sono necessari un dispositivo supervisionato e il diritto di accesso **Device Lock** (Blocco dispositivo). Il dispositivo viene riavviato immediatamente. I dispositivi iOS bloccati con passcode non si ricollegano a una rete Wi-Fi dopo il riavvio. È possibile che dopo il riavvio non siano in grado di comunicare con il server.
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="how-to-restart-a-device"></a>Come riavviare un dispositivo

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo, scegliere **Altro** e quindi scegliere l'azione remota del dispositivo **Riavvia**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi**.
