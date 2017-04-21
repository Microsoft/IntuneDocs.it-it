---
title: Impedire la divulgazione di dati aziendali da app di Office 365 per dispositivi mobili | Documentazione Microsoft
description: Usare Intune consente di proteggere i dati dell&quot;organizzazione tramite criteri di gestione delle app mobili (MAM) in grado di evitare la divulgazione di dati aziendali da app di Office 365 per dispositivi mobili o da altre app line-of-business (LOB).
keywords: 
author: jeffgilb
ms.author: jeffgilb
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 19be3de7-539c-49f5-8c46-5363b987fef9
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 4c13eb3149ea0cc21604a5a05445cfccdc984293
ms.lasthandoff: 04/14/2017


---

# <a name="quick-start-guide-prevent-company-data-leaks-from-office-365-mobile-apps"></a>Guida introduttiva: Impedire la divulgazione di dati aziendali da app di Office 365 per dispositivi mobili

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune aiuta a proteggere i dati dell'organizzazione usando criteri di gestione delle applicazioni mobili (MAM) che consentono di impedire la divulgazione di dati aziendali da app di Office 365 per dispositivi mobili o da altre app line-of-business (LOB). È possibile usare i criteri MAM di Intune senza che gli utenti finali debbano registrare i propri dispositivi nel software per la gestione dei dispositivi mobili (MDM) di Intune. Pertanto, se alcuni utenti non vogliono registrare i dispositivi mobili iOS o Android BYOD in una soluzione Microsoft MDM (Intune, Configuration Manager o EAS), se si desidera proteggere i dati aziendali senza gestire i dispositivi degli utenti finali o se si usa già una soluzione non Microsoft MDM, Intune è lo strumento ideale per aumentare la sicurezza dei dati della società.   

## <a name="is-this-quick-start-guide-right-for-me"></a>Questa guida introduttiva offre la soluzione adatta ai requisiti d'uso?
Le aziende vogliono consentire agli utenti finali di accedere ai dati delle app LOB e di Office 365 sui dispositivi iOS e Android senza che tali dispositivi debbano essere registrati in una soluzione MDM. Nel contempo, tuttavia, desiderano controllare le operazioni consentite e non consentite agli utenti, ad esempio quelle di copia e incolla in app personali.

Microsoft Intune consente di impostare criteri MAM per le app di Office 365 per dispositivi mobili su iOS e Android, incluse le limitazioni per le operazioni di taglia, copia e incolla, impedendo di eseguire il comando 'Salva con nome', impostare requisiti PIN e cancellare in remoto dati protetti MAM.  In questo modo, i dati aziendali risultano protetti senza che gli utenti debbano registrare i propri dispositivi in una soluzione MDM. Al tempo stesso, continua ad essere garantita un'eccezionale esperienza d'uso con le app di Office per dispositivi mobili.

## <a name="how-do-i-do-it"></a>In che modo procedere?
1.    Acquisire conoscenze di base sul funzionamento della [gestione di applicazioni mobili (MAM) di Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune).
2.    Scoprire i [passaggi da eseguire prima di creare i criteri MAM](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) nel portale di Azure.
3.    [Creare e distribuire i criteri MAM](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) con Intune.

### <a name="additional-information"></a>Informazioni aggiuntive:
- [Esperienza dell'utente finale](/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune) con app compatibili con MAM.
- [Preparare app LOB per MAM con Intune](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
- <a href="https://www.microsoft.com/cloud-platform/microsoft-intune-partners" target="_blank"> Elenco di partner di Microsoft Intune &rarr;</a> che forniscono app compatibili con MAM.

## <a name="what-should-i-do-next"></a>Operazioni successive
[Eseguire la migrazione da una soluzione MDM non Microsoft in Microsoft Intune](/intune/deploy-use/migrate-to-intune)

[Registrare dispositivi nella soluzione MDM Intune](/intune/deploy-use/enroll-devices-in-microsoft-intune)

