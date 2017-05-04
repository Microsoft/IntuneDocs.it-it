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
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 08e2f65bcd600489f6599d37e5ef56c205176cd7
ms.lasthandoff: 04/25/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Problemi noti nell'anteprima di Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Usare questo argomento per informazioni sui problemi noti in anteprima di Intune.

Per segnalare un bug non elencato qui, [aprire una richiesta di supporto](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

Per richiedere l'aggiunta di una nuova funzionalità a Intune, è possibile generare un report nel nostro sito [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>I gruppi creati da Intune durante la migrazione potrebbero influire sulle funzionalità di altri prodotti Microsoft

Quando si esegue la migrazione da Intune classico al portale di Azure, si potrebbe notare un nuovo gruppo denominato **Tutti gli utenti - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Tenere presente che questo gruppo contiene tutti gli utenti di Azure Active Directory e non solo gli utenti con licenza per Intune. Se si prevede che alcuni utenti nuovi o esistenti non diventino membri di alcun gruppo, ciò potrebbe causare problemi con altri prodotti Microsoft.

### <a name="altering-groups-created-by-intune-during-migration-will-delay-migration"></a>La modifica di gruppi creati da Intune durante la migrazione ritarderà la migrazione

In preparazione della migrazione, i gruppi vengono copiati da Intune ad Azure AD. Qualsiasi modifica apportata successivamente nel portale classico di Intune verrà aggiornata nel gruppo di Azure AD. Tuttavia, qualsiasi modifica apportata in Azure AD non verrà sincronizzata nella console di Intune classica. Ciò potrebbe causare l'esito negativo della migrazione al portale di Azure e ritardi per la migrazione.

### <a name="compliance-policies-from-intune-will-not-show-up-in-new-console"></a>I criteri di conformità da Intune non verranno visualizzati nella nuova console 

Gli eventuali criteri di conformità creati nel portale di Intune classico vengono inclusi nella migrazione, ma non vengono visualizzati nel portale di Azure. Ciò è dovuto a modifiche di progettazione nel portale di Azure. I criteri di conformità creati nel portale di Intune classico vengono ancora applicati, ma è necessario visualizzarli e modificarli nel portale classico.
Inoltre, i nuovi criteri di conformità creati nel portale di Azure non saranno visibili nel portale classico.
Per altre informazioni, vedere [Che cos'è la conformità dei dispositivi?](https://docs.microsoft.com/intune-azure/set-device-compliance/what-is-device-compliance).




### <a name="administration-and-accounts"></a>Amministrazione e account

Gli amministratori globali, noti anche come amministratori tenant, possono continuare a eseguire attività di ordinaria amministrazione senza una licenza separata di Intune o Enterprise Mobility Suite (EMS). Tuttavia, se gli amministratori globali vogliono usare il servizio, ad esempio per registrare il proprio dispositivo, un dispositivo aziendale oppure usare il portale aziendale di Intune, avranno bisogno di una licenza Intune o EMS, esattamente come qualsiasi altro utente.

### <a name="apple-enrollment-profile-migration"></a>Migrazione dei profili di registrazione di Apple
Nei prossimi mesi Intune consentirà di gestire le registrazioni di Apple Device Enrollment Program e Apple Configurator tramite il nuovo portale di Azure. Se si elimina il token di Apple Device Enrollment Program e non si carica un token aggiornato, quello originale verrà ripristinato nel nuovo portale di Azure come parte della migrazione dell'account di Intune. Per rimuovere questo token e impedire la registrazione di DEP, è sufficiente eliminare il token nel portale di Azure. 

