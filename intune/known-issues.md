---
title: Problemi noti in Microsoft Intune
titlesuffix: Microsoft Intune
description: Informazioni sui problemi noti in Microsoft Intune.
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02efc7e2369c590e2d21ac8c27db54ffbaae38c1
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="known-issues-in-microsoft-intune"></a>Problemi noti in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Usare questo argomento per informazioni sui problemi noti in Microsoft Intune.

Per segnalare un bug non elencato qui, [aprire una richiesta di supporto](get-support.md).

Per richiedere una nuova funzionalità per Intune, è possibile compilare un report nel sito [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) di Microsoft.

## <a name="migration"></a>Migrazione

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Le funzionalità del client PC legacy Intune sono disponibili solo nella console di Silverlight

La possibilità di gestire Windows 10 in Intune nel portale di Azure è disponibile tramite la registrazione MDM di Windows. Per altre informazioni, vedere [Intune nella console di Azure e nel client PC Intune legacy](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>I gruppi creati da Intune durante la migrazione potrebbero influire sulle funzionalità di altri prodotti Microsoft

Quando si esegue la migrazione da Intune al portale di Azure, si potrebbe notare un nuovo gruppo denominato **Tutti gli utenti - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Questo gruppo contiene tutti gli utenti di Azure Active Directory e non solo gli utenti con licenza per Intune. Se si prevede che alcuni utenti nuovi o esistenti non diventino membri di alcun gruppo, ciò potrebbe causare problemi con altri prodotti Microsoft.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>I pannelli di stato per i criteri migrati non funzionano

Non è possibile visualizzare informazioni di stato per i criteri di cui è stata eseguita la migrazione dal portale classico al portale di Azure. È comunque possibile continuare a visualizzare i report per questi criteri nel portale classico. Per visualizzare informazioni di stato per i criteri di configurazione migrati, ricrearli nel portale di Azure.

## <a name="apps"></a>App

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>Le app iOS acquistate con Volume Purchase Program sono disponibili solo nella lingua del tenant di Intune predefinita
Le app iOS acquistate con volume Purchase Program sono visualizzate e possono essere assegnate solo per lo stesso codice paese dell'account di Intune. Intune sincronizza solo le app con le stesse impostazioni locali di iTunes del codice di paese dell'account del tenant di Intune. Ad esempio, se si acquista un'app che è disponibile solo nello store degli Stati Uniti e il proprio account di Intune è tedesco, Intune non visualizza l'app.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>Vengono caricate più copie dello stesso programma iOS acquistato con volume Purchase Program
Non fare clic sul pulsante **Carica** più volte per lo stesso token VPP. Se si fa clic più volte verranno caricati token VPP duplicati e le app verranno sincronizzate più volte per lo stesso token VPP.


<!-- ## Groups -->

## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Non è possibile salvare criteri di Windows Information Protection per alcuni dispositivi

Per i dispositivi non registrati in Intune, è possibile specificare solo un dominio primario nel campo **Identità aziendale** nelle impostazioni per criteri di Windows Information Protection.
Non sarà possibile salvare il criterio se si aggiungono altri domini tramite**Impostazioni avanzate** > **Perimetro di rete** > **Add a protected domain** (Aggiungi dominio protetto). Il messaggio di errore visualizzato verrà sostituito a breve da un messaggio più dettagliato.

### <a name="cisco-anyconnect-vpn-client-support"></a>Supporto del client VPN Cisco AnyConnect

La versione più recente del client VPN Cisco AnyConnect (4.0.07072) non è attualmente compatibile con Intune.
Un aggiornamento futuro di Intune includerà la compatibilità con questa versione del client VPN. Fino ad allora, si consiglia di non aggiornare il client VPN Cisco AnyConnect e di continuare a usare la versione esistente.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Uso del tipo di password numerica con i dispositivi macOS Sierra

Attualmente, se si seleziona l'opzione **Numerica** per **Tipo di password richiesto** in un profilo di restrizioni per i dispositivi macOS Sierra, il tipo applicato è **Alfanumerica**. Se si vuole usare una password numerica con questi dispositivi, non configurare questa impostazione.
Questo problema potrebbe essere corretto in una versione futura di macOS.

Per altre informazioni su queste impostazioni, vedere [Impostazioni relative alle restrizioni dei dispositivi macOS in Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Conformità

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>I criteri di conformità da Intune non vengono visualizzati nella nuova console

I criteri di conformità creati nel portale di Intune classico vengono inclusi nella migrazione, ma non vengono visualizzati nel portale di Azure a causa di modifiche della progettazione nel portale di Azure. I criteri di conformità creati nel portale classico di Intune vengono ancora applicati, ma è necessario visualizzarli e modificarli nel portale classico.

Inoltre, i nuovi criteri di conformità creati nel portale di Azure non sono visibili nel portale classico.

Per altre informazioni, vedere [Che cos'è la conformità dei dispositivi?](device-compliance.md).

<!-- ## Enrollment -->


## <a name="data-protection"></a>Protezione dati

### <a name="ios-app-protection-policies"></a>Criteri di protezione delle app iOS

È possibile definire i [criteri di protezione delle app per iOS](app-protection-policy-settings-ios.md) disponibili per gli utenti nei dispositivi gestiti tramite una soluzione di gestione delle app per dispositivi mobili (MAM) senza registrazione. A causa di un errore temporaneo, è possibile definire questi criteri solo per le versioni di iOS con una sola cifra decimale e non con più cifre decimali. Anziché impostare una versione minima di iOS 10.3.1, è possibile impostare iOS 10.3. Questo errore verrà risolto a breve con un aggiornamento a iOS SDK.


## <a name="administration-and-accounts"></a>Amministrazione e account

Gli amministratori globali, noti anche come amministratori tenant, possono continuare a eseguire attività di ordinaria amministrazione senza una licenza separata di Intune o Enterprise Mobility Suite (EMS). Tuttavia, per usare il servizio, ad esempio per registrare il proprio dispositivo, un dispositivo aziendale oppure usare il portale aziendale di Intune, hanno bisogno di una licenza per Intune o EMS.

<!-- ## Additional items -->
