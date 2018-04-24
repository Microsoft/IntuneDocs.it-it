---
title: Come creare profili VPN personalizzati con Microsoft Intune
titleSuffix: ''
description: Usare configurazioni personalizzate per creare profili VPN in Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec9b959d086051985287a62f7d10fe8d4cbad7e9
ms.sourcegitcommit: 28ed8902a11500b195fff839d59b90c16af6e743
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Come creare profili VPN personalizzati in Microsoft Intune

È possibile usare i criteri di configurazione personalizzati di Intune per creare profili VPN per le piattaforme seguenti:

* Android 4 e versioni successive
* Dispositivi registrati che eseguono Windows 8.1 e versioni successive
* Windows Phone 8.1 e versioni successive
* Dispositivi registrati che eseguono Windows 10 Desktop 
* Windows 10 Mobile

Questo tipo di criteri può essere utile quando i criteri VPN Intune standard non includono le impostazioni che si vuole usare.

## <a name="to-create-a-custom-configuration-policy"></a>Per creare criteri di configurazione personalizzati:

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
5. Nel riquadro dei profili scegliere **Crea profilo**.
6. Nel riquadro **Crea profilo** immettere un **Nome** e una **Descrizione** per il profilo VPN.
7. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni VPN. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni dispositivo personalizzate:
    - **Android**
    - **Android for Work**
    - **iOS** (configurato tramite un file esportato da Apple Configurator).
    - **macOS** (configurato tramite un file esportato da Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Personalizzato**.
7. Nel riquadro **Impostazioni OMA-URI personalizzate** per ogni impostazione URI che si vuole specificare, scegliere **Aggiungi**, specificare le informazioni richieste e scegliere **OK**. Ad esempio:

   ![Finestra di dialogo Configurazione personalizzata per il profilo VPN](./media/Intune_Add_VPN_URI.png)

4.  Dopo aver immesso tutte le impostazioni URI necessarie, scegliere **OK**, quindi nel riquadro **Crea profilo** fare clic su **Crea**.

Il profilo viene creato e visualizzato nel riquadro dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).




