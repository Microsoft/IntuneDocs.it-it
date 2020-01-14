---
title: Abilitare il connettore Mobile Threat Defense per i dispositivi non registrati
titleSuffix: Microsoft Intune
description: Abilitare il connettore mobile Threat Defense in Microsoft Intune per i dispositivi non registrati.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9571f7d0ae10f33007d5ae50b403580232c2e870
ms.sourcegitcommit: 06dce5c8111592ad774247e86e539dd3128117e5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/30/2019
ms.locfileid: "75545933"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Abilitare il connettore Mobile Threat Defense in Intune per i dispositivi non registrati

Durante l'installazione di Mobile Threat Defense (MTD), sono stati configurati criteri di classificazione delle minacce nella console del partner Mobile Threat Defense e sono stati creati i criteri di protezione delle app in Intune. Se il connettore Intune nella console del partner MTD è già stato configurato, è possibile abilitare la connessione MTD in Intune per le applicazioni del partner MTD.

> [!NOTE]
> Questo articolo si applica a tutti i partner Mobile Threat Defense che supportano i criteri di protezione delle app: Better Mobile (Android), Zimperium (Android/iOS), Lookout for Work (Android/iOS).

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Criteri di accesso condizionale classici per app MTD

Quando si integra una nuova applicazione in Intune Mobile Threat Defense e si abilita la connessione per Intune, Intune crea criteri di accesso condizionale classici in Azure Active Directory. Ogni app MTD integrata, inclusi [Defender ATP](advanced-threat-protection.md) o uno qualsiasi dei [partner MTD](mobile-threat-defense.md#mobile-threat-defense-partners) aggiuntivi, crea nuovi criteri di accesso condizionale classici. Questi criteri possono essere ignorati, ma non devono essere modificati, eliminati o disabilitati.

Se i criteri classici vengono eliminati, sarà necessario eliminare la connessione a Intune che li ha creati e poi riconfigurarla. In questo modo si ricreano i criteri classici. Non è possibile eseguire la migrazione dei criteri classici per le app MTD al nuovo tipo di criteri per l'accesso condizionale.

I criteri di accesso condizionale classici per le app gestite:

- Vengono usati da Intune MTD per richiedere che i dispositivi vengano registrati in Azure AD in modo da avere un ID dispositivo prima di comunicare con i partner MTD. L'ID è necessario per consentire ai dispositivi di segnalare correttamente lo stato a Intune.

- Non ha alcun effetto su altre app o risorse cloud.

- Sono diversi dai criteri di accesso condizionale che è possibile creare per facilitare la gestione di MTD.

- Per impostazione predefinita non interagiscono con altri criteri di accesso condizionale usati per la valutazione.

Per visualizzare i criteri di accesso condizionale classici, in [Azure](https://portal.azure.com/#home) passare a **Azure Active Directory** > **Accesso condizionale** > **Criteri classici**.

## <a name="to-enable-the-mtd-connector"></a>Per abilitare il connettore MTD

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Mobile Threat Defense**.

3. Nel riquadro **Mobile Threat Defense** scegliere **Aggiungi**.

4. Scegliere la soluzione MTD nell'elenco a discesa **Selezionare il connettore Mobile Threat Defense da configurare**.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Abilitare le opzioni di attivazione/disattivazione in base ai requisiti dell'organizzazione. Le opzioni di attivazione/disattivazione visibili variano a seconda del partner MTD.

## <a name="mobile-threat-defense-toggle-options"></a>Opzioni di attivazione/disattivazione di Mobile Threat Defense

È possibile scegliere le opzioni di attivazione/disattivazione MTD da abilitare in base ai requisiti dell'organizzazione. Di seguito sono riportate informazioni dettagliate:

**Impostazioni dei criteri di protezione delle app**

- **Connetti i dispositivi Android con versione 4.4 e successiva a *\<nome partner MTD>* per la valutazione dei criteri di protezione dell'app**: Quando si abilita questa opzione, i criteri di protezione delle app che usano la regola Livello di minaccia del dispositivo valuteranno i dispositivi che includono dati da questo connettore.

- **Connetti i dispositivi iOS con versione 11 e successiva a *\<nome partner MTD>* per la valutazione dei criteri di protezione dell'app**: Quando si abilita questa opzione, i criteri di protezione delle app che usano la regola Livello di minaccia del dispositivo valuteranno i dispositivi che includono dati da questo connettore.

**Impostazioni condivise comuni**

- **Numero di giorni dopo i quali il partner risulta non reattivo**: numero di giorni di inattività prima che Intune consideri il partner non reattivo a causa della perdita della connessione. Intune ignora lo stato di conformità per i partner MTD non reattivi.

> [!TIP]
> Nel riquadro Mobile Threat Defence sono visualizzati lo **Stato connessione** e l'ora dell'**Ultima sincronizzazione** tra Intune e il partner MTD.

## <a name="next-steps"></a>Passaggi successivi

- [Creare criteri di protezione delle app MTD (Mobile Threat Defense) con Intune](~/protect/mtd-app-protection-policy.md).
