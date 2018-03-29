---
title: Reimpostare i passcode dei dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Rimuovere o reimpostare il passcode tramite l'azione di rimozione del passcode nei dispositivi gestiti o monitorati con Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4cca5922f036711093469e71489e267af53f05a9
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Reimpostare o rimuovere il passcode di un dispositivo in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Per creare un nuovo passcode per un dispositivo, usare l'azione **Rimuovi il passcode**.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows Phone 8.1 (non aggiunto ad Azure Active Directory), incluse le versioni fino a Windows 10 Creators Update
- Windows 10 Creators Update e versioni successive
- iOS
- Le versioni di Android precedenti alla 7

Questa funzionalità non è supportata per i sistemi seguenti:

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>Reimpostare un passcode

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti selezionare un dispositivo e scegliere **...Altre informazioni**. Quindi scegliere l'azione remota del dispositivo **Rimuovi il passcode**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** in **Dispositivi**.
