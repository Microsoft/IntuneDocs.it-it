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
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a719b3f53076a55f1e888a9ddf8e98c7074dd25f
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>Come creare profili di configurazione del dispositivo in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


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

    ![Creare un profilo del dispositivo](./media/create-device-profile.png)
4. Dopo aver terminato di configurare le impostazioni, nel pannello **Crea profilo** scegliere **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).


### <a name="next-steps"></a>Passaggi successivi
Vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md) per informazioni sull'assegnazione dei profili di dispositivo.

