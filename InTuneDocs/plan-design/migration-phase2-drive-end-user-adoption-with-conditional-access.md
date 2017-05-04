---
title: Promuovere l&quot;adozione da parte degli utenti finali con l&quot;accesso condizionale | Microsoft Docs
description: "Lo scopo di questo articolo è fornire informazioni dettagliate su come sfruttare l&quot;accesso condizionale per promuovere la registrazione in Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 12584743534a76d0b2ce92e5de6cb5f916453938
ms.lasthandoff: 04/25/2017


---

# <a name="phase-2-drive-end-user-adoption-with-conditional-access"></a>Fase 2: Promuovere l'adozione da parte degli utenti finali con l'accesso condizionale

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Abilitare le funzionalità di accesso condizionale con Intune, ad esempio il blocco della posta elettronica per i dispositivi non registrati, può essere utile ai fini della registrazione e della conformità, ma non è obbligatorio per l'esito positivo di una migrazione. Il successo dipende dagli obiettivi e dai requisiti di sicurezza per l'adozione.

## <a name="migration-campaign-with-conditional-access"></a>Campagna di migrazione con accesso condizionale

Ecco un approccio tipico per ottimizzare una campagna di migrazione con accesso condizionale:

1.  Impostare le regole di accesso condizionale da applicare a tutti gli utenti, ma escludere specificamente gli utenti di cui è necessario eseguire la migrazione dal provider MDM precedente. È possibile creare un gruppo di utenti di Azure AD con tutti gli utenti esclusi dall'accesso condizionale.

2.  Man mano che gli utenti eseguono la migrazione, rimuoverli dal gruppo di esclusione dall'accesso condizionale.

3.  Al termine della migrazione, configurare tutti i criteri di accesso condizionale in modo che attivino il blocco per impostazione predefinita, a meno che Intune non consenta l'accesso.

### <a name="advantages"></a>Vantaggi

-   Controllo degli accessi per i nuovi account utente o gli account utente non gestiti dalla soluzione precedente.

-   Periodo di tolleranza per consentire agli utenti della soluzione precedente di completare la migrazione.

-   Perdita di produttività ridotta al minimo

### <a name="disadvantages"></a>Svantaggi

-   Gli utenti della soluzione precedente potrebbero riuscire potenzialmente ad accedere alle risorse usando dispositivi non gestiti fino a quando non viene abilitato l'accesso condizionale per tali utenti.

> [!TIP]
> Questo è solo uno dei tanti approcci disponibili. È possibile scegliere un processo più semplice che posticipa del tutto l'accesso condizionale fino al completamento della registrazione per tutte le fasi oppure un processo più rigido che impone l'accesso condizionale sin dall'inizio e richiede la conformità completa per tutti gli accessi.

-   Altre informazioni sull'[accesso condizionale](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access).

## <a name="task-list-for-conditional-access"></a>Elenco di attività per l'accesso condizionale

### <a name="task-1-get-ready-for-intune-conditional-access"></a>Attività 1: Prepararsi per l'accesso condizionale di Intune

-   Scoprire [come configurare l'accesso condizionale](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

### <a name="task-2-set-up-intune-conditional-access"></a>Attività 2: Configurare l'accesso condizionale di Intune

Scegliere uno dei tipi di criteri di accesso condizionale seguenti per altre informazioni:

-   [Exchange Online e nuovo Exchange Online dedicato](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)

-   [Exchange locale e Exchange Online dedicato legacy](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)

-   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

-   [Skype for Business Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)

-   [Dynamics CRM Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

-   [Scenari di accesso tramite posta elettronica di esempio](https://docs.microsoft.com/intune/deploy-use/restrict-email-access-example-scenarios)

## <a name="next-steps"></a>Passaggi successivi

[Fase 2: Ciclo di migrazione tipico](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)

