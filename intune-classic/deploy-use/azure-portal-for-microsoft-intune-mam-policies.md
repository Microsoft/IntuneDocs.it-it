---
title: Portale di Azure per i criteri MAM
description: Creare criteri di gestione delle app per dispositivi mobili tramite il portale di Azure. I criteri creati possono essere applicati ai dispositivi con o senza registrazione in Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 00328885d7fb5e75ffe894326591c0225f4b07ab
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="azure-portal-for-intune-app-protection-policies"></a>Portale di Azure per i criteri di protezione delle app di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Il portale di Azure consente di creare e gestire i criteri di protezione delle app per:

- App in esecuzione in dispositivi **registrati e gestiti da Intune**.

- App in esecuzione su dispositivi **non registrati** in qualsiasi soluzione MDM.
- App in esecuzione in dispositivi **registrati in una soluzione MDM di terze parti**.

>[!IMPORTANT]
> Il portale di Azure è la nuova console di amministrazione per la creazione di criteri di protezione delle app, ma è anche possibile creare un criterio di protezione delle app che supporta le app per dispositivi registrati in Intune tramite la [console di amministrazione di Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) per gli scenari MDM.

> È possibile che nella console di amministrazione di Intune non vengano visualizzate tutte le impostazioni dei criteri di protezione delle app disponibili. Inoltre, se si creano criteri di protezione delle app nella console di amministrazione di Intune e nel portale di Azure, i criteri creati nel portale di Azure sostituiranno quelli creati nella console di amministrazione di Intune. In questo scenario, i criteri di protezione delle app del portale di Azure verranno applicati alle app e distribuiti agli utenti.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Accedere al portale di Azure e personalizzare la pagina iniziale

1.  Andare nel [portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune.

    ![Schermata della pagina di accesso al portale di Azure](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Dopo l'accesso viene visualizzato il **Dashboard**. La pagina **Dashboard** può essere personalizzata.

    ![Schermata del dashboard del portale di Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

    ![Screenshot del menu Sfoglia con Intune evidenziato](../media/AppManagement/MAM-Azure-Portal-1.png)

4.  Scegliere **Protezione app di Intune** > **Gestione di applicazioni mobili di Intune** > **Tutte le impostazioni**.

    ![Schermata del pannello Gestione di applicazioni mobili di Intune](../media/AppManagement/MAM-Azure-Portal-2.png)

5. (Facoltativo): per aggiungere un pannello alla pagina **iniziale**, è possibile usare l'opzione di **aggiunta** nel pannello. Fare clic sull'icona a forma di puntina nel pannello **Gestione di applicazioni mobili di Intune** per aggiungere il pannello alla pagina **iniziale**.

    ![Schermata del pannello Gestione di applicazioni mobili di Intune con l'icona della puntina evidenziata](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Schermata del dashboard con il riquadro di Intune bloccato](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)

## <a name="next-steps"></a>Passaggi successivi
[Prepararsi alla configurazione dei criteri di protezione delle app](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
