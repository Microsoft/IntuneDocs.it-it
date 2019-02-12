---
title: Evitare perdite di dati nei dispositivi non gestiti
titlesuffix: Microsoft Intune
description: Consentire l'accesso ai dati aziendali nei dispositivi e proteggere i dati dalla divulgazione usando Microsoft Intune.
keywords: protezione dati impedire divulgazione dispositivo O365 Office 365
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fe1db753753c56ddb5ee6a71632f70a879c382c
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839924"
---
# <a name="prevent-data-leaks-on-non-managed-devices-using-microsoft-intune"></a>Evitare perdite di dati nei dispositivi non gestiti usando Microsoft Intune

Se si consente l'accesso ai dati aziendali ospitati in Office 365, è possibile stabilire il modo in cui gli utenti condividono e salvano i dati senza rischiare la divulgazione intenzionale o accidentale dei dati. In Microsoft Intune è possibile impostare criteri di protezione app per proteggere i dati aziendali presenti nei dispositivi personali degli utenti. Non è necessario che i dispositivi siano registrati nel servizio Intune. 

I criteri di protezione app impostati con Intune funzionano anche nei dispositivi gestiti con una soluzione di gestione non Microsoft. I dati personali nei dispositivi non vengono modificati, il reparto IT gestisce solo i dati aziendali. 

È possibile impostare criteri di protezione app per le app per dispositivi mobili di Office nei dispositivi che eseguono Windows, iOS o Android per proteggere i dati aziendali. Questi criteri consentono di impostare un PIN basato sulle app o la crittografia dei dati aziendali oppure impostazioni più avanzate per limitare l'uso delle funzionalità taglia, copia, incolla e salva con nome da parte degli utenti tra le app gestite e non gestite. È anche possibile cancellare i dati aziendali in remoto senza richiedere agli utenti di registrare i propri dispositivi. 

I criteri di protezione app di Intune sono indipendenti dalla gestione dei dispositivi. I criteri di protezione app consentono di gestire le app per dispositivi mobili di Office nei dispositivi non gestiti e in quelli gestiti da Intune, nonché nei dispositivi gestiti da soluzioni MDM non Microsoft. 

## <a name="before-you-begin"></a>Prima di iniziare

Il piano di azione descritto di seguito può essere usato quando sono soddisfatti i requisiti seguenti:
* L'azienda è pronta per eseguire la transizione al cloud in modo sicuro.
* L'azienda usa Office 365 Exchange Online, SharePoint Online, OneDrive for Business o Yammer.
* L'azienda ha le licenze per Microsoft 365, Enterprise Mobility + Security (EMS) o Azure Information Protection.
* L'azienda consente agli utenti di accedere ai dati aziendali da dispositivi Windows, iOS o Android aziendali o personali. 
* L'azienda non vuole richiedere la registrazione dei dispositivi personali in un servizio di gestione dei dispositivi. 

## <a name="action-plan"></a>Piano di azione

Per i dispositivi iOS e Android: 

1. Sapere come funzionano i [criteri di protezione app](app-protection-policy.md).
2. Scoprire come [creare e distribuire i criteri di protezione app](app-protection-policies.md) per le app per dispositivi mobili di Office. 
3. [Monitorare i criteri di protezione app](app-protection-policies-monitor.md) che si creano e si distribuiscono. 

Per i dispositivi Windows 10: 

1. Sapere [come funziona Windows Information Protection (WIP)](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip). 
2. Prepararsi alla configurazione dei [criteri di protezione app per Windows 10](app-protection-policies-configure-windows-10.md).
3. [Creare e distribuire criteri di protezione app WIP con Intune](windows-information-protection-policy-create.md).

## <a name="what-to-tell-employees-and-students"></a>Informazioni da comunicare a dipendenti e studenti

In base alle esigenze, condividere i collegamenti per consentire l'accesso ad altre informazioni: 
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)
* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md) 

## <a name="next-steps"></a>Passaggi successivi

Se si vuole ottenere assistenza per l'abilitazione di questi scenari o di altri scenari per EMS oppure Office 365 e sono disponibili almeno 150 licenze per Microsoft 365, Enterprise Mobility + Security o Azure Active Directory Premium, usare i propri [vantaggi FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 
