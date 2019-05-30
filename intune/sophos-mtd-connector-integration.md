---
title: Configurare l'integrazione di Sophos Mobile con Intune
titleSuffix: Intune on Azure
description: Come configurare la soluzione Sophos Mobile con Microsoft Intune per controllare l'accesso dei dispositivi mobili alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: eeddbf39093210e640125db3be6ddd6bcad7d59b
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044992"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Integrare Sophos Mobile con Intune  

Seguire questa procedura per integrare la soluzione Sophos Mobile con Intune.  

## <a name="before-you-begin"></a>Prima di iniziare  

Prima di avviare il processo di integrazione di Sophos Mobile con Intune, verificare di avere quanto segue:  
- Sottoscrizione di Microsoft Intune  
- Credenziali di amministratore di Azure Active Directory per concedere le autorizzazioni seguenti:  
  - Accesso e lettura del profilo utente  
  - Accesso alla directory come utente connesso  
  - Lettura dati directory  
  - Invio di informazioni sul dispositivo a Intune  
- Credenziali di amministratore per accedere alla console di amministrazione di Sophos Mobile.  


### <a name="sophos-mobile-app-authorization"></a>Autorizzazione dell'app Sophos Mobile  
  
Il processo di autorizzazione dell'app Sophos Mobile è il seguente:  
- Consentire al servizio Sophos Mobile di comunicare a Intune informazioni relative allo stato di integrità dei dispositivi.  
- Sophos Mobile esegue la sincronizzazione con l'appartenenza al gruppo di registrazione di Azure AD per popolare il relativo database del dispositivo.  
- Consentire alla console di amministrazione di Sophos Mobile di usare la funzionalità Single Sign-On (SSO) di Azure AD.  
- Consentire all'app Sophos Mobile di eseguire l'accesso mediante la funzionalità SSO di Azure AD.  


## <a name="to-set-up-sophos-mobile-integration"></a>Per configurare l'integrazione di Sophos Mobile  

1. Accedere al [portale di Azure]( https://portal.azure.com/), passare a **Intune** > **Conformità del dispositivo** > **Mobile Threat Defense** e selezionare **Aggiungi**.  
2. Nella pagina **Aggiungi un connettore** scegliere **Sophos** dal menu a discesa. Selezionare quindi **Crea**.  
3. Selezionare il collegamento *Apri la console dell'amministratore di Sophos*.  
4. Accedere alla [console di amministrazione di Sophos](https://central.sophos.com/) con le credenziali di Sophos.  
5. Passare a **Mobile** > **Settings (Impostazioni)** > **Setup (Configura)** > **Sophos setup (Configurazione di Sophos)**.  
6. Nella pagina **Sophos setup** selezionare la scheda **Intune MTD**.  
   ![Configurazione di Sophos](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. Selezionare **Bind** (Associa) e quindi **Yes** (Sì). Sophos si connette a Intune e chiede di eseguire l'accesso alla sottoscrizione di Intune. 
8. Nella finestra di autenticazione di Microsoft Intune immettere le credenziali di Intune e **accettare** la richiesta di autorizzazioni per *Sophos Mobile Thread Defense*.  
   ![Autenticazione di Intune ](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. Nella pagina **Sophos setup** selezionare **Save** (Salva) per completare la configurazione per Intune:  
   ![Salvare la configurazione di Sophos](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. Quando viene visualizzato il messaggio **Successful Integration** (Integrazione riuscita), l'integrazione è completa.  
1. Sophos è ora disponibile nella console di Intune.  


## <a name="next-steps"></a>Passaggi successivi  
[Configurare le app client di Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
