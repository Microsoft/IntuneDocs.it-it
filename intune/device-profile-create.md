---
title: Creare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o configurare un profilo di dispositivo in Microsoft Intune, incluse la selezione del tipo di piattaforma e la configurazione delle impostazioni nel portale di Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3d46960e6ea7e2ae9bed6c0016ddc309bd15f572
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Creare un profilo di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Creare il profilo
1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi** e cercare **Microsoft Intune**.

2. In **Microsoft Intune** selezionare **Configurazione del dispositivo** e quindi **Profili**. Selezionare quindi **Crea profilo**.

3. Immettere le seguenti proprietà:

   - **Nome**: immettere un nome descrittivo per il nuovo profilo.
   - **Descrizione:** immettere una descrizione per il profilo. Facoltativa, ma consigliata.
   - **Piattaforma**: selezionare il tipo di piattaforma:  

       - **Android**
       - **Android for Work**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e versioni successive**
       - **Windows 10 e versioni successive**

   - **Tipo di profilo**: selezionare il tipo di profilo che si vuole creare. L'elenco dipende dalla piattaforma scelta.
   - **Impostazioni**: gli argomenti seguenti descrivono le impostazioni per ogni tipo di profilo:

       -  [Impostazioni delle funzionalità dei dispositivi](device-features-configure.md)
       -  [Device restriction settings](device-restrictions-configure.md) (Impostazioni relative alle restrizioni dei dispositivi)
       -  [Email settings](email-settings-configure.md) (Impostazioni di posta elettronica)
       -  [VPN settings](vpn-settings-configure.md) (Impostazioni VPN)
       -  [Wi-Fi settings](wi-fi-settings-configure.md) (Impostazioni Wi-Fi)
       -  [Windows 10 edition upgrade settings](edition-upgrade-configure-windows-10.md) (Impostazioni di aggiornamento edizione di Windows 10)
       -  [Certificate settings](certificates-configure.md) (Impostazioni dei certificati)
       -  [Windows Information Protection settings](windows-information-protection-configure.md) (Impostazioni di Windows Information Protection)
       -  [Education settings](education-settings-configure.md) (Impostazioni di Education)
       -  [Custom settings](custom-settings-configure.md) (Impostazioni personalizzate)

     ![Screenshot di Crea profilo](./media/create-device-profile.png)

4. Al termine selezionare **Crea**.

Il profilo viene creato e quindi visualizzato nell'elenco.


## <a name="next-steps"></a>Passaggi successivi
Per assegnare profili di dispositivo, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).
