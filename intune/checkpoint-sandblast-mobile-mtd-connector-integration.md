---
title: Configurare l'integrazione di Check Point SandBlast con Intune
titlesuffix: Azure portal
description: Configurare l'integrazione di Check Point SandBlast con Intune
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 92e1f8474625d2036c698da0473ec20926da68d2
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>Integrare Check Point SandBlast Mobile con Intune

## <a name="before-you-begin"></a>Prima di iniziare

> [!NOTE] 
> La procedura seguente deve essere eseguita nella [console MTD di Check Point SandBlast Mobile](https://intune-4.eu1.locsec.net/).

Prima di avviare il processo di integrazione di Check Point SandBlast Mobile con Intune, assicurarsi di disporre di quanto segue:

-   Sottoscrizione di Microsoft Intune

-   Credenziali di amministratore di Azure Active Directory per concedere le autorizzazioni seguenti:

    -   Accesso e lettura del profilo utente

    -   Accesso alla directory come utente connesso

    -   Lettura dati directory

    -   Invio di informazioni sul dispositivo a Intune

-   Credenziali di amministratore per accedere alla console MTD di Check Point SandBlast Mobile.

### <a name="check-point-sandblast-app-authorization"></a>Verificare le autorizzazioni dell'app Check Point SandBlast

Il processo di autorizzazione dell'app Check Point SandBlast è costituito dai seguenti elementi:

-   Consentire al servizio Check Point SandBlast Mobile di comunicare a Intune informazioni relative allo stato di integrità dei dispositivi.

-   CheckPoint SandBlast Mobile esegue la sincronizzazione con l'appartenenza al gruppo di registrazione di Azure AD per popolare il relativo database del dispositivo.

-   Consentire alla console di amministrazione di Check Point SandBlast di usare la funzionalità Single Sign-On (SSO) di Azure AD.

-   Consentire all'app Check Point SandBlast Mobile di eseguire l'accesso tramite la funzionalità SSO di Azure AD.

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>Per configurare l'integrazione di Check Point SandBlast Mobile

1.  Passare alla [console MTD di Check Point SandBlast Mobile](https://intune-4.eu1.locsec.net/) e accedere con le proprie credenziali.

2.  Fare clic sulla scheda **Settings** (Impostazioni).

3.  Scegliere **Device management** (Gestione dispositivi), quindi **Settings** (Impostazioni).

4.  Scegliere **Microsoft Intune** dall'elenco a discesa **MDM Service** (Servizio MDM).

5.  Dopo aver impostato Microsoft Intune come servizio MDM, verrà visualizzata la finestra **Microsoft Intune Configuration** (Configurazione di Microsoft Intune). Scegliere **Add to my organization** (Aggiungi alla mia organizzazione) per ogni piattaforma per i dispositivi (iOS, Android e Windows) per autorizzare Check Point SandBlast Mobile a comunicare con Intune e Azure AD.

    ![Configurazione di Check Point MTD in Intune](./media/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > È necessario aggiungere tutte le piattaforme per i dispositivi per procedere al passaggio successivo.

6.  Scegliere **Accept** (Accetta) per autorizzare l'app Check Point SandBlast Mobile a comunicare con Intune e Azure Active Directory.

7.  Dopo avere abilitato tutte le piattaforme per i dispositivi, è necessario immettere il gruppo di sicurezza di Azure AD.

8.  Scegliere **Verify** (Verifica). Dopo avere verificato correttamente il gruppo di sicurezza di Azure AD, scegliere **Save** (Salva).

## <a name="next-steps"></a>Passaggi successivi

- [Abilitare il connettore Check Point SandBlast Mobile con Intune](mtd-connector-enable.md)