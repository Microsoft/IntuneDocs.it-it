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
ms.sourcegitcommit: 206f7c927cce0b66cf554f60342f3f0b1ca43105
ms.openlocfilehash: d40687127841754f3994b8ad55e839e08bb8dd33


---

# Panoramica di Microsoft Intune App SDK
Intune App SDK è disponibile per la piattaforma iOS e Android e abilita le funzionalità di gestione di app per dispositivi mobili con Microsoft Intune. Un altro obiettivo è quello di ridurre la quantità di modifiche al codice necessarie per lo sviluppatore. La maggior parte delle funzionalità SDK possono infatti essere abilitate senza modificare il comportamento dell'app. Per un'esperienza avanzata per utenti finali e amministratori IT, è possibile usare le API per personalizzare il comportamento dell'app per le funzionalità che richiedono la partecipazione dell'app. 

Dopo avere abilitato l'app, gli amministratori IT possono distribuire i criteri alle app gestite da Intune e sfruttare queste funzionalità per proteggere i dati aziendali.

# Caratteristiche
## Controllare la capacità degli utenti di spostare documenti aziendali
Gli amministratori IT possono controllare lo spostamento di file di documenti aziendali nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio che impedisce alle app di backup dei file di eseguire il backup dei dati aziendali nel cloud.  

## Configurare le restrizioni per gli Appunti
Gli amministratori IT possono configurare il comportamento degli Appunti nelle app gestite da Intune. Ad esempio, è possibile distribuire un criterio che impedisca agli utenti finali di usare gli Appunti per tagliare/copiare da un'app gestita da Intune e incollare in un'app non gestita.

## Configurare le restrizioni per l'acquisizione dello schermo
Gli amministratori IT possono impedire agli utenti di acquisire la schermata se è visualizzata un'app gestita da Intune. L'applicazione di questa restrizione impedisce l'acquisizione e la divulgazione di contenuti aziendali riservati. Questa funzionalità è disponibile solo per i dispositivi Android. 

## Applicare la crittografia ai dati salvati
Gli amministratori IT possono applicare un criterio che assicura che i dati salvati nel dispositivo dall'app siano crittografati.

## Cancellare i dati aziendali da remoto
Gli amministratori IT possono cancellare i dati aziendali da un'app gestita da Intune quando viene annullata la registrazione del dispositivo in Microsoft Intune. Questa funzionalità è basata sull'identità ed elimina solo i file correlati all'identità aziendale dell'utente finale. A questo scopo, la funzionalità richiede la partecipazione dell'app. L'app può specificare l'identità per cui è necessario cancellare i dati sulla base delle impostazioni utente. Se nell'applicazione non sono presenti queste impostazioni utente specifiche, il comportamento predefinito prevede la cancellazione della directory dell'applicazione e l'invio di una notifica all'utente finale relativa alla rimozione dell'accesso alle risorse aziendali. 

## Imporre l'uso di un browser gestito
Gli amministratori IT possono imporre l'uso di un browser gestito quando vengono aperti collegamenti dalle app gestite da Intune. L'uso di un browser gestito da Microsoft Intune contribuisce a garantire che i collegamenti visualizzati nei messaggi di posta elettronica (che si trovano in un client di posta elettronica gestito da Intune) restino all'interno del dominio delle app gestite da Intune.

## Applicare un criterio PIN
Gli amministratori IT possono applicare un criterio PIN quando viene avviata un'app gestita da Intune. Questo criterio consente di verificare che gli utenti finali che hanno registrato i propri dispositivi in Microsoft Intune siano le stesse persone che stanno avviando le app. Quando gli utenti finali configurano il PIN, Intune App SDK usa Azure Active Directory per verificare le credenziali degli utenti finali a fronte delle credenziali di registrazione del dispositivo. 

## Richiedere agli utenti di immettere le credenziali prima di avviare le app
Gli amministratori IT possono richiedere agli utenti finali di immettere le proprie credenziali per avviare un'app gestita da Intune. Intune App SDK usa Azure Active Directory per fornire un'esperienza Single Sign-On, in cui le credenziali vengono immesse una sola volta e riutilizzate per gli accessi successivi. È supportata anche l'autenticazione di soluzioni di gestione delle identità [federate con Azure Active Directory](/active-directory/active-directory-aadconnect-federation-compatibility). 

## Verificare la conformità e l'integrità dei dispositivi
Gli amministratori IT possono controllare l'integrità del dispositivo e la sua conformità ai criteri aziendali prima che gli utenti finali accedano alle app gestite da Intune. Nella piattaforma iOS questo criterio controlla se il dispositivo è jailbroken. Nella piattaforma Android questo criterio controlla se il dispositivo è rooted.  





<!--HONumber=Jul16_HO3-->


