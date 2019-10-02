---
title: Abilitare il connettore Mobile Threat Defense in Microsoft Intune
titleSuffix: Microsoft Intune
description: Abilitare il connettore tra il partner Mobile Threat Defense (MTD) e Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ac49edcd4ea71bdbc83cfa093f2bb5e42aefd54
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722072"
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


## <a name="to-enable-the-mtd-connector"></a>Per abilitare il connettore MTD

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. Nel **dashboard di Intune** scegliere **Conformità del dispositivo** e quindi scegliere **Mobile Threat Defense** nella sezione **Installazione**.

5. Nel riquadro **Mobile Threat Defense** scegliere **Aggiungi**.

6. Scegliere la soluzione MTD nell'elenco a discesa **Selezionare il connettore Mobile Threat Defense da configurare**.

    ![Configurazione di MTD nel portale di Intune di Azure](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. Abilitare le opzioni con interruttore di attivazione/disattivazione in base ai requisiti dell'organizzazione. Le opzioni di attivazione/disattivazione visibili variano a seconda del partner MTD.

## <a name="mtd-toggle-options"></a>Opzioni di attivazione/disattivazione di MTD

È possibile scegliere le opzioni di attivazione/disattivazione MTD da abilitare in base ai requisiti dell'organizzazione. Ecco ulteriori dettagli:

- **Connetti dispositivi Android 4.1+ a [nome partner MTD] for Work MTD**: quando si abilita questa opzione, è possibile fare in modo che i dispositivi Android 4.1+ segnalino i rischi di sicurezza a Intune.
  - **Contrassegna come non conforme se non vengono ricevuti dati**: se Intune non riceve dati su un dispositivo in questa piattaforma da un partner MTD, il dispositivo viene considerato non conforme.
<br></br>
- **Connetti dispositivi iOS 8.0+ a [nome partner MTD] for Work MTD**: quando si abilita questa opzione, è possibile fare in modo che i dispositivi iOS 8.0+ segnalino i rischi di sicurezza in Intune.
  - **Contrassegna come non conforme se non vengono ricevuti dati**: se Intune non riceve dati su un dispositivo in questa piattaforma da un partner MTD, il dispositivo viene considerato non conforme.
<br></br>
- **Abilita la sincronizzazione delle app per dispositivi iOS**: consente a questo partner di Mobile Threat Defense di richiedere metadati delle applicazioni iOS da Intune da usare per l'analisi delle minacce.

- **Blocca le versioni del sistema operativo non supportate**: bloccare un dispositivo che esegue un sistema operativo con un versione precedente a quella minima supportata.

- **Numero di giorni dopo i quali il partner risulta non reattivo**: numero di giorni di inattività prima che Intune consideri il partner non reattivo a causa della perdita della connessione. Intune ignora lo stato di conformità per i partner MTD non reattivi.

> [!IMPORTANT] 
> Se possibile, è consigliabile aggiungere e assegnare le app MTD prima di creare le regole di conformità del dispositivo e dei criteri di accesso condizionale. Ciò garantisce che l'app MTD sia pronta e disponibile in modo che gli utenti finali possano installarla prima di ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.

> [!TIP]
> Nel riquadro Mobile Threat Defence sono visualizzati lo **Stato connessione** e l'ora dell'**Ultima sincronizzazione** tra Intune e il partner MTD.
