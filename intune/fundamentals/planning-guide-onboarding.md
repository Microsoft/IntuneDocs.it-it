---
title: Processo di onboarding di Intune
titleSuffix: Microsoft Intune
description: Questo articolo illustra tutti i dettagli che devono essere presi in considerazione durante l'onboarding di una soluzione Microsoft Intune in configurazione solo cloud nel proprio ambiente.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: fdc704d1971dfcc46ee2c3f5550e201d7a8e89fb
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505196"
---
# <a name="implement-your-microsoft-intune-plan"></a>Implementare il piano di Microsoft Intune

Durante la fase di onboarding, viene distribuito Intune nell'ambiente di produzione. Il processo di implementazione comprende l'impostazione e la configurazione di Intune e delle dipendenze esterne (se necessario), in base ai [requisiti dei casi d'uso](planning-guide-requirements.md).

Nella sezione seguente viene fornita una panoramica del processo di implementazione di Intune che include i requisiti e le attività generali.

## <a name="intune-requirements"></a>Requisiti di Intune

I requisiti principali per la configurazione autonoma di Intune sono:

- Sottoscrizione Enterprise Mobility + Security (EMS)/Intune

- Sottoscrizione Office 365 (per le app di Office e le app gestite con criteri di protezione delle app)

- Certificato APN Apple (per consentire la gestione della piattaforma per dispositivi iOS)

- Azure AD Connect (per la sincronizzazione della directory)

- Intune On-Premises Connector per Exchange (per l'accesso condizionale per Exchange locale, se necessario)

- Connettore di certificati di Intune (per la distribuzione del certificato SCEP, se necessario)

>[!TIP]
> Per un elenco completo dei dispositivi che è possibile gestire con Intune, consultare l'elenco dei [dispositivi supportati](supported-devices-browsers.md).

## <a name="intune-implementation-process"></a>Processo di implementazione di Intune

Sono state identificate 13 attività discrete per l'implementazione di una distribuzione di Intune. A seconda dei requisiti aziendali, dell'infrastruttura esistente e della strategia di gestione dei dispositivi, alcune di queste attività potrebbero essere già state completate. Altre potrebbero non essere applicabili al piano.

### <a name="task-1-get-an-intune-subscription"></a>Attività 1: Ottenere una sottoscrizione di Intune

Come indicato in precedenza nella sezione relativa ai requisiti per Intune, è necessaria una sottoscrizione a EMS o Intune. Se l'organizzazione non dispone di una sottoscrizione, contattare Microsoft o il team dell'account Microsoft e comunicare il proprio interesse per l'acquisto di Enterprise Mobility + Security (EMS) o Intune.

- Altre informazioni su [come acquistare Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing).

### <a name="task-2-add-office-365-subscription"></a>Attività 2: Aggiungere l'abbonamento a Office 365

Questo passaggio è facoltativo. Se si prevede di usare Exchange Online e di gestire app Office Mobile con i criteri di protezione delle app, è necessaria una sottoscrizione Office 365. Se l'organizzazione non dispone di una sottoscrizione Office 365, contattare Microsoft o il team dell'account Microsoft e comunicare il proprio interesse per l'acquisto di Office 365.

- Altre informazioni su [come acquistare Office 365](https://products.office.com/business/compare-office-365-for-business-plans).

### <a name="task-3-add-users-groups-in-azure-ad"></a>Attività 3: Aggiungere gruppi di utenti in Azure AD

Potrebbe essere necessario aggiungere utenti o gruppi di sicurezza in Active Directory o Azure Active Directory, in base agli scenari per i casi d'uso e ai requisiti della distribuzione di Intune. Esaminare gli utenti e i gruppi di sicurezza correnti in Active Directory o Azure Active Directory e stabilire se soddisfano pienamente le proprie esigenze. Quando si aggiungono nuovi utenti e gruppi di sicurezza, è consigliabile aggiungerli in Active Directory ed eseguire la sincronizzazione con Azure Active Directory tramite Azure AD Connect.

- Altre informazioni su [come aggiungere utenti o gruppi in Intune](users-add.md).
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect--->


### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>Attività 4: Assegnare licenze utente di Intune e Office 365

A tutti gli utenti interessati dalla distribuzione di Office 365 ed EMS/Intune deve essere assegnata una licenza. È possibile assegnare licenze di EMS/Intune e Office 365 nell'interfaccia di amministrazione di Microsoft 365.

- Altre informazioni su [come assegnare le licenze di Intune](licenses-assign.md).

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>Attività 5: Impostare l'autorità di gestione di dispositivi mobili su Intune

Prima di iniziare a impostare, configurare, gestire e registrare i dispositivi con Intune, è necessario impostare l'autorità di gestione dei dispositivi su Intune.

- Altre informazioni su [come impostare l'autorità di gestione dei dispositivi](mdm-authority-set.md).

### <a name="task-6-enable-device-platforms"></a>Attività 6: Abilitare le piattaforme per i dispositivi

Per impostazione predefinita, è abilitata la maggior parte delle piattaforme per i dispositivi, ad eccezione dei dispositivi Apple (iOS e Mac). Per poter registrare e gestire in Intune i dispositivi iOS, è prima necessario abilitare la piattaforma del dispositivo. A tale scopo, è necessario creare un certificato push MDM Apple e aggiungerlo a Intune.

- Altre informazioni su [come abilitare i dispositivi Apple per la registrazione](../enrollment/apple-mdm-push-certificate-get.md).

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>Attività 7: Aggiungere e distribuire criteri di termini e condizioni

Intune supporta criteri di termini e condizioni. Aggiungere i criteri di termini e condizioni a seconda delle esigenze e distribuirli ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

- Altre informazioni su [come aggiungere e distribuire i criteri di termini e condizioni](../enrollment/terms-and-conditions-create.md).

### <a name="task-8-add-and-deploy-configuration-policies"></a>Attività 8: Aggiungere e distribuire criteri di configurazione

Intune supporta due tipi di criteri di configurazione: generali e personalizzati. Aggiungere i criteri di configurazione a seconda delle esigenze e distribuirli ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

- Altre informazioni su [come aggiungere e distribuire i criteri di configurazione](../configuration/device-profiles.md).

### <a name="task-9-add-and-deploy-resource-profiles"></a>Attività 9: Aggiungere e distribuire profili delle risorse

Intune supporta i profili di posta elettronica, Wi-Fi e VPN. Aggiungere questi profili a seconda delle esigenze e distribuirli ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

- Altre informazioni su [come abilitare l'accesso alle risorse aziendali con Intune](../configuration/device-profiles.md).

### <a name="task-10-add-and-deploy-apps"></a>Attività 10: Aggiungere e distribuire app

Intune supporta la distribuzione di app Web, line-of-business e di Store pubblici. È anche possibile gestire app in cui è integrato Intune SDK, associandole con i criteri di protezione delle app. Aggiungere le app a seconda delle esigenze e distribuirle ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

- Altre informazioni su [come aggiungere e distribuire app](../apps/app-management.md).

### <a name="task-11-add-and-deploy-compliance-policies"></a>Attività 11: Aggiungere e distribuire criteri di conformità

Intune supporta i criteri di conformità. Aggiungere i criteri di conformità a seconda delle esigenze e distribuirli ai gruppi di destinazione in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

- Altre informazioni sui [criteri di conformità](../protect/device-compliance-get-started.md).

### <a name="task-12-enable-conditional-access-policies"></a>Attività 12: Abilitare i criteri di accesso condizionale

Intune supporta l'accesso condizionale per Exchange Online, Exchange locale, SharePoint Online, Skype for Business Online e Dynamics CRM Online. Abilitare e configurare l'accesso condizionale a seconda delle esigenze, in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

- Altre informazioni sull'[accesso condizionale](../protect/conditional-access.md).

### <a name="task-13-enroll-devices"></a>Attività 13: Registrare i dispositivi

Intune supporta le piattaforme per dispositivi mobili iOS, Mac OS, Android, Windows desktop e Windows Mobile. Registrare le piattaforme per dispositivi mobili a seconda delle esigenze, in base ai casi d'uso e ai requisiti per la distribuzione di Intune.

- Altre informazioni su [come registrare i dispositivi](../enrollment/device-enrollment.md).


## <a name="next-steps"></a>Passaggi successivi
Vedere le indicazioni su [test e convalida della distribuzione di Intune](planning-guide-test-validation.md).
