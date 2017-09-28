---
title: Abilitare il connettore Mobile Threat Defense con Intune
titlesuffix: Azure portal
description: Abilitare il connettore Mobile Threat Defense in Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d818581ca74e64bf27c968b39969afd889b6fbda
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2017
---
# <a name="enable-mobile-threat-defense-in-intune"></a>Abilitare Mobile Threat Defense in Intune

> [!NOTE] 
> Questo argomento si applica a tutti i partner Mobile Threat Defense.

Per abilitare la connessione Mobile Threat Defense (MTD) in Intune, è necessario avere già configurato il connettore Intune nella console del partner MTD.

## <a name="to-enable-the-mtd-connector"></a>Per abilitare il connettore MTD

1. Andare nel [portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune. Dopo l'accesso viene visualizzato il **dashboard di Azure**.

2. Nel **dashboard di Azure** scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune**. Viene visualizzato il **dashboard di Intune**.

4. Nel **dashboard di Intune** scegliere **Conformità del dispositivo** e quindi scegliere **Mobile Threat Defense** nella sezione **Installazione**.

5. Nel pannello **Mobile Threat Defense** scegliere **Aggiungi**.

6. Scegliere la soluzione MTD nell'elenco a discesa **Selezionare il connettore Mobile Threat Defense da configurare**.

    ![Configurazione di MTD nel portale di Intune di Azure](./media/enable-mtd-connector-1.png)

7. Abilitare le opzioni con interruttore di attivazione/disattivazione in base ai requisiti dell'organizzazione.

## <a name="mtd-toggle-options"></a>Opzioni di attivazione/disattivazione di MTD

È possibile decidere quali opzioni di attivazione/disattivazione di MTD è necessario abilitare in base ai requisiti dell'organizzazione. Per informazioni più dettagliate:

- **Connetti dispositivi Android 4.1+ a [nome partner MTD] for Work MTD**: quando si abilita questa opzione è possibile fare in modo che i dispositivi Android 4.1+ segnalino i rischi di sicurezza in Intune.
    - **Contrassegna come non conforme se non vengono ricevuti dati**: se Intune non riceve dati su un dispositivo in questa piattaforma da un partner MTD, il dispositivo viene considerato non conforme.
<br></br>
- **Connetti dispositivi iOS 8.0+ a [nome partner MTD] for Work MTD**: quando si abilita questa opzione è possibile fare in modo che i dispositivi iOS 8.0+ segnalino i rischi di sicurezza in Intune.
    - **Contrassegna come non conforme se non vengono ricevuti dati**: se Intune non riceve dati su un dispositivo in questa piattaforma da un partner MTD, il dispositivo viene considerato non conforme.
<br></br>
- **Blocca le versioni del sistema operativo non supportate**: bloccare un dispositivo che esegue un sistema operativo con un versione precedente a quella minima supportata.

- **Numero di giorni dopo i quali il partner risulta non reattivo**: numero di giorni di inattività prima che Intune consideri il partner non reattivo a causa della perdita della connessione. Intune ignora lo stato di conformità per i partner MTD non reattivi.

> [!IMPORTANT] 
> È necessario aggiungere e assegnare le app MTD prima di creare le regole di conformità del dispositivo e dei criteri di accesso condizionale. Ciò garantisce che l'app MTD sia pronta e disponibile in modo che gli utenti finali possano installarla prima di ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.

> [!TIP]
> Nel pannello Mobile Threat Defence sono visualizzati lo **Stato connessione** e l'ora dell'**Ultima sincronizzazione** tra Intune e il partner MTD.
