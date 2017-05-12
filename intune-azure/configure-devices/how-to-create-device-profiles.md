---
title: Creare i profili di configurazione dei dispositivi Intune | Anteprima di Intune in Azure
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come creare i profili di configurazione dei dispositivi Intune.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 74a905ed2ba9ec04ae14df96fcd3f6b6caf1241c
ms.contentlocale: it-it
ms.lasthandoff: 05/10/2017


---

# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>Come creare profili di configurazione del dispositivo in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
2. Nel pannello contenente l'elenco dei profili scegliere **Crea profilo**.
3. Nel pannello **Crea profilo** specificare quanto segue:
    - **Nome**: immettere un nome descrittivo per il nuovo profilo.
    - **Descrizione**: immettere una descrizione facoltativa per il profilo.
    - **Piattaforma**: selezionare il tipo di piattaforma per il profilo che si desidera creare.
    - **Tipo di profilo**: selezionare il tipo di profilo che si desidera creare. L'elenco dei tipi disponibili varia in base alla piattaforma scelta.
    - **Impostazioni**: vedere gli argomenti seguenti per informazioni sulle impostazioni per ogni tipo di profilo:
        -  [Impostazioni delle funzionalità dei dispositivi](how-to-configure-device-features.md)
        -  [Device restriction settings](how-to-configure-device-restrictions.md) (Impostazioni relative alle restrizioni dei dispositivi)
        -  [Email settings](how-to-configure-email-settings.md) (Impostazioni di posta elettronica)
        -  [VPN settings](how-to-configure-vpn-settings.md) (Impostazioni VPN)
        -  [Wi-Fi settings](how-to-configure-wi-fi-settings.md) (Impostazioni Wi-Fi)
        -  [Windows 10 edition upgrade settings](how-to-configure-windows-10-edition-upgrade.md) (Impostazioni di aggiornamento edizione di Windows 10)
        -  [Certificate settings](how-to-configure-certificates.md) (Impostazioni dei certificati)
        -  [Windows Information Protection settings](how-to-configure-windows-information-protection.md) (Impostazioni di Windows Information Protection)
        -  [Education settings](how-to-configure-education-settings.md) (Impostazioni di Education)
        -  [Custom settings](how-to-configure-custom-settings.md) (Impostazioni personalizzate)

    ![Creare un profilo del dispositivo](./media/create-device-profile.png)
4. Dopo aver terminato di configurare le impostazioni, nel pannello **Crea profilo** scegliere **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md).


### <a name="next-steps"></a>Passaggi successivi
Vedere [Come assegnare i profili di dispositivo con Microsoft Intune](how-to-assign-device-profiles.md) per informazioni sull'assegnazione dei profili di dispositivo.

