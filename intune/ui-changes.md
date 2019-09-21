---
title: Dove si trovano le funzionalità di Intune in Azure?
titleSuffix: Microsoft Intune
description: Suggerimenti per trovare le funzionalità di Microsoft Intune nel portale di Azure.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/4/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac74cc547d13e92b87a8e148845ff1bc7be8efe4
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166994"
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>Dove si trovano le funzionalità di Intune in Azure?
Con lo spostamento di Intune nel portale di Azure, alcune attività sono state riorganizzate in modo più logico. Ma ogni ottimizzazione implica la necessità di abituarsi a una nuova organizzazione. Questa guida di riferimento è pensata espressamente per chi conosce già Intune nel portale classico e vuole imparare a usarlo nel portale di Azure. Se questo articolo non fornisce informazioni su una funzionalità specifica, lasciare un commento alla fine dell'articolo in modo che possa essere aggiornato.
## <a name="quick-reference-guide"></a>Guida di riferimento rapido

|Funzionalità |Percorso nel portale classico|Percorso in Intune nel portale di Azure|
|------------|---------------|---------------|
|Device Enrollment Program (DEP) [solo iOS]|Amministrazione > Gestione dispositivi mobili > iOS > Device Enrollment Program|[Registrazione del dispositivo > Registrazione Apple > Token DEP](#where-did-apple-dep-go) |
|Device Enrollment Program (DEP) [solo iOS]| Amministrazione > Gestione dispositivi mobili > iOS e Mac OS X > Device Enrollment Program |[Registrazione del dispositivo > Registrazione Apple > Numeri di serie DEP](#where-did-apple-dep-go) |
|Regole di registrazione |Amministrazione > Gestione dispositivi mobili > Regole di registrazione|[Registrazione del dispositivo > Restrizioni di registrazione](#where-did-enrollment-rules-go) |
|Gruppi in base al numero di serie iOS |Gruppi > Tutti i dispositivi > Dispositivi aziendali preregistrati > Per numero di serie iOS|[Registrazione del dispositivo > Registrazione Apple > Numeri di serie DEP](#where-did-corporate-pre-enrolled-devices-go) |
|Gruppi in base al numero di serie iOS |Gruppi > Tutti i dispositivi > Dispositivi aziendali preregistrati > Per numero di serie iOS| [Registrazione del dispositivo > Registrazione Apple > Numeri di serie AC](#where-did-corporate-pre-enrolled-devices-go)|
|Gruppi in base a IMEI (tutte le piattaforme)| Gruppi > Tutti i dispositivi > Dispositivi aziendali preregistrati > Per IMEI (tutte le piattaforme) | [Registrazione del dispositivo > Identificatori dei dispositivi aziendali](#by-imei-all-platforms)|
| Profilo di registrazione di dispositivo aziendale| Criteri > 	Pre-Approved	Registrazione di dispositivi aziendali | [Registrazione del dispositivo > Registrazione Apple > Profili DEP](#where-did-corporate-pre-enrolled-devices-go) |
| Profilo di registrazione di dispositivo aziendale | Criteri > 	Pre-Approved	Registrazione di dispositivi aziendali | [Registrazione del dispositivo > Registrazione Apple > Profili AC](#where-did-corporate-pre-enrolled-devices-go) |
| Android for Work | Amministrazione > Gestione dispositivi mobili > Android for Work | Registrazione del dispositivo > Registrazione Android |
| Termini e condizioni | Criteri > Termini e condizioni | Registrazione del dispositivo > Termini e condizioni |
Impostazioni del portale aziendale|Amministrazione > Portale aziendale|**Gestisci** > App per dispositivi mobili<br> **Installazione** > Personalizzazione del portale aziendale


## <a name="where-do-i-manage-groups"></a>Dove si gestiscono i gruppi?
Intune nel portale di Azure usa [Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) per gestire i gruppi.

## <a name="where-did-enrollment-rules-go"></a>Dove si trovano le regole di registrazione?
Nel portale classico è possibile impostare regole per controllare la registrazione MDM dei dispositivi Windows e macOS mobili e moderni.

![Immagine delle regole di registrazione dei dispositivi mobili nella console classica](./media/01-classic-rules.png)

Queste regole vengono applicate a tutti gli utenti nell'account di Intune senza eccezione. Nel portale di Azure queste regole vengono suddivise in due tipi di criteri distinti, ovvero restrizioni sul tipo di dispositivi e restrizioni sul limite di dispositivi.

![Immagine delle restrizioni per la registrazione dei dispositivi mobili in Azure](./media/02-azure-enroll-restrictions.png)

Il valore predefinito di restrizione sul limite di dispositivi corrisponde al limite di registrazione dei dispositivi nel portale classico.

![Immagine delle restrizioni sul limite di dispositivi in Azure](./media/03-azure-device-limit.png)

Il valore predefinito di restrizione dei tipi di dispositivo corrisponde alle restrizioni della piattaforma nel portale classico.

![Immagine delle restrizioni sul tipo di dispositivi in Azure](./media/04-azure-platform-restrictions.png)

La possibilità di consentire o bloccare i dispositivi personali è ora gestita nelle configurazioni della piattaforma delle restrizioni sul tipo di dispositivi.

![Immagine delle impostazioni di blocco dei dispositivi personali in Azure](./media/05-azure-personal-block.png)

Nuove funzionalità di restrizione vengono aggiunte solo al portale di Azure.

## <a name="where-did-my-conditional-access-policies-go"></a>Dove si trovano i criteri di accesso condizionale?
Dopo la migrazione del tenant al portale di Azure, i criteri di accesso condizionale del tenant continuano a essere applicati. Tuttavia, non è possibile visualizzarli o modificarli da Intune nel portale di Azure.

Per visualizzare e apportare modifiche ai criteri di accesso condizionale dal portale di Azure, sarà necessario rimuovere i criteri precedenti dal portale classico e poi ricrearli nel portale di Azure. Per altre informazioni sulla migrazione dei criteri di accesso condizionale, vedere [Eseguire la migrazione di criteri classici](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration). 

## <a name="where-did-my-compliance-policies-go"></a>Dove si trovano i criteri di conformità?
Dopo la migrazione del tenant al portale di Azure, i criteri di conformità del tenant continuano a essere applicati. Tuttavia, non è possibile visualizzarli o modificarli da Intune nel portale di Azure.

Per visualizzare e apportare modifiche ai criteri di conformità dal portale di Azure, sarà necessario rimuovere i criteri precedenti dal portale classico e poi ricrearli nel portale di Azure. Per altre informazioni sui criteri di conformità dei dispositivi, vedere [Introduzione ai criteri di conformità dei dispositivi in Intune](device-compliance-get-started.md). 

## <a name="where-did-apple-dep-go"></a>Dove si trova il servizio Apple DEP?
Nel portale classico è possibile impostare Intune in modo da integrarsi con Apple Device Enrollment Program e richiedere manualmente la sincronizzazione con il servizio Apple:

![Immagine del token DEP nella console classica](./media/06-classic-dep-token.png)

Nel portale di Azure Apple Device Enrollment Program viene impostato allo stesso modo che nella console classica di Intune:

![Immagine del token DEP in Azure](./media/07-azure-dep-token.png)

L'opzione **Sincronizza** nel portale classico è stata tuttavia spostata nel flusso di lavoro di gestione dei numeri di serie, dal momento che i risultati di una sincronizzazione manuale vengono visualizzati in quella finestra:

![Immagine della sincronizzazione DEP in Azure](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>Dove si trovano i dispositivi aziendali preregistrati?
### <a name="by-ios-serial-number"></a>Per numero di serie iOS
Nel portale classico è possibile registrare i dispositivi iOS tramite Apple Device Enrollment Program (DEP) e lo strumento Apple Configurator. Entrambi i metodi offrono le preregistrazione dei dispositivi in base al numero di serie e comportano l'assegnazione di speciali profili di registrazione di dispositivi aziendali. Prima della registrazione, l'assegnazione del profilo di registrazione può essere gestita tramite il gruppo di dispositivi **Dispositivi aziendali preregistrati per numero di serie iOS**:

![Immagine dei numeri di serie Apple nella console classica](./media/09-classic-apple-serials.png)

I numeri di serie per la registrazione tramite Apple DEP e Apple Configurator sono visualizzati in un unico elenco. Per ridurre la mancata corrispondenza nell'assegnazione del profilo (profilo DEP assegnato a numero di serie AC e viceversa), i numeri di serie sono stati distinti in due elenchi nel portale di Azure:

**Numeri di serie DEP**
![Immagine dei numeri di serie DEP in Azure](./media/10-azure-dep-serials.png)

**Numeri di serie di Apple Configurator**
![Immagine dei numeri di serie di Apple Configurator in Azure](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>Per IMEI (tutte le piattaforme)

Nel portale classico è possibile pre-elencare i numeri IMEI dei dispositivi per contrassegnarli come aziendali quando vengono registrati in Intune:

![Immagine dell'elenco dei numeri IMEI nella console classica](./media/12-classic-corp-imei.png)

Nel portale di Azure è necessario caricare lo stesso IMEI nell'elenco Identificatori dei dispositivi aziendali con un file di valori separati da virgole (CSV). Il nuovo portale non supporta l'immissione manuale di numeri IMEI:

![Immagine dell'elenco dei numeri IMEI in Azure](./media/13-azure-corp-imei.png)

In futuro, Intune nel portale di Azure sarà in grado di supportare altri tipi di identificatori oltre ai numeri IMEI, ma attualmente consente soltanto l'uso di numeri IMEI per i pre-elenchi.

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>Dove si trovano i profili di registrazione dei dispositivi aziendali?
Per registrare i dispositivi iOS tramite Apple Device Enrollment Program o con lo strumento Apple Configurator, è necessario fornire un profilo di registrazione dei dispositivi aziendali da assegnare al dispositivo. Nel portale classico la creazione e la gestione di questi profili è accessibile da un unico elenco:

![Immagine dei profili di registrazione dei dispositivi nella console classica](./media/14-classic-corp-profiles.png)

Questo elenco mostra i profili abilitati per l'uso con Apple Device Enrollment Program (**DEP Sì**) e i profili abilitati solo per l'uso con lo strumento Apple Configurator (**DEP No**).

Per ridurre la confusione tra i due tipi di profilo e le potenziali assegnazioni non corrispondenti (profilo DEP associato a dispositivi dello strumento Configurator e viceversa), sono state separate la creazione e la gestione dei profili di Enrollment Program (che supportano sia Apple Device Enrollment Program che Apple School Manager) e i profili di Apple Configurator:

**Profili DEP**
![Immagine dei profili DEP in Azure](./media/15-azure-dep-profiles.png)

**Profili di Apple Configurator**
![Immagine dei profili di Apple Configurator in Azure](./media/16-azure-ac-profiles.png)
