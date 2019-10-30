---
title: Creare criteri di protezione delle app MTD (Mobile Threat Defense) con Intune
titleSuffix: Microsoft Intune
description: Creare criteri di protezione delle app MTD (Mobile Threat Defense) con Microsoft Intune.
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
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794420"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Creare criteri di protezione delle app Mobile Threat Defense con Intune

> [!NOTE] 
> Questo articolo si applica a tutti i partner MTD (Mobile Threat Defense) che supportano i criteri di protezione delle app: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

Intune con MTD consente di rilevare le minacce e valutare il rischio nei dispositivi mobili. È possibile creare criteri di protezione delle app di Intune che valutano i rischi per determinare se al dispositivo è consentito o meno l'accesso ai dati aziendali. 

## <a name="before-you-begin"></a>Prima di iniziare

Nell'ambito della configurazione di MTD, nella console partner di MTD sono stati creati criteri per la classificazione delle varie minacce come ad alto, medio o basso rischio. È ora necessario impostare il livello di Mobile Threat Defense nei criteri di protezione delle app di Intune.

Prerequisiti per i criteri di protezione delle app con MTD:

- Configurare l'integrazione di MTD con Intune. Senza questa integrazione, i criteri di protezione delle app MTD non avranno alcun effetto.

## <a name="to-create-an-mtd-app-protection-policy"></a>Per creare un criterio di protezione delle app MTD

1. Andare nel [portale di Azure](https://portal.azure.com/) e accedere con le credenziali di Intune.

2. Nel **dashboard di Azure** scegliere **Tutti i servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune**. Si aprirà il **dashboard di Intune**.

4. Nel **dashboard di Intune** scegliere **App client** e quindi nella sezione **Gestisci** scegliere **Criteri di protezione delle app**.

5. Scegliere **Crea criterio**, immettere **Nome** e **Descrizione**, quindi selezionare la **Piattaforma**. 

6. Nel riquadro **Avvio condizionale**, nella tabella **Condizioni del dispositivo** scegliere il livello di minaccia per dispositivi mobili nell'elenco a discesa in **Livello di minaccia massimo consentito del dispositivo**.

    a.  **Protetti**: questo livello è il più sicuro. Nel dispositivo non possono essere presenti minacce per poter accedere alle risorse aziendali. Se viene rilevata qualsiasi minaccia, il dispositivo viene valutato come non conforme.

    b.  **Basso**: il dispositivo è conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.

    c.  **Medio**: il dispositivo è conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.

    d.  **Alto**: questo livello è il meno sicuro. Questa impostazione consente tutti i livelli di minacce e usa Mobile Threat Defense solo a scopi di report. È necessario che nei dispositivi l'app MTD sia attivata con questa impostazione.

7. Fare clic su **Salva** due volte e quindi scegliere **Crea**.

## <a name="to-assign-an-mtd-app-protection-policy"></a>Per assegnare un criterio di protezione delle app MTD

Per assegnare agli utenti criteri di conformità dei dispositivi, scegliere criteri configurati in precedenza. I criteri esistenti sono disponibili nel riquadro **Conformità del dispositivo - criteri**.

1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Questa azione apre il riquadro da cui è possibile selezionare i **Gruppi di sicurezza Azure Active Directory** e assegnarli ai criteri.

2. Scegliere **Selezionare i gruppi da includere** per aprire il riquadro che consente di visualizzare i gruppi di sicurezza di Azure AD. Se si sceglie **Seleziona** il criterio verrà distribuito agli utenti.

> [!NOTE] 
> Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per l'accesso ai dati aziendali nelle app di destinazione tramite la protezione delle app di Intune.

## <a name="next-steps"></a>Passaggi successivi  

- Altre informazioni su [Mobile Threat Defense](~/protect/mobile-threat-defense.md) in Microsoft Intune.
