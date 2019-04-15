---
title: Reimpostare i dispositivi Windows 10 con Microsoft Intune - Azure | Microsoft Docs
description: Usare Fresh Start per rimuovere o disinstallare app nei PC Windows 10 tramite Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/09/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 230c328c14f0da39db34c8b91ac30fe05f9b05ca
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57388201"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Usare Fresh Start per ripristinare i dispositivi Windows 10 con Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Fresh Start** rimuove le eventuali app installate nei PC con Windows 10, versione 1703 o successive. Fresh Start consente di rimuovere le app (OEM) preinstallate in genere in un nuovo PC.  

1. Accedere al [portale di Azure](https://portal.azure.com) e passare a > **Microsoft Intune** > **Dispositivi** > **Tutti i dispositivi**.
2. Nell'elenco dei dispositivi gestiti scegliere un dispositivo desktop Windows 10.
3. Fare clic su **Fresh Start**. 
4. Selezionare **Mantieni i dati utente in questo dispositivo** per:
   * Mantenere il dispositivo aggiunto ad Azure AD
    * Il dispositivo viene nuovamente iscritto alla gestione di dispositivi mobili quando un utente abilitato per Azure Active Directory accede al dispositivo stesso.
    * Mantenere il contenuto della home directory dell'utente del dispositivo e rimuovere le app e le impostazioni  
  > [!IMPORTANT]
 > Se non si mantengono i dati dell'utente, verrà ripristinato lo stato predefinito del dispositivo. La registrazione dei dispositivi personali (BYOD) in Azure AD e nella gestione di dispositivi mobili verrà annullata.
 > I dispositivi con accesso ad Azure AD verranno iscritti nuovamente alla gestione di dispositivi mobili quando un utente abilitato per Azure Active Directory accede al dispositivo.
 
5. Fare clic su **OK**.   
6. Per visualizzare lo stato di questa azione, tornare a **Dispositivi** e fare clic su **Azioni del dispositivo**.  
