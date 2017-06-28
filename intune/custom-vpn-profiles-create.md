---
title: Come creare profili VPN personalizzati con Microsoft Intune
titleSuffix: Intune on Azure
description: Usare configurazioni personalizzate per creare profili VPN in Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 11da0d31a9a00364a6105006c3e75b6bb6f2cb77
ms.contentlocale: it-it
ms.lasthandoff: 06/08/2017


---

# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Come creare profili VPN personalizzati in Microsoft Intune

## <a name="create-a-custom-configuration"></a>Creare una configurazione personalizzata
È possibile usare configurazioni personalizzate di Intune per creare profili VPN per:

* Dispositivi che eseguono Android 4 e versioni successive
* Dispositivi registrati che eseguono Windows 8.1 e versioni successive
* Dispositivi che eseguono Windows Phone 8.1 e versioni successive
* Dispositivi registrati che eseguono Windows 10 Desktop 
* Dispositivi che eseguono Windows 10 Mobile

Questo tipo di criteri può essere utile quando i criteri VPN Intune standard non includono le impostazioni che si vuole usare.

## <a name="to-create-a-custom-configuration-policy"></a>Per creare criteri di configurazione personalizzati:

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
4. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
5. Nel pannello dei profili scegliere **Crea profilo**.
6. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo VPN.
7. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni VPN. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni dispositivo personalizzate:
    - **Android**
    - **iOS** (configurato tramite un file esportato da Apple Configurator).
    - **macOS** (configurato tramite un file esportato da Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Personalizzato**.
7. Nel pannello **Impostazioni OMA-URI personalizzate** per ogni impostazione di URI che si desidera specificare, scegliere **Aggiungi**, fornire le informazioni richieste e scegliere **OK**. Ad esempio:

   ![Finestra di dialogo Configurazione personalizzata per il profilo VPN](./media/Intune_Add_VPN_URI.png)

4.  Dopo aver immesso tutte le impostazioni URI necessari, scegliere **OK**, quindi scegliere il pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).





