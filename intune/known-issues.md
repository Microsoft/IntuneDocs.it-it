---
title: Problemi noti nell&quot;anteprima di Microsoft Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: Informazioni sui problemi noti in anteprima'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 36b35e5311f6262c545a266003fb72b2febb277c
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Problemi noti nell'anteprima di Microsoft Intune


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


Usare questo argomento per informazioni sui problemi noti in anteprima di Intune.

Per segnalare un bug non elencato qui, [aprire una richiesta di supporto](https://docs.microsoft.com/intune-classic/troubleshoot/get-support).

Per richiedere l'aggiunta di una nuova funzionalità a Intune, è possibile generare un report nel nostro sito [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>I gruppi creati da Intune durante la migrazione potrebbero influire sulle funzionalità di altri prodotti Microsoft

Quando si esegue la migrazione da Intune classico al portale di Azure, si potrebbe notare un nuovo gruppo denominato **Tutti gli utenti - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Tenere presente che questo gruppo contiene tutti gli utenti di Azure Active Directory e non solo gli utenti con licenza per Intune. Se si prevede che alcuni utenti nuovi o esistenti non diventino membri di alcun gruppo, ciò potrebbe causare problemi con altri prodotti Microsoft.

### <a name="altering-groups-created-by-intune-during-migration-will-delay-migration"></a>La modifica di gruppi creati da Intune durante la migrazione ritarderà la migrazione

In preparazione della migrazione, i gruppi vengono copiati da Intune ad Azure AD. Qualsiasi modifica apportata successivamente nel portale classico di Intune verrà aggiornata nel gruppo di Azure AD. Tuttavia, qualsiasi modifica apportata in Azure AD non verrà sincronizzata nella console di Intune classica. Ciò potrebbe causare l'esito negativo della migrazione al portale di Azure e ritardi per la migrazione.

### <a name="compliance-policies-from-intune-will-not-show-up-in-new-console"></a>I criteri di conformità da Intune non verranno visualizzati nella nuova console

Gli eventuali criteri di conformità creati nel portale di Intune classico vengono inclusi nella migrazione, ma non vengono visualizzati nel portale di Azure. Ciò è dovuto a modifiche di progettazione nel portale di Azure. I criteri di conformità creati nel portale di Intune classico vengono ancora applicati, ma è necessario visualizzarli e modificarli nel portale classico.
Inoltre, i nuovi criteri di conformità creati nel portale di Azure non saranno visibili nel portale classico.
Per altre informazioni, vedere [Che cos'è la conformità dei dispositivi?](device-compliance.md).




### <a name="administration-and-accounts"></a>Amministrazione e account

Gli amministratori globali, noti anche come amministratori tenant, possono continuare a eseguire attività di ordinaria amministrazione senza una licenza separata di Intune o Enterprise Mobility Suite (EMS). Tuttavia, se gli amministratori globali vogliono usare il servizio, ad esempio per registrare il proprio dispositivo, un dispositivo aziendale oppure usare il portale aziendale di Intune, avranno bisogno di una licenza Intune o EMS, esattamente come qualsiasi altro utente.

### <a name="apple-enrollment-profile-migration"></a>Migrazione dei profili di registrazione di Apple
Nei prossimi mesi Intune consentirà di gestire le registrazioni di Apple Device Enrollment Program e Apple Configurator tramite il nuovo portale di Azure. Se si elimina il token di Apple Device Enrollment Program e non si carica un token aggiornato, quello originale verrà ripristinato nel nuovo portale di Azure come parte della migrazione dell'account di Intune. Per rimuovere questo token e impedire la registrazione di DEP, è sufficiente eliminare il token nel portale di Azure. 

### <a name="rbac-for-apple-corporate-owned-device-enrollment"></a>Controllo degli accessi in base al ruolo per la registrazione di dispositivi Apple di proprietà dell'azienda
Per eseguire le attività di registrazione Apple DEP e Apple Configurator sono necessari i ruoli di tenant o amministratore del servizio di Azure AD nonostante il fatto che le autorizzazioni di controllo degli accessi in base al ruolo sino elencate e disponibili nel ruolo utente personalizzato. Il supporto del ruolo Controllo degli accessi in base al ruolo per queste funzionalità verrà annunciato in futuro.

