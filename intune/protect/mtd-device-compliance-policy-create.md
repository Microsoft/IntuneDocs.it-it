---
title: Creare criteri di conformità dei dispositivi MTD con Microsoft Intune
titleSuffix: Microsoft Intune
description: Creare criteri di conformità dei dispositivi di Intune che usano i livelli di minaccia del partner MTD per determinare se un dispositivo mobile può accedere alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409705"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Creare criteri di conformità dei dispositivi Mobile Threat Defense (MTD) con Intune

Intune con MTD consente di rilevare le minacce e valutare il rischio nei dispositivi mobili. Per ogni dispositivo Intune è possibile creare una regola dei criteri di conformità che consenta di valutare i rischi e determinare se il dispositivo è conforme o meno. È quindi possibile usare [criteri di accesso condizionale](create-conditional-access-intune.md) per bloccare l'accesso ai servizi in base alla conformità dei dispositivi.

> [!NOTE]
> Queste informazioni si applicano a tutti i partner Mobile Threat Defense.

## <a name="before-you-begin"></a>Prima di iniziare

Nell'ambito della configurazione di MTD, nella console partner di MTD sono stati creati criteri per la classificazione delle varie minacce come ad alto, medio o basso rischio. È ora necessario impostare il livello di Mobile Threat Defense nei criteri di conformità dei dispositivi Intune.

Prerequisiti dei criteri di conformità dei dispositivi con MTD:

- Configurazione dell'integrazione di MTD con Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>Per creare criteri di conformità per dispositivi MTD

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivo** > **Criteri di conformità** > **Crea criterio**.

3. Specificare **Nome**, **Descrizione** per il criterio di conformità del dispositivo, selezionare la **Piattaforma**, quindi scegliere **Configura** nella sezione **Impostazioni**.

4. Nel riquadro **Criteri di conformità** scegliere **Integrità del dispositivo**.

5. Nel riquadro **Integrità del dispositivo** scegliere il livello di minaccia per dispositivi mobili nell'elenco a discesa in **Richiedi che il dispositivo si trovi al massimo al livello di minaccia del dispositivo**.

   - **Protetti**: questo livello è il più sicuro. Nel dispositivo non possono essere presenti minacce per poter accedere alle risorse aziendali. Se viene rilevata qualsiasi minaccia, il dispositivo viene valutato come non conforme.

   - **Basso**: il dispositivo è conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.

   - **Medio**: il dispositivo è conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.

   - **Alto**: questo livello è il meno sicuro. Questa impostazione consente tutti i livelli di minacce e usa Mobile Threat Defense solo a scopi di report. È necessario che nei dispositivi l'app MTD sia attivata con questa impostazione.

6. Selezionare **OK** due volte, quindi scegliere **Crea** per creare i criteri.

> [!IMPORTANT]
> Se si creano criteri di accesso condizionale per Office 365 o altri servizi, viene eseguita la valutazione della conformità dei dispositivi e per i dispositivi non conformi viene bloccato l'accesso alle risorse aziendali fino alla risoluzione della condizione di minaccia nei dispositivi interessati.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>Per assegnare criteri di conformità per dispositivi MTD

Per assegnare criteri di conformità dei dispositivi agli utenti:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivo** > **Criteri di conformità**.

3. Selezionare il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Usare le opzioni disponibili per *includere* ed *escludere* i gruppi che riceveranno questo criterio.  

4. Selezionare Salva per completare l'assegnazione. Quando si salva l'assegnazione, i criteri vengono distribuiti agli utenti selezionati e i relativi dispositivi vengono valutati per la conformità.

## <a name="next-steps"></a>Passaggi successivi

[Abilitare MTD con Intune](mtd-connector-enable.md)
