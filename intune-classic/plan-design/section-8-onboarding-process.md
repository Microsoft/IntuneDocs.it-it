---
title: Processo di onboarding di Intune | Documentazione Microsoft
description: Questo articolo illustra tutti i dettagli che devono essere presi in considerazione durante l&quot;onboarding di una soluzione Intune in configurazione solo cloud nel proprio ambiente.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 562e24af8058df56f1b952c82fefe62d38388ec3
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="intune-implementation"></a>Implementazione di Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Durante la fase di onboarding, verrà implementato Intune nell'ambiente di produzione. Il processo di implementazione comprenderà l'impostazione e la configurazione di Intune e delle dipendenze esterne (se necessario), in base ai [requisiti dei casi d'uso](section-3-determine-use-case-requirements.md) che sono stati illustrati nelle sezioni precedenti di questa guida.

Nella sezione seguente viene fornita una panoramica del processo di implementazione di Intune che include i requisiti e le attività generali.

>[!TIP]
> Per altre informazioni sul processo di implementazione di Intune, vedere [Risorse aggiuntive](additional-resources.md).

## <a name="intune-requirements"></a>Requisiti di Intune

I requisiti principali per la configurazione autonoma di Intune sono indicati di seguito:

-   Sottoscrizione EMS/Intune

-   Sottoscrizione Office 365 (per le app di Office e le app gestite tramite criteri MAM)

-   Certificato APN Apple (per consentire la gestione della piattaforma per dispositivi iOS)

-   Azure AD Connect (per la sincronizzazione della directory)

-   Intune On-Premises Connector per Exchange (per la CA per Exchange locale, se necessario)

-   Connettore di certificati di Intune (per la distribuzione del certificato SCEP, se necessario)

>[!TIP]
> Altre informazioni sui requisiti per la configurazione autonoma di Intune sono disponibili [qui](/intune-classic/get-started/what-to-know-before-you-start-microsoft-intune).

## <a name="intune-implementation-process"></a>Processo di implementazione di Intune

### <a name="overview-of-implementation-tasks"></a>Panoramica delle attività di implementazione

Di seguito viene fornita una panoramica di ogni attività durante l'implementazione di Intune.

#### <a name="task-1-add-intune-subscription"></a>Attività 1: Aggiungere la sottoscrizione Intune

Come indicato nella sezione dei requisiti precedente, è necessario una sottoscrizione EMS o Intune. Se l'organizzazione non dispone di una sottoscrizione EMS o Intune, contattare Microsoft o il team dell'account Microsoft e comunicare il proprio interesse per l'acquisto di Enterprise Mobility + Security (EMS) o Intune.

-   Altre informazioni su [come acquistare Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing).

#### <a name="task-2-add-office-365-subscription"></a>Attività 2: Aggiungere la sottoscrizione Office 365

Questo passaggio è facoltativo. Come indicato nella sezione dei requisiti precedente, è necessaria una sottoscrizione Office 365 se si intende usare Exchange Online e gestire le app di Office Mobile con i criteri MAM. Se l'organizzazione non dispone di una sottoscrizione Office 365, contattare Microsoft o il team dell'account Microsoft e comunicare il proprio interesse per l'acquisto di Office 365.

-   Altre informazioni su [come acquistare Office 365](https://products.office.com/business/compare-office-365-for-business-plans).

#### <a name="task-3-add-users-groups-in-azure-ad"></a>Attività 3: Aggiungere i gruppi di utenti in Azure AD

Potrebbe essere necessario aggiungere utenti o gruppi di sicurezza in Active Directory o AAD, in base agli scenari per i casi d'uso e ai requisiti della distribuzione di Intune. È consigliabile esaminare gli utenti e i gruppi di sicurezza correnti in Active Directory o Azure Active Directory e stabilire se soddisfano pienamente le proprie esigenze. In genere, i nuovi utenti e gruppi di sicurezza vengono aggiunti in Active Directory e quindi sincronizzati in Azure Active Directory tramite Azure AD Connect.

-   Altre informazioni su [come aggiungere utenti o gruppi in Intune](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3).

#### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>Attività 4: Assegnare le licenze utente di Intune e Office 365

A tutti gli utenti che saranno interessati dalla distribuzione di Office 365 ed EMS/Intune deve essere assegnata una licenza. L'assegnazione delle licenze di EMS/Intune e Office 365 può essere eseguita nel portale dell'interfaccia di amministrazione di Office 365.

-   Altre informazioni su [come assegnare le licenze di Intune](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).

#### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>Attività 5: Impostare l'autorità di gestione dei dispositivi mobili su Intune

Prima di iniziare a impostare, configurare, gestire e registrare i dispositivi con Intune, è necessario impostare l'autorità di gestione dei dispositivi su Intune. L'attività di impostazione dell'autorità di gestione dei dispositivi viene eseguita nell'area di lavoro Amministrazione del portale di amministrazione di Intune.

-   Altre informazioni su [come impostare l'autorità di gestione dei dispositivi](/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).

#### <a name="task-6-enable-device-platforms"></a>Attività 6: Abilitare le piattaforme per i dispositivi

Per impostazione predefinita, nella console di amministrazione di Intune è abilitata la maggior parte delle piattaforme per i dispositivi, ad eccezione dei dispositivi Apple (iOS e Mac). Per poter registrare e gestire in Intune i dispositivi iOS, è prima necessario abilitare la piattaforma del dispositivo. L'abilitazione della piattaforma per i dispositivi iOS comprende tre passaggi: creare il certificato APN, scaricarlo e caricarlo in Intune.

-   Altre informazioni su [come funziona la configurazione della gestione dei dispositivi iOS e Mac.]/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)

#### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>Attività 7: Aggiungere e distribuire i criteri di termini e condizioni

Microsoft Intune supporta l'aggiunta e la distribuzione di criteri di termini e condizioni. L'aggiunta e la distribuzione dei criteri di termini e condizioni vengono eseguite nell'area di lavoro Criteri del portale di amministrazione di Intune. Aggiungere i criteri di termini e condizioni a seconda delle esigenze e distribuirli ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

-   Altre informazioni su [come aggiungere e distribuire i criteri di termini e condizioni](/intune-classic/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune).

#### <a name="task-8-add-and-deploy-configuration-policies"></a>Attività 8: Aggiungere e distribuire i criteri di configurazione

Microsoft Intune supporta l'aggiunta e la distribuzione di due tipi di criteri di configurazione: generali e personalizzati. L'aggiunta e la distribuzione dei criteri di configurazione vengono eseguite nell'area di lavoro Criteri del portale di amministrazione di Intune. Aggiungere i criteri di configurazione a seconda delle esigenze e distribuirli ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

-   Altre informazioni su [come aggiungere e distribuire i criteri di configurazione](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

#### <a name="task-9-add-and-deploy-resource-profiles"></a>Attività 9: Aggiungere e distribuire i profili delle risorse

Microsoft Intune supporta i profili di posta elettronica, Wi-Fi e VPN. L'aggiunta e la distribuzione dei profili vengono eseguite nell'area di lavoro Criteri del portale di amministrazione di Intune. Aggiungere i profili di posta elettronica, Wi-Fi e VPN a seconda delle esigenze e distribuirli ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

-   Altre informazioni su [come abilitare l'accesso alle risorse aziendali con Intune](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

#### <a name="task-10-add-and-deploy-apps"></a>Attività 10: Aggiungere e distribuire le app

Microsoft Intune supporta la distribuzione di app Web, line-of-business e di Store pubblici. È inoltre supportata la gestione delle app in cui è integrato Intune SDK, associandole con i criteri MAM. L'aggiunta e la distribuzione delle app vengono eseguite nell'area di lavoro App del portale di amministrazione di Intune. L'aggiunta dei criteri MAM viene eseguita nell'area di lavoro Criteri del portale di amministrazione di Intune. Aggiungere le app a seconda delle esigenze e distribuirle ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

-   Altre informazioni su [come aggiungere e distribuire applicazioni](/intune-classic/deploy-use/deploy-apps).

#### <a name="task-11-add-and-deploy-compliance-policies"></a>Attività 11: Aggiungere e distribuire i criteri di conformità

Microsoft Intune supporta i criteri di conformità. L'aggiunta e la distribuzione dei criteri di conformità vengono eseguite nell'area di lavoro Criteri del portale di amministrazione di Intune. Aggiungere i criteri di conformità a seconda delle esigenze e distribuirli ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

-   Altre informazioni sui [criteri di conformità](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

#### <a name="task-12-enable-conditional-access-policies"></a>Attività 12: Abilitare i criteri di accesso condizionale

Microsoft Intune supporta l'accesso condizionale per Exchange Online e locale, SharePoint Online, Skype for Business Online e Dynamics CRM Online. I criteri di accesso condizionale vengono abilitati nell'area di lavoro Criteri del portale di amministrazione di Intune. Abilitare e configurare l'accesso condizionale a seconda delle esigenze, in base ai [casi d'uso e ai requisiti per la distribuzione di Intune](section-3-determine-use-case-requirements.md).

-   Altre informazioni sull'[accesso condizionale](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

#### <a name="task-13-enroll-devices"></a>Attività 13: Registrare i dispositivi

Intune supporta le piattaforme per dispositivi mobili iOS, Mac OS, Android, Windows desktop e Windows Mobile. Registrare le piattaforme per dispositivi mobili a seconda delle esigenze, in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

-   Altre informazioni su [come registrare i dispositivi](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune).

>[!TIP]
> Per altre informazioni sul processo di implementazione di Intune, vedere questo [modulo della sessione su Intune di Microsoft Virtual Academy](https://mva.microsoft.com/training-courses/deploying-microsoft-enterprise-mobility-suite-16408?l=PPWNoZxvD_1404778676).

## <a name="next-section"></a>Sezione successiva

Nella sezione successiva vengono fornite indicazioni su [test e convalida della distribuzione di Intune](section-9-test-and-validation.md).

