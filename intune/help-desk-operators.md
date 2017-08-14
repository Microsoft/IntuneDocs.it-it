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
ms.openlocfilehash: 066f8668ea37e928455792f512e4e337a1f19c20
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2017
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il portale di risoluzione dei problemi consente agli operatori del supporto tecnico e agli amministratori di Intune di visualizzare le informazioni degli utenti per rispondere alle richieste di assistenza degli utenti. Le organizzazioni con operatori del supporto tecnico possono assegnare il ruolo **Help Desk Operator** (Operatore del supporto tecnico) a un gruppo di utenti che possono quindi usare il pannello Risoluzione dei problemi per aiutare gli utenti.

Ad esempio, quando un utente contatta il supporto tecnico per un problema tecnico di Intune, l'operatore del supporto tecnico immette il nome dell'utente. Intune Mostra dati utili che consentono di risolvere molti problemi di livello 1 tra cui:
- Stato utente
- Assignments
- Errore di installazione dell'app
- Problemi di conformità
- Un dispositivo che non risponde
-   Un dispositivo che non riceve le impostazioni VPN o Wi-Fi
-   Un errore di installazione dell'app

## <a name="add-help-desk-operators"></a>Aggiungere operatori del supporto tecnico
Come amministratore di Intune, è possibile assegnare il ruolo Help Desk Operator (Operatore del supporto tecnico) a un gruppo di utenti. I membri del gruppo possono usare il portale di amministrazione per risolvere i problemi degli utenti. Ogni operatore del supporto tecnico deve avere una licenza di Intune per accedere al portale di Intune. Informazioni su come [assegnare le licenze di Intune](licenses-assign.md).

Per aggiungere utenti al gruppo del supporto tecnico:
1. [Aggiungere utenti a Intune](users-add.md) se necessario.
2. [Creare un gruppo di operatori del supporto tecnico](groups-add.md) e aggiungere utenti al gruppo.
3. [Assegnare il ruolo Help Desk Operator (Operatore del supporto tecnico) di controllo degli accessi in base al ruolo](role-based-access-control.md#built-in-roles)

  ![Screenshot del portale di Intune con i ruoli di Intune evidenziati e un elenco dei ruoli predefiniti, incluso Help Desk Operator (Operatore del supporto tecnico)](./media/help-desk-user-add.png). È anche possibile [creare un ruolo personalizzato](role-based-access-control.md#custom-roles) e modificarlo per consentire l'accesso agli operatori del supporto tecnico.  Per risolvere i problemi degli utenti, gli operatori del supporto tecnico devono avere le autorizzazioni seguenti:
    - MobileApps: Lettura
    - ManagedApps: Lettura
    - ManagedDevices: Lettura
    - Organization: Lettura
    - DeviceCompliancePolices: Lettura
    - DeviceConfigurations: Lettura

4. Per concedere agli operatori del supporto tecnico l'autorizzazione per visualizzare l'integrità del servizio e i ticket di supporto aperti per Intune, [concedere agli utenti autorizzazioni di amministratore](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal) come **amministratore del servizio**. Non assegnare l'autorizzazione di **amministratore del servizio Intune** perché questo ruolo della directory ha più diritti di quelli necessari per gli operatori del supporto tecnico.

## <a name="access-the-troubleshooting-portal"></a>Accedere al portale per la risoluzione dei problemi

Il personale del supporto tecnico e gli amministratori di Intune possono accedere al portale per la risoluzione dei problemi in due modi:
- Aprire [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) in un Web browser per visualizzare solo il portale per la risoluzione dei problemi.
  ![Screenshot della console di risoluzione dei problemi](./media/help-desk-console.png)
- Accedere al portale di Azure, scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune** e quindi passare a **Guida e supporto tecnico** > **Risoluzione dei problemi**.

Fare clic su **Selezionare l'utente** per visualizzare un utente e i relativi dettagli.

![Screenshot del carico di lavoro Intune Troubleshoot (Risoluzione dei problemi di Intune) con il collegamento Seleziona utente](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>Usare il portale per la risoluzione dei problemi

Nel portale per la risoluzione dei problemi è possibile scegliere **Seleziona utente** per visualizzare le informazioni relative a un utente. Le informazioni utente sono utili per definire lo stato corrente degli utenti e dei loro dispositivi. Il portale per la risoluzione dei problemi mostra i seguenti dettagli per la risoluzione dei problemi:
- **Stato dell'account**
- **Stato utente**
- **Dispositivi** con le azioni per i dispositivi
- **Appartenenza a gruppi**
- **Stato protezione app**
