---
title: Usare dispositivi personalizzati in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo per usare le impostazioni personalizzate per i dispositivi Windows, Android e iOS con Microsoft Intune
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: adecb332c91f17cf92362295b6b0c81445f5acaf
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Creare un profilo con impostazioni personalizzate in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

È possibile che Intune non abbia tutte le impostazioni predefinite di cui l'utente necessita. Oppure l'utente vuole usare un'impostazione disponibile in altri profili di dispositivo. Per aggiungere tali impostazioni, creare un profilo di dispositivo e configurarlo con impostazioni personalizzate.

In questo articolo vengono elencati i passaggi di base per creare un profilo con impostazioni personalizzate. Sono anche disponibili collegamenti per approfondire la creazione di impostazioni personalizzate con piattaforme diverse.

## <a name="custom-settings-on-different-platforms"></a>Impostazioni personalizzate su piattaforme diverse
Le impostazioni personalizzate sono configurate in modo diverso per ogni piattaforma. Ad esempio, per controllare le funzionalità nei dispositivi Android e Windows, è possibile specificare valori Open Mobile Alliance Uniform Resource Identifier (URI OMA). Per i dispositivi Apple è possibile importare un file creato con [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo**, selezionare **Profili** e fare clic su **Crea profilo**.
4. Immettere **Nome** e **Descrizione** per il profilo personalizzato.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si vogliono applicare le impostazioni personalizzate. È possibile scegliere una delle piattaforme seguenti:

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**

6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Personalizzato**.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. I collegamenti seguenti specificano altri dettagli sulle impostazioni personalizzate per ogni piattaforma:

    - [Impostazioni Android](custom-settings-android.md)
    - [Impostazioni iOS](custom-settings-ios.md)
    - [Impostazioni macOS](custom-settings-macos.md)
    - [Impostazioni Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
    - [Impostazioni Windows 10](custom-settings-windows-10.md)
    - [Impostazioni di Windows Holographic for Business](custom-settings-windows-holographic.md)
    - [Impostazioni di Android for Work](custom-settings-android-for-work.md)

8. Al termine, selezionare **Crea**.

Il profilo viene creato e visualizzato nell'elenco dei profili. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).
