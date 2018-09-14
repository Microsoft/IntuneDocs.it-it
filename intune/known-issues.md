---
title: Problemi noti in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni sui problemi noti in Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 421eea460ee7c00b79a63a014291a8abb88ddaea
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347798"
---
# <a name="known-issues-in-microsoft-intune"></a>Problemi noti in Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare questo articolo per informazioni sui problemi noti in Microsoft Intune.

Per segnalare un bug non elencato qui, [aprire una richiesta di supporto](get-support.md).

Per richiedere una nuova funzionalità per Intune, è possibile compilare un report nel sito [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="migration"></a>Migrazione

### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal"></a>Esportare i criteri di conformità dal portale di Azure classico per ricrearli nel portale di Intune di Azure

I criteri di conformità creati nel portale di Azure classico saranno deprecati. È possibile rivedere ed eliminare i criteri di conformità esistenti ma non aggiornarli. Se è necessario eseguire la migrazione di criteri di conformità al portale di Intune di Azure, è possibile esportare i criteri come file con valori delimitati da virgole (file CSV). Quindi, usare i dettagli del file per ricreare i criteri nel portale di Intune di Azure.

> [!IMPORTANT]
> Quando il portale di Azure classico verrà ritirato, non sarà più possibile accedere ai criteri di conformità né visualizzarli. Assicurarsi quindi di esportarli e ricrearli nel portale di Azure prima che il portale di Azure classico venga ritirato.

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Le funzionalità del client PC legacy Intune sono disponibili solo nella console di Silverlight

La possibilità di gestire Windows 10 in Intune nel portale di Azure è disponibile tramite la registrazione MDM di Windows. Per altre informazioni, vedere [Intune nella console di Azure e nel client PC Intune legacy](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>I gruppi creati da Intune durante la migrazione potrebbero influire sulle funzionalità di altri prodotti Microsoft

Quando si esegue la migrazione da Intune al portale di Azure, si potrebbe notare un nuovo gruppo denominato **Tutti gli utenti - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Questo gruppo contiene tutti gli utenti di Azure Active Directory e non solo gli utenti con licenza per Intune. Se si prevede che alcuni utenti nuovi o esistenti non diventino membri di alcun gruppo, ciò potrebbe causare problemi con altri prodotti Microsoft.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>I pannelli di stato per i criteri migrati non funzionano

Non è possibile visualizzare informazioni di stato per i criteri di cui è stata eseguita la migrazione dal portale classico di Azure al portale di Azure. È comunque possibile continuare a visualizzare i report per questi criteri nel portale classico. Per visualizzare informazioni di stato per i criteri di configurazione migrati, ricrearli nel portale di Azure.

## <a name="apps"></a>App


### <a name="multiple-app-install-prompts-for-certain-vpp-apps"></a>Richieste di app VPP specifiche durante l'installazione di più app
L'installazione di più app può richiedere app VPP specifiche già installate nei dispositivi degli utenti finali. Questo problema si verifica se l'opzione **Aggiornamenti automatici delle app** è **attivata** per il token VPP caricato nel portale di Intune di Azure.    

Per aggirare questo problema, è possibile disabilitare l'opzione **Aggiornamenti automatici delle app** per il token VPP. A tale scopo, nel portale di Azure aprire Microsoft Intune. Da Intune selezionare **App client** > **Token VPP iOS**. Selezionare quindi il token VPP che ha distribuito l'app interessate e selezionare **Modifica** > **Aggiornamenti automatici delle app** > **No** >  **Salva**. In alternativa, è possibile interrompere la distribuzione dell'app interessata come app VPP. Questa operazione interrompe la visualizzazione delle richieste.    

Si tratta di un problema noto nella versione corrente. Sarà presto disponibile una correzione che risolverà il problema. Dopo l'implementazione della correzione, gli utenti non visualizzeranno più le richieste durante l'installazione di più app.

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>Le app iOS acquistate con Volume Purchase Program sono disponibili solo nella lingua del tenant di Intune predefinita
Le app iOS acquistate con volume Purchase Program sono visualizzate e possono essere assegnate solo per lo stesso codice paese dell'account di Intune. Intune sincronizza solo le app con le stesse impostazioni locali di iTunes del codice di paese dell'account del tenant di Intune. Ad esempio, se si acquista un'app che è disponibile solo in uno store degli Stati Uniti e il proprio account di Intune è tedesco, Intune non visualizza l'app.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>Vengono caricate più copie dello stesso programma iOS acquistato con volume Purchase Program
Non fare clic sul pulsante **Carica** più volte per lo stesso token VPP. Se si fa clic più volte verranno caricati token VPP duplicati e le app verranno sincronizzate più volte per lo stesso token VPP.

### <a name="some-managed-browser-traffic-not-routed-through-azure-app-proxy----2463492---"></a>Una parte del traffico di Managed Browser non viene instradata attraverso il proxy app di Azure <!-- 2463492 -->
Esiste un problema noto con l'integrazione di Managed Browser e del proxy app per cui traffico terziario specifico (ad esempio chiamate javascript o AJAX) non viene instradato attraverso il proxy app di Azure. Si tratta di un problema noto nella versione corrente.  

<!-- ## Groups -->

## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Non è possibile salvare criteri di Windows Information Protection per alcuni dispositivi

Per i dispositivi non registrati in Intune, è possibile specificare solo un dominio primario nel campo **Identità aziendale** nelle impostazioni per criteri di Windows Information Protection.
Non sarà possibile salvare il criterio se si aggiungono altri domini tramite**Impostazioni avanzate** > **Perimetro di rete** > **Add a protected domain** (Aggiungi dominio protetto). Il messaggio di errore visualizzato verrà sostituito a breve da un messaggio più dettagliato.

### <a name="cisco-anyconnect-and-cisco-legacy-anyconnect-vpn-client-support---ios"></a>Supporto per i client VPN Cisco AnyConnect e Cisco Legacy AnyConnect - iOS

Nei dispositivi iOS l'integrazione del controllo dell'accesso alla rete non funziona con il nuovo client Cisco AnyConnect. È in corso un'operazione congiunta con Cisco per attivare l'integrazione del controllo dell'accesso alla rete.

In [Creare profili VPN in Intune](vpn-settings-ios.md) sono disponibili informazioni più dettagliate sui client Cisco AnyConnect e Cisco Legacy AnyConnect.

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
