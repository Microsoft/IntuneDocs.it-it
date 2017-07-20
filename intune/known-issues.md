---
title: Problemi noti di Microsoft Intune in Azure
titleSuffix: Intune on Azure
description: Informazioni sui problemi noti in Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4fda224613d8b69be82ef7f9681ba9165be33e52
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="known-issues-in-microsoft-intune"></a>Problemi noti in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Usare questo argomento per informazioni sui problemi noti in Microsoft Intune.

Per segnalare un bug non elencato qui, [aprire una richiesta di supporto](get-support.md).

Per richiedere una nuova funzionalità per Intune, è possibile compilare un report nel sito [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) di Microsoft.

## <a name="migration"></a>Migrazione

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>I gruppi creati da Intune durante la migrazione potrebbero influire sulle funzionalità di altri prodotti Microsoft

Quando si esegue la migrazione da Intune classico ad Azure, si potrebbe notare un nuovo gruppo denominato **Tutti gli utenti - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Questo gruppo contiene tutti gli utenti di Azure Active Directory e non solo gli utenti con licenza per Intune. Se si prevede che alcuni utenti nuovi o esistenti non diventino membri di alcun gruppo, ciò potrebbe causare problemi con altri prodotti Microsoft.

### <a name="secondary-migration-required-for-select-capabilities"></a>Migrazione secondaria necessaria per alcune funzionalità

È necessario eseguire la migrazione degli account di Intune creati prima di gennaio 2017 prima di poter usare queste funzionalità nel portale di Azure:

- Profili di registrazione di dispositivo aziendale
- Programma di registrazione del dispositivo mobile di Apple:
- Dispositivi aziendali preregistrati in base al gruppo di numero di serie iOS
- Manager di registrazione dispositivi
- Volume Purchase Program di Apple

Dato che queste funzionalità non possono essere gestite sia dalla console classica Silverlight che dalla console di Azure, la migrazione:
- Le disabilita nella console classica
- Le abilita nella console di Azure.  

Se queste funzionalità di Intune sono attualmente gestite nel portale di Azure, tenere presente quanto segue:

#### <a name="removes-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Rimozione dei profili di registrazione di dispositivi aziendali nel programma DEP di Apple
Il portale di Azure non supporta un profilo di registrazione di dispositivi aziendali predefinito per dispositivi DEP (Device Enrollment Program) di Apple. Questa funzionalità, disponibile nella console di Intune Silverlight classica, è stata sospesa per evitare che i profili venissero assegnati involontariamente. Quando i numeri di serie DEP vengono sincronizzati nel portale di Azure, non viene assegnato alcun profilo di registrazione di dispositivi aziendali. È necessario assegnare un profilo di registrazione prima di usare il dispositivo.

#### <a name="apple-dep-token-restored-with-migration"></a>Token DEP Apple ripristinato con la migrazione

Se è stato eliminato un token DEP (Device Enrollment Program) Apple nel portale di Intune classico (Silverlight) e non si carica un nuovo token, quello originale viene ripristinato nel portale di Azure durante la migrazione. Per rimuovere il token e impedire la registrazione DEP, eliminare il token dal portale di Azure.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>I pannelli di stato per i criteri migrati non funzionano

Non è possibile visualizzare informazioni di stato per i criteri di cui è stata eseguita la migrazione dal portale classico al portale di Azure. È comunque possibile continuare a visualizzare i report per questi criteri nel portale classico.
Per visualizzare informazioni di stato per i criteri di configurazione migrati, ricrearli nel portale di Azure.

## <a name="apps"></a>App

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>Le app iOS acquistate con Volume Purchase Program sono disponibili solo nella lingua del tenant di Intune predefinita
Le app iOS acquistate con volume Purchase Program sono visualizzate e possono essere assegnate solo per lo stesso codice paese dell'account di Intune. Intune sincronizza solo le app con le stesse impostazioni locali di iTunes del codice di paese dell'account del tenant di Intune. Ad esempio, se si acquista un'app che è disponibile solo nello store degli Stati Uniti e il proprio account di Intune è in lingua tedesca, Intune non visualizza l'app.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>Vengono caricate più copie dello stesso programma iOS acquistato con volume Purchase Program
Non fare clic sul pulsante **Carica** più volte per lo stesso token VPP. Se si fa clic più volte verranno caricati token VPP duplicati e le app verranno sincronizzate più volte per lo stesso token VPP. 

<!-- ## Groups -->

## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Non è possibile salvare criteri di Windows Information Protection per alcuni dispositivi

Per i dispositivi non registrati in Intune, è possibile specificare solo un dominio primario nel campo **Identità aziendale** nelle impostazioni per criteri di Windows Information Protection.
Non sarà possibile salvare il criterio se si aggiungono altri domini tramite**Impostazioni avanzate** > **Perimetro di rete** > **Add a protected domain** (Aggiungi dominio protetto). Il messaggio di errore visualizzato verrà sostituito a breve da un messaggio più dettagliato.

### <a name="cisco-anyconnect-vpn-client-support"></a>Supporto del client VPN Cisco AnyConnect
 
La versione più recente del client VPN Cisco AnyConnect (4.0.07072) non è attualmente compatibile con Intune. Un aggiornamento futuro di Intune includerà la compatibilità con questa versione del client VPN. Fino ad allora, si consiglia di non aggiornare il client VPN Cisco AnyConnect e di continuare a usare la versione esistente.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Uso del tipo di password numerica con i dispositivi macOS Sierra

Attualmente, se si seleziona l'opzione **Numerica** per **Tipo di password richiesto** in un profilo di restrizioni per i dispositivi macOS Sierra, il tipo applicato è **Alfanumerica**. Se si vuole usare una password numerica con questi dispositivi, non configurare questa impostazione.
Questo problema potrebbe essere corretto in una versione futura di macOS.

Per altre informazioni su queste impostazioni, vedere [Impostazioni relative alle restrizioni dei dispositivi macOS in Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Conformità

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>I criteri di conformità da Intune non vengono visualizzati nella nuova console

I criteri di conformità creati nel portale di Intune classico vengono inclusi nella migrazione, ma non vengono visualizzati nel portale di Azure a causa di modifiche della progettazione nel portale di Azure. I criteri di conformità creati nel portale di Intune classico vengono ancora applicati, ma è necessario visualizzarli e modificarli nel portale di Intune classico.
Inoltre, i nuovi criteri di conformità creati nel portale di Azure non sono visibili nel portale di Intune classico.

Per altre informazioni, vedere [Che cos'è la conformità dei dispositivi?](device-compliance.md).

<!-- ## Enrollment -->


<!-- ## Data protection -->


## <a name="administration-and-accounts"></a>Amministrazione e account

Gli amministratori globali, noti anche come amministratori tenant, possono continuare a eseguire attività di ordinaria amministrazione senza una licenza separata di Intune o Enterprise Mobility Suite (EMS). Tuttavia, per usare il servizio, ad esempio per registrare il proprio dispositivo, un dispositivo aziendale oppure usare il portale aziendale di Intune, hanno bisogno di una licenza per Intune o EMS.

<!-- ## Additional items -->












 
