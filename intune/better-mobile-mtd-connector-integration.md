---
title: Configurare l'integrazione di Better Mobile con Intune
titleSuffix: Intune on Azure
description: Integrazione del connettore Better Mobile con Intune
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 7/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.openlocfilehash: 5aad0e4aa0f3377c0d46f241d92712d81e4cfbd6
ms.sourcegitcommit: 973a06f4a35b74314fece2bae17dd6885b4211c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42823291"
---
# <a name="integrate-better-mobile-with-intune"></a>Integrare Better Mobile con Intune

Seguire questa procedura per integrare la soluzione Better Mobile Threat Defense con Intune.

## <a name="before-you-begin"></a>Prima di iniziare

> [!NOTE]
> I passaggi seguenti devono essere completati nella [console di amministrazione di Better Mobile](https://aad.bmobi.net).

Prima di avviare il processo di integrazione di Better Mobile con Intune, verificare di avere quanto segue:

-   Sottoscrizione di Microsoft Intune

-   Credenziali di amministratore di Azure Active Directory per concedere le autorizzazioni seguenti:

    -   Accesso e lettura del profilo utente

    -   Accesso alla directory come utente connesso

    -   Lettura dati directory

    -   Invio di informazioni sul dispositivo a Intune

-   Credenziali di amministratore per accedere alla console di amministrazione di Better Mobile.

### <a name="better-mobile-app-authorization"></a>Autorizzazione dell'app Better Mobile

Il processo di autorizzazione dell'app Better Mobile è il seguente:

-   Consentire al servizio Better Mobile di comunicare a Intune informazioni relative allo stato di integrità dei dispositivi.

-   Better Mobile esegue la sincronizzazione con l'appartenenza al gruppo di registrazione di Azure AD per popolare il relativo database del dispositivo.

-   Consentire alla console di amministrazione di Better Mobile di usare la funzionalità Single Sign-On (SSO) di Azure AD.

-   Consentire all'app Better Mobile di eseguire l'accesso mediante la funzionalità SSO di Azure AD.

## <a name="to-set-up-better-mobile-integration"></a>Per configurare l'integrazione di Better Mobile

1. Passare alla [console di amministrazione di Better Mobile](https://aad.bmobi.net) e accedere con le proprie credenziali.
2. Scegli **Integration** > **EMM/MDM** > **ADD ACCOUNT** (Integrazione > EMM/MDM > AGGIUNGI ACCOUNT).

     ![Console di amministrazione di Better Mobile](media/better_mobile_console.png)
 
3. Scegliere **Intune**.
4. Immettere un descrittore accanto ad **ACCOUNT NAME** (NOME ACCOUNT). 
5. Nella finestra di **accesso di Microsoft** immettere le credenziali di Intune.
6. Nella finestra **Autorizzazioni richieste** scegliere **Accetta**.
7. Cercare i gruppi di sicurezza di Azure AD desiderati con cui Better Mobile deve eseguire la sincronizzazione e selezionarli nell'elenco. Selezionare quindi **Continua**.
8. Seleziona **Chiudi**.
9. Verrà visualizzata di nuovo la pagina **Add account** (Aggiungi account). Chiudere la pagina. 

## <a name="next-steps"></a>Passaggi successivi

-   [Configurare le app di Better Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)