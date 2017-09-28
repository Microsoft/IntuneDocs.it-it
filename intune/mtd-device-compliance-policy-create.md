---
title: "Creare criteri di conformità dei dispositivi Mobile Threat Defense con Intune"
titlesuffix: Azure portal
description: "Creare criteri di conformità dei dispositivi Mobile Threat Defense in Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e9b1a3dc42a9c18d61fc9b55d5a7b71f00c3e29
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2017
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Creare criteri di conformità dei dispositivi Mobile Threat Defense (MTD) con Intune

> [!NOTE] 
> Questo argomento si applica a tutti i partner Mobile Threat Defense.

Intune con MTD consente di rilevare le minacce e valutare il rischio nei dispositivi mobili. Per ogni dispositivo Intune è possibile creare una regola dei criteri di conformità che consenta di valutare i rischi e determinare se il dispositivo è conforme o meno. È quindi possibile usare criteri di accesso condizionale per bloccare l'accesso ai servizi in base alla conformità dei dispositivi.

## <a name="before-you-begin"></a>Prima di iniziare

Nell'ambito della configurazione di MTD, nella console partner di MTD sono stati creati criteri per la classificazione delle varie minacce come ad alto, medio o basso rischio. È ora necessario impostare il livello di Mobile Threat Defense nei criteri di conformità dei dispositivi Intune.

Prerequisiti dei criteri di conformità dei dispositivi con MTD:

-   Configurazione dell'integrazione di MTD con Intune

## <a name="to-create-a-mtd-device-compliance-policy"></a>Per creare criteri di conformità dei dispositivi per MTD

1.  Andare nel [portale di Azure](https://portal.azure.com/) e accedere con le credenziali di Intune.

2.  Nel **dashboard di Azure** scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3.  Scegliere **Intune**. Si aprirà il **dashboard di Intune**.

4. Nel **dashboard di Intune** scegliere **Conformità del dispositivo** e quindi nella sezione **Gestisci** scegliere **Criteri**.

5.  Scegliere **Crea criterio**, immettere **Nome** e **Descrizione** della conformità del dispositivo, selezionare la **piattaforma** e quindi nella sezione **Impostazioni** scegliere **Configura**.

6.  Nel pannello **Criteri di conformità** scegliere **Integrità del dispositivo**.

7.  Nel pannello **Integrità del dispositivo** scegliere il livello di minaccia per dispositivi mobili dall'elenco a discesa in **Richiedi che il dispositivo si trovi al massimo al livello di minaccia per dispositivi mobili**.

    a.  **Protetto**: questo è il livello più sicuro. Nel dispositivo non possono essere presenti minacce per poter accedere alle risorse aziendali. Se viene rilevata qualsiasi minaccia, il dispositivo viene valutato come non conforme.

    b.  **Basso**: il dispositivo è conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.

    c.  **Medio**: il dispositivo è conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.

    d.  **Alta**: questo è il livello meno sicuro. Questa impostazione consente tutti i livelli di minacce e usa Mobile Threat Defense solo a scopi di report. È necessario che nei dispositivi l'app MTD sia attivata con questa impostazione.

8.  Fare clic su **OK** due volte e quindi scegliere **Crea**.

> [!IMPORTANT]
> Se si creano criteri di accesso condizionale per Office 365 o altri servizi, viene eseguita la valutazione della conformità dei dispositivi e per i dispositivi non conformi viene bloccato l'accesso alle risorse aziendali fino alla risoluzione della condizione di minaccia nei dispositivi interessati.

## <a name="to-assign-a-mtd-device-compliance-policy"></a>Per assegnare criteri di conformità dei dispositivi per MTD

Per assegnare agli utenti criteri di conformità dei dispositivi, scegliere criteri configurati in precedenza. I criteri esistenti sono disponibili nel pannello **Tutti i criteri di conformità del dispositivo**.

1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Si apre il pannello da cui è possibile selezionare i **Gruppi di sicurezza Azure Active Directory** e assegnarli ai criteri.

2. Scegliere **Seleziona gruppi** per aprire il pannello che consente di visualizzare i gruppi di sicurezza di Azure AD.  Se si sceglie **Seleziona** il criterio verrà distribuito agli utenti.

    > [!NOTE] 
    > Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

## <a name="next-steps"></a>Passaggi successivi

- [Abilitare MTD con Intune](mtd-connector-enable.md)