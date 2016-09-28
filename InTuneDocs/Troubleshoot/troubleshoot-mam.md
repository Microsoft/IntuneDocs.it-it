---
title:
- Risolvere i problemi relativi alla gestione di applicazioni mobili | Microsoft Intune
description: 
keywords: 
author: karaman
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: 9cfb3694b2fae919fd0554a6e21b497cdcf19c72
ms.openlocfilehash: f33e8de82ee07bb4571a5bfaff63af72f9086376


---

# Risolvere i problemi relativi alla gestione di applicazioni mobili

In presenza di problemi relativi alla gestione delle applicazioni mobili, è possibile iniziare da qui. Questo argomento descrive alcuni problemi comuni e le relative soluzioni.


**Problema:** i criteri MAM senza registrazione dalla console di Azure non vengono applicati all'app Skype for Business in dispositivi iOS e Android.

Soluzione: è necessario configurare Skype for Business per l'autenticazione moderna.  Per configurare l'autenticazione moderna per Skype, seguire le istruzioni in [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Abilitare il tenant per l'autenticazione moderna).

**Problema:** i criteri MAM senza registrazione non vengono applicati ad alcuna app di Office supportata[https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners] per alcun utente.
 
Soluzione: verificare che l'utente abbia la licenza per Intune.  

**Problema:** l'utente amministratore IT non riesce a configurare i criteri MAM nel portale di Azure

Soluzione: i ruoli seguenti hanno accesso al portale di Azure:

- Amministratore globale, configurabile nel [portale di Office](http://portal.office.com/)
- Proprietario, configurabile nel [portale di Office](https://portal.azure.com/)
- Collaboratore, configurabile nel [portale di Office](https://portal.azure.com/)

Per informazioni sulla configurazione di questi ruoli, vedere [Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). 

**Problema:** il report sulle app non include utenti selezionati di recente come destinazione di criteri MAM.

Soluzione: se un utente è stato selezionato di recente come destinazione di criteri MAM, possono trascorrere fino a 24 ore prima che l'utente compaia nei report come utente di destinazione. 

**Problema:** per l'applicazione di modifiche o aggiornamenti dei criteri possono essere richieste fino a 8 ore.  

Soluzione: l'utente finale può disconnettersi dall'app e rieseguire l'accesso per forzare la sincronizzazione con il servizio.  

**Problema:** i criteri MAM non vengono applicati ai dispositivi DEP di Apple

Soluzione: assicurarsi di usare l'affinità utente con il programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple. L'affinità utente è obbligatoria per qualsiasi app che richiede l'autenticazione utente nell'ambito del programma DEP.
Per altre informazioni sulla registrazione al programma DEP iOS, vedere [Registrare i dispositivi iOS di proprietà dell'azienda usando il programma di registrazione dispositivi (DEP)](https://docs.microsoft.com/en-us/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune).


### Vedere anche
- [Convalidare la configurazione dei criteri di gestione delle applicazioni mobili](https://docs.microsoft.com/en-us/intune/deploy-use/validate-mobile-application-management)
- [Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 





<!--HONumber=Sep16_HO2-->


