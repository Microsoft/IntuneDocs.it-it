---
title: Set di criteri
titleSuffix: Microsoft Intune
description: Usare i set di criteri per raggruppare raccolte di oggetti di gestione in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e539f44fc9c9b4e7382368c0f3ad9f79bb1c98b1
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585657"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>Usare i set di criteri per raggruppare raccolte di oggetti di gestione

I set di criteri consentono di creare aggregazioni di riferimenti a entità di gestione già esistenti che devono essere identificate, selezionate e monitorate come una singola unità concettuale. Un set di criteri è una raccolta assegnabile di app, criteri e altri oggetti di gestione creati. La creazione di un set di criteri consente di selezionare contemporaneamente molti oggetti diversi e di assegnarli da un'unica posizione. Con l'evolversi dell'organizzazione è possibile modificare un set di criteri per aggiungere o rimuovere i relativi oggetti e assegnazioni. È possibile usare un set di criteri per associare e assegnare oggetti esistenti, ad esempio app, criteri e VPN, in un unico pacchetto. 

> [!IMPORTANT]
> Per un elenco di problemi noti relativi ai set di criteri, vedere [Problemi noti relativi ai set di criteri](~/fundamentals/policy-sets.md#policy-sets-known-issues).

I set di criteri non sostituiscono concetti o oggetti esistenti. È possibile continuare ad assegnare singoli oggetti e anche fare riferimento a singoli oggetti come parte di un set di criteri. Pertanto, tutte le modifiche apportate ai singoli oggetti verranno rispecchiate nel set di criteri. 

È possibile usare i set di criteri per:

- Raggruppare gli oggetti che devono essere assegnati insieme
- Assegnare i requisiti minimi di configurazione dell'organizzazione in tutti i dispositivi gestiti
- Assegnare app di uso comune o pertinenti a tutti gli utenti

È possibile includere gli oggetti di gestione seguenti in un set di criteri:
- App
- Criteri di configurazione dell'app
- Criteri di protezione delle app
- Profili di configurazione dispositivo
- Criteri di conformità dei dispositivi
- Limitazioni del tipo di dispositivo
- Profili di distribuzione di Windows Autopilot
- Pagina Stato registrazione

Quando si crea un set di criteri, si crea una singola unità di assegnazione e si gestiscono le associazioni tra oggetti diversi. Un set di criteri sarà un riferimento a oggetti esterni. Eventuali modifiche apportate agli oggetti inclusi influenzeranno anche il set di criteri. Dopo aver creato un set di criteri, è possibile visualizzarne e modificarne ripetutamente gli oggetti e le assegnazioni. 

> [!NOTE]
> I set di criteri supportano le impostazioni di Windows, Android, macOS e iOS e possono essere assegnati tra piattaforme diverse.

## <a name="how-to-create-a-policy-set"></a>Come creare un set di criteri

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Nel pannello **Intune** scegliere **Set di criteri** > **Set di criteri** > **Crea**.
3. Nella pagina **Informazioni di base** aggiungere i valori seguenti:
    - **Nome set di criteri** - Specificare un nome per il set di criteri.
    - **Descrizione** - Specificare facoltativamente una descrizione per il set di criteri.
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. Fare clic su **Avanti: Gestione delle applicazioni**.<br>
   Nella pagina **Gestione delle applicazioni** e possibile aggiungere facoltativamente [app](~/apps/apps-add.md), [criteri di configurazione delle app](~/apps/app-configuration-policies-overview.md) e [criteri di protezione delle app](~/apps/app-protection-policy.md) al set di criteri. Per informazioni sulla gestione delle app, vedere [Informazioni sulla gestione delle app in Microsoft Intune](~/apps/app-management.md). 
5. Fare clic su **Avanti: Gestione dei dispositivi**.<br>
   La pagina **Gestione dei dispositivi** consente di aggiungere oggetti di gestione dei dispositivi al set di criteri, ad esempio [profili di configurazione dei dispositivi](~/configuration/device-profiles.md) e [criteri di conformità dei dispositivi](~/protect/device-compliance-get-started.md). Assicurarsi di includere tutti gli oggetti associati, ad esempio altri criteri, certificati e profili di baseline di sicurezza.
6. Fare clic su **Avanti: Registrazione del dispositivo**.<br>
   La pagina **Registrazione del dispositivo** consente di aggiungere oggetti di registrazione del dispositivo al set di criteri, ad esempio [limitazioni del tipo di dispositivo](~/enrollment/enrollment-restrictions-set.md), [profili di distribuzione di Windows Autopilot](~/enrollment/enrollment-autopilot.md) e [profili delle pagine di stato della registrazione](~/enrollment/windows-enrollment-status.md).
7. Fare clic su **Avanti: Assegnazioni**.<br>
   La pagina **Assegnazioni** consente di assegnare il set di criteri a utenti e dispositivi. Si noti che è possibile assegnare un set di criteri a un dispositivo indipendentemente dal fatto che il dispositivo sia gestito da Intune o meno.
8. Fare clic su **Avanti: Rivedi e crea** per verificare i valori immessi per il profilo.
9. Al termine, fare clic su **Crea** per creare il set di criteri in Intune. 

## <a name="policy-sets-known-issues"></a>Problemi noti relativi ai set di criteri

I set di criteri, una novità della versione 1910, presentano i seguenti problemi noti.

- Quando si crea un set di criteri, se un amministratore con ambito tenta di creare un set di criteri senza tag di ambito selezionati, quando si raggiunge la pagina **Rivedi e crea**, la convalida avrà esito negativo e verrà visualizzato un errore nella barra di stato. L'amministratore deve passare a una pagina diversa del processo e quindi tornare alla pagina **Rivedi e crea**. In questo modo verrà abilitata l'opzione **Crea**.  
 
- I tipi di app seguenti sono attualmente supportati dai set di criteri:
    - App di iOS Store
    - App line-of-business iOS
    - App line-of-business iOS gestite
    - App di Android Store
    - App line-of-business Android
    - App line-of-business Android gestite
    - Office 365 ProPlus Suite (Windows 10)
    - Collegamento Web
    - App iOS predefinita
    - App Android predefinita

- L'impostazione dell'assegnazione di un set di criteri **Tutti gli utenti** su **Profilo Autopilot** non è supportata.

- Per i set di criteri esistono le restrizioni di registrazione e i problemi per la pagina relativa allo stato della registrazione seguenti:
    - Le restrizioni e la pagina relativa allo stato della registrazione non supportano le assegnazioni di gruppi virtuali.
    - Le restrizioni e la pagina relativa allo stato della registrazione non supportano assegnazioni di gruppi di esclusione. 
    - Le restrizioni e la pagina relativa allo stato della registrazione usano la risoluzione dei conflitti basata sulla priorità. Le restrizioni e la pagina relativa allo stato della registrazione potrebbero non essere applicate agli stessi utenti del resto dei payload di un set di criteri se le restrizioni e la pagina relativa allo stato della registrazione sono anche la destinazione di restrizioni e della pagina relativa allo stato della registrazione con priorità più elevata.
    - Le restrizioni e la pagina relativa allo stato della registrazione predefinite non possono essere aggiunte a un set di criteri.

- I tipi di criteri MAM che supportano i set di criteri includono quanto segue: 
    - Protezione delle app gestite con destinazione MDM MAM WIP (Windows) 
    - Protezione delle app gestite con destinazione iOS MAM
    - Protezione delle app gestite con destinazione Android MAM
    - Configurazione delle app gestite con destinazione iOS MAM
    - Configurazione delle app gestite con destinazione Android MAM

- I tipi di criteri MAM che non supportano i set di criteri includono quanto segue: 
    - Protezione delle app gestite con destinazione MAM WIP (Windows)

- MAM elabora le assegnazioni dei set di criteri come assegnazioni dirette per i tipi di criteri seguenti:
    - Protezione delle app gestite con destinazione iOS MAM
    - Protezione delle app gestite con destinazione Android MAM
    - Configurazione delle app gestite con destinazione iOS MAM
    - Configurazione delle app gestite con destinazione Android MAM

    Se un criterio viene aggiunto a un set di criteri distribuito a un gruppo, il gruppo viene visualizzato come assegnato direttamente nel carico di lavoro e non come "assegnato tramite il set di criteri". Di conseguenza, MAM non elabora le eliminazioni di assegnazione dei gruppi provenienti da set di criteri.

- MAM non supporta la distribuzione ai gruppi virtuali **Tutti gli utenti** e **Tutti i dispositivi** per tutti i tipi di criteri.

## <a name="next-steps"></a>Passaggi successivi

- [Registrare i dispositivi in Microsoft Intune](~/enrollment/index.yml).