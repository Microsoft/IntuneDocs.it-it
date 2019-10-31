---
title: Abilitare il connettore Mobile Threat Defense in Microsoft Intune
titleSuffix: Microsoft Intune
description: Abilitare il connettore tra il partner Mobile Threat Defense (MTD) e Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4f917167baecc643e045610e86e582957e535978
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810298"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Abilitare il connettore Mobile Threat Defense in Intune

> [!NOTE] 
> Questo argomento si applica a tutti i partner Mobile Threat Defense.

Durante l'installazione di Mobile Threat Defense (MTD), sono stati configurati criteri di classificazione delle minacce nella console del partner MTD e sono stati creati criteri di conformità del dispositivo in Intune. Se il connettore Intune nella console del partner MTD è già stato configurato, è possibile abilitare la connessione MTD in Intune per le applicazioni del partner MTD.

Quando si integra una nuova applicazione in Intune Mobile Threat Defense e si abilita la connessione per Intune, Intune crea criteri di accesso condizionale classici in Azure Active Directory. Ogni app MTD integrata, inclusi [Defender ATP](advanced-threat-protection.md) o uno qualsiasi dei [partner MTD](mobile-threat-defense.md#mobile-threat-defense-partners) aggiuntivi, crea nuovi criteri di accesso condizionale classici. Questi criteri possono essere ignorati, ma non devono essere modificati, eliminati o disabilitati.

I criteri di accesso condizionale classici per le app gestite: 

- Vengono usati da Intune MTD per richiedere che i dispositivi vengano registrati in Azure AD in modo da avere un ID dispositivo prima di comunicare con i partner MTD. L'ID è necessario per consentire ai dispositivi di segnalare correttamente lo stato a Intune.  
- Non ha alcun effetto su altre app o risorse cloud.  
- Sono diversi dai criteri di accesso condizionale che è possibile creare per facilitare la gestione di MTD.
- Per impostazione predefinita non interagiscono con altri criteri di accesso condizionale usati per la valutazione.  

Per visualizzare i criteri di accesso condizionale classici, in [Azure](https://portal.azure.com/#home) passare a **Azure Active Directory** > **Accesso condizionale** > **Criteri classici**.


## <a name="to-enable-the-mobile-threat-defense-connector"></a>Per abilitare il connettore Mobile Threat Defense

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. Nel **dashboard di Intune** scegliere **Conformità del dispositivo** e quindi scegliere **Mobile Threat Defense** nella sezione **Installazione**.

5. Nel riquadro **Mobile Threat Defense** scegliere **Aggiungi**.

6. Scegliere la soluzione MTD nell'elenco a discesa **Selezionare il connettore Mobile Threat Defense da configurare**.

    ![Configurazione di MTD nel portale di Intune di Azure](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. Abilitare le opzioni con interruttore di attivazione/disattivazione in base ai requisiti dell'organizzazione. Le opzioni di attivazione/disattivazione visibili variano a seconda del partner MTD.

## <a name="mobile-threat-defense-toggle-options"></a>Opzioni di attivazione/disattivazione di Mobile Threat Defense

È possibile decidere quali opzioni di attivazione/disattivazione di Mobile Threat Defense è necessario abilitare in base ai requisiti dell'organizzazione. Ecco ulteriori dettagli:

**Impostazioni dei criteri di conformità di MDM**
- **Connetti dispositivi Android 4.1+ a *\<nome partner MTD>***: quando si abilita questa opzione, è possibile fare in modo che i dispositivi Android 4.1+ segnalino i rischi di sicurezza a Intune.
- **Connetti dispositivi iOS 8.0+ a *\<nome partner MTD>***: quando si abilita questa opzione, è possibile fare in modo che i dispositivi iOS 8.0+ segnalino i rischi di sicurezza in Intune.
- **Abilita la sincronizzazione delle app per dispositivi iOS**: consente a questo partner di Mobile Threat Defense di richiedere metadati delle applicazioni iOS da Intune da usare per l'analisi delle minacce.
- **Blocca le versioni del sistema operativo non supportate**: bloccare un dispositivo che esegue un sistema operativo con un versione precedente a quella minima supportata.

**Impostazioni dei criteri di protezione delle app**
- **Connetti i dispositivi Android con versione 4.1 e successiva a *\<nome partner MTD>* per la valutazione dei criteri di protezione dell'app**: Quando si abilita questa opzione, i criteri di protezione delle app che usano la regola Livello di minaccia del dispositivo valuteranno i dispositivi che includono dati da questo connettore.
- **Connetti i dispositivi iOS con versione 8.0 e successiva a *\<nome partner MTD>* per la valutazione dei criteri di protezione dell'app**: Quando si abilita questa opzione, i criteri di protezione delle app che usano la regola Livello di minaccia del dispositivo valuteranno i dispositivi che includono dati da questo connettore.

Per altre informazioni sull'uso dei connettori Mobile Threat Defense per la valutazione dei criteri di protezione app di Intune, vedere [Abilitare il connettore Mobile Threat Defense in Intune per i dispositivi non registrati](~/protect/mtd-enable-unenrolled-devices.md).

**Impostazioni condivise comuni**
- **Numero di giorni dopo i quali il partner risulta non reattivo**: numero di giorni di inattività prima che Intune consideri il partner non reattivo a causa della perdita della connessione. Intune ignora lo stato di conformità per i partner MTD non reattivi.

> [!IMPORTANT] 
> Se possibile, è consigliabile aggiungere e assegnare le app MTD prima di creare le regole di conformità del dispositivo e dei criteri di accesso condizionale. Ciò garantisce che l'app MTD sia pronta e disponibile in modo che gli utenti finali possano installarla prima di ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.

> [!TIP]
> Nel riquadro Mobile Threat Defence sono visualizzati lo **Stato connessione** e l'ora dell'**Ultima sincronizzazione** tra Intune e il partner MTD.
