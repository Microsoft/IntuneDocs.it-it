---
title: Configurare Skycure per l'uso di Single Sign-On (SSO) di Azure AD con Intune
titleSuffix: Intune on Azure
description: Configurare Skycure per l'uso di Single Sign-On (SSO) di Azure AD con Intune
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0466ac4-4942-4c4c-b8af-996b597c701d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b2d8a79baf65208e87dbe85d8cc934e167710144
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Configurare Skycure per l'uso di Single Sign-On (SSO) di Azure Active Directory

La funzionalità SSO di Azure AD viene usata quando Intune è integrato con Skycure. Ecco i principali vantaggi:

-   Gli **amministratori** possono usare le stesse credenziali senza doverle digitare di nuovo ogni volta che accedono e si disconnettono dai portali Microsoft (Intune, Azure) e dalla console di gestione di Skycure.

-   Gli **utenti finali** possono usare le stesse credenziali di Azure AD senza doverle digitare di nuovo ogni volta che accedono e di disconnettono dalle app Skycure.

Di seguito sono riportati i passaggi per l'integrazione di Skycure con la funzionalità SSO di Azure Active Directory.

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>Per recuperare l'ID del tenant di Azure Active Directory

È necessario recuperare l'ID del tenant di Azure AD.

1.  Andare nel [portale di Azure](https://portal.azure.com/) e accedere con le proprie credenziali.

2.  Nel **Dashboard** visualizzato scegliere **Azure Active Directory**.

    ![Dashboard di Azure AD](./media/skycure-sso-1.png)

3.  Nel pannello **Azure Active Directory** visualizzato scegliere **Proprietà**.

    ![Pannello Proprietà di Azure AD](./media/skycure-sso-2.png)

4.  Fare clic sull'icona **Copia** sotto **ID directory** nel pannello **Proprietà** di Azure Active Directory.

5. Incollare l'ID directory copiato in un file di testo per poterlo usare in un secondo momento. L'ID directory sarà necessario più avanti nella procedura di integrazione di Skycure e Intune.

    ![Dashboard di Azure AD](./media/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Consentire a Skycure di comunicare con Azure Active Directory

1.  Immettere l'URL seguente nel browser. Anziché **DIRECTORY_ID**, immettere l'ID del tenant di Azure Active Directory copiato in precedenza nel file di testo.

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  È necessario accedere usando le credenziali di Azure Active Directory. Fare clic su **Accept** (Accetto) per continuare.

![Pagina di accesso di Azure AD](./media/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Creare un gruppo di sicurezza di Azure AD per Skycure (facoltativo)

Può essere opportuno creare un gruppo dedicato a cui appartengono gli utenti che eseguono Skycure (ad esempio, Utenti Skycure). Questo gruppo può essere utile per l'analisi dell'attività di Skycure tramite report.

-   Per altre informazioni, vedere [Creare un gruppo e aggiungere membri in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).

> [!NOTE] 
> È anche possibile usare un gruppo di sicurezza di Azure AD esistente.

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Configurare l'account di Azure AD per integrare Intune con Skycure

1.  Dalla [console di gestione di Skycure](https://aad.skycure.com/) immettere l'ID del tenant di Azure Active Directory salvato in precedenza nel file di testo.

![Campo dell'ID del tenant di Azure AD nella console di gestione di Skycure](./media/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure verifica se l'ID del tenant di Azure AD esiste eseguendo una query in Azure AD. Se l'ID viene trovato, l'amministratore può proseguire con il passaggio successivo, ovvero la configurazione di base.

## <a name="next-steps"></a>Passaggi successivi

[Scaricare i criteri di configurazione delle app iOS Skycure](skycure-ios-app-configuration-policy-download.md)
