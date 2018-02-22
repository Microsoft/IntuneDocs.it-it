---
title: Aggiornare Windows Holographic a Windows Holographic for Business
titleSuffix: Azure portal
description: Informazioni su come aggiornare i dispositivi che eseguono Windows Holographic a Windows Holographic for Business
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c467d2d4e02785bfac48afe2b39c50300eb4be40
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Aggiornare i dispositivi che eseguono Windows Holographic a Windows Holographic for Business


Per gestire i dispositivi che eseguono Windows Holographic con Microsoft Intune, è necessario creare un profilo di aggiornamento edizione per aggiornare i dispositivi da Windows Holographic a Windows Holographic for Business. Per Microsoft HoloLens è possibile acquistare Commercial Suite per ottenere la licenza necessaria per l'aggiornamento. Per altre informazioni, vedere [Sbloccare le funzionalità di Windows Holographic for Business](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise).

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>Per configurare un profilo di configurazione del dispositivo di aggiornamento edizione

1. Accedere al [portale di Azure](https://portal.azure.com) con un account amministratore.


2.  Fare clic su **Configurazione del dispositivo**, **Profili** e quindi su **+ Crea profilo**.

    ![Creazione profilo](media/Holographic-create-profile.png)

3.  Nel pannello **Crea profilo** digitare un nome per il profilo, selezionare **Windows 10 e versioni successive** per la piattaforma e selezionare **Aggiornamento edizione** per il tipo di profilo. Fare clic su **Impostazioni Configura**.

5. Nel pannello **Aggiornamento edizione** in **Edizione a cui eseguire l'aggiornamento** selezionare **Windows 10 Holographic for Business**. In **File di licenza** cercare e selezionare il file di licenza XML fornito.

    ![Immettere il nome del file XML](media/Holographic-edition-upgrade.png)
 
5.  Fare clic su **OK** e quindi fare clic su **Crea** per creare il profilo.


## <a name="deploy-the-edition-upgrade-policy"></a>Distribuire i criteri di aggiornamento edizione

È quindi possibile assegnare il profilo di aggiornamento edizione ai dispositivi o gruppi selezionati.

1. Nel profilo creato nei passaggi precedenti fare clic su **Assegnazioni**.

2. Nel pannello **Assegnazioni** selezionare i gruppi di utenti e i dispositivi che si vuole includere ed escludere con i criteri.

![Includere ed escludere gruppi](media/Holographic-groups.PNG)

Quando questi utenti o dispositivi vengono registrati in Intune, viene applicato il profilo di aggiornamento edizione. 

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui gruppi, vedere [Introduzione ai gruppi](get-started-groups.md).


