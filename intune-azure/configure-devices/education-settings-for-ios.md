---
title: Configurare le impostazioni relative all&quot;istruzione di Intune per iOS | Anteprima di Intune Azure | Documentazione Microsoft
description: "Anteprima di Intune Azure: informazioni sulle opzioni che è possibile usare per controllare le impostazioni relative all&quot;istruzione nei dispositivi iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44c427f8-0f22-43c2-8c29-e0f9fa533b1f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f05e0018fb202ab5774e935c3f59855e4aa2e75
ms.openlocfilehash: e52fdf8c30a680d62071cd31e308dd0180e8b9dc


---

# <a name="how-to-configure-intune-education-settings-for-ios-devices-in-intune-azure-preview"></a>Come configurare le impostazioni relative all'istruzione di Intune per i dispositivi iOS nell'anteprima di Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="create-a-device-profile-containing-ios-education-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative all'istruzione per iOS

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** selezionare **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di aggiornamento dell'edizione.
5. Dall'elenco a discesa **Piattaforma** scegliere **iOS**.
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Istruzione**.
7. Nel pannello **Istruzione** selezionare le opzioni seguenti:
    - **File del certificato radice docente**
    - **Profilo PKCS12/PFX docente**
    - **File del certificato radice studente**
    - **Profilo PKCS12/PFX studente**
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.



<!--HONumber=Feb17_HO1-->


