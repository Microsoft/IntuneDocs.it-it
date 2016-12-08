---
title: Panoramica di Microsoft Intune App SDK | Microsoft Intune
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 4cb153c601b83b113a22b2acf3da5200cdb70472


---

# <a name="overview-of-the-microsoft-intune-app-sdk"></a>Panoramica di Microsoft Intune App SDK
Intune App SDK è disponibile per le piattaforme iOS e Android e abilita le funzionalità di gestione di app per dispositivi mobili con Microsoft Intune. Contribuisce inoltre a ridurre la quantità di modifiche che lo sviluppatore deve apportare al codice.

La maggior parte delle funzionalità SDK possono infatti essere abilitate senza modificare il comportamento dell'app. Per assicurare un'esperienza avanzata agli utenti finali e agli amministratori IT, è possibile usare le API per personalizzare il comportamento dell'app riguardo alle funzionalità che richiedono la partecipazione dell'app stessa.

Dopo avere abilitato l'app, gli amministratori IT possono distribuire i criteri alle app gestite da Intune e sfruttare queste funzionalità per proteggere i dati aziendali.

# <a name="features"></a>Caratteristiche
## <a name="control-users-ability-to-move-corporate-documents"></a>Controllare la capacità degli utenti di spostare documenti aziendali
Gli amministratori IT possono controllare lo spostamento di file di documenti aziendali nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio che impedisce alle app di backup dei file di eseguire il backup dei dati aziendali nel cloud.  

## <a name="configure-clipboard-restrictions"></a>Configurare le restrizioni per gli Appunti
Gli amministratori IT possono configurare il comportamento degli Appunti nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio che impedisca agli utenti finali di usare gli Appunti per tagliare o copiare da un'app gestita da Intune e incollare in un'app non gestita.

## <a name="enforce-encryption-on-saved-data"></a>Applicare la crittografia ai dati salvati
Gli amministratori IT possono applicare un criterio che assicura che i dati salvati nel dispositivo dall'app siano crittografati.

## <a name="remotely-wipe-corporate-data"></a>Cancellare i dati aziendali da remoto
Gli amministratori IT possono cancellare i dati aziendali da un'app gestita da Intune quando viene annullata la registrazione del dispositivo in Microsoft Intune. Questa funzionalità è basata sull'identità ed elimina solo i file correlati all'identità aziendale dell'utente finale. A questo scopo, la funzionalità richiede la partecipazione dell'app. L'app può specificare l'identità per cui è necessario cancellare i dati sulla base delle impostazioni utente. Se nell'applicazione non sono presenti queste impostazioni utente specifiche, il comportamento predefinito prevede la cancellazione della directory dell'applicazione e l'invio di una notifica all'utente finale relativa alla rimozione dell'accesso alle risorse aziendali.

## <a name="enforce-the-use-of-a-managed-browser"></a>Imporre l'uso di un browser gestito
Gli amministratori IT possono imporre l'uso di un browser gestito quando gli utenti aprono collegamenti dalle app gestite da Intune. L'uso da parte degli utenti di un browser gestito da Microsoft Intune contribuisce a garantire che i collegamenti visualizzati nei messaggi di posta elettronica in un client di posta elettronica gestito da Intune restino all'interno del dominio delle app gestite da Intune.

## <a name="enforce-a-pin-policy"></a>Applicare un criterio PIN
Gli amministratori IT possono applicare un criterio PIN quando viene avviata un'app gestita da Intune. Questo criterio consente di verificare che gli utenti finali che hanno registrato i propri dispositivi in Microsoft Intune siano le stesse persone che stanno avviando le app. Quando gli utenti finali configurano il PIN, Intune App SDK usa Azure Active Directory per verificare le loro credenziali rispetto alle credenziali di registrazione del dispositivo.

## <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>Richiedere agli utenti di immettere le credenziali prima di avviare le app
Gli amministratori IT possono richiedere agli utenti finali di immettere le proprie credenziali prima di avviare un'app gestita da Intune. Intune App SDK usa Azure Active Directory per fornire un'esperienza Single Sign-On. Questo significa che le credenziali vengono immesse una sola volta e riutilizzate per gli accessi successivi. Intune App SDK supporta anche l'autenticazione di soluzioni di gestione delle identità [federate con Azure Active Directory](/active-directory/active-directory-aadconnect-federation-compatibility).

## <a name="check-device-health-and-compliance"></a>Verificare la conformità e l'integrità dei dispositivi
Gli amministratori IT possono controllare l'integrità del dispositivo e la sua conformità ai criteri aziendali prima che gli utenti finali accedano alle app gestite da Intune. Nella piattaforma iOS questo criterio controlla se il dispositivo è jailbroken. Nella piattaforma Android questo criterio controlla se il dispositivo è rooted.  



<!--HONumber=Nov16_HO5-->


