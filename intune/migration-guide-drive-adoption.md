---
title: Promuovere l'adozione da parte degli utenti finali con l'accesso condizionale
titleSuffix: Microsoft Intune
description: Informazioni su come usare l'accesso condizionale per la registrazione in Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40e78d85c215bbb5cc126705f26041ce4f7786f4
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549444"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Promuovere l'uso da parte degli utenti finali con l'accesso condizionale in Microsoft Intune

Abilitare le funzionalità di accesso condizionale con Intune, ad esempio il blocco della posta elettronica per i dispositivi non registrati, può essere utile ai fini della registrazione e della conformità, ma non è obbligatorio per l'esito positivo di una migrazione. Il successo dipende dagli obiettivi e dai requisiti di sicurezza per l'adozione.

## <a name="migration-campaign-with-conditional-access"></a>Campagna di migrazione con l'accesso condizionale

Ecco un approccio tipico per ottimizzare una campagna di migrazione con accesso condizionale:

1. Impostare le regole di accesso condizionale da applicare a tutti gli utenti, ma escludere specificamente gli utenti di cui è necessario eseguire la migrazione dal provider MDM precedente. È possibile creare un gruppo di utenti di Azure AD con tutti gli utenti esclusi dall'accesso condizionale.

2. Man mano che gli utenti eseguono la migrazione, rimuoverli dal gruppo di esclusione dall'accesso condizionale.

3. Al termine della migrazione, configurare tutti i criteri di accesso condizionale in modo che attivino il blocco per impostazione predefinita, a meno che Intune non consenta l'accesso.

### <a name="advantages"></a>Vantaggi

- Controllo degli accessi per i nuovi account utente o gli account utente non gestiti dalla soluzione precedente.

- Periodo di tolleranza per consentire agli utenti della soluzione precedente di completare la migrazione.

- Perdita di produttività ridotta al minimo

### <a name="disadvantages"></a>Svantaggi

- Gli utenti della soluzione precedente potrebbero riuscire potenzialmente ad accedere alle risorse usando dispositivi non gestiti fino a quando non viene abilitato l'accesso condizionale per tali utenti.


Questo è solo uno dei tanti approcci disponibili. È possibile scegliere un processo più semplice che posticipa del tutto l'accesso condizionale fino al completamento della registrazione per tutte le fasi oppure un processo più rigido che impone l'accesso condizionale sin dall'inizio e richiede la conformità completa per tutti gli accessi.

- Altre informazioni sull'[accesso condizionale](conditional-access.md).

## <a name="task-list-for-conditional-access"></a>Elenco di attività per l'accesso condizionale

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Attività 1: Decidere come si intende implementare l'accesso condizionale

[Modi comuni per usare l'accesso condizionale](conditional-access-intune-common-ways-use.md).

### <a name="task-2-set-up-intune-conditional-access"></a>Attività 2: Configurare l'accesso condizionale di Intune

Scegliere una delle seguenti opzioni:

- [Configurare l'accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

- [Installare On-premises Exchange Connector con Intune](exchange-connector-install.md)

- [Configurare criteri di accesso condizionale basato su app per Exchange Online](app-based-conditional-access-intune-create.md)

- [Configurare criteri di accesso condizionale basato su app per SharePoint Online](app-based-conditional-access-intune-create.md)

- [Bloccare le app che non usano l'autenticazione moderna (ADAL)](app-modern-authentication-block.md)

## <a name="next-steps"></a>Passaggi successivi

Informazioni sul [ciclo di migrazione tipico](migration-guide-cycle.md).
