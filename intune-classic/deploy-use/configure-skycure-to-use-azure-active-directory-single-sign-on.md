---
title: Configurare Skycure per l&quot;uso di Single Sign-On di Azure Active Directory | Microsoft Docs
description: Configurare Skycure per l&quot;uso di Single Sign-On (SSO) di Azure Active Directory
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 34d5d359-5c7c-4225-a205-8ce890b6f890
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: bf4cf8441a0ff53abf3f7830f0cdd955a4317fb0
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Configurare Skycure per l'uso di Single Sign-On (SSO) di Azure Active Directory

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

La funzionalità SSO di Azure AD viene usata quando Intune è integrato con Skycure. Ecco i principali vantaggi:

-   Gli **amministratori** possono usare le stesse credenziali senza doverle digitare di nuovo ogni volta che accedono e si disconnettono dai portali Microsoft (Intune, Azure) e dalla console di gestione di Skycure.

-   Gli **utenti finali** possono usare le stesse credenziali di Azure AD senza doverle digitare di nuovo ogni volta che accedono e di disconnettono dalle app Skycure.

Di seguito sono riportati i passaggi per l'integrazione di Skycure con la funzionalità SSO di Azure Active Directory.

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>Per recuperare l'ID del tenant di Azure Active Directory

È necessario recuperare l'ID del tenant di Azure AD.

1.  Andare nel [portale di Azure](https://portal.azure.com/) e accedere con le proprie credenziali.

2.  Nel **Dashboard** visualizzato scegliere **Azure Active Directory**.

![Dashboard di Azure AD](../media/mtp/skycure-sso-1.png)

1.  Nel pannello **Azure Active Directory** visualizzato scegliere **Proprietà**.

![Pannello Proprietà di Azure AD](../media/mtp/skycure-sso-2.png)

1.  Fare clic sull'icona **Copia** sotto **ID directory** nel pannello **Proprietà** di Azure Active Directory.

> Incollare l'ID directory copiato in un file di testo per poterlo usare in un secondo momento. L'ID directory sarà necessario più avanti nella procedura di integrazione di Skycure e Intune.

![Dashboard di Azure AD](../media/mtp/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Consentire a Skycure di comunicare con Azure Active Directory

1.  Immettere l'URL seguente nel browser. Anziché **DIRECTORY_ID**, immettere l'ID del tenant di Azure Active Directory copiato in precedenza nel file di testo.

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  È necessario accedere usando le credenziali di Azure Active Directory. Fare clic su **Accept** (Accetto) per continuare.

![Pagina di accesso di Azure AD](../media/mtp/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Creare un gruppo di sicurezza di Azure AD per Skycure (facoltativo)

Può essere opportuno creare un gruppo dedicato a cui appartengono gli utenti che eseguono Skycure (ad esempio, Utenti Skycure). Questo gruppo può essere utile per l'analisi dell'attività di Skycure tramite report.

-   Per altre informazioni, vedere [Creare un gruppo e aggiungere membri in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).

> [!NOTE] 
> È anche possibile usare un gruppo di sicurezza di Azure AD esistente.

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Configurare l'account di Azure AD per integrare Intune con Skycure

1.  Dalla [console di gestione di Skycure](https://aad.skycure.com/) immettere l'ID del tenant di Azure Active Directory salvato in precedenza nel file di testo.

![Campo dell'ID del tenant di Azure AD nella console di gestione di Skycure](../media/mtp/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure verifica se l'ID del tenant di Azure AD esiste eseguendo una query in Azure AD. Se l'ID viene trovato, l'amministratore può proseguire con il passaggio successivo, ovvero la configurazione di base.

## <a name="next-steps"></a>Passaggi successivi

[Scaricare i criteri di configurazione delle app iOS Skycure](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)

