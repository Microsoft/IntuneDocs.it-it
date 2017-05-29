---
title: Configurare l&quot;integrazione di Skycure con Intune | Microsoft Docs
description: Configurare l&quot;integrazione di Skycure con Microsoft Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93722f66-7641-4a3f-b1fb-3a0a58a36675
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8c862b085f654102f2d461ee5571aba1ab470ea5
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="set-up-the-skycure-integration-with-intune"></a>Configurare l'integrazione di Skycure con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

È necessario aggiungere app Skycure in Azure AD per usufruire di funzionalità di accesso Single Sign-On.

## <a name="before-you-begin"></a>Prima di iniziare

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>Account di Azure AD usato per l'integrazione di Intune e Skycure

-   Prima di avviare la procedura di configurazione di base di Skycure, verificare che l'account di Azure AD sia configurato correttamente nella [console di gestione di Skycure](https://aad.skycure.com).

### <a name="full-integration-vs-read-only"></a>Confronto tra integrazione completa e integrazione di sola lettura

Intune supporta due modalità di integrazione con Intune:

-   **Integrazione di sola lettura (configurazione di base)**: esegue solo l'inventario dei dispositivi da Azure Active Directory e li inserisce nella console di Skycure.
<br>
    -   Se le caselle **Report the health and risk of devices to Intune** (Segnala l'integrità e i rischi dei dispositivi a Intune) e **Also report security incidents to Intune** (Segnala anche gli eventi imprevisti per la sicurezza a Intune) non sono selezionate nella console di gestione di Skycure, l'integrazione è di sola lettura e pertanto lo stato dei dispositivi (conforme o non conforme) rimarrà sempre invariato in Intune.
<br></br>
-   **Integrazione completa**: consente a Skycure di segnalare a Intune i dettagli relativi ai rischi e agli eventi imprevisti per la sicurezza, creando così una comunicazione bidirezionale tra i due servizi cloud.

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>Come vengono usate le app Skycure con Azure AD e Intune?

-   **App iOS**: consente agli utenti finali di accedere ad Azure AD usando un'app iOS.

-   **App Android**: consente agli utenti finali di accedere ad Azure AD usando un'app Android.

-   **App di gestione**: questa è l'app multi-tenant Azure AD Skycure che consente le comunicazioni da servizio a servizio con Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>Per configurare l'integrazione di sola lettura tra Intune e Skycure

> [!IMPORTANT]
> Le credenziali di amministratore di Skycure sono costituite da un account di posta elettronica che deve corrispondere a un utente valido in Azure Active Directory, altrimenti il tentativo di accesso non riesce. Skycure usa Azure Active Directory per autenticare l'amministratore tramite Single Sign-On (SSO).

1.  Passare alla [console di gestione di Skycure](https://aad.skycure.com).

2.  Immettere le **credenziali di amministratore di Skycure** e quindi fare clic su **Continue** (Continua).

3.  Scegliere **Settings** (Impostazioni) e quindi **Basic Setup** (Configurazione di base) in **Intune Integration** (Integrazione di Intune).

4.  Nell'etichetta **iOS App** (App iOS) fare clic su **Add to Active Directory** (Aggiungi ad Active Directory).

    ![App iOS nella console di gestione di Skycure](../media/mtp/skycure-setup-1.png)

5.  Verrà visualizzata la pagina di accesso. Immettere le credenziali di Intune e quindi fare clic su **Accept** (Accetto).

    ![App iOS - prompt di accesso a Intune](../media/mtp/skycure-setup-2.png)

6.  Dopo che l'app è stata aggiunta in Azure AD, viene visualizzato un messaggio per indicare il completamento dell'operazione nella console di gestione di Skycure.

    ![App iOS - schermata di completamento](../media/mtp/skycure-setup-3.png)

> [!NOTE]
> Ripetere lo stesso processo per l'**app Android** e l'**app di gestione** di Skycure.

### <a name="add-an-azure-ad-security-group-into-skycure"></a>Aggiungere un gruppo di sicurezza di Azure AD in Skycure

È necessario aggiungere un gruppo di sicurezza di Azure AD contenente tutti i dispositivi che eseguono Skycure.

1.  Immettere e selezionare tutti i gruppi di sicurezza dei dispositivi che eseguono Skycure e quindi fare clic su **Apply changes** (Applica modifiche).

    ![Configurare un gruppo di sicurezza nella console di gestione di Skycure](../media/mtp/skycure-setup-4.png)

Skycure sincronizza i dispositivi che eseguono il servizio Mobile Threat Defense con i gruppi di sicurezza di Azure AD.

![Configurazione dei gruppi di sicurezza completata nella console di gestione di Skycure](../media/mtp/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>Per configurare l'integrazione completa tra Intune e Skycure

1.  Passare alla [console di gestione di Skycure](https://aad.skycure.com).

2.  Immettere le **credenziali di amministratore di Skycure** e quindi fare clic su **Continue** (Continua).

3.  Scegliere **Settings** (Impostazioni) e quindi **Full Integration** (Integrazione completa) in **Intune Integration** (Integrazione di Intune).

4.  Controllare le impostazioni seguenti:

    a.  Report the health and risk of device to Intune (Segnala l'integrità e i rischi dei dispositivi a Intune)

    b.  Also report security incidents to Intune (Segnala anche gli eventi imprevisti per la sicurezza a Intune)

5.  Fare clic su **Apply changes** (Applica modifiche).

    ![Integrazione completa di Skycure completata](../media/mtp/skycure-setup-6.png)

## <a name="next-steps"></a>Passaggi successivi

[Abilitare Skycure Mobile Threat Defense in Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

