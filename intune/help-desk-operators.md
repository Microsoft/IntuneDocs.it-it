---
title: Portale del supporto tecnico per la risoluzione dei problemi
titleSuffix: Intune on Azure
description: Il personale del supporto tecnico usa il portale per risolvere i problemi tecnici degli utenti
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 7a61c3703cd1016ef63c8baa371c3a21dca127fc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Assistere gli utenti con il portale per la risoluzione dei problemi in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il portale di risoluzione dei problemi consente gli operatori del supporto tecnico e agli amministratori di Intune di visualizzare le informazioni sull'utente per risolvere le richieste degli utenti. Le organizzazioni con operatori del supporto tecnico possono assegnare il ruolo **Help Desk Operator** (Operatore del supporto tecnico) a un gruppo di utenti che possono quindi usare il pannello Risoluzione dei problemi per aiutare gli utenti.

Ad esempio, quando un utente contatta il supporto tecnico per un problema tecnico di Intune, l'operatore del supporto tecnico immette il nome dell'utente. Intune visualizza informazioni pertinenti che consentono di risolvere molti problemi di primo livello, ad esempio lo stato dell'utente, un errore di installazione di un'app o problemi di conformità. I problemi risolti possono includere:
- Un dispositivo che non risponde
-   Un dispositivo che non riceve le impostazioni VPN o Wi-Fi
-   Un errore di installazione dell'app


## <a name="add-help-desk-operators"></a>Aggiungere operatori del supporto tecnico
Un amministratore di Intune può assegnare agli utenti l'autorizzazione di operatore del supporto tecnico in due modi:
- Assegnare il ruolo predefinito **Help Desk Operator** (Operatore del supporto tecnico)
- Creare e assegnare un ruolo personalizzato

## <a name="assign-help-desk-operator-role"></a>Assegnare il ruolo di operatore di help desk
Come amministratore di Intune, è possibile assegnare il ruolo Help Desk Operator (Operatore del supporto tecnico) a un gruppo di utenti. I membri del gruppo possono usare il portale di amministrazione. Ogni operatore del supporto tecnico deve avere una licenza di Intune per accedere al portale di Intune. Informazioni su come [assegnare le licenze di Intune](licenses-assign.md).

1. Come amministratore di Intune, accedere al portale di Intune e selezionare **Ruoli di Intune**.
2. In **Ruoli di Intune** selezionare **Help Desk Operator** (Operatore del supporto tecnico) > **Assegnazioni** e quindi selezionare **Assegna**.
  ![Screenshot del portale di Intune con i ruoli di Intune evidenziati e un elenco dei ruoli predefiniti, incluso Help Desk Operator (Operatore del supporto tecnico) con Assegnazioni evidenziato e una casella rossa per Assegna](./media/help-desk-user-assign.png)
3. Digitare un **Nome dell'assegnazione** (obbligatorio), una **Descrizione dell'assegnazione** (facoltativa), quindi assegnare **Membri (gruppi)** e **Ambito (gruppi)**.
4. Ora i membri appartenenti al ruolo Operatore del supporto tecnico possono usare il portale per la risoluzione dei problemi.

Per altre informazioni sui ruoli di Intune, vedere [Ruoli di Intune (Controllo degli accessi in base al ruolo)](role-based-access-control.md).

## <a name="create-a-custom-role-for-troubleshooting"></a>Creare un ruolo personalizzato per la risoluzione dei problemi
Come amministratore di Intune, è possibile creare un ruolo personalizzato che consente agli utenti di usare il portale di risoluzione dei problemi con autorizzazioni che rispondono alle esigenze dell'organizzazione. Per altre informazioni sui ruoli di Intune, vedere [Ruoli di Intune (Controllo degli accessi in base al ruolo)](role-based-access-control.md).

![Screenshot del portale di Intune con i ruoli di Intune evidenziati e un elenco dei ruoli predefiniti, incluso Help Desk Operator (Operatore del supporto tecnico)](./media/help-desk-user-add.png)

Per usare la console di Intune per una visualizzazione del supporto tecnico, un ruolo di supporto tecnico personalizzato deve avere le autorizzazioni seguenti:
- MobileApps: Lettura
- ManagedApps: Lettura
- ManagedDevices: Lettura
- Organization: Lettura

## <a name="access-the-troubleshooting-portal"></a>Accedere al portale per la risoluzione dei problemi

Il personale del supporto tecnico e gli amministratori di Intune possono accedere al portale per la risoluzione dei problemi in due modi:
- Aprire [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) in un Web browser.
- Nel portale di Intune passare **Guida e supporto tecnico** > **Risoluzione dei problemi**.

![Screenshot del carico di lavoro Intune Troubleshoot (Risoluzione dei problemi di Intune) con il collegamento Seleziona utente](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>Usare il portale per la risoluzione dei problemi

Nel portale per la risoluzione dei problemi è possibile scegliere **Seleziona utente** per visualizzare le informazioni relative a un utente. Le informazioni utente sono utili per definire lo stato corrente degli utenti e dei loro dispositivi. Il portale per la risoluzione dei problemi mostra i seguenti dettagli per la risoluzione dei problemi:
- **Stato tenant**
- **Stato utente**
- **Dispositivi** e azioni di dispositivo
- **Appartenenza a gruppi**
- **Stato protezione app**
