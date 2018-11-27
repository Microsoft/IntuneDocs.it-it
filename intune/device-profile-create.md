---
title: Creare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o configurare un profilo di dispositivo in Microsoft Intune, incluse la selezione del tipo di piattaforma e la configurazione delle impostazioni nel portale di Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6bc6f5d2f32ff060eb2eec568b0048628ad0e09c
ms.sourcegitcommit: 349ab913932547b4a7491181f0aff092f109b87b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52303856"
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
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e versioni successive**
       - **Windows 10 e versioni successive**

   - **Tipo di profilo**: selezionare il tipo di profilo che si vuole creare. L'elenco dipende dalla piattaforma scelta.
   - **Impostazioni**: gli argomenti seguenti descrivono le impostazioni per ogni tipo di profilo:

       -  [Funzionalità dei dispositivi](device-features-configure.md)
       -  [Restrizioni dei dispositivi](device-restrictions-configure.md)
       -  [Endpoint Protection](endpoint-protection-configure.md)
       -  [Protezione dell'identità](identity-protection-configure.md)  
       -  [Modalità tutto schermo](kiosk-settings.md)
       -  [Posta elettronica](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  Education per [Windows 10](education-settings-configure.md) e [iOS](wi-fi-settings-ios.md)
       -  [Aggiornamento edizione di Windows 10](edition-upgrade-configure-windows-10.md)
       -  [Criteri di aggiornamento iOS](software-updates-ios.md)
       -  [Certificati](certificates-configure.md)
       -  [Windows Information Protection](windows-information-protection-configure.md)
       -  [Personalizzato](custom-settings-configure.md)

     ![Screenshot di Crea profilo](./media/create-device-profile.png)

4. Al termine selezionare **Crea**.

Il profilo viene creato e quindi visualizzato nell'elenco.

## <a name="next-steps"></a>Passaggi successivi
[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
