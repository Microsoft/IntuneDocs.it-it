---
title: Come configurare le impostazioni dispositivo personalizzate di Intune
titleSuffix: Intune on Azure
description: Informazioni su come usare Intune per configurare impostazioni personalizzate nei dispositivi gestiti."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 769c566c7ebb91743fc0f18ebf8f3e76377ca847
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-custom-device-settings-in-microsoft-intune"></a>Come configurare le impostazioni dispositivo personalizzate in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="when-to-use-custom-settings"></a>Quando usare le impostazioni personalizzate

Le impostazioni dispositivo personalizzate possono essere utili quando Intune non dispone delle impostazioni che si desiderano configurare come predefinite, disponibili da altri profili dispositivo.
Le impostazioni personalizzate sono configurate in modo diverso per ogni piattaforma. Ad esempio, con i dispositivi Android e Windows, è possibile specificare valori Open Mobile Alliance Uniform Resource Identifier (URI OMA) per controllare le funzionalità nei dispositivi. Per i dispositivi Apple è possibile importare un file creato con [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione di un profilo con impostazioni personalizzate e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-custom-settings"></a>Creare un profilo dispositivo contenente le impostazioni personalizzate

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo personalizzato.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni personalizzate. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni dispositivo personalizzate:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Personalizzato**.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [Impostazioni Android](custom-settings-android.md)
    - [Impostazioni iOS](custom-settings-ios.md)
    - [Impostazioni macOS](custom-settings-macos.md)
    - [Impostazioni Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
    - [Impostazioni Windows 10](custom-settings-windows-10.md)
    - [Impostazioni di Android for Work](custom-settings-android-for-work.md)
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).