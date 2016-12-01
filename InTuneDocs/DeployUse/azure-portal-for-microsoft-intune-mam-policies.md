---
title: Portale di Azure per i criteri MAM | Microsoft Intune
description: Creare criteri di gestione delle app per dispositivi mobili tramite il portale di Azure. I criteri creati possono essere applicati ai dispositivi con o senza registrazione in Intune.
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 03410d1e82cfeb8d354ee1d010ada07ca86191bc
ms.openlocfilehash: e9d917401a8927099bdf8558e9f7e7185351f709


---

# <a name="azure-portal-for-microsoft-intune-mam-policies"></a>Portale di Azure per i criteri MAM di Microsoft Intune

## <a name="use-the-azure-portal"></a>Usare il portale di Azure
Il portale di Azure consente di creare e gestire i criteri di gestione delle app per dispositivi mobili (MAM).

Il portale di Azure supporta la creazione di criteri MAM per:
- App in esecuzione in dispositivi **registrati e gestiti da Intune**.

- App in esecuzione su dispositivi **non registrati** in qualsiasi soluzione MDM.
- App in esecuzione in dispositivi **registrati in una soluzione MDM di terze parti**.

>[!IMPORTANT]


> Se si sta usando la console di amministrazione di Intune per la gestione dei dispositivi, è possibile creare criteri MAM che supportano le app per i dispositivi registrati in Intune tramite la [console di amministrazione di Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) stessa.

> È possibile che nella console di amministrazione di Intune non vengano visualizzate tutte le impostazioni dei criteri MAM. Il portale di Azure è la nuova console di amministrazione per la creazione dei criteri MAM. Se si creano criteri MAM nella console di amministrazione di Intune e nel portale di Azure, i criteri del portale vengono applicati alle app e distribuiti agli utenti.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Accedere al portale di Azure e personalizzare la pagina iniziale

1.  Andare nel [portale di Azure](https://portal.azure.com) e accedere con le proprie credenziali di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Schermata della pagina di accesso al portale di Azure](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Dopo l'accesso viene visualizzato il **Dashboard**. La pagina **Dashboard** può essere personalizzata.

    ![Schermata del dashboard del portale di Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  Nel menu **Sfoglia** individuare **Intune**.![Screenshot del menu Sfoglia con Intune evidenziato](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Scegliere **Intune** > **Gestione di applicazioni mobili di Intune** > **Impostazioni**.

    ![Schermata del pannello Gestione di applicazioni mobili di Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]

    > Per aggiungere un pannello alla pagina **iniziale** , è possibile usare l'opzione di **aggiunta** nel pannello. Fare clic sull'icona a forma di puntina nel pannello **Gestione di applicazioni mobili di Intune** per aggiungere il pannello alla pagina **iniziale**.

    ![Schermata del pannello Gestione di applicazioni mobili di Intune con l'icona della puntina evidenziata](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Schermata del dashboard con il riquadro di Intune bloccato](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## <a name="next-steps"></a>Passaggi successivi
[Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Nov16_HO2-->


