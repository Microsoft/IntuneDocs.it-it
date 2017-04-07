---
title: Problemi noti nell&quot;anteprima di Microsoft Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: Informazioni sui problemi noti in anteprima'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: ec3f87994b19591bda4ec201eac3c839798d634c
ms.lasthandoff: 03/15/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Problemi noti nell'anteprima di Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Usare questo argomento per informazioni sui problemi noti in anteprima di Intune.

Per segnalare un bug non elencato qui, [aprire una richiesta di supporto](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

Per richiedere l'aggiunta di una nuova funzionalità a Intune, è possibile generare un report nel nostro sito [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="administration-and-accounts"></a>Amministrazione e account

- Gli amministratori globali, noti anche come amministratori tenant, possono continuare a eseguire attività di ordinaria amministrazione senza una licenza separata di Intune o Enterprise Mobility Suite (EMS). Tuttavia, se gli amministratori globali vogliono usare il servizio, ad esempio per registrare il proprio dispositivo, un dispositivo aziendale oppure usare il portale aziendale di Intune, avranno bisogno di una licenza Intune o EMS, esattamente come qualsiasi altro utente.

## <a name="apple-enrollment-profile-migration"></a>Migrazione dei profili di registrazione di Apple
- Nei prossimi mesi Intune consentirà di gestire le registrazioni di Apple Device Enrollment Program e Apple Configurator tramite il nuovo portale di Azure. Se si elimina il token di Apple Device Enrollment Program e non si carica un token aggiornato, quello originale verrà ripristinato nel nuovo portale di Azure come parte della migrazione dell'account di Intune. Per rimuovere questo token e impedire la registrazione di DEP, è sufficiente eliminare il token nel portale di Azure. 

